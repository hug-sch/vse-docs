Header
======
The Header of the VSE is by default located at the very top of the editor. You can however flip it to the bottom (see `Header > Context menu <https://docs.blender.org/manual/en/dev/interface/window_system/regions.html#header>`_ for more info about the available options.

There are three areas within the Header. The left area contains the Editor Type selector and the View Type selector (see figure 1). As the name implies, you can swap the entire editor to another type (e.g. Compositor) with the Editor Type selector. With the View Type selector (second button) you can select a specific view: Sequencer, Preview or Sequencer/Preview. Depending on the selected type, you'll get slightly different headers (menu and right handside buttons).

The middle area contains the menu bar. Again, the menu can be toggled on or off with the context menu. Figure 1 shows the menu bar for the three view types. Note that the Preview type contains only one menu item. This View menu is different for all three types; see figure 1 bottom part. The other menu items are identical in the Sequencer and Sequencer/preview type.

.. figure:: /images/editors_vse_header-1.svg
   :alt: Headers VSE


   Figure 1: Headers of the 3 view types of the VSE and their View menu

The menus Select, Marker, Add and Strip are discussed in following sections or in the Video Editing chapter, when they appear in our typical workflow. The View menu contains many items which are specific for operation within the Sequencer; so, they are discussed here.

View Menu
---------

See figure 1 (left panel) for an overview of all the submenus of the Sequencer's View menu.

Sidebar (shortcut :kbd:`N`)
   Show or hide the sidebar. This sidebar appears at the right of the sequencer and will show all the properties of the active strip. Please, note that the active strip does *not* need to be a selected strip (see :ref:`Selecting <video_editing_edit_timeline_select>`). A detailled description of all the properties of the various strip types can be found :doc:`Video Editing Introduction </video_editing/setup/project/striptypes/index>` 

.. figure:: /images/editors_vse_header_toolbar.png
   :alt: Toolbar addon
   :scale: 80%
   :align: right


   Figure 2: Toolbar of the VSE Transform tool addon

Toolbar (shortcut :kbd:`T`)
   Show or hide the toolbar. The toolbar in the Video Sequencer is rather minimalistic and not useful. It contains only a Select and Blade tool.

.. warning::
   Both generic tools don't seem to work. Some addons, for example the `VSE Transform Tools <https://github.com/zeograd/VSE_Transform_Tools>`_ make better use of this toolbar.

Adjust Last Operation
   If enabled, this option will display a pop-up panel to alter properties of the last completed operation. For some general background info, see :ref:`bpy.ops.screen.redo_last`.

   For example, after a Duplicate Strip operation, you can still change the horizontal and vertical Offset. Or after a Split operation, you can change the type of split (see figure 2).
   
   .. figure:: /images/editors_vse_header_adjust_last_operation.svg
      :alt: Adjust Last Operation


      Figure 2: Examples of Adjust Last Operation

Preview as Backdrop
   Displays the current frame in the background of the main view like in the `Compositor <https://docs.blender.org/manual/en/dev/editors/compositor.html>`_. The backdrop will be updated when the playhead is moved. Of course, when there are a lot of strips in the sequencer, they will occlude most of the backdrop image. However, when the Sequencer is in Full View, this could be an alternative of having the preview window on a separate monitor.

   .. figure:: /images/editors_vse_header_backdrop.png
      :alt: Backdrop


      Figure 3: Backdrop of movie in the sequencer   

Frame Selected :kbd:`NumpadPeriod`
   Zooms in the display to fit only the selected strips.
Frame All :kbd:`Home`
   Zooms the display to show all strips.
Zoom :kbd:`Shift-B`
   Click and drag to draw a rectangle and zoom to this rectangle.

Navigation
   Play Animation :kbd:`Spacebar`
      Start or stop playback of animation. This will start playback in all editors.
   Go to Current Frame :kbd:`Numpad0`
      Scrolls the timeline so the current frame is in the center.
   Jump to Previous Strip :kbd:`PageDown`
      Current frame will jump to beginning of strip.
   Jump to Next Strip :kbd:`PageUp`
      Current frame will jump to end of strip.
   Jump to Previous Strip (Center) :kbd:`Alt-PageDown`
      Jump to previous center of the strip.
   Jump to Next Strip (Center) :kbd:`Alt-PageUp`
      Jump to next center of the strip.
Range
   Set Preview Range :kbd:`P`
      Interactively define frame range used for playback.
      Allows you to define a temporary preview range to use for animation playback
      (this is the same thing as the *Playback Range* option of
      the :ref:`Timeline editor header <animation-editors-timeline-headercontrols>`).
   Set Preview Range to Strips
      Sets the frame range of preview to the range of the selected strips.
   Clear Preview Range :kbd:`Alt-P`
      Clears preview range.
   Set Start Frame :kbd:`Ctrl-Home`
      Set Start of animation range to current playhead position.
   Set End Frame :kbd:`Ctrl-End`
      Set End of animation range to current playhead position.
   Set Frame Range to Strips
      Sets the frame range of preview and render animation to the frame range of the selected strips.

.. _bpy.ops.sequencer.refresh_all:

Refresh All
   To force Blender to re-read in files, and to force a re-render of the 3D Viewport,
   click the *Refresh Sequencer* button.
   Blender will update and synchronize all cached images and compute the current frame.

   Certain operations, like moving an object in the 3D Viewport, may not force the *Sequencer*
   to call for a refresh of the rendered image (since the movement may not affect the rendered image).
   If an image or video, used as a strip, is changed by some application outside of Blender,
   Blender has no real way of being notified from your operating system.

Sync Visible Range
   Synchronize the visible range with other time based editors.

Show Seconds :kbd:`Ctrl-T`
   Shows seconds instead of frames on the time axis.
Show Markers
   Shows the markers region. When disabled, the `Markers Menu`_ is also hidden
   and markers operators are not available in this editor.

.. _bpy.types.SequenceEditor.show_cache:

Show Cache
   Show which frames are :doc:`Cached </video_editing/sequencer/sidebar/cache>`
   Show all enabled types;
   Final Images, Raw Images, Preprocessed Images, Composite Images

   In order for this property to be visible, enable :ref:`Developer Extras <prefs-interface-dev-extras>`.

Sequence Render Image
   Render an image of the current frame.
Sequence Render Animation
   Render timeline from Preview Start to Preview End Frame to a Video file or series of images.

Export Subtitles
   Exports :doc:`Text strips </video_editing/sequencer/strips/text>`,
   which can act as subtitles, to a `SubRip <https://en.wikipedia.org/wiki/SubRip>`__ file (``.srt``).
   The exported file contains all Text strips in the video sequence.

Toggle Sequencer/Preview :kbd:`Ctrl-Tab`
   Switch the editor display type between Sequencer and Preview.



The area at the right contains one or three buttons.

.. figure:: /images/editors_vse_header_buttons.svg
   :alt: Display buttons in Header VSE
   :align: right


   Figure 1: Display buttons Header

For a detailled explanation, see `Display Mode <https://docs.blender.org/manual/en/dev/video_editing/preview/display_mode.html>`_.
