# Trimming in the timeline

## Status

* [x] It is explained clearly what the feature is supposed to do
* [ ] [Same-Track-Transition](https://invent.kde.org/kde/kdenlive/-/wikis/dev/ideas/Same-Track-Crossfades) has to be implemented first
* [ ] It is clear how this can be implemented in Kdenlive

## Intro

Inputs:

* https://kdenlive.org/en/video-editing-applications-handbook/#trim

Questions:

* Are operations clear to understand? (which target track, IN/OUT points, short tutorial with pictures)
* Are operations easy to find?


### Summary

Trimming functionality consists of different parts:

* The logic to apply the different operations in the timeline (setting new IN/OUT points for the clips etc.)
* The user controls for using the trimming tools. This includes keyboard/mouse control, buttons, menu entries.
* The clip monitor which shows the relevant IN/OUT points of affected clips (up to 4)

Workflow:

1. Select a clip in the timeline
1. Choose a trim tool
1. Trim the clip

![image](uploads/7f93d6d0c1a397c91afdb73045b8b0ec/image.png)


## Tools

| Name | Status | Description
| --- | --- | --- |
| Rolling | | Trim adjacent IN and OUT points
| Ripple | | Trim clip and shift following clips by the trimmed amount
| Slip | | Shift IN and OUT points of a clip by X
| Slide | | Move clip on timeline and trim adjacent IN and OUT points

