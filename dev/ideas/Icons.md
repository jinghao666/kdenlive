Goal: Create an icon set which use a **consistent style** (currently different themes are mixed) and which is also available as **dark theme** variant.

Ideas:

* Define some icon guidelines (see [GitLab Iconography](https://design.gitlab.com/product-foundations/iconography/) for an example)
* Define a colour schema
  * Use a linter which ensures that only colours from the colour schema are used; this allows to e.g. generate a dark theme variant
  * Define colour meanings (e.g. red for content that is removed, green for new content, blue for modified content)
* Define icon priorities
  1. Icons which have a tool button
  1. Icons from the default (Breeze?) theme
  1. Remaining icons