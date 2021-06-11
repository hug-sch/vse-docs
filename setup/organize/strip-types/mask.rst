.. _bpy.types.MaskSequence:

**********
Mask Strip
**********

In general, any strip could be a masking strip.
The VSE Mask strip however is rather restricted to the masks, created in the Movie Clip Editor.
There will be nothing in the Mask menu unless you have created a mask in the Movie Clip Editor.
At all other times, it's just a blank menu. If there are multiple masks in the Movie Clip Editor,
you can choose the appropriate mask from the drop-down menu. These masks could also be used as a modifier.

.. figure:: img/mask.svg
   :alt: Masking

   Figure 2: Masking with the Movie Clip Editor and the Mask strip

A mask is a grey-scale image. The Movie Clip Editor generates this image
as you create a mask but also a common Image strip can be used.
It is stored in a data-block and saved within the Blend-file.
You place this mask image on top of a background image and apply the ``Multiply`` blend mode.
Therefore, you need a Mask strip or a Mask modifier. Because the color White is coded as RGB(1,1,1),
multiplying a color from the background (underlying strip) with 1 will return the same color as the background.
The white area of the mask is thus fully transparent, the background image 'shines' through.
A black color is coded as RGB (0,0,0).
So, multiplying this color with the background color will result in 0 or black. The mask is opaque.

In the Movie Clip Editor, you can do also tracking. The mask should indeed follow the movement of the dog.


Options
=======

.. admonition:: Panels documented elsewhere!

   The following panels are identical to those from the Movie strip:
   :ref:`Compositing <compositing-panel>`, :ref:`Transform <transform-panel>`,
   :ref:`Crop <crop-panel>`, :ref:`Video <video-panel>`, :ref:`Color <color-panel>`,
   :ref:`Time <time-panel>` and :ref:`Custom <custom-panel>`.

A Mask panel is added to the Properties (see figure 2)

.. admonition:: Mask Panel

   :menuselection:`--> Sequencer --> Strip --> Sidebar --> Panel --> Mask`

.. figure:: img/panel-mask.png
   :scale: 50%
   :alt: Mask Property of Mask Strip
   :align: Right

   Figure 2: Mask Property of Mask Strip

Mask selector
   With the drop-down, you can select the appropriate mask. If a mask is selected,
   this mask will be stored with the Blend file. If a mask is nowhere selected,
   it will be garbage-collected upon closing Blender and no more available the next time.
   With the Fake User button, you can prevent the loss of the mask, even if it is nowhere selected.

Original Frame Range
   In the Movie Clip Editor, you have to set the Frame Range that the mask that will be applied.
   By default, this range is set to frame 1 -100.
