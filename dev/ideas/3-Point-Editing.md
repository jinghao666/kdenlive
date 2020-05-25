# 3-Point Editing in the timeline

## Intro

Inputs:

* https://kdenlive.org/en/video-editing-applications-handbook/#3point
* #225
* #677

Questions:

* Are operations clear to understand? (which target track, IN/OUT points, short tutorial with pictures)
* Are operations easy to find?

## Tools

| Name | Description |
| --- |  --- |
| Insert |  Insert clip and move following clip material to the right
| Extract | Remove clip and move following clip material to the left
| Overwrite |  Replace section in timeline by clip
| Lift |  Remove clip from timeline, leave following clip material where it was


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
* How does the spacer tool behave?

Scope: At most one audio/video stream each is inserted (multi-track audio not considered yet).

More on groups:

* Groups are in this case more like a tag on clips – for running the operations, there are only clips on the tracks. Groups may change *which clips* are affected by an operation and *which group* the result is assigned to, but not *how* the operation works.
* A clip always has an innermost group.

### Insert Mode

Insert is supposed to move the clips after the insert position to the right by the length of the clip to insert. If necessary, a cut is added.

When moving a clip to the timeline:

* Keyboard: Target tracks are the selected tracks. :white_check_mark: 
* Mouse: Target tracks are the hovered tracks and :question: (currently the audio or video track with the same number)
* Clips on the target track follow the insert mode rules :white_check_mark: 
* Clips on other active tracks are cut and shifted to the right :question: 
* Locked and inactive tracks are not affected :white_check_mark: 
* Groups: When there is a clip at the insert position, the newly inserted clip could be added to the same group as the existing clip (unless it is only a group of the video and the corresponding audio stream).

When clip already is in timeline: Moving a clip consists of two actions, removing it from the original position and inserting it at the new position. As *insert* is the opposite of *extract*, it would be intuitive to extract it at the original position and insert it at the new position.


### Overwrite Mode

When moving a clip to the timeline:

* Clips on other tracks should not change or be blanked in the insert region. :white_check_mark: 
* Groups: The new clip overwrites some existing clips. It may make sense to add the new clip to the innermost group which the overwritten/changed clips have in common.
* Spacer tool:
  * When moving content to the right, there is no difference to insert mode as nothing can be overwritten.
  * When moving content to the left, clips should overwrite existing content. :question: 

|Status|Description|
|---|---|
| TODO | ![image](uploads/57d1c7b9152fc849168c86ae74e2fff8/image.png) |

When the clip is already in the timeline (mouse): When thinking of the overwrite mode as of covering the timeline are a with another clip, moving that other clip away would again reveal the clip below (the undo operation of overwrite). So ideally, in overwrite mode, moving a clip around would first restore the original section and then overwrite the target section. However it is questionable if that is feasible. :question: 


### Extract Mode

* Clips on other tracks are extracted as well to maintain sync amongst tracks.
* Groups: As clip material is only removed, there are only items removed from groups.
* Spacer Tool: Should probably be disabled in Extract Mode :question:

When clip is already on the timeline: Behave the same way as insert mode as the modes are coupled :question: 



## Border Case examples (20.04)

Several functions have to be considered for 3-point editing:

* Tracks on the timeline: which ones are affected?
* Grouped clips: How are clips affected, if they are in the same group and time range, but on different tracks?
* Locked tracks: Tracks can be locked, in that case they should not be affected
* Target tracks: When inserting clips by keyboard, they will be inserted in the target track.
* Active tracks: Tracks which are active react to operations like insert, extract, etc.

### Overwrite clip in group

In the situation below, when the clip region to use for overwriting (with <kbd>b</kbd>), the left hand site of the group is replaced entirely.

| What |Before | After |
|---|---|--|
| Overwrite | ![image](uploads/33f81ef16dde4e8daad7b97f80b733c2/image.png) | ![image](uploads/ba1c54525135f43b58edb8d5699fa17a/image.png) |
| Extract section | ![image](uploads/84eb979c78541d9be8e4767914363b0a/image.png) | ![image](uploads/102acea957f31b2690db728e5b010505/image.png) |


### Drag and drop timeline clip in insert mode adds space

When using the mouse in insert mode to drag&drop the selected clip a few frames to the right, the original space of the clip is preserved and it is inserted again, shifting everything to the right. As the clip already is on the timeline, it should probably behave the same way as in normal mode.

Furthermore, clips on other tracks are shifted as well; in the second example, the selected clip has been dragged a few frames to the right as well.

| Example| Before | After |
|---|---|---|
|1| ![image](uploads/35b118c0f1e85648afd583422de48492/image.png) | ![image](uploads/79f4f0d8d7b30507e12e988cc3191d96/image.png) |
|2| ![image](uploads/cdf48e42e270f38f491f616543a255d2/image.png) | ![image](uploads/5ac983ed48f80f11848cfc252d1d72bc/image.png) |


### Overwrite with locked audio track crashes

#694


### Using spacer tool in overwrite mode

See #677


## Other ideas

* Snap cursor to clip boundaries in the timeline, e.g. when holding Shift → workflow: Snap to end of a clip, then insert clip there with `V` in insert mode
* Also support [4 point editing](https://www.premiumbeat.com/blog/3-and-4-point-editing-premiere-pro/)?