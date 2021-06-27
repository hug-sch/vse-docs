Header
------
The Type Selector buttons are identical to those of the Sequencer header. The menu bar is limited to a stripped-down View menu. The Show Overlay button gets the company of the Display buttons (far right). For more general info about the header, see :doc:`Sequencer header <../sequencer/header>`

View Menu
.........

.. figure:: /images/editors_vse_preview_view-menu.png
   :alt: View menu of Preview


   Figure 1: View menu of the Preview window

Sidebar - Toolbar
   See :doc:`Sequencer header <../sequencer/header>` for more info.

Preview During Transform
   Setting this option will change the behavior of dragging the left or right strip handle. Normally, this will extend or reduce the strip length. With this option set, dragging the strip handles will show the frame the strip handle is pointing to in the Preview window. This will allow very precise trimming. The (previous) alternative way to do precise trimming is by scrubbing with the playhead through a strip and finding the exact location. Then, splitting the strip and deleting the redundant part.
Fit Preview in Window :kbd:`Home`
   Resize the Preview window so that the Project Dimensions area it fits in. Depending on the specific rendered image, the height or the width or both are set equal to the project height or width.
Zoom :kbd:`Shift-B`
   Click and drag to draw a rectangle and zoom to this rectangle. The selected area is centered in the window and the Preview is zoomed with a factor size preview window/ size selected rectangle. This is normally a zoom i, but you can also drag a rectangle selection that is larger than the Preview window (by starting outside the window.
Fractional Zoom
   Resize the preview in steps from 1:8 to 8:1 (see figure 1). A fractional zoom of 1:1 (:kbd:`Numpad - 1`) ...

   .. todo::
      Explain ratios and difference between 1:1 and Fit Preview in Window.

Show Cache, Sequence Render Image, Sequence Render Animation, Export Subtitles

* Rendering is described in section Video Editing > Render.
* Subtitles are described in Video Editing > Edit > Sound.

.. todo::
   Add links to those sections 

Toggle Sequencer/Preview :kbd:`Ctrl-Tab`
   Switch the editor display type between Sequencer and Preview.

Display Mode
............

Mode to show different aspects of the composite result, for the current frame:

Image Preview
   The Image Preview mode shows you what the resulting video will look like when rendered. This is the default working mode. 
Luma Waveform
   The Luma Waveform is the graphical representation of the luminance of an image or video. For more detailed information about how to use this tool, see section on Color Grading.

   .. todo::
      Prepare this section

.. figure:: /images/editors_vse_preview_luma-waveform.svg
   :alt: Luma Waveform
 

   Figure 2: Luma Waveform and Image preview

   Figure 2 shows two Preview windows: the left one with Display Mode Luma Waveform, the right one with the default display Mode Image Preview. The image is composed of 4 columns with several areas of grey-scale.
   
   The X-axis of the Luma Waveform represents the X-axis of the image. Although you cannot recognize shapes in the Luma Waveform, the 4 columns are discernible because they are very different in luminance.
   
   The Y-axis of the Luma Waveform represents luminance, ranging from zero (black) at the bottom to 1 (white) at the top. The first column (from the left) has a RGB-value (0.5,0.5, 0.5), which is a 50% grey. This luminance value of this column is shown as the little white line at (a). The luminance values for respectively (c), (d) and (e) are 0.8, 0.6 and 0.2. Because the second column contains only those 3 luminance values, the Luma Waveform shows only three small (white) lines at the values 0.8, 0.6 and 0.2.
   
   The third column is a gradient, going from almost black to almost white. This column however contains all luminance values within this range. They are represented with several lines, indicating that all those values are in that area.
   
   The first column contains also some kind of point-cloud above the 0.5 luminance. This is caused by the anti-alisiad white text (50%). These luminance values (from white to mid-grey) occur in the middle of the column where the text resides.

   With the sample tool (see figure 2) you can determine the Luminance value and other color values of every pixel in the image. :kbd:`LMB-Click` will show this info in the statusbar.

Chroma Vectorscope
   Color hue and saturation analyzer.
Histogram
   RGB distribution histogram.


Display Channels
................

Color and Alpha
   Display preview image with transparency over checkerboard pattern.
Color
   Ignore transparency of preview image (fully transparent areas will be black).


Show Overlay
............

Overlays are information that is displayed on top of the preview region.
There is a switch to turn off/on all overlays for the preview region.

.. rubric:: Preview Overlays

Frame Overlay
   Displays the :ref:`Frame Overlay <bpy.types.SequenceEditor.show_overlay>`,
   to compare the current frame to a reference frame.

.. _bpy.types.SpaceSequenceEditor.show_safe_areas:

Safe Areas
   Display an overlay on the preview, marking where the title safe regions are.

.. _bpy.types.SpaceSequenceEditor.show_metadata:

Metadata
   Display Image metadata in the preview area.

.. _bpy.types.SpaceSequenceEditor.show_annotation:

Annotations
   Displays :doc:`Annotations </interface/annotate_tool>` in the preview region.



   
For a detailled explanation, see `Display Mode <https://docs.blender.org/manual/en/dev/video_editing/preview/display_mode.html>`_.
