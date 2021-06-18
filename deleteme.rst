Adding
------

.. toctree::
    :maxdepth: 3

    adding/index
    selecting
    moving
    splitting
    trimming
    grouping
    deleting



Strip Types
-----------

.. toctree::
   :maxdepth: 1

   movie
   sound
   image
   clip
   scene
   color
   mask
   text

.. figure:: /images/vse_setup_project_striptypes_strip-types.svg
   :alt: Available strip types

   Figure 1: Available strip types with color code and properties.

A strip is a sequence of images displayed as a colored horizontal bar.
Each image occupies one frame in the timeline.
In figure 1 the basic strip types are added with the menu :menuselection:`Add` or :kbd:`Shift-A`.
They run from frame 1 up to frame 300.

The strip types are classified into 4 groups:

   1. *Scene, Clip, Mask*: the input source is created in another Blender module
   2. *Movie, Sound, Image/Sequence*: the input source is an external file
   3. *Color, Text*: the input is created within the Sequence Editor
   4. *Adjustment Layer, Effect Strip, Transition, Fade*: the input source is another strip.

Each strip type is uniquely color-coded.
In figure 1, from top to bottom: Scene strip :scene:`███`,
Clip strip :clip:`███`, Mask strip :mask:`███`, Movie strip :movie:`███`,
Sound strip :sound:`███`, Image/Sequence strip :image:`███`,
Color :color:`███` + selected color), and Text :text:`███`.

.. _default-color:

These colors are defined in the User Preferences and can be changed with the menu
:menuselection:`Edit --> Preferences --> Themes --> Video Sequencer`.

The Group 4 strip types are *not* shown in figure 1 and will be discussed in a separate section.
They presume the existence of one or more of the above basic strips.

Each strip has multiple Properties. Figure 1 shows the Properties of a Movie strip at the right hand side.
This sidebar can be displayed with :menuselection:`View --> Sidebar` or shortcut key :kbd:`N`.
All properties are organized in panels, e.g. Compositing, Transform, Crop, ect...
Navigating these panels is explained in `Tabs & panels <https://docs.blender.org/manual/en/dev/interface/window_system/tabs_panels.html>`_.
The top of the sidebar contains the always visible header with the icon of the strip type,
the name of the strip, and a Mute checkbox. You can name or rename your strips here.
If the Mute button is checked the strip will still be visible in the Sequencer but will not produce any output.

