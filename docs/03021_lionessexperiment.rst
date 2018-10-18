====================
LIONESS experiment
====================

A standard LIONESS experiment can be created in LIONESS Lab and brings along a set of standard features to enable online interactive experiments. The build-in features are described here. They can be configured when developing an experiment. 

.. note:: This section provides an overview over the general functioning of a LIONESS experiment. It does not discuss the details of how to implement these things. The details can be found in :ref:`the develop section <develop>`.

Principles
===========

For online experimentation (in contrast to normal lab experiments) some principles should be considered which are all implemented in LIONESS expeirments.

1. Minimize dropouts if possible! 
2. The basic principle for all this is that participants should be kept active and waiting times should not be too long.
3. Dropout of participants are unavoidable. Measures should be in place to deal with this.
4. Matching and assignment of roles and treatments can only be done on-the-fly and not predetermined as the total number of participants varies.
5. Participants should be able to complete the experiment even if their couterparts dropped out in order to prevent negative feedback by participants which damage the experimenter's reputation.

Experimental Flow
==================

The following figure shows the standard flow of an online experiment and describes all the mechanisms along this flow. 

1. Participants log in via a link from an external website (e.g. Amazon MTurk). 
2. Then they go through the experiment. 
3. At the end they return to the external site to get their payoff. 

.. image:: _static/control_flow2.png

The blue arrows show the normal flow of the experiment. The red arrows show possible dropouts. The euro symbol shows if a showup fee is paid on dropout or not. The blue line around the stages mark the boundaries of a LIONESS experiment.

When participants arrive from the external site, they are registered and get a player number. Then they go to the first stage of the experiment. After that a quiz may follow where, participants have to answer control questions in order to participate. The quiz is optional. After passing the quiz, participants wait in the lobby to be matched to a group. This is optional for single player games. Then participants make their decisions (maybe over several rounds) before they are informed about their payoff (end). From there they are directed back to the external site they came from. 

On the way through the experiment, LIONESS experiment handle all kind of possible dropout issues, which are described in the following.

.. note:: On dropout participants receive different standard messages, which can be customized in the paramters. For all list of all messages see also :ref:`here <Reference manual>`. All messages refer to the terminology HIT which is a task on Amazon MTurk.

a) Internet Explorer
---------------------

LIONESS experiment (and many other modern web applications) do not support the Internet Explorer as it is outdated. Experimenters should inform their participants that they cannot participate if the use the Internet Explorer. If participants use the Internet Explorer, they are informed that they cannot participate in the experiment.

.. attention:: As indicated in our HIT text on MTurk, our HIT does **not** support Microsoft Internet Explorer.                         Please return this HIT. We apologise for any inconvenience caused.

b) Task not active
-------------------

c) Double login
----------------

d) Session full
----------------

e) Not registered
-------------------


f) Time out
-------------

g) Kicked out by experimenter
-------------------------------

h) No re-entering possible
---------------------------


i) Too many quiz errors
-------------------------

j) No group match
------------------

k) Group aborted
------------------



