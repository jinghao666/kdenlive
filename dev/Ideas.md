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


# UI and UX

* How can we **improve user guidance?** Use modern methods to help the user find features and understand what they do.
* **Is the workflow intuitive** or can it be improved (e.g. less clicks, more clarity in navigation or switching widgets)?

| Topic | Benefit | Description |
| --- | --- | --- |
| **Improved keyframe editing** | | For example, edit all keyframes together: #259, add more easing modes #572 (note: CSS animations also contain easing modes) |
| **Project Bin improvements** | 🤓 | Improve visual clarity and UX for project bin. For example, add a bit of spacing between clip entries, fix #283. See also #287, #291 |
| **Improve effect experience** | 🤓 – Applying effects is faster | Improve visual clarity of the effects list (coloured number boxes do not help too much e.g.), keep looping a zone while modifying effects (see #293), check if interactions work (e.g. scrolling has a double assignment: It scrolls the effect properties page, but also the keyframe item). See also #350. Add comments to effects, see #582. Remove all effects on a clip, as in [T9797][T9797]. Check if resetting with RMB is the standard way of if double-click is better (see [T10295][T10295]). |
| **Workspaces for specialised workflows** | 🤓 – Faster editing in an editing stage | Change what widgets are shown and how Kdenlive behaves depending on the current editing stage (audio, effects, color correction, …); see #407. Reset layouts (#249) and include them in the project file #417 |
| **Window management** | | Make a widget cover the whole window for better focus, see #519. Auto-adjust the clip monitor width to the video aspect ratio to give other widgets more space. |
| **Shortcuts** | 🎥 | Give shortcuts another visit and make sure they are consistent (see e.g. #550, #563) and also get inputs from [other editing tools][kbd]. Create a shortcut guideline document where shortcuts are listed including the reasoning behind (e.g. in and out points with i and o because of the words and because the keys are next to each other). Add shortcuts for different playback speeds as in #406. |
| **General usability improvements** | 🎥 – Kdenlive provides a consistent and practical UX | Redesign clip popups (e.g. other location) to avoid that they overlap controls (#592), make it easier to resize the timeline (#593), use timeline scrubbing/zooming for faster navigation in the timeline, see [T10897][T10897] |

[T9797]: https://phabricator.kde.org/T9797
[T10295]: https://phabricator.kde.org/T10295
[T10897]: https://phabricator.kde.org/T10897


## Performance

| Topic | Benefit | Description |
| --- | --- | --- |
| **Rendered preview** | 🎥 | Pre-render the selected zone while editing when normal playback stutters. (implemented) |


# Editing Workflow

| Topic | Benefit | Description |
| --- | --- | --- |
| [**Advanced editing in timeline**][imp-kf] | 🎥 – Users of other professional video editing applications are familiar with the editing workflow from other programs. | Editing includes both *[trimming][trim]* and *[3-point editing][lift]*. Improve trimming of clips directly in the timeline whereby adjacent clips are trimmed as well, and inserting/(re-)moving clips on the timeline. See also #225 |
| **Editoral Collaboration** | | [T10260][T10260] | 

[T10260]: https://phabricator.kde.org/T10260
[imp-kf]: /dev/ideas/Advanced%20Editing

## Colour Correction

| Topic | Benefit | Description |
| --- | --- | --- |
| **Secondary Colour Correction** | | Colour Correction for parts of the image. This first requires a solid general colour correction workflow. |

## Timeline

| Topic | Benefit | Description |
| --- | --- | --- |
| **Track types** | | #421 – also support video-only tracks |
| **Various timeline enhancements** | | Use user-defined categories (name and colour) for guidelines, see #547. Merge clips again after they have been split, see [T10846][T10846]. |
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
| **Professional Audio Support** | 🎥 | Improve [working with audio][audio]. Cross-fade audio on a single track. Support more than 2 audio channels as #382. Add a master mixer for audio, as in #357. Support audio busses where audio output can be sent to, edited with an effect, and then mixed together in master. |
| **Enhanced Audio Recording Workflow** | YouTubers, Users which record audio directly within Kdenlive | Make it easier for users to record audio, e.g. as #594. Also, see #105. |
| **Auto-cut silence** | ❤️ – YouTubers | When recording voice, mute when the person is not talking. This could be an audio effect (threshold) which works in post, or directly included in the recorder (would not work for existing audio). See #247 |


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
| **Project Recovery after Crash** | Users are less likely to lose work. | Enhance project recovery. Check if the backup time interval is suitable. If a project crashes on load, catch the crash and offer to load an older version. See also #309, #418. |

# Random

Where is my Light Graffiti effect? {:-S

[hb]: https://kdenlive.org/en/video-editing-applications-handbook/
[kbd]: https://kdenlive.org/en/video-editing-applications-handbook/#shortcuts
[sv]: http://slowmovideo.granjow.net/
[trim]: https://kdenlive.org/en/video-editing-applications-handbook/#trim
[lift]: https://kdenlive.org/en/video-editing-applications-handbook/#3point
[audio]: https://kdenlive.org/en/video-editing-applications-handbook/#audio
