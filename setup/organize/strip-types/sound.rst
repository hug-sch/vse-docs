Sound strip
===========

The input source of a Sound strip is an audio file with extension ``.AAC``, ``.AC3``, ``.FLAC``, ``.MP2``, ``.MP3``,  ``.opus``, ``.PCM``,  or ``.vorbis`` (see `audio formats <https://docs.blender.org/manual/en/dev/files/media/video_formats.html>`_). You can add a Sound strip directly from one of the above-mentioned filetypes. It is also indirectly created when you add a Movie strip from a video file with an embedded audio channel. Blender will automatically extract the sound strip and put it in the channel beneath the video strip (if there is room). There is no linking between the source video file and the embedded audio. So, you can move the sound strip without moving the movie strip and vice versa; thereby creating a synchronization problem. The :ref:`default <default-color>` color of the Sound strip bar is: :sound:`███` 

.. warning::

   Sometimes, after adding a Movie strip, you will notice that the Movie and Sound strip have not the same length. This is the result of a mismatch between the Frame rate (fps) of the project and the video clip.

.. figure:: img/sound.svg
   :alt: Synchronization problem
   :align: Right

   Figure 1: Synchronization problem, due to unmatched fps.

Suppose, you are adding a 30 fps video with a duration of 1 second or 30 frames to a 24 fps project. The embedded audio in the video file is of course synchronized with the frame sequence of the video. Frame 1 of the video file is synced with a specific time code in the audio, and so is frame 2, frame 3, ... In figure 1, there is a beep at timecode 0.27 s (frame 8) and at 0.73 s (frame 22). But, the project runs at 24 fps. The beeps still occur at 0.27 and 0.73 s but frame 8 and 22 are shifted to the right. Frame 24 in the project is after all at time code 1 s, so, frame 22 is lightly before that at timecode 0.91 s. The Sound strip therefore will end at frame 24 because sound cannot be compressed without changing the Pitch.

.. admonition:: Panels documented elsewhere!

   The following panels are identical to those of the Movie strip: :ref:`Time <time-panel>`, :ref:`Source <source-panel>` and :ref:`Custom <custom-panel>`.
   
There are **no** *Compositing*, *Transform*, *Crop*, *Video*, and *Color* panels for the Sound strip. The following properties are **specific** for sound strips.

.. admonition:: Sound Panel

   :menuselection:`--> Sequencer --> Strip --> Sidebar --> Panel --> Sound`

.. figure:: img/panel-sound.svg
   :scale: 80%
   :alt: Sound Panel
   :align: Right

   Figure 2: Sound Panel

Volume
   The volume or loudness of the sound. Setting the Volume to zero will mute the sound. A value of 0 - 1 will reduce the volume,  while a value = 1 results in the original sound level. Above 1 will increase the sound level. However, does a sound with value = 2 sound double as loud or with value = 0.5 half as loud as the original? Not at all! 

   For more detailed information about the interpretation of the sound level in terms of decibels; see :doc:`Volume level </edit/sound/measuring/volume>`.

Pitch
   Pitch (lower versus higher tones) is closely related to the frequency of a sound. The Pitch value of the Sound strip will change the playback speed or frequency of the sound. Increasing the value will make the sound appear higher in tone, decreasing will lower the tone. Because the playback rate is also changed, the length of the sound is changed.
   
   This is however not visually represented in the timeline. Neither the length nor the shape of the waveform is changed. The Sound strip appears equally long as before but the sound will stop earlier or premature in case of a reduction of the speed.

.. figure:: img/sound-waveform.svg
   :alt: Sound waveform

   Figure 3: Sound waveform does not change with pitch change in Blender

Figure 3 shows the waveform of a countdown audio file. Whatever pitch you select, this waveform and length will not change in Blender. The middle waveform is from the same file in Audacity with a speed value (= pitch value in Blender) of 1. As you can see the length of this wave is the same; ~ 13 s. When the speed is changed to 1.4, the length of the wave is reduced to 9.5 s (~13s /1.4) in Audacity but visually not in Blender. However, playing the audio will reveal that the tone height (and speed) is about the same and that the sound will stop at ~9.5 s. Please, note also that the file is stereo in Audacity but mono in Blender.

So, changing the pitch or duration of a sound file can -and is usually- also done with the :doc:`speed control </edit/effects/speed/speed>` in Blender.
:doc:`Striptypes </setup/organize/strip-types/blender-striptypes>`

Pan
   .. figure:: img/sound-pan.svg
      :scale: 50%
      :alt: Pan values
      :align: Right

      Figure 4: Pan values
   
   Depending on your sound system, you have one, two, or more speakers. Panning is the distribution of the sound over those speakers. It is mainly used to pan (distribute) the audio from left and right channels.  Pan values can be between -2 and 2 (see figure 4). A value of zero means front/center (12 o'clock). An equal amount of sound is sent to the left and right speakers. A value of -1 means that all sound is sent to the left channel (10 o'clock). And a value of +1 means that the sound will appear at 2 o'clock).  In the case of multichannel audio (rear speakers), you can pan to those with the higher values: -2 (7 o'clock) and +2 (5 o'clock). So this value basically represents the angle at which the sound is played. Only works for mono sources.


Display Waveform
   Display an approximate waveform of the sound file inside of the sound strip. The waveform reflects strip volume. This volume can be animated using keyframes. If the waveform is not displayed, you'll have to turn on the Show Overlays (button at the top right; see figure 1).

Mono
   Mixdown all audio channels into a single one.

Pack
   Packing the sound file means that the sound is embedded -not linked- in the blend-file. This can ease the job of transferring a project to another computer because you have to distribute only one file. But, remember, we advocate the use of a single, all-containing project folder  (see :doc:`../dir-structure/creating-directory-structure`). Packing the file will only increase the size of the Blend-file and is in any case already included in the distribution of the project folder.

Caching
   The sound file is decoded and loaded into RAM for fluent playing.

