Snapping
-------- 

.. figure:: /images/video_editing_montage_move-guides-icon.png
   :alt: Snapping guides
   :scale: 50%
   :align: right

   Figure 1: Snapping guides

If there is only one strip in the sequencer, then you can move that strip freely around and there will be no snapping. However, most of the time this is not the case and snapping could occur. The moving strip is suddenly clamped to another strip and the edges are aligned on consecutive frames. This occurs whenever those edges are within a distance of less than 15 pixels.

Snapping can also occur with the playhead. The moving strip is then aligned with the playhead, whenever one of the edges is within that distance of 15 pixels. 

Snapping can be induced by *moving the strip* **or** by *moving the handles* (and thus changing the strip duration). The snapping can be visualized by a thin white line. Click on the magnet-icon in the middle of the header to turn on the snapping guides. You can also use the shortcut key :kbd:`Shift - Tab`  to toggle (see figure 1).

Holding down the :kbd:`Ctrl` key while moving a strip, will also toggle the *Show Guides* command. So, if *Show Guides* is enabled, you can disable it temporarily while moving the strip by holding down the :kbd:`Ctrl` key.

The snapping guide will appear whenever an edge of the moving strip is close (< 15 pixels) to an edge of another strip (see figure 2). *All* channels are taken into account. So, in a crowded scene, there can be lot of snapping guides (but only those within 15 pixels are shown).

.. figure:: /images/video_editing_montage_move-snapping-guides.svg
   :alt: Snapping guides

   Figure 2: Snapping guides

Figure 2 shows all possible snapping guides with 3 strips. The top-panel represents the original situation (before moving strip-3). Because there are two other strips, there are 8 possibilities to snap. The Start frame of strip-3 can snap to the Start and End frame of strip-2; and so can the End frame (= 4 possibilities; middle row in figure 2). The same reasoning holds for the edges of strip-1 (bottom row of figure 2).

(a) The Start frame of strip-3 is snapped to End frame of strip-2. Result: Strip-3 is appended to strip-2. This is in fact the original situation. Because there are no strips to the right of strip-2, this is a legal move and the border of strip-3 is colored in white.

(b) The End frame of strip-3 is snapped to the End frame of strip-2. This could cause an Overwrite of strip-2; so the border of strip-3 is colored red. Result: because d1 > d2, strip-3 is moved to the next available location: End frame of strip-2.

(c) The Start frame of strip-3 is snapped to Start frame of strip-2. This is again an illegal operation; so the border is red. Because d1 < d2, you should expect that strip-2 should be placed before strip-2. However, there is not enough room> and the result is that strip-3 is put back in its original location.

(d) The End frame of strip-3 is snapped to the Start frame of strip-2. This could be a normal operation if the gap between strip-1 and strip-2 was big enough to hold strip-3. Unfortunately, this is not the case; so the border of strip-3 is colored red and the strip is once again appended to the End of strip-2.

(e) The Start frame of strip-3 is snapped to End frame of strip-1. As in (d), this could be a normal operation but again, the gap is not big enough; so strip-3 is moved again to the End of strip-2 and the border is colored red.

(f) The End frame of strip-3 is snapped to the End frame of strip-1. This is an illegal operation because strip-1 could be overwritten. The border is colored red. Because d1 > d2, it should be moved at the end of strip-1. But there is not enough room; so, the other side is tried, which succeeds.

(g) The Start frame of strip-3 is snapped to Start frame of strip-1. Strip-1 could be overwritten; so the border of strip-3 is red. The result is that strip-3 is moved to the front of strip-1, because d1 < d2.>.

(h) The End frame of strip-3 is snapped to the Start frame of strip-1. There is plenty of room before strip-1; so this could be a normal operation (white border). Strip-3 is moved in front of strip-1.

It's a little confusing that for example, the snapping guide in figure 2-d and 4-e seems to implicate that the moved strip will be inserted between strip-1 and strip-2. As explained above, this is not the case, *unless* you activate the Insert-mode (see later).

The snapping guide tool has 5 options (see figure 1).

* Current Frame: the playhead (= current frame) is counted as a supplemental edge to snap on. So, the moving strip can either be snapped to an edge of another strip or to the playhead, whichever is closest.
  
* Hold Offset: Strips can be the result of a Hold Split operation (see :ref:`Hold Split <hold-split-command>`). For example, in figure 3, the Hold Offset Start is at frame 1133 while the first 250 frames are freezed.

   .. figure:: /images/video_editing_montage_move-snapping-hold-split.svg
      :alt: Snapping Hold Split

      Figure 3: Snapping to the Hold Offset Start field

* Muted strips/Sound Strips: when you move a strip, most of the time you don't want to snap this strip to Muted (hidden) or Sound strips. These options are *not* ignored by default, but you have switch them on here.
  
* Snap Current Frame to strip start or end: *not* the strips are snapped, but the playhead is snapped to the strip edges while scrubbing. To see this happen, you need to scrub at a low speed; otherwise you will be past the edge before snapping could take place.

Snap to the playhead
....................

There is also a special command to snap strips to the playhead. Select one or multiple clips. They can be spread over multiple channels. Press :kbd:`Shift - S` to snap the selection to the playhead.

.. Warning::
   If multiple strips are selected, all of them will start at the playhead. The relative position to each other will not be preserved and all the strips are spread over different channels. This command is probably only useful for strips that share a common Start frame; eg. Movie strips with their accompanying Sound strips.
