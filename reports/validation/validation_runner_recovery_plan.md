# Validation Runner Recovery Plan

## Decision Summary

Primary recommended path: **repair `codex exec` by explicitly using the Codex.app bundled CLI**:

```bash
/Applications/Codex.app/Contents/Resources/codex exec   --skip-git-repo-check   --ephemeral   --ignore-user-config   --ignore-rules   --sandbox read-only   --config 'model="gpt-5.5"'   --config 'model_reasoning_effort="none"'   --output-last-message <raw_output_path>   - < <input_snapshot_path>
```

Do not run validation until this runner command is separately approved for the validation pass.

## Option 1: Repair `codex exec`

Use `/Applications/Codex.app/Contents/Resources/codex` directly instead of PATH-resolved `/opt/homebrew/bin/codex`.

### Reproducibility

High. The executable path and version are explicit: `codex-cli 0.133.0-alpha.1`. The command can be repeated per variant/task with frozen package inputs and fixed flags.

### Contamination Risk

Low if run from the already-created isolated runtime packages and `input_snapshot.md` only. Use `--ignore-user-config`, `--ignore-rules`, `--ephemeral`, and `--sandbox read-only`. The smoke test still emitted bundled skill-loader warnings, so the validation run metadata should record those warnings and the exact command. Runtime prompts must continue to say to use only package files.

### No-Tool Constraints

Comparable to the dev `codex exec` protocol: read-only sandbox, no external retrieval instructions, no benchmark gold/rubric in generation context, and no dynamic tool use requested. The CLI may still have its normal shell capability internally, but the model is instructed not to use dynamic tools and the sandbox is read-only. If stricter tool prohibition is required, use Option 3 instead.

### Artifact Capture

Strong. Use `--output-last-message` for `raw_output.md`, preserve `input_snapshot.md`, and write `run_metadata.yaml` after each generation. stdout/stderr can be saved separately if desired.

### Post-Generation Scoring

Unaffected. Gold, rubric, and agent-review decision layer remain outside the generation package and are used only afterward.

### Fairness With Dev Runs

Best match. Prior dev metadata used `codex-cli 0.133.0-alpha.1`, the same version exposed by the bundled app binary. This is more comparable than the broken Homebrew `0.118.0` cask binary.

### Recommendation

Recommended primary path.

## Option 2: Use A Simpler `codex exec` Command With Fewer Flags

Example:

```bash
/Applications/Codex.app/Contents/Resources/codex exec --skip-git-repo-check --sandbox read-only - < input_snapshot.md
```

### Reproducibility

Medium. Fewer flags reduce parsing errors but may permit user config, rules, persistence, or notification hooks to influence execution.

### Contamination Risk

Medium. Without `--ignore-user-config` and `--ignore-rules`, runtime behavior can be affected by local config, rules, hooks, or enabled plugins. That is less desirable for formal validation.

### No-Tool Constraints

Weaker than Option 1 because local config could expose extra behavior. Still no benchmark gold/rubric if package is isolated.

### Artifact Capture

Good if combined with `--output-last-message`.

### Post-Generation Scoring

Unaffected.

### Fairness With Dev Runs

Potentially weaker if user config differs from prior dev execution assumptions.

### Recommendation

Use only as a debugging fallback, not the formal validation runner.

## Option 3: Use An OpenAI API No-Tool Runner

Create a small script that sends one request per task with only the frozen `input_snapshot.md` content. No tools would be declared. The script would write `raw_output.md` and metadata, then scoring would happen separately.

### Reproducibility

High if model, parameters, request body, and input hashes are recorded. It avoids CLI binary instability.

### Contamination Risk

Low to very low. The script can hard-code no tools and read only the isolated runtime packages. It can be easier to enforce that gold/rubric/review reports never enter generation.

### No-Tool Constraints

Strongest. No tools are exposed at all.

### Artifact Capture

Strong. The script can write `input_snapshot.md`, `raw_output.md`, `run_metadata.yaml`, and request metadata deterministically.

### Post-Generation Scoring

Unaffected if scoring is a separate explicit phase.

### Fairness With Dev Runs

Medium. This changes the execution surface from Codex CLI to direct API calls. Outputs may differ because Codex CLI agent scaffolding and API request scaffolding are not identical. It is acceptable only if documented as a new validation runner and, ideally, all variants including B0 are rerun through the same API runner.

### Recommendation

Do not use as primary while the bundled Codex CLI is repairable. Keep as backup if formal no-tool enforcement is more important than continuity with dev runs.

## Option 4: Manual App-Based Isolated Threads

Open one fresh Codex desktop thread per variant/task and paste the isolated `input_snapshot.md`, then save outputs manually.

### Reproducibility

Low. Manual thread setup is harder to audit, and model/app state may vary.

### Contamination Risk

Medium to high. Desktop project guidance, skills, plugins, or conversation state could accidentally enter the run unless carefully isolated.

### No-Tool Constraints

Weak. It is difficult to prove identical disabled-tool permissions across 48 runs.

### Artifact Capture

Manual and error-prone.

### Post-Generation Scoring

Possible, but provenance would be weaker.

### Fairness With Dev Runs

Poor compared with scripted execution.

### Recommendation

Not recommended except as an emergency manual sanity check, not as formal validation.

## Recommended Runner Contract

Before validation execution, approve a runner command based on Option 1:

```bash
/Applications/Codex.app/Contents/Resources/codex exec   --skip-git-repo-check   --ephemeral   --ignore-user-config   --ignore-rules   --sandbox read-only   --config 'model="gpt-5.5"'   --config 'model_reasoning_effort="none"'   --output-last-message runs/validation/<variant>/<task_id>/raw_output.md   - < /private/tmp/ling_bot_validation_v0_1_execution/<variant>/tasks/<task_id>/input_snapshot.md
```

For each run, save:

- `input_snapshot.md` copied from the frozen runtime package;
- `raw_output.md` from `--output-last-message`;
- `run_metadata.yaml` with executable path, CLI version, command flags, package path, input hash, packet hash, variant hash, and fresh-context confirmation;
- stdout/stderr transcript if practical;
- no `scorecard.yaml` or `scoring_notes.md` until after generation completes for the relevant run.

## Integrity Conditions For Retrying

- Do not modify validation freeze artifacts.
- Do not modify validation task YAMLs, packets, gold, rubric, run protocol, or variants.
- Do not include gold/rubric/agent-review reports in runtime packages.
- Do not use PATH-resolved `codex` unless it is repaired and re-diagnosed.
- Do not design B4 until validation results exist.

## API Runner Status

Because the Codex.app bundled CLI can be repaired cleanly, no API runner script was created in this pass. If the bundled CLI later fails during full validation, the next fallback should be a dry-run-default API runner specification and script, followed by explicit approval before use.
