# Advanced Audio Workflow


## Status

* [x] It is explained clearly what the feature is supposed to do
* [ ] It is clear how this can be implemented in Kdenlive
  * A lot of information available, more discussion on details is required
* [ ] Usability and consistency is checked


## Intro

This idea is about handling audio when there are not only stereo clips.

Inputs:

* [In-depth introduction](https://invent.kde.org/kde/kdenlive/uploads/fec036664d3c462ffaa6d664512551c1/Audio_guide_updated_Mar_06_2020_ver01.pdf) on #382.
* [Channel Export Mapping in Audacity](https://manual.audacityteam.org/man/advanced_mixing_options.html)


## Additional notes

### Audio/Clip Basics

In the simple case (phone/camera recording), video clips have one stereo audio track. There are many more options however.

Technically, clips (video+audio like .mp4, or audio only like .wav) are primarily **containers** which contain encoded audio/video streams. The container describes what streams there are and in which format (and more). **Streams** can again contain channels. **Channels** represent a single (mono) waveform.

![image](uploads/79a760ee671fa9061b110d254996315a/image.png)

A video clip could now contain a video stream and two audio streams, one with stereo English language (i.e. 2 channels) and one with 5.1 Italian language (i.e. 6 channels). An audio clip from a field recording (with a multi-channel recorder) could contain 5 channels where CH1/CH2 are a stereo voice recording, CH3 is a sound effect mono channel, and CH4/CH5 are used for stereo environment recording. The channels can be combined in an arbitrary way in the input clip, but for editing they are used separately, for example the two voice channels only would be used on an audio track in the timeline.

```
INPUT ─────────────> TIMELINE  ────────────> OUTPUT

CLIPS contain e.g.   TRACKS to keep sound    Video CONTAINER with
* Live Voice         sources separated as    Audio TRACKS, e.g.
* Environment        long as possible (like  - with and without voice
* Sound fx           GIMP layers)            - different languages
* Music                                      containing CHANNELS
* Voiceover          CHANNELS in track       to achieve sound image, e.g.
  (other lang)       → achieve sound image   - Stereo
                     TRACKS                  - 5.1 Surround
                     → distinguish topics    
```