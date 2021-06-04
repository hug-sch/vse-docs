
***********
Color Strip
===========

The Color strip is a sequence of 25 frames with a solid color.
It fills the complete preview area with the selected color.
The resolution is derived from the Project Settings.
Its Duration is set by the same mechanism as the Image strip (see :ref:`Movie strip - Time panel <time-panel>`.
The :ref:`default <default-color>` color of the Color strip bar is: :color:`███`.
However, the selected color will also be shown in the lower half of the strip bar (see figure 1).

The Color strip is used to create some custom transitions and in combination
with the Crop and/or Transform property to create some horizontal or vertical colored bars (see figure 1).

.. figure:: img/color.svg
   :alt: Use of the Color strip

   Figure 1: Possible use of the Color strip

Note that the original color strips have a dimension of 1920 x 1080.
Cropping Left and Right will produce the vertical bars.
You can do some simple math to position the bars exactly.
Because the height is 1080, the middle bar should be at 1080/2.
If you want a width of 10 pixels for this bar, you need to subtract additional 5 pixels from top and bottom crop.
Please, note also that these Color strips should have a blend mode of Overdrop or Alpha Over.

.. admonition:: Panels documented elsewhere!

   The following panels are identical to those from the Movie strip:
   :ref:`Compositing <compositing-panel>`, :ref:`Transform <transform-panel>`,
   :ref:`Crop <crop-panel>`, :ref:`Video <video-panel>`, :ref:`Color <color-panel>`,
   :ref:`Time <time-panel>` and :ref:`Custom <custom-panel>`.

   The Time panel has no Strip Offset or Hold Offset properties because there is no content to offset.
   The strip is evenly colored.

An Effect panel is added to the Properties.

.. admonition:: Effect Strip Panel

   :menuselection:`--> Sequencer --> Strip --> Sidebar --> Panel --> Effect Strip`


.. figure:: img/panel-effect-strip-color.png
   :scale: 50%
   :alt: Effect Strip Property
   :align: right

   Figure 2: Effect Property of Color Strip

Effect Strip
   With the vertical slider, you can set the brightness of the color.
   Clicking on the horizontal slider will display a standard Color Picker.
   More info about the :doc:`Color Picker </edit/color-grading/terminology/terminology>` in the Color grading section.
   This Color Picker has some additional settings, i.e. opacity.

   The existing Color panel has some overlap with the Effect Strip panel, for example, the Saturation field.
