***********
Time code
***********
As you can see from figure 1 (sidebar), the timeline codes are given in so called SMPTE-timecodes (first code) and frame numbers (second field). A SMPTE-timecode is a standard format, adopted by the Society of Motion Picture and Television Engineers (SMPTE) in the late 1960's. It is written as HH:MM:SS:FF, e.g. 00:01:12:06. This means the time after 1 minute, 12 seconds and 6 frames. If your project has a framerate of 24 fps, the 6 frames will add another 0.25 seconds to the timecode.

You cannot enter the SMPTE time code directly in Blender, you have to enter the frame number. The conversion from frame to SMPTE code is done by a Python function *smpte_from_frame*. This function takes one parameter (the frame number) and converts it to a timecode.

Blender keeps track of several time codes. Some - but not all - are exposed in the sidebar under the Strip > Time panel (see figure 1).

.. figure:: img/time_code.svg
   :alt: Time properties

   Figure 1: Time properties of a Movie strip.

With these time codes, Blender can calculate and draw the strip bars in the Preview section of the Sequencer.  The most important ones are of course *Start* and *Duration*. The *Start* field marks the position (frame number) from which all further calculations are done. The *Duration* is the number of frames of this strip.

.. warning::
    The *Start* field is NOT the same as the actual start of a strip; the position that you see in the Preview. It is the original start position of a strip that is not trimmed or cut. If you've added a strip at frame 5 and later on you trimmed that strip with a Start offset of +7 frames, then the visible strip will start at frame 12 but the *Start* field still says frame 5 (see figure 1).

    The *Duration* field however shows the actual duration. If a strip is trimmed or cut, this field will not show the original *Duration* but the Duration as you can see it in the Preview.

With the *Start* and the *Duration* the *End* field can be calculated.  This is what Blender insinuates by making this field non-editable. However, there is no reason for that and changing this field could for example result in the recalculation of the *Duration*.

In figure 1, the original strip has a *Duration* of 30 frames. It starts as frame 5; so the *end* should be at frame 35. Because there is some trimming, the actual start is at frame 12: *Start* + *Strip Offset Start*. The actual end is at frame 27: *(Original) End* - *Strip Offset End*. The (actual) *Duration* is thus 15 frames: *(Actual) End - (Actual) Start*. The Offset values could be made visible in the Preview as small blue bars with the Show Overlays button (tp right in figure 1).

The *Hold Offset Start* and *Hold Offset End* are used to store the position of a strip cut. The *frame_still_start* and *frame_still_end* codes are not exposed in the side bar and are used to extend a one frame strip, e.g. a still image.

.. note::
   The naming of the fields in the previous paragraph is not quite accurate. There isn't any field with the name *Actual Start*. On the other hand, Blender's naming system also isn't very logical. You can look up the name of every Python generated field by enabling Developer Extras, User Tooltips and Python Tooltips in the Blender Preferences > Interface > Display. Hovering over the field in the UI. For example, the *Start* field is called  *frame_start* and the *End* field is called *frame_final_end*.

There are 12 time code fields in Blender. We discuss them more in detail in the following sections.