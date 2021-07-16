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

.. figure:: /images/editors_vse_preview_sidebar-overlay.svg
   :alt: Frame Overlay

   Figure 3: Frame Overlay Type: Reference (left), Current (mid), Rectangle (right)

Set Overlay region
   You have to set the Frame Offset (see below) *first*; otherwise you want see much happening. Pressing the Set Overlay Region button lets you draw a box where you want the Overlay to appear in the Preview. The shortcut is :kbd:`O`. In figure 3, an Overlay Region is drawn at the left side of the Preview.

   This Overlay type (Rectangle) is however not that useful. Suppose, you want to see the mid-region of the reference frame. Therefore, you need to draw a box at the mid-region of the current frame, hiding probably some vital info. Drawing it at the top will move it out of the way but will probably show also the less interesting area (top) from the reference frame.

Frame Offset
   This slider controls the offset of the reference frame relative to current frame. In figure 3, the current frame is at position 7650 and the reference frame at position 6650 (dashed blue line), which is an offset of -1000 frames from the current frame. Changing the Frame Offset will *not* update in real time the Preview window. To see the result of this change, you have to move the playhead.

Overlay Type
   Rectangle
      A rectangle area of the reference frame will be displayed on top of current frame at the same position. This is the case used in figure 3 (right handside).
   Reference
      Only the reference frame is displayed in the preview region (see figure 3, left handside). Of course, this is exactly the same as moving the current frame and switching off the frame overlay.
   Current
         Only the current frame is displayed in the preview region (figure 3, mid section). This is, of course, the default behavior of the Preview.

   .. tip::
      The last two options are only useful when working with two preview windows.It is possible to have several Sequence Editors opened at the same time and they can use different overlay types. So, the middle sequence editor displays the Current frame, while the left editor displays the Reference frame.

Overlay Lock
   The reference frame is moved in sync with the current frame. With this option, you can (temporary) lock the reference frame to its current position.


.. admonition:: Reference
   :class: refbox

   =============   ==========================================================================
   **Name**:       Safe Areas
   **Context**:    Video Sequence Editor > Preview
   **Location**:   Sidebar > View
   =============   ==========================================================================

.. figure:: /images/editors_vse_preview_sidebar-safe-areas.png
   :alt: Safe Areas
   :scale: 50%
   :align: right

   Figure 4: Safe Areas

A safe area is a screen area that is visible on most devices. Especially, older TV's with rounded corners have a much smaller visible area. This safe area is indicated in Blender by dashed lines (see figure 5) and conform to the  `European Broadcasting Union (EBU) <https://tech.ebu.ch/docs/r/r095.pdf>`_ rules. There are two areas:

.. figure:: /images/editors_vse_preview_safe-areas.svg
   :alt: Safe areas
  

   Figure 5: Safe Areas

Title Safe Margins X & Y
   According to the EBU document (where this option is called "Graphics Safe Area"), this is set by default to 5% of the project resolution. All text and graphic elements such as subtitles or a logo must be placed within this area.
Action Safe Margins X & Y 
   All major action should be viewable within this area. By default, the Action Safe Margins are set to 3.5% of the the project resolution. The Action Safe Margins are smaller than the Title Safe Margins because loosing some text (or logo) is more harmful than cutting some action.
Center-Cut Safe Areas
   This ensures that people who still have old 4×3 TVs or monitors won’t have the text cut off on the sides. By default, this is set to 17.5% of the X project resolution and 5% of the Y axis. Of course, these values are for a 16:9 aspect ratio project. If you want to display a 16:9 image in a 4:3 area, there are two possibilities (see figure 6).

.. figure:: /images/editors_vse_preview_safe-areas-4x3.svg
   :alt: Safe areas conversion
  
   Figure 6: How to fit a 16:9 image in a 4:3 area?

In the left solution of figure 6, the complete 16:9 image is preserved but two black rectangular areas (called letterboxes) are added to the top and bottom. If you want to completely fill the 4:3 area with footage, you need the solution at the right of figure 6. The original 16:9 image is cropped 12.5%, both left and right. Add another 5% for the Title Safe Area and you'll get the default 17.5%.

.. note::
   Modern TV's and computer monitors have fixed pixel matrix screens and the viewable area is much larger than older CRT (Cathode Ray Tube) screens. So, the safe areas are not that important anymore. However, users are accustomed with the safe area layout. So, following the safe area guides is good practice. Also, from an aesthetic view point it is not advisable to stick text or logos to the very edge of the screen. 

.. admonition:: Reference
   :class: refbox

   =============   ==========================================================================
   **Name**:       Scene Strip Display
   **Context**:    Video Sequence Editor > Preview
   **Location**:   Sidebar > View
   =============   ==========================================================================

.. figure:: /images/editors_vse_preview_sidebar-scene-strip-display.png
   :alt: Scene Strip Display
   :scale: 50%
   :align: right

   Figure 5: Scene Strip Display

   
With this option, you can control how the images of Scene Strips are displayed in the preview. In figure 1, a scene strip was added to display the orange circle at the left of the intro text. This orange circle was created in the 3D view of another scene; you cannot use the same scene of the sequencer. It's a simple mesh with an orange emission material applied to it.

Shading
   Shading refers to the way objects are drawn and lit in the 3D View. More info can be found at `Viewport Shading <https://docs.blender.org/manual/en/dev/editors/3dview/display/shading.html#wireframe>`_ 

   Solid: shows the objects from the scene strip as massive objects but without any materials assigned. The lightning, colors and other options could be set in Workbench Render Engine (Properties > Render Tab > Render Engine). 
   Wireframe: *Does not seem to work!*
   Material Preview: Renders the scene strip with the Eevee render engine, independent of the render engine that was selected in the scene itself. 
   Rendered: Render the scene strip with the scene Render Engine (Cycles, Eevee, Workbenck). By default the scene lights are used for lighting. 


Override Scene Settings
   This option is only available, if Solid shading is activated. When enabled, it uses the Workbench render settings from the sequencer scene, *not* the Workbench render settings from the source scene. You can find these settings in the Properties > Render tab > Render Engine.
   

   
.. _bpy.types.SpaceSequenceEditor.show_annotation:

.. admonition:: Reference
   :class: refbox

   =============   ==========================================================================
   **Name**:       Annotations
   **Context**:    Video Sequence Editor > Preview
   **Location**:   Sidebar > View
   =============   ==========================================================================

Annotations
   Displays :doc:`Annotations </interface/annotate_tool>` in the preview region.

   .. _bpy.types.SpaceSequenceEditor.show_metadata:

Metadata
   Display Image metadata in the preview area.