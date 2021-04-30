Movie strip
===========

The input source of a movie strip is a video file with extension ``.mp4``, ``.mpg``, ``.mpeg``, ``.dvd``, ``.vob``,  ``.avi``, ``.mov``, ``.dv``, ``.ogg``, ``.ogv``, ``.mkv``, ``.flv``, or ``.webm`` (see `Video formats <https://docs.blender.org/manual/en/dev/files/media/video_formats.html>`_). Blender uses the ffmpeg library to process the video files. Which codecs are available depends on the operating system and ffmpeg version.

Each video file contains a sequence of image frames (the actual movie) and some meta information such as resolution and frame rate (fps). The resolution info for example is exposed in the source-panel_. Unfortunately, the source FPS is not.

.. warning:: 
   It is important that the Project Settings parameters are in accordance with the strip parameters. For example, if the project is set to a frame rate of 30 fps, and your clip is only 24 fps, then the clip will appear accelerated. A 1 second play back time will contain 30 frames; according to the project settings. But, these 30 frames take 1.2 s in the original footage. Compressing 1.2s in 1s during playback will induce the acceleration. 

   Also, if your clip has variable framerate; e.g. footage from some smart phones, then you'll get an audio sync problem because Blender uses a constant frame rate. So, you have to convert your clip to a constant frame rate with programs as `ffmpeg <https://ffmpeg.org/>`_ or `Handbrake <https://handbrake.fr/>`_

The movie strip is the most commonly used strip type and has a lot of properties. They are organized in panels in the sidebar.

.. admonition:: Panel Compositing
   :class: refbox

   :menuselection:` --> Strip --> Sidebar --> Panel --> Compositing`

.. figure:: img/panel-compositing.png
   :scale: 50 %
   :alt: Compositing property
   :align: Right

   Figure 2: Compositing Panel

In the Compositing panel you can set the properties `Blend` and `Opacity` (see figure 1).

Blend
   When two strips are placed on top of each other, e.g. channel 2 on top of channel 1, the strip of channel 1 is completely covered by the strip of channel 2 as if channel 1 does not exist. This is because the Blend Mode of the channel 2 strip is set to Cross (default value). The Blend mode of a strip on the upper channel specifies how the strip on a lower channel should combine or blend with the strip on the upper channel. There are plenty of blend modes,such as Replace and Darken but also with less intuitive names such as Color Dodge or Alpha Over.

   .. todo::
      The blend modes and their functional differences are described in detail in section ...

Opacity
   The opacity or alpha value of the image is multiplied with this value. A value of 1 has no effect on the opacity of the strip. If the strip is semi-transparent (e.g. alpha=0.6), then it remains semi-transparent. A value of zero will make the strip fully transparent because the alpha-value of the strips becomes zero. See :doc:`Mask strips <mask>` for more details on transparency/opacity.

.. admonition:: Panel Transform
   :class: refbox

   :menuselection:` --> Strip --> Sidebar --> Panel --> Transform`

.. figure:: img/panel-transform.png
   :scale: 50%
   :alt: Transform Property
   :align: Right

   Figure 2: Transform Panel

The Transform panel is probably the panel that you'll need to have open most of the time. It contains the Position, Scale and Rotation properties and the less important Mirror property.

Position X, Y
   The view area of the sequencer output is set formats the project dimensions (see :doc:`../dir-structure/creating-directory-structure`). A movie is centered (and scaled) within this view area. With the position X, Y values, you can move the frame along the X and Y axis. The values are expressed in pixels.

Scale X, Y
   With this value, you can scale the image on the X and Y axis. It is a number between 0 and infinity. A scale of 0.5 on the X axis for example will halve the width of the frame. A scale of 2 will double it. To scale the frame proportionally, you have to use the same value for X and Y.

Rotation
   Rotates the frame along the Z axis; expressed in degrees. A negative value will rotate counter clockwise. This value can be > 360°, e.g. in animations you can rotate a frame 3 times around its Z axis by entering the value 1080° = 3 x 360°.

Mirror
   Mirrors the image along the X axis (left to right) or the Y axis (top to bottom).

