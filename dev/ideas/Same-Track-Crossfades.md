## Status

* [ ] It is explained clearly what the feature is supposed to do
* [ ] It is clear how this can be implemented in Kdenlive
* [ ] Usability and consistency is checked

## Intro

Inputs:

* [What Does It Mean To Crossfade Audio?][cfa]

```
Before:
   ┌────────┐┌──────────────┐
   │Clip A  ││    Clip B    │
   └────────┘└──────────────┘
After:
   ┌───────┲━━━┱────────────┐
   │Clip A ┃CF ┃  Clip B    │
   └───────┺━━━┹────────────┘
```

In Audio, cross-fading refers to the process of fading out one audio track while fading in another one. For same-track cross-fading, this is typically accomplished by the user by letting two audio clips overlap each other, which automatically generates a cross-fade effect.

* Fading is desired to avoid clicking noise when cutting audio if the audio curve does not end at 0.
* Cross-fading is desired to transition seamlessly from one recording to another, e.g. two consecutive recordings
* Same-track cross-fading is useful because only one track is needed.

The same applies for video clips where the images of the two clips are blended together.


### Approaches

In video editing applications, there are two different approaches to add a cross-fade between two clips A and B:

* Drag clip B to the left so it overlaps clip A. The overlapping section then becomes a cross-fade section.
* Select clip A and use a keyboard shortcut to add a cross-fade between those clips. This variant is used mainly by professional video editing appliations.



[cfa]: https://www.homebrewaudio.com/crossfade-meaning-what-does-it-mean-to-crossfade-audio/