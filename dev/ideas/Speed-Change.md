# Speed Change

Speed effects are different from other effects in that they alter the length of a clip. This puts speed effect into a separate effect category.

There are different challenges that arise with speed change.

* When slowing down, intermediate frames are needed. This is done e.g. by [slowmoVideo](http://slowmovideo.granjow.net/) using optical flow.
* When speeding up, motion blur may be desired to keep the image look natural
* Audio also changes. Is it simply stretched, whereby pitch changes as well, or should only the speed change (but not pitch) as done e.g. by [Paulstretch](http://hypermammut.sourceforge.net/paulstretch/)?

Editing also poses challenges:

* It is impossible to edit inside the timeline due to the clip length change
* When allowing curves for speed change, the effect GUI becomes much more complex and does not fit into a widget anymore. slowmoVideo has an own UI just for that with a 2D canvas. The input video is on one axis and the output video on another axis, and a curve defines which frames the output video picks from the input video.

![image](uploads/691865b1f9a55b2f7d674b296d3f9546/image.png)
