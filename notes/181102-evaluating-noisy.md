# Evaluating model performance with noisy, partially observed ground truth
**Moderators:** Alex Paino and Yuan Zhuang from [Sift Science (S11)](https://siftscience.com/)  
**Blurb**: We'll focus on how Sift evaluates model accuracy, both in offline experiments and in production. This is an active area of development for us so we would be curious to hear about others' experiences here. If we have time, we can also share other details of Sift's ML (e.g. handling highly sparse features, safely shipping new models on a regular cadence, using deep learning to model user behavioral sequences, explaining predictions, etc.).  
**Slides**: http://go.siftscience.com/sift-yc-aml  
**Keywords**: evaluation, noisy labels

---

## Ground truth problems
* Noisy
  * _Source_: Manual review-- Labeled by human fraud analysts
    * Covers _false positives_ and _true positives_    
  * _Mitigation_: 
    * Global models over all customers, smooth out customer-specific issues
    * Better tools for manual review by showing analyst accuracy, hierarchies for escalating uncertain scenarios
* Delayed:
  * _Source_: Chargebacks-- Requires 90 days from payment processor
    * Covers _false negatives_
  * _Mitigation_:
    * Offline ML experiments
* Incomplete: 
  * _Source_: Customer complaints- rare event!
    * Only source that covers _false positives_
  * _Mitigation_: 
    * Capture decisions via workflows (automation product for auto-blocks, manual review, etc.)
    * Allow some auto-blocked to complete to measure true distribution

## Running ML experiments correctly
* Train/test set creation
  * Watch for class skew!
  * Don't use random splits -- watch out for disjoint sets in time + users
* Avoid leaking ground truth into features
  * Version external data sources
* Parity with online system
  * Use same code paths for offline/online learning

## Model accuracy
* In Sift setting, Partial-AUC is better fit than AUC because it tailors evaluation towards customer interest!
* At a higher-level, evaluate by considering the $$ value of a model
  * How much cost does this model cut?

## Interesting questions
* What's the role of open-source in noisy evaluation?
* What's the gap between offline/online metrics?
* What is the timeline for backfilling data sources?
