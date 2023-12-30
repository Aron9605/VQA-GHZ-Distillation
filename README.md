# VQA-GHZ-Distillation

This project contains the reproduction of essential results of the '*Training iterated protocols for distillation of GHZ states with variational quantum algorithms.*' article. [ref. [	arXiv.2311.04646](https://doi.org/10.48550/arXiv.2311.04646
)]

The study has been submitted to a scientific journal; the corresponding authors are **Aron Rozgonyi**[1,2], **Gabor Szechenyi**[1,2], **Orsolya Kalman**[2] and **Tamas Kiss**[2].

*Affiliations*:

[1] Institute of Physics, [Eotvos Lorand University](https://www.elte.hu/en/), Budapest, Hungary

[2] Department for Quantum Optics and Quantum Information, [HUN-REN Wigner Research Centre for Physics](https://wigner.hu/en/news), Budapest, Hungary

## Abstract

We present optimized distillation schemes for preparing Greenberger-Horne-Zeilinger (GHZ) states. Our approach relies on training variational quantum circuits with white noise affected GHZ states as inputs. Optimizing for a single iteration of the scheme, we find that it is possible to achieve an increased fidelity to the GHZ state, although further iterations decrease the fidelity. The same scheme, acting on coherently distorted pure-state inputs, is effective only in certain special cases. We show that radically different results can be achieved, however, when one optimizes for the output after two iterations of the protocol. In this case, the obtained schemes are more effective in distilling GHZ states from inputs affected by white noise. Moreover, they can also correct several types of coherent pure-state errors.
