
*******************
Import your footage
*******************

After setting up a central project directory with all your files
(see :doc:`Creating a project directory </setup/organize/dir-structure/creating-directory-structure>`),
you need to (1) import your footage into your project or timeline,
(2) set the correct options, and (3) organize your timelines.


Importing
=========

.. note::

   Blender is - as all video editors nowadays - a non-linear editing (NLE) system.
   According to `wikipedia <https://en.wikipedia.org/wiki/Non-linear_editing>`_
   non-linear editing is a form of offline editing for audio, video, and image editing,
   where the original content is not modified in the course of editing.
   In a linear system, a movie is edited by copying scenes from a source tape to a new tape,
   and in case of error (e.g. something forgotten) all the subsequent scenes must be recopied.

   It's probably superfluous to mention, but importing your assets will not change them in any way.

There are three methods available to import footage. For a detailed description of these methods and their intricacies, see section :doc:`section Edit > Assembling > Adding </edit/assembling/adding/adding>`.

1. Add a strip with the shortcut key (Shift + A) or the Add menu to the
   Sequencer timeline and locate the desired file with a modified Blender File Browser version.
2. Drag a video, sound, or image/image sequence on the timeline with the
   `Blender File Browser <https://docs.blender.org/manual/en/dev/editors/file_browser.html>`_.
   The Blender File Browser is the top-left window in the Video Editing workspace (see figure 1).
3. Drag and drop the desired video, sound, or image file on the sequencer
   timeline from the File Browser of the operating system.

.. figure:: img/methods.gif
   :alt: Import methods

   Figure 1: Three import methods

These three import techniques are also clearly explained in a short video by
`Mikeycal Meyers <https://www.youtube.com/watch?v=zslAZxC29rk>`_.

There are subtle but sometimes annoying differences between the three methods.

- Only with the Add (2nd) method can you add all of the
  :doc:`available strip types </setup/organize/strip-types/index>`.
  The other methods only allow adding Movie, Sound, or Image/Image Sequence strips.
- Also, only the Add method offers the Import options (Scale To Fit, ...).
  A discussion of these options is in the next section.
- And also, only the Add method can import multiple files.
  Although you can select multiple files (as well in the Blender File Browser as in the OS File Browser),
  only one file (the first selected) is dropped on the timeline.
  Probably, for the same reason, it is not possible to add an Image Sequence.

Options
=======

.. figure:: img/options-moviestrip.png
   :alt: Import options Movie strip
   :scale: 70%
   :align: right

   Figure 2: Import options Movie strip

There are only import options for :doc:`strip types of group 2 </setup/organize/strip-types/index>`:
Movie, Sound, and Image/Image Sequence because they have an external source.

Relative Path
     The location of the video file is stored and available in the :ref:`Source panel <source-panel>`.
     This location can be relative - starting from the location of the Blend-file
     where the asset is imported - or absolute - starting from the root directory of the computer -
     (see `Blender manual <https://docs.blender.org/manual/en/dev/files/blend/open_save.html#relative-paths>`_ ).
     The Blend-file is of course already saved and the external file could not be on a different drive.

Start Frame
     As the name implies, the Start frame of the movie.
     This field is automatically filled in with the position of the playhead;
     e.g. with the value zero if the playhead is at position 0, or 15 if the playhead is at position 15.

Channel
     The Channel to place the strip. The filled-in channel is always one,
     even if there is already a strip at that position.
     The newly added strip however will be placed at the next lower or higher free channel.
     The maximum number of channels is 32, even though you can see more channels.

Replace Selection
     Replaces the currently selected strips with the new strip.

.. todo::
     The Replace Selection option does not seem to do anything.

Set View Transform
    When enabled (default), this option sets the View Transform to Standard on the first import of a Movie clip.
    You can find the View Transform property in the Properties Editor > Render Properties > Color Management panel.
    Most video files are encoded in the sRGB (=standard) color space.
    Color values can fluctuate between 0 and 1. In the 3D modeling world,
    however, color values can fluctuate between 0 and infinity, depending on the amount of light you add to a scene.
    Therefore, a different View Transform algorithm (e.g. Filmic) is used.
    For example, if you start your project within the Modeling workspace,
    the View Transform option is set by default to Filmic.
    A mismatch of this View Transform setting can cause huge delays in render time and distortions of colors.

