
============================
Notes on experimental design
============================

Based on running numerous experiments online, we suggest that LIONESS experiments follow a basic structure with the components in the order listed below. Each component may be one stage (as is the case in the :ref:`quick start <basic>`), but can of course be expanded to include multiple stages. A methodological discussion of running interactive experiments online can be found in `this paper <https://link.springer.com/article/10.1007/s10683-017-9527-2>`__.

Instructions
============

At the beginning of your experimental task, you have to tell the participants what is expected from them. Apart from explaining the task they are about to complete, this is a good place to inform them about the duration of the experiment, as well as the earnings they may expect. In addition, it is often useful to inform participants that they will only get paid if they complete the task until the end.

Quiz
============

One big difference between online sessions and sessions in the laboratory is that you, as an experimenter, are not physically present. This means that participants cannot ask any questions. To ensure that participants understand their instructions, it is useful to introduce a set of compulsory comprehension questions, before they proceed to the lobby. You can make responses to input elements compulsory by clicking the *required* switch inside the element. You can set a target value for an input element in the parameter field *correct value*.

For each participant, LIONESS experiments will automatically record the number of attempts for each quiz item. This is stored in the :ref:`session table <experiment_tables__session>`.

Lobby
============

To reduce waiting times as much as possible, you can place the lobby after the comprehension questions. This ensures that participants in the lobby understand the game and are matched as soon as sufficient participants are ready to start interacting. By default, the lobby will display the number of participants are necessary to form a group.

Experimenters can choose 3 types of :ref:`matching procedures <matching_procedures>`.

Decision
============

As soon as participants are matched, the first period begins. Typically, participants progress through the experiment at the speed of the slowest member of a group. In many cases it will be useful use :ref:`countdown timers <stage_and_element__countdown_timer>` to make sure that the participants do not have to wait too long, and that non-responsive participants are booted out of the session.

Results
============

Once all group members have made their decisions in a period, you typically want to show results. You can retrieve decisions from the database with :ref:`JavaScript <elements__javascript_program>` and display these in :ref:`test boxes <elements__text_box>`. If this is the last stage of a period, participants will be directed to a waiting screen and pushed on to the next period once all group members are finished viewing the results. Also for stages displaying results, it is often useful to add :ref:`countdown timers <stage_and_element__countdown_timer>` to keep up the pace of a session.

Questionnaire
========================

Once the periods of interaction are over, you may want to record some information about the participants. Common items include age, gender and questions on social and economic status. It can also be useful to ask participants about their prior experience with tasks similar to yours.

Final earnings
========================

Once participants have finalized the experiment, you can show them their final earnings. In a typical experiment, you can store a participant's earnings for each period in a variable in the :ref:`decisions table <experiment_tables__decisions>`. For example, you may store them in a variable called *payoffThisPeriod*. In the final earnings screen, you can then sum the participant's earnings with the following code:

.. code-block:: javascript

      totalEarnings = 0;
      for (var i=1; i <= numberPeriods; i+){
         totalEarnings += getFloat('decisions', 'playerNr=' + playerNr + ' and period=' + i, 'payoffThisPeriod');
      }
      setBonus(totalEarnings);

Note that JavaScript is evaluated in the participants' browsers. This means that you have to make sure that payoffs are calculated in a way that is *refresh-safe* (that is, if participants refresh their page, payoffs should not change). It is therefore advisable to calculate payoffs anew from a *final earnings* page (i.e. sum up over all rounds starting from 0). With the function ``setBonus()``, the bonus earnings of the participant is written to the :ref:`session table <experiment_tables__session>`. It is then used for :ref:`automatic payment <pay_your_participants>` later.

For linking participants' earnings to their IDs in crowdsourcing platforms (where participants are typically recruited from), the final stage of your experiment should also have a random ID. LIONESS Lab has available a unique random code for each participant in the :ref:`session table <experiment_tables__session>`. In the JS code, you can retrieve this random code with the following line:

.. code-block:: javascript

   randomID = getInt('session', 'playerNr='+playerNr, 'randomid');

Subsequently, you can display this ID to the participant screen in the usual way by :ref:`using the dollar signs <javascript__access_the_variables>`. You can prompt the participants to fill out this code on the crowdsourcing website to :ref:`arrange their payment <pay_your_participants>`.


Tips and tricks
================

The MTurk HIT will include a link to the LIONESS experiment. You can
have the participants complete the experiment in a new window, in which
you disable the navigation bar. You can add this piece of code to the
link:

.. code-block:: javascript

   function width() { return window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth || 0; } function height() { return window.innerHeight || document.documentElement.clientHeight || document.body.clientHeight || 0; }

   var w = width() * 0.9; var h = height() * 0.9; window.open(url, 'LIONESSwindow', "resizable=no,location=no,toolbar=no,scrollbars=yes,menubar=no,status=no,directories=n o,width=" + w + ",height=" + h + ",left=" + w * 0.1 + ",top=" + h * 0.1 + "");

