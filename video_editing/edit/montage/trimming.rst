Trimming
--------

Trimming is changing the duration of a strip by altering the In and Out point. In figure 1, the original strip of channel 2 starts at frame 1 and has a duration of 11138 frames. It is duplicated to channel 3 and trimmed. The new In point is at frame 2226 (1 + Strip Offset Start) and the new Out point at frame 7665 (Duration - Strip Offset End). As already discussed in the section on the :ref:`Time panel <time-panel>` or the :doc:`Split operation  <splitting>` trimming and splitting is done with the use of the Strip Offset fields.

.. figure:: /images/video_editing_edit_montage_trimming.png
   :alt: Example of trimming

   Figure 1: Trimming a movie strip

Trimming of strips is mostly done with the mouse. You can however also change the Strip Offset fields directly by entering a value with the keyboard or use the slider of the property. Values can be negative. This will result in duplicating (freezing) the first and/or last frame.

:kbd:`LMB Click` on handles and dragging
    The *Strip Offset Start* property of a strip could be selected by :kbd:`LMB Click` on the left handle of the strip. In figure 1 this handle has a white color for the selected and active strip and an orange color for the selected but non-active strip. Holding the LMB down and then moving the mouse left/right changes the IN point of the selected strips by the number of frames you moved it. The frame number label at the bottom left corner of the strip displays the frame number of the new IN point, only if the height of the strip bar is sufficient (see figure 1).

    If you have a 20-image sequence strip, and drag the left handle to the right by 10 frames, the strip will start at image 11 (images 1 to 10 will be skipped). Use this to clip off a roll-up or undesired lead-in. Dragging the left arrow left will create a lead-in (copies) of the first frame for as many frames as you drag it. Use this when you want some frames for a transition at the start of the clip.

    The *Strip Offset End* of a strip could be selected by :kbd:`LMB Click` on the right handle of the strip; holding it down (or pressing G grab) and then moving the mouse changes the OUT point within the strip. The frame number label at the bottom right corner of the strip displays the frame number of the OUT point.

    Dragging the right arrow to the left shortens the clip; any original images at the tail are ignored. Use this to quickly clip off a roll-down. Dragging the right arrow to the right extends the clip. For movies and images sequences, more of the animation is used until exhausted. Extending a clip beyond its end results in Blender making a copy of the last image. Use this for transitions out of this clip.

    You can select multiple left or right handles of different strips with :kbd:`Shift LMB`. The selected handles are colored: white for the active strip and orange for the non-active strips. :kbd:`LMB Click & drag` on any selected handle will move all selected handles in the same direction as your mouse movement and with the number of frames that the mouse is moved.

.. note::
    Selecting handles can be done with the :kbd:`LMB`, the special Box Select with Handles (:kbd:`Ctrl B`) or the the menu Select > Handle; see section on :doc:`Selecting <selecting.rst>` for more details.

:kbd:`LMB Click` on handles and :kbd:`G` (Grab)
    In stead of :kbd:`LMB Click` on handles and dragging, you could also select all handles and press :kbd:`G`. This will result in the same trimming. The advantage is that you don't need to click and drag on a strip area. It is sufficient to press :kbd:`G` and move the mouse (where ever it is positioned).

:kbd:`LMB Click` on strips and :kbd:`E` (Extend)
    You can move or extend/shorten (thus, trimming) selected strips *without* selecting the handles with the :kbd:`E` key or the menu Strip > Transform > Move/Extend from Current Frame key. However, the position of the Current Frame (playhead) and the initial mouse position are important here.
   - If the playhead is outside the range of the selected strips, the :kbd:`E` will move the all selected strips in the direction of the mouse movement. This mimics the move behavior of an entire strip with :kbd:`G` key.
   - If the playhead is within the range of (some) selected strips, the :kbd:`E` key will trim the selected strips. If the mouse is at the left side of the playhead, the IN points of the selected strips will follow the direction of the mouse (as if trimming with the left strip handle). If the mouse is at the right side of the playhead, the OUT point will follow the direction of the mouse (as if trimming with the right strip handle).

    In summary, all selected strip handles from the “mouse side” of the current frame indicator (playhead) will transform together, to move or extend/shorten the selected strips.

Clear strip offsets: :kbd:`ALT O`
    All the trimming of selected strips can be cleared with the :kbd:`Alt O` or the menu Strip > Transform > Clear Strip Offset. The Strip Offset Start and End fields are reset to zero for the selected strips.

Precision trimming
    Although the movie strips of the sequencer timeline can display thumbnails (Show Overlay > Thumbnails), trimming with precise visual feedback is not possible with these thumbnails.

    The Preview window however only shows the Current Frame (frame at the position of the playhead) by default. With the menu View > Preview during Transform of the Preview window, you can enable precision trimming. The Preview window will temporarily display the frame at the position of the selected handle of the active strip (see figure 2).

.. figure:: /images/video_editing_edit_montage_trimming_preview_during_transform.gif
   :alt: Preview during Transform
 
   Figure 2: Trimming with Preview during Transform enabled

:kbd:`Esc`
    Pressing :kbd:`Esc` *while* trimming will reset the strip handles to the original position and will cancel the trim operation.



