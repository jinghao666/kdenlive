*This page contains ideas for future development which still need refinement.*

# UI and UX

| Topic | Benefit | Description |
| --- | --- | --- |
| **Improved keyframe editing** | | For example, edit all keyframes together: #259 |
| **Project Bin improvements** | | Improve visual clarity and UX for project bin. For example, add a bit of spacing between clip entries, fix #283. See also #287, #291 |
| **Improve effect experience** | Applying effects is faster | Improve visual clarity of the effects list (coloured number boxes do not help too much e.g.), keep looping a zone while modifying effects (see #293), check if interactions work (e.g. scrolling has a double assignment: It scrolls the effect properties page, but also the keyframe item). See also #350 |
| **Workspaces for specialised workflows** | Faster editing in an editing stage | Change what widgets are shown and how Kdenlive behaves depending on the current editing stage (audio, effects, color correction, …); see #407 |
| **Window management** | | Make a widget cover the whole window for better focus, see #519. Auto-adjust the clip monitor width to the video aspect ratio to give other widgets more space. |
| **Shortcuts** | | Give shortcuts another visit and make sure they are consistent (see e.g. #550) and also get inputs from [other editing tools][hb]. Create a shortcut guideline document where shortcuts are listed including the reasoning behind (e.g. in and out points with i and o because of the words and because the keys are next to each other). |


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

## Effects

| Topic | Benefit | Description |
| --- | --- | --- |
| **Speed Change** | | Reverse parts of videos easily (#555). Advanced speed editing including slow-motion can be accomplished e.g. with [slowmoVideo][sv], but including slowmoVideo requires building a slow-motion library which can be used by MLT e.g. |

# Audio

| Topic | Benefit | Description |
| --- | --- | --- |
| **Enhanced Audio Recorder** | Users which record audio directly within Kdenlive | See #105 |

# Stability and Testing

| Topic | Benefit | Description |
| --- | --- | --- |
| **Project Recovery after Crash** | Users are less likely to lose work. | Enhance project recovery. Check if the backup time interval is suitable. If a project crashes on load, catch the crash and offer to load an older version. See also #309, #418. |

# Random

Where is my Light Graffiti effect? {:-S

[hb]: https://kdenlive.org/en/video-editing-applications-handbook/
[sv]: http://slowmovideo.granjow.net/