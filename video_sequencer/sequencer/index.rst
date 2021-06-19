Sequencer
=========

The Sequencer is an area within the VSE that is divided horizontally into channels and vertically into time segments. Optional, there can be a Toolbar at the left and a Sidebar at the right (see figure 1).

.. toctree::
   :maxdepth: 3


   timecode
   move
   navigate
   zoom
   scrub

.. figure:: /images/editors_vse_sequencer.svg
   :alt: Sequencer
  

   Figure 1: Sequencer and components
   
Header
------
The Header of the VSE is by default located at the very top of the editor. You can however flip it to the bottom :kbd:`RMB` on header ; see `Header > Context menu <https://docs.blender.org/manual/en/dev/interface/window_system/regions.html#header>`_ for more info about the available options.

There are three areas within the Header. The left area contains the Editor Type selector and the View Type selector (see figure 2). As the name implies, you can swap the entire editor to another type (e.g. Compositor) with the Editor Type selector. With the View Type selector you can select a specific view: Sequencer, Preview or Sequencer/Preview. Depending on the selected type, you'll get slightly different headers.

The middle area contains the menu bar. Again, the menu can be toggled on or off with the context menu. Figure 2 shows the menu bar with the expanded menu items beneath.

.. figure:: /images/editors_vse_header-sequencer.svg
   :alt: Header Sequencer


   Figure 2: Header of the Sequencer View with menu bar expanded


The menus Select, Marker, Add and Strip are discussed in following sections or in the Video Editing chapter, when they appear in our typical workflow. The View menu contains many items which are specific for operation within the Sequencer; so, they are discussed here.

View Menu
.........

See figure 1 (left panel) for an overview of all the submenus of the Sequencer's View menu.

Sidebar :kbd:`N`
   Show or hide the sidebar. You can use the shortcut :kbd:`N` or the Sidebar button (see figure 1) to toggle on or off. This sidebar appears at the right of the sequencer and will show all the properties of the active strip. Please, note that the active strip does *not* need to be a selected strip (see :ref:`Selecting <video_editing_edit_timeline_select>`). A detailled description of all the properties of the various strip types can be found in the :ref:`Video Editing <striptypes>` section.

.. figure:: /images/editors_vse_header_toolbar-generic.png
   :alt: Toolbar
   :scale: 80%
   :align: right

Toolbar :kbd:`T`
   Show or hide the toolbar. You can use the shortcut :kbd:`T` or the Toolbar button (see figure 1) to toggle on or off. The toolbar in the Video Sequencer is rather minimalistic and not useful. It contains only a Select and Blade tool.

.. warning::
   Both generic tools don't seem to work. Some addons, for example the `VSE Transform Tools <https://github.com/zeograd/VSE_Transform_Tools>`_ make better use of this toolbar.

Adjust Last Operation
   If enabled, this option will display a pop-up panel to alter properties of the last completed operation. For some general background info, see :ref:`bpy.ops.screen.redo_last`.

   For example, after a Duplicate Strip operation, you can still change the horizontal and vertical Offset. Or after a Split operation, you can change the type of split (see figure 2).
   
   .. figure:: /images/editors_vse_header_adjust_last_operation.svg
      :alt: Adjust Last Operation


      Figure 3: Examples of Adjust Last Operation

Preview as Backdrop
   Displays the current frame in the background of the Sequencer (like in the `Compositor <https://docs.blender.org/manual/en/dev/editors/compositor.html>`_). The backdrop will be updated when the playhead is moved. Of course, when there are a lot of strips in the sequencer, they will occlude most of the backdrop image. When you open the :ref:`Sequencer in Full View <sequencer_full_view>` , this could be an alternative of having the preview window on a separate monitor.

   .. figure:: /images/editors_vse_header_backdrop.png
      :alt: Backdrop


      Figure 4: Backdrop of movie in the sequencer   

Frame Selected - Frame All - Zoom
   These menu items are all about zooming in or out of the Sequencer window. This topic is covered more in depth (with all shortcuts) in section :doc:`Zoom <zoom>`

Navigation
   Navigating your timeline is done by moving the playhead. The Navigation submenus are covered in detail in section :doc:`Navigate <navigate>`

.. figure:: /images/editors_vse_header_menu-range.png
   :alt: Menu Range
   :align: right
   :scale: 60%
  
   Figure 5: Submenu Range

Range
   With the menu Range you can specify which frames are going to be previewed or rendered.
   The first three menu items will change the *Preview Range* or *Playback Range*. The last three menu items are meant to set the *Render Range*.

   Set Preview Range :kbd:`P`
      Interactively define the frame range used for preview or playback. After selecting this menu item, a crosshair cursor appears. With this cursor you can drag a box around the frames that you want to preview. You can drag anywhere within the Sequencer area. The selected Preview Range will be displayed in the normal black color. The frames outside the Preview Range will be colored brown. The Shortcut :kbd:`P` is, of course, much faster to apply.
     
      This Preview Range will not affect in any way the Render Range. Both can exist independently.
   Set Preview Range to Strips
      Sets the Preview Frame range to the range of the selected strips.
   Clear Preview Range (Shortcut: :kbd:`Alt-P`)
      Pressing :kbd:`Alt-P` anywhere within the Sequencer area will clear the preview range. If no Preview Range is defined, then the Render Range willbe used to playback or Preview the movie.

   The Render Range is normally set during the Setup phase of your project (see :doc:`Project Settings </video_editing/setup/project/project-settings>`). They also can be set in different editors: `Properties <https://docs.blender.org/manual/en/dev/render/output/properties/dimensions.html>`_ , and `Timeline <https://docs.blender.org/manual/en/dev/editors/timeline.html>`_.

   Set Start Frame :kbd:`Ctrl-Home`
      Set Start of Render Range to the current playhead position.
   Set End Frame :kbd:`Ctrl-End`
      Set End of Render Range to current playhead position.
   Set Frame Range to Strips
      Sets the Render Range to the frame range of the selected strips.

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
