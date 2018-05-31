=========================
Reference manual
=========================

.. _elements:

Elements
=========================

.. _adding_an_element:

Adding an element
-----------------

Generic properties of elements
------------------------------

Element types
-------------

.. _text_box:

Textbox
~~~~~~~

Here is an example of how textbox element looks like:

.. image:: _static/exampletext1.png
   :alt: exampletext1.png

This text box element will show the following text to the participants.

.. image:: _static/exampletext2.png
   :alt: exampletext2.png

In the textbox element, you can insert text, such as the description of
your experiment. When you double~click the area inside the text box, a
user~friendly rich~text editor will appear.

.. image:: _static/textboxdoubleclick.png
   :alt: textboxdoubleclick.png

In this interface you can adjust text fonts and colour, but you can also
use standard HTML. You can toggle between rich~text and HTML view by
double~clicking in the editor.

.. image:: _static/textbox_gui.png
   :alt: textbox_gui.png

.. _button:

Button
~~~~~~

.. image:: _static/button.png
   :alt: button.png

The Button element mainly functions as a trigger to move on to the next
desired stage. There are six sub~elements in the Button element. They
are like the following:

Button label
************

You can define the name of the button which will appear to the
participant, in this case ‘continue.’

Proceed
*******

In the ‘proceed’ element, you can define whether pressing the button
automatically leads to the next desired page or wait until all other
participants press the button so that all participants can continue
simultaneously. For the former case you can select ‘if possible,’ and
for the latter case you can select ‘Wait for others.’

Appears after
*************

If you would like to set a restriction that participants can proceed
only after some amount of time, then you can define after how many
seconds will the participants be able to proceed to the next stage. If
you wish not to use this function, then you can just leave it as it is.

Button countdown
****************

If this is activated, then a countdown is shown until the button
appears.

Next stage
**********

In this menu, you can define onto which stage the experiment proceed.
Default is it will proceed to the next stage so you can just leave it as
it is if this is the case, but you can also define it to jump to another
page. Jumping to another page is useful when you want to skip certain
pages in the middle.

Checker
*******

If you want to execute JavaScript code when a participant clicks a
button, you can use the checker element. One useful application of this
option is checking whether two values in two separate input fields add
up to a certain value, for example:

.. code-block:: javascript

   if (value1+value2!= 10) { 
      showError('The total number should be 10!');
      return false; 
      }

.. _javascript:

JavaScript program
~~~~~~~~~~~~~~~~~~

JavaScript programs allow you to interact with the server and do
calculations. A set of pre~defined
`functions <JavaScript#Interacting_with_the_database>`__ is available to
get variables from the database and to write data to the database
tables. When you start defining your JavaScript element, LIONESS Lab
will open an editor.

.. image:: _static/javascript_program.png
   :alt: javascript_program.png


By default, JavaScript programs will be executed in the participants'
browsers when the page loads. One exception to this is the
`checker <#Checker>`__ functionality in `button <#Button>`__ elements,
which is executed once the button is clicked.

Note that JavaScript elements allow for great flexibility. For example,
with a bit of programming experience you can add design your own display
items (e.g. in an SVG canvas), add interactive elements to your page
revealing information upon mouse~click, or animate items in your screen.
We have a few `examples <Javascript_code_snippets>`__ available.

Also note that JavaScript is a language widely used by web programmers.
The large user base ensures that you will be able to solve the vast
majority of your programming issues with a simple Google search.

Java script programs are limited to 500 lines.

.. _numeric_input:

Numeric input
~~~~~~~~~~~~~

An example of using numeric input element in an experiment is like the
following.

.. image:: _static/numeric_input.png
   :alt: numeric_input.png


This content will show the following screen to participants.

.. image:: _static/example_numericInput.png
   :alt: example_numericInput.png


In this element, you can collect participant’s responses in numbers.

.. image:: _static/numeric.png
   :alt: numeric.png


Text
****

You can set the question to which the participants will be answering.

Variable name
*************

You can set the name of the variable of the numeric input. This will be
handy later on when you have to use the participant’s answers in
Javascript or for analysis.

Minimum
*******

You can define the minimum value which participants can enter. If this
condition is not met, a warning message will appear to the participants.

Maximum
*******

This is the maximum value the participants can enter. Like minimum, when
participants enter a value which exceeds this value, then a warning sign
will appear.

Decimal place
*************

Correct value
*************

Optionally, you can set a correct value for the participants’ answer. If
the participant’s response does not match this value, a warning sign
will appear and participants will not be able to proceed to the next
stage.

Required
********

If you activate this element, then the participants will be able to
proceed only if this input field is answered.

Inline
******

Display the input field next to the text.

Radio line
~~~~~~~~~~

An example of the radioline produced by this element looks like this:

.. image:: _static/radioline_example.png
   :alt: radioline_example.png


In this element, you can make a scale on which the participants can
choose their discrete numerical answer.

Adding a radio line element prompts you to define the following:

.. image:: _static/radioline1.png
   :alt: radioline1.png

Text above
**********

Define the question to which the participants will answer. It will be
located where ‘radioline’ is in the example.


Variable name
*************

You can set the name of the variable of the numeric input. This will be
handy later on when you have to use the participant’s answers in
Javascript or for analysis.


Minimum
*******

The minimum value is the value of the leftmost option of the radioline.
However, the absolute value of the minimum option does not appear to the
participants. Subtracting maximum value by minimum value determines how
many dots (options) there are between minimum and maximum value.


Maximum
*******

The maximum value is the value of the rightmost option of the radioline.
However, the absolute value of the maximum option does not appear to the
participants. Subtracting maximum value by minimum value determines how
many dots (options) there are between minimum and maximum value.

