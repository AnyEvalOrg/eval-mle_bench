# NOTICE — upstream attribution and licence status

`eval-mle_bench` packages an evaluation from **inspect_evals**.

- **Upstream:** https://github.com/UKGovernmentBEIS/inspect_evals (`src/inspect_evals/mle_bench`)
- **inspect_evals licence:** MIT (Copyright (c) UK AI Security Institute)
- **OpenEvalz wrapper code in this repository:** Business Source License 1.1, see `LICENSE`

## Two licences, two scopes — do not conflate them

BSL 1.1 applies to **OpenEvalz-authored packaging only**: `openevalz.json`, `bundle.template.json`,
`redaction.yaml`, `tr/`, `scaffolds/`, `k8s/`, CI and documentation written here.

BSL does **not** apply to anything obtained from upstream. Files copied from or derived from
inspect_evals remain **MIT** under the UK AI Security Institute's copyright, and datasets and
container images remain under whatever terms their own publishers set. Applying BSL to upstream
work would be a licence violation, not a business decision.

## The eval, its dataset and its images are NOT relicensed here

Harness licence and dataset terms are different things, and the distinction has bitten
this project before. Known examples: the `princeton-nlp/SWE-bench_Verified` dataset card
states **no licence field at all**, and SWE-bench spans 12 repositories including
GPL-2.0 `pylint` — so published traces can embed copyleft source. GPQA ships as a
password-protected archive *deliberately*, to resist contamination.

### External assets declared upstream

- `git_clone`: `https://github.com/openai/mle-bench.git`
- `direct_url`: `https://github.com/conda-forge/miniforge/releases/download/24.11.3-0/Miniforge3-Linux-x86_64.sh`
- `direct_url`: `https://github.com/git-lfs/git-lfs/releases/download/v3.6.1/git-lfs-linux-amd64-v3.6.1.tar.gz`
- `git_dependency`: `https://github.com/openai/mle-bench.git`

### Clearance checklist — must be complete before this repo publishes anything

- [ ] Dataset licence identified and recorded
- [ ] Redistribution rights confirmed for any mirrored image
- [ ] Trace-publication rights confirmed for the model providers in scope
- [ ] `redaction.yaml` reviewed against this eval's specific answer surface
- [ ] Dual-use review (skip only if clearly not applicable)
