# Low-Precision Training of Deep Neural Networks
**Moderator:** Jack Kendall from [Rain Neuromorphics (S18)](http://rain-neuromorphics.com/)  
**Blurb**: _Who should come?_ Anyone interested in low precision training, compact models, and Deep Bayesian networks. _Why should you care?_ Low precision networks make better use of hardware resources, and scale more efficiently than high precision networks  
**Reading**: ["Quantized Neural Networks" by Daniel Soudry's group and Yoshua Bengio](http://www.jmlr.org/papers/volume18/16-456/16-456.pdf)  
**Slides**: https://docs.google.com/presentation/d/11e5pPLYPugwEycadpaiFLmHTUj3UC4lv6l-GP3BGY9k/edit?ts=5bfddf28  
**Keywords**: training, low-precision, hardware

---

## Why low precision?
* Hardware trends << performance per compute trends
* Half-precision (16-bits) gives little to no reduction in accuracy using standard techniques: [[S. Gupta et al (2015)](https://arxiv.org/pdf/1502.02551.pdf)]


## Current approaches
* Stochastic rounding - trade bias for variance by stochastically rounding up or down
* Straight-through estimator - backprop through the identity function [Y. Bengio et al (2013)](https://arxiv.org/abs/1308.3432) -- works surprisingly well!
* Bit-shift operations -- approximate ops with big speed-ups by replacing multiplications with bit shifts

## Quantized Networks
* Paper discussion -- achieve nice results on ImageNet for training low precision networks
* Implications for power-constrained environments!

## Interesting questions/discussion
* Should you switch precisions at train/test time?
* For chip/programming framework designers: what primitives make sense as levels as abstractions to users?
