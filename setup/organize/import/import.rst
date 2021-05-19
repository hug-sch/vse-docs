*******************
Import your footage
*******************

After setting up a central project directory with all your files (see :doc:`Creating a project directory </setup/organize/dir-structure/creating-directory-structure>`), you need to (1) import your footage into your project or timeline, (2) set the correct options, and (3) organize your timelines.

Importing
=========

.. note::
   Blender is - as all video editors nowadays - a non-linear editing (NLE) system. According to `wikipedia <https://en.wikipedia.org/wiki/Non-linear_editing>`_ non-linear editing is a form of offline editing for audio, video, and image editing, where the original content is not modified in the course of editing. In a linear system, a movie is edited by copying scenes from a source tape to a new tape, and in case of error (something forgotten) all the subsequent scenes must be recopied.
   
   It's probably superfluous to mention, but importing your assets will not change them in any way.

In Blender, you can use three methods to import footage.

1. Drag a video, sound, or image/image sequence on the timeline with the `Blender File Browser <https://docs.blender.org/manual/en/dev/editors/file_browser.html>`_. The Blender File Browser is the top-left window in the Video Editing workspace (see figure 1).
2. Add a strip with the shortcut key (Shift + A) or the Add menu to the Sequencer timeline and locate the desired file with a modified Blender File Browser version.
3. Drag and drop the desired video, sound, or image file on the sequencer timeline from the File Browser of the operating system.

.. figure:: img/methods.gif
   :alt: Import methods

   Figure 1: Three import methods

These three import techniques are clearly explained in a short video by `Mikeycal Meyers <https://www.youtube.com/watch?v=zslAZxC29rk>`_.

There are subtle but sometimes annoying differences between the three methods.

- Only with the Add (2nd) method can you add all of the :doc:`available strip types </setup/organize/strip-types/striptypes>`. The other methods only allow adding Movie, Sound, or Image/Image Sequence strips.
- Also, only the Add method offers the Import options (Scale To Fit, ...). A discussion of these options is in the next section.
- And also, only the Add method can import multiple files. Although you can select multiple files (as well in the Blender File Browser as in the OS File Browser), only one file (the first selected) is dropped on the timeline. Probably, for the same reason, it is not possible to add an Image Sequence.

Options
=======

.. figure:: img/options-moviestrip.png
   :alt: Import options Movie strip
   :scale: 70%
   :align: right

   Figure 2: Import options Movie strip

There are only import options for :doc:`strip types of group 2 </setup/organize/strip-types/striptypes>`: Movie, Sound, and Image/Image Sequence because they have an external source.

Relative Path
     The location of the video file is stored and available in the :ref:`Source panel <source-panel>`. This location can be relative - starting from the location of the Blend-file where the asset is imported - or absolute - starting from the root directory of the computer - (see `Blender manual <https://docs.blender.org/manual/en/dev/files/blend/open_save.html#relative-paths>`_ ). The Blend-file is of course already saved and the external file could not be on a different drive.

Start Frame
     As the name implies, the Start frame of the movie. This field is automatically filled in with the postion of the playhead; e.g. with the value zero is the playhead is at postion 0, 15 if the playhead is at position 15.

Channel
     The Channel to place the strip.The filled-in channel is always one, even if there is already a strip at that position. The newly added strip however will be placed at the next lower or higher free channel. The maximum number of channels is 32, even though you can see more channels.

Replace Selection
     Replaces the currently selected strips with the new strip.

.. todo::
     The Replace Selection option does not seem to do anything.
     
Fit Method
    The dimensions of the scene/project do not always fit the dimensions of the movie or image that you want to import. For example; you want to import an image of 500 (w) x 500 (h) into a scene of 640 (w) x 360 (h). It's obvious that the height of the image (500) will not fit into the height of the scene (360). The Fit method determines how images are scaled to fit inside the render area. This is done by changing the Transform Scale X and Y properties of the imported image.
    
    Scale to Fit
        The visual content of the strip fits exactly within the project’s Dimensions while maintaining the original aspect ratio. This means that -  from the above example (see also figure 3) - that the height of image (500) should be scaled to fit exactly in the height of the scene (360) with a factor of 0.72 (360/500). Because this method wants to maintain the original aspect ratio of the image, also the width should be scaled by 0.72, creating transparent vertical bands
    Scale to Fill
        The visual content of the strip spans the project’s Dimensions while maintaining the original aspect ratio. In our example: the largest dimension of the scene (640) should be filled with the image (500). So the image should be enlarged in the X axis with a factor of 1.28 (= 640 /500). 

        This may mean that portions of the original image no longer fit the content inside the rendered area.
    Stretch to Fill
        The visual content of the strip fills the project’s Dimensions. Note that, unlike the other two methods, Stretch to Fill does not maintain the original aspect ratio.

        This could result in a distortion of the original image (see figure 3).

    .. figure:: img/scale-methods.svg
       :alt: Import methods

       Figure 3: Three Fit methods

Sound
    If the video file contains an embedded audio channel, enabling this option will add a Sound Strip to the that contains the movie’s audio track. Disabling the option will only add a movie strip without the audio.

Use Movie Frame Rate
    This option sets the Scene Frame Rate of the Scene to the frame rate encoded in the added movie file. A mismatch of the project and strip frame rate is often the cause of :doc:`synchronzing problems </setup/organize/strip-types/movie>` with the audio. When a new Blend-file is created, the framerate is by default set to 24 fps. Unless this option is enabled, adding a movie with a framerate of 30 fps, will result in this kind of problems.


Organize timeline
==================

- Organize the channels: choice between keep audio & video together; could be done with parenting and the use of the VSQF addon
- another possibility is to have functional bands: e.g. channel 1-5: audio, 5-10: video

.. raw:: html

    <object data="img/importing-methods.svg" type="image/svg+xml"></object>
