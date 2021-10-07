Inserting
---------

Moving Strip-3 between strip-1 and strip-2 in figure 6 will need an Insert-mode. Simply moving the strip will snap strip-3 to either the Start of strip-1 or the End of strip-2, depending on the mouse position.

If you want to insert strip-3 between the other 2 and thus making room by shifting strip-2 to a later time, you need to hold the :kbd:`Alt` key while moving. Pressing :kbd:`Enter` or :kbd:`LMB - Click` will insert the strip. The message to do this appears at the left side in the header of the preview (see figure 6): *Sequence Slide: -76,0, (G or Alt) Expand to fit ON*. So, pressing the :kbd:`Alt` key while moving will set *Expand to fit ON*. Releasing the key will toggle the message to *Expand to fit OFF*. 

.. figure:: /images/video_editing_montage_move-snapping-insert.svg
   :alt: Insert mode

   Figure 6: Inserting a strip

The Insert mode works also with multiple, selected clips. If there are any gaps between the moving strips, these  will be preserved.