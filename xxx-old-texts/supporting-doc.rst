MPEG


MPEG-1: standard for storage and retrieval of moving pictures and audio on storage media
MPEG-2: standard for digital television
MPEG-4: standard for multi-media applications

MPEG-1 part 1: combining video and audio inputs into a single/multiple atastream
part 2: vieo compressionpart 3: audio compression
audio: mp1: little processing, poor quality
mp2: minimal processing, OK quality
mp3: massive processing, CD quality 

The command ffmpeg -i video.mp4 video.mpg will produce a MPEG-1 systems container. Use ffmpeg -i video.mp4 -f vob video.mpg for MPEG-2 PS.

Immediately after the PACK START CODE 00 00 01 BA. if the next two bits are 01, it's MPEG-2 PS (VOB, DVD-VOB or SVCD), else if it's 0010. it's MPEG-1 Systems or VCD

Need a small-sized video with a decent picture quality? Try a VBR
file with a low minimum data rate and a high peak. This will keep
the average fairly low while allowing the codec to decide when it
needs to spend more bits to get the image right.

Only certain audio codecs will be able to fit in your target output file. For example, the MP4 container, supports only MP2, MP3, LC-AAC, HE-AAC, and AC3 codecs. And the webM and Ogg file format can only contain a Vorbis and Opus codec (see FFmpeg docs for an `overview table of container - audio combinations <https://trac.ffmpeg.org/wiki/Encode/HighQualityAudio>`_ ).

128 kbit/s is considered the "sweet spot" for MP3; meaning it provides generally acceptable quality stereo sound on most music, and there are diminishing quality improvements from increasing the bitrate further. MP3 is also regarded as exhibiting artifacts that are less annoying than Layer II, when both are used at bitrates that are too low to possibly provide faithful reproduction.

MPEG-1 supports only noninterlaced video. Normally, its picture resolution is 352 × 240 for NTSC video at 30 fps, or 352 × 288 for PAL video at 25 fps. It uses 4:2:0 chroma subsampling. Layer III audio files use the extension ".mp3". 

MPEG-1 most commonly uses a GOP size of 15–18. i.e. 1 I-frame for every 14-17 non-I-frames (some combination of P- and B- frames). The standard uses macroblocks of 16 x 16 (so width & height are best exact multiples of 16).

