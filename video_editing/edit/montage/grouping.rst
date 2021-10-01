Grouping
--------

.. _bpy.types.MetaSequence:

Selected strips can easily be grouped together into one so-called meta strip with :kbd:`Ctrl-G`. A Meta Strip is a strip that can contain multiple strips, but is treated as if it was one strip. The max number of strips that can be grouped is 128, due to the max number of available channels in the sequencer. The duration of the Meta strip will span from the earliest Start time until the latest End time of any strip.

.. figure:: /images/video-editing_edit_montage_grouping_meta_example.png
   :align: center

   Figure 1: Example of Meta strip.

The Meta strip has a very specific appearance because the channels of the grouped strips are represented by small horizontal bars within the Meta strip. In figure 1, the grouped strips occupy 4 channels, so the Meta strip contains 4 (small) horizontal bars. The grouped strips themselves are represented by their own color in the Meta strip. For example, the two purple areas at the top come from the text strips at channel 6. The color of the Meta strip itself is blueish purple, which covers the areas where no grouped strip is available. If there is only one strip to group, then the color of the Meta strip is very similar to the grouped stripp (most of the time a little darker) aand it's hard to reognize a Meta strip as such.

The Meta strip replaces the selected strips in the sequencer timeline and is placed at the channel of the active strip. This could result in somewhat unexpected positions when box selecting the group (the active strip isn't changed by box selecting).

.. note::
   Figure 1 is a bit misleading because a Meta strip and the grouped strips could never be visible at the same time in the timeline. The Meta strip *replaces* the grouped strips.

   Figure 1 is made by creating a Meta strip, duplicating it and un-meta-ing the duplicate. 

The Meta strip is in fact a completely new strip with its own (independent) properties such as position X & Y, scale, rotation, .... It's like if the grouped strips are rendered out and the render result is imported back into the timeline as a new (meta) strip. For example, increasing the duration of the grouped strips *after* creating the Meta strip will *not* increase the duration of the Meta strip. You have to do that manually by dragging the strip handles.

Meta strips can be nested. For example, you can copy one Meta strip and paste it into another.

Make Meta Strip :kbd:`Ctrl-G`
   To create a Meta strip, select all the strips you want to group, and bd:`Ctrl-G` to group them. The Meta strips will span from the beginning of the first strip to the end of the last one, and condenses all channels into a single strip. The Meta strip is placed at the channel of the active strip.
UnMeta Strip :kbd:`Ctrl-Alt-G`
   Separating (ungrouping) the Meta strip restores the strips to their relative positions and channels. This can be used if you choose to delete a Meta strip and want to keep the strips inside.

   Be aware that effects added to the Meta strip will be removed.

Edit a Meta strip :kbd:`Tab`
   You can edit the content inside a Meta strip by pressing :kbd:`Tab`. This will expand the strip to the original group and hide any other strips. To exit the Meta strip press :kbd:`Tab` again. Meta strips can also be nested, which make editing them a little confusing. To exit out one level of Meta Strip make sure you do not have a Meta strip selected when you press :kbd:`Tab` (select nothing or anoter regulare strip).

.. Warning::
   Adding effects e.g. Glow to a Meta strip is possible but the effects will be removed if you unMeta the strip.

   The default blend mode for a Meta strip is Replace (all strips below will not be visible). There are many cases where this alters the results of the animation so be sure to check the results and adjust the blend mode if necessary.

   Because of the above, adding a new strip to an existing meta strip should not be done by unMeta, followed by adding the new strip and recreate the Meta strip again. Better is to copy the new strip (on the clipboard), go into the Meta strip (Tab), paste the new strip and go out of the the Meta strip.

The Meta strip is primarily an organization tool but has numerous other use cases.
* If you are using a lot of strips with complicated arrangement, you can group them together using Meta strips. It allows you to reduce the vertical space used in the Sequencer.
* You can extend the limit of 128 channels with Meta Strips. The grouped strips will occupy only one channel.
* A Meta strip is a handy way to keep audio and video together in a synced way. Unfortunately, you will loose the advantage of thumnails.
* You can use it for adding speed effects in a simpler manner. See `Blender Frenzy <https://www.youtube.com/watch?v=jnrOzrPDAA0>`_ for a detailled tutorial about the procedure.
* One convenient use for Meta strips is when you want to apply the same effect to multiple strips. It is much more convenient to apply a single set of effects to one Meta strip than applying it to each individual strip. It is also possible to do the similar task described above with an :doc:`Adjustment Layer </video_editing/sequencer/strips/adjustment>` effect strip.