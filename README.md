# DiaLexPoL WSD datasets

## Krzysztof Nowak, Iwona Krawczyk, Jagoda Marszałek

This repository contains the data released with the DiaLexPoL paper:
dictionary quotations and contexts, curated sense inventories, sampled
Neo-Latin concordance lines, human annotations, parsed prediction tables and
the coding of 15 consensus-failure quotations.

It does not contain complete dictionary exports or complete source works.

## Structure

- [`dictionary_quotations/`](dictionary_quotations/) — quotations, features
  and consensus-failure coding;
- [`neolatin_concordances/`](neolatin_concordances/) — source metadata,
  concordance lines, gold labels, annotations and sigla;
- [`senses/`](senses/) — the released sense inventories;
- [`llm_predictions/`](llm_predictions/) — parsed Exp. 1 and Exp. 2 results.

`gold.csv` contains 839 analyzable records. The paper's evaluation scope has
837 records because two `comitia` records were excluded during evaluation-set
construction; see [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md) and
`exp2_iaa.ipynb` in the companion code repository.

The dataset is released under CC BY 4.0; see [`LICENSE`](LICENSE).

## Paper and code

Paper: *DiaLexPoL: LLM-assisted Sense Assignment for a Diachronic Dictionary
of Latin*.

Companion code:
[`novacellus/dialexpol-llm-wsd-2026-code`](https://github.com/novacellus/dialexpol-llm-wsd-2026-code)
and [Zenodo](https://doi.org/10.5281/zenodo.21626003).

Please cite this dataset using
[its Zenodo DOI](https://doi.org/10.5281/zenodo.21625867), together with the
paper.
