H. Text strip
=============

The Text strip allows you to directly display text in the Sequence editor.
The strip will display the text inserted in its text field on the final sequence.

.. tip::

   All Text strips in a video sequence can be exported as a `SubRip <https://en.wikipedia.org/wiki/SubRip>`__ file. This is useful when using Text strips as subtitles.

The Compositing, Transform, Crop, Video, Color, and Custom panels are unchanged. The Time panel has no Strip Offset and Hold Offset properties. An Effect panel is added to the Properties.  There is no Source panel because the text is defined in the Effect panel.

.. figure:: img/panel-effect-strip-text-.png
   :scale: 50%
   :alt: Effect Property of Text Strip
   :align: Right

   Figure 16: Effect Property of Text Strip

**Effect**

``Text`` The actual text that is displayed. This text can be 511 characters long.

``Wrap Width`` Wraps the text by the percentage of the frame width. Setting this to zero will disable word wrapping. A value of 0.5 will wrap the text at the middle of the frame.

.. todo::
   The text strip is recently changed e.g. the shadow on the text or the box. Adjust the text accordingly.

``Style: Font`` Clicking on the Open button will show a File Browser window with the Fonts directory of your system. There you can choose a new font for the selected Text strip. This directory is set in the Preferences > File Path > Data.

``Style: Size`` Size of the text. Value between 0 and 2000.

``Style: Color`` The text color. Clicking on the color button will display a standard Color Picker.

``Style: Shadow`` Creates a shadow of the specified color under the text.

``Style: Box`` Creates a background for the text to improve the readability and clarity of text in some situations. The color and opacity of the box can be adjusted using the color selector.

``Style: Box Margin`` The distance the box boundaries extends from the boundaries of the font glyphs. The distance is measured as a factor of the image's width.

``Layout: Location X, Y`` With the values *X* and *Y* you can position the text in the frame. The value (0,0) refers to the bottom left and (1,1) to the top right. A value of (0.5, 0.5) sets the text in the middle of the frame. Pay attention also to the Anchor (see below).

.. todo::
   It's not obvious where the anchor point is for vertical alignment.

``Layout: Anchor X, Y``  Horizontal (Left, Center, Right) or vertical (Top, Center, Bottom) anchor point of the text. With this value you can align the text horizontally or vertically.