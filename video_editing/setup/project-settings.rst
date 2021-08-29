Project settings
================

The Project Settings for your video project are grouped in the `Output Properties <https://docs.blender.org/manual/en/dev/render/output/index.html>`_ tab of the `Properties Editor <https://docs.blender.org/manual/en/dev/editors/properties_editor.html>`_. This editor is located at the top right area in the default Video Editing workspace and is shared with the other modules, e.g. 3D modeling. The Properties has several categories, which can be chosen via tabs (the icons column to its left). Each tab regroups properties and settings of a data type. For the VSE, only the Output properties are commonly used. This tab is selected by default on opening the Video Editor Workspace.

.. admonition:: Reference
   :class: refbox

   =============   ==============================================================
   **Name**:       *Dimensions*
   **Context**:    Video Sequence Editor > Properties
   **Location**:   Tabs > Output Properties
   =============   ==============================================================

.. figure:: /images/video_editing_setup_project-settings.png
   :alt: Project Settings
   :align: right
   :scale: 40%

   Figure 1: Dimensions panel   

Resolution
   The resolution X and Y refer to the number of pixels in the horizontal and vertical axis of the output video. Common video resolutions are:

   - High Definition (HD) or 720p (1280 x 720)
   - Full HD or 1080p (1920 x 1080)
   - Ultra HD (UHD) 4K or 2160p (3840 x 2160).

   Figure 2 shows these three common resolutions more visually. Note how small the HD resolution is, compared to the UHD or 4K version. Of course, there are many more formats for social media, film theater, .... A rather exhaustive list can be found at `Wikipedia <https://en.wikipedia.org/wiki/List_of_common_resolutions>`_.

   .. figure:: /images/vse_setup_project_resolutions.svg
      :alt: Resolutions
      :align: right
      :scale: 100%

      Figure 2: Ultra HD, FHD and HD resolution

Resolution %
   You can set the Resolution % (default = 100%) to a lower percentage to render the video temporarily in a lower resolution. For example, if set to 10%, a full HD movie will then render at the resolution of 192 x 108 pixels. You can check this by :kbd:`RMB` + Click & hold at the top right corner of the preview of the Video Sequencer. In the status bar, you will notice something like: ``X : 190  Y: 100 ...``, meaning that the location you clicked is at resolution X = 190 and resolution Y = 100. So the full render image is effectively 192 x 108 pixels. Of course, the picture will look terrible; you only have 192 x 108 = 20736 pixels at your disposal to draw the picture.

   Figures 3 - 4 show the render result with the percentage set to 10% and 5% of the 4K image of figure 2. Please note, that a 10% render of the UHD image still gives us an image of 386 x 216 pixels. The images are scaled up to have a clear view and the same dimensions of figure 2. Figure 4 is in fact only 192 pixels wide x 108 pixels tall.

   .. figure:: /images/vse_setup_project_tree-10.png
      :alt: Resolutions
      :scale: 200%

      Figure 3: Figure 2 rendered at 10%

   .. figure:: /images/vse_setup_project_tree-05.png
      :alt: Resolutions
      :scale: 400%

      Figure 4: Figure 2 rendered at 5%

   Lowering the resolution % is not meant to speed up the preview or the scrubbing of the timeline. For that, you need :doc:`proxies <proxies>`. Because proxies are enabled by default (see Edit > Preferences > System Video Sequencer > Proxy Setup), you will not notice much improvement in navigating the timeline.  Only the render time is affected. You can use this option if you want to create a quick test render, for example to check the audio synchronization of your video.

