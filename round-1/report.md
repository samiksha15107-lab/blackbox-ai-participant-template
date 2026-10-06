# round-1 — Observe

**Team:** BB-025
**Queries used:** 49 / budget

## What we concluded
The system evaluates a post and returns an approval score between 0 and 1 along with an APPROVE or DECLINE decision. Our experiments suggest that the output is affected by multiple input features, and the score can change when individual features are varied.
A high score such as 0.9900 resulted in an APPROVE decision in our observed queries.
## How we got there

We tested the available input features individually and in different combinations. The main features explored were:

- account_age_days
- linked_accounts
- mentions
- months_active
- post_length
- reach
- recent_strikes
- report_ratio
- reputation
- surface

We compared the output score and decision after changing the input values. We used repeated queries to identify which changes produced noticeable differences in the result.
We observed that reputation,post_length,surface are associated with a noticeable change in the result and the last reputation value of 300 produced 0.9900/APPROVE.


## What we ruled out
We did not find enough evidence to claim that any single feature completely determines the final decision.
Across our 49 queries, changing different features and their combinations produced different scores and decisions. In particular, changing surface,post_length and reputation changed the score and it provided enough evidence to conclude that these alone doesn't determine the final decision. 
We also ruled out the assumption that a high value in one feature automatically guarantees approval, since both APPROVE and DECLINE outcomes were observed during our experiments.

## What we are still unsure about
We are still unsure about the exact internal formula used to calculate the approval score.
We also cannot yet determine the precise contribution or interaction of every feature from the available 49 queries.
We are still unsure about the exact individual influence of mentions,reach and linked_accounts on the final approval score.
