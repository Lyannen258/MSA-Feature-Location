# Supplementary Material: Feature Location via Multi-Sequence Alignment

Supplementary material for our paper on a formal framework for feature location and a token-level technique based on multi-sequence alignment. Includes results for an example SPL and the ArgoUML-SPL benchmark.

Accompanies the paper **"Sequence alignment and code: An application to feature location"** by Janik Eriksson, Nico Willert Stark and Yannis Hübenthal.

The tools used to produce these results are available in two repositories:

- Feature computations (feature isolation): [YAH-Coder/feature_isolation](https://github.com/YAH-Coder/feature_isolation)
- Alignment and feature location: [iwi-se/feature_location_msa](https://github.com/iwi-se/feature_location_msa)

## Repository Structure

```
.
├── Example-SPL/              # Example SPL and its feature location results
└── ArgoUML-SPL-Challenge/    # Results for the ArgoUML-SPL benchmark
```

## Example SPL (`Example-SPL/`)

A small example product line implementing a `factorial` function in C++.

| Path | Content |
|------|---------|
| `variants/` | The variants of the example SPL, one folder per system. The folder names are equivalent to the **system indices** used in the theory. Each folder contains the variant's source file (`factorial.hpp`). |
| `alignment.txt` | The intermediate result of the technique: the raw multi-sequence alignment of the variants. |
| `factorial_spl_specification.spl` | The SPL specification (fundamental features and constraints). |
| `result_rendered.html` | A simple interactive view of the result. Open it in a browser. |

## ArgoUML-SPL Benchmark (`ArgoUML-SPL-Challenge/`)

Results for the [ArgoUML-SPL benchmark](https://github.com/marcusvnac/argouml-spl).

### Granularity

`java_atomic_types.txt` defines the granularity at which the alignment operates. It lists the Tree-sitter node types that are treated as atomic, i.e., that are not split further into tokens. It is passed to both tools via `--atomic-types-file`.

### Scenarios

Each `Scenario*` folder contains the results for one scenario:

| Scenario folder | Variants |
|-----------------|----------|
| `ScenarioOriginalVariant` | the original variant (1) |
| `ScenarioTraditionalVariants` | the traditional scenario (10) |
| `ScenarioPairwiseVariants` | pair-wise sampling (9) |
| `ScenarioRandom002Variants` … `ScenarioRandom010Variants`, `ScenarioRandom050Variants`, `ScenarioRandom100Variants` | randomly selected variants (2–10, 50, 100) |
| `ScenarioAllVariants` | all 256 variants |
| `ScenarioAllVariants_TokenLevel` | all 256 variants, run without the atomic types file, i.e., at the default granularity of Tree-sitter tokens. |

Every scenario folder has the same layout:

| Path | Content |
|------|---------|
| `argo_uml_*.spl` | The SPL specification for the scenario. |
| `scenario_*_map.txt` | Mapping from variant folder to system ID. |
| `commands.txt` | The commands we used to align the variants and to produce the benchmark results, including timings. |
| `argo_uml_*_precomputed_traces.txt` | The precomputed "most probable" traces. |
| `alignment_result/alignment_result.zip` | The per file alignments zipped. |
| `benchmark_result/` | The benchmark result, i.e., the output that the metrics are calculated on. |
| `metrics/` | The metrics computed from the benchmark result. |

