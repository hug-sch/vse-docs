Sound strip
===========

The input source of a Sound strip is an audio file with extension ``.AAC``, ``.AC3``, ``.FLAC``, ``.MP2``, ``.MP3``,  ``.opus``, ``.PCM``,  or ``.vorbis`` (see `audio formats <https://docs.blender.org/manual/en/dev/files/media/video_formats.html>`_). You can add a Sound strip directly from one of the above mentioned filetypes. It is also indirectly created when you add a Movie strip from a video file with an embedded audio channel. Blender will automatically extract the sound strip and put it in the channel beneath the video strip (if there is room). There is no linking between the source video file and the embedded audio. So, you can move the sound strip without moving the movie strip and vice versa; thereby creating a synchronize problem.

.. warning::

   Sometimes, after adding a Movie strip, you will notice that the Movie and Sound strip aren't the same length. This is the result of a mismatch between the Frame rate (fps) of the project and the video clip.

   Suppose, you are adding a 30 fps video with a duration of 1 second or 30 frames to a 24 fps project. The embedded audio in the video file is of course synchronized with the frame sequence of the video. Frame 1 of the video file is synced with a specific time code in the audio, and so is frame 2, frame 3, ... But, due to the different framerates, frame 24 in the sequencer is really frame 30 (1 s) in the video file, which is the end of the video and embedded audio. The Sound strip therefore will end at frame 24 because sound cannot be compressed without changing the Pitch.

There are no Compositing, Transform, Crop, Video and Color panels for the Sound strip. The Header, Time, Source, and Custom panels are the same as for a Movie strip. The following properties are specific for sound strips.

.. admonition:: Sound Panel

   :menuselection:`--> Sequencer --> Strip --> Sidebar --> Panel --> Sound`

.. figure:: img/panel-sound.png
   :scale: 50%
   :alt: Sound Property of Sound Strip
   :align: Right

   Figure 1: Sound Property of Sound Strip

Volume
   The volume of the sound. Setting the Volume to zero will mute the sound, a value of 1 results in the original sound level and a value > 1 will increase the sound level. However, does a sound with level 2 sounds double as loud as the original; a more detailed explanation is given in the advanced section.

   For more detailed information about the interpretation of sound level and decibels; see :doc:`Volume level </edit/sound/measuring/volume>`.

Pitch
   Pitch (lower versus higher tones) is closely related to the frequency of a sound. The Pitch value of the Sound strip will change the playback speed or frequency of the sound. Increasing the value will make the sound appear higher in tone, decreasing will lower the tone. Because the playback rate is also changed, the length of the sound is changed.
   
   This is however not visually represented in the timeline. The Sound strip appears equally long as before but the sound will stop earlier or premature.

.. todo::
   Add a link to the speed strip: youtube.com/watch?v=VqP1j87aeU4

Pan
   Depending on your sound system, you have one, two or more speakers. Panning is the distribution of the sound over those speakers. It is mainly used to pan (distribute) the audio from left and right channels.  Pan values can be between -2 and 2. A value of zero means front/center (12 o'clock). Equal amount of sound is sent to the left and right speaker. A value of -1 means that all sound is sent to the left channel and 1 to the right (10 o'clock). And a value of +1 means that the sound will appear at 2 o'clock).  In case of multichannel audio (rear speakers) you can pan to those with the higher values: -2 (7 o'clock) and +2 (5 o'clock). So this value basically represents the angle at which the sound is played. Only works for mono sources.

.. todo::
   image about dragging sound around?

Display Waveform
   Display an approximate waveform of the sound file inside of the sound strip. The waveform reflects strip volume and its animation using keyframes. If the waveform is not displayed, you'll have to turn on the Overlays (button at the top right; see figure 1).

Mono
   Mixdown all audio channels into a single one.

Pack
   Packing the sound file means that the sound is embedded -not linked- in the blend-file. This can ease the job of transferring a project to another computer because you have to distribute only one file. But, remember, we advocate the use of a single, all-containing project folder  (see :doc:`../dir-structure/creating-directory-structure`).

Caching
   The sound file is decoded and loaded into RAM for fluent playing.

