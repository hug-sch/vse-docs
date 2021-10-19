Annotating screenshots
**********************

Adding annotated figures to the Blender documentation can be a labor intensive process; especially if the figure content changes a lot, due to Blender internal development. The following text describes an optimized workflow for creating these frequently changing figures in the Blender docs. Most of the time, these figures are based upon a screenshot of some part of the Blender interface; where upon some annotation (coloring, text, arrows, labels, ...) is added.

Embedding the screenshot in SVG
===============================

1. Create a blend-file with the same name as the figure; e.g. video_editing_setup_workspace.blend. If you have a high resolution monitor, it is perhaps better to set the Edit > Preferences > Interface > Resolution Scale to a higher value (e.g. 1.5) to enhance the readability of the text.
2. Prepare the Blender environment for the screenshot (e.g. choose workspace, resize, expand or collapse panels, ...).  With the menu Edit > Toggle Full Screen, you can hide hide the title bar where the file location of the Blend-file is displayed. Be sure that your Blender window is maximized (or remember the actual window dimensions).
3. Take a screenshot. You can use Blender (menu Window > Save Screenshot or Save Screenshot (Editor). The second option will allow you to point to the specific editor, you want a screenshot from. You can also use a dedicated screen-grabber. Be sure that you can recreate this screenshot easily (in case you missed or the Blender UI changes and you need a new screenshot.
4. Open your SVG paint program; e.g. Inkscape. Paste the screenshot from the clipboard as an embedded image. The overhead of this embedding is reasonable. For example, a PNG file of 105 Kb results in a SVG file of 143 Kb.
5. Annotate the image. Because SVG is a vector format, these annotations can always be changed without having to recreate everything.

Blender-only solution
=====================

The basic idea of this workflow is to keep all info into one blend-file (and do all the work in Blender) in stead of dispersing the work and data into several third party programs (blender, screen grabber, graphic editor).

1. Create a blend-file with the same name as the figure; e.g. video_editing_setup_workspace.blend. If you have a high resolution monitor, it is perhaps better to set the Edit > Preferences > Interface > Resolution Scale to a higher value (e.g. 1.5) to enhance the readability of the text. Set the project resolution to the size of your monitor (e.g. 1920 x 1080 or 3840 x 2160 for a 4K monitor). Otherwise, Blender will scale your screenshot, resulting in a blurry output. *Is this correct?*
2. Prepare the Blender environment for the screenshot (e.g. choose workspace, resize, expand or collapse panels, ...).  With the menu Edit > Toggle Full Screen, you can hide hide the title bar where the file location of the Blend-file is displayed. Be sure that your Blender window is maximized (or remember the actual window dimensions).
3. Take a screenshot the menu Window > Save Screenshot or Save Screenshot (Editor). The second option will allow you to point to the specific editor, you want a screenshot from. Save this screenshot in a subfolder; e.g. screenshots-original. Later on, you can crop the image. You don't need a third-party screen grabber; except if you want to capture the mouse cursor or for example expanded menu-items. The problem with an external screen grabber however is that it is difficult to recreate the exact same size a second time. It is important that after the screen grab, the UI of Blender is not changed any longer (for example zoom level). *Question: is it possible to freeze the UI?*
4. Create a new scene (for example scene-output) with the Copy Settings option (so, that the resolution is automatically set correctly).  Activate 3D view (Layout workspace) and change to the Top level view. In this scene you create the annotated figure.
5. Add an Image as Plane (addon) with the aforementioned screenshot as source. Choose for an Emit Material Setting and a Camera Relative > Fill Plane Dimension. *Note: not sure this is the best option!*
6. Switch to Orthographic Camera view and and adjust the Orthographic scale until the complete screenshot fits into the camera view. With the View > Layout Properties, you can enable Render Region and Crop to Render Region. With these options you can crop the image to the desired size (if you are in Camera view).
7. Start annotating. There exists a preset Blend-file (grease-pencil-shapes.blend) that contains some sample texts and shapes, together with the appropriate materials and colors. Append this blend-file to your project and choose the needed text or shape objects (in the Objects folder).
8. Adding text. Append a preset text-object. Press Tab and change the content. Duplicate the object, if you need more text. You can add text yourself with the 3D Text object. Remember that you are in Top view, so you have to rotate the text 90° on the X-axis. *Question: should we propose a specific font and color?*
9. Adding shapes. Append the desired preset shape object (rectangle, arrow-single, arrow-double, arrow-single-curved, ...). You can scale and rotate these shapes as needed. You can create your own shapes with the Grease Pencil object.
    
    * Add a Blanc Grease Pencil object. Switch to Draw mode and create the desired shape. If you want some artistic annotation, you can draw the strokes. Or you can use one of the preset tools (line, polyline, arc, curve, ... ). If you use one of the preset tools, don't forget to switch on the Curve Editing in Edit mode. 
    * For the dashed line drawings, you need two modifiers: Simplify > Sample to generate equally distributed points in the shape and the dash-dot modifier to create the dashed line. See the predefined shapes in grease-pencil-shapes.blend for some inspiration. *Perhaps, there should be some kind of tutorial to create these shapes in GP.*
10. Create the final figure. Render the scene (don't forget Crop to Render Region if you only need a part of the screenshot). Save the rendered image as a .png file. Save the Blend-file.

If you need to update this figure: open the blend-file (eventually into a new version of Blender). Re-prepare the Blender environment (step 2). Try of course, to change as little as possible. Take the screenshot (step 3). Switch to the second scene and refresh the image datablock of the image-as-plane object (underneath the Material property).


.. note::
   Some of the above steps could be done with a Python script. The problem of huge png-files from HD monitors is not solved. Can they be scaled down within Sphinx? I've tried to put Blender into a 1920 x 1080 window on a 4K monitor but that is not very practical.