Label left
**********

You can assign a name for the lowest value on the radio line. For
example, if you were to indicate in a scale of 1 to 7 about liking, then
usually the value on the left is most negative.

Label right
***********

You can assign a name for the highest value on the radio line. For
example, if you were to indicate in a scale of 1 to 7 about liking, then
usually the value on the right is most positive.


Required
********

If you activate this element, then the participants will be able to
proceed only if this input field is answered.


Correct value
*************

Optionally, you can set a correct value for the participants’ answer. If
the participant’s response does not match this value, a warning sign
will appear and participants will not be able to proceed to the next
stage.

Slider
~~~~~~

.. image:: _static/slider_example.png
   :alt: slider_example.png


This is an example of how a slider element looks like to the
participants.

In this element, you can make a slider on which participants can
indicate their discrete numerical answer by sliding the button onto a
certain location in the slider. It is basically same as radio line.

.. image:: _static/slider.png
   :alt: slider.png


Variable name
*************

You can set the name of the variable of the numeric input. This will be
handy later on when you have to use the participant’s answers in
Javascript or for analysis.


Minimum
*******

The minimum value is the value of the leftmost option of the slider.
However, the absolute value of the minimum option does not appear to the
participants. Subtracting maximum value by minimum value determines how
many dots (options) there are between minimum and maximum value.


Maximum
*******

The maximum value is the value of the rightmost option of the slider.
However, the absolute value of the maximum option does not appear to the
participants. Subtracting maximum value by minimum value determines how
many dots (options) there are between minimum and maximum value.

Stepsize
********

This indicates the unit which the button can be incremented or
decremented along the slider. For example, if the stepsize is big, then
the distance among possible locations of the button will be also larger.

Default
*******

The starting position of the slider. This is the value that the slider
takes when it is not moved by the participant.


Label left
**********

You can assign a name for the lowest value on the slider. For example,
if you were to indicate in a scale of 1 to 7 about liking, then usually
the value on the left is most negative.


Label right
***********

You can assign a name for the highest value on the slider. For example,
if you were to indicate in a scale of 1 to 7 about liking, then usually
the value on the right is most positive.


Correct value
*************

Optionally, you can set a correct value for the participants’ answer. If
the participant’s response does not match this value, a warning sign
will appear and participants will not be able to proceed to the next
stage.

.. _discrete_choice:

Discrete choice
~~~~~~~~~~~~~~~

.. image:: _static/ExampleDiscreteChoice.png
   :alt: ExampleDiscreteChoice.png


This is an example of a discrete choice element shown to the
participants.

Discrete choice element is basically just like a multiple~choice
question. Participants can choose their answers among the given options.

.. image:: _static/discrete_choice.png
   :alt: discrete_choice.png



Text above
**********

You can set the question to which the participants will be answering.


Variable name
*************

You can set the name of the variable of the discrete choice the
participants will make.


Required
********

If you activate this element, then the participants will be able to
proceed only if this input field is answered.


Inline
******

Display the input field next to the text.

Order of options
****************

There are two ways of presenting options – one is ‘as stated’ and one is
‘random.’ In the former case, the order of options will appear exactly
how the experimenter arranged the order, and for the latter the order of
options will be random for each subject.

Display of options
******************

There are three ways to display options – vertical boxes, horizontal
boxes, and dropdown list.

.. _correct~value~3:

Correct value
*************

Optionally, you can set a correct value for the participants’ answer. If
the participant’s response does not match this value, a warning sign
will appear and participants will not be able to proceed to the next
stage.

.. _default~1:

Default
*******

Num options
***********

Here, you can define among how many discrete choices the participants
can make their choice.

Options
*******

You can write the name of the options which will be appeared to the
participants. Also, presenting images instead of text is possible by
providing a link: <img src = “link of the image”>. Beware that the image
should be uploaded on another open access website. The 'value' for each
options will be recorded to the database, and can be used for later
analysis or Javascript program.

Element reference
~~~~~~~~~~~~~~~~~

Reference
*********

.. image:: _static/element_reference.png
   :alt: element_reference.png


Here, you can refer to a previously created element. When you change the
original element, the element reference will change along with it. You
can only refer to an element from your current experiment.

Text input
~~~~~~~~~~

.. image:: _static/ExampleTextInput.png
   :alt: ExampleTextInput.png


This is an example of a text input element shown in the actual
experiment.


Variable name
*************

You can set the name of the variable of the numeric input. This will be
handy later on when you have to use the participant’s answers in
Javascript or for analysis.

Minimum characters
******************

Optionally, you can define minimum number of characters the participants
should enter in this input field before proceeding to the next stage.

Maximum characters
******************

Optionally, you can define maximum number of characters the participants
can enter in this input field.

Number of rows
**************

The vertical size of the box (the number of lines that is displayed).


Required
********

If you activate this element, then the participants will be able to
proceed only if this input field is answered.

Back button
~~~~~~~~~~~

.. image:: _static/backbutton.png
   :alt: backbutton.png


Button label
************

You can define the name of the button which will appear to the
participant, in this case ‘back.’

Back to
*******

In this menu, you can define onto which stage the experiment will go
back. The default setting is it will go back to the stage right before
so you can just leave it as it is if this is the case. You can also
define it to jump to another page.

.. _stage_type:

Stage type
=========================

Standard
--------

Quiz
----

.. _lobby:

Lobby
-----

JavaScript
=========================

.. _standard_variables:

Standard variables
------------------

.. _javascript_functions:

Predefined functions
---------------------

