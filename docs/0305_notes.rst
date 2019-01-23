.. _notes_experimental_design:

============================
Notes on experimental design
============================

Based on running numerous experiments online, we suggest that LIONESS experiments follow a basic structure with the components in the order listed below. Each component may be one stage (as is the case in the :ref:`quick start <basic>`), but can of course be expanded to include multiple stages. Here we briefly discuss these components, and as we go along we describe some aspects you might want to consider when designing your online experiment. A methodological discussion of running interactive experiments online can be found in `this paper <https://link.springer.com/article/10.1007/s10683-017-9527-2>`__.  

The most important methodological issue with running interactive experiments online is the possiblity of dropouts. As mentioned elsewhere, LIONESS experiments have a number of built-in measures to drive down dropouts. A smart design for your online experiment can help drive down dropouts even further. As a general rule, experimental designs likely to produce a smooth data collection online are simple, short, and done in small groups. 

This section can be seen as a practical guide that helps developing such a smart design. It mostly includes notes on the use of LIONESS experiments with participants recruited from MTurk.

Instructions
============

At the beginning of your experimental task, you have to tell the participants what is expected from them. Apart from explaining the task they are about to complete, this is a good place to inform them about the duration of the experiment, as well as the earnings they may expect. Being clear about these things helps avoiding disappointment on the part of participants. If expectations are not met, online participants may discuss this on forums like `turkopticon <https://turkopticon.ucsd.edu/>`__. This may damage the reputation of your (or your institute's) account used for administering experiments online. In addition, it is often useful to inform participants that they will only get paid if they complete the task until the end.

Quiz
============

One big difference between online sessions and sessions in the laboratory is that you, as an experimenter, are not physically present. This means that participants cannot ask any questions to clarify the instructions. To ensure that participants understand their instructions, it is useful to introduce a set of compulsory comprehension questions, before they proceed to the lobby. You can make responses to input elements compulsory by clicking the *required* switch inside the element. You can set a target value for an input element in the parameter field *correct value*.

For each participant, LIONESS experiments will automatically record the number of attempts for each quiz item. This is stored in the :ref:`session table <experiment_tables__session>`.

Lobby
============

To reduce waiting times as much as possible, you can place the :ref:`lobby <lobby>`. after the comprehension questions. This ensures that participants in the lobby understand the game and are matched as soon as sufficient participants are ready to start interacting. By default, the lobby of LIONESS experiments will display the number of participants currently necessary to form a group.

Note that the risk of participant :ref:`dropout <parameters__dropouthandling>` increases when participants have to wait on others (in this case, for their group to be formed). It is therefore important that waiting times are minimized. For smooth group formation, participants should enter the lobby at a decent rate.

This means that participants should enter your experiment at a decent rate to begin with (this is why Amazon MTurk can work well as a platform for recruiting participants; the sheer size of the pool of potential participants allows for very high entrance rates). Entrance rates will typically depend on expected earnings and the expected completion time, which should be announced beforehand. Setting relatively generous completion fees and possible bonuses may promote entrance rates. As entrance rates tend taper off after some time, it is often advisable to take down the advertisement for your experiment and then publish it again.  For that you can set the *HIT expiration time* on MTurk to  30 minutes.

To minimize the variation in completing reading of the instructions and the control questions, it is often worth spending some time in making your instructions as clear and concise as your research question allows.

Furthermore, smaller groups can obviously form more rapidly simply because they require fewer people to be formed. Smaller groups also tend to progress faster through an experiment, which also drives down dropouts. It is therefore advisable to design your experiment for groups as small as your research question allows you to.

From experiments we conducted on MTurk, we noticed that participants often just leave the task when they have to wait long, or when they have no information as to how long they have to wait. This is why the *lobby* has a timer. When this timer reaches 0, participants can choose to leave the HIT and get their participation fees. Alternatively, they can choose to return to the lobby and wait two more minutes (after which they again can choose to either leave or wait for another two minutes).

Experimenters can choose 3 types of :ref:`matching procedures <matching_procedures>`. Using multiple treatments within one experimental session is possible, but will lead to longer waiting times in the lobby (as more participants need to be ready to form a group). A similar logic applies to group size: the smaller the groups, the faster matching will be, and the smaller the chances are of dropouts. 

Decision
============

As soon as participants are matched, the first period begins. Typically, participants progress through the experiment at the speed of the slowest member of a group. As is the case for group formation (see above), here smaller groups will have lower waiting times, and are therefore less prone to suffer from dropouts. In many cases it will be useful use :ref:`countdown timers <stage_and_element__countdown_timer>` to make sure that the participants do not have to wait too long. Non-responsive participants can be removed from the experimental session.

Results
============

Once all group members have made their decisions in a period, you typically want to show results. You can retrieve decisions from the database with :ref:`JavaScript <elements__javascript_program>` and display these in :ref:`test boxes <elements__text_box>`. If this is the last stage of a period, participants will be directed to a waiting screen and pushed on to the next period once all group members are finished viewing the results. Also for stages displaying results, it is often useful to add :ref:`countdown timers <stage_and_element__countdown_timer>` to keep up the pace of a session.

Questionnaire
========================

Once the periods of interaction are over, you may want to record some information about the participants. Common items include age, gender and questions on social and economic status. It can also be useful to ask participants about their prior experience with tasks similar to yours; especially on MTurk, non-naïveté to common paradigms may impact your results (see, for example `Peer et al. 2017 <https://www.sciencedirect.com/science/article/pii/S0022103116303201>`__ and `Chander et all 2014 <https://link.springer.com/article/10.3758/s13428-013-0365-7>`__).

.. _final_earnings:

Final earnings
========================

Once participants have finalized the experiment, you can show them their final earnings. In a typical experiment, you can store a participant’s earnings for each period in a variable in the :ref:`decisions table <experiment_tables__decisions>`. For example, you may store them in a variable called *payoffThisPeriod*. In the final earnings screen, you can then sum the participant’s earnings with the following code:

.. code-block:: javascript

      totalEarnings = 0;
      for (var i=1; i <= numberPeriods; i+){
         totalEarnings += getValue('decisions', 'playerNr=' + playerNr + ' and period=' + i, 'payoffThisPeriod');
      }
      setBonus(totalEarnings);


Note that JavaScript is evaluated in the participants’ browsers. This means that you have to make sure that payoffs are calculated in a way that is *refresh-safe* (that is, if participants refresh their page, payoffs should not change). It is therefore advisable to calculate payoffs anew from a *final earnings* page (i.e. sum up over all rounds starting from 0). With the function ``setBonus()``, the bonus earnings of the participant is written to the :ref:`session table <experiment_tables__session>`. It is then used for :ref:`automatic payment <pay_your_participants>` later.

For linking participants' earnings to their IDs in crowdsourcing platforms (where participants are typically recruited from), the final stage of your experiment should display :ref:`random ID <standard_variables>`. LIONESS experiments have a unique code for every participant available, which can be displayed as ``$randomid$``. You can prompt the participants to fill out this code on the crowdsourcing website to :ref:`arrange their payment <pay_your_participants>`.

