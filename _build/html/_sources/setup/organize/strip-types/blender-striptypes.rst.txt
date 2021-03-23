*********************
Blender's strip types
*********************

.. figure:: img/strip-types.svg
   :scale: 100 %
   :alt: Available strip types
   

   Figure 1: Available strip types with color code and properties.

A strip is a sequence of images, displayed as a colored horizontal bar. Each image occupies one frame in the timeline. In figure 1 the 8 basic strip types are added (menu :menuselection:`Add` or shortcut key Shift+A). They run from frame 1 up to frame 300. 

The strip types are separated into 4 groups: (1) the input source is created in another Blender module (2) the input source is external (3) the input is created within the Sequence Editor (4) the input source is another strip.

Each strip type is uniquely color-coded. In figure 1, from top to bottom: Scene strip (Light Green),  Mask strip (Dark Grey), Movie strip (Aquamarine), Sound strip (Turquoise), Image/Sequence strip (Brown), Color (Light Grey + selected color), and , Text (Purple).

Each strip has multiple Properties. Figure 1 shows the Properties of a Movie strip. This sidebar can be displayed with :menuselection:`View --> Sidebar` or shortcut key N. These Properties are organized into sub panels, e.g. Compositing, Transform, Crop, ... and preceded by a header with the icon of the strip type, the name of the strip and a Mute checkbox. You can name or rename your strips here. If the Mute button is checked the strip will still be visible in the Sequencer but will not produce any output.

A. Movie strip
==============

The input source of a movie strip is a video file with extension ``.mp4``, ``.mpg``, ``.mpeg``, ``.dvd``, ``.vob``,  ``.avi``, ``.mov``, ``.dv``, ``.ogg``, ``.ogv``, ``.mkv``, ``.flv``, or ``.webm`` (see `video formats <https://docs.blender.org/manual/en/dev/files/media/video_formats.html>`_). Blender uses the ``ffmpeg`` library to process the video files. Which codecs are available depends on the operating system and FFmpeg version.

Each video file contains a sequence of image frames (the actual movie) and some meta information such as resolution and frame rate (fps). The resolution info is exposed in the source panel. Unfortunately, the source FPS is not.

.. warning:: 
   It is important that the Project Settings parameters are in accordance with the strip parameters. For example, if the project is set to a frame rate of 30 fps, and your clip is only 24 fps, then the clip will appear accelerated. A 1 second play back time will contain 30 frames or 1.2 s of original footage.

   Also, if your clip has variable framerate; e.g. footage from some smart phones, then you'll get an audio sync problem because Blender uses a constant frame rate.

The movie strip is the most commonly used strip type and has a lot of properties. They are organized in panels in the sidebar.

**Compositing**

.. figure:: img/panel-compositing.png
   :scale: 50 %
   :alt: Compositing property
   :align: Right

   Figure 2: Compositing Property

``Blend`` When two strips are placed on top of each other, e.g. channel 1 and channel 2, the strip of channel 1 is completely covered by the strip of channel 2 as if channel 1 does not exist. This is because the Blend Mode of the channel 2 strip is set to Cross (default value). The Blend mode of a strip on the upper channel specifies how the strip on a lower channel should combine or blend with the strip on the upper channel. There are 27 blend modes, some with `exotic names <https://docs.blender.org/manual/en/dev/video_editing/sequencer/strips/effects/index.html>`_ as "Color Dodge" or "Color Burn".

.. todo::
   The blend modes (see above) and their functional differences are described in detail in section ...

``Opacity`` The opacity or alpha value of the image is multiplied with this value. A value of 1 has no effect on the opacity of the strip. A value of zero will make the strip fully transparent. See the `Mask strip`_ for more details on transparency/opacity.

**Transform**

.. figure:: img/panel-transform.png
   :scale: 50%
   :alt: Transform Property
   :align: Right

   Figure 3: Transform Property

``Position X, Y`` The view area of the sequencer output is set with the project dimensons (see :doc:`../dir-structure/creating-directory-structure`). A movie is centered (and scaled) within this view area. With the position X, Y values, you can move the frame along the X and Y axis. The values are expressed in pixels.

``Scale X, Y`` With this value, you can scale the image on the X and Y axis. It is a number between 0 and infinity. A scale of 0.5 on the X axis for example will halve the width of the frame. A scale of 2 will double it. To scale the frame proportionally, you have to use the same value for X and Y.

``Rotation`` Rotates the frame along the Z axis; expressed in degrees. A negative value will rotate counter clockwise. This value can be > 360°, e.g. in animations you can rotate a frame 3 times around its Z axis by entering the value 1080° = 3 x 360°.

