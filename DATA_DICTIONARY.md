# DiaLexPoL WSD release data dictionary

## Evaluation-set scope

`neolatin_concordances/gold.csv` contains the 988 sampled and annotated
records. Its `analyzable` flag identifies 839 records that passed the
annotation-level validity and quality criteria.

The released `neolatin_concordances/concordance_lines.csv` contains 837
records: two analyzable `comitia` records were removed during evaluation-set
construction because they could not be used as valid WSD prompts (one lost
the lemma keyword after restoration; the other was a short index/TOC-like
record). Consequently, counts made from `gold.csv[analyzable]` are 585
consensus and 254 adjudicated, while the paper's evaluation-set counts are
583 consensus and 254 adjudicated.

The two excluded keys and their curation metadata are printed by
`exp2_iaa.ipynb` when it runs.

## Consensus-failure coding

`dictionary_quotations/consensus_failure_coding.csv` contains the 15 manual
exploratory codings underlying the paper's consensus-failure analysis. It
retains the quotation, candidate-sense information, public metadata and final
decision category. Draft notes and the unused review field are not released.

## Prediction columns

`predicted_number` is the recorded answer position. `predicted_sid` is the
exporter's validated decoding of that position to a sense id; analysis code
uses this column directly. Empty values mean that no valid sense id could be
assigned. `outcome_stored` reproduces the paper's original scoring and
`outcome_corrected` contains the corrected Exp1 JSON scoring described in
`corrigendum.md`.
