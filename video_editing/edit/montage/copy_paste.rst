Copy - Paste
------------

You can copy/paste strips and keyframes within a scene and between scenes and projects. The latter two are a bit more complicated.

Within the same scene
.....................
To copy and paste a strip within the same scene:
* Select the strip or strips.
* Press :kbd:`Ctrl-C` or menu Strip > Copy or :kbd:`RMB` and select Copy.
* Move the playhead to the desired location
* Press :kbd:`Ctrl-V` or menu Strip > Paste or :kbd:`RMB` and select Paste.

To duplicate a strip within the same scene
* Select the strips or strips.
* Press :kbd:`Shft - D` or menu Strip > Duplicate Strips or :kbd:`RMB` and select Duplicate Strips.
* Move the strip by simply moving the mouse (no click or drag). The strip(s) will follow the mouse cursor. When in position, :kbd:`LMB-Click`.
  
The result of Duplicate and Copy/Paste is the same. Duplicate however is a bit easier and requires less mouse clicks.

There seems to be no **Cut and paste** equivalent. For that operation, you have to copy/paste first the strips and then delete the old strip.

.. Important::
   The Copy-Paste and Duplicate command will copy the associated keyframes of the source strip (BUT only within the same scene). For example, if the copy-strip has a rotation animation, then animation will be copied and duplicated to the destination strip. The position of the keyframes is calculated relative to the visual start of the strip.


Between scenes
..............

To copy and paste a strip between two scenes:
* Select the strip or strips in the source-scene.
* Press :kbd:`Ctrl-C` or menu Strip > Copy or :kbd:`RMB` and select Copy.
* Change the scene and move the playhead to the desired location
* Press :kbd:`Ctrl-V` or menu Strip > Paste or :kbd:`RMB` and select Paste.

.. Important::
   1. You *cannot* use the Duplicate command top make copies between scenes.
   2. Keyframes are *not* copied to the destination strip.

You can use the following work-around to copy the keyframes.
* First; copy and paste the strips as in the workflow from above. Keyframes are not copied.
* Select the destination strip and create at least one keyframe for the desired attribute; e.g. rotation. If there are keyframes on multiple attributes, you have to repeat this step for all the attributes that have keyframes.
* Switch to the source scene and open the Timeline Editor or the Dope Sheet Editor in a separate window. There, you will see the keyframes.
* Make a copy of the keyframes (:kbd:`Ctrl-C`).
* Switch to the destination scene, select the destination strip and position the playhead where you want the keyframes to start.
* Paste the keyframes (:kbd:`Ctrl-V`).If the keyframe from step 2 is within the range of the copied keyframes, it will be overwritten; else you have to manually delete it.
* Repeat the above steps for all attributes.

Between projects
................

You *cannot* copy individual strips between projects. If you need a certain strip from another project, you have to copy the entire scene.

* Append the project that contains the desired strip with the menu File > Append
* Select the appropriate project and the appropriate scene.
* If that scene name already exists in your project, it will be renamed to something as scene.001.
* Switch to that scene in the video editing workspace and copy the desired strips.
* Paste the strips in another scene (pay attention to the keyframes)
* Eventually, delete the appended scene.