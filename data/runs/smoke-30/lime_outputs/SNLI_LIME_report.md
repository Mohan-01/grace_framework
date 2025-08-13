# SNLI LIME Explanation Analysis Report
**Dataset**: SNLI  
**Model**: roberta-large-mnli  
**Analysis Date**: 2025-08-13  
**Total Examples**: 30  
**Git Hash**: b1491a0b
## Key Results
- **Model Accuracy**: 0.733 (22/30)
- **Average Confidence**: 0.933
- **LIME Parameters**: 700 samples, 10 features
- **Random Seed**: 42

## Attribution Metrics Results
| Metric | Mean | Std | Min | Max | 95% CI |
|--------|-----:|----:|----:|----:|:------:|
| Faithfulness | 0.302 | 0.333 | -0.050 | 0.991 | [0.195, 0.433] |
| Sufficiency | 0.715 | 0.325 | 0.022 | 0.996 | [0.588, 0.826] |
| Comprehensiveness | 0.302 | 0.333 | -0.050 | 0.991 | [0.188, 0.427] |

## Sanity Checks
- Correct predictions: **22**
- Incorrect predictions: **8**

## Error Analysis (Top Patterns)
- No pattern summary available.

## LIME Stability Sweep (mini)
- num_samples=500, kernel_width=None: avg_fidelity=0.000 (n=1)- num_samples=1000, kernel_width=None: avg_fidelity=0.000 (n=1)

## LIME Configuration
- **Number of Samples**: 700
- **Number of Features**: 10
- **Top-k Tokens for Metrics**: 3
- **Chunk Size**: 64

## Qualitative Examples — Top Correct Predictions
**Example 1** (Conf: 0.999)
- **Premise**: People look at a glass case holding food for sale.
- **Hypothesis**: The person looked away from the glass case.
- **Predicted**: contradiction
- **Top Attributions**: away(-0.134), looked(-0.122), case.(-0.069), glass(-0.049), person(-0.027)

**Example 2** (Conf: 0.999)
- **Premise**: A red bus is driving on a street between a large building and a water fountain.
- **Hypothesis**: A purple bus is driving on the street.
- **Predicted**: contradiction
- **Top Attributions**: purple(-0.072), driving(-0.038), street.(-0.029), bus(-0.022)

**Example 3** (Conf: 0.998)
- **Premise**: A blue car in front of people under a tent.
- **Hypothesis**: The people are hiding from the rain.
- **Predicted**: neutral
- **Top Attributions**: hiding(+0.151), rain.(+0.116), people(+0.042)


## Qualitative Examples — Top Incorrect Predictions
**Example 1** (Conf: 0.991)
- **Premise**: A man with long hair getting stopped by security guards.
- **Hypothesis**: The man has long hair.
- **True**: neutral  
- **Predicted**: entailment
- **Top Attributions**: hair.(-0.176), long(-0.111), man(-0.068)

**Example 2** (Conf: 0.986)
- **Premise**: A potter making a vase on a spinning wheel.
- **Hypothesis**: The potter's wheel spins.
- **True**: neutral  
- **Predicted**: entailment
- **Top Attributions**: spins.(-0.146), potter's(-0.035), wheel(-0.028)


## Known Caveats
- **Delimiter Handling**: Uses ` [SEP] ` separator between premise and hypothesis
- **Stopword Filtering**: Removes common English stopwords and special tokens
- **Sample Size**: Analysis based on **30** examples
- **Perturbation Sensitivity**: LIME results may vary with different num_samples settings

## Next Steps
1. Add `kernel_width` variant to stability on a small subset (e.g., 50 ex)
2. Calibrate confidence (reliability diagram) and note over-/under-confidence
3. Compare with SHAP/Integrated Gradients on the same subset