.. admonition:: Panel Crop
   :class: refbox

   :menuselection:` --> Strip --> Sidebar --> Panel --> Crop`


.. figure:: img/panel-crop.png
   :scale: 50%
   :alt: Crop Property
   :align: Right

   Figure 5: Crop Property

Crop
   Cropping is the removal of unwanted outer areas from an image. Use (from) *Top*, *Left*, *Bottom*, and *Right* to remove pixels from the top, Left, ...

Crop is often combined with Transform, for example to create a Picture-in-Picture (PIP) effect.

.. admonition:: Panel Video
   :class: refbox

   :menuselection:` --> Strip --> Sidebar --> Panel --> Video`


.. figure:: img/panel-video-strip-movie.png
   :scale: 50%
   :alt: Video Property
   :align: Right

   Figure 5: Video Property

Strobe
   A strobe is a device used to produce regular flashes of light. In this context, the floating point number indicates that only each nth frame will be displayed. For example, if you set this to 10, the strip will only display frames 1, 11, 21, 31, 41... of the source. You can use this property to sync your video to a sound beat.

Reverse Frames
   The strip is played backwards starting from the last frame in the sequence to the first frame.

**Color**

.. figure:: img/panel-color.png
   :scale: 50%
   :alt: Color Property
   :align: Right

   Figure 6: Color Property

``Saturation`` Increases or decreases the color saturation or the vividness of an image.

``Multiply`` Multiplies the colors by this value. This will increases the brightness for values > 1. Using a value < 1 will reduce the brightness. A value of zero will produce a uniformly black image; the color code of black is RGB (0,0,0).

``Convert to Float`` Converts the multiply value to a float data.

.. todo::
   This is probably related to the color management and scene referred color values. To research.
  
**Time**

.. figure:: img/panel-time.png
   :scale: 50%
   :alt: Time Property
   :align: Right

   Figure 7: Time Property

``Channel`` Strips are placed in channels; rows stacked upon each other. Upon adding a movie clip, Blender searches for the next free channel to place the movie strip. With this property you can change the channel number, e.g. the row number of the strip. If the channel is already taken by another strip, the strip will be positioned at the next higher available channel.

``Start``: The starting frame number of the strip.

.. warning:: 
   The time codes in Blender are not very coherent. The Start frame is the original frame number where the strip is added or moved. But, you can trim the strip so that it starts later; this is done with the Strip Offset Start time code. Visually, you see in the sequencer that the strip starts later than the Start frame indicates.
   
.. todo::
   In the section on editing the time codes are discussed in more depth.

``Duration`` The length, in frames of the strip

``End`` Specifies the ending time and ending frame number for the strip. This value cannot be edited.

``Strip Offset Start/End``: Can be used to either extend the strip beyond the end frame by repeating the last frame. Or it can be used to shorten the strip, as if you were cropping the end frame. This is the same as adjusting the strip handles.

``Hold Offset Start/End`` Offset of the uncut strip content.
``Current Frame`` Position of the Playhead relative to the start of the active strip.


.. _source-panel:

**Source**

.. figure:: img/panel-source-movie-strip.png
   :scale: 50%
   :alt: Source Property
   :align: Right

   Figure 8: Source Property

``File`` The directory and filename that contains the source file. When a file is moved this field can be updated instead of re-creating the strip.

``Color Space`` To specify the color space of the source file.

.. todo::
   The following properties must be described in more detail

``MPEG Preseek`` Use Preseek field to tell Blender to look backward and compose an image based on the specified amount of previous frames (e.g. 15 for MPEG-2 DVD).

``Stream Index`` For files with several movie streams, use the stream with the given index.

``Deinterlace`` Removes fields in a video file. For example, if it is an analog video and it has even or odd interlacing fields.

``Resolution`` Dimension (width x height in pixels) of the active strip image output. This property is not editable. Note that scaling the strip will change the visual dimension of the frame but of course not its resolution.

**Custom Properties**

.. figure:: img/panel-custom.png
   :scale: 50%
   :alt: Custom Property
   :align: Right

   Figure 9: Custom Property

Here you can create custom properties for this.

.. todo::
   How and why can these custom properties be used in VSE? Metadata such as copyright?
