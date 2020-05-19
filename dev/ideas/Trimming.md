# Trimming in the timeline

## Status

* [x] It is explained clearly what the feature is supposed to do
* [ ] [Same-Track-Transition](https://invent.kde.org/kde/kdenlive/-/wikis/dev/ideas/Same-Track-Crossfades) has to be implemented first
* [ ] It is clear how this can be implemented in Kdenlive

## Intro

Inputs:

* https://kdenlive.org/en/video-editing-applications-handbook/#trim  
* [Café 42 inputs](https://share.kde.org/s/bwPtC8s8C3gRggG)

Questions:

* Is trimming by mouse needed/convenient?
  * Dragging the clip in *slip/slide* mode would probably feel intuitive, as would dragging the edges in *roll/ripple*


### Summary

Trimming functionality consists of different parts:

* The logic to apply the different operations in the timeline (setting new IN/OUT points for the clips etc.)
* The user controls for using the trimming tools. This includes keyboard/mouse control, buttons, menu entries.
* The clip monitor which shows the relevant IN/OUT points of affected clips (up to 4)

Workflow:

1. Select which clip should be trimmed
   * For mouse, this is usually done with either special positions on the clip or with special mouse tools
   * For keyboard, the selection is usually controlled with the timeline cursor position and the active track and the activation of the trimming tool
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

