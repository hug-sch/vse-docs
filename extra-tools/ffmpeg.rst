FFMPEG
******

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

**4. Create multiple video channels into one container**

Some video containers can contain multiple video and audio channels; for example two surveillance camera outputs next to each other. In Blender you can select the channel to preview (not both at the same time) with Strip > Source panel > Stream index. The following command creates a two video channels  into one container.

``ffmpeg -i input-1.mp4 -i input-2.mp4 -map 0:0 -map 1:0 output.mkv``

**4. Fix the "not divisible by 2" error**

Sometimes you need a render resolution, other than the classic 1080p (1920 x 1080). You can then enter your X and Y Resolution in the Dimensions panel of the Output Properties. However, when you try for example 1500 px x 399 px and use the H.264 codec you'll get the "not divisible by 2" error (or worse sometimes, a crash). The reason for this error is that the H.264 encoder uses macroblocks of a fixed size (e.g. 4x4) to compress your movie. Each frame is divided into these small macroblocks and to compress your video, it only encodes the differences between these macroblocks.  However, this adds the requirement that the width and height of your movie must be divisible by 2.  Changing the Y-resolution to 400 will fix the problem.

If, for some reason, you want to stick with the original resolution of 1500 x 399, then you have to render your animation first as a PNG sequence. The PNG format does not has this restriction on width & height. Of course, you don't have a playable movie.

Therefore, you need FFMPEG to create a movie (e.g. MP4) of it. To create a movie out of a sequence of images, you need the following command:

``ffmpeg -f image2 -r 24 -i %04d.png test.mp4``

- ``-f image2`` specifies the filter to convert from images to movie
- ``-r 24`` sets the framerate to 24 fps
- ``-i %04d.png`` specifies the input as a 4 digit number, followed by .png, e.g. 0001.png, 0002.png, ...
- ``test.mp4`` specifies the output file.


