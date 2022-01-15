Animation
---------

Blender is a 2D modeling and animation program. So, animation appears in many different places; for example, rigging, 2D animation (grease pencil), physics simulation and, of course, in video editing.

Animation in the VSE is exclusively achieved with the use of keyframes. Creating and editing `keyframes <https://docs.blender.org/manual/en/latest/animation/keyframes/introduction.html>`_ is extensively described in the docs; section `animation & rigging <https://docs.blender.org/manual/en/latest/animation/keyframes/introduction.html`_ . 

Here's how to create a `Ken Burns effect <https://en.wikipedia.org/wiki/Ken_Burns_effect>`_; to simulate motion from still images.

.. figure:: /images/video_editing_edit_effects_animation_ken-burns.svg
   :alt: Ken Burns effect
  

   Figure 1. Example of Ken Burns effect

1. Select the strip you want to apply the effect on. You cannot add keyframes to multiple strips in one action.
2. Set the playhead at the very start of the strip.
3. Zoom in on the image for a wide-angle view.
4. Hover the mouse cursor over the transform > Scale X attribute in the side bar.
5. Press I to insert a keyframe. Repeat step 4-5 for the Scale Y attribute; eventually also for the Position X and Y attributes. This action will remeber the original zoom-state of the image; eg. the green outline in figure 1.
6. Move the playhead to the last frame of the still image strip.
7. Zoom in on the image; eventually reposition the image a bit. This is represented by the red rectangle in figure 1.
8. Repeat step 4-5 for each attribute.

