#####################
Video Sequence Editor
#####################

Blender is a versatile software used for modeling, sculpting, 2D drawing, animation, and video editing. Most of the work is done in so-called editors: tools for viewing and modifying your work through a specific part of Blender.

There are a couple of editors that can manage video: the `Compositor <https://docs.blender.org/manual/en/dev/editors/compositor.html>`_, the `Movie Clip Editor <https://docs.blender.org/manual/en/dev/editors/clip/index.html>`_, the `Image Editor <https://docs.blender.org/manual/en/dev/editors/image/index.html>`_ (only for still images) and the Video Sequencer. Every editor has a Editor Type selector in the top-left corner (see figure 1). This chapter describes only the Video Sequence Editor (VSE), sometimes shortened to “Sequencer”.

.. note::
   It is not always obvious whether to describe something in the Video Sequencer section or in the Video Editing section. We try to apply the following rule: Anything that comes down to how to move around the editor(view menu, overlays, display modes, ...) is described in the Editor section. Anything that involves working with the editors data (e.g. strips in case of the VSE) will go into the video editing section. For example, selecting strips is described in the Video Editing section, while zooming in on the timeline is covered in the Editor section.

With the View Type selector (see figure 1; top left) you can choose if the Video Sequence Editor contains only the Sequencer or only the Preview or both.


.. figure:: /images/editors_vse_view_types.svg
   :alt: View types
   
   Figure 1: Three view types for the Video Sequence Editor

Note that any area within the Blender main window can contain any Editor and that the same Editor can occur multiple times within the main window. So, theoretically, you can rebuild the combined Sequencer/Preview, starting from an empty workspace and placing two Video Sequence Editors on top of each other. The bottom editor has View Type Sequencer and the top one has type Preview.

The VSE is composed of multiple areas (see figure 2). They are described in more detail in the next sections. Figure 2 shows the combined view *Sequencer/Preview*. You can select this view with the View Type selector. This view can contain the following areas:

.. figure:: /images/editors_vse_overview.svg
   :alt: Main view of Sequencer
   
   Figure 2: Sequence Editor main view: Header (red), Preview (Yellow), Sequencer (blue), Properties (Grey), Panels & Tabs (Yellow), Toolbar (Purple)



- Sequencer: area for the montage of the strips.
- Properties: shows the properties of the active strip. Is divided into panels and tabs. Toggle on or off with :kbd:`N` key.
- Toolbar: collection of icons. Clicking the icons will perform an operation on the selected strips in the sequencer. Toggle on or off with :kbd:`T` key.
- Preview: shows the output of the sequencer at the time of the playhead.
- Header: with the menu and buttons. This header changes slightly depending on the selected view (see below).



.. toctree::
   :hidden:
   
   sequencer/index
   preview/index
   sequencer&preview/index



