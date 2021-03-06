# Kdenlive Wiki

This wiki contains information which is relevant for development.

* [Ecosystem](ecosystem) – describes the video editing ecosystem around Kdenlive
* [Inputs](dev/Inputs) – various sources which serve as basis for ideas
* [Ideas](dev/Ideas) – ideas to different topics start here
* [Stories](dev/Stories) – elaborated ideas, ready to work on, as story/epic
* [Roadmap](Roadmap) – road to vNext


## Issue links

Issues can be linked simply by their ID, like #42. The issues do not receive a backlink, but they can be extracted from this Wiki by cloning it locally and then running the following command:

```bash
git grep -I --only-matching -E '#[0-9]+' \
    | sed -e 's/\(.*\):#\([0-9]\+\)$/#\2 https:\/\/invent.kde.org\/kde\/kdenlive\/-\/issues\/\2 \1/' \
    | sort --unique \
    | column -s' ' -t
```

## All pages + menu sidebar

To see all pages https://invent.kde.org/multimedia/kdenlive/-/wikis/pages, or use the ~~force~~ API: [https://invent.kde.org/api/v4/projects/19/wikis](https://invent.kde.org/api/v4/projects/19/wikis)

GitLab Wiki has some limitations for the sidebar as it does not show all pages. This wiki is therefore using a [custom sidebar which is editable](/_sidebar). It is [generated with Node.js](https://invent.kde.org/eugster/node-area-41) from the JSON returned by the API.