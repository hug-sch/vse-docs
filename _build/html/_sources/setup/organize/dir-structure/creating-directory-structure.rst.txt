Creating a directory structure
==============================

A video project is most likely a combination of several different assets. You can separate them into three broad categories.

* Video files: video clips (or movies in Blender-talk), photos, graphic files (charts, logos, ...) and Visual Effects (VFX) such as masks, lens flares, animation.
* Audio files: recorded dialog, voice-over, music, and Sound Effects (SFX) such as environmental sounds, swooshes, ...
* Project files: the blend files and backups, (partial) render results, documentation such as scripts and story boards. 

Together they can form rapidly an intangible heap of files. It's good practice to collect all those assets in one project directory with appropriate subdirectories. Why? It will lower the probability that you accidently delete a file (which will result in a 'file not found' error) or that you forget to include a necessary file when transferring the project (file is missing). And most of all, with an appropriate directory structure, it will help you to keep a clear overview on your assets.

.. seealso::

    Blender can incorporate some files within the blend-file (see `Packed Data <https://docs.blender.org/manual/en/latest/files/blend/packed_data.html>`_). However, for the VSE, this is not good practice because video files can have very huge file sizes and movie-files cannot be packed anyway. It's better to assure that your project directory contains all neccessary files.

It's also good practice to use some kind of naming convention and add metadata. Figure 1 shows a possible example, based on our categorization of the assets above. The directories are numbered so that they mimic a normal workflow.

.. figure:: /images/setup/vse_setup_organize_dir-structure_example.svg
   :scale: 50 %
   :alt: Organizing your project

   Figure 1: Organizing your project.

Blender does not have a full-blown asset manager yet, but with the File Browser you already can go a long way. For example, with the ``Display Settings`` you could recursively browse up to three levels of directories. Because the 'demo-project'-directory is selected in figure 1, "1_video" (first level), "1-1-movie" (second level) and "Spring - Blender Open Movie.mp4" (third level) are displayed. With the ``Filter Settings`` you could prevent the display of certain types of files.
