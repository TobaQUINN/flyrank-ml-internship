# RESEARCH QUESTION

Can we predict which content pages are likely to decline in organic performance during a future time window using only information available from an earlier time window?

The objective is to identify pages at risk before performance drops so that SEO and content teams can intervene proactively rather than react after traffic has already been lost.


# Why This Lane?

Search performance naturally changes over time. Some pages steadily gain momentum, while others gradually decline because of changing search demand, competition, or content freshness.

If we can estimate which pages are most likely to decline, teams can prioritize updates instead of reviewing thousands of pages manually.

This problem is well suited for my supervIsed machine learning background because many interacting factors may contribute to future performance, making it difficult to capture with a simple hand-written rule.


# Unit of Analysis

The primary unit of analysis is a content page.

Each observation represents one page described by its historical SEO, traffic, engagement, and content characteristics.

Features will come from a prior observation window (for example, the previous 90 days), while the prediction target will describe what happens during a future window (for example, the next 30 days).


# Decision

Which pages should the SEO team review first?

The model does not decide how to improve a page.


# Model Output

The expected output is a probability that each page will decline during the future prediction window.

Pages can then be ranked from highest risk to lowest risk.

Example:

Page A → 91% chance of decline

Page B → 73% chance of decline

Page C → 12% chance of decline

The final product is therefore a ranked review queue rather than a simple yes/no prediction.


# Action

The predictions can support several actions:

- refresh outdated content
- improve internal linking
- update keywords
- improve content quality
- prioritize editorial review

Rather than reviewing every page equally, the SEO team can focus first on pages with the highest predicted risk.


# Why Machine Learning?

Before choosing machine learning, it is important to consider whether a simple rule could solve this problem.

One possible heuristic is:

> "Flag any page whose impressions have decreased by at least 20% over the last 30 days."

This rule is easy to understand, inexpensive to implement, and may work reasonably well in some situations.

However, future page performance is unlikely to depend on a single metric. Decline may result from interactions among search demand, user engagement, content characteristics, competition, and historical trends. These relationships may differ across clients and change over time.

As more conditions are added to improve the rule, it becomes increasingly complex, harder to maintain, and more difficult to adapt as search behaviour evolves.

A machine learning model can learn these relationships directly from historical data and estimate the probability of future decline using many signals simultaneously.

The goal is not to replace simple heuristics automatically, but to determine whether a predictive model provides enough additional value to justify its increased complexity.


# Evidence From the Starter Dataset

The starter dataset contains 30,000 observations across 32 clients. 
The average number of search impressions per page over the 90-day window is approximately 5,200.
Together with the observed spread in traffic and engagement metrics, this suggests that page performance varies substantially across content pages.

These differences indicate that page performance is not uniform and that historical information contains potentially useful signals for prioritizing future review.

While this dataset is not sufficient to predict future decline directly, it demonstrates that page-level behavior varies enough to justify exploring predictive models using a warehouse dataset with proper time windows.


# Why This Is More Than Training a Model

This project is fundamentally a decision-support problem rather than a modeling exercise.

The objective is to help SEO teams decide which pages deserve attention first.

Success depends not only on predictive performance, but also on:

- preventing information leakage
- defining a realistic prediction window
- evaluating ranked recommendations using Precision@K
- communicating uncertainty
- understanding what the model can and cannot claim

A highly accurate model trained with future information would be misleading and unusable in practice. Careful problem framing and validation are therefore as important as model selection.


# Next Steps

During the coming weeks I plan to:

1. Define a leakage-free prediction target.
2. Engineer historical features from prior time windows.
3. Establish a simple rule-based baseline.
4. Train and compare several classification models.
5. Evaluate ranked recommendations using Precision@K and calibration.
6. Document the limitations and practical use of the model.

This lane remains provisional until Week 4, when additional evidence from the warehouse dataset may justify refining or changing the prediction task.
