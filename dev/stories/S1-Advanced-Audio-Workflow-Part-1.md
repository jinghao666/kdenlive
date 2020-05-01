See [Advanced Audio Workflow](/dev/ideas/Advanced-Audio-Workflow).


## Summary of first feature package

* In this package, we only consider the **Stereo** audio.
* Important is **channel mapping** from input clips.
* When that is possible, extend the **timeline mixer**

Bonus Features

* Support **multiple output tracks**
* When dropping a clip with multiple tracks to the timeline, add all tracks to the timeline (to separate audio tracks).
* Add notes to channels of input clips to describe them (e.g. *Voice L* or *Environment*) for easier mapping

To keep in mind:

* How do we stay backwards compatible?
  * We need to know the current behaviour and map channels the old way for old project files
* For normal users (with stereo only), the workflow should stay simple


## Features

The following drawing shows the main topics. Example steps would be:

1. Create a new project and define two output tracks. One track will be used for English voice and the second track for Italian voice. Both have two channels.
1. Define which audio tracks in the timeline are routed to which master track.
1. Import the clips in the project bin. For clips which are not single-track stereo, map the clip channels to output channels. Normally, one would map to Timeline track channels, but for a stereo project it is always CH1 and CH2.
1. Add the clips to the timeline. For individual timeline clip instances, the channel mapping can be adjusted.

![image](uploads/f762567944d8123f0e4ddc3eb2d52c1f/image.png)


### Mapping input clip channels

As described in [Advanced Audio Workflow][aaw], clips can have multiple tracks and each track can have a number of channels. The user has to be able to choose which channels to use in the timeline.

There are different approaches for defining the mapping, each with advantages and disadvantages.

* (a) Define the output channel per clip channel.
* (b) Define clip source channels per output channel. For the stereo case, this only needs two dropdowns as there are only two output channels.
* (c) Use a graphical mapper as e.g. Audacity is doing it. This is the most flexible and could also be implemented in a later step.

![image](uploads/2ccc2964c4d5f9c8b8a18c48864a7229/image.png)

In case of mono clips, the single clip channel has to be distributed to both CH1 and CH2. This can be accomplished in (a) by using a dropdown with checkboxes.

If multiple clip channels should be sent to the same output channel, this can be accomplished in (b) in the same way.


### Changing the mapping in timeline clip instances

Take an example audio file which contains voice on CH1+CH2 and environment sound on CH3+CH4. To treat them separately in the timeline, one wants to add the clip twice to the timeline, but once with the voice channels mapped to CH1+CH2 on the timeline track, and once with the environment sound mapped to CH1+CH2 on the timeline track.

The mapping done in the project bin only sets the default. Afterwards, it is possible to change the mapping for every clip instance in the timeline.


### Track Mixer

Every audio track has its own mixer. The output of the track, after mixing, is sent to the master track. The mixer should allow keyframed volume and stereo panning control.

In a later stage, multiple tracks can first be sent to a submix track in order to mix all of them simultaneously and then to the master track. Submix tracks are not part of this feature package.


### Project Master Mixer

In the master mixer, audio is expected to be panned correctly already and only requires overall volume control. The more important feature here is to define the number of tracks which are exported when the file is rendered. Two common use cases are:

* Multi-language tracks. Every language has a track in the exported video.
* Environment-only and environment+voice tracks


## Behaviour of Kdenlive 20.04

This table describes how Kdenlive 20.04 behaves in order to provide backwards compatibility when loading projects.

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

[aaw]: /dev/ideas/Advanced-Audio-Workflow