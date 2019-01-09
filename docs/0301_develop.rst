.. _develop:

=========================
Develop your experiment
=========================

There are two basic ways to develop your LIONESS experiment. You can either start from scratch, or :ref:`build on an existing experiment <build_on_an_existing_experiment>`. The :ref:`repository` contains a range of different LIONESS experiments for you to use and adjust to accommodate your requirements.

Here we describe how to develop your LIONESS experiment from scratch. We describe how to create a new experiment and define your screens. If you have already completed the tutorial, many of the steps described here will look familiar to you. This chapter gives a fuller description of the features that LIONESS Lab has to offer.

Create experiment
=========================

On the LIONESS Lab landing page, you can create a new LIONESS experiment by clicking *new experiment* in the :ref:`top horizontal bar <main_menu>`.

In the next screen you can define basic settings of your experiment by filling out the appropriate screens.

.. image:: _static/New_game.png
   :alt:  300px


With the drop-down menu under *availability* you can choose to keep  experiment private, or to share it with other LIONESS Lab users by making it *public*. Other users will be able to copy public experiments from the :ref:`repository <repository>`  to their LIONESS Lab accounts and edit these for their own purposes. Experiments' settings can be adjusted at any time.

With the input fields on the right you can give additional information on your experiment (e.g. you can use the comments section to list the number of sessions run with this experiment, or add any caveats you might have). This information can then be used by other LIONESS Lab users that might want to build on (parts of) your experiment.

Defining your screens
=========================

Your screens consist of three sections: *settings*, an *active screen* and a *waiting screen*.

.. image:: _static/Three_sections.png
   :alt:  1300 px
   :align: center

Stage settings (top panel)
--------------------------

In the top horizontal bar, you can give the stage a name, and define its :ref:`type <stage_type>`: (:ref:`standard <stage_type__standard>`, :ref:`quiz <quiz>` or :ref:`lobby <lobby>`). Also, you can add an :ref:`optional timer <stage_and_element__countdown_timer>`.


.. _defining_your_screens__active_screen:

Active screen (left panel)
--------------------------

The active screen is the main screen of a stage. Typically, this section will be used for displaying information (e.g. instructions, results from previous periods) and recording participants' responses.

You can build up these screens step-by-step using :ref:`elements <elements>`. You can add these elements by clicking the button *add new element* and paste it in the place you want. On the participant screens, elements will in principle be placed below each other, in the order you define them in your LIONESS Lab screen.
Typically, the final element of an active screen is a :ref:`button <elements__button>`, that submits any responses of the participant in that screen, and directs them to the next screen. In this button, you can also define whether the participants can move on to the next screen as soon as they have finished, or whether they have to wait for their groups mates to also finish this screen. In the latter case, participants will be directed to the Waiting screen of this stage (see
below).


.. _defining_your_screens__waiting_screen:

Waiting screen (right panel)
----------------------------

In case you allow participants to move to the next stage only when all group members have completed the stage (by setting the *proceed* condition in the active screen :ref:`button <elements__button>` to *wait for others*), participants will be directed to the Waiting screen of the stage.

You can add :ref:`elements <elements>` to the Waiting screen in the same way as you add them to the Active screen. If you do not define any element there, the Waiting screen will show a default text indicating that participants should wait for all group mates to complete.


Setting parameters
=========================

For testing (and running) your experiment, you need to set the experiment :ref:`parameters <parameters>`. Make sure that the :ref:`loopStart <parameters__loopstart>` and :ref:`loop end <parameters__loopend>` parameters are set to the stages that mark the beginning and end of a period, respectively. The full list of parameters together with an explanation can be found :ref:`here<parameters>`.

.. _build_on_an_existing_experiment:

Build on an existing experiment
===================================

Go to the :ref:`repositiory <repository>` and import an existing experiment. Any experiment that was made public can is shared with, and can be imported by, other experimenters. After importing an experiment it will be visible in your landing page with the overview of your experiments. If you want to the imported experiment,you have to make a copy of it. To do this, click *View* next to the experiment on your landing page. In the experiment's page, you will see you cannot edit the experiment as it was created by another user. Click *experiment* in the top bar, and then *copy experiment*. An editable copy of the experiment will be created in your account.


.. _experimental_flow:

Experimental Flow
==========================
A standard LIONESS experiment created in LIONESS Lab and brings along a set of standard features to enable online interactive experiments. The build-in features are described here. They can be configured when developing an experiment. This section provides an overview over the general functioning of a LIONESS experiment. The following figure shows the standard flow of an online experiment and describes all the mechanisms along this flow.

1. Participants log in via a link from an external website (e.g. Amazon MTurk).
2. Then they go through the experiment.
3. At the end they return to the external site to get their payoff.

.. image:: _static/control_flow2.png

The blue arrows show the normal flow of the experiment. The red arrows show possible dropouts. The euro symbol shows if a show up fee is paid on dropout or not. The blue lines around the stages mark the boundaries of a LIONESS experiment.

When participants arrive from the external site, they are registered and get a player number. Then they go to the first stage of the experiment. After that a quiz may follow where, participants have to answer control questions in order to participate. The quiz is optional. After passing the quiz, participants wait in the lobby to be matched to a group. This is optional for single player games. Then participants make their decisions (maybe over several rounds) before they are informed about their payoff (end). From there they are directed back to the external site they came from. On the way through the experiment, LIONESS experiment handle all kind of possible dropout issues, which are described in the following.

