# Multicam Editing

## Status

* [ ] It is explained clearly what the feature is supposed to do
* [ ] It is clear how this can be implemented in Kdenlive
* [ ] Usability and consistency is checked

## Intro

Inputs:

* PDF by Massimo
* [Editing tutorial in Premiere Pro](https://www.youtube.com/watch?v=tj75m4WYHm4)

Multi Camera Editing targets the video editing workflow where multiple cameras film the same scene (e.g. a theater, soccer game, …) and one wants to toggle between the cameras while keeping time in sync (i.e. there should not be any jumps forward or backward in time).

Typically, this is achieved in 3 steps:

1. Create a new multicam sequence of the selected clips
2. Align the clips, e.g. manually or based on their audio
3. Add the multicam sequence to the timeline and toggle between the cameras

A multi-camera sequence is a collection of time-synchronised clips. For example, it could contain 3 clips (i.e. from 3 different cameras). When playing it back, the clip monitor could display all 3 clips simultaneously to help deciding which clip (which camera) to show.

Without a multicam sequence, the user would manually have to cut the clip pieces of all sources together. For every change of the camera angle, the next clip would have to be added again, synced again, and cut to the correct length.

With a multicam sequence, the user would only add the sequence to a timeline track and then on-the-fly decide which clip from the sequence to show; the selection is remembered by the multicam sequence.

The multicam sequence is a clip that contains both video and audio.


## Questions

Can multiple clips be on the same track (e.g. because the camera recorded two consecutive files)?
