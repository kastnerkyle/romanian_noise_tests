# romanian_noise_tests
Samples and visualization of a small test for speech synthesis.

Cost here is MSE over a 63 dimensional vector. Details can be seen in our workshop paper for char2wav http://josesotelo.com/speechsynthesis/ . Training with extremely high levels of noise is a key part of getting this model to work, so studying annealing the noise is something I have been working on. 

Note that most of the weird noises at the tail are due to me letting the generations "continue" long after they travel beyond the end of the conditioning text.


I sampled at each of 5 stages: noise std 4. (the primary curve), noise std 3. (first step down), noise std 2. (next), noise std 1. (next), noise std .5 (next), noise std 0. (last)

This curve represents about 2 weeks of training - 125 epochs at about 9000 seconds an epoch, or 312.5 hours, or 13.02 days.

sample_0_* is a sample that is generally good for all 3 speakers, there is a bit of fluctuation in the start/cutoff due to the voice detector I am using and the unreasonably weird noises the vocoder tends to make.

sample_6_* is a sample that is generally bad for all speakers - it seems like the attention stops working at the tail end to comedic effect.

![chart_goes_here](https://raw.githubusercontent.com/kastnerkyle/romanian_noise_tests/master/romanian_multispeaker_noise_chart.jpg)
