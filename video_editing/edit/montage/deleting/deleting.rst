Deleting & Muting & Locking
---------------------------

.. figure:: img/delete.svg
   :alt: Strip menu
   :scale: 50%
   :align: right

   Figure 2: Strip menu
Deleting one or multiple selected strips is done by pressing the :kbd:`X` key or the :kbd:`Delete` key or with the menu Strip > Delete or the context menu with :kbd:`RMB + Click` (see figure 1).

This Delete operation can of course be undone with the Undo command or :kbd:`Ctrl Z` key. Deleting a strip that has an associated effect (e.g. Glow or Gaussian Blur) will also delete the effect strip.

The *preferred* key for deletion is X and not Delete because the X key can be accessed easily with the left hand on a standard (Qwerty) keyboard. That way, you don't have to release the mouse in your right hand (of course, if you are right-handed).

|

.. figure:: img/mute-lock.svg
   :alt: Mute-lock menu
   :align: right

   Figure 2: Mute & Lock menu

The Mute command will make a strip invisible in the preview. The command was previously called *Hide*, which you can deduce from the shortcut key (H). The strip is still visible in the time line (a little bit greyed out; see figure 2) but it will not contribute to the image in the preview. The effect of the Mute command is the same as clicking on the Mute icon in the Strip properties (see figure 2). If you want to apply the Mute on all selected strips, you have to press the :kbd:`Alt` key while clicking the icon. You can mute the selected strips or the inverse: the unselected strips.

- Mute/Unmute Strips (kbd:`H`, :kbd:`Alt-H`): mute or unmute the selected strips. The strips will be (in) visible in the preview.
- Mute/Unmute Deselected Strips (:kbd:`Shift-H`, :kbd:`Ctrl-Alt-H`): mute or unmute all strips but the selected.

The Lock command prevents the strip from being moved in time or that the duration could be changed. The effect of the Lock command is the same as clicking on the Lock symbol in the Time panel (see figure 2) of the strip properties. If you want to apply the Lock on all selected strips, you have to press the :kbd:`Alt` key while clicking the Lock symbol. The strip is shown as striped in the sequencer.

- Lock Strips (:kbd:`Shift-L`): disables the strip from being changed.
- Unlock Strips (:kbd:`Shift-Alt-L`): enables disabled strips allowing them to be changed.