``Mirror``  Mirrors the image along the X axis (left to right) or the Y axis (top to bottom).

**Crop**

.. figure:: img/panel-crop.png
   :scale: 50%
   :alt: Crop Property
   :align: Right

   Figure 5: Crop Property

``Crop`` Cropping is the removal of unwanted outer areas from an image. Use (from) *Top*, *Left*, *Bottom*, and *Right* to remove pixels from the top, Left, ...

Crop is often combined with Transform, for example to create a Picture-in-Picture (PIP) effect.

**Video**

.. figure:: img/panel-video-strip-movie.png
   :scale: 50%
   :alt: Video Property
   :align: Right

   Figure 5: Video Property

``Strobe`` A strobe is a device used to produce regular flashes of light. In this context, the floating point number indicates that only each nth frame will be displayed. For example, if you set this to 10, the strip will only display frames 1, 11, 21, 31, 41... of the source. You can use this property to sync your video to a sound beat.

``Reverse Frames`` The strip is played backwards starting from the last frame in the sequence to the first frame.

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

B.Sound strip
=============

The input source of a Sound strip is an audio file with extension ``.AAC``, ``.AC3``, ``.FLAC``, ``.MP2``, ``.MP3``,  ``.opus``, ``.PCM``,  or``.vorbis`` (see `audio formats <https://docs.blender.org/manual/en/dev/files/media/video_formats.html>`_). You can add a Sound strip directly from one of the above mentioned filetypes. It is also indirectly created when you add a Movie strip from a video file with an embedded audio channel. Blender will automatically extract the sound strip and put it in the channel beneath the video strip (if there is room).

.. warning::

   Sometimes, after adding a Movie strip, you will notice that the Movie and Sound strip aren't the same length. This is the result of a mismatch between the Frame rate (fps) of the project and the video clip. Suppose, you are adding a 24 fps video with a duration of 1 second or 24 frames to a 30 fps project. The embedded audio in the video file is of course synchronized with the frame sequence of the video. Frame 1 of the video file is synced with a specific time code in the audio, and so is frame 2, frame 3, ... But, due to the different framerates, frame 30 in the sequencer is really frame 24 (1 s) in the video file, which is the end of the video and embedded audio. The Sound strip therefore will end at frame 24 because sound cannot be compressed without changing the Pitch.

There are no Compositing, Transform, Crop, Video and Color panels for the Sound strip. The Header, Time, Source, and Custom panels are the same as for a Movie strip. The following properties are specific for sound strips.

**Sound**

.. figure:: img/panel-sound.png
   :scale: 50%
   :alt: Sound Property of Sound Strip
   :align: Right

   Figure 10: Sound Property of Sound Strip

``Volume`` The volume of the sound. Setting the Volume to zero will mute the sound, a value of 1 results in the original sound level and a value > 1 will increase the sound level. However, does a sound with level 2 sounds double as loud as the original; a more detailed explanation is given in the advanced section.

.. todo::
   Refer here to the advanced section with text about sound level.

``Pitch`` Pitch (lower versus higher tones) is closely related to the frequency of a sound. The Pitch value of the Sound strip will change the playback speed or frequency of the sound. Increasing the value will make the sound appear higher in tone, decreasing will lower the tone. Because the playback rate is also changed, the length of the sound is changed. This is however not visually represented in the timeline. The Sound strip appears equally long as before but the sound will stop earlier or premature.

