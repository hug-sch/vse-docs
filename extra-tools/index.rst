###########
Extra-tools
###########

Blender's VSE is a great video editor but of course it's not a Swiss knife. In addition, the main focus of Blender is not on video editing but on 3D modeling. Some areas such as sound are less important in that perspective. So,  some functionality is not available or up-to-date. You'll need some extra-tools for this.

In this section, we describe some extra tools; mainly open source that you might need when editing.

**Python**

Blender uses the Python programming language for its scripting API (Application Programming Interface). Many internal data structures and operators can be accessed through a Python script. The `official docs <https://docs.blender.org/api/current/>`_ are well-written. In this text we provide some :doc:`usefull scripts <python-useful-scripts>` and an in-depth description of  the :doc:`Scripting Workspace <python-scripting-workspace>`.

FFmpeg

FFmpeg is a open-source framework to work with video and audio. Blender's VSE  uses it heavily through its libraries libavcodec, libavutil, ... 

As an end-use, you probably will use the command line tool `ffmpeg <https://ffmpeg.org/ffmpeg.html>`_, the `mediaplayer ffplay <https://ffmpeg.org/ffplay.html>`_, or the multimedia ` stream analyzer ffprobe <https://ffmpeg.org/ffprobe.html>`_.

We provide some :doc:`useful scripts <ffmpeg>` that you probably will need in your job as a video editor.

ExifTool


ExifTool is a platform-independent library and a `command-line application <https://exiftool.org/>`_  command-line application for reading, writing and editing meta information in a wide variety of files (including most graphic file formats).

:doc:`Some usefull scripts <exiftool>` are provided.

.. toctree::
   

   Python <python-useful-scripts.rst>
   ffmpeg <ffmpeg>
   Script Editor <python-scripting-workspace.rst>
   exiftool
   annotating-screenshot


