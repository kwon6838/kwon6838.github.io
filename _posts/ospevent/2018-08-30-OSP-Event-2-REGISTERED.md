---
title: REGISTERED EVENT
permalink: /workbench/event/registered/
author_profile: false
image:
  cover: true
  path: &image /assets/images/analyzerguide1/1.png
  feature: *image
  teaser: /assets/images/analyzerguide1/1.png
  thumbnail: /assets/images/analyzerguide1/14.png
  caption: "Post-Processor Development Guide"
categories: [event]
tags: [workbench, event]
support: true
date: 2018-08-30 09:00:00 +0900
comments: true
order: 10
support: true
classes: wide
redirect_from:
  - /theme-setup/
sidebar:
  nav: workbenchevent
---

### OSP REGISTERED 이벤트

- 샘플 예제
```javascript
Liferay.on(
	OSP.Event.OSP_EVENTS_REGISTERED,
	function(e){
		var myId = '<%=portletDisplay.getId()%>';
		if(e.targetPortlet === myId){
			console.log('[NGLViewer]Regestered'+e.portletId+' activated. '+new Date()+']');
		}
	}
);
```
