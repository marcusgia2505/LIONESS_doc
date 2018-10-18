====================
LIONESS experiment
====================

A standard LIONESS experiment can be created in LIONESS Lab and brings along a set of standard features to enable online interactive experiments. The build-in features are described here. They can be configured when developing an experiment. 

The following figure shows the standard flow of an online experiment and describes all the mechanisms along this flow. 

1. Participants log in via a link from an external website (e.g. Amazon MTurk). 
2. Then they go through the experiment and 
3. At the end they return to the external site to get their payoff. 

.. image:: _static/control_flow2.png

LIONESS experiments direct participants their way through the experiment and provide several measures which have been evidenced as being useful for online experimentation.

Principles
===========

For online experimentation (in contrast to normal lab experiments) some principles should be considered which are all implemented in LIONESS expeirments.

1. The basic principle for all this is that participants should be kept active and waiting times should not be too long.
2. Dropout of participants are unavoidable. Measures should be in place to deal with this.
3. Matching and assignment of roles and treatments can only be done on-the-fly and not predetermined as the total number of participants varies.
4. Participants should be able to complete the experiment even if their couterparts dropped out in order to prevent negative feedback by participants which damage the experimenter's reputation.



