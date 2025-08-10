# SNLI LIME Explanation Analysis Report

## Executive Summary

**Dataset**: SNLI (Stanford Natural Language Inference)  
**Model**: roberta-large-mnli  
**Analysis Date**: 2025-08-11  
**Total Examples**: 50  
**Git Hash**: 41a0e17f  

### Key Results
- **Model Accuracy**: 0.380 (19/50)
- **Average Confidence**: 0.943
- **LIME Parameters**: 1000 samples, 10 features
- **Random Seed**: 42

## Attribution Metrics Results

### Faithfulness, Sufficiency, and Comprehensiveness

| Metric | Mean | Std | Min | Max | 95% CI |
|--------|------|-----|-----|-----|--------|
| Faithfulness | 0.171 | 0.163 | 0.000 | 0.627 | [0.127, 0.218] |
| Sufficiency | 0.538 | 0.124 | 0.000 | 0.804 | [0.504, 0.570] |
| Comprehensiveness | 0.122 | 0.203 | -0.412 | 0.627 | [0.066, 0.177] |

## LIME Configuration

- **Number of Samples**: 1000
- **Number of Features**: 10
- **Top-k Tokens for Metrics**: 3
- **Chunk Size**: 64

## Qualitative Examples

### Top Correct Predictions

**Example 1** (Confidence: 0.998)
- **Premise**: Five kids are on a yellow ride at the amusement park.
- **Hypothesis**: The kids are having fun on the ride.
- **Predicted**: neutral
- **Top Attributions**: fun(0.400), ride(0.104), amusement(-0.094), park(0.088), Five(-0.045)

**Example 2** (Confidence: 0.998)
- **Premise**: A group of produce buyers inspecting fresh produce.
- **Hypothesis**: The people are looking at tomatoes.
- **Predicted**: neutral
- **Top Attributions**: tomatoes(0.561), produce(0.091), people(-0.029), buyers(0.017), group(0.014)

**Example 3** (Confidence: 0.998)
- **Premise**: People are watching a boy on a skateboard at the top of a skate ramp.
- **Hypothesis**: People are watching a boy on a skateboard at the top of a skate ramp before he attempts to break a world record.
- **Predicted**: neutral
- **Top Attributions**: break(0.047), record(0.043), People(0.036), attempts(0.029), skateboard(0.019)

### Top Incorrect Predictions

**Example 1** (Confidence: 1.000)
- **Premise**: A young man is participating in a competitive gun shooting event.
- **Hypothesis**: The young man is asleep at home.
- **True**: contradiction, **Predicted**: contradiction
- **Top Attributions**: asleep(-0.103), home(-0.092), man(-0.040), gun(-0.025), shooting(-0.017)

**Example 2** (Confidence: 0.999)
- **Premise**: A little girl wearing a yellow dress moves frantically in front of a crowded baseball stadium.
- **Hypothesis**: Everything is calm at the stadium.
- **True**: contradiction, **Predicted**: contradiction
- **Top Attributions**: calm(-0.371), frantically(-0.062), Everything(0.056), moves(-0.039), crowded(-0.035)


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
