# PS-DEV-01 Model Input Packet

## Corpus

1. BERT Rediscovers the Classical NLP Pipeline, arXiv:1905.05950, 9-page arXiv PDF.
2. A Primer in BERTology: What we know about how BERT works, arXiv:2002.12327, 23-page arXiv PDF.
3. A Structural Probe for Finding Syntax in Word Representations, ACL Anthology N19-1419 PDF, 10 pages.
4. Local seed idea brief: representation probing.

## Controlled Source Notes

BERT Rediscovers:

- The paper uses edge-probing tasks and layer analysis to investigate where linguistic information appears in BERT representations.
- It explicitly warns that inspection/probing has limitations: observing a pattern does not necessarily show how the model uses that information.
- Evidence locations: abstract; Section 2 probing tasks; Section 3 scalar mixing/cumulative scoring; Figures 1-3; limitations paragraph.

BERTology primer:

- The primer surveys work on BERT representations, attention, probing, and what is known about how BERT works.
- The primer is a survey source covering BERT representations, attention, probing, and methodological cautions.
- Evidence locations: survey sections on probing and representations; methodological cautions and discussion.

Structural Probe:

- The paper proposes a structural probe that learns a linear transformation under which squared distances or norms correspond to parse-tree distances or depths.
- It evaluates contextual representations such as ELMo and BERT and includes baselines.
- The paper discusses limitations of probing tasks and the tradeoff between probe complexity, probe task, and hypothesis.
- Evidence locations: abstract; Section 2; Table 1; Figures 1-5; limitations discussion around probing tasks.

Local seed idea:

- The local seed idea concerns whether probing results reveal stable representational structure or reflect probe capacity, dataset artifacts, and analysis choices.
