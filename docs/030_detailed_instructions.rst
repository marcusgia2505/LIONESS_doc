
.. _develop:

=========================
Develop
=========================

There are two basic ways to develop your LIONESS experiment. You can either start from scratch, or :ref:`build on an existing experiment <build_on_an_existing_experiment>`. The :ref:`repository` contains a range of different LIONESS experiments for you to use and adjust to accommodate your requirements.

Here we describe how to develop your LIONESS experiment from scratch. We describe how to create a new game and define your screens. If you have already completed the tutorial, many of the steps described here will look familiar to you. This chapter gives a fuller description of the features that LIONESS Lab has to offer.

Create experiment
=========================

On the LIONESS Lab landing page, you can create a new LIONESS experiment by clicking *new experiment* in the :ref:`top horizontal bar <main_menu>`.

In the next screen you can define basic settings of your experiment by filling out the appropriate screens.

.. image:: _static/New_game.png
   :alt:  300px


With the drop-down menu under *availability* you can choose to keep  experiment private, or to share it with other LIONESS Lab users by making it *public*. Other users will be able to copy public experiments from the :ref:`repository`  to their LIONESS Lab accounts and edit these for their own purposes. Experiments' settings can be adjusted at any time.

With the input fields on the right you can give additional information on your experiment (e.g. you can use the comments section to list the number of sessions run with this experiment, or add any caveats you might have). This information can then be used by other LIONESS Lab users that might want to build on (parts of) your experiment.

Defining your screens
=========================

Your screens consist of three sections: *settings*, an *active screen* and a *waiting screen*.


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


.. _compile_and_test:

====================
Compile and test
====================
Once you are ready specifying your experimental screens, you can test your LIONESS experiment. Here we describe the basic procedures of how test your experiment and make adjustments on the fly. Once you are done testing, you can download your experiment, put it on your own server, and :ref:`run <run>` your experiment online.


Compile your LIONESS experiment
==================================================

In LIONESS Lab, click *compile and test*, and compile your experiment by selecting *compile* from the drop-down menu. During the compilation process, LIONESS Lab activates a script that will build the database underlying your experiment and creates the experimental pages from the stages that you defined in each of the tabs. Once the compilation process has completed, a new tab will open with the :ref:`control panel <control_panel>` of your LIONESS experiment. All further testing can be done from the control panel.

In case you want to make any changes to your screens, you can go back to LIONESS Lab. You can use the *Update screens* option from the same drop-down menu. This will create the experimental pages, without re-building the tables. In most cases this means that you can directly view your changes by refreshing the page in the participant's screen, and continue testing. In cases where you added new variables (e.g. by adding a new input element or by using the `` record()`` function in a JavaScript element), you have to re-build the tables and start a new test session.

.. _control_panel:

Control panel
=========================

The :ref:`control panel <control_panel>` allows the experimenter to control the experimental flow (start and stop the experiment), observe the data collection and download the data and payment file. The control panel also triggers the :ref:`central controller algorithm <control_panel__controller_algorithm>`.

**During a session, the control panel of the experiment needs to be open on the experimenter's computer.**

.. image:: _static/Control_panel_0.png
   :alt:  800px

.. _control_panel__global_control:

Global control
---------------------

The horizontal top bar contain basic control functions.

.. image:: _static/Control_panel_1.png
   :alt:  800px

.. _control_panel__controller_algorithm:

Controller algorithm
---------------------------

The controller algorithm is called by the control panel page. Each second, the control panel will run a PHP script on the server performing checks related to the flow of the experiment. This is indicated with the animated heartbeat next to the LIONESS icon. Specifically, the controller algorithm:

- Controls the registration of new participants. Participants automatically receive a unique playerNr upon entering the experimental pages. If the button Game active is switched off, no participant can enter a session, but those that are already in will be able to proceed.
- Regulates grouping. It tracks the number of participants waiting in the lobby, and groups together those that are ready. Various pre-programmed :ref:`grouping procedures <lobby>` are available.
- Regulates group progress. It tracks for each group the number of participants that are ready to proceed to the next period (or a next stage, in case the experiment requires participants to wait for their fellow group mates) and controls their proceeding to the next period
- Handles dropouts. In case a participant has dropped out (that is, the server cannot detect that their are active), the controller algorithm can take action. Upon dropout, you can choose to have the group continue with reduced size, terminate the whole group, or to take no action at all. You can define your :ref:`dropout handling <parameters__dropouthandling>` preferences in the :ref:`parameters table <parameters>` of an experiment.


