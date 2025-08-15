# SNLI Explanations — LIME / IG / GradientSHAP

_Generated: 2025-08-14T01:08:13_

## Run configuration

```json
{
  "schema_version": "1.2",
  "timestamp": "2025-08-14T01:07:31.183510",
  "git_hash": "76243edd",
  "model_name": "roberta-large-mnli",
  "random_seed": 42,
  "num_samples": 700,
  "chunk_size": 64,
  "lime_num_samples": 700,
  "lime_num_features": 10,
  "k_tokens": 3,
  "snli_labels": [
    "entailment",
    "neutral",
    "contradiction"
  ],
  "mnli_labels": [
    "contradiction",
    "neutral",
    "entailment"
  ],
  "snli_to_mnli_idx": {
    "0": 2,
    "1": 1,
    "2": 0
  },
  "do_ig": true,
  "do_gshap": true,
  "gshap_num_examples": 1000,
  "attr_k_metrics": 3,
  "stable_pool": {
    "enable": true,
    "k": 5,
    "jaccard_min": 0.4,
    "suff_min": 0.8,
    "faith_min": 0.0
  },
  "num_examples": 1000,
  "ig_num_examples": 1000,
  "ig_n_steps": 700,
  "gshap_num_samples": 700
}
```


## LIME

- Examples: **0**
- Faithfulness: **0.000 ± 0.000**
- Sufficiency: **0.000 ± 0.000**
- Comprehensiveness: **0.000 ± 0.000**

_(plots not found for this method)_

## Integrated Gradients

- Examples: **0**
- Faithfulness: **0.000 ± 0.000**
- Sufficiency: **0.000 ± 0.000**
- Comprehensiveness: **0.000 ± 0.000**

_(plots not found for this method)_

## GradientSHAP

- Examples: **0**
- Faithfulness: **0.000 ± 0.000**
- Sufficiency: **0.000 ± 0.000**
- Comprehensiveness: **0.000 ± 0.000**

_(plots not found for this method)_

### Sanity checks
Saved at `sanity_check_results.json`.


### Error analysis
Saved at `error_analysis.json`.


### LIME stability sweep
Saved at `lime_stability_sweep.json`.

