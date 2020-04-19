---
title: Update Hexo blog layout for theme icarus
author: Jun Hu
toc: true
tags:
  - Hexo
date: 2019-08-16 23:25:31
---

>In this post I am following instruction kindly provided by [xiefayang](https://www.xiefayang.com/) to create a two-cloumn layout for post pages for Hexo theme icarus, so that post pages are clean and tidy, and easier to focus.

<!-- more -->


# update layout.js

`themes/hexo-theme-icarus/includes/helpers/layout.js`

```javascript
...
...
//return widgets.filter(widget => widget.hasOwnProperty('position') && widget.position === position);
if (this.page.layout !== 'post') {
	return widgets.filter(widget => widget.hasOwnProperty('position') && widget.position === position);
}
if (position === 'left') {
//here you can choose your own widgets showing on the left of post pages
	return widgets.filter(widget => widget.hasOwnProperty('position') && (widget.type === 'toc' || widget.type === 'category'));
} else {
	return []
}
...
...
```

# update widget.ejs

`themes/hexo-theme-icarus/layout/common/widget.ejs`

```javascript
<% if (get_widgets(position).length) { %>
<% function side_column_class() {
	switch (column_count()) {
		case 2:
			//return 'is-4-tablet is-4-desktop is-4-widescreen';
			return 'is-4-tablet is-4-desktop is-3-widescreen';
		case 3:
			return 'is-4-tablet is-4-desktop is-3-widescreen';
	}
	return '';
} %>
...
...
```
# update layout.ejs

`themes/hexo-theme-icarus/layout/layout.ejs`

```javascript
...
...
<% function main_column_class() {
	switch (column_count()) {
		case 1:
			return 'is-12';
		case 2:
			//return 'is-8-tablet is-8-desktop is-8-widescreen';
			return 'is-8-tablet is-8-desktop is-9-widescreen';
		case 3:
			return 'is-8-tablet is-8-desktop is-6-widescreen'
	}
	return '';
} %>
...
...
```

# update style.styl

`themes/hexo-theme-icarus/source/css/style.styl`

```css
...
...
@media screen and (min-width: screen-widescreen)
    .is-1-column .container
    .is-2-column .container
        max-width: screen-desktop - 2 * gap
        width: screen-desktop - 2 * gap
    .is-3-column .container
        max-width: screen-widescreen - gap
        width: screen-widescreen - gap
@media screen and (min-width: screen-fullhd)
    .is-3-column .container
        max-width: screen-fullhd - 2 * gap
        width: screen-fullhd - 2 * gap
    .is-2-column .container
        max-width: screen-widescreen - 2 * gap
        width: screen-widescreen - 2 * gap
    .is-1-column .container
        max-width: screen-desktop - 2 * gap
        width: screen-desktop - 2 * gap
...
...
```

# P.S.
It is worth mentioning that, to use video-container class for YouTube vedios, which has been included in theme icarus (it allows the videos auto-resize in a responsive site layout), simply put `<div class="video-container"></div>` pair outside the original HTML codes.
`themes/hexo-theme-icarus/source/css/style.styl`
```css
...
...
/* ---------------------------------
 *        Fix Video
 * --------------------------------- */
.video-container {
	position: relative;
	padding-bottom: 56.25%;
	padding-top: 25px;
	height: 0;
}
.video-container iframe {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
}
...
...
```