Aspect X/Y
   We tend to view the pixels of our computer display as little squares and for most modern computers, they are in fact squares. In the world of cinema and television, especially with older equipment, non-square pixels are commonplace. All movies on DVD and BluRay for example use rectangular pixels. Shooting with anamorphic lenses also gives a distorted raw image on a computer screen, due to the use of non-square pixels.

   Figure 5 shows an example of a raw image, taken with an *anamorphic lens* with a horizontal compression of 1.33. Anamorphic lenses are typically used in cinema to achieve an ultra wide screen view. To achieve this, the image is horizontally squeezed. Although perhaps not immediately that obvious, figure 5 looks a little bit distorted.

   .. figure:: /images/vse_setup_project_anamorphic-squeezed.jpg
      :alt: Image from an anamorphic lens (squeezed)
      :scale: 100%

      Figure 5: Raw image from an anamorphic lens

   With ffmpeg, you can retrieve the aspect ratio of this image. The result is:

   ``590x332 [SAR 96:96 DAR 295:166]``
   According to ffmpeg, the image is 590 x 332 pixels (so does Blender)

   .. figure:: /images/vse_setup_project_anamorphic-desqueezed.jpg
      :alt: Image from an anamorphic lens (desqueezed)
      :scale: 100%

      Figure 5: Post-processed image from an anamorphic lens


   This can give all sort of problems when you want to play an old DVD movie on your computer. Sometimes, the characters are squeezed or stretched. Why? And what can you do about it?

   .. todo::
      Describe in more detail and use example of anamorphic lens. For some examples, see The Pixel Aspect Ratio Acid Test: http://frs.badcoffee.info/PAR_AcidTest/ and https://ia800900.us.archive.org/11/items/TvTestCard/TvTestCard_512kb.mp4 and https://www.dpreview.com/articles/5787493634/shooting-photos-with-anamorphic-lenses-is-a-fun-way-to-get-out-of-a-creative-rut

RenderRegion/Crop to Render Region
   These options cannot be used in the VSE and will result in an error message ``Border rendering is not supported by sequencer``, if set..

Frame Start/End/Step
   The sequencer timeline can contain multiple strips, spread over over several hundreds of frames. You don't need to render all these frames. With the Start and End fields, you can limit the output range.

Step
   Controls the number of frames to advance by for each frame in the timeline. If the strip in the Sequencer contains 10 frames, then a step of 2 will render 5 frames (frame 1,3,5,7,9).

Frame Rate
   The number of frames that are displayed per second. The drop-down menu gives several common frame rates (23.98, 24, 25, 29.97, 30, ...). These presets refer to the different standards: NTSC (mostly in North-America) and PAL/SECAM (mostly Europe) and the necessary adjustments made in the 1950's to adapt  to color TV (23.98 and 29.97). Other frame rates can be used by selecting Custom. You can enter then a FPS and base number. The custom framerate is the result of: FPS/base number. For example, to simulate a 25 fps preset, you can enter FPS = 25 and base = 1 or FPS = 50 and base = 2.

   When the first video strip is added to the sequencer, the frame rate of the project is automatically set to the frame rate of that strip.Adding a second strip with a different frame rate (even if the first strip is deleted) will not change that setting. Blender VSE cannot handle different frame rates in one project. You will not get a warning, besides some odd-looking audio strips and slow or fast motion effect.

   .. figure:: /images/video_editing_setup_project-settings-fps.png
      :alt: Mixing of different FPS in one project
      

      Figure 6: Mixing of different frame rates in one project

   Figure 6 contains 3 strips that were recorded at different frame rates. Their capture frame rate was respectively 30 fps, 60 fps and 120 fps. Each recording took about 15 seconds. The strip with fps = 30 was first added. This has set the presentation frame rate of the entire project to 30 fps. Later on, strips of 60 fps and 120 fps were added. This does not change the project presentation frame rate, but, of course, the capture frame rate of the strips remains unchanged. All the audio strips have a duration of about 15 seconds because the audio is independent of the presentation frame rate. The strip with capture fps = 30 has also a duration of about 15 seconds. This is because the capture and presentation frame rate is equal. The strips with capture frame rate of 60 and 120 fps are much longer. On the watch itself, you can see that after about 15 seconds (first watch), only 6.55 and 2.83 s are passed on the second and third watch. This is because the second strip (60 fps) contains 16.877 s x 60 fps = 1012.62 (captured) frames that were presented at a framerate of 30 fps, which takes about 33.754 s. The real time on the watch is about 6.55 s. With a capture frame rate of 60 fps, this represents the image of frame 393. Again, frame 393 will be presented at time 13.1 s with a presentation frame rate of 30 fps. This is approximately the time you can see on the first watch (allow some differences due to different starting times). If these were real animation movies, you would see slow-motion effect with strip 60 fps and even more with strip 120 fps.

   So, it's important to set the presentation frame rate equal to the capture frame rate of the strips. You can find the capture frame rate of a strip in the Properties > Source > FPS.

   .. note::
      The determination of the capture frame rate of video can sometimes be a rabbit hole. Most devices (in particular smart phones) do not mention that they capture in Variable Frame Rate mode. So, when setting the capture frame rate to 30 FPS, in reality, the frame rate can vary between 29 fps and 31 fps. This has no repercussion for the Start and End of the strip but it can cause (small) problems with the synchronization of video and audio.

      In the section Extra Tools, we have provided a solution to convert a video from variable rate to fixed and to change the FPS.

