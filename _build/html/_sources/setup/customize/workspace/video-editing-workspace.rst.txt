The Video Editing workspace
===========================

Upon opening Blender, the `splash screen <https://docs.blender.org/manual/en/dev/interface/window_system/splash.html>`_ gives you the possibility to create a Video Editing project. Choosing this option takes you immediately into the Video Editing workspace. This workspace is a smart combination of five editors: File Browser (top left), Video Sequencer: Preview (top middle), Properties (top right),Video Sequencer: Sequencer (near bottom) and Timeline (bottom). Together they provide you with all the necessary tools to edit your videos.

.. figure:: /images/setup/vse_setup_organize_workspace_video-editing_workspace.svg
   :scale: 100 %
   :alt: The Video Editing Workspace

   Figure 1: screenshot of the video editing workspace


As a result of your preparation for this video editing project, all of your assets (clips, images, sounds, ...) are organized in folder structure that is appropriate for your project. For example, they are organized on daily basis, per topic, per character, ... You can use the File Browser for displaying this structure and for easily adding assets to your timeline by dragging and dropping files. If you select multiple files, they will added one after the other to the timeline. You can customize (sorting, filtering, ...) the file browser, so that you have an optimal overview of your assets.

The Sequence Editor has three view types for the main view:

* **Sequencer**: view timeline and strip properties. This is the bottom panel in the figure 1. This region is where strips can be selected, modified by moving, cutting, or extending strips. There are also several built-in effects that can be combined with other strips to change their appearance. The Sequencer region is horizontally divided into channels, each channel can contain what is called a strip. A strip can be an image, animation, or any number of effects. Each channel is numbered consecutively on the Y axis, starting from zero and allows up to 32 total channels. The X axis represents time. Each channel can contain as many strips as it needs as long as they do not overlap. If a strip needs to overlap another, it needs to be placed on a channel above or below the other strip. When strips are stacked, they stack from bottom to top where the lowest channel forms the background and the highest the foreground. The first channel 0 is unusable as a place to put strips. This is because it is used by the Sequencer Display to show a composite of all strips above channel 0.
* **Preview**: view preview window and preview properties. This is the top middle panel in figure 1. The properties however are not displayed in this case. 
* **Sequencer/Preview**: combined view of preview and timeline and properties of both.

It is possible to create multiple instances of any view type in single workspace; so, the Video Sequencer occupy two areas in the workspace. You can switch easily between the Sequencer and the Preview with the Ctrl Tab shortcut.

The Properties panel shows and allows editing of many active data. They are organized into several categories, which can be chosen via tabs (the icons column to its left). Not all categories are relevant in the Video Sequencer. By default only the following are shown: Active Tool, Render Properties, View Layer Properties, Scene Properties, World Properties, and Texture Properties. Most of the time, you will use only the Render Properties.

The built-in Video Editing workspace is very handy and it can be customized very easily. Each editor area can be sized, moved, replaced or removed from the workspace. As example, an alternative workspace with auto-installed add-ons can be download from `tin2tin's github <https://github.com/tin2tin/Sequence_Editing>`_. A screenshot is provided below.

.. figure:: https://raw.githubusercontent.com/tin2tin/Sequence_Editing/main/Sequence_Editing.png
   :scale: 100 %
   :alt: A customized Video Editing Workspace
   
   Figure 2: a customized Video Editing Workspace.

