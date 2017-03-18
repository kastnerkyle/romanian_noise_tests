# romanian_noise_tests
Samples and visualization of a small test for speech synthesis

I sampled at each of 5 stages: noise std 4. (the primary curve), noise std 3. (first step down), noise std 2. (next), noise std 1. (next), noise std .5 (next), noise std 0. (last)

This curve represents about 2 weeks of training - 125 epochs at about 9000 seconds an epoch, or 312.5 hours, or 13.02 days.

sample_0_* is a sample that is generally good for all 3 speakers, there is a bit of fluctuation in the start/cutoff due to the voice detector I am using and the unreasonably weird noises the vocoder tends to make.

sample_6_* is a sample that is generally bad for all speakers - it seems like the attention stops working at the tail end to comedic effect.

![chart_goes_here]()
