***************
Timeline basics
***************

.. toctree::
    :maxdepth: 3
  
    timecode/timecode.rst
    zoom/zoom.rst
    navigate/navigate.rst
    scrub/scrub.rst
  
    As a video editor, you probably are most interested in the SMPTE-timecode. It seems more natural to refer to a video fragment with a time indication, e.g. 00:01:15:10 or 1' 15'' and 10 frames than with a frame number, e.g. frame 55. Blender, however, is in the first place a 3D modeling tool where framenumbers are much more common.

    Also don't make the mistake to think that timecode is equal to time. For modern video, all time information, you'll get is the timestamp at the start of the recording and the duration in frames of the video. So, the time codes should be calculated. 
    
    As the name implies, the timeline represents time (seconds). But, because the unit of a video clip (or strip in Blender talk) is one frame, the timeline is sometimes labeled in frames or a combination of time and frames. For example, in Blender you can choose to show the timeline in seconds or in frames. But, even the "seconds"-view is in fact a combination. The time code 01:21+11 indicates "1 minute and 21 seconds and 11 frames". Because each project has a frame-per-seconds `fps` parameter, you can always derive one code from the other. In a 30 fps project:
    
    * frame 155 is at time 115/30 = 3.8333 seconds or in Blender notation: 00:03+25.
    * time 2.5s falls within frame  2.5 * 30 = 75.