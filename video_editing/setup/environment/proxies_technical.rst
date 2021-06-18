Proxies technical
=================

Videos can have huge file sizes. Taken for example a 4K file (3840 x 2160). One uncompressed frame needs 3840 x 2160 x 24 bits (8 bits for each color R, G and B)or 24 883 200 bytes, ~21 MB. 

The FFProbe code to select the first 10 frames and to pint the picture type

ffprobe -v error -hide_banner -of default=noprint_wrappers=0 -print_format flat  -select_streams v:0 -show_entries frame=pict_type -read_intervals "%+#10" dolby-4k.mkv


1920 x 1080 = 2 073 600 x 24 bits = 49 766 400 bits / 8 = 6.220 800 / 0 048 576 = 5.932 MB






Blender VSE Easy Proxy Addon for Video Sequence Editor
From https://blender.community/c/rightclickselect/0Nfbbc/


Ffmpeg Command:

We are using this command for building proxy:

ffmpeg -i input.mp4 -vf scale=640:-2 -vcodec libx264 -g 1 -bf 0 -vb 0 -crf 20 -preset veryfast -acodec aac -ab 128k out.avi

    This will create intraframes in h264 within an AVI container with a fixed width of 640 preserving aspect ratio.
    Fixed ratio of 640:-2 ("-:2" is needed for x264 to use the scale filter which needs to be divisible by 2) Details: https://ffmpeg.org/ffmpeg-filters.html#scale

Reasons we are using fixed width of 640 preserving aspect ratio are:

    It's straight forward. No need to make decision for variable size for a simple proxy operation.

    Mixed media like HD and 4k can be used together with the same quality.

    The interface can fit 640 width nicely.

    Industry is going for 4k and 4k+. Where 25% proxy creates a huge file size of 960x540 for example.

    Variable scaling also affects the encoding speed and frame blending.

    We are using CRF for the image quality and file size instead.
