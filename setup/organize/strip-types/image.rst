
C. Image/Image Sequence strip
=============================

The input source of an Image strip is a graphics file with extension ``.BMP``, ``.Iris``, ``.PNG``, ``.JPEG``, ``.JPG2000``,  ``.targa``, ``.cineon & DPX``,  ``openEXR``, ``Radiance HDR`` or ``.TIFF``. (see `graphics formats <https://docs.blender.org/manual/en/dev/files/media/image_formats.html>`_).

Although an image is normally only one frame, the resulting Image strip has a length of 25 identical frames or stills. This is done by manipulating the time codes.

.. todo::
   Refer to same section as the timecode.

The input source of an Image Sequence strip is a sequence of (numbered) graphic files (e.g. \*-0001.png, \*-0002.png, \*-0003.png, etc. In the input source you can retrieve the individual image names. The strip however is treated as one indivisible movie and is as such indistinguishable from a movie strip.

The Image/image Sequence strip has a brown color while the Movie strip is Aquamarine (see figure 1). Image sequences can use placeholder files. This is done by enabling Use placeholders checkbox when adding an image strip (see TODO).

The properties are mostly the same as a Movie strip.  Only in the Source panel, there is a minor change. The default setting for Blend mode is however AlphaOver for an Image/Sequence strip and Cross for a Movie Strip. 

**Source**

.. figure:: img/panel-source-movie-strip.png
   :scale: 50%
   :alt: Source Property of Image Strip
   :align: Right

   Figure 11: Source Property of Image Strip

In contrast to the Movie strip, the Source property is split into a directory and a file component.

``Directory`` The directory that contains the source files. When the image files are moved this field can be updated instead of having to recreate the strip.

``File``: The filename of the image for that particular frame, e.g. \*-0001.png, \*-0002.png, \*-0003.png, ... 

``Color Space``: see `Movie strip`.

``Alpha``: Premultiplied (RGB channels in transparent pixels are multiplied by the alpha channel) or Straight (RGB channels in transparent pixels are unaffected by the alpha channel) of the image.

``Change Datafile``: replaces the complete image sequence with the selected images.

``Resolution`` See `Movie strip`