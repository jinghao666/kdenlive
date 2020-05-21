# 3-Point Editing in the timeline

## Status

* [x] It is explained clearly what the feature is supposed to do
* [x] It is clear how this can be implemented in Kdenlive
  * Tools are implemented!
* [ ] Usability and consistency is checked

## Intro

Inputs:

* https://kdenlive.org/en/video-editing-applications-handbook/#3point
* #225

Questions:

* Are operations clear to understand? (which target track, IN/OUT points, short tutorial with pictures)
* Are operations easy to find?

## Tools

Clip operations can be chosen with a shortcut, which then affects the selected audio/video track. Or by using the mouse after choosing the timeline mode (e.g. insert mode) from a dropdown – in that case, audio is not moved to the selected audio track but to the audio track with the same number as the video track (bug?).

| Name | Status | Description |
| --- | --- | --- |
| Insert | ✔️ | Insert clip and move following clip material to the right
| Extract | | Remove clip and move following clip material to the left
| Overwrite | ✔️ | Replace section in timeline by clip
| Lift | ✔️ | Remove clip from timeline, leave following clip material where it was

Questions:

* What should happen in insert mode when moving a clip which is already on the timeline? Currently it behaves as if a new clip was inserted.


## Border Cases

Several functions have to be considered for 3-point editing:

* Tracks on the timeline: which ones are affected?
* Grouped clips: How are clips affected, if they are in the same group and time range, but on different tracks?
* Locked tracks: Tracks can be locked, in that case they should not be affected
* Active tracks: Tracks can be marked as active, in which case they serve as 

### Overwrite clip in group

In the situation below, when the clip region to use for overwriting (with <kbd>b</kbd>), the left hand site of the group is replaced entirely.

| Before | After |
|---|---|
| ![image](uploads/33f81ef16dde4e8daad7b97f80b733c2/image.png) | ![image](uploads/ba1c54525135f43b58edb8d5699fa17a/image.png) |

### Overwrite clip affects other tracks

When overwriting with A2/V2 selected as target tracks, the clips on A1/V1 are removed as well.

| Before | After |
|---|---|
| ![image](uploads/b15df17626397f84d52dc7a3ca43efac/image.png) | ![image](uploads/911f1ea47aaab84fd7d77058f06bb1f9/image.png) |


### Drag and drop timeline clip in insert mode adds space

When using the mouse in insert mode to drag&drop the selected clip a few frames to the right, the original space of the clip is preserved and it is inserted again, shifting everything to the right. As the clip already is on the timeline, it should probably behave the same way as in normal mode.

| Before | After |
|---|---|
| ![image](uploads/35b118c0f1e85648afd583422de48492/image.png) | ![image](uploads/79f4f0d8d7b30507e12e988cc3191d96/image.png) |


## Other ideas

* Snap cursor to clip boundaries in the timeline, e.g. when holding Shift → workflow: Snap to end of a clip, then insert clip there with `V` in insert mode
* Also support [4 point editing](https://www.premiumbeat.com/blog/3-and-4-point-editing-premiere-pro/)?