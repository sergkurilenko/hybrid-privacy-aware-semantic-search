# Hybrid privacy-aware semantic search

This repository contains the manuscript, implementation, tests, and curated
experimental evidence for:

> **Hybrid privacy-aware semantic search: SVD-truncated document geometry
> and CKKS-encrypted query reranking under a restricted threat model**
> Sergey Kurilenko, [arXiv:2606.26373](https://arxiv.org/abs/2606.26373).

The canonical project URL is
<https://github.com/sergkurilenko/hybrid-privacy-aware-semantic-search>.

## Repository layout

- `paper_revised/` contains the current Springer Nature LaTeX source, figures,
  bibliography, and compiled manuscript.
- `system/` contains the public-PQ, block-packed CKKS, graded-IR, security, and
  systems experiment harnesses used by the manuscript.
- `tests/` contains unit and protocol tests for the current harnesses.
- `results/system_revision/` contains the curated machine-readable experiment
  outputs reported in the paper.
- `docs/` contains reproduction instructions, the pinned environment, and the
  evidence manifest.
- `submission/` contains arXiv metadata and revision notes.

Large embeddings and indexes are regenerated rather than committed. The
million-vector corpus is a Russian Wikipedia paragraph slice, while graded
utility uses pinned BEIR collections. Exact commands and artifact boundaries
are documented in `docs/reproduce_system_revision.md`.

## Local verification

```powershell
python -m pytest tests -q
python system\make_revision_figures.py
python system\make_expansion_figures.py
cd paper_revised
pdflatex -interaction=nonstopmode -halt-on-error main.tex
bibtex main
pdflatex -interaction=nonstopmode -halt-on-error main.tex
pdflatex -interaction=nonstopmode -halt-on-error main.tex
```

The LWE-estimator transcript requires SageMath. Its pinned input, raw output,
runtime description, and parsed costs are preserved under
`results/system_revision/security_expansion/lwe_security/`. Large experiments
checkpoint atomically, so the IR and PQ sweeps can resume without accepting a
partially written index.

## Citation

The preferred citation is the article record in `CITATION.cff`. The arXiv DOI
is `10.48550/arXiv.2606.26373`.

## Licensing

Code and software documentation are available under the MIT License in
`LICENSE`. The manuscript and original figures are available under CC BY 4.0;
see `LICENSE-MANUSCRIPT`. Third-party materials remain subject to their source
licenses as listed in `docs/THIRD_PARTY_NOTICES.md`.

The pre-split history and canonical source commit are recorded in
`PROVENANCE.md`.