Global settings
-------------------

.. _control_panel__active_inactive:

Game active / inactive
~~~~~~~~~~~~~~~~~~~~~~~

With the *Game (in)active* button, you can block new participants from entering. When switched to *inactive*, participants will be directed to a page that they cannot participate at this time. You can customize the default text shown in these cases in the experiment's :ref:`parameters table <parameters>`.

.. _control_panel__terminate_player:

Terminate player
~~~~~~~~~~~~~~~~~~~~~~

You can manually remove a participant from a session by entering their value of *playerNr* in the field next to *Terminate player*. This will take that participant to a screen indicating that they can no longer proceed. The software will treat this participant as a *dropout*, that is, the group will proceed according to the :ref:`dropout handling <parameters__dropouthandling>` settings. Note that terminating a participant is a last resort measure.

Export database
~~~~~~~~~~~~~~~~~~~~~~

With this button the database of the experiment is exported as an Excel file. Each of the :ref:`experiment tables <experiment_tables>` will be shown in a separate Excel tab. The :ref:`decisions table <experiment_tables__decisions>` will typically be the most interesting one as it contains the participants' responses in the experiment.

Empty data tables
~~~~~~~~~~~~~~~~~~~~~~

With this button you can empty the tables of the experiment's database. This will not emtpy the :ref:`globals table <experiment_tables__globals>`. Be aware that this cannot be undone. LIONESS Lab does not store old results.

Map
~~~~~~~~~~~~~~~~~~~~~~

By clicking this button, an external program will create a map showing the location of the participants of your session. These locations are based on the participants' IP addresses (which are encrypted upon entrance) and may be not correct. The tool is just to get an overview from where participants are logged in.

Logout
~~~~~~~~~~~

Log out of the experiment. Logging out implies that the controller algorithm is no longer running. Typically you'd want to click this button only after an experimental session is over.

.. _control_panel__test_mode:

Test mode
----------

When developing your experiment, it is often useful to test you experiment by playing as a participant and inspecting the screens. The test mode will allow you to enter multiple times (i.e. control multiple *test players*) from the same browser.

.. image:: _static/Start_testing.png
   :alt:  400px


In the top bar of the Control panel, make sure that the experiment is active. Then, switch on the test mode. Two buttons will appear: *Start testplayer* and *Start bot*.

Once click this button, two more buttons will appear that will allow you to start your experiment as a test player or start a :ref:`bot <bots>` , which will make automated decisions. Bots are particularly useful for is useful for experiments in groups (so you have to control only one test player while the other decisions are generated automatically) in case you want to check whether all data is correctly recorded in the database.


.. _control_panel__test_player:

Testplayers
~~~~~~~~~~~~

When you click *Start testplayer*, a new tab opens in your browser, which takes you to the first stage of your experiment. You can see the screens that a participant in your experiment would see. Multiple testplayers are supported.

.. _bots:

Bots
~~~~~~

In experiments with many stages (or large groups), it can be useful to automate some players, while operating some others as test players. The 'bot' functionality will help you do that. Clicking the button *start bot* will open a new tab with a robot player. With automated JavaScript functions, this *bot* will give random responses to input elements and will try to proceed through your experiment. We write *try* here, because the *bot* is still in beta version and is not yet able to deal with more sophisticated ways to record data with JavaScript functions.



.. _control_panel__monitor:

Monitor
-------------------

In the bottom part of your :ref:`control panel <control_panel>` you can browse the :ref:`tables <experiment_tables>` of your experiment and :ref:`monitor <control_panel__monitor>` the progress of a session. In the :ref:`core table <experiment_tables__core>`, you can keep track of the test players by selecting to view the variables ``playerNr``, ``groupNr``, ``period`` and ``onPage``. Once you have started one or more Testplayers, they should be visible a entries in this table.

During a session, basic information about the entered participants will appear in the *core* table. By clicking the *display options* button, you can choose which variables in this table you want to track. Clicking the buttons with the variable names will make them visible in the page section below. This section will be updated every second. Among the most useful variables are: playerNr, groupNr, period and onPage. The *onPage* variable tracks which page a participant is currently watching. These pages are marked with stars (indicating :ref:`active screen <defining_your_screens__active_screen>`) or dashes (indicating :ref:`waiting screen <defining_your_screens__waiting_screen>`).

