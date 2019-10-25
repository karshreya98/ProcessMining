# SeminarProcessMining
The following code is a python based implementation which shows Monte Carlo based simulation to predict the remaining time for a process, based on the work of Andreas Rogge-Solti and Mathias Weske presented in the paper "Prediction of Remaining Service Execution Time Using Stochastic Petri Nets with Arbitrary Firing Delays".The following code is a simple implementation catering only to this example. However, it still provides a foundation for the possibility of the proposed prediction algorithm being implemented as an open source plugin in the python based process mining library(pm4py).I presented this as a part of a pro seminar I did in my Masters course at the Process and Data Science Chair, RWTH Aachen University.

Firstly, lets go over the running example. Here,an airline customer seeks for a compensation on account of a ﬂight delay. The request either gets accepted to be handled with probability of 0.7 or rejected with a probability of 0.3. The GDT SPN model associated with this example is shown in Fig 1.

![Alt text](/pnet1.PNG?raw=true "Title")

Assuming that the activity with higher probability(handle case) was chosen, we will calculate the remaining process time for this particular case. From the token in the petri net we can see that the current state of the trace is that the event ”examine claim for compensation” was already executed. Let current time be t0 = 4.5s and number of iterations be 2n = 40 for Monte Carlo simulation. In each iteration we will draw a sample from the truncated duration distribution of the ”handle case” transition, which is normal with a mean value of 5 and standard deviation 1. In order to obtain a sample from truncated normal distribution, rejection sampling is used. At the end of all iterations the mean i.e nth sample is returned. The code snippet for that is as follows:
![Alt text](/py1.PNG?raw=true "Title")

Then the truncated distribution of the transition is plotted through the following code.
![Alt text](/py2.png?raw=true "Title")

![Alt text](/pic_3.png?raw=true "Title")

From the above plot we can deduce that the remaining process time is an estimated 9 days.


