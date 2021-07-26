Proxies & cache
===============

.. _proxies:

Proxies are low-quality copies of high-quality raw footage. They are used as a substitute to ease the playback of high-quality source videos. Creating proxies can be done by either decreasing the resolution and/or decompressing the source files. They are transcoded in such a way that is optimal for real-time editing.  Nowadays, a 4K video file (3840 × 2160) is no exception anymore. With 30 fps, this can quickly become a burden to your computer's performance.


.. note::
   You can try it yourself by creating a 4K test movie (see :doc:`test files </setup/organize/dir-structure/creating-test-files>`) and adding it to the sequencer. Without proxies you will notice that scrubbing through the strip will stutter. Adding an effect (e.g. Gaussian Blur) will aggravate the problem.

Using a 720p (1280×720) or a more optimized format will reduce the load on your computer. Proxies are only used to speed up the editing. For rendering out the final project, the original, high quality source files are used.

A very instructive video tutorial (for version 2.92) is made by `Blender Frenzy <https://www.youtube.com/watch?v=kfTJ2Wsmc9c>`_.

The use of proxies is much simplified in Blender 2.93 and an average user shouldn't be worried about it any longer. Of course, understanding what happens under the hood can't harm! The following default settings take care of this automatic creation of the proxy files and make sure that everything will work right out of the box.

* ``Proxy Setup`` : default set to ``Automatic`` (see figure 1-a)
* ``Proxy Render Size``: default set at ``100%`` (see figure 1-b)
* ``Use Proxies``: default set to ``True`` (see figure 1-b)
* ``Proxy Settings: Storage``: default set to ``Per Strip`` (see figure 1-g)

.. figure:: /images/vse_setup_environment_proxies.svg
   :alt: Proxies

   Figure 1: Overview of the proxy building process.


1. First and foremost, by default, proxies are now built automatically in the background. To enable or disable the Automatic Proxy Setup, go to the Edit > Preferences menu and select the System tab (see figure 1-a). You can choose between Manual or Automatic. If Automatic is chosen, several things occur after adding a movie or image sequence strip to the sequencer or after changing the View Settings of a strip (see figure 1-b).

   1. A small progress indicator with a percentage shows up in the status bar (see figure 1-c). Depending on your system and the resolution of the clip, this can take a while. You can continue working however, because the building process occurs in the background.
   2. A directory BL_proxy is created as a subdirectory of the source folder of the strip (see figure 1-d). Within this directory a subdirectory is created with the name of the active strip; e.g. testfile_4K_10s_30fps.mp4 (figure 1-e). And within this folder, the proxy file is created; e.g. proxy_100.avi (figure 1-f), together with some other supplemental files. Note that the proxy files are quite larger in size (even for 25%) but also faster because they use a more optimized compression format that the original H.264 (MP4) codec.
   3. Scrubbing through the strip should be much smoother now.

.. todo::
   At the moment, proxies can only be generated for movie strips, not image sequences! In general, proxies are only used for video files, not audio.

2. The Proxy Render Size is set by default to 100%. You can change it in the View Settings (see figure 1-b) of the Preview window. If 100% is selected, the resolution of the Preview window is set to 100% of the strip resolution AND the original video clip (e.g. testfile_4K_10s_30fps.mp4) will be replaced by the proxy (e.g. proxy_100.avi). If you select afterwards another Proxy Render Size; e.g. 25%, a supplemental proxy will be created (proxy_25.avi) and there will be two proxy files (see figure 1-f) from which the second (25%) will be used for previewing.

   There are 6 Proxy Renders Sizes: No display, Scene size, 25%, 50%, 75%, 100%. Remember that these View settings are intended to set the resolution of the Preview window. For example, if the strip has a resolution of 1080p (1920 x 1080), then setting the Proxy Render Size to 25% means that the Preview window will have a resolution of 480 x  270. Displaying the strip in this low-resolution window will speed up the rendering a little. The setting No display, will set the resolution at zero (=no display!). The setting Scene size will set the resolution the same as the project (see figure 1-h), which can be different from the resolution of the strip.

   .. note::
      You can easily see the effect of the Proxy Render Size in the following example. Create a new Video Editing project. The project resolution is probably 1080p (1920 x 1080). Add a text strip with size 30. Set the zoom to View > Fractional Zoom 1:1. Change the Proxy Render Size and watch the degradation of the image quality.

   .. figure:: /images/vse_setup_environment_proxies-render-size.svg
      :alt: Example of proxy Render Sizes

      Figure 2: Effect on quality of Proxy Render Sizes 100%, 50% and 25%.

   Reducing the display resolution will certainly reduce the time necessary to draw the display. On the other hand, the source file has a different resolution; so some additional scaling must be done. Perhaps, it confuses you that there exists a 100% proxy size. What's the use of this? If the display resolution is not changed, how will this help performance? Well, then comes the following default setting into action.

3. The checkbox ``Use proxies`` is enabled by default (see figure 1-b). It's a global setting, meaning that all strips in the project will use proxies. You can reverse this setting per strip (see later). So, if you select the Proxy Render Size of 25% in the View Settings, then the file proxy_25.avi is set as the strip source.

A proxy file can differ in two ways from the source file.

* The resolution; e.g. 25% of the original resolution.
* The encoding; e.g. only intra-frame compression instead of intra- and inter-frame compression.

