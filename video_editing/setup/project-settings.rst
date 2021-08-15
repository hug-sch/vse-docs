Project settings
================

The Project Settings for your video project are grouped in the `Output Properties <https://docs.blender.org/manual/en/dev/render/output/index.html>`_ tab of the `Properties Editor <https://docs.blender.org/manual/en/dev/editors/properties_editor.html>`_. This editor is located at the top right area in the default Video Editing workspace and is shared with the other modules, e.g. 3D modeling. The Properties has several categories, which can be chosen via tabs (the icons column to its left). Each tab regroups properties and settings of a data type. For the VSE, only the Output properties are commonly used. This tab is selected by default on opening the Video Editor Workspace.

.. admonition:: Reference
   :class: refbox

   =============   ==============================================================
   **Name**:       Dimensions
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
      

      Figure 5: Mixing of different frame rates in one project

   Figure 5 contains 3 strips that were recorded at different frame rates. Their capture frame rate was respectively 30 fps, 60 fps and 120 fps. Each recording took about 15 seconds. The strip with fps = 30 was first added. This has set the presentation frame rate of the entire project to 30 fps. Later on, strips of 60 fps and 120 fps were added. This does not change the project presentation frame rate, but, of course, the capture frame rate of the strips remains unchanged. All the audio strips have a duration of about 15 seconds because the audio is independent of the presentation frame rate. The strip with capture fps = 30 has also a duration of about 15 seconds. This is because the capture and presentation frame rate is equal. The strips with capture frame rate of 60 and 120 fps are much longer. On the watch itself, you can see that after about 15 seconds (first watch), only 6.55 and 2.83 s are passed on the second and third watch. This is because the second strip (60 fps) contains 16.877 s x 60 fps = 1012.62 (captured) frames that were presented at a framerate of 30 fps, which takes about 33.754 s. The real time on the watch is about 6.55 s. With a capture frame rate of 60 fps, this represents the image of frame 393. Again, frame 393 will be presented at time 13.1 s with a presentation frame rate of 30 fps. This is approximately the time you can see on the first watch (allow some differences due to different starting times). If these were real animation movies, you would see slow-motion effect with strip 60 fps and even more with strip 120 fps.

   So, it's important to set the presentation frame rate equal to the capture frame rate of the strips. You can find the capture frame rate of a strip in the Properties > Source > FPS.

   .. note::
      The determination of the capture frame rate of video can sometimes be a rabbit hole. Most devices (in particular smart phones) do not mention that they capture in Variable Frame Rate mode. So, when setting the capture frame rate to 30 FPS, in reality, the frame rate can vary between 29 fps and 31 fps. This has no repercussion for the Start and End of the strip but it can cause (small) problems with the synchronization of video and audio.

      In the section Extra Tools, we have provided a solution to convert a video from variable rate to fixed and to change the FPS.

Time Remapping
   You can use this to speed up or slow down the playback of the whole project. For example, in figure 6, there are two indicators of the Current Frame. The Playhead is split into a blue line (the old frame number) and a blue box with the new frame number (which you actually see in the preview).
   
   Old
      The length in frames of the original animation.

   New
      The length in frames of the new animation.

.. figure:: /images/video_editing_setup_project-settings-time-remapping.png
      :alt: Time Remapping (Old:1, New:2)
      

      Figure 6: Time Remapping (Old:1, New:2)




