# round-4 — Reconstruct

**Team:** BB-025
**Queries used:** 75 / 170

## What we concluded
We concluded that the black-box system can be approximated by an ML model that learns relationships between the given input features and the resulting score/decision. We reconstructed and trained a similar model to reproduce the observed behavior.
The most significant observation is the strong dependence on the surface type: even with identical numerical inputs, the score drops from 0.9900 on surface D to 0.0560 on surface C, resulting in a 0.9340 difference caused by changing just one categorical variable.
At the same time, controlled post_length experiments show a clear monotonic increase from 0.9411 → 0.9695 → 0.9865 → 0.9897 as length increases from 26.5 → 50 → 85.5 → 100.

## How we got there
We analyzed the available Round 1 and Round 2 query results, identified important input features and their relationship with the outputs, and used them to train an ML model. We then evaluated the trained model using the queries given to check its predictions.
We analyzed the effect of surface while keeping the entire numerical configuration unchanged. The resulting scores were:
- A: 0.9872
- B: 0.9876
- C: 0.0560
- D: 0.9900

This comparison revealed the most significant change in behavior across the observed dataset. The result for surface C is especially notable, as its score falls sharply while the other three surfaces remain close to 0.99.
By combining these observations, we were able to identify the overall pattern of the decision surface instead of simply matching individual output values.
## What we ruled out
We ruled out simple assumptions that a single input feature determines the output. We also ruled out relying only on manually defined rules, as the output appears to depend on multiple features together.
Controlled tests showed effectively no measurable score movement for linked_accounts, mentions, and report_ratio within the tested region. For example, changing mentions between 0, 3, and 6 retained a score of approximately 0.9900.
We also ruled out a purely smooth numerical explanation. Such a model cannot explain the transition from 0.9900 to 0.0560 when only surface changes.
Most importantly, we did not treat the high scores around 0.99 as evidence that the system simply approves everything. The existence of the surface-C cliff and the lower-score numerical probes demonstrates that the system contains distinct regions of behavior.

## What we are still unsure about
We are still unsure about the exact internal model, feature weights, and hidden decision logic used by the original black-box system. Our model is an approximation based on the observations available to us, so some hidden relationships may still differ from the original model.
