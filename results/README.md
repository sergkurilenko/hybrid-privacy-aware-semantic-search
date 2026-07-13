# Experimental results

`system_revision/` contains the curated machine-readable evidence for the
current manuscript. The directory includes result summaries, per-query or
per-request records where appropriate, configuration and environment
manifests, hashes, and small content-addressed projection bases.

Large derived embeddings, projected matrices, and Faiss indexes are not
committed. They can be rebuilt from the pinned inputs and recipes documented
in `../docs/reproduce_system_revision.md`. The claim-to-artifact mapping is in
`../docs/results_manifest.md`.