Some raw footage is heavily compressed to keep the storage requirements (e.g. smartphone) within reasonable limits. One compression technique that is used by the popular H2.64 codec is inter-frame compression. On an average video, content does not change abruptly from frame to frame. So, in stead of storing each frame fully, we can store only the changes from the previous frame. So, there are a few frames which contain the full image (i-frames) in a file, but most frames are delta-frames. This results in a huge reduction in storage but ... There is also a downside. In a typical editing task, you scrub and jump between frames. If most frames are delta-frames however, the software has to regenerate each time that frame by searching for the corresponding i-frame and adding all the subsequent changes. That takes time.

A proxy is a transcoded file in which no interframe compression is applied. So, scrubbing will be smoother; each frame has all information it needs to display and does not depend on others. So even if the resolution is the same as the source file (100%), the proxy will still be faster than the original. However, proxy files are on average much larger than the (inter-frame compressed) source files. In figure 1-d you can see that the original 4K source file is 525 Kib and the proxy_100.avi/proxy_25.avi are respectively 9.2 and 1.5 MiB. So, even the 25% proxy is approximately 3x larger than the original.

Of course, much depends on the format of the source files. If your source files have already an optimized codec for editing (e.g. Apple’s ProRes, Avid’s DNxHD/HR and GoPro’s Cineform), creating proxy files isn't much of help.

.. todo::
   Better explanation of inner working of proxies; link to external website/tutorial?

4. The above settings can be tweaked for individual strips with the Proxy Settings panel in the sidebar. To show the panel, select the strip in the Sequencer and press N or select the menu View > Sidebar.

   A. You have to decide if the proxies should be generated Per Strip or globally for the project. If you choose Per Strip, then the Proxy folder (BL_proxy) will be created at the location of the selected strip.  You can override this directory location and name in the panel below with the Custom Proxy Directory checkbox. Or, you can choose Project. The proxy folder BL_proxy will then be created in the directory from the field below. This setting influences also the Automatic setup. The chosen directory will be used for the automatic creation of the BL_proxy directory.

   .. note::
      In general, it is easier to manage, if you have a separate directory for all of your proxies of the same project. It's also advisable to have that folder on a different disk than the Blender program or source files (to minimize the disk access time).

   B. If you have opted for a Manual Proxy setup, you have to build the proxy files yourself. Select the strips (it can be more than one!) for which you want to create proxies. With the button ``Set Selected Strip Proxies`` you can enable multiple proxy render sizes (25%, 50%, 75%, 100%). With the Overwrite checkbox, you give permission to overwrite existing proxy-files. You'll use this button to enable these settings for *multiple* selected clips.

   C. The result of pushing the ``Set Selected Strip Proxies`` is that the checkbox next to ``Strip Proxy & Timecode`` is enabled and that the proxy sizes are filled in for all the selected strips. Eventually, you can deviate for the storage directory and filename of an individual strip here.

   D. The proxy files however are not yet created. To generate them, you have to click the ``Rebuild Proxy and Timecode Indices``. By this time, you probably will appreciate the ease of the Automatic mode. The Build indicator (see figure 1-c) appears and the folders and files are created in the background. Unchecking the box ``Strip Proxy & Timecode`` will remove the advantage of smooth previewing but will not delete the proxy file on the hard disk.
   E. The Build JPEG Quality setting 0-100 corresponds to "Lowest Quality" to "Perceptually Lossless" in Blender's H.264 encoding presets.

   .. todo::
      Better explanation of Quality & Time Code; see `Timecode index <https://docs.blender.org/manual/en/dev/video_editing/sequencer/sidebar/proxy.html>`_ .

.. _proxies_cache:

Cache
-----
In order for this property to be visible, enable :ref:`Developer Extras <prefs-interface-dev-extras>`.

The biggest impact on playback performance is to allow the Video Sequencer to cache the playback. Because, it is so important, the cache system is designed to work silently in the background without much user interference. In fact, the Cache tab in the sidebar (see figure 3) will only be visible if the Developer Extras are switched on in the Edit > Preferences menu (Interface tab). In every case, the cache system will run silently for your benefit in the background.

There are two panels:

* Cache Settings: these settings apply to **all** strips in the Project
* Strip Cache: if enabled, these settings apply only to the **selected strip**; thus overriding the global settings.

With the menu View > Show you can visualize the cache. They appear as small colored bars beneath the strips.

.. figure:: /images/vse_setup_environment_cache.svg
   :alt: Cache settings & bars

   Figure 3: Cache settings and cache bars.

.. todo::
   What do the following options really mean? Any supplemental info?
   From the manual (https://docs.blender.org/manual/en/dev/video_editing/sequencer/sidebar/cache.html):

* Raw: Cache raw images read from drive, for faster tweaking of strip parameters at the cost of memory usage.
* Pre-processed: Cache preprocessed images, for faster tweaking of effects at the cost of memory usage.
* Composite: Cache intermediate composited images, for faster tweaking of stacked strips at the cost of memory usage.
* Final: Cache final image for each frame.

There are two levels of cache, the first is a RAM cache, this is enabled by default but can be increased based on the amount of RAM available. The next level of cache is a disk cache which stores cached strips on disk. A disk cache can generally cache more than a RAM cache, but it can be slower. Both of these cache options can be configured in the Edit > Preferences menu under the System tab.(see figure 1-a).


.. todo::
   Summarizing difference between cache, e.g. disk cache and proxies

* Proxies only work with movie strips; cache supports all strip types.
* Proxies store result on hard disk; cache store result in RAM (except diskcache)
* Proxies cache only the RAW datafile; cache can store intermediate results
* Proxies are persistent, cache becomes eventually invalidated


.. toctree::
   :maxdepth: 2

   proxies_technical
