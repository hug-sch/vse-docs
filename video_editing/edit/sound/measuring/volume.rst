************
Volume level
************

Every program that works with audio has some sort of volume slider. And, they all have different meanings! In Blender, you can find it as a Property of the Sound Strip. It is a number between 0 and 100. A value > 1 will amplify the sound; a value < 1 will decrease the sound level. Simple, isn't it? But how loud is a volume level of 0.5? Is it half as loud as 1.0? And what about the max value of 100? Really? One hundred?

Relationship between Volume level value and loudness
====================================================

You can calculate the gain or loss in decibels (dB) with the following formula:

* dB = 20 x log (volume level)
* volume level = antilog (dB/20)

So, if you decrease the volume level to 0.5, this will result in a loss of -6 dB. Increasing the volume level to 100 will result in a gain of 20 x log(100) = 40 db. You can use the antilog function (10<sup>x</sup>) of a calculator to do the inverse: antilog(-6dB/20) = 0.5012.

.. csv-table:: Decibels versus Volume level
   :header: "db loss/gain", "-40", "-30", "-20", "-10", "-6", "0", "+6", "+10", "+20", "+30", "+40""
   :widths: 12, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4

   "Volume Level", 0.01, 0.0316, 0.1, 0.316, 0.501, 1, 1.995, 3.162, 10, 31.62, 100

According to psychological research, perceived loudness is doubled every 10 dB. So, to make a sound twice as loud, you have to set the volume level to antilog(+10dB/20) = 3.16. To reduce the perceived sound to half, you have to decrease the volume level to antilog(-10dB/20) = 0.316.

Remember that decibel is not a linear but a logarithmic scale. This is the reason of the asymmetrical Volume slider (0 - 100) instead of 0 - 1. If you set the slider to +100, you'll increase the loudness with 40 dB. To decrease the loudness with the same amount, you'll have to set the volume to 0.01. A handy conversion table can be found at `Wikipedia <https://en.wikipedia.org/wiki/Decibel>`_.

When a sound is digitized, the analog sound wave is sampled at discrete moments in time and the amplitude (the loudness) of the wave is stored. Two concepts are very important:

* Sample rate: a typical sample rate is 44.100 Hz (audio CD quality), which means that 44100 samples per second are taken. More samples results in better quality but also higher storage needs.
* Bit depth:  at each sample the amplitude of the analog sound wave is converted to a voltage that is stored in a number, typically a 16 or 24 bit integer. Because a 16 bit integer has only 2<sup>16</sup> = 65536 values, there will be a maximum amplitude that can be represented. These numbers are converted to a floating point number between -1 and +1. Amplitudes that exceed these thresholds (-1 or +1) will be clipped at -1 or +1  and result in distortion.

The volume or loudness of a sound is a perceptual/psychological phenomenon. As such, the loudness of a sound is influenced by many factors: the amplitude of the sound wave but also the frequency (bass tones need more power), the environment (e.g. distance to the sound source), the habituation of the listener, ... To simplify the following discussion, we reduce loudness (a psychological phenomenon) to the amplitude or voltage of the sound wave (a physical phenomenon).

The decibel scale is a relative scale; it's the ratio of a sound compared to some reference sound. For digital sound the reference is a sound with an amplitude of +1V or the maximum amplitude that can be stored with the chosen bit depth. Because of this definition - dB = log(sample voltage/1 V) - the dB value of a sample voltage = 1V is zero, because log(1/1) = 0. Zero dB is thus the maximum sound level we can have without distortion. Decreasing the sound level will result in a negative dB.

How to calculate the dB value in Blender Python?
================================================

