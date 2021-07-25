Moving
------

Moving strips in the timeline is of course a basic operation in video editing. Figure 1 shows a few possibilities.

.. figure:: /images/video_editing_montage_move.svg
   :alt: Moving strips
 

   Figure 1: Moving strips in the Sequencer


LMB - drag
   You can select one or more strips and drag them to a new location. Releasing the :kbd:`LMB` will place the strip at the new location. Pressing :kbd:`Escape` or :kbd:`RMB` (while still holding :kbd:`LMB`) will cancel the movement. From the moment, you start dragging a *Grab* operation (see below) is started and new options are available.  

Grab
   In figure 1 the first strip is selected and the :kbd:`G` key is pressed. Note that a statusbar appears with some options, the header is temporarily replaced by a message, the cursor shape changes to a move-icon and the Start and End frame appear within the strip. These are all signs that you are in Grab mode.

   The Grab or G-command is universal in Blender and works the same in most editors. It is also accessible through the menu: Strip > Transform > Move.
   
   * Select one or multiple strips. They can be in different channels. See section on `selecting <selecting>`_ for various methods. If you have selected with the mouse, you can release the mouse button.
   * Press :kbd:`G`. The location of the mouse pointer is irrelevant but it is good practice to have the mouse on top of the to-be-moved strip. The Move icon will then nicely follow the strip bar.
   * Move the mouse horizontally, vertically or both. The strip bar will jump to the next available location. You can move past the border (although you want see where you will drop the strip).
   * Press :kbd:`Escape` or :kbd:`RMB` to cancel the movement or :kbd:`LMB - Click` or :kbd:`Enter` to confirm the operation. The selected strips will then be locked at the new location.

Grab - :kbd:`Shift`
   Moving a strip with the :kbd:`Shift` button pressed will move in small increments; eventually frame by frame. The increment size depends on the zoom level (larger steps when zoomed out).

Grab - :kbd:`Arrow Left/Right`
   After :kbd:`MMB - drag` or :kbd:`G`, you can move left or right by one frame with the :kbd:`Arrow - Left` or :kbd:`Arrow - Right`. This method won't work with the Up or Down arrow keys to change channel number.

Grab - number
   Pressing :kbd:`G`, followed by a positive number X will move the strip horizontally to the right with X frames. So G 10 will move the strip 10 frames to the right. A negative number will move the strips to the left. As always, finish with Escape to cancel or Enter (Click) to confirm.

Grab - X/Y
   You can restrain the movement to the horizontal X-axis or to the vertical Y-axis. So, Grab Y will move the selected strips vertically to a new channel, without changing horizontal position.

Grab - X/Y - number
   Combines the previous two commands. So, G Y 2 will move the strip 2 channels up and G X -10 will move the strip 10 frames to the left.

   .. todo::
      If you want to specify the movement in seconds, you can always enter the necessary calculation. Suppose, that your project has a fps = 24, then moving a strip 5 seconds is done by G X 5*24

Snapping
-------- 

.. figure:: /images/video_editing_montage_move-guides-icon.png
   :alt: Snapping guides
   :scale: 50%
   :align: right

   Figure 2: Snapping guides

If there is only one strip in the sequencer, then you can move that strip freely around and there will be no snapping. However, most of the time this is not the case and snapping could occur. The moved strip is clamped to another strip and the edges are aligned on consecutive frames. Snapping can also occur with the playhead. The moved strip is then aligned with the playhead. 

Snapping can be induced by *moving the strip* **or** by *moving the handles* (and thus changing the strip duration). There are currently two modes: with and without snapping guides. You can toggle the snapping guides by clicking on the magnet-icon in the middle of the header or with the shortcut key :kbd:`Shift - Tab` (see figure 2).

Without snapping guides
.......................

Moving a strip, so that it (partially) overlap with another strip, will create a temporary red outline around the moved strip, indicating that the strip can't be moved there (without overwriting) and will be moved further away and snapped to either side of the overlapping strip. Which side? The moved strip will snapped to the start of the overlapped strip, if the midpoint of the moved strip is closer to the start of the overlapped strip. Otherwise, it will be snapped to the end of the overlapped strip. Contiguous strips (without any gap between them) are considered as *one* longer strip.

.. figure:: /images/video_editing_montage_move-guides-snapping-side.png
   :alt: Snapping side
   :align: center


   Figure 3: Snapping side (without guides)

In figure 3, strip-1 is moved on top of the contiguous strips 2 & 3. Because the midpoint of strip-1 is closer to the Start of the strip-2 + strip-3 combination, it will be snapped to the Start of strip-2.

It is not always easy to see where the moved strip will go. Snapping guides can help here a lot.

With snapping guides
....................

You can enable the snapping guides with the magnet-button (see figure 2). A thin white guide will appear whenever an edge of the moved strip is close (< 15 pixels) to an edge of another strip (see figure 4). *All* channels are taken into account. So, in a crowded scene, there can be lot of snapping guides (but only those within 15 pixels are shown).

Holding down the :kbd:`Ctrl` key while moving a strip, will toggle the *Show Guides* command. So, if *Show Guides* is enabled, you can disable it while moving the strip by holding down the :kbd:`Ctrl` key.

.. figure:: /images/video_editing_montage_move-snapping-guides.svg
   :alt: Snapping guides

   Figure 4: Snapping guides