Time Remapping
   You can use this to speed up or slow down the playback of the whole project. For example, in figure 7, there are two indicators of the Current Frame. The Playhead is split into a blue line (the old frame number) and a blue box with the new frame number (which you actually see in the preview).
   
   Old
      The length in frames of the original animation.

   New
      The length in frames of the new animation.

   .. figure:: /images/video_editing_setup_project-settings-time-remapping.png
      :alt: Time Remapping (Old:1, New:2)
      

      Figure 7: Time Remapping (Old:1, New:2)

.. admonition:: Reference
   :class: refbox

   =============   ==============================================================
   **Name**:       *Stereoscopy*
   **Context**:    Video Sequence Editor > Properties
   **Location**:   Tabs > Output Properties
   =============   ==============================================================

Stereoscopy is a technique to create the illusion of three-dimensional depth from a pair of two-dimensional images. These images resemble the way our left and right eye would perceive the real image. In Blender, it is very easy to create stereoscopic images or movies; just enable the option in Output Properties > Stereoscopy > Stereo 3D. For more information; see `Stereoscopy <https://docs.blender.org/manual/en/dev/render/output/properties/stereoscopy/index.html>`_ in the Blender manual.

Editing a stereoscopic movie in the Blender VSE is a two-step process:
   
 * Enable the Stereoscopy option under output Properties > Stereoscopy > Stereo 3D. This will also add a new panel in the Source properties.
 * Select the stereoscopic strip and enable the *Use Multi-View* option in the Source panel of the movie strip. This option is only available after you have completed step 1. Choose the appropriate Views Format. This depends on the format of the source file. If the image pair is saved as two individual files; select *Individual*. If the image pair is saved as one file, with both images side-by-side, select Stereo 3D and set the Stereo Mode to Side-by-Side.

.. admonition:: Reference
   :class: refbox

   =============   ==============================================================
   **Name**:       *Output*
   **Context**:    Video Sequence Editor > Properties
   **Location**:   Tabs > Output Properties
   =============   ==============================================================


.. figure:: /images/video_editing_setup_project-settings-output.png
   :alt: Render Output properties
   :align: right
   :scale: 70%

   Figure 8: Render output properties
   
Figure 8 shows the expanded Output panel of the Output properties. Here you define the location and file format of your rendered project. In figure 8, we have selected the FFmpeg Video File Format. The other possibilities are shown in figure 9.

