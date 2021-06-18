#############
Video Editing
#############

The Video Editing documentation is split into 3 chapters, representing a typical workflow in a video editing project: :red:`(1)` Setup, :red:`(2)` Edit and :red:`(3)` Render. You can think of these phases also as : pre-editing, editing and post-editing.

Before even starting to edit a single video, you need to :red:`(1)` setup your :blue:`(1.1)` Work Environment and your specific :blue:`(1.2)` Project. Setting up your work environment includes: :green:`(1.1.1)` Customize the Video Editing Workspace, :green:`(1.1.2)` Install some Add-ons, :green:`(1.1.3)` Manage your User Preferences, and :green:`(1.1.4)` Tweak the Proxies & Cache system. 

A typical :blue:`(1.2)` project contains hundreds of files. Setting up a logical and comprehensible :green:`(1.2.1)` directory structure and appropriate :green:`(1.2.2)` Project Settings will improve your workflow. Then you can :green:`(1.2.3)` Import your footage.

The :red:`(2)` Editing phase start with the :blue:`(2.1)` montage of the final video, e.g. :green:`(2.1.1)` adding, :green:`(2.1.2)` selecting, :green:`(2.1.3)` splitting, :green:`(2.1.4)` moving, :green:`(2.1.5 )` trimming, :green:`(2.1.6)` grouping, and :green:`(2.1.7)` deleting strips. An extensive description of all available strip types is included in :green:`(2.1.1)`. When the rough montage is done, you can add some :blue:`(2.2)` effects such as transition and fade but also more advanced animation effects, including speeding and masking. This will give you a semi-final timeline. Then, you start :blue:`(2.3)` color grading and :blue:`(2.4)` editing the sound, although some authors start with the sound much earlier (for example when editing a music video).
 
When the editing is complete, you can start :red:`(3)` rendering the project. First, you have to :blue:`(3.1)` choose your codec and probably do some :blue:`(3.2)` post-processing in the compositor or FFMPEG. Sometimes you need subtitles.

Please note that there is also a special chapter about the :doc:`Video Sequence Editor </video_sequencer/index>` . There, you can find detailed info about basic timeline operations such as moving, zooming, and navigating the timeline.

This text contains also two supplemental chapters. Chapter :red:`(4)` is about specific workflows. Editing a documentary, an interview or a music video is very different from each other. As said, the sound editing will occur probably much earlier in the workflow for a music video than for a documentary. Chapter :red:`(5)` is about some extra-tools, you may need while editing; e.g. some useful Python or FFMPEG scripts.

.. toctree::
   :maxdepth: 3
   :numbered:

   setup/index
   edit/index
   render/render