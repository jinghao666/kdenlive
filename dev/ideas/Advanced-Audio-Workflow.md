# Advanced Audio Workflow


## Status

* [x] It is explained clearly what the feature is supposed to do
* [ ] It is clear how this can be implemented in Kdenlive
  * A lot of information available, more discussion on details is required
* [ ] Usability and consistency is checked


## Intro

This topic is about handling audio channels and tracks correctly and in a more professional workflow. Users should be able to choose which audio channels of an input file to use, and in which way to use them.

Currently, support for tracks and channels is limited. For example, for a clip with two tracks and two channels each, it is only possible to use the channels of one of the tracks.

Inputs:

* [In-depth introduction to audio editing](https://invent.kde.org/kde/kdenlive/uploads/fec036664d3c462ffaa6d664512551c1/Audio_guide_updated_Mar_06_2020_ver01.pdf) on #382.
* [Channel Export Mapping in Audacity](https://manual.audacityteam.org/man/advanced_mixing_options.html)


## Additional notes

Multi-channel and multi-track audio files can easily be created and edited in [Audacity](https://www.audacityteam.org/) for testing.

### Clip Basics:

In the simple case (phone/camera recording), video clips have one stereo audio track. There are many more options however.

Technically, clips (video+audio like .mp4, or audio only like .wav) are primarily **containers** which contain encoded audio/video streams. The container describes what streams there are and in which format (and more). **Streams** can again contain channels. **Channels** represent a single (mono) waveform.

(Streams are usually called tracks in video editing.)

![image](uploads/79a760ee671fa9061b110d254996315a/image.png)

To give two examples:

* A video clip could now contain a video stream and two audio streams, one with stereo English language and one with stereo Italian language.
* An audio clip from a field recording (with a multi-channel recorder) could contain 5 tracks with one channel each where tracks 1 and 2 are used for stereo voice recording, track 3 is used for sound effects, and tracks 4 and 5 are used for stereo environment recording. 

The channels can be combined in an arbitrary way in the input clip, but for editing they are used separately, for example the audio clip’s two voice channels would be used on an audio track in the timeline, the sound effect channel on another track.

### Editing workflow with streams

A high-level picture of the 3 stages input, editing, and output:

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

The editing part is obviously the most complex. Three different concepts are of importance there:

* **Remapping** of channels to decide which clip channels are used on the timeline track
* **Panning** or, generally, changing the sound image, e.g. to convert from stereo to surround or the other way round; this influences the number of channels
* **Submix tracks** which are like virtual track groups on which effects can be applied


### Example project with audio streams

An example of a more complex project could be the following:

![image](uploads/2aede732c2073e145c9dcc3696ca868c/image.png)

The goal in this project is to create a bilingual video file, each language track using 5.1 surround sound. It should be achieved from the sample audio input clips which may need some adjustment before they can be used. There is also a voiceover for the second language which is a stereo track recorded in post.

What is happening in this imaginary project?

1. When adding clips to the timeline, decide which channels should be used on the target audio track. A2 is a stereo track, and the voice channels from clip 2 need to be swapped (CH1 goes to the track’s CH2 and vice-versa). The effect is a mono track but should be heared as surround effect, which is accomplished by the panning.
2. A1 and A3 are first combined in a submix track: the two 5.1 tracks are reduced to one 5.1 track. Now there is keyframed volume control on the combined result.
3. Finally, all channels are routed to the master track which is another virtual submix track, with the difference that it has 18 input channels so the languages can be routed to separate output tracks. The voices are also mapped to 5.1 with a panning effect.