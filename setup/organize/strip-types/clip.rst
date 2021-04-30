Clip strip
==========

A clip strip is created from the output of the Movie Clip Editor. There is nothing in the Clip menu unless you've opened media (video or images) in the Movie Clip Editor. At all other times it's just a blank menu. The Movie Clip Editor is used to create advanced edits such as motion tracking and advanced masking. See special workflows for an example.

The property panels of Compositing, Transform, Crop, ... are the same as in the Movie Clip Editor. There isn't any Source panel because the Clip strip is created from an in-memory data block of the Movie Clip Editor. There can be multiple data blocks and they are stored within the Blend-file upon saving.

**Video**

.. figure:: img/panel-video-strip-clip.png
   :scale: 50%
   :alt: Video Property of Clip Strip
   :align: Right

   Figure 12: Video Property of Clip Strip


Two extra properties are added underneath the Video panel.

``Tracker: Stabilize 2D clip`` The purpose of Tracking in the Movie Clip Editor is mostly to stabilize the video. With this checkbox you can use the stabilized version of the clip.

``Distortion: Undistort clip`` Stabilizing of a video is done by moving and rotating the video. With this option you can remove the distortion of the clip which is the result of stabilizing it.
