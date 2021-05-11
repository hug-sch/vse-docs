**********************
Useful FFMPEG commands
**********************

FFMPEG is a command line tool for handling (decode, encode, convert, …) video and audio files. It is used by many commercial and free software products, including Blender. The core is the FFMPEG program, together with a video & audio player (FFPLAY) and a stream analyzer (FFPROBE).

There are lots of tutorials for installing FFMEG and for using the command line (just google "how install ffmpeg"). A nice `3-part tutorial <https://www.youtube.com/watch?v=MPV7JXTWPWI&t=669s>`_ is by NerdFirst. 

**1. Trim a video lossless**

You have a source file "input.mkv" from which you want to cut a part in the middle. The following command will cut out the section from about 2 min and 2 sec (after the -ss command) to 2 min 43 sec (after the -to command). Both the video (c:v) and the audio (c:a) are copied without recompressing (copy). The result is wirtten to "output.mkv"

``ffmpeg -i input.mkv -ss 00:02:02 -to 00:02:43 -c:v copy -c:a copy output.mkv``


**2. Combine several video fragments into one file**

I used to create my videos in separate scenes; e.g. one scene for each month of a yearly review montage. During the year I could render the separate scenes into a video fragment. At the end of the year I need then to combine them into one piece.

``ffmpeg -safe 0 -f concat -i list.txt -c copy output.mp4``

The output file is called “output.mp4”. The monthly fragments are named in a separate file “list.txt” which contains 12 lines with the name of the fragments, eg. “01-jan.mp4 02-feb.mp4 … 12-dec.mp4”. You have to run the command in the folder where the fragments are located.

**3. Generate testfiles**

Sometimes you need a test video or test image with a specific resolution, duration or framerate. You can first try with ffplay to view the test video. Replace afterwards the ffplay command with ffmpeg and add the outputfile parameter.

``ffplay -f lavfi -i testsrc=duration=10:size=1280x720:rate=30``

``ffmpeg -f lavfi -i testsrc=duration=10:size=1280x720:rate=30 test.mp4``

This command will show/create a count-up video with a resolution of 1280 x 720 pixels, a framerate of 30 frames per second with a duration of 10 seconds in MP4-format More commands and test formats can be found at `bogotobogo <https://www.bogotobogo.com/FFMpeg/ffmpeg_video_test_patterns_src.php>`_.

The following command will show/create a red color background with opacity set to 0.2, with a duration of 5 seconds and a resolution of 640x480 with 10 a framerate of 10 fps in MP4-format.

``ffplay -f lavfi -i color=c=red@0.2:duration=5:s=640x480:r=10``

``ffmpeg -f lavfi -i color=c=red@0.2:duration=5:s=640x480:r=10 test.mp4``

**4. Create multiple video channels into one container

Some video containers can contain multiple video and audio channels; for example two surveillance camera outputs next to each other. In Blender you can select the channel to preview (not both at the same time) with Strip > Source panel > Stream index. The following command creates a two video channels  into one container.

ffmpeg -i input-1.mp4 -i input-2.mp4 -map 0:0 -map 1:0 output.mkv
