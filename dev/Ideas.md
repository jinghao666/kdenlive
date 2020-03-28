*This page contains ideas for future development which still need refinement.*

What should be discussed about ideas?

* Bigger picture: Is the idea related to another topic and should be tackled from a more general perspective (e.g. change the timeline behaviour altogether instead of adjusting here and there)
* What is the benefit of the idea? Does it target a reasonably large user group to justify the development effort?
* What is the estimated effort? If it is hard to estimate, what details or what knowledge is missing?

GitLab issues are considered until 2020-03-28.

# UI and UX

| Topic | Benefit | Description |
| --- | --- | --- |
| **Improved keyframe editing** | | For example, edit all keyframes together: #259 |
| **Project Bin improvements** | | Improve visual clarity and UX for project bin. For example, add a bit of spacing between clip entries, fix #283. See also #287, #291 |
| **Improve effect experience** | Applying effects is faster | Improve visual clarity of the effects list (coloured number boxes do not help too much e.g.), keep looping a zone while modifying effects (see #293), check if interactions work (e.g. scrolling has a double assignment: It scrolls the effect properties page, but also the keyframe item). See also #350 |
| **Workspaces for specialised workflows** | Faster editing in an editing stage | Change what widgets are shown and how Kdenlive behaves depending on the current editing stage (audio, effects, color correction, …); see #407. Reset layouts (#249). |
| **Window management** | | Make a widget cover the whole window for better focus, see #519. Auto-adjust the clip monitor width to the video aspect ratio to give other widgets more space. |
| **Shortcuts** | | Give shortcuts another visit and make sure they are consistent (see e.g. #550) and also get inputs from [other editing tools][hb]. Create a shortcut guideline document where shortcuts are listed including the reasoning behind (e.g. in and out points with i and o because of the words and because the keys are next to each other). |
| **General usability improvements | Kdenlive provides a consistent and practical UX | Redesign clip popups (e.g. other location) to avoid that they overlap controls (#592), make it easier to resize the timeline (#593)


# Editing Workflow

| Topic | Benefit | Description |
| --- | --- | --- |
| **Advanced editing in timeline ** | Users of other professional video editing applications are familiar with the editing workflow from other programs. | #225 |

## Colour Correction

| Topic | Benefit | Description |
| --- | --- | --- |
| **Secondary Colour Correction** | | Colour Correction for parts of the image. This first requires a solid general colour correction workflow. |

## Timeline

| Topic | Benefit | Description |
| --- | --- | --- |
| **Track types ** | | #421 – also support video-only tracks |
| **Various timeline enhancements** | | Use user-defined categories (name and colour) for guidelines, see #547 |
| **Nested timelines** | Larger projects are easier to structure and to edit in post | Edit some clips on a timeline and add the result on the main timeline, see #226 |

## Effects

| Topic | Benefit | Description |
| --- | --- | --- |
| **Speed Change** | | Reverse parts of videos easily (#555, #224). Advanced speed editing including slow-motion can be accomplished e.g. with [slowmoVideo][sv], but including slowmoVideo requires building a slow-motion library which can be used by MLT e.g. |
| **Effect groups** | | #4 |

# Audio

| Topic | Benefit | Description |
| --- | --- | --- |
| **Enhanced Audio Recorder** | Users which record audio directly within Kdenlive | See #105. |
| **Improved audio recording workflow** | YouTubers | Make it easier for users to record audio, e.g. as #594 |
| **Auto-cut silence** | YouTubers | When recording voice, mute when the person is not talking. This could be an audio effect (threshold) which works in post, or directly included in the recorder (would not work for existing audio). See #247 |

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
[sv]: http://slowmovideo.granjow.net/