# Keyboard Maestro Windows Manager

This is a group of Keyboard Maestro macros to move windows in a way inspired
by Windows snap move shortcuts.

The snap move macros have the same logic in the four different directions.

If the window moves along the directory, the side which first hit the screen
boundary is named as near side, and the opposite side is the far side. For
example, in the macro "Window Snap Right <kbd>Ctrl + Option + Left</kbd>", the
right window side is the near side, and the left is the far side.

* (1) If the near side does not near the screen boundary, move the near side
   along the direction until it meets the screen boundary.

``` txt
+----------------------------+        +----------------------------+
|                            |        |                            |
|   +-------------------+    |        |   +------------------------+
|   |                   |    |        |   |                       ||
|   |                   |    |        |   |                       ||
|   |                   |    | +----> |   |                       ||
|   |                   |    |        |   |                       ||
|   +-------------------+    |        |   +------------------------+
|                            |        |                            |
|                            |        |                            |
+----------------------------+        +----------------------------+
```

* (2) Otherwise, if the far side does not cross the screen mid line yet, move the
   far side along the direction until it meets the mid line.

``` txt
+----------------------------+        +----------------------------+
|                            |        |                            |
|   +------------------------+        |              +-------------+
|   |                       ||        |              |            ||
|   |                       ||        |              |            ||
|   |                       || +----> |              |            ||
|   |                       ||        |              |            ||
|   +------------------------+        |              +-------------+
|                            |        |                            |
|                            |        |                            |
+----------------------------+        +----------------------------+
```

* (3) Otherwise, if the window does not occupy the 95% of the space in the perpendicular
   direction yet, resize the window so it fills the half of the screen.

``` txt
+----------------------------+        +----------------------------+
|                            |        |              +-------------|
|              +-------------+        |              |            ||
|              |            ||        |              |            ||
|              |            ||        |              |            ||
|              |            || +----> |              |            ||
|              |            ||        |              |            ||
|              +-------------+        |              |            ||
|                            |        |              |            ||
|                            |        |              +-------------|
+----------------------------+        +----------------------------+
```

* (4) Otherwise, if there's a monitor along the direction, move the window to the
   next monitor.

```
     +----------------------------+ +----------------------------+
     |              +-------------| |                            |
     |              |            || |                            |
     |              |            || |                            |
     |              |            || |                            |
     |              |            || |                            | +-+
     |              |            || |                            |   |
     |              |            || |                            |   |
     |              |            || |                            |   |
     |              +-------------| |                            |   |
     +----------------------------+ +----------------------------+   |
                                                                     |
+--------------------------------------------------------------------+
|
|    +----------------------------+ +----------------------------+
|    |                            | |--------------+             |
|    |                            | ||             |             |
|    |                            | ||             |             |
|    |                            | ||             |             |
+->  |                            | ||             |             |
     |                            | ||             |             |
     |                            | ||             |             |
     |                            | ||             |             |
     |                            | |--------------+             |
     +----------------------------+ +----------------------------+
```
