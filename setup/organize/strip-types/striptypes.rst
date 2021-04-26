***********
Strip types
***********

.. toctree::
   :maxdepth: 2
 
   movie.rst
   sound.rst
   image.rst
   clip.rst
   scene.rst
   color.rst
   mask.rst
   text.rst

.. figure:: img/strip-types.svg
   :alt: Available strip types
   

   Figure 1: Available strip types with color code and properties.

A strip is a sequence of images, displayed as a colored horizontal bar. Each image occupies one frame in the timeline. In figure 1 the basic strip types are added with the menu :menuselection:`Add` or the shortcut key Shift+A). They run from frame 1 up to frame 300. 

The strip types are classified into 4 groups: (1) the input source is created in another Blender module (2) the input source is external (3) the input is created within the Sequence Editor (4) the input source is another strip.

Each strip type is uniquely color-coded. In figure 1, from top to bottom: Scene strip (Light Green),  Mask strip (Dark Grey), Movie strip (Aquamarine), Sound strip (Turquoise), Image/Sequence strip (Brown), Color (Light Grey + selected color), and Text (Purple). The Group 4 strip types are not shown in figure 1 and will be discussed in a separate section. They presume the existence of one or more of the above basic strips.

Each strip has multiple Properties. Figure 1 shows the Properties of a Movie strip. This sidebar can be displayed with :menuselection:`View --> Sidebar` or shortcut key N. All properties are organized in panels, e.g. Compositing, Transform, Crop, ... Navigating these panels is explained in :doc:`Tabs & panels </interface/window_system/tabs_panels>` . The top of the sidebar contains the always visible header with the icon of the strip type, the name of the strip and a Mute checkbox. You can name or rename your strips here. If the Mute button is checked the strip will still be visible in the Sequencer but will not produce any output.







