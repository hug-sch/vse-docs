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
   
   If you want to specify the movement in *seconds*, you can always enter the necessary calculation. Suppose, that your project has a fps = 24, then moving a strip 5 seconds is done by G X 5**24. You have to tap the multiply symbol twice (**)!

.. admonition:: Conflict resolution

   Moving a strip, so that it (partially) overlap with another strip, will create a temporary red outline around the moving strip, indicating that the strip can't be moved there (without overwriting) and will be placed further away and clamped to either side of the overlapping strip.
   
   Which side? Two distances are calculated; eg. d1 and d2 in figure 3. Because d2 is smaller than d1, the moving strip-1 will be appended at the end of strip-2 + strip-3 (if there is room). Moving strip-3 between strip-1 and strip-2 is a little more difficult to predict. If d3 < d4, then strip-3 will be placed before strip-1. Otherwise, it will be appended to strip-2.

   .. figure:: /images/video_editing_montage_move-guides-snapping-side.svg
      :alt: Snapping side
      :align: center


      Figure 3: Snapping side (without guides)

If a strip is moved a strip, its background is drawn semi-transparent
if it overlaps with another strip. It's convenient to see what's
underneath, especially with the Overwrite feature.