The attached blend-file contains a Python script to calculate the dB value of a sound strip, as well as some other sound-parameters. The code is based on [Snuq's VSEQF-addon](https://github.com/snuq/VSEQF) (vu_meter.py). As example we use Blender's open movie [Spring](https://www.youtube.com/watch?v=WhWc3b3KhnY).

You first need a handle to the selected audio strip and the sound data that it contains. Because strip properties (eg Volume) can be animated, we need access to the animated data blocks which are continuously updated in the dependency graph for the current scene and view layer.

.. code-block:: Python

   import bpy
   import math

   strip = bpy.context.scene.sequence_editor.active_strip
   depsgraph = bpy.context.evaluated_depsgraph_get()
   sound = strip.sound.evaluated_get(depsgraph).factory


dB value for the whole strip
----------------------------

There are quite a few measures. The most used are:

* Peak value: what is the highest/lowest dB value in the strip. This is what you see in Volume Meter(VU-meter).
* RMS (Root-Mean-Squared): the average dB of the whole strip.

First, we need access to the sampled data. This is a two dimensional numpy float array. The first dimension is the number of samples. The second is the number of channels (1 for mono, 2 for stereo). The values are floating point numbers between 0 - 1.

.. code-block:: Python

   max = sound.data().max()
   min = sound.data().min()

   if abs(max) > abs(min):
      peak = abs(max)
   else:
      peak = abs(min)

   db = 20 * math.log10(peak)

The data()-method of the Sound-object returns the sampled data for the entire strip, even if the strip is trimmed and without the Volume-level applied. In other words, these are the raw sampled data. The peak value of a sound, however, is sometimes not a good estimate of the loudness of the sound. We need some kind of average. Because a sound-wave contains positive and negative sample values, a simple average will cancel out to about zero-level. A RMS value is the solution. Each sample value is squared (eliminating the negative numbers), then the mean (average) of these squares is calculated and reduced again to the original level with a square root.

Because the sampled data are contained in a numpy array, the code is relatively simple.

.. code-block:: Python
   
   samples = sound.data()
   m = np.mean(samples**2)
   rms =  np.sqrt(m)
   db = 20 * math.log10(rms)

dB value of the current frame or a section of a strip
-----------------------------------------------------

Suppose, you want the dB value for the sound samples underneath the playhead/cursor in the timeline. Audio strips however work with time code, not frames. This is the cause of many misunderstandings. For example, if you have a MP4-file (video + audio) and you change the frame-per-second parameter of the scene, then the length of the video will change but not the length of the audio strip. The duration of an audio-strip can be calculated, based on the sample rate and the number of samples.

.. code-block:: Python

   sample_rate = sound.specs[0]
   nr_of_samples = sound.length
   duration = nr_of_samples/sample_rate


You would expect that sound.length is equal to len(sound.data()) but apparently that's not true. For the open movie spring: sound.length = 20466685 and len(sound.data() = 20466688.

Because there are many more samples than frames, the sound data for each frame will contain several samples.

.. code-block:: Python

   nr_of_frames = strip.frame_final_end
   nr_of_samples_per_frame = nr_of_samples/nr_of_frames

In case of the open movie "Spring": duration = 464.1s, nr_of_frames = 11139 and nr_of_sample_per_frame = 1837.38. So, for each frame there are 1837 samples. To calculate the dB value underneath the playhead, we need the peak or rms value of these 1837 samples.

You can access these samples with the limit-method. This method works with timecode. So, you need the start and end time code of the current frame. These start and end times are relative to the selected strip. The first frame of the selected strip is zero. The current frame however is relative to the timeline. So, you have to subtract the strip.frame_start from the current frame. The calculation of the db or RMS value is the same as above.

.. code-block:: Python

   cur_frame = bpy.context.scene.frame_current
   fps = bpy.context.scene.render.fps / bpy.context.scene.render.fps_base
   time_from = (cur_frame - 1 - strip.frame_start) / fps
   time_to = (cur_frame - strip.frame_start) / fps
   sound_cur_frame = sound.limit(time_from, time_to)

The decibel value of a trimmed strip
------------------------------------

Because the Data method of a Sound object always returns all samples of the entire strip, you also have to use the limit-method (see above section 2.2) for a trimmed strip. [Trimming and cutting](../video/trimming.md) of a strip is extensively described in a separate post. Fig. 3 summarizes the different achor points.

.. code-block:: Python

   time_from = (strip.frame_final_start - strip.frame_start)/fps
   time_to = (strip.frame_final_end -  strip.frame_start)/fps
   sound_trimmed_strip = sound.limit(time_from, time_to)

The decibel value of an animated strip
--------------------------------------

The sound data contain the raw sampled data. To account for a changed volume level for the entire strip, you simply multiply this level with the raw data.

.. code-block:: Python

   max = sound.data().max() * strip.volume

The volume level of a strip, however can be changed and animated on a per frame basis. In section 2.2 you calculated the dB value for one frame. Thanks to the dependency graph, we can use the strip.volume value because this value will updated for that specific frame. So, to calculate the dB value for an entire animated strip, the easiest (but perhaps not the most efficient way) will be to loop through the strip frame by frame, set the playhead to that frame, retrieving the sound.data for the frame, multiplying it with the sound volume and cumulating these data into an array.

.. code-block:: Python

   def get_rms(samples):
      m = np.mean(samples**2)
      rms =  np.sqrt(m)
      return 20 * math.log10(rms)

   animated_samples = np.empty(shape=[0, 1])
   for f in range (strip.frame_final_start, strip.frame_final_end):
      bpy.context.scene.frame_set(f)
    
      time_from = (f - strip.frame_start - 1)/fps
      time_to   = (f - strip.frame_start)/fps

      chunk = sound.limit(time_from, time_to).data()
      chunk = chunk * strip.volume
    
        
      animated_samples = np.append(animated_samples, chunk, axis=0)
      print("frame ", bpy.context.scene.frame_current,"time:", time_from, "-", time_to, "-",
        "size:", len(chunk), "cum", len(animated_samples),
        "RMS:", get_rms(chunk), "volume:" ,strip.volume)
    print("total rms: ", get_rms(animated_samples))


Some useful URL
---------------

* https://www.sawvideo.com/index.php/news/2020/measuring-sound-levels-volume-and-loudness
* http://www.sengpielaudio.com/TableOfSoundPressureLevels.htm
* http://www.sengpielaudio.com/calculator-soundlevel.htm
* http://sengpielaudio.com/calculator-gainloss.htm
* http://www.sengpielaudio.com/calculator-loudness.htm
* http://sengpielaudio.com/calculator-levelchange.htm
* https://archive.org/details/fundamentalsofhe00yost/mode/2up

