
************
Introduction
************

In addition to modeling and animation, Blender can be used to edit video.
There are two possible methods for this, one being the :doc:`Compositor </compositing/introduction>`.
However, this chapter describes the other, the Video Sequence Editor (VSE), sometimes shortened to just "Sequencer".
The Sequencer within Blender is a complete video editing system that allows you to combine multiple
video channels and add effects to them. You can use these effects to create powerful video edits,
especially when you combine it with the animation power of Blender!

To use the VSE, you load multiple video clips and lay them end-to-end (or in some cases, overlay them),
inserting fades and transitions to link the end of one clip to the beginning of another.
Finally, you can add audio and synchronize the timing of the video sequence to match it.

.. figure:: /images/video-editing_introduction_screen-layout.png

   Default Video Editing screen layout.

How to use this text
====================

The VSE documentation is split into 3 chapters, representing a typical workflow in a video editing project: (1) Setup, (2) Edit and (3) Render your project.

Before even starting to edit a single video, you need to (1) setup your working environment. A typical project contains hundreds of files: video, audio, graphics, text and so on. You need to organize these assets in an efficient way. A logical and comprehensible (1.1) directory structure to hold these files is a prerequisite. Although Blender's Video Editing workspace is finetuned for the job, you may need to (1.2) customize this workspace to your specific needs. Also, the (1.3) Project Settings (e.g. resolution, framerate, ...) should be set before (1.4) importing your footage in the Sequencer's timeline. In some circumstances, you may need to (1.5) extend your working environment with add-ons or a proxy file system.

Then, you can start (2) editing. Working within the timeline require some (2.1) basic timeline operations such as moving, zooming, selecting and navigating. The (2.2) montage of the final video with adding, splitting, moving, trimming, grouping, and deleting strips will probably take most of your time. When the rough montage is done, you can add some (2.3) effects such as transition and fade but also more advanced animation effects, including speeding and masking. This will give you a semi-final timeline. Then, you start (2.4) color grading and (2.5) editing the sound, although some authors start with the sound much earlier (for example when editing a music video).

When the editing is complete, you can start (3) rendering the project. First, you have to (3.1) choose your codec and probably do some (3.2) post-processing in the compositor or FFMPEG. Sometimes you need subtitles.

This text contains also two supplemental chapters. Section (4) is about specific workflows. Editing a documentary, an interview or a music video is very different from each other. As said, the sound editing will occur probably much earlier in the workflow for a music video than for a documentary. Section (5) is about some extra-tools, you may need while editing; e.g. some useful Python or FFMPEG scripts. 