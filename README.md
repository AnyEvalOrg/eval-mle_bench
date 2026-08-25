# eval-mle_bench

**MLE-bench: Evaluating Machine Learning Agents on Machine Learning Engineering**

**Paper:** https://arxiv.org/abs/2410.07095

Machine learning tasks drawn from 75 Kaggle competitions.

## At a glance

| | |
|---|---|
| Upstream | [`src/inspect_evals/mle_bench`](https://github.com/UKGovernmentBEIS/inspect_evals/tree/main/src/inspect_evals/mle_bench) |
| Group | Coding |
| Total samples | 98 |
| Execution class | `sandbox-local` |
| Cost class | `high` |
| Flags | sandboxed |
| Tags | Agent |

### Tasks

| Task | Samples |
|---|---|
| `mle_bench` | 1 |
| `mle_bench_full` | 75 |
| `mle_bench_lite` | 22 |

### External assets

- `git_clone` — `https://github.com/openai/mle-bench.git` (pinned)
- `direct_url` — `https://github.com/conda-forge/miniforge/releases/download/24.11.3-0/Miniforge3-Linux-x86_64.sh` (pinned)
- `direct_url` — `https://github.com/git-lfs/git-lfs/releases/download/v3.6.1/git-lfs-linux-amd64-v3.6.1.tar.gz` (pinned)
- `git_dependency` — `https://github.com/openai/mle-bench.git` (pinned)

## Running one problem

OpenEvalz is problem-level: the atomic unit is a single sample, not the whole eval.

```bash
inspect eval inspect_evals/mle_bench \
  --sample-id "<sample-id>" \
  --model openai-api/trustedrouter/<model> \
  --token-limit 200000
```

> **Two things that bite here, both verified in Inspect's source.**
>
> 1. **`--cost-limit` does not work on this routing path.** Inspect only records cost when its
>    pricing table resolves the model, and `_model_info.py` strips only `azure|bedrock|vertex`
>    prefixes — so `trustedrouter/<model>` never resolves and the cap silently never binds. The
>    real spend cap is enforced **server-side by TrustedRouter** via the delegated key's
>    `limit_microdollars` and spend window. Use `--token-limit` as the in-process bound.
> 2. **`--sample-id` matches with `fnmatch`.** A glob silently selects many samples and only warns.
>    Always pass a literal id.

## Reproducibility

`bundle.template.json` is the contract. A run that cannot emit a complete bundle does not publish.
Every image is pinned by `sha256` digest and every dataset by revision.

## Licensing

OpenEvalz wrapper code in this repository is **Business Source License 1.1** (see `LICENSE`) —
Licensor Lore Hex Corp, Change Date four years from publication, Change License Apache 2.0, no
Additional Use Grant. Same terms as TrustedRouter. Source-available, not open source: you may read,
modify and make non-production use of it, but production use needs a commercial licence
(licensing@openevalz.com).

**The packaged evaluation is NOT relicensed.** The task code, dataset and container images come from
upstream under their own terms — inspect_evals is MIT (UK AI Security Institute), and individual
datasets and images carry their own, sometimes unstated, licences. BSL covers only the OpenEvalz
packaging around them. See `NOTICE.md`, which must be completed before this repo publishes anything.
