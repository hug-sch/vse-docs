Zoom
----

In a video project it is important that you can zoom in on the section you're working on. On the other hand it's also important to have an overview of your timeline. Zooming in and out is thus a frequent occurring action.

.. raw:: html

   <iframe width="560" height="315" src="https://www.youtube.com/embed/mgmaP45gKqA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Figure 1: Annotated video with all the Zoom commands.

.. figure:: img/menu-view.svg
   :alt: Menu View
   :scale: 20%
   :align: right

   Figure 2: Menu View

.. |previous-button| image::
   img/previous-button.png
   :alt: Back to Previous button
   :scale: 60%

Ctrl-Spacebar
   The :kbd:`Ctrl-Spacebar` key will switch the area under the mouse cursor into full view. The video in figure 1 is created with this view. You can tell because at the very top, there is a button "Back to Previous" |previous-button|. This full-screen view will help you especially in the vertical dimension.
Home
   Pressing the :kbd:`Home` key zooms in on the total project; from start to finish and for all channels. Whenever you get lost in your timeline, press the :kbd:`Home` key to get back at the complete picture. Most Zoom commands can also be issued from the menu (see figure 2). The :kbd:`Home` equivalent is: View > Frame All.

NumpadPeriod
   Pressing the :kbd:`NumpadPeriod` key zooms the timeline to fit only the selected strips. Please note that this key is the period key on the numpad, not the period key on the alphanumeric keypad. The menu equivalent is: View > Frame Selected (see figure 2).

Shift-B
   After pressing the :kbd:`Shift-B` key (from Box Select), a crosshair cursor appears and you can click and drag to draw a rectangle in the sequencer area. Upon releasing the mouse button, the display is zoomed to this rectangle. The menu equivalent of pressing :kbd:`Shift-B` is: View > Zoom (see figure 2).

Wheel
   Scrolling the middle mouse wheel will zoom in horizontally on the section where the cursor is. Scrolling towards yourself will zoom out. Scrolling towards the screen will zoom in.

   You can modify this behavior by pressing the SHIFT, CTRL or ALT key.
   - SHIFT: pressing :kbd:`Shift` in combination with MMB will zoom vertically.
   - CTRL: pressing :kbd:`Ctrl` in combination with MMB will pan horizontally.
   - ALT: pressing :kbd:`Alt` in combination with MMB will move the playhead.

.. Warning::
   The User Preferences can change the function of the above modifiers.

   If you don't have a numpad, the `Emulate Numpad <https://docs.blender.org/manual/en/dev/editors/preferences/input.html>`_ option in the User Preferences will not help you out. You cannot use the regular period key from the alphanumeric keypad. You can change these shortcuts or make some of your own. Blender Frenzy has a nice video about creating these `Custom Keymaps <https://www.youtube.com/watch?v=2RtlvZfv8TI>`_.

   The situation is a little different if you don't have a middle mouse button. In the User Preferences you can set Emulate 3 button mouse. Pressing :kbd:`Alt-Shift-LMB` and dragging Left will zoom out and dragging right will zoom in (see also below). 

Ctrl-MMB
   Pressing :kbd:`Ctrl-MMB` and dragging left will zoom out or dragging right will zoom in. Dragging up will zoom in vertically and dragging down will zoom out vertically.

Scrollbar circles
   At the bottom and far right of the sequencer area, there are scrollbars. These scrollbars span the whole available width or height if all strips are visible. The length or height of the scrollbar gives you an indication how much percentage of the strips are not visible. Pressing the :keyb:`Home` key for example will make the scrollbars at full length and height.

   Each scrollbar has a circle at the beginning and end (see figure 3). Dragging these circles will shorten the scrollbars and as a result also the area of visible strips.

.. figure:: img/scrollbars.svg
   :alt: Scrollbars
   :align: right

   Figure 3: Vertical and horizontal scrollbars with zoom circles.
   
Zoom vertically or horizontally
   Most commands from above will zoom in or out on both dimensions simultaneously. For example, the :kbd:`Home` will zoom until all strips are visible, both on the horizontal and vertical dimension.
   
   With the :kbd:`MMB`, :kbd:`Ctrl-MMB` and the scrollbar circles, you can zoom in or out in one dimension only.