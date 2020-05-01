See [Advanced Audio Workflow](/dev/ideas/Advanced-Audio-Workflow).


## Summary of first feature package

* In this package, we only consider the Stereo workflow.
* Important is mapping channels from input clips.
* When that is possible, extend the mixer.
* When dropping a clip with multiple tracks to the timeline, add all tracks to the timeline (to separate audio tracks).

To keep in mind:

* How do we stay backwards compatible?
  * We need to know the current behaviour and map channels the old way for old project files


## Features

![image](uploads/f762567944d8123f0e4ddc3eb2d52c1f/image.png)


### Mapping input clip channels




## Behaviour of Kdenlive 20.04

| Clip | Result |
| ------ | ------ |
| 1 track with 2 channels (e.g. stereo) | 1 audio track with 2 channels as stereo channels are added |
| 2 tracks with 1 channels each (e.g. separate stereo tracks) |  | 
| 1 track with 6 channels (e.g. 5.1 audio) | |
| 6 tracks with 1 channels each (e.g. 5.1 audio) | |
| 1 track with 1 channel (mono) | |



## OLD

| Story | Description |
| --- | --- |
| | Choose clip channels to be used in the audio track. |
| | 

## Choose default clip channels

* Every channel in the input clip has a meaning. Allow to add a description, e.g. CH1: Voice L, CH2: Voice R, CH3: Sound fx mono
* For each channel, allow to define the default target channel when the clip is inserted in the timeline.
* When inserted in the timeline, the clip should play with the selected channel mapping.

## Change clip channel mapping

When a clip is already in the timeline, allow to change the channel mapping.