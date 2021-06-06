Splitting
---------
Splitting a strip is separating the strip into two parts at the position of the playhead. Both parts continue to function as independent strips (who shares the same source). Splitting can be done on all strip types. Splitting an effect strip however will also slit the input strip of the effect and vice versa.

In previous versions of Blender and also in a substantial part of the literature this operation was called "Cutting".  In a computer environment however this term is primarily used in the sense of copy-cut-paste, where it implicates delete. So, the term *Split* is preferred, although it stays very visible in terms such as *Jump Cut*, *J- or L-Cut*, ....

There are two variants of the command: Split and Hold Split.

Split command
.............

With the menu :menuselection:`Strip --> Split` or the shortcut key :kbd:`K` you can split the selected strip in two at the current frame. This will result in two strips which use the same source, fitting the original strip's timing and length.

.. warning::
   If you are using the shortcut :kbd:`K`, then it matters which side of the playhead the mouse cursor is (see figure 1). If the cursor is at the left hand side of the playhead, then the left strip is the active one (white outline & text overlay) and therefore also selected. If the mouse cursor is at the right of the playhead, then the right strip is the selected strip (orange outline)  *but* not the active one (no white text overlay). Contrary to what you might suspect, the Time fields then relate to the left strip; not the (selected) right strip. 

.. figure:: img/split.svg
   :alt: Split command
   
   Figure 1: Strip properties before and after Split command

Please note, that in figure 1 the result right after the Split command is issued, is shown in the second column. In the third column the right part of the Split is deleted. In the fourth column, the left part is deleted and the right strip is made the active one.

Also note that the Start frame of the left and right strip is the same: frame 1; even though the right strip starts visually at frame 8. This is accomplished with the Strip Offset Start field. And likewise, the premature ending of the left strip is done with the Strip Offset End field.


Hold Split command
..................

The menu :menuselection:`Strip --> Hold Split` or the shortcut :kbd:`Shift-K` splits a strip in two distinct strips; however you will not be able to drag the endpoints to show the frames past the split of each resulting strip.

