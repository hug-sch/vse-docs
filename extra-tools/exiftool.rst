ExifTool
********

All image, video and audio files contain metadata, e.g. the CreationDate of the image, the Camera type, GPS coordinates, ... With ExifTool, you can read and sometimes also update (write) these metadata.

Change the creation date of a video
===================================

Sometimes the date and time are not set correctly in a camera (for example, when switching time zones). When shooting a video with this camera, the metadata will not represent the actual date the video was shot.  For example, the video test.mov (see below) was shot on 2021-08-05 with a smartphone, but due to a previous factory reset the date was incorrectly set as 2019-11-01 within the phone. 

This particular smartphone recorded several date and time fields within the test.mov file. The following command will display all the date & time info that is available within test.mov.

``exiftool -time:all -groupNames -short test.mov``

- *time:all*: shortcut to display all metadata fields that contain date/time info
- *groupNames*: print the group name in front of each tag
- *short*: tag names are printed instead of descriptions.

.. code-block:: none

   [File]          FileModifyDate                  : 2019:11:01 22:22:22+01:00
   [File]          FileAccessDate                  : 2021:08:07 16:29:11+02:00
   [File]          FileCreateDate                  : 2021:08:07 16:29:05+02:00
   [QuickTime]     CreateDate                      : 2019:11:01 21:22:22
   [QuickTime]     ModifyDate                      : 2019:11:01 21:22:30
   [QuickTime]     TrackCreateDate                 : 2019:11:01 21:22:22
   [QuickTime]     TrackModifyDate                 : 2019:11:01 21:22:30
   [QuickTime]     MediaCreateDate                 : 2019:11:01 21:22:22
   [QuickTime]     MediaModifyDate                 : 2019:11:01 21:22:30
   [QuickTime]     CreationDate                    : 2019:11:01 22:22:22+01:00

There are two group names [File] and [QuickTime]. The first group of tags is usually managed by the operating system of the device. For example, you can see that the file test.mov is apparently copied from the smartphone to a desktop on 2021-08-07; while the other dates (due to the wrong date/time settings in the smartphone) are set to 2019-11-01. The [QuickTime] tags are set by the smartphone (in this case an Apple iPhone).

To update a time-field, for example the [QuickTime] CreateDate, you can use the Shift command.

``exiftool "-QuickTime:CreateDate += 0000:21:04 00:00:00"  testing.mov``

The metadata field *QuickTime:CreateDate* is incremented with 0 years, 21 months and 4 days, resetting 2019-11-01 to 2021-08-05. The command will make a copy of the original file with the name testing.mov_original and update the field in testing.mov.

To update all the [QuickTime] time-fields, you can use the following command:

``exiftool "-QuickTime:time:all += 0000:21:04 00:00:00"  testing.mov``

This will result in the following update of the file testing.mov. Because the previous command runned at 2021:08:08 16:01:44+02:00, the [File] tags are updated consequently by the operating system.

.. code-block:: none

   [File]          FileModifyDate                  : 2021:08:08 16:01:44+02:00
   [File]          FileAccessDate                  : 2021:08:08 16:01:44+02:00
   [File]          FileCreateDate                  : 2021:08:07 16:29:05+02:00
   [QuickTime]     CreateDate                      : 2021:08:05 21:22:22
   [QuickTime]     ModifyDate                      : 2021:08:05 21:22:30
   [QuickTime]     TrackCreateDate                 : 2021:08:05 21:22:22
   [QuickTime]     TrackModifyDate                 : 2021:08:05 21:22:30
   [QuickTime]     MediaCreateDate                 : 2021:08:05 21:22:22
   [QuickTime]     MediaModifyDate                 : 2021:08:05 21:22:30
   [QuickTime]     CreationDate                    : 2021:08:05 22:22:22+01:00

To set the all [QuickTime] date & time metadata to as specific time, you can use the following command. As explained above, the [File] tags will not be updated to this specific time.

``exiftool -wm w -QuickTime:time:all="2022:08:05 23:12:12" testing.mov``