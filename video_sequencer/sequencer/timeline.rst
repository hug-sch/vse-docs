Timeline
--------

The concept *Timeline* can refer to different things. In Blender, it denotes in the first place the `Timeline Editor <https://docs.blender.org/manual/en/dev/editors/timeline.html>`_ , identified by a clock icon and used for manipulating keyframes and scrubbing the playhead (see figure 1). This Timeline Editor was originally intended for editing the animations in 3D modeling. For video editing, this editor is less useful.

.. figure:: /images/editors_vse_timeline-editor.svg
   :alt: Timeline editor

   Figure 1: The Timeline Editor in Blender

You can find the Timeline Editor also in the :doc:`Video Sequence Editor workspace </video_editing/setup/environment/workspace>`, all the way at the bottom of the screen. Only the header is visible; so you have to drag the horizontal top border to reveal the time units and eventual keyframes.

The use of *this* Timeline Editor within the Video Editor workspace is rather *limited* and a case could be made to remove it from the Video Editing workspace. Its functions can easily be overtaken by the Sequencer (see figure 2), which is right on top of it in the Video Editing Workspace.

The Sequencer has indeed also a kind of timeline on its own. Practically all the regular operations like zoom, move, ... can be done here. Only the Frame and Transport controls are missing. These can however easily be added to the workspace (see the addon by TintwoTin; `Playback_control_in_VSE_header.zip <https://github.com/tin2tin/Sequence_Editing>`_ ). 


.. figure:: /images/editors_vse_sequencer_timeline_sequencer.svg
   :alt: Sequencer timeline

   Figure 2: The timeline of the Sequencer Video Editor in Blender

The timeline of the sequencer is divided horizontally in channels and vertically in time units. The default *Visible Range* is from channel 0 to channel 7 and from time 0 to time 10s.

The header of the timeline is formed by a kind of ruler with time units. As you can see from figure 2, the time units are displayed in so-called SMPTE timecodes. A SMPTE timecode is a standard format, adopted by the Society of Motion Picture and Television Engineers (SMPTE) in the late 1960s. It is written as HH:MM:SS:FF, e.g. 00:01:12:06. This means the time after 1 minute, 12 seconds, and 6 frames. If your project has a framerate of 24 fps, the 6 frames will add another 0.25 seconds to the timecode.

You can change the timecode style. It's rather well hidden in User Preferences > Animation > Timeline (see figure 3). By default, the time units are shown with Minimal Info; see table 1 for the other options.

.. figure:: /images/editors_vse_sequencer_timeline_timecode-style.png
   :alt: Timecode style

   Figure 3: The Timecode Style in User Preferences

.. csv-table:: Table 1: Timecode style
   :header: "Type", "Style", "Comment"
   :widths: 35, 10,350

   Minimal info, 1+18, 1 second and 18 frames
   SMPTE (Full), 00:00:01:18,
   SMPTE (Compact), 00:01:18,
   Compact with Milliseconds, 00:01:6, with fps = 30
   Only Seconds, 1.6,

In Blender, you can choose to show the timeline in *seconds* or in *frames*. Use the command :kbd:`Ctrl + T` or the menu View > Show seconds. In figure 4, the timeline is shown in frames. As a video editor, you probably are most interested in time. It seems more natural to refer to a video fragment with a time indication, e.g. 00:01:15:10 or 1' 15'' and 10 frames than with a frame number, e.g. frame 55. You cannot enter the SMPTE timecode directly in the side panel, you have to enter the frame number. 

Because each project has a frame-per-seconds `fps` parameter, you can always derive one code from the other. In a 30 fps project:

* frame 155 is at time 115/30 = 3.8333 seconds or in SMPTE (Compact) notation: 00:03+25.
* time 2.5s falls somewhere within frame  2.5 * 30 = 75.

The conversion from frame to SMPTE code is done by a Python function *smpte_from_frame*. This function takes one parameter (the frame number) and converts it to a timecode.

Strips are placed in channels; rows stacked upon each other (see for example figure 2 with 2 channels). There are 32 channels available; although you can zoom out much further. The first channel 0 is unusable as a place to put strips. This is because it is used by the Sequencer Display to show a composite of all strips above channel 0.

Theoretically, the Timeline can span the frames from - |infinity| to + |infinity| and from channel 0 to channel 32. In practice, only a limited amount of frames and channels can be seen in the Sequencer. This range is called the *Visible Range*. There are three basic operations you can perform in the Timeline (see figure 1).

- Move: the Visible Range covers the same amount but different frames and channels. 
- Zoom: pack more (zoom out) or less (zoom in) frames and channels within the Visible Range.
- Navigate: move the playhead, so that you see another frame in the preview.

Please note that in a Move operation, the Visible Range can be moved horizontally, vertically or both. The area will not change. As a result of the Move, the playhead could fall out of view. The Zoom operation always start from the current Visible Range and will shrink or expand its area. Again, as a result the playhead could fall fall outside the Visible Range. In a Navigate operation, the Visible Range will never change, only the playhead will move.

.. figure:: /images/editors_vse_sequencer_timeline_move-size.svg
   :alt: Sequencer window

   Figure 1: Move, zoom & navigate operations in the Sequencer

.. |infinity| unicode:: 0x221E

.. toctree::
   :maxdepth: 3

   move
   zoom
   navigate

