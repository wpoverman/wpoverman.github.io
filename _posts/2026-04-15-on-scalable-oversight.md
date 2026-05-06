---
layout: v2-post
title: "On scalable oversight and the limits of conservative policies"
subtitle: "Why calibrating conservatism matters more than maximizing safety"
category: Research
permalink: /v2/notes/on-scalable-oversight/
---

This is a sample research note to test the post template. Replace with real content.

## The core tension

When we build AI systems that operate under human oversight, we face a fundamental tradeoff: more conservative policies are safer but less useful, while more autonomous policies are useful but harder to verify.

> The question is not whether to be conservative, but how to calibrate conservatism to the stakes of the decision.

## A conformal approach

One way to think about this is through the lens of conformal prediction. We can construct prediction sets that provide coverage guarantees — the model's uncertainty is quantified in a way that's distribution-free.

```python
def conformal_threshold(scores, alpha=0.1):
    """Compute conformal quantile for coverage 1-alpha."""
    n = len(scores)
    q = np.ceil((n + 1) * (1 - alpha)) / n
    return np.quantile(scores, q)
```

The key insight is that we can *trade off* coverage for set size, and this tradeoff maps directly onto the safety-autonomy spectrum.

## What's next

In the next post, I'll explore how this connects to the Oversight Game framework and multi-agent equilibria.
