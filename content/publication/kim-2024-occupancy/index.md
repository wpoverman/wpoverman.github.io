---
title: 'Occupancy Prediction with Patient Data: Evaluating Time-Series, Patient-Level
  Aggregation, and Deep Set Models'
authors:
- Song-Hee Kim
- William Overman
- Jean Pauphilet
- Won Chul Cha
date: '2024-02-01'
publishDate: '2024-02-01'
abstract: With the growing availability of patient-level data and advanced data analytics tools, hospitals are increasingly looking to develop prediction models that leverage this rich data to improve operational efficiency. This study evaluates different models that use patient-level information to predict Emergency Department (ED) occupancy. We explore three approaches; time-series models that incorporate summary patient information, bottom-up models that aggregate patient-level outcomes, and deep set neural networks that predict occupancy directly from the concatenation of all patient-level information available. Our results show that time-series models, despite their simplicity and relatively low complexity, significantly benefit from the inclusion of summary information about current ED patients, leading to a 15-30% reduction in Mean Absolute Error (MAE). Bottom-up approaches, offering dual-level (patient and ED) predictions, not only improve interpretability, but also significantly improve occupancy prediction accuracy by 35% compared to time-series models. However, to achieve these gains, we show that bottom-up pipelines require an additional calibration step (and careful re-calibration over time). Meanwhile, deep set models show promise with performance between that of time-series and bottom-up models. However, their performance on low-volume days suggests limitations for smaller institutions. This study underscores the potential of patient-level data in predicting ED occupancy and highlights the importance of model selection, calibration, and fine-tuning when using patient-level data to predict ED occupancy.
links:
- name: URL
  url: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4523116
---
