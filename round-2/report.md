# round-2 — Investigate

**Team:** BB-025
**Queries used:** 32/ budget

## What we concluded
1.Reputation, on decreasing -increased approval score
2.Post-length,on increasing -increased approval score
3.reach,on decreasing-increased score
4.linked_accounts-not influenced the score
5.mentions-not influenced the score
6.report_ratio-not influenced the score
## How we got there
We used controlled experiments by changing selected input values while keeping the other values constant.

1. Reputation and reach
   decreasing reputation improved the score, while increasing reach reduced the score.

2. Reputation and Recent Strikes
   Higher reputation increased the score, whereas increasing recent strikes reduced the score.

3. Account Age and Months Active
   Increasing account age and decreasing months active generally resulted in a higher approval score.

These experiments helped us identify the important positive and negative factors affecting the hidden model.

## What we ruled out
We ruled out the assumption that every input has the same influence on the final score. Our experiments showed that some variables have a much stronger effect than others.
We also ruled out relying only on real-world intuition because the challenge uses a synthetic black-box system

## What we are still unsure about
We are still unsure about the exact mathematical formula used by the hidden model and whether some variables interact with each other. We also cannot determine the exact contribution or threshold of every feature from the limited query budget.
