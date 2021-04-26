Mask strip
=============

In general, any strip could be a masking strip. The VSE Mask strip however is rather restricted to the masks, created in the Movie Clip Editor. There will be nothing in the Mask menu unless you have created a mask in the Movie Clip Editor. At all other times it's just a blank menu. If there are multiple masks in the Movie Clip Editor, you can choose the appropriate mask from the drop-down menu. These masks could also be used as a modifier.


A mask is a grey-scale image. The Movie Clip Editor generates this image as you create a mask but also a common Image strip can be used. You place this mask image on top of a background image and apply the ``Multiply`` blend mode. Because the color White is coded as RGB(1,1,1), multiplying a color from the background (underlying strip) with 1 will return the same color as the background. A white area of the mask is thus fully transparent, the background image 'shines' through. A black color is coded as RGB (0,0,0). So, multiplying this color to the background color will result in 0 or black. The mask is opaque.


The Compositing, Transform, Crop, Video, Color, Time, and Custom panels are unchanged. A mask panel is added to the Properties.

**Mask**

.. figure:: img/panel-mask.png
   :scale: 50%
   :alt: Mask Property of Mask Strip
   :align: Right

   Figure 14: Mask Property of Mask Strip

``Header`` with logo of strip, mask selector (if there are more than one), Fake User button and link/unlink checkbox.

``Original Frame Range`` In the Movie Clip Editor you have to set the Frame Range that the mask will be applied. By default, this range is set to frame 1 -100.
