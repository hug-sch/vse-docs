.. _bpy.types.ImageSequence:

**************************
Image/Image Sequence Strip
**************************

.. figure:: /images/vse_setup_project_striptypes_add-strips.png
   :scale: 50%
   :alt: Add stips
   :align: Right

   Figure 1: Add command

Image and Image Strip are two different strip types.
Nevertheless, you need the same command to add them to the timeline (see figure 1).
The :ref:`default <default-color>` color of the Image/Image Sequence strip bar is: :image:`███`

The input source of an Image/Image Sequence strip is a graphics file
or a collection of graphics files with extension
``.BMP``, ``.Iris``, ``.PNG``, ``.JPEG``, ``.JPG2000``, ``.targa``,
``.cineon & DPX``, ``openEXR``, ``Radiance HDR`` or ``.TIFF``.
For more in-depth information about these formats,
see `graphics formats <https://docs.blender.org/manual/en/dev/files/media/image_formats.html>`_.


Image
=====

Although an image file contains normally only one image,
the resulting Image strip has a length of 25 identical frames or stills.
As such, these strips are very much like Movie strips.
The default length of 25 is hard-coded but you can change it easily
by entering a new Duration or by dragging the strip handles.

.. note::

   The exact numerical Offset is stored in two unexposed fields: *still_offset_start*
   and *still_offset_end*. See :doc:`Extra Tools > Python > Useful scripts </extra-tools/python/useful-scripts>`
   to make those timecodes visible in the sidebar and :ref:`Movie strip > Time panel <time-panel>` for an explanation.


Image Sequence
==============

The input of an Image Sequence strip is a sequence of graphic files, e.g. *0001.png*, *0002.png*, *0003.png*, etc.
Most of the time these files are numbered as in the previous example.
However, this is not necessary because Blender creates the sequence based on the sort order in the File browser.
You could name them also as *a.png*, *b.png*, and *c.png*.
If - by coincidence - you sorted the above files in reversed order,
then the sequence will begin with *0003.png* or *c.png*.

When this image sequence is added to the timeline, the resulting strip is treated as one movie.
In the :ref:`Source panel <image-source-panel>` of the sidebar you can retrieve the individual image names.

Sometimes, you don't have all of the image files available at the time you want to create the Image Sequence.
You can then enable the Use placeholders checkbox when adding the image strip.
This will create the image strip with empty -but named- frames for the missing images.
Suppose 0002.png is missing in the previous example.
Creating the Image Sequence -- with Use Placeholders checked -- will create a strip of three frames.
The second frame appears as black but is named 0002.png.
Later on, you can add this file to the folder with the others.
This method will only work with correctly numbered sequences.
Our previous example with *a.png*, *b.png*, *c.png* will not succeed.


Options
=======

.. note:: Panels documented elsewhere!

   The following panels are identical to those from the Movie strip:
   :ref:`Compositing <compositing-panel>`, :ref:`Transform <transform-panel>`,
   :ref:`Crop <crop-panel>`, :ref:`Video <video-panel>`, :ref:`Color <color-panel>`,
   :ref:`Time <time-panel>`, :ref:`Source <source-panel>`  and :ref:`Custom <custom-panel>`.


Only in the Source panel, there are minor changes.


Source
------

.. _image-source-panel:

.. admonition:: Reference
   :class: refbox

   :View:      Sequencer
   :Panel:     :menuselection:`Sidebar --> Strip --> Source`

.. figure:: /images/vse_setup_project_striptypes_panel-source-strip-image.png
   :scale: 50%
   :alt: Source Property of Image Strip
   :align: Right

   Figure 2: Source Property

In contrast to the Movie strip, the Source property of the Image Sequence strip
is split into a directory and a file component (see figure 2).

Directory
   The directory that contains the source files.
   When the image files have moved this field can be updated instead of having to recreate the strip.

File
   The filename of the image for that particular frame, e.g. *0001.png*.
   If you want to replace a particular frame in the Image sequence with another one, you can change the name here.

Color Space
   :ref:`See Movie strip <source-panel>`.

Alpha
   The options are *Premultiplied* or *Straight*.

   .. todo::

      Clarify the following text. Next to the Red, Green & Blue channels,
      most graphic formats at the top of this page support a fourth channel:
      the Alpha channel. One notably exception is JPEG.

      Alpha channels store transparency information in files in one of two ways:
      straight or premultiplied. Although the alpha channels are the same, the color channels differ.

      With straight (or unmatted) channels, transparency information is stored
      only in the alpha channel, not in any of the visible color channels.
      With straight channels, the effects of transparency aren’t visible until
      he image is displayed in an application that supports straight channels.

      With premultiplied (or matted) channels, transparency information is stored
      in the alpha channel and also in the visible RGB channels,
      which are multiplied with a background color.
      The colors of semitransparent areas, such as feathered edges,
      are shifted toward the background color in proportion to their degree of transparency.

      Some software lets you specify the background color with which the channels are premultiplied;
      otherwise, the background color is usually black or white.

      Premultiplied (RGB channels in transparent pixels are multiplied by the alpha channel)
      or Straight (RGB channels in transparent pixels are unaffected by the alpha channel) of the image.

Change Datafile
   Replaces the complete image sequence with the selected images.
   It is advisable to have the same number of images in the sequence as the original strip.
   The duration of the original strip is indeed not changed; so, if there are fewer images the last one is repeated,
   or if there more images the last ones are cut off.

Resolution
   :ref:`See Movie strip <resolution>`.
