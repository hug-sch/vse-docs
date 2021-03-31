Extend your environment
=======================

Blender's Video Sequencer is a fairly good editor but, nevertheless, it lacks some (vital) components. For example, sound editing is for the most part neglected. Sound level monitoring, normalizing sound level, can easily be done in an open-source package as Audacity. So, there is an add-on to export your sound data to Audacity and importing it back.

`Tin2Tin <https://blenderartists.org/t/video-sequence-editor-news-add-ons/1188770>`_has compiled a webpage on Blenderartists.org with more than 100 links to add-ons. They fit into categories such as toolboxes, (multi-threaded) export and import, effects, strip editing, generate, audio, scene strips, markers, organization, Multicam, user interface, shortcut keys, and templates.

The working environment can also be heavily extended/improved by the use of proxies. A proxy is a low-resolution video file that can take the place of a larger-resolution video file in your timeline. This way you can render faster. 

Adding functionality with add-ons
---------------------------------
Here about an image of the add-ons panel of the preferences.

For installing add-ons: see manual ...

Built-in add-ons
,,,,,,,,,,,,,,,,

There is one built-in add-on that is not activated by default: Power Sequencer.

Here about a screenshot of the UI eg the menu.

External add-ons
,,,,,,,,,,,,,,,,

* Reference to the overview on tintwotin.
* How installing (zip-file or py-file); refering to the manual? 

Tweaking performance with proxies & cache
-----------------------------------------
Playback performance can be improved through several ways. The biggest impact on performance is to allow the Video Sequencer to cache the playback. There are two levels of cache, the first is a RAM cache, this is enabled by default but can be increased based on the amount of RAM available. The next level of cache is a disk cache which stores cached strips on disk. A disk cache can generally cache more than a RAM cache, but it can be slower. Both of these cache options can be configured in the Preferences.

Another way to improve performance is by using Strip Proxies These are used to cache images or movies in a file that is easier to playback by reducing the image quality by either decreasing the resolution and/or compressing the image. 

Proxies
,,,,,,,

* Will probably heavily changed in upcoming version?
* Settings: location, %

cache
,,,,,