Figure 4 shows all possible snapping guides with 3 strips. The top-panel represents the original situation (before moving strip-3). Because there are two other strips, there are 8 possibilities to snap. The Start frame of strip-3 can snap to the Start and End frame of strip-2; and so can the End frame (= 4 possibilities; middle row in figure 4). The same reasoning holds for the edges of strip-1 (bottom row of figure 4).

(a) The Start frame of strip-3 is snapped to End frame of strip-2. Result: Strip-3 is appended to strip-2. This is in fact the original situation. Because there are no strips to the right of strip-2, this is a legal move and the border of strip-3 is colored in white.

(b) The End frame of strip-3 is snapped to the End frame of strip-2. This could cause an Overwrite of strip-2; so the border of strip-3 is colored red. Result: Strip-3 is moved to the next available location: End frame of strip-2 because the midpoint of strip-3 is closer to the End frame than to the Start frame.

(c) The Start frame of strip-3 is snapped to Start frame of strip-2. This is again an illegal operation; so the border is red and the result is that strip-3 is appended to strip-2.

(d) The End frame of strip-3 is snapped to the Start frame of strip-2. This could be a normal operation if the gap between strip-1 and strip-2 was big enough to hold strip-3. Unfortunately, this is not the case; so the border of strip-3 is colored red and the strip is once again appended to the End of strip-2.

(e) The Start frame of strip-3 is snapped to End frame of strip-1. As in (d), this could be a normal operation but again, the gap is not big enough; so strip-3 is moved again to the End of strip-2 and the border is colored red.

(f) The End frame of strip-3 is snapped to the End frame of strip-1. This is an illegal operation because strip-1 could be overwritten. The border is colored red. Strip-3 is moved to the Start frame of strip-1 because the midpoint of strip-3 is closer to the Start than the End frame of strip-1.

(g) The Start frame of strip-3 is snapped to Start frame of strip-1. Strip-1 could be overwritten; so the border of strip-3 is red. The result is that strip-3 is moved to the front of strip-1.

(h) The End frame of strip-3 is snapped to the Start frame of strip-1. There is plenty of room before strip-1; so this could be a normal operation (white border). Strip-3 is moved in front of strip-1.

It's a little confusing that for example, the snapping guide in figure 4-e seems to implicate that the moved strip will be inserted between strip-1 and strip-2. As explained, this is not the case, *unless* you activate the Insert-mode (see later).

The snapping guide tool has 5 options (see figure 2).

* Current Frame: the playhead (= current frame) is counted as a supplemental edge to snap on. So, the moved strip can either be snapped on to an edge of another strip or to the playhead, whichever is closest to the midpoint of the moved strip.
  
* Hold Offset: Strips can be the result of a Hold Split operation (see :ref:`Hold Split <hold-split-command>`). For example, in figure 5, the Hold Offset Start is at frame 1133 while the first 250 frames are freezed.

   .. figure:: /images/video_editing_montage_move-snapping-hold-split.svg
      :alt: Snapping Hold Split

      Figure 5: Snapping to the Hold Offset Start field

* Muted strips/Sound Strips: when you move a strip, most of the time you don't want to snap this strip to Muted (hidden) or Sound strips. These options are disabled by default, but you can swith them on here.
  
* Snap Current Frame to strip start or end:

.. todo::
   Research Snap Current Frame option.

Inserting
---------

Moving Strip-3 between strip-1 and strip-2 in figure 6 will need an Insert-mode. Simply moving the strip will snap strip-3 to either the Start of strip-1 or the End of strip-2, depending on the mouse position.

If you want to insert strip-3 between the other 2 and thus making room by shifting strip-2 to a later time, you need to hold the :kbd:`Alt` key while moving. Pressing :kbd:`Enter` or :kbd:`LMB - Click` will insert the strip. The message to do this appears at the left side in the header of the preview (see figure 6): *Sequence Slide: -76,0, (G or Alt) Expand to fit ON*. So, pressing the :kbd:`Alt` key while moving will set *Expand to fit ON*. Releasing the key will toggle the message to *Expand to fit OFF*. 

.. figure:: /images/video_editing_montage_move-snapping-insert.svg
   :alt: Insert mode

   Figure 6: Inserting a strip

The Insert mode works also with multiple, selected clips. If there are any gaps between the moved strips, these  will be preserved. 

Snap to the playhead
--------------------

Select one or multiple clips. They can be spread over multiple channels. Press :kbd:`Shift - S` to snap the selection to the playhead.

.. Warning::
   If multiple strips are selected, all of them will start at the playhead. The relative position to each other will not be preserved and all the strips are spread over different channels. This command is probably only useful for strips that share a common Start frame; eg. Movie strips with their accompanying Sound strips.

.. note::
   You can move strips between:
   
   * Scenes: copy the strips (:kbd:`Ctrl - C`), switch to the other scene and paste (:kbd:`ctrl - V`). All strip settings will be copied, *except* the animation keyframes.
   * Projects: import the scene with the wanted strips into the current project with the menu File > Append.

Remove gaps
-----------

Remove blank columns in the timeline window, starting from project Start (usually frame 1). A blank column is a time/frame location where there isn't any strip in any channel. In other words, the Preview window is empty for that time/frame location.

You can invoke the command with the menu: Strip > Transform > Remove Gaps or with the :kbd:`Backspace` key. After the command is issued, you can tick the *All Gaps* option to remove other gaps or you can press :kbd:`Backspace` several times to remove the other gaps.