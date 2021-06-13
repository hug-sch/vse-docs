
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

.. figure:: /images/vse_introduction_screen-layout.png

   Default Video Editing screen layout.

How to use this text
====================

The VSE documentation is split into 3 chapters, representing a typical workflow in a video editing project: :red:`(1)` Setup, :red:`(2)` Edit and :red:`(3)` Render. You can think of these phases also as : pre-editing, editing and post-editing.

Before even starting to edit a single video, you need to :red:`(1)` setup your :blue:`(1.1)` Work Environment and your specific :blue:`(1.2)` Project. Setting up your work environment includes: :green:`(1.1.1)` Customize the Video Editing Workspace, :green:`(1.1.2)` Install some Add-ons, :green:`(1.1.3)` Manage your User Preferences, and :green:`(1.1.4)` Tweak the Proxies & Cache system. 

A typical :blue:`(1.2)` project contains hundreds of files. Setting up a logical and comprehensible :green:`(1.2.1)` directory structure and appropriate :green:`(1.2.2)` Project Settings will improve your workflow. Then you can start :green:`(1.2.3)` Importing your footage and create various :green:`(1.2.4)` Strip types in your timeline.

Most of the work will be done in the :red:`(2)` Editing phase. Working within the timeline require some :blue:`(2.1)` basic timeline operations such as moving, zooming, selecting and navigating. The :blue:`(2.2)` montage of the final video with adding, splitting, moving, trimming, grouping, and deleting strips will probably take most of your time. When the rough montage is done, you can add some :blue:`(2.3)` effects such as transition and fade but also more advanced animation effects, including speeding and masking. This will give you a semi-final timeline. Then, you start :blue:`(2.4)` color grading and :blue:`(2.5)` editing the sound, although some authors start with the sound much earlier (for example when editing a music video).

When the editing is complete, you can start :red:`(3)` rendering the project. First, you have to :blue:`(3.1)` choose your codec and probably do some :blue:`(3.2)` post-processing in the compositor or FFMPEG. Sometimes you need subtitles.

This text contains also two supplemental chapters. Chapter :red:`(4)` is about specific workflows. Editing a documentary, an interview or a music video is very different from each other. As said, the sound editing will occur probably much earlier in the workflow for a music video than for a documentary. Chapter :red:`(5)` is about some extra-tools, you may need while editing; e.g. some useful Python or FFMPEG scripts.