title: Add an RSS feed to your hexo blog
author: Jun Hu
tags:
  - Hexo
  - RSS

date: 2019-06-16 13:54:00
---
1. Install hexo-generator-feed plugin
```bash
npm install hexo-generator-feed
```
<!-- more -->
2. Open your hexo configuration file:

_config.yml, add the following to the bottom:

  ```yml
  feed:
      type: atom
      path: atom.xml
      limit: 20
      hub:
      content:
      content_limit: 100
      content_limit_delim: ' '
  ```

- type - Feed type. (atom/rss2)
- path - Feed path. (Default: atom.xml/rss2.xml)
- limit - Maximum number of posts in the feed (Use 0 or false to show all posts)
- hub - URL of the PubSubHubbub hubs (Leave it empty if you don't use it)
- content - (optional) set to 'true' to include the contents of the entire post in the feed.
- content_limit - (optional) Default length of post content used in summary. Only used, if content setting is false and no custom post description present.
- content_limit_delim - (optional) If content_limit is used to shorten post contents, only cut at the last occurrence of this delimiter before reaching the character limit. Not used by default.


---


Reference:


*- [hexojs/hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed)*

