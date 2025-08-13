# SNLI LIME Explanation Analysis Report
**Dataset**: SNLI  
**Model**: roberta-large-mnli  
**Analysis Date**: 2025-08-13  
**Total Examples**: 1000  
**Git Hash**: b1491a0b
## Key Results
- **Model Accuracy**: 0.861 (861/1000)
- **Average Confidence**: 0.934
- **LIME Parameters**: 700 samples, 10 features
- **Random Seed**: 42

## Attribution Metrics Results
| Metric | Mean | Std | Min | Max | 95% CI |
|--------|-----:|----:|----:|----:|:------:|
| Faithfulness | 0.296 | 0.356 | -0.495 | 0.997 | [0.274, 0.321] |
| Sufficiency | 0.693 | 0.321 | 0.002 | 1.000 | [0.672, 0.714] |
| Comprehensiveness | 0.296 | 0.356 | -0.495 | 0.997 | [0.272, 0.321] |

## Sanity Checks
- Correct predictions: **861**
- Incorrect predictions: **139**

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
**Example 1** (Conf: 1.000)
- **Premise**: A city street with a telephone booth, passing cars, a parked bicycle, and a blond woman with a purse and young girl with a backpack walking away.
- **Hypothesis**: None of the cars are moving.
- **Predicted**: contradiction
- **Top Attributions**: None(-0.405), moving.(-0.066), cars(+0.055)

**Example 2** (Conf: 1.000)
- **Premise**: A man is laying on a deck.
- **Hypothesis**: A woman is laying on a deck in a bikini.
- **Predicted**: contradiction
- **Top Attributions**: woman(-0.621), bikini.(+0.200), deck(+0.075), laying(+0.020)

**Example 3** (Conf: 1.000)
- **Premise**: Guitar player practices surrounded by instruments.
- **Hypothesis**: The guitar player is cooking dinner.
- **Predicted**: contradiction
- **Top Attributions**: cooking(-0.117), dinner.(-0.106), player(-0.026), guitar(-0.017)


## Qualitative Examples — Top Incorrect Predictions
**Example 1** (Conf: 1.000)
- **Premise**: a man and a woman enjoy a nice meal at an outdoor restaurant.
- **Hypothesis**: The people eating are indoors.
- **True**: entailment  
- **Predicted**: contradiction
- **Top Attributions**: indoors.(-0.439), people(+0.018), eating(+0.010)

**Example 2** (Conf: 0.998)
- **Premise**: A man and his son are sitting in the open door of a white van.
- **Hypothesis**: The man and his son were watching tv
- **True**: contradiction  
- **Predicted**: neutral
- **Top Attributions**: watching(+0.457), tv(+0.180), son(+0.086), man(-0.039)


## Known Caveats
- **Delimiter Handling**: Uses ` [SEP] ` separator between premise and hypothesis
- **Stopword Filtering**: Removes common English stopwords and special tokens
- **Sample Size**: Analysis based on **1000** examples
- **Perturbation Sensitivity**: LIME results may vary with different num_samples settings

## Next Steps
1. Add `kernel_width` variant to stability on a small subset (e.g., 50 ex)
2. Calibrate confidence (reliability diagram) and note over-/under-confidence
3. Compare with SHAP/Integrated Gradients on the same subset