``Pan`` Depending on your sound system, you have one, two or more speakers. Panning is the distribution of the sound over those speakers. It is mainly used to pan (distribute) the audio from left and right channels.  Pan values can be between -2 and 2. A value of zero means front/center (12 o'clock). Equal amount of sound is sent to the left and right speaker. A value of -1 means that all sound is sent to the left channel and 1 to the right (10 o'clock). And a value of +1 means that the sound will appear at 2 o'clock).  In case of multichannel audio (rear speakers) you can pan to those with the higher values: -2 (7 o'clock) and +2 (5 o'clock). So this value basically represents the angle at which the sound is played. Only works for mono sources.

``Display Waveform`` Display an approximate waveform of the sound file inside of the sound strip. The waveform reflects strip volume and its animation using keyframes. If the waveform is not displayed, you'll have to turn on the Overlays (button at the top right; see figure 10).

``Mono`` Mixdown all audio channels into a single one.

``Pack`` Packing the sound file means that the sound is embedded -not linked- in the blend-file. This can ease the job of transferring a project to another computer because you have to distribute only one file. But, remember, we advocate the use of a single, all-containing project folder  (see :doc:`../dir-structure/creating-directory-structure`).

``Caching`` The sound file is decoded and loaded into RAM for fluent playing.


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

``File``: The filename of the image for that particular frame, e.g. *-0001.png, *-0002.png, *-0003.png, ... 

``Color Space``: see `Movie strip`.

``Alpha``: Premultiplied (RGB channels in transparent pixels are multiplied by the alpha channel) or Straight (RGB channels in transparent pixels are unaffected by the alpha channel) of the image.

``Change Datafile``: replaces the complete image sequence with the selected images.

``Resolution`` See `Movie strip`

D. Clip strip
==========

A clip strip is created from the output of the Movie Clip Editor. There is nothing in the Clip menu unless you've opened media (video or images) in the Movie Clip Editor. At all other times it's just a blank menu. The Movie Clip Editor is used to create advanced edits such as motion tracking and advanced masking. See special workflows for an example.

The property panels of Compositing, Transform, Crop, ... are the same as in the Movie Clip Editor. There isn't any Source panel because the Clip strip is created from an in-memory data block of the Movie Clip Editor. There can be multiple data blocks and they are stored within the Blend-file upon saving.

**Video**

.. figure:: img/panel-video-strip-clip.png
   :scale: 50%
   :alt: Video Property of Clip Strip
   :align: Right

   Figure 12: Video Property of Clip Strip


Two extra properties are added underneath the Video panel.

``Tracker: Stabilize 2D clip`` The purpose of Tracking in the Movie Clip Editor is mostly to stabilize the video. With this checkbox you can use the stabilized version of the clip.

``Distortion: Undistort clip`` Stabilizing of a video is done by moving and rotating the video. With this option you can remove the distortion of the clip which is the result of stabilizing it.


E. Scene strip
==============

Blender has next to its VSE also a very impressive 3D and 2D modeling environment. You can model and render animated realistic scenes with it. But, instead of rendering out that scene to a video, and then inserting the video file in the sequence editor, you can insert the scene directly. Scene strips are a way to insert the render output of another scene into your sequence.

The strip length will be determined based on the animation settings in that scene. 

.. warning::

   Each scene has its own Video Sequencer. Scene strips cannot be used to insert the sequence's own scene. If you have a 3D animation in scene_1, you can insert it as a scene strip in scene_2 but not in scene_1.

The Compositing, Transform, Crop, Video, Color, Time, and Custom panels are unchanged. In the Time a new property is added: ``Original Frame Range`` . As the name indicates, this new property shows the the number of frames of the original scene held. A new Scene panel is also added.

**Scene**

.. figure:: img/panel-scene.png
   :scale: 50%
   :alt: Scene Property of Scene Strip
   :align: Right

   Figure 13: Scene Property of Scene Strip


``Scene header`` with logo, name and link/unlink checkbox. This header seems to be a duplicate of the header of the Properties Sidebar.

``Input`` Choice between Camera or Sequencer. The original Scene -where this Scene strip came from- can also have a Video Sequencer. Therefore, the output of that scene could be generated from that Video Sequencer or from the camera/compositor of that scene. In the original scene, this could be set in the Post Processing panel of the Output Properties. But, of course, it is not a good habit to change this setting from within another scene. So, With this input choice, you can choose between the two possibilities.

``Camera`` The same reasoning holds for multiple cameras. The active camera is set in the original scene. But the receiving scene can choose to use another camera. If the original scene has multiple cameras, you can choose here which camera to use. This is very useful in multicam-editing.

.. todo::
   Add info for Volume (meaning of slider value), further explanation for show grease Pencil and use of Transparent.
    
``Volume`` The volume of the original audio can be increased (> 1) or reduced (< 1) with this setting.

``Show Grease Pencil`` Shows Grease Pencil strokes in OpenGL previews.

``Transparent`` Creates a transparent background. This is useful for doing overlays like rendering out Grease Pencil films via the Sequencer. 


F. Mask strip
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

G. Color strip
==============

The Color strip is a sequence of 25 frames with a solid color. Its Duration is set by the same mechanism as the Image strip. The resolution is derived from the Project Settings and by default takes the complete movie screen area.

You'll use this strip heavily to create some custom transitions and in combination with the Crop and/or Transform property to create some horizontal or vertical colored bars.

The Compositing, Transform, Crop, Video, Color, Time, and Custom panels are unchanged. An Effect panel is added to the Properties. The existing Color panel has some overlap with the Effect panel. The Time panel has no Strip Offset and Hold Offset properties. 

**Effect**

.. figure:: img/panel-effect-strip-color.png
   :scale: 50%
   :alt: Effect Property of Color Strip
   :align: Right

   Figure 15: Effect Property of Color Strip

With the vertical slider you can set the brightness of the color. Clicking on the horizontal slider will display a standard Color Picker.

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







