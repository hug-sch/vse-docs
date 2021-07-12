Sidebar
--------
The sidebar of the Preview can be toggled with the menu :menuselection:`View --> Sidebar` or with the shortcut :kbd:`N`. You can select one of three tabs: Tool, View or Metadata. Figure 1 shows the side bar of the Preview, but also the side bar of the sequencer. In the Preview side bar, the View tab is activated and the panel View Settings is expanded.

.. figure:: /images/editors_vse_preview_sidebar-overview.svg
   :alt: Sidebar overview


   Figure 1: Video Sequence Editor with two sidebars: Preview and Sequencer.

.. admonition:: Reference
   :class: refbox

   =============   ==========================================================================
   **Name**:       View Settings
   **Context**:    Video Sequence Editor > Preview
   **Location**:   Sidebar > View
   =============   ==========================================================================



.. figure:: /images/editors_vse_preview_sidebar-view-settings.png
   :alt: Side bar View Settings
   :scale: 50%
   :align: right

   Figure 2: Side bar View Settings

Proxy Render Size
   The use of proxies is fully described in section :doc:`Setup </video_editing/setup/environment/proxies>`. Prefetching frames is described in the section about cache.
Channel
   The Sequencer can contain multiple channels. Figure 1 has three channels with strips: a Sound strip at channel 1, a Movie strip at channel 2 and a Scene strip at channel 3. The channel that is shown in the preview, is indicated here. You can get a similar result by Muting strips above the indicated channel. Channel 0 (default setting) is the compositing result of all strips and is shown by default.

   .. note::
      This option should not be interpreted as some kind of "isolation mode". The indicated channel is *not* isolated in the sense that *only* that channel is shown. Each channel is implicitly composited on top of the channel(s) below. A better description could be "show up to channel".
Show Overexposed
   Shows overexposed (bright) areas using a zebra pattern. When is an area overexposed?  You can set the threshold with the slider. The values 0 - 110 should be interpreted as a percentage of decimal value (0 - 1.1). Whenever the RGB value (any component) of a pixel is greater or equal to the specified threshold, it will be marked (zebra-striped) as overexposed. You can check this easily with a color strip. Set the color for example to bright yellow (RGB = 0.9, 0.9, 0). When the threshold is set to 90, everything will be zebra-striped (supposedly overexposed). From threshold value 91 on, the preview shows a bright yellow color again. A threshold of 0 will disable this filter.

.. admonition:: Reference
   :class: refbox

   =============   ==========================================================================
   **Name**:       Frame Overlay
   **Context**:    Video Sequence Editor > Preview
   **Location**:   Sidebar > View
   =============   ==========================================================================

.. figure:: /images/editors_vse_preview_sidebar-frame-overlay.png
   :alt: Side bar Frame Overlay
   :scale: 50%
   :align: right

   Figure 2: Side bar Frame Overlay


By enabling this Frame Overlay setting, you can compare the current frame to a reference frame. This is very handy, for example in color grading. You can have the preview of two shots on the screen so that it is easier to match the colors of two shots. Also in multicam editing where you have shots of the same scene from different cameras, it can come handy to have a preview of both cameras at the same time.

The User Interface of this option is however a bit rusty.

Set Overlay region
   You have to set the Frame Offset (see below) *first*; otherwise you want see much happening. Pressing this button lets you draw a box where you want the Overlay to appear in the Preview. The shortcut is :kbd:`O`. In figure 3, an Overlay Region is drawn at the top-right corner of the Preview.

   This Overlay type (Rectangle) is however not that useful. Suppose, you want to see the mid-region of the reference frame. Therefore, you need to draw a box at the mid-region of the current frame, hiding probably some vital info. Drawing it at the top will reveal this info in the current frame but will show also the less interesting area (top) from the reference frame.

Frame Offset
   This slider controls the offset of the reference frame relative to current frame. In figure 3, the current frame is at position 1500 and the reference frame at position 2000, which is an offset of +500 frames from the current frame. Changing the Frame Offset will *not* update in real time the Preview window. To see the result of this change, you have to move the playhead.

Overlay Type
   
      Rectangle
         A rectangle area of the reference frame will be displayed on top of current frame at the same position. This is the case used in figure 3.
      Reference
         Only the reference frame is displayed in the preview region. Of course, this is exactly the same as moving the current frame and switching off the frame overlay.
      Current
         Only the current frame is displayed in the preview region. The last two options are only useful when working with two preview windows.

Overlay Lock
   The reference frame is moved in sync with the current frame. With this option, you can (temporary) lock the reference frame to its current position.

   .. tip::
      It is possible to have several Sequence Editors opened and they can use different overlay types. So it is possible to have current and reference frames displayed in different editor spaces.

Safe Areas
   A safe area is a screen area that is visible on most devices. Especially, older TV's with rounded corners have a much smaller visible area. This safe area is indicated in Blender by dashed lines (see figure 5) and conform to the European Broadcasting Union (EBU) rules. There are two areas:
   
   * TitleGraphics  safe area:
   * Action safe area:
   * 
   * . smaller screens have on the Display an overlay on the preview, marking where the title safe regions are.


.. figure:: /images/editors_vse_preview_safe-areas.svg
   :alt: Safe areas
  

   Figure 2: Safe Areas

.. _bpy.types.SpaceSequenceEditor.show_metadata:

Metadata
   Display Image metadata in the preview area.

.. _bpy.types.SpaceSequenceEditor.show_annotation:

Annotations
   Displays :doc:`Annotations </interface/annotate_tool>` in the preview region.
