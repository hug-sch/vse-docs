Toolbar
-------
The Toolbar can be toggled on or off with :menuselection:`View --> Toolbar` or the shortcut :kbd:`T`. It contains two tools: Sample and Annotate (see figure 1, left side).

Sample
   The Sample tool (with the little eyedropper icon) can be used to sample a pixel's color. Be sure that the Sample Tool is selected (which is by default) and :kbd:`LMB - Click` anywhere in the Project Preview area. Information about the pixel under the mouse cursor appears in the status bar.

.. figure:: /images/editors_vse_preview_sample-tool.svg
   :alt: Sample Tool

   Figure 1: Sample Tool in action

   The Preview window of figure 1 contains a simple Color strip with RGB values (0.8, 0.7, 0.4) or the equivalent HSV values (0.142, 0.5, 0.8). These values are set with the Color Picker. They are also shown in figure 1. :kbd:`LMB - Click` on the bottom-right corner of the Preview (position X = 1870 and Y = 79; see figure 2) will show a status bar, containing the following info:

   * The X and Y coordinates of the clicked pixel. Remember that the left bottom corner is location (0,0) and that the project resolution is set to 1920 x 1080.
   * The values for the Red, Green, and Blue component as from the Color Picker.
   * The Alpha value of the pixel.
   * The Color Managed values of the Red, Green and Blue component or the color as you see in the Preview.
   * The Hue, Saturation, Value and Luminance equivalent values of the Color Managed values.

The Color Managed values are the result of applying the View Transform function from the `Color Management panel <https://docs.blender.org/manual/en/latest/render/color_management.html>`_. For the Video Editing Workspace, this is by default the Standard View Transform. This Transform function does not change the display device color values.

.. note::
   If your colors look a bit "washed" out, then better check the `View Transform function <https://docs.blender.org/manual/en/latest/render/color_management.html>`_. If you started your project from another workspace than the Video Editing Workspace, this function is set by default to Filmic. This Transform function does change your colors (makes them "washed out"). Luckily, the VSE resets the Transform function to Standard, but only if the first added strip is a movie or image. If you add, for example a Scene strip as the first strip, the Transform function will not be changed.

.. todo::
   Reference to the color management section or short explanation about rgb --> HSV conversion and/or transform function.



:ref:`Annotate <tool-annotate>`
   With the Annotate tool, you can draw free-hand annotations onto the Preview window (thus, also outside the Project Preview area). This is a handy tool to give some instructions if you are working in team on a project (or to your later self). These annotations are saved with the Blend-file.

   The Annotations and its Settings are stored in the :ref:`Annotations panel <annotations>` in the Side bar. To remove all annotations, just click on the Unlink button.

   More information about the Annotate tool can be found in the :ref:`User Interface section <tool-annotate>` of the docs.

