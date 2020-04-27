*This page contains ideas for future development which still need refinement.*

What should be discussed about ideas?

* Bigger picture: Is the idea related to another topic and should be tackled from a more general perspective (e.g. change the timeline behaviour altogether and redesign the clip monitor for trimming, instead of adjusting here and there)
* What is the benefit of the idea? Does it target a reasonably large user group to justify the development effort?
* What is the estimated effort? If it is hard to estimate, what details or what knowledge is missing?

What are possible goals?

* Provide a workflow that is efficient enough to work on long projects
* Provide core functionality that is expected from a professional video editor
* Attract more developers to speed up development

What are possible benefits?

* ❤️ – Community will love this feature
* 🎥 – Professionals need this feature
* 🤓 – Makes work with Kdenlive more efficient/pleasurable

GitLab issues are considered until 2020-03-28.


# Web Site

| Topic | Benefit | Description |
| --- | --- | --- |
| **Improved download experience** | ❤️ – new users have no troubles downloading Kdenlive | Always link to the newest Kdenlive.AppImage in the download section |


# UI and UX

* How can we **improve user guidance?** Use modern methods to help the user find features and understand what they do.
* **Is the workflow intuitive** or can it be improved (e.g. less clicks, more clarity in navigation or switching widgets)?

| Topic | Benefit | Description |
| --- | --- | --- |
| **Improved keyframe editing** | | For example, edit all keyframes together: #259, add more easing modes #572 (note: CSS animations also contain easing modes) |
| **Project Bin improvements** | 🤓 | Improve visual clarity and UX for project bin. For example, add a bit of spacing between clip entries, fix #283. See also #287, #291. Show start frame of zones and not just duration. Open and collapse folders with arrow keys ←→ instead of forwarding the clip in the clip monitor. Make tags more visible and allow to filter by tag. Add “Move to folder” to context menu to speed up clip sorting (rather than dragging the clip in a long list to the top and waiting for the content to scroll). |
| **Improve effect experience** | 🤓 – Applying effects is faster | Improve visual clarity of the effects list (coloured number boxes do not help too much e.g.), keep looping a zone while modifying effects (see #293), check if interactions work (e.g. scrolling has a double assignment: It scrolls the effect properties page, but also the keyframe item). See also #350. Add comments to effects, see #582. Remove all effects on a clip, as in [T9797][T9797]. Check if resetting with RMB is the standard way of if double-click is better (see [T10295][T10295]). Check for consistency in the effect widgets in general and check that numeric input is possible (also for Lift/Gamma/Gain value bar). |
| **Workspaces for specialised workflows** | 🤓 – Faster editing in an editing stage | Change what widgets are shown and how Kdenlive behaves depending on the current editing stage (audio, effects, color correction, …); see #407. Reset layouts (#249) and include them in the project file #417 |
| **Window management** | | Make a widget cover the whole window for better focus, see #519. Auto-adjust the clip monitor width to the video aspect ratio to give other widgets more space. |
| **Shortcuts** | 🎥 | Give shortcuts another visit and make sure they are consistent (see e.g. #550, #563) and also get inputs from [other editing tools][kbd]. Create a shortcut guideline document where shortcuts are listed including the reasoning behind (e.g. in and out points with i and o because of the words and because the keys are next to each other). Add shortcuts for different playback speeds as in #406. |
| **General usability improvements** | 🎥 – Kdenlive provides a consistent and practical UX | Redesign clip popups (e.g. other location) to avoid that they overlap controls (#592), make it easier to resize the timeline (#593), use timeline scrubbing/zooming for faster navigation in the timeline, see [T10897][T10897] |
| **Icons** | | Add more custom icons. For example, “Insert zone in project bin” is the clip icon – make it look related to set in and out points. Consistent icon language for Select/Razor/Spacer tools. Also have an “Enable Effect” icon. |
| **Rendering Dialog** | | Remember if the user wants to show advanced options |

[T9797]: https://phabricator.kde.org/T9797
[T10295]: https://phabricator.kde.org/T10295
[T10897]: https://phabricator.kde.org/T10897


## Performance

| Topic | Benefit | Description |
| --- | --- | --- |
| **Rendered preview** | 🎥 | Pre-render the selected zone while editing when normal playback stutters. (implemented) |
| **GPU support** | 🎥 – Everybody loves x-fold speed-up | Make use of GPUs to render videos and scopes. Use [ArrayFire](https://arrayfire.com/) e.g. to stay hardware independent. Ask Nicolas for his research. |


# Editing Workflow

| Topic | Benefit | Description |
| --- | --- | --- |
| [**3-point editing in timeline**][i-3pe] | 🎥 – Users of other professional video editing applications are familiar with the editing workflow from other programs. | Improve inserting/(re-)moving clips on the timeline. See the description on *[3-point editing][lift]*. See also #225 |
| **[Trimming][i-trim]** | 🎥 – Users of other professional video editing applications are familiar with the editing workflow from other programs. | Improve trimming of clips directly in the timeline whereby adjacent clips are trimmed as well. See the description on *[trimming][trim]*.
| **Editoral Collaboration** | | [T10260][T10260] | 

[T10260]: https://phabricator.kde.org/T10260
[i-3pe]: /dev/ideas/3-Point-Editing
[i-trim]: /dev/ideas/Trimming


## Colour Correction

| Topic | Benefit | Description |
| --- | --- | --- |
| **Scope improvements** | Simon wants it | Add logarithmic scale to histogram. Check what the `%%` mean in the Vectorscope. Show better colour levels in the vector scope when everything gathers on one point. |
| **[Secondary Colour Correction][i-scc]** | | Colour Correction for parts of the image. This first requires a solid general colour correction workflow. |

[i-scc]: /dev/ideas/Secondary-Colour-Correction

## Timeline

| Topic | Benefit | Description |
| --- | --- | --- |
| **Track types** | | #421 – also support video-only tracks |
| **Various timeline enhancements** | | Use user-defined categories (name and colour) for guidelines, see #547. Merge clips again after they have been split, see [T10846][T10846]. Upgrade the timeline ruler and e.g. highlight seconds and not just every 25th pixel. |
| **Nested timelines** | Larger projects are easier to structure and to edit in post | Edit some clips on a timeline and add the result on the main timeline, see #226, or combine clips as blender does it, see #422 |

[T10846]: https://phabricator.kde.org/T10846


## Effects

| Topic | Benefit | Description |
| --- | --- | --- |
| [**Speed Change**][speed] | ❤️ | Reverse parts of videos easily (#555, #224). Advanced speed editing including slow-motion can be accomplished e.g. with [slowmoVideo][sv], but including slowmoVideo requires building a slow-motion library which can be used by MLT e.g. |
| **Effect groups** | | #4 |

[speed]: /dev/ideas/Speed-Change


# Audio

| Topic | Benefit | Description |
| --- | --- | --- |
| [**Professional Audio Support**][aaw] | 🎥 | Improve [working with audio][audio]. Cross-fade audio on a single track. Support more than 2 audio channels as #382. Add a master mixer for audio, as in #357. Support audio busses where audio output can be sent to, edited with an effect, and then mixed together in master. |
| **Enhanced Audio Recording Workflow** | YouTubers, Users which record audio directly within Kdenlive | Make it easier for users to record audio, e.g. as #594. Also, see #105. |
| **Auto-cut silence** | ❤️ – YouTubers | When recording voice, mute when the person is not talking. This could be an audio effect (threshold) which works in post, or directly included in the recorder (would not work for existing audio). See #247 |

[aaw]: /dev/ideas/Advanced-Audio-Workflow


# Video

| Topic | Benefit | Description |
| --- | --- | --- |
| **Video orientation handling** | ❤️ – everybody taking pictures with a Smartphone, Action Cam, … | Change orientation of videos before they are used (e.g. a video that would mistakenly be inserted in portrait mode) |


# Titler

| Topic | Benefit | Description |
| --- | --- | --- |
| **Improved titler handling** | 🤓 | If the name of a duplicated title is auto-generated, use text content of the title as title, see #320 |

# Projects

| Topic | Benefit | Description |
| --- | --- | --- |
| **Archiving support** | Users which work a lot with Kdenlive and have many projects will like improvements here | Only include clips in the archive when they are actually used in the timeline, see #561 |


# Stability and Testing

| Topic | Benefit | Description |
| --- | --- | --- |
| **Project Recovery after Crash** | 🤓 – Users are less likely to lose work. | Enhance project recovery. Check if the backup time interval is suitable. If a project crashes on load, catch the crash and offer to load an older version. See also #309, #418. |
| **Stability improvements** | 🤓 – Users get less random crashes. Download counts show that patch releases are downloaded more often than `.0` releases. | Do not crash because MLT throws an exception (e.g. in `const uchar *imagedata = frame->get_image(format, ow, oh);` in `kthumb.cpp`), [see here][419603]. |

[419603]: https://bugs.kde.org/show_bug.cgi?id=419603

[hb]: https://kdenlive.org/en/video-editing-applications-handbook/
[kbd]: https://kdenlive.org/en/video-editing-applications-handbook/#shortcuts
[sv]: http://slowmovideo.granjow.net/
[trim]: https://kdenlive.org/en/video-editing-applications-handbook/#trim
[lift]: https://kdenlive.org/en/video-editing-applications-handbook/#3point
[audio]: https://kdenlive.org/en/video-editing-applications-handbook/#audio
