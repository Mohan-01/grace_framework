# SNLI LIME Explanation Analysis Report

## Executive Summary

**Dataset**: SNLI (Stanford Natural Language Inference)  
**Model**: roberta-large-mnli  
**Analysis Date**: 2025-08-11  
**Total Examples**: 1000  
**Git Hash**: a5cf6fc0  

### Key Results
- **Model Accuracy**: 0.861 (861/1000)
- **Average Confidence**: 0.934
- **LIME Parameters**: 700 samples, 10 features
- **Random Seed**: 42

## Attribution Metrics Results

### Faithfulness, Sufficiency, and Comprehensiveness

| Metric | Mean | Std | Min | Max | 95% CI |
|--------|------|-----|-----|-----|--------|
| Faithfulness | 0.102 | 0.137 | 0.000 | 0.602 | [0.093, 0.110] |
| Sufficiency | 0.675 | 0.318 | 0.000 | 1.000 | [0.655, 0.695] |
| Comprehensiveness | 0.063 | 0.159 | -0.507 | 0.602 | [0.054, 0.073] |

## LIME Configuration

- **Number of Samples**: 700
- **Number of Features**: 10
- **Top-k Tokens for Metrics**: 3
- **Chunk Size**: 64

## Qualitative Examples

### Top Correct Predictions

**Example 1** (Confidence: 1.000)
- **Premise**: A city street with a telephone booth, passing cars, a parked bicycle, and a blond woman with a purse and young girl with a backpack walking away.
- **Hypothesis**: None of the cars are moving.
- **Predicted**: contradiction
- **Top Attributions**: None(-0.263), passing(-0.062), walking(-0.026)

**Example 2** (Confidence: 1.000)
- **Premise**: A man is laying on a deck.
- **Hypothesis**: A woman is laying on a deck in a bikini.
- **Predicted**: contradiction
- **Top Attributions**: man(-0.411), woman(-0.299), bikini(0.243), deck(0.075), laying(0.039)

**Example 3** (Confidence: 1.000)
- **Premise**: Guitar player practices surrounded by instruments.
- **Hypothesis**: The guitar player is cooking dinner.
- **Predicted**: contradiction
- **Top Attributions**: Guitar(-0.124), practices(-0.107), cooking(-0.101), instruments(-0.068), surrounded(0.028)

### Top Incorrect Predictions

**Example 1** (Confidence: 1.000)
- **Premise**: a man and a woman enjoy a nice meal at an outdoor restaurant.
- **Hypothesis**: The people eating are indoors.
- **True**: entailment, **Predicted**: contradiction
- **Top Attributions**: outdoor(-0.366), indoors(-0.253), eating(0.098), meal(-0.062), woman(-0.029)

**Example 2** (Confidence: 0.998)
- **Premise**: A man and his son are sitting in the open door of a white van.
- **Hypothesis**: The man and his son were watching tv
- **True**: contradiction, **Predicted**: neutral
- **Top Attributions**: watching(0.520), tv(0.098), sitting(0.093), van(0.050), open(0.045)


## Known Caveats

- **Delimiter Handling**: Uses `</s>` separator between premise and hypothesis
- **Stopword Filtering**: Removes common English stopwords and special tokens
- **Limited Sample Size**: Analysis based on 50 examples for speed
- **Perturbation Sensitivity**: LIME results may vary with different num_samples settings

## Next Steps for GRACE Framework

1. **Dynamic Retrieval-Guided Attribution (DRGA)**: Implement confidence-based retrieval
2. **Explanation Hallucination Detection**: Build 4-type taxonomy detection
3. **Fairness Auditor**: Add demographic bias detection
4. **Unified Trust Score**: Combine faithfulness + factuality + fairness
