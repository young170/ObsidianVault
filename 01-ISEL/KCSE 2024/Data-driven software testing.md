very solid motivation
a "higher" higher level overview: ParaDySe

1. manual features for scoring **branch** paths
	1. combined with weights
2. how are the weights computed?
	1. randomly refine the random range of the weights that apply to the feature vectors

Extended this work by viewing states instead of branches

2nd paper's motivation:
review of the 1st paper: is your approach's coverage the superset? or are there unique coverages?
* found out not a perfect superset
* switch among strategies

3rd paper
automate parameters
* also did "additional" research to find out what parameters were more impactful
* found it was different for every target
* this firmly establishes their research that considering multiple criteria leads to better results

3.5th paper
DL - neurons
white-box testing and neuron-selection strategy
### etc.
This researcher is continuing on this flow of research. His most recent paper is essentially the same idea applied to a different field.
* machine-guided
	1. feature
	2. random
	3. refine
Also, the researches' motivations are really solid
* especially, symtuner, found other researchers simply used the default params.

Kinda interesting to see he didn't mention this approach is also useful for extendibility
* if a new heuristic-based approach is introduced -> integrate to this approach
* maybe it's mentioned in the paper? check.

Really good at identifying problems
* the extraction of the features (feature engineering) is still manual

Big Idea:
Let's automate
* conventional + hand-written -> data-driven machine-tuned

presentation:
simple icons but crowded + small labels : poor choice

### Paper links
ParaDySe: [Automatically Generating Search Heuristics for Concolic Testing](http://acm.mementodepot.org/pubs/proceedings/acmconferences_3180155/3180155/3180155.3180166/3180155.3180166.pdf), ICSE '18
Chameleon: [Concolic Testing with Adaptively Changing Search Heuristics](https://prl.korea.ac.kr/papers/fse19.pdf), FSE '19
SymTuner: [SymTuner: Maximizing the Power of Symbolic Execution by Adaptively Tuning External Parameters](https://seokhyunlee.info/papers/icse22-symtuner.pdf), ICSE '22
DL: [Effective White-Box Testing of Deep Neural Networks with Adaptive Neuron-Selection Strategy](https://seokhyunlee.info/papers/issta20-adapt.pdf), ISSTA '20