.. image:: _static/Control_panel_3.png
   :alt:  800px

In the example above, there are 5 participants in the experiment. Participants 1-4 have just passed the lobby and have been grouped together - the value of groupNr is *1* for each of these participants. They are currently in period 1, on the page *Decision*. Participant 5 is currently on a page called *Instructions* (which in this case comes before the lobby).

One of the key purposes of testing is to check whether participants' responses are recorded correctly, and to verify if any calculations are performed as they should. For this, the :ref:`decisions table <experiment_tables__decisions>` is most useful. For each period, a new row is added to this table for each participant. Values should appear there once they are entered in the participants' screens.

.. _experiment_tables:

Experiment tables
========================

.. _experiment_tables__core:

core
-----------------

The variables in this table form the core of the experiment. These variables regulate the flow of the experiment, and are used by the controller algorithm to detect progress. This table is the most useful table to monitor during an experimental session. It allows you to track the participants' group number, the page that they are currently on (the variable *onPage*) and their current period number. All columns in the table are explained in detail :ref:`here<parameters__predefined_parameters>`

.. _experiment_tables__decisions:

decisions
-----------------

This table stores the data that is generated by the participants. All their responses are stored in this table. For each period, for each participant, one row will be added to this table to store any responses generated in that period. This table also contains the response times (in seconds) for those pages that are visited in a given period.

.. _experiment_tables__globals:

globals
-----------------

This table stores the parameters of the session. These can be manipulated in LIONESS Lab, in the :ref:`parameter tables <Parameters>` of an experiment. In addition, this table contains the :ref:`message texts <parameters__messages>` displayed to participants once they have dropped out of a session, or cannot or cannot participate. These messages can explain to participants the reasons why they dropped out, or why they cannot participate.

.. _experiment_tables__logevents:

logEvents
-----------------

This table documents key events during the experiment, such as participant entry and dropout. Entries are automaticly added by the :ref:`controller algorithm <control_panel__controller_algorithm>`.

.. _experiment_tables__session:

session
-----------------

This table contains session data. Each participant is associated with one row in this table.


Debugging program code
=========================

One of the key purposes of testing your experiment is to check whether all program code works as intended. Find pointers to debug the code in your JavaScript elements :ref:`in the reference manual <javascript__debugging_your_javascript_code>`.

========================
Set up your experiment
========================

While :ref:`testing <develop>` your experiment, the web pages were on the LIONESS Lab server. This server is for development purposes only. For conducting your online experiment, you need to put your LIONESS experiment on your own server.


Download your experiment
===========================

The first step to copy your LIONESS experiment on your own server, is to download your experiment. In your LIONESS Lab page, click *compile and test* and select *download experiment*.

