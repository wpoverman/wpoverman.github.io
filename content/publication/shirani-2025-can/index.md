---
title: Can We Validate Counterfactual Estimations in the Presence of General Network Interference?
authors:
- Sadegh Shirani
- Yuwei Luo
- William Overman
- Ruoxuan Xiong
- Mohsen Bayati
date: '2025-02-03'
publishDate: '2025-02-03'
publication_types:
- paper-conference
publication: ''
featured: false
abstract: In experimental settings with network interference, a unit's treatment can influence outcomes of other units, challenging both causal effect estimation and its validation. Classic validation approaches fail as outcomes are only observable under one treatment scenario and exhibit complex correlation patterns due to interference. To address these challenges, we introduce a new framework enabling cross-validation for counterfactual estimation. At its core is our distribution-preserving network bootstrap method -- a theoretically-grounded approach inspired by approximate message passing. This method creates multiple subpopulations while preserving the underlying distribution of network effects. We extend recent causal message-passing developments by incorporating heterogeneous unit-level characteristics and varying local interactions, ensuring reliable finite-sample performance through non-asymptotic analysis. We also develop and publicly release a comprehensive benchmark toolbox with diverse experimental environments, from networks of interacting AI agents to opinion formation in real-world communities and ride-sharing applications. These environments provide known ground truth values while maintaining realistic complexities, enabling systematic examination of causal inference methods. Extensive evaluation across these environments demonstrates our method's robustness to diverse forms of network interference. Our work provides researchers with both a practical estimation framework and a standardized platform for testing future methodological developments.
links:
- name: URL
  url: https://arxiv.org/abs/2502.01106
image:
  caption: 'Evolution of outcomes sample mean (z-axis) with respect to time t and treatment probability p. Red
and blue contours highlight the counterfactual evolutions at treatment probabilities p = 0.25 and p = 0.75,
respectively. The magenta line represents the equilibrium state, where the treatment effect has stabilized.'
focal_point: ''
preview_only: false
---