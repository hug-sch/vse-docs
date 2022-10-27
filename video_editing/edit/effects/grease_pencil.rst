Animation with Grease Pencil
----------------------------
To create a Grease Pencil animation over your footage in the Video Sequence Editor, you need two scenes; one for the Grease Pencil animation and one for the Video Sequencer. Let's call them GP-scene and VSE-scene. The GP-scene can copy the settings from the VSE-scene. This will make the framerate, number of frames and resolution of both scenes the same (a camera however is not copied).

.. figure:: /images/video_editing_edit_effects_grease_pencil.svg
   :alt: Grease Pencil Animation (scene from VSE)

   Figure 1: Video Sequencer with a Scene strip

Add the GP-scene as a scene strip in the VSE-scene (menu Add > Scene) on top of the already existing footage. Of course, the animation hasn't been created yet, so nothing will appear in the preview.

Switch to the GP-scene and open the 2D Animation workspace. Add a new camera and position it correctly. You also have to make the canvas background transparent. Switch to the Render Properties in the Properties panel and set the Film property to Transparent. Put the Current Frame indicator at frame 1 and add a Grease Pencil object (menu Add > Grease Pencil > Blank). Switch to the Draw mode in Grease Pencil and draw something on the canvas.

.. figure:: /images/video_editing_edit_effects_grease_pencil-strokes.svg
   :alt: Grease Pencil Animation (scene from 2D Animation)

   Figure 1: Video Sequencer with a Scene strip


Switch back to the VSE-scene and to the Video Sequencer Editor workspace and look for the result. You will see the GP drawing on top of the underlying movie. You probably need to switch first to the Material Preview Shading in the View panel of the Properties of the Preview.

Some real-life work-arounds

- The GP animation remains visible throughout the entire sequence of the Scene strip. If you have only one animation, you can trim the Scene strip. If you need multiple animations, the following options are available:
   - Create the keyframes from the first animation (e.g. Frames 1 - 20), insert a blank keyframe at frame 21 (with the menu Key > Insert key frames and create the next animation.
   - You can also create a different layer for each animation (in the Layers panel of the Grease Pencil property) and keyframe the Set Layer Visibility property (Eye icon in the Layers panel) appropriately.
- The preview from the VSE is not automatically visible in the 2D Animation workspace. You have to draw your animation so to speak in the dark. A work around is to insert a plane with the original movie strip as source. You can use the addon Image As Plane. Don't forget to specify the Orientation as Align to Camera (or position the camera yourself). If you have cut the movie strip in the VSE, you also have to specify an offset in the Material panel of the Plane. Don't forget to disable Rendering in the Outliner tab (click on the Camera icon). Otherwise, you will see the output of the GP-scene video.
- You can create the animation keyframe by keyframe or use the automatic interpolation of Blender. For this, draw the first key frame, create a second keyframe (duplicate or drawn), switch to Edit mode,  put the Current frame between those two keyframes on the timeline, hit Ctrl-Shft-E or the menu Grease Pencil > Interpolate Sequence. All frames between the two original ones will be filled with a transitory image.
