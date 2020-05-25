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
* #677

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


## Border Case examples (20.04)

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

Furthermore, clips on other tracks are shifted as well; in the second example, the selected clip has been dragged a few frames to the right as well.

| Example| Before | After |
|---|---|---|
|1| ![image](uploads/35b118c0f1e85648afd583422de48492/image.png) | ![image](uploads/79f4f0d8d7b30507e12e988cc3191d96/image.png) |
|2| ![image](uploads/cdf48e42e270f38f491f616543a255d2/image.png) | ![image](uploads/5ac983ed48f80f11848cfc252d1d72bc/image.png) |


## Handling border cases

To be answered for the cases

* when a clip from the project bin is moved to the timeline (insert, overwrite, …)
* when the clip is already in the timeline and is moved

are the following questions:

* Which one is the target track? (Keyboard vs. mouse)
* What happens to the clips on the target track?
* How are clips on other tracks affected?
* What happens to locked tracks?
* What happens to clip groups and clips inside clip groups? Groups can be nested!
  * Is the change added to a group if it spans a group?
  * What if the changed region spans more than one group?
  * What if some of the clips in a clip group are on a locked track?

Scope: At most one audio/video stream each is inserted (multi-track audio not considered yet).

More on groups:

* Groups are in this case more like a tag on clips – for running the operations, there are only clips on the tracks. Groups may change *which clips* are affected by an operation and *which group* the result is assigned to, but not *how* the operation works.
* A clip always has an innermost group.

### Insert Mode

Insert is supposed to move the clips after the insert position to the right by the length of the clip to insert. If necessary, a cut is added.

When moving a clip to the timeline:

* Keyboard: Target tracks are the selected tracks.
* Mouse: Target tracks are the hovered tracks and :question: (currently the audio or video track with the same number)
* Clips on the target track follow the insert mode rules
* Clips on other tracks are cut and shifted to the right :question: 
* Locked tracks are not affected
* Groups: When there is a clip at the insert position, the newly inserted clip could be added to the same group as the existing clip (unless it is only a group of the video and the corresponding audio stream).

When clip already is in timeline: Moving a clip consists of two actions, removing it from the original position and inserting it at the new position. As *insert* is the opposite of *extract*, it would be intuitive to extract it at the original position and insert it at the new position.


### Overwrite Mode

When moving a clip to the timeline:

* Clips on other tracks should not change or be blanked in the insert region. :question: 
* Groups: The new clip overwrites some existing clips. It may make sense to add the new clip to the innermost group which the overwritten/changed clips have in common.


### Extract Mode

* Clips on other tracks are extracted as well to maintain sync amongst tracks.
* Groups: As clip material is only removed, there are only items removed from groups.


## Other ideas

* Snap cursor to clip boundaries in the timeline, e.g. when holding Shift → workflow: Snap to end of a clip, then insert clip there with `V` in insert mode
* Also support [4 point editing](https://www.premiumbeat.com/blog/3-and-4-point-editing-premiere-pro/)?