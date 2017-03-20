# romanian_noise_tests
Samples and visualization of a small test for speech synthesis - description below.

Listen on youtube in this playlist: https://www.youtube.com/watch?v=_Yaf2uETvHg&list=PLRMa_gJ8vx8kS72M3idtwB-honoArlkAR&index=1

![chart_goes_here](https://raw.githubusercontent.com/kastnerkyle/romanian_noise_tests/master/romanian_multispeaker_noise_chart.jpg)

Cost here is MSE over a 63 dimensional vector. Details can be seen in our workshop paper for char2wav http://josesotelo.com/speechsynthesis/ . Training with noise is a key part of getting this model to work, so studying noise annealing is something I have been working on. 


Note that some of the weird noises at the tail are due to me letting the generations "continue" long after they travel beyond the end of the conditioning text. This is fixed by the "stop heuristic" from Graves' Generating Sequences with Recurrent Neural Networks (https://arxiv.org/abs/1308.0850) but I prefer hearing the full output for debugging - and sometimes it is quite funny.

In all cases, we use mean 0. noise, with varying standard deviations.

I sampled at many different values of the noise, these different values correspond to the different stages of training and the bumps in the graph. The final stage is a standard deviation of 0. This is a weird concept, but with the ``noisydata = data + std * randn()`` formulation it just means we don't add noise.

Note that these stages correspond to *training noise* - at sampling time we always have 0 noise, and *sampling* in this model is not stochastic - we always take the prediction from the output layer, which is also the mean of some gaussian with fixed variance when viewed as a mixture density network.

This curve represents about 2 weeks of training - 125 epochs at about 9000 seconds an epoch, or 312.5 hours, or 13.02 days.

sample_0_* is a sample that is generally good for all 3 speakers, there is a bit of fluctuation in the start/cutoff due to the voice up/down detector I am using and the unreasonably weird noises the vocoder tends to make at the end.


sample_6_* is a sample that is generally bad for all speakers - it seems like the attention stops working at the tail end to comedic effect.


Videos made with this script: https://gist.github.com/kastnerkyle/d8205ff521dbee3061d9b5ccd3dde8f8
