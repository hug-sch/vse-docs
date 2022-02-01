Speed
-----

With the Speed Control strip, you can change the apparent speed of an action in a shot. This is done by inserting or skipping frames in the preview of the strip.

.. figure:: /images/video_editing_edit_effects_speed-control-basic-concepts.svg
   :alt: Speed Control Basic concepts

   Figure 1: Speed control - basic concepts

The top strip in figure 1 contains the recording of a 0.5 second motion-trajectory of a red ball, recorded in camera with a frame rate of 24 frames per second (fps). This strip is imported in a Blender VSE project with the same frame rate. With a Speed control strip, you can produce the two bottom strips The bottom strip contains a slow-motion of a fragment (the first 6 frames of the original). This is done by inserting a duplicate of each frame.  It takes 0.5 s or 12 frames for the ball to travel half of the original trajectory. The apparent speed of the ball is halved. The mid strip illustrates a time lapse or speed-up. This is done by skipping each other frame in the preview. The trajectory is completed in 0.25 s, whereas in the original strip half a second was needed. The ball seems to move twice as fast.

.. note::
   The above mentioned method of slow-motion is *not* a real slow-motion (slow-mo). Therefore, you need different recording and presentation frame rates. When you shoot a video, your camera records the action with a certain frame rate; e.g. 24 or 30 images or frames per second. For a regular replay, your presentation frame rate (Blender's project frame rate) need to be the same as the recording frame rate.
   
   Suppose however, that the recording frame rate of your camera is 60 fps; so 1 second of actual movement is spread over 60 frames. But, you can import this clip into a Blender project that is set with a 30 fps frame rate. So, in Blender, it will take 2 seconds to play this clip of 60 frames. The movement in the clip seems to be slowed down (1 second of actual movement is spread over 2 seconds of display time). This is real slow-motion; each frame is a real tiny movement. With the Speed Control, you insert duplicate frames; so only half of the movement in figure 1 is real. The other half never actually took place at that moment in time.

To add a Speed Control strip, you have to select a regular Movie, Image Sequence or Meta strip (in figure 2, this is the Target strip). With the menu :menuselection:`Add --> Effect --> Speed Control`  or :kbd:`Shft A` you can add a Speed control strip (green bar in figure 2). This strip is put above the original target strip and cannot be moved below it (but it can be moved higher up). You can look at it as a modified copy of the target strip, so you can hide the original target strip.

.. figure:: /images/video_editing_edit_effects_speed-control-properties.png
   :alt: Speed control properties
   :scale: 50%
   :align: right

   Figure 2: Speed control properties

Options
.......
With the Speed Control strip, you can choose between four methods to create the speed effect: Stretch, Multiply, Frame Number, and Length.

Stretch
   The playback speed is determined by the relationship between the duration of the original target strip and its current visible duration. In figure 3, the original target strip has a duration of 10 frames (frame 0 - 9). Dragging the right strip handle to the left will shorten the strip by introducing a Strip Offset End. So, the visible strip and also the Speed Control strip counts 6 frames (0 - 5).

   .. figure:: /images/video_editing_edit_effects_speed-control.svg
      :alt: Speed control - stretch option
 
      Figure 3: Speed Control - Stretch option with skipping frames

   The Speed Control strip in figure 3 seems to play faster because it skips some frames from the original target strip (e.g. C, E, H, and J). It squeezes (stretches) the original target strip of 10 frames into a playback strip of 6 frames; so, its seems to play faster. The playback rate, of course, is always the same and equal to the project's FPS.

   Which frames are skipped and which are displayed? Each frame in the Speed Control strip gets its value, based on its relative position within the strip. For example, the fourth frame (frame 3 because index starts at zero) in the speed strip gets the value F because frame 5 in the target strip is at the same relative position as frame 3 in the Speed Control strip. The formula is: ``relative position within speed strip * duration of original target strip``.

   What will happen if you shorten the original target strip even more, for example up to two frames. The first frame will again contain the value of A because 0/2 * 10 = 0 or the first frame in the target strip. The second frame contains F because 1/2 * 10 = 5 which contains the value F. You could argue that if you want to speed up a 10 frame strip to only two frames, you should choose the first and last frame, in stead of the first and mid one.

    You can also increase the visual duration of the original strip by dragging the right handle to the right or introducing a Still Offset End (see :doc:`Time panel Movie strip <../montage/striptypes/movie>`).  This will introduce a slo-mo effect.

   .. figure:: /images/video_editing_edit_effects_speed-control-still-offset.svg
      :alt: Speed control with Still Offset End

      Figure 4: Speed Control - Stretch option with inserting frames
   
   In figure 4, the Speed Control strip is twice as large as the original target strip. So, each frame is duplicated, which will reduce the playback speed effectively to half. For example: frame 4 (in speed strip) gets the value of 4/20 (relative position) * 10 (duration of original strip) = 2 or value C. Frame 5 gets the value of 5/20 x 10 =  2.5 or rounded down 2; thus also value C.

   .. Important::
      The effect of the stretch option is controlled by the amount of the Strip Offset End. A larger offset results in a faster speed. The Speed Control strip is *not* influenced by a Strip Offset Start, Hold Offset Start, or Hold Offset End. These Offsets will only change the length of the preview by skipping the first or last frames but will have no effect on the speed.

   .. tip::
      The Stretch option can be very handy if the video and audio strip haven't the same duration; mostly because of a mismatch between the framerate of the strip and the project. A change in video speed is often less noticeable than a change in audio speed (which will influence the pitch).
   
Multiply
   If you select the Multiply option, an additional field (Multiply factor) is shown. A multiply factor > 1 will speed up the preview. A factor < 1 will slow down the action. The input for this effect is the entire original target strip minus the Strip Offset Start, Hold Offset Start and Hold Offset End. The Hold Offset End will reduce the duration of the preview but not the speed effect. Figure 5 shows the result of different Multiply Factors with a Target strip A ... J. 

   .. figure:: /images/video_editing_edit_effects_speed-control-multiply.svg
      :alt: Speed Control with multiply option
         
      Figure 5: Speed Control with multiply option
   
   The top-panel in figure 5 has a Multiply factor = 1.3. Each frame in the Speed Control strip represents the duration of 1.3 frames of the target strip. So frame 4 of the Speed control contains the value of 4 * 1.3 = 5.2 ~5 or the value of frame 5 of the target strip; e.g. F. Because, some frames are skipped, the Speed Control strip will run out of frames before the end frame. When this occurs, it will just keep repeating the last one; the action will appear to freeze. This is shown in frames 8 and 9; which refer to a non-existing target frame (8 * 1.3 = 10.4 and 9 * 1.3 = 11.7). So, the last value (J) is repeated. Up until frame 8, the movie seems to play faster.
   
   The mid-panel has a Multiply Factor = 0.4. So, the duration of two frames of the target strip is even a little less than the duration of one Speed Control frame. The movie seems to play slower. There isn't even any action until frame 3. Because of this lower playback speed, not all frames from the target strip could be shown in the equal-sized Speed Control strip.

   The bottom panel is a special case because there is a Strip Offset Start and End. Because of these Offsets, the duration of the Speed Control strip is reduced with the sum of both Offsets. The duration of the Target strip, however is only reduced with the strip Offset Start. The first frame (frame 0) of the Target strip has value C. The first two frames (A & B) are no longer accessible. But the last two frames (I & J) - even if they are not visible - are still accessible as frame 7 & 7 to the Speed Control. Because of the Multiply factor of 1.5, the action seems to play faster (frames E & H are skipped).

    You won't get any visual clues in the effect strip that point to the direction or size of the speed effect. You have to deduce it from the preview.

.. note::
   It is possible to enter and keyframe a negative Multiply value. This will reverse play the strip. See video below, for an example.

.. raw:: html

   <video controls src="/_static/videos/video_editing_edit_effects_speed-control-multiply-negative.mp4" width ="640"></video>  

The target strip has a duration of 100 frames (1 - 100). A keyframe is set on the Multiply factor with value = 1 at frame 1 and value = -1 at frame 100. Note that a F-curve appears in the Graph Editor that runs from +1 (frame 1) to -1 (frame 100). It crosses the zero value at about frame 50. So, from frame 50 on, the Multiply factor is negative and the play direction should be reversed. The preview shows a value of about 25. This is because the Multiply factor < 1 in the range 1 -50; so, the speed slows down.

Frame Number
   This option provides you with maximum control. For each position of the playhead (current frame), you can specify a frame number from the target strip to display in the Speed Control strip. Because you can :doc:`keyframe </animation/keyframes/index>` this Frame Number value, you are able to specify custom speed profiles. For example, suppose you want a slo-mo effect of the target strip from figure 2 *but* between frame C and F. So, the 9 available frames from the Speed Control has to be filled with the frames C, D, E, and F.

   * Select the Speed Control strip with the option Frame Number and set the playhead at frame 0 (first frame). Normally, it should display the letter A; which is the first frame of the target strip.
   * Enter the value 2 in Frame Number (frame 2 in the target strip is value C). The preview changes to C.
   * Keyframe the Frame Number attribute (press I when hovering over the field). The field becomes yellow a an indication of the existence of a keyframe.
   * Set the playhead to frame 9. The Frame Number attribute is green; indicating that the value is governed by a keyframe that is not changed since. The value is still 2 and the preview is C.
   * Change the Frame Number value to 9. The preview changes to J and the attribute color changes to brown.
   * Keyframe this value (color changes to yellow)
   
   If you play the animation the following sequence will be shown: C, C, C, D, D, D,  E, E, E, F; which is effectively a slow-mo between C and F.setting this value to 50 displays the 50th frame.

Length
      As with the previous option *Frame Number*, this option will display a frame from the target strip but the frame number is specified as a percentage. For example, 50% will result in figure 2 as frame 5 (F), which is the mid frame of the target strip of 10 frames.
      
      You can also keyframe this value as in the example from above.

Frame Interpolation
   Crossfades between frames to reduce screen tearing when the speed is slower than the original frame rate.


Examples
........

Creating a Slow-Motion Effect
,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

Select the clip and :menuselection:`Add --> Effect --> Speed Control` effect strip.
Set the Speed Control option to Multiply and the Speed factor to be the factor by which you want to adjust the speed.
To cut the displayed speed by 50%, enter 0.5. Now, a 275-frame clip will play at half speed, and thus display only the first 137 frames.

If you want the remaining frames to show in slow motion after the first set is displayed, double the Length of the source strip (Time Panel > Duration). If you are using a speed factor other than 0.5 then use the formula:

``new_length = real_length / speed_factor``



Creating a Time-Lapse + Freeze + Slow-mo sequence
,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

Action movies often use the effect of a speeded action up until a certain momentum, then a freeze for a few seconds, followed by a slow-motion; e.g. bullets flying, impact, and slow-mo explosion.  

Suppose, you have a 150 frames sequence. The first 100 frames should be played at twice, the speed. Frame 100 should be freezed for 20 frames, and the following frames (101 - 150) should be played in slow-motion (half of the speed).

You could this easily by splitting the strip into three parts (0-100, 100, and 101-150) and using the techniques described above. You can also accomplish this with one strip and the Frame Number option.

* Place the playhead at frame 0 and keyframe the field Frame Number (to zero).
* Move the playhead to frame 49, change the value of Frame Number to 99 and keyframe again.
* Move the playhead to frame 50, change the value of Frame Number to 100 and keyframe.
* Move the playhead to frame 69, leave the value of Frame Number to 100 and keyframe.
* Move the playhead to frame 170, change the value of Frame Number to 150 and keyframe.

To get even finer control over your clip timing, you can use the Graph Editor (see figure 6).

.. figure:: /images/video_editing_edit_effects_speed-control-frame-numbers.svg
   :alt: Speed control in combination with Graph Editor

   Figure 6: Speed control (option Frame Number) in combination with Graph Editor

The horizontal axis represents the Sequencer timeline. The vertical axis represents the internal frame sequence of the Target strip. As you can see, the first 50 frames in the Sequencer timeline run from frame 0 to frame 99 in the Target strip frame sequence, so, in fact, skipping each other frame. Frame 100 (from the Target strip) remains in place until frame 69 of the Sequencer timeline (=freeze). The slo-mo is illustrated by the fact that you need 100 frames from the Sequencer timeline to play only 50 frames from the internal Target strip frame sequence. Because the original Target strip only took 150 frames on the Sequencer timeline, you have to expand its duration up to 170 (the dark purple region at the right).

While it is possible to keyframe the Multiply factor, usually you want to keyframe the Frame number directly. The curve interpolation is set to Linear by default but you can change it to Bézier to create Ease In and/or OUT effects.

.. _video_editing-change_fps:

Changing Video Frame Rates
,,,,,,,,,,,,,,,,,,,,,,,,,,

You can use the speed control to change the frame rate in frames per second (fps) of a video.
If you are rendering your video to a sequence set, you can effectively increase or decrease the number of individual image files created, by using the Multiply option with the Multiply Factor.

For example, if you captured a five-minute video at 30 fps and want to transfer that to film, which runs at 24 fps, you would enter a Multiply Factor of 30/24, or 1.25
(and Enable Frame Interpolation to give that film blur feel).

Instead of producing ``5 × 60 × 30 = 9000`` frames, Blender would produce ``9000 / 1.25 = 7200 = 5 × 60 × 24`` frames. In this case, you set a *start* = 1 and *end* = 7200, set your Format output to for example ``jpeg`` 30fps, and image files ``0001.jpg`` through ``7200.jpg`` would be rendered out, but those images cover the entire 9000 frames. The image file ``7200.jpg`` is the same at frame 9000. Be aware that there can be a quality degradation, due to the encoding.

When you read those images back into your film blend-file at 24 fps, the strip will last exactly 5 minutes.