Fit Method
    The dimensions of the scene/project do not always fit the dimensions of the movie or image that you want to import.
    For example; you want to import an image of 500 (w) x 500 (h) into a scene of 640 (w) x 360 (h).
    It's obvious that the height of the image (500) will not fit into the height of the scene (360).
    The Fit method determines how images are scaled to fit inside the render area.
    This is done by changing the Transform Scale X and Y properties of the imported image.

    Scale to Fit
        The visual content of the strip fits exactly within the
        project’s Dimensions while maintaining the original aspect ratio.
        This means that -  from the above example (see also figure 3) - that the height of image (500)
        should be scaled to fit exactly in the height of the scene (360) with a factor of 0.72 (360/500).
        Because this method wants to maintain the original aspect ratio of the image,
        also the width should be scaled by 0.72, creating transparent vertical bands.
    Scale to Fill
        The visual content of the strip spans the project’s Dimensions while maintaining the original aspect ratio.
        In our example: the largest dimension of the scene (640) should be filled with the image (500).
        So the image should be enlarged in the X axis with a factor of 1.28 (= 640 /500).

        This may mean that portions of the original image no longer fit the content inside the rendered area.
    Stretch to Fill
        The visual content of the strip fills the project’s Dimensions.
        Note that, unlike the other two methods, Stretch to Fill does not maintain the original aspect ratio.

        This could result in a distortion of the original image (see figure 3).

    .. figure:: img/scale-methods.svg
       :alt: Import methods

       Figure 3: Three Fit methods

Sound
    If the video file contains an embedded audio channel,
    enabling this option will add a Sound Strip to the that contains the movie’s audio track.
    Disabling the option will only add a movie strip without the audio.

Use Movie Frame Rate
    This option sets the Scene Frame Rate of the Scene to the frame rate encoded in the added movie file.
    A mismatch of the project and strip frame rate is often the cause of
    :doc:`synchronizing problems </setup/organize/strip-types/movie>` with the audio.
    When a new Blend-file is created, the framerate is by default set to 24 fps.
    Unless this option is enabled, adding a movie with a framerate of 30 fps, will result in this kind of problems.

The Image/Image Sequence strip has no ``Sound`` or ``Use Movie Frame Rate`` option
(because they don't make any sense in this context). The ``Use Placeholders`` option is added.
The Sound strip has in addition no ``Fit method`` option. The options ``Cache`` and ``Mono`` however are added.
These options are already described in the properties list of the
:doc:`Image Sequence strip <../strip-types/image>` and :doc:`Sound strip <../strip-types/sound>`.


Organize timeline
=================

Working with a long and complex timeline isn't easy.
Some kind of organization is needed in order to work as efficiently as possible.
The adagio "Leave your timeline in a state that someone else could pick it up" certainly applies.
Although organizing your timeline is probably a highly individual approach,
the following tips may offer some help.

- Blender VSE lets you place whatever strip on whatever channel.
  Many editors however group their channels into functional bands: e.g.
  channel 1-5: audio, 5-10: video, 11-15: effects.
  Within each band there can be sub-bands such as background music, voice-over, ambient sounds, ...
  Take a look at :doc:`Organize your assets </setup/organize/dir-structure/creating-directory-structure>` for a possible categorization.
- Some video editing programs link the video and embedded audio strip.
  The advantage of course is that moving one strip will move the other.
  Synchronization issues will less likely appear. In Blender VSE, the video and audio are not linked.
  A work-around is to use meta strips but this has the disadvantage that you cannot see the Sound wave.
  The VSQEF addon lets you parent strips: see `video tutorial <https://www.youtube.com/watch?v=rJg8xH8PyGc&t=40s>`_.
- Blender's VSE doesn't use the concept of a "bin": a virtual folder
  that lives only inside the project to hold references to source clips.
  But, it can easily be emulated by using multiple scenes.
  In figure 4, two scenes (Raw footage and Rough cut) are created (slide 1).
  All clips are added to the timeline of the Raw Footage scene.
  The Display Mode of the Outliner (top right window) is set to ``Scenes`` (slide 2).
  You can switch very easily between the timelines of both scenes by just selecting the scene in the Outliner (slide 3).

.. raw:: html

    <object data="/_static/images/bins.svg" type="image/svg+xml"></object>

Figure 4: How to create "Bins"? *Click on the image or use the keyboard arrows to view the next slide.*

When doing fiction, you could organize your footage in:

- Sequence: a series of scenes. S. Kubrick always told his stories in 8 sequences.
- Scene: a situation that plays out in one location in continuity.
- Shot: a camera set up to cover the entire scene or a part of it.
- Take: a recorded attempt out of many to get the shot right.