The experimental pages will be downloaded as a .zip file. When you unzip this file, you will see a folder with mainly PHP files. These are the experimental pages (with names *stage* followed by a number. Two files in this folder are of particular importance: credentials.php and sqlCode.sql. These files are for adding the credentials of your own server and setting up the :ref:`tables <experiment_tables>` underlying your experiment. We will get to these two files below.

Adjust your credentials
=========================

In the LIONESS experiment you downloaded from LIONESS Lab, located the file *credentials.php*. In this file you have to set the username and password of your server. You also have to specify the name of the database you intend to use for your experiment (see below).

.. image:: _static/Credentials.png
   :alt:  200px


Set up your server in a few simple steps
=========================================

For running an interactive experiment it is a good idea to use a server with enough computational power to handle many connections and data traffic simultaneously. Such servers are widely available at low cost. Here we describe how to set up your own *virtual server* using Google Cloud. You can use this service to rent a powerful server for the duration of your session, and take the server offline after the session is over. The costs of renting a virtual server for a typical session of around 2 hours will cost you only a tiny fraction of the amounts that participants will usually earn.

If you already have a server running and you know how to operate it, you can skip this section.

Virtual server
---------------

You do not need advanced technical skills to set up a virtual server. Bitnami has a user-friendly point-and-click interface to do this. Here we briefly run you through how to do this. Click here for a more detailed instruction how to set up a :ref:`bitnami server <bitnami>`

(1) Go to the `bitnami <https://google.bitnami.com>`__ website and create a free account.

(2) You receive an email from bitnami to confirm and activate your account.

(3) For your LIONESS experiment, you need to set up a so-called *LAMP stack*, which you can do `here <https://bitnami.com/stack/lamp>`__.

(4) Choose *Launch in the cloud* by clicking the button.

.. _bitnami:


Bitnami
--------

We will use Bitnami to set up a pay-as-you-go server that you can take offline as soon as your session is over. This saves the costs of having a permanent server. As an indication: renting a suitably powerful server for a session of two hours will costs you less than $1 - which is very low compared to the other costs involved (e.g. paying participants).

 1. Go to bitnami.com/stack/lamp and click *Launch in the cloud* and choose the Google Cloud. - On the page *New Virtual Machine*, give your server a name (e.g. *LIONESS server*)

[ go step by step through this setup process ]

 - Connect to your server with [FileZilla]

 2. Set up your LIONESS Lab task on your server

 - Download your task by choosing Compile and test --> Download game - Extract the ZIP file

 - Go to the folder *htdocs* on your server and create a folder with the name of your task (e.g. PGG). Note that this name will be part of the web address that your participants will visit, so you might want to use a non-descriptive name (e.g. PGG, or task).

 - Upload the task to the folder *htdocs* on your server.

 3. Prepare your HIT on MTurk

 copy text from http://surveycamel.com/hively/drafts/LIONESS/mturk-session/

4. Launch your HIT, monitor the progress and pay the participants the random code - a shorter version of http://research-tricks.blogspot.de/2012/07/bulk-bonuses-on-mturk.html\


Upload your LIONESS experiment to your server
===============================================

Now your server has been set up, you can upload your LIONESS experiment to your server. To transfer the experiment to your server, you have to install an *FTP application*. A decent (and free) option is `FileZilla <https://filezilla-project.org/>`__. Choose the FileZilla Client. When installing, stick to the default options.

Once FileZilla is installed, choose File... and then Site manager.

The screenshot below illustrates the settings you need: choose *New site* and add the IP address of the virtual server in the Host field.
You can find this IP address in bitnami. For Protocol, choose *SFTP-SSH*.

.. image:: _static/FileZilla_sm.png
   :alt:  350px

Once you are logged in, create a new folder for your experiment (e.g. *myExperiment*). Copy all LIONESS files into that folder.

Set up your database and LIONESS tables
-----------------------------------------

On your server, log into your MySQL administrator environment (e.g. phpMyAdmin or adminer). The below example assumes you use adminer.php, but for phpMyAdmin it works very similarly.

Create a new database by clicking Create new database on the top of the page. Give it the name of your experiment and save (e.g. *myExperiment*). **The database name needs to correspond to the database name you set in *credentials.php* (see above)**.

In *credentials.php*, the HOST should be set to *localhost*, and the ADMIN to *root*. The DBNAME should correspond to the database you just created (e.g. *myExperiment*). The PASSW (password) should match that of the server you created. You can find this password in the bitnami launchpad.

.. image:: _static/PasswordLaunchpad.png
   :alt:  300px

Set up the tables by clicking Import and select the file sqlCode.sql

After selecting this file, click the Execute button to define the structure of the database. This structure ensures that the data produced by the participants in the experiment will be saved in the appropriate place. If all went well, you should now see the the following tables in your database: core, decisions, globals, logEvents, and session.

.. image:: _static/ResultSQL.png
   :alt:  300px


Your experiment is now ready to run. You can go to the ControlPanel through the address http://%5Byour server name]/[your experiment name]/_beginControl.php (so, for example http://myServer/myExperiment/_beginControl.php).

.. _run:

=================
Run
=================

Once you have completed testing and setting up your experiment, you can run your LIONESS experiment online. Here we describe the steps to collect data with participants recruited from `Amazon Mechanical Turk <http://www.mturk.com>`__. Before you run your experiment, it is useful to take a look at `this <https://link.springer.com/article/10.1007/s10683-017-9527-2>`__ paper discussing best practices and methodological details of conducting interactive experiments online.

Recruit participants
======================

If you have access to an established laboratory participant pool (e.g. through your research institute), you may be able to recruit your participants for your LIONESS experiment from there. Alternatively, there are several crowd-sourcing platforms available to recruit participants for online experiments. Here we describe how to recruit participants from Amazon Mechanical Turk (AMT). A description for Prolific Academic will be added soon.

Setting up a HIT on Amazon Mechanical Turk
-------------------------------------------

Once you logged into your AMT account, click on the tab Create and then choose *New project*. Among the options displayed, you might want to use Survey Link. This type of project will allow you to request a code for the task to be paid. Hence, participants in your study will complete their task, see a unique code at the end of your LIONESS experiment and then enter it as a code in this type of survey.

Select *Create Project* and fill in the required details for the tab *Properties* as you like (title, description, reward per assignment, etc). Select Design Layout (shown below). In this page edit the content that you want your participants to see, usually the title and description you already used in the previous tab will be enough.

Once you are done with the edition, press Source and search for the two instances where “http://www.linktomysurvey.com” appears. Replace these with the link to your LIONESS experiment. You can find the link in the control panel under *address for participants*. Press Source again, and finally click on Preview. If you are happy with the way your task looks, press Finish.

General pointers for writing a HIT description can be found `here <https://link.springer.com/article/10.1007/s10683-017-9527-2>`__. Make sure you have the control panel of your experiment open when you publish your HIT.

Monitor your experiment
========================

During a session you can monitor your experiment using the :ref:`Control panel <control_panel>`. This allow you to track the session' progress, and browse through all data associated with the session (parameter settings, participants' decisions, etc).