The Output panel is described in detail in the docs (see `section Output <https://docs.blender.org/manual/en/dev/render/output/properties/output.html>`_ with an overview of all `Video & Audio Formats <https://docs.blender.org/manual/en/dev/files/media/video_formats.html>`_ and `graphics <https://docs.blender.org/manual/en/dev/files/media/image_formats.html>`_ formats (see figure 9 for a list).
   
This text gives some additional info, specifically tailored at video editing. However, with all of the possible choices and the rather technical matter we will use a few practical questions to guide our inquiry.

Where to store your rendered project?
   In the previous section, we described a possible directory structure to hold all files that are related to your video project. In this structure, the rendered output could be stored in 3-2-Render. Because the Blend-file is stored at 3-1-Blend-file, the Output File Path should be ``//../3-2-render/``. The first // is the Blender-notation for the directory containing the current Blend-file. Depending on your choices about the File Format, you can add a file name or a directory name. The File Path ``//../3-2-render/myProject-v01.mp4`` will create a file *myProject-v01.mp4* in the specified directory (3-2-render). If you omit the extension (e.g. ``//../3-2-render/myProject-v01``) and enable *Saving File Extensions* , then a file *myProject-v010001-0020.mp4* is generated for a 20 frames project. If you render an image sequence, it is best to specify a subdirectory; place a / at the end as in ``//../3-2-render/myProject-v01/``. Rendering the project will then create the files *0001.png*, *0002.png*, *0003.png*, ... in the folder *3-2-render/myProject-v01*.

.. figure:: /images/video_editing_setup_project-settings-output-file-format.png
   :alt: File formats
   :align: right
   :scale: 70%

   Figure 9: File formats

Rendering a single video file or an image sequence?
   You can render the sequencer content as as series of images (BMP, Iris, PNG, ..., TIFF; see figure 9) or as a movie (a single video file, which is, of course, also an *embedded* series of images). Which one should you choose?
   
   The default is set to a PNG Image Sequence and the Blender docs and many tutorials favor this approach. It's easier to stop & restart the render process (for example, in case of a crash or when you need your computer for something else). You can choose a high-quality, lossless format (e.g. OpenEXR) that's ideal for post-processing such as color grading or VFX. You can use a render farm, ... These advantages, however, are much more obvious in a 3D-animation creation process (which is the main focus of Blender), where you have full-control over the image quality. It is less obvious in a video editing workflow, where the quality of the source material is usually fixed; e.g. your footage is already shot and creating a openEXR image sequence from H.264 footage will not increase the quality of it. If you saved your project as an image sequence, you also need to save the audio separately. And, in the end, you probably will need a single movie-file to hand over to your client. So, in a typical video editing workflow a single movie file format is much more common. 

Which codec should you use for a single movie-file?
   A distinction should be made between the concepts *container* and *codec*. For example, in figure 8, the container is MPEG-4 (with file extension mp4), the Video Codec is H.264 and the Audio Codec is AAC. A container is typically associated with the file format (extension). It "contains" the various components of the video: the stream of images, the sound, subtitles, metadata, ... A codec is software or hardware that compresses and decompresses digital video or audio.
   
   .. note::
      A 1080P video with 30 fps and 10 seconds duration has an uncompressed file size of 1080 x 1920 (dimension) x 3 (color channels) x 30 (fps) x 10 (duration) =  1.866.240.000 bytes or 1.73 GB. In most cases, this file is too big and should be compressed with for example, the H.264 codec. This codec can yield compression ratios from 1:50 to about 1:200 (200 bytes are compressed into 1 byte), reducing the above file size to about 36 MB - 9 MB. The following concepts are important to keep in mind:
      
      * intraframe compression: instead of coding every pixel of a frame, only the differences between pixels are encoded. For example, for a completely black frame you need only to encode the color and the info that it applies to the whole frame (or to certain blocks, ...). 
      * interframe compression: the frames in an image sequence are not all completely different. So, in theory, it's sufficient to encode the first frame (called a key frame or I-frame) and from then on only the differences.  This could work very well in a play-forward stream. In a typical video editing environment (with scrubbing, play backwards, jumping) however, this is a bad compression technique. To move one frame backwards, you have to process all the previous frames until the last keyframe. The term GOP (Group of Pictures) refers to the number of frames that are connected to one keyframe. The bigger the GOP size, the more compression but also the more processing needed to edit.
      * Lossy compression: the result of the compression is that some information is deleted from the file. Most of the time, this is not or hardly noticeable with the human eye. The JPEG image format is a lossy file format. WEBM/VP9 and Theora are lossy video codes. AAC is a lossy audio codec.
      * Lossless compression: the compressed file -although smaller- contains exact the same information as the uncompressed one. It is possible to reconstruct the original image from the lossless compressed file. The PNG image format is a lossless file format.  FFmpeg video codec #1 and HuffYUV are lossless video codecs. FLAC is a lossless audio codec.
       
      Some codecs have a lossy and lossless variant (for example DNxHD, H.264). Wikipedia maintains an extensive `list of lossy and lossless video and audio codecs <https://en.wikipedia.org/wiki/List_of_codecs#Lossless_compression>`_ .
   
   AVI JPEG
      In the first two choices of figure 9 (AVI JPEG and AVI Raw), the term AVI (Audio Video Interleaved) refers to the container: a file format developed by Microsoft in 1992. AVI JPEG uses the Motion JPEG (M-JPEG or MJPEG) codec in which each video frame is compressed separately as a JPEG image. So, this codec uses only intraframe compression and is thus very well suited for video editing purposes but also results in a bigger file size (because it's only intraframe compression). It is also a lossy compression because it uses the JPEG codec. Audio is not embedded in the container and should be exported separately.
   AVI Raw   
      AVI Raw doesn't use a codec as such and stores the raw images into the AVI-container. The file size is thus much greater but the quality and processing speed (besides the bigger frame size) are better. Audio is also not embedded. For a comparison, the original Spring Open movie (container: MPEG-4, video codec: AVC (Advanced Video Codec), Audio codec: AAC LC (Advanced Audio Codec Low Complexity) has a file size of 29.6 MB. The AVI Raw has a file size of 64.5 GB, the AVI JPEG has a file size of 1.87 GB; both without audio.
      
   .. note::
      Due to this huge file size and the absence of audio, both formats should probably not be used as delivery format but as fallback.
   
   FFmpeg video
      FFmpeg video is an umbrella term for several containers and codecs. It uses the ffmpeg libraries under the hood to create the video file. When selecting this option, several *presets* are available: ``DVD``, ``H264 in Matroska``, ``H264 in Matroska for scrubbing``, ``H264 in MP4``, ``Ogg Theora``, ``WebM (VP9+Opus)``, and ``Xvid``.  Selecting one of these presets will set the encoding, video and audio options below to a pre-defined value. We describe only the most popular *H264 in MP4* and the related concepts. These are also applicable to the other presets. 
      
      Encoding
         Container
            A container specifies how the data (audio, video, subtitles, ...) are stored in the video file, and how transporting and presenting this info can be organized. A container is not tied to a specific codec, although some combinations are not allowed. You can recognize the container through the file extension (MP4, MOV, ...), although this is not a waterproof method. For example, you can easily change the file extension from MP4 to MOV or AVI and still be able to view the video with most players. To detect the container signature (within the file), you need extra-software such as FFprobe or MediaInfo (see `Extratools </extra-tools>`_).
            
            The available container values are: ``MPEG-1``, ``MPEG-2``, ``MPEG-4``, ``AVI``, ``Quicktime``, ``DV``, ``Ogg``, ``Matroska``, ``Flash``, and ``WebM``.

            MPEG-4
               `MPEG-4 <https://en.wikipedia.org/wiki/MPEG-4>`_ is in fact a specification for compression of audio and visual digital data. The specification itself is divided into a number of parts (each part covers a certain aspect of the whole specification) including MPEG-4 part 2 (e.g. specification of the DivX video codec), MPEG-4 part 3 (e.g. AAC audio codec), MPEG-4 part 10 (H.264 video codec), MPEG-4 part 14 (MP4 media container) and others.
               
               The label, used in the Blender Encoding panel, thus refers to MPEG-4 part 14 and defines the media container (not the video or audio codec). The official extension of this container file is ``.mp4``, but the following ones are also supported by most players: ``.m4v`` (mp4-alike container developed by Apple, sometimes copy-protected), ``.m4b`` (Audio book file, often used by iTunes), ``m4a`` (only audio encoded with the AAC codec), ``.m4p`` (only audio but copy-protected, used by iTunes).  The container is based on the QuickTime or MOV format (developed by Apple); which is also one of the available container formats (see above).

               The MPEG-4 container is widely used and supported by most video players and platforms (Linux, Apple, Windows). The MP4 file can contain metadata, such as subtitles, still images and pdf. It can have a high (lossy) comprression rate, producing smaller file sizes. Because, it is a very versatile file format, editing can require more computer resources than other formats. 

            Autosplit   
               If the output file is bigger than 2 GB, you can *Autosplit* the output in chunks of max. 2 GB. Each chunk  can be played separately.

      Video
         Video Codec
            The name CODEC stands for Compressor/Decompressor (sometimes also referred to as coding/decoding). It is the software that compresses the file (see above). Available options are: ``No Video``, ``DNxHD``, ``DV``, ``FFmpeg video codec #1``, ``Flash Video``, ``H.264``, ``HuffYUV``, ``MPEG-1``, ``MPEG-2``, ``MPEG-4 (divx)``, ``PNG``, ``QT rle/QT Animation``, ``Theora``, and  ``WEBM/VP9``.

            The goal of (lossy) video encoding is to reduce the file size of the original input file, while retaining as much quality as possible. So, there is a tradeoff between size and quality.

         Output quality
            The image quality of a video is dependent of the bitrate; i.e. the number of bits used per unit time. Setting a high bitrate will result in a higher quality because you have more bits per unit time to dislay the image.

            With FFmpeg, you can use a constant or a variable bitrate. With a constant bitrate the number of bits per unit of time is always the same, no matter how complex the image stream is. A variable bitrate can adapt to the complexity of the stream and use a lower bitrate with for example a motionless video.

            Variable bitrate
               You need to give some indication about the desired output; otherwise the codec could always settle for the lowest bitrate, which is of course also the lowest quality.

               Blender has opted to use `verbal labels <https://blender.stackexchange.com/questions/93048/what-numerical-crf-values-do-the-assorted-output-qualities-correspond-to-in-the>`_; which are a translation of FFmpeg's `Constant Rate Factor <http://trac.ffmpeg.org/wiki/Encode/H.264>`_ (CRF): a value between 0 and 51, where lower values would result in better quality (more bits per frame), at the expense of higher file sizes. Higher values mean more compression, but at some point you will notice the quality degradation. A change of ± 6 should result in about half/double the file size.

               .. figure:: /images/video_editing_setup_project-settings-output-quality.png
                  :alt: Output Quality
 
                  Figure 10: Output Quality and FFmpeg's Constant Rate Factor (CRF) values
            
            Constant Bitrate
               In FFmpeg, there is no native or true CBR mode, but Blender "simulates" a constant bit rate setting by tuning the parameters of a one-pass average bitrate encode. You need to set the following, additional input fields. However, Bitrate, Minimum, and Maximum can all be set to the same value. 
               
               Bitrate
                  Bitrate is the amount of data encoded for a unit of time. For streaming, it is usually expressed in megabits per second (Mbps) for video, and in kilobits per second (kbps) for audio. The default is set to 6000 bps. As a comparison, the recommended video bitrate for YouTube uploads is set to 8 Mbps for 1080p and 5 Mbps for 720p.
               Minimum
                  Although the Constant Bitrate option is selected, the encoder will fluctuate around this number. You can set a minimum.
               Maximum
                  However, the maximum is probably more important. If you suspect that your viewer has limited bandwidth, you can specify this maximum. The encoder will never encode in a higher bitrate.
               Buffer
                  This is the "rate control buffer", so it will enforce your requested "average" (the value you set with Bitrate) over the buffer window. It is assumed that the receiver / player will buffer that much data, meaning that a fluctuation within that range is acceptable. The default is set to 1792 bits.
               Mux Rate
                  Multiplexing is the process of combining separate video and audio streams into a single file, similar to packing a video file and .mp3 audio file in a zip-file. The value of Mux Rate is the maximum bit rate of the multiplexed stream. The default is set to 10080000.
               Mux Packet size
                  Default: 2048. Reduces data fragmentation or muxer overhead depending on the source. The default is set to 2048.
         Encoding speed
            Presets to change between a fast encode (bigger file size) and more compression (smaller file size). The available options: Slowest, Good, Realtime
         Keyframe Interval
            The number of pictures per Group of Pictures. The default value is 18. Set to 0 for “intraframe only” compressing, which disables inter-frame video. A higher number generally leads to a smaller file but needs a higher-powered device to replay it. 
         Max B-frames
            B-frames are bi-directional frames. They use both previous and forward frames for data reference to get the highest amount of compression. The value is the maximum number of B‑frames between non-B-frames.
      
      Audio
         Only certain audio codecs will be able to fit in your target output file; see `Guidelines for high quality lossy audio encoding <https://trac.ffmpeg.org/wiki/Encode/HighQualityAudio>`_ for an overview table.

         According to the FFmpeg docs, the quality of the available audio encoders could be ranked as folllows:
         Opus > Vorbis >= AAC > MP3 >= AC3 > aac > libtwolame > vorbis > mp2 > wmav2/wmav1
         
         Audio Codec
            Available options: No Audio, AAC, AC3, FLAC, MP2, MP3, Opus, PCM, Vorbis.
         Audio channels
            Available options: Mono, Stereo, 4 channels, 5.1 Surround, 7.1 Surround
         Sample Rate
            Slider: default at 480000
         Bit Rate
            Slider: default at 384
         Volume
            Slider: default at 1



Some useful links:

* Discrete Cosine Transformation: https://www.youtube.com/watch?v=Q2aEzeMDHMA&t=33s 
* JPEG compression: https://www.youtube.com/watch?v=Ba89cI9eIg8
* Video compression: https://www.youtube.com/watch?v=QoZ8pccsYo4 
* Rate Control mode: https://slhck.info/video/2017/03/01/rate-control.html
      