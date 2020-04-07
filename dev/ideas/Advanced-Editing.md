# Advanced Editing in the timeline

* Are operations clear to understand? (which target track, IN/OUT points, short tutorial with pictures)
* Are operations easy to find?

## Tools

| Name | Status | Description
| --- | --- | --- |
| Rolling | | Trim adjacent IN and OUT points
| Ripple | | Trim clip and shift following clips by the trimmed amount
| Slip | | Shift IN and OUT points of a clip by X
| Slide | | Move clip on timeline and trim adjacent IN and OUT points

Clip operations can be chosen with a shortcut, which then affects the selected audio/video track. Or by using the mouse after choosing the timeline mode (e.g. insert mode) from a dropdown – in that case, audio is not moved to the selected audio track but to the audio track with the same number as the video track (bug?).

| Name | Status | Description |
| --- | --- | --- |
| Insert | ✔️ | Insert clip and move following clip material to the right
| Extract | | Remove clip and move following clip material to the left
| Overwrite | ✔️ | Replace section in timeline by clip
| Lift | ✔️ | Remove clip from timeline, leave following clip material where it was

Questions:

* What should happen in insert mode when moving a clip which is already on the timeline? Currently it behaves as if a new clip was inserted.


## Other ideas

* Snap cursor to clip boundaries in the timeline, e.g. when holding Shift → workflow: Snap to end of a clip, then insert clip there with `V` in insert mode