End of a session
===================

At the end of a session, you can download all data as an Excel file by clicking the button *Export database*. This will download the database of the experiment in Excel format. The first five tabs correspond to the five tables underlying your experiment. The most informative table for the data analysis will often be the :ref:`decisions table <experiment_tables__decisions>`, as it stores the responses of the participants in the experiment.

.. _pay_your_participants:

Pay your participants
=======================

One can assign bonuses manually in the AMT user interface. However, especially when sessions are large, it is often handy to pay participants with the help of a script. One useful software for this is Amazon's Command Line Tools. Click `here <https://requester.mturk.com/developer/tools/clt>`__ to get the CLT running on your system. To do this, follow these steps:

 - On MTurk, download and open *Batch results file*
 - Copy all its contents to the clipboard
 - Open the LIONESS results file in Excel and paste the copied cells to cell A1 of the tab ‘batchResults’. The Excel file will automatically link the LIONESS code and its earnings to the MTurk worker ID of the participant.
 - The tab *paymentsMTurk* then contains the ready-made codes you can use in MTurk Command Line Tools.
 - Double-check if the bonus amounts in the column *bonus* are correct
 - Add a description explaining participants why they earned this bonus and copy that into all rows of that column
 - The column *MTurkPaymentToolsCode* will contain a list of codes that can you can paste into CLT


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

Experimenters can choose 3 types of :ref:`matching_procedures`.

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



=========================
Share with others
=========================

LIONESS Lab encourages its users to share their experiments once they are ready. Experiments are shared through the :ref:`repository<repository>`. By sharing your experiments, you can contribute to the number of experimental designs that are available for others to build on.

Sharing your experiments is important for a number of reasons. A large set of usable and customisable designs facilitates the easy development of experiments, and helps avoiding that experimenters are re-inventing the wheel by programming from scratch their own solutions to common issues. Moreover it promotes reproducibility of experimental methods and results.

.. _repository:

Repository
==========

The Repository allow you to browse the experiments of other LIONESS Lab users and import them to your own account. You can then view the experiment, test it, copy it to your account and customise it as you wish. By making your own experiments *public* (see below), other users may also import your experiment to their accounts and adjust it to meet their own requirements.

The Repository aims to facilitate easy development of experiments, avoid that experimenters are re-inventing the wheel by programming from scratch their own solutions to common issues, and to promote reproducibility of experimental methods and results.

Using the repository
---------------------

You can access the Repository of LIONESS Lab experiments from the landing page.

.. image:: _static/Repository_main_menu.png
   :alt:  600px

You can search for experiments by using the field on the top right.

.. image:: _static/Repository_search.png
   :alt:  600px


In case you with to view an experiment, you can simply import it to your account by clicking on the *+* sign. The system will take you right to your own account, and the newly imported experiment will be ready for viewing. Note that you cannot make any changes until you have made a copy of the imported experiment in your own account.

.. image:: _static/Import_experiment.png
   :alt:  600px


Making your experiment available in the repository
------------------------------------------------------

When you have made your experiment *public* in the experiment settings page, your experiment will be visible to others in the Repository. You can always change the settings for an experiment by adjusting this setting in the *experiment settings*.

And then make your choice from the dropdown menu.