.. note:: On dropout participants receive different standard messages, which can be customized in the parameters. For all list of all messages see also :ref:`here <parameters__messages>`. All messages refer to the terminology HIT which is a task on Amazon MTurk.

a) Internet Explorer
----------------------

LIONESS experiment (and many other modern web applications) do not support the Internet Explorer as it is outdated. Experimenters should inform their participants that they cannot participate if the use the Internet Explorer. If participants use the Internet Explorer, they are informed that they cannot participate in the experiment with the following message:

.. warning:: As indicated in our HIT text on MTurk, our HIT does **not** support Microsoft Internet Explorer.                         Please return this HIT. We apologize for any inconvenience caused.

Participants can return with a different browser as they were not registered with their IP address in the LIONESS experiment yet.

b) Task not active
----------------------

As an experimenter you can set the task inactive or active at any time in the control panel. If the task is inactive, new participants cannot enter and receive the following message:

.. warning:: This HIT is currently offline. You cannot participate at this time.

Participants who are already in the game can complete the game.


c) Double login
----------------------

LIONESS experiments record the IP addresses in an anonymized way to protect personal data. With the anonymized IP addresses it can be checked if two participants log in from the same IP address. The actual IP address cannot be retrieved.

If a second participant tries to log in from the same IP address, he or she receives the following message and cannot enter.

.. warning:: According to our records, your device has already been connected to the server during this session.                Participants are only allowed to enter a session once. Thank you for your understanding.

The IP address check is **deactivated** when test mode is on.

.. note:: LIONESS experiments do their best to prevent double participation by IP address check and cookies in the browser. Some of these measures can still be circumvented with some effort. If you want to be 100% sure that participants only participate once they should be provided with a ticket or unique ID which they have to enter during the experiment.
 If you think that your participants may use the same IP address you may switch to test mode. Otherwise they cannot enter. This may happen if e.g. all participants play in the same network.

d) Session full
----------------------

In this parameter the total number of players can be specified. If enough players entered the game, further participants cannot enter anymore and receive the message:

.. warning:: We have sufficient participants for this HIT. Unfortunately, you cannot participate at this time.                Thank you for your understanding.

If you increase the total number of players during the experiment, more participants are allowed to enter.

.. note:: The number of participants are counted at the beginning of the experiment. It also includes participants who started the game but dropped out according to reasons f), g), i), j) and k). This means you should choose a number that is larger than the actual number of participants that you need.

e) Not registered
----------------------

If a participant tries to participate in a LIONESS experiment by navigating to a stage in the experiment without being registered he or she is informed about that.

.. warning:: You are currently not logged in. You cannot participate in the HIT.

Entrance to an experiment is only possible via the first stage where participants are registered.

f) Time out
----------------------

In each stage, you can define a maximum time participants have to complete the stage. This is useful to keep up the pace of the experiment. If a participant does not finish in time, he or she can be directed towards a different stage in the game or to the standard time out page which shows the following message:

.. warning:: You did not make a decision before the time was up. You have been removed from the HIT.                         You can close down this window.

g) Kicked out by experimenter
--------------------------------------------

In the control panel, experimenters can kick out participants by entering their player number. They receive the following message and get their show-up fee. The values between $ signs are filled by the values set in the parameters.

.. warning:: Unfortunately, this HIT was terminated for a technical reason! You cannot continue. You will receive your guaranteed participation fee of $ $participationFee$. To collect your earnings, please fill out this random code on MTurk:
                **$randomid$** Once you have filled out this code, you can close this window.
                Thank you for your participation.


.. note:: This features should be used with care. It is mainly intended when technical problems appear.

h) No re-entering possible
--------------------------------------------

If participants try to re-enter after being kicked out, they are also informed that they cannot participate in the experiment anymore.

.. warning:: You are currently not logged in. You cannot participate in the HIT.

.. note:: This information that a participant has been kicked out is based on the IP address (if the test mode is switched off) and a cookie in the browser. If the participant uses a different browser from a different IP address he or she can still enter as a new participant.

i) Too many quiz errors
--------------------------------------------

In the quiz stage, the experimenter can specify a maximum number of quiz failures. It the participant fails more than that, he is excluded from the experiment and receives the following message:

.. warning:: You did not answer the quiz correctly and were excluded from further participation.

j) No group match
----------------------

In the lobby, participants wait until they are matched for a certain time span. If there is no other participant within this time span, the participant is directed to a page where he or she can choose to wait additional two minutes or to leave the experiment. In the latter case the participant should receive the show up-fee. The experimenter can set to which stage the participant is directed when he or she leaves.

k) Group aborted
----------------------

In the parameter setting the experimenter can choose what happens if during the decision phase a participant drops out. If the experimenter opts for *terminate group*, all players of the group are kicked out of the experiment and receive the following message:

.. warning:: Unfortunately, one of the players in your group dropped out of the HIT! You cannot continue. You will receive your guaranteed participation fee of $ $participationFee$. To collect your earnings, please fill out this random code on MTurk: **$randomid$** Once you have filled out this code, you can close this window. Thank you for your participation.

For the different options on drop outs in a group see :ref:`dropout handling <parameters__dropouthandling>`.

