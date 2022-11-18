---
title: "Finding Some Inspiration"
date: 2022-11-11T18:28:44-06:00
draft: true

# HelloFriend Specific
#hideReadMore: false
#cover = "img/default.jpg"
#description = "Finding inspiration from others, a kick in the butt."
---

It's been a few years since I'd actively used Mastodon but with the recent flood of users to the fediverse I figured I'd give it another shot, this time creating a profile on fosstodon. While this isn't a post about Mastodon I found a ton of inspiration seeing so many creative folks doing interesting things.

Simon Willison... I love the format of his [GitHub readme](https://github.com/simonw/), the live updates of Github activity, blog posts, and TIL's, and the TILs!!! I'd been thinking about using ActivityPub/Plermo/Mastodon to essentially micro-blog short bits of things I learned to track them like notes on a public scale but [TIL](https://github.com/simonw/til) is awesome! My approach I decided to take a bit differently, at least until I can figure out how I want to post my TIL items. I have a [Shiori](https://github.com/go-shiori/shiori) bookmark server (which has a very very limited and goofy API that only returns 30 items, no pagination, no filters) so it's like a "what I'm reading" feed. So with some Python and Flask, ripping a free HTML5 template off the interwebz, and putting together a single page site that lists GitHub activity, Blog Posts, and Bookmarks/Recently Read. I wanted this to be hosted on DigitalOcean as a web function but it needs clean-up and performance tweaks before I can get there, but it's working and running on [keyboardcrunch.com](https://keyboardcrunch.com/).
![Work Section](/uploads/finding-some-inspiration/work.png)
![Recent Reads Section](/uploads/finding-some-inspiration/RecentReads.png)