# Validation Runner Diagnosis

## Scope

This diagnosis investigates why validation execution was blocked before any benchmark run completed. It does not run validation, score validation, modify benchmark artifacts, modify variants, or design B4.

## Blocked Run Record Inspected

File inspected: `reports/validation/validation_execution_blocked_by_codex_cli.md`

Recorded smoke-test command:

```bash
codex exec --skip-git-repo-check --ask-for-approval never --sandbox read-only --reasoning-effort none "Reply with exactly VALIDATION_CLI_OK"
```

Recorded working directory:

```text
/private/tmp/ling_bot_validation_v0_1_execution/B0_base_agent
```

Recorded result:

```text
exited immediately with code -1 and no generation output
```

## Executable Discovery

### Shell path

```bash
command -v codex
```

stdout:

```text
/opt/homebrew/bin/codex
```

### Homebrew/Cask executable

```bash
ls -l /opt/homebrew/bin/codex
file /opt/homebrew/bin/codex
```

stdout:

```text
/opt/homebrew/bin/codex -> /opt/homebrew/Caskroom/codex/0.118.0/codex-aarch64-apple-darwin
/opt/homebrew/bin/codex: Mach-O 64-bit executable arm64
```

Installed path implies Codex CLI version family `0.118.0`, but `codex --version` cannot execute for this binary.

### Codex.app bundled executable

```bash
ls -l /Applications/Codex.app/Contents/Resources/codex
file /Applications/Codex.app/Contents/Resources/codex
/Applications/Codex.app/Contents/Resources/codex --version
```

stdout:

```text
/Applications/Codex.app/Contents/Resources/codex: Mach-O 64-bit executable arm64
codex-cli 0.133.0-alpha.1
```

stderr:

```text
WARNING: proceeding, even though we could not update PATH: Operation not permitted (os error 1)
```

Interpretation: the bundled Codex.app CLI is executable and matches the version recorded in prior dev run metadata (`codex-cli 0.133.0-alpha.1`).

## Environment And Auth Checks

Relevant environment variables were present but values were redacted:

```text
CODEX_CI=<present>
CODEX_INTERNAL_ORIGINATOR_OVERRIDE=<present>
CODEX_SANDBOX=<present>
CODEX_SANDBOX_NETWORK_DISABLED=<present>
CODEX_SHELL=<present>
CODEX_THREAD_ID=<present>
OPENAI_API_KEY=<present>
SSH_AUTH_SOCK=<present>
```

Codex config/auth files:

```text
/Users/tilly/.codex/config.toml exists, size 3532
/Users/tilly/.codex/auth.json exists, size 4383
/Users/tilly/.codex/credentials.json missing
```

Interpretation: authentication material appears present. The successful bundled-CLI smoke test below confirms auth is not the blocking issue for that executable.

## Command Tests

The following tests were run in three working directories:

- `/Users/tilly/code/repository/Ling-bot`
- `/private/tmp`
- `/private/tmp/ling_bot_validation_v0_1_execution/B0_base_agent`

For the Homebrew/Cask `codex` on PATH, all of these commands exited with signal-kill semantics and no stdout/stderr:

```bash
codex --help
codex --version
codex exec --help
codex exec "Reply with exactly VALIDATION_CLI_OK"
codex exec --skip-git-repo-check --ask-for-approval never --sandbox read-only --reasoning-effort none "Reply with exactly VALIDATION_CLI_OK"
codex exec --skip-git-repo-check --ask-for-approval never "Reply with exactly VALIDATION_CLI_OK"
codex exec --skip-git-repo-check "Reply with exactly VALIDATION_CLI_OK"
```

Observed result for each:

```text
exit code: -9
stdout: <empty>
stderr: <empty>
```

Dropping Codex sandbox variables, dropping `OPENAI_API_KEY`, and using a minimal PATH did not change this outcome; `codex --help` still exited `-9`.

## Code Signing / Quarantine Checks

```bash
codesign -dv /opt/homebrew/Caskroom/codex/0.118.0/codex-aarch64-apple-darwin
xattr -l /opt/homebrew/Caskroom/codex/0.118.0/codex-aarch64-apple-darwin
spctl -a -vv /opt/homebrew/Caskroom/codex/0.118.0/codex-aarch64-apple-darwin
```

Relevant output:

```text
TeamIdentifier=2DC432GLL2
com.apple.quarantine: 0181;69d3de48;Homebrew Cask;...
spctl: internal error in Code Signing subsystem
```

Interpretation: the Homebrew/Cask executable is signed but quarantined, and macOS assessment reports an internal code-signing subsystem error. Combined with universal `-9` before `--help`, this is consistent with OS/runtime rejection or sandbox-incompatible binary execution rather than a Codex prompt, auth, task, or flag problem.

## Bundled CLI Help Test

```bash
/Applications/Codex.app/Contents/Resources/codex exec --help
```

exit code: `0`

stdout excerpt:

```text
Run Codex non-interactively

Usage: codex exec [OPTIONS] [PROMPT]
       codex exec [OPTIONS] <COMMAND> [ARGS]
...
      --skip-git-repo-check
          Allow running Codex outside a Git repository

      --ephemeral
          Run without persisting session files to disk

      --ignore-user-config
          Do not load `$CODEX_HOME/config.toml`; auth still uses `CODEX_HOME`

      --ignore-rules
          Do not load user or project execpolicy `.rules` files

  -o, --output-last-message <FILE>
          Specifies file where the last message from the agent should be written
```

Important flag difference: this bundled CLI does **not** accept `--ask-for-approval`; attempting that flag returns:

```text
error: unexpected argument '--ask-for-approval' found
```

## Minimal Bundled CLI Generation Smoke Test

Command tested:

```bash
/Applications/Codex.app/Contents/Resources/codex exec   --skip-git-repo-check   --ephemeral   --ignore-user-config   --ignore-rules   --sandbox read-only   --config 'model="gpt-5.5"'   --config 'model_reasoning_effort="none"'   "Reply with exactly VALIDATION_APP_CLI_OK"
```

Working directory:

```text
/private/tmp
```

Exit code: `0`

stdout/stderr stream excerpt:

```text
OpenAI Codex v0.133.0-alpha.1
workdir: /private/tmp
model: gpt-5.5
provider: openai
approval: never
sandbox: read-only
reasoning effort: none
...
VALIDATION_APP_CLI_OK
```

Warnings appeared about PATH update and bundled skill icon metadata, but the command completed and returned the expected final text. This was a non-benchmark smoke test only.

## Likely Root Cause

Primary root cause: the PATH-resolved Homebrew/Cask `codex` executable at `/opt/homebrew/Caskroom/codex/0.118.0/codex-aarch64-apple-darwin` is not executable in this environment. It is killed before help/version parsing, independent of working directory, prompt, sandbox variables, auth variables, or validation package contents.

Secondary issue: the previously attempted flag set mixed flags from a different/newer CLI shape. In the working bundled CLI, `--ask-for-approval` is unsupported, while approval behavior is reported as `approval: never` by default under the tested `exec` invocation.

Not likely root causes:

- Validation runtime package contamination: scans already passed.
- Authentication absence: auth files exist and bundled CLI generation succeeds.
- Validation task prompt size/content: `codex --help` fails before any prompt is involved for the Homebrew binary.
- Isolated runtime directory: the same Homebrew failure occurs in repo root and `/private/tmp`.
- Read-only sandbox flag: Homebrew binary fails even without it; bundled CLI works with it.
- `--ignore-user-config` or `--ignore-rules`: bundled CLI works with both.

## Safety Of Retrying With Changed Runner Flags

It is safe to retry validation later with a changed runner command **if** all of the following hold:

1. Invoke `/Applications/Codex.app/Contents/Resources/codex` explicitly rather than `codex` from PATH.
2. Use only flags supported by `codex exec --help` for that executable.
3. Preserve the frozen validation packages and do not alter task packets, gold, variants, rubric, or run protocol.
4. Keep generation inputs limited to each package's `input_snapshot.md`.
5. Use `--ephemeral`, `--ignore-user-config`, `--ignore-rules`, `--skip-git-repo-check`, and `--sandbox read-only`.
6. Use `--output-last-message` or equivalent stdout capture to save raw outputs deterministically.
7. Score only after generation using the frozen validation gold, frozen rubric, and agent-review decision layer.

## Reference Behavior

The bundled Codex CLI help identifies `codex exec` as the non-interactive command and documents prompt/stdin input plus `--output-last-message`. This matches the expected official behavior that non-interactive scripted runs should be possible. The local Homebrew/Cask binary fails before reaching that behavior; the bundled Codex.app binary reaches and executes it.
