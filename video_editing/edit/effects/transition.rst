Transition
----------

A video transition is a post-production technique to connect one shot to another. The simplest transition is a basic cut where the first image is instantly replaced by the next.

.. figure:: /images/video_editing_edit_effects_transition_basic-cut.svg
   :alt: Basic cut

   Figure 1: Example of a basic cut in Sprite Fright - Blender Open Movie
 
A basic cut, such as in figure 1, is fine because the image content of the frames is very different and the viewer should have no problem to understand the change in the story ( in this case; it's also a very clever choice because the girl is peeping through a hole in the fence to discover a new world). In other cases, the change in the story is not that obvious and a video transition could help this other point of view.

With the menu Add, shortcut key :kbd:`Shft-A` or the shortcut menu :kbd:`RMB`, you can add transitions to two strips. It is not possible to add transitions to more than two strips at once.

The classic and most self-explanatory procedure is to place the two strips on different channels and let them overlap in time. The channels are normally consecutive (e.g. channel 1 & 2), but that has not to be the case.  An extra transition strip is placed at the first free channel above both strips with a run length of the overlap. Each frame of the transition strip is a blending of the two corresponding frames from input 1 and input 2 strip.

.. figure:: /images/video_editing_edit_effects_transition_add-methods.svg
   :alt: Add methods

   Figure 2: Two methods to add a transition between two strips

In order not to occupy additional channels, you can put the two input strips also on the same channel and leave a small gap between them. The gap will then be filled with the transition strip (see figure 2, second method). The gap can be zero frames, in other words, the input strips are placed next to each other. After adding the transition, nothing seems to be happened. However, the transition strip is created and if you drag the End handle of the first strip or the Start handle of the second strip, the transition strip will appear between the two strips. 

This is also how you have to shorten or lengthen the transition strip. You cannot change the Duration of the strip it self. The Duration is determined by the overlap of the two input strips. So, by dragging the handles of the input strips, and therefore changing the overlap, the length of the transition is likewise changed..

.. important::
   If the strips are still images, the content of both images is used to create the transition. Each frame in the transition is a combination of the same two images. If the two strips are movies, each frame in the transition contains a combination of the corresponding images in the offset range.

   .. figure:: /images/video_editing_edit_effects_transition_blending.svg
      :alt: Transition with Strip Offset
      
   
      Figure 3: Transition on strips with a Strip Offset Start or End


   In figure 3, the second frame in the transition is a combination of the corresponding images (E & 1) in the offset range. For the first and last frame in the transition, there is only one corresponding image in the Offset. The second image is filled in with the last used image (1 & E).

.. figure:: /images/video_editing_edit_effects_transition-direction.png
   :alt: Switch direction of transition
   :scale: 50%
   :align: right

   Figure 4: Switch direction

The order of selection of the two strips is important for the direction of the transition; e.g. from strip-1 to strip-2 or vice versa. The active strip (the one with the white rectangle) is the target strip; the transition runs from the non-active (but selected) strip to the active strip. In other words, the non-active strip is assigned to Input 1 and the active strip is assigned to Input 2. You can always change the direction of the transition by switching the Input 1 and Input 2 field in the side bar (see figure 4 and 5). You can also use the shortcut :kbd:`Alt-S` or :kbd:`RMB menu`  and Effect Strip > Change Effect Input > A --> B.

.. figure:: /images/video_editing_edit_effects_transition_direction.svg
   :alt: Direction of transition

   Figure 5: Direction of transition (input 1 vs input 2)

Cross & Gamma Cross Fade
........................

The Cross and Gamma Cross effect is a dissolve between the Red, Green and Blue color component and the alpha of the input 1 and input 2 strip. The input 1 strip is faded out (starts fully opaque and becomes gradually more transparent). The input 2 strip starts the transition fully transparent and becomes fully opaque. So, the second strip in time should be the input 2 strip; otherwise there will be a glitching effect. 

Figure 6 has two color strips with the following color:

* strip-1: RGBA(1,0,0,0.4); red color with alpha = 0.4
* strip-2: RGB(0,1,0, 0.6); green color with alpha = 0.6

.. figure:: /images/video_editing_edit_effects_transition_cross.svg
   :alt: Cross Fade

   Figure 6: Cross Fade between two colors (strip-1 and strip-2 are both PNG images)

The Cross fade takes 4 frames and the playhead is at the second frame. So, the Red component of the Cross fade has to go from 1 (input 1) to 0 (input 2) and the Green component from 0 (input 1) to 1 (input 2). The Blue component does not change between input 1 and input 2 and the alpha value goes from 0.4 to 0.6. To make this transition, the effect has 4 frames available. So, the Red component should be decremented by 0.25 each frame and the Green component should be incremented with the same value. The alpha should increment with 0.05 each frame.

As you can see in figure 6, at the second frame, the Red component = 0.74902 and the Green component = 0.24706 (+- 0.25 ). The alpha = 0.4471 or is incremented by about 0.05.

.. note::
   The alpha value of Color strips is *not* taken into account. The Cross Fade strip has always an alpha = 1, regardless the opacity of the input Color strips. Although the strips in figure 5 seems to be Color strips, they are in realty PNG's with an alpha channel.

Of course, this is done for each pixel in the preview window. The transition effect is applied *after* all transformations (crop, scale, modifiers, ...) on the input strips.

The Cross and Gamma Cross fade are very similar. According to the docs: "Gamma Cross uses color correction in doing the fade, resulting in a smooth transition that is easier on the eye". 

.. todo::
   To be elaborated.

Wipe
....

.. figure:: /images/video_editing_edit_effects_wipe-properties.png
   :alt: Wipe properties
   :scale: 50%
   :align: right

   Figure 7: Wipe transition properties

In a Wipe transition, two shots are connected with some sort of sliding animation. It looks as if one shot is wiped out to reveal the next one. The Wipe transition can be easily overdone; so use it sparingly and only to enhance the content. For example in a falling scene, the vertical wipe can strengthen the movement.

The Effect Strip Input 1 and Input 2 properties are already covered above; see figure 5 for an explanation. Remember that the first frames of the transition resembles more the Input 1 and the last frames more the Input 2 strip.

There are four types of Wipe transitions; each with a Fade In or Out direction; resulting in 8 different variants (see figure 8).

* Single: reveals the next strip by uncovering it in a straight line moving across the image. The Direction Out corresponds with a top to bottom or left to right (depending on the angle) reveal.  
* Double: similar to Single, but uses two lines either starting from the middle of the image or the outside. Like the blink of an eye; opening or closing, depending of the direction of the transition. With direction Out, Input strip 2 starts small at the middle of the frame and becomes larger. 
* Iris: reveals the next strip through an expanding (or contracting) circle. Like the aperture of a camera or pupil of an eye. You can blur the transition, so it looks like ink bleeding through a paper.
* Clock: like the hands of an analog clock, it sweeps clockwise or (if Wipe In is enabled) counterclockwise from the 9:00 position. As it sweeps, it reveals the next strip.

.. figure:: /images/video_editing_edit_effects_transition_direction-in-out.svg
   :alt: Direction In Out

   Figure 8: Eight transition variants (4 types x 2 Directions)

Direction: controls whether to fade In or Out. See figure 8 for the movement that corresponds with the In or Out direction.

Blur Width: in figure 8, the border of the sweeping line is very sharp (from green to red in one pixel. You can however blur this line, resulting in a more smooth gradient from the two colors. The width is specified in percentage of the the width of total image.

Angle: controls the angle of the line for Single and Double transition types. An angle of -45° will show a sweeping triangle from top left to bottom right.

The default Fade automatically calculates a linear fade over the length of the strip. So, if the transition strip is 4 frames, then the Single Fade Type will cover respectively 0, 0.25, 0.50, and 0.75 of the image area for frames 1 to 4 of the transition strip. If the default Fade is not enabled, then you can specify a custom Effect Fader. You can keyframe this field, so that each frame of the transition has a different Fader value. This allows you to create custom ease in or out effects (smaller areas in the beginning and end of the animation).

Sound Crossfade
...............

The Sound Crossfade transition works by animating the Volume of two overlapping Sound strips to evenly fade between them. Because this simply animates a value it does not create a strip like other effects or transitions. To apply the effect however, the two sound strips have to overlap (you cannot use method 2 from figure 1). To see the F-curves and the sound wave form, you have to enable them in Show Overlay (top right) and Display Waveform (bottom). As you can see in figure 9, the cross fade is implemented by keyframing the volume from the initial value to zero and vice versa. 

.. figure:: /images/video_editing_edit_effects_transition_sound-cross-fade.svg
   :alt: Sound Cross Fade effect

   Figure 9: Sound Cross Fade effect

   Because both strips in figure 9 have an initial volume = 1, the cross fade goes from 1 to zero for sound-1 and vice versa for sound-2. The animation has an ease in (starting slowly and accelerating) and ease out (slowing down at the end).