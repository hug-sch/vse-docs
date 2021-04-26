E. Scene strip
==============

Blender has next to its VSE also a very impressive 3D and 2D modeling environment. You can model and render animated realistic scenes with it. But, instead of rendering out that scene to a video, and then inserting the video file in the sequence editor, you can insert the scene directly. Scene strips are a way to insert the render output of another scene into your sequence.

The strip length will be determined based on the animation settings in that scene. 

.. warning::

   Each scene has its own Video Sequencer. Scene strips cannot be used to insert the sequence's own scene. If you have a 3D animation in scene_1, you can insert it as a scene strip in scene_2 but not in scene_1.

The Compositing, Transform, Crop, Video, Color, Time, and Custom panels are unchanged. In the Time a new property is added: ``Original Frame Range`` . As the name indicates, this new property shows the the number of frames of the original scene held. A new Scene panel is also added.

**Scene**

.. figure:: img/panel-scene.png
   :scale: 50%
   :alt: Scene Property of Scene Strip
   :align: Right

   Figure 13: Scene Property of Scene Strip


``Scene header`` with logo, name and link/unlink checkbox. This header seems to be a duplicate of the header of the Properties Sidebar.

``Input`` Choice between Camera or Sequencer. The original Scene -where this Scene strip came from- can also have a Video Sequencer. Therefore, the output of that scene could be generated from that Video Sequencer or from the camera/compositor of that scene. In the original scene, this could be set in the Post Processing panel of the Output Properties. But, of course, it is not a good habit to change this setting from within another scene. So, With this input choice, you can choose between the two possibilities.

``Camera`` The same reasoning holds for multiple cameras. The active camera is set in the original scene. But the receiving scene can choose to use another camera. If the original scene has multiple cameras, you can choose here which camera to use. This is very useful in multicam-editing.

.. todo::
   Add info for Volume (meaning of slider value), further explanation for show grease Pencil and use of Transparent.
    
``Volume`` The volume of the original audio can be increased (> 1) or reduced (< 1) with this setting.

``Show Grease Pencil`` Shows Grease Pencil strokes in OpenGL previews.

``Transparent`` Creates a transparent background. This is useful for doing overlays like rendering out Grease Pencil films via the Sequencer. 

