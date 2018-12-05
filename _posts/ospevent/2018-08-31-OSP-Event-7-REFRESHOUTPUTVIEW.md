---
title: REQUEST OUTPUT VIEW EVENT
permalink: /workbench/event/requestoutputview/
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
date: 2018-08-31 09:00:00 +0900
comments: true
order: 10
support: true
classes: wide
redirect_from:
  - /theme-setup/
sidebar:
  nav: workbenchevent
---

### OSP REQUEST OUTPUT VIEW 이벤트

- 샘플 예제
```javascript
Liferay.on(
		OSP.Event.OSP_REFRESH_OUTPUT_VIEW,
		function(e){
			var myId = '<%=portletDisplay.getId()%>';
			if( myId !== e.targetPortlet ) return;

			var eventData = {
					portletId: '<%=portletDisplay.getId()%>',
					targetPortlet: <portlet:namespace/>connector
			};

			Liferay.fire(OSP.Event.OSP_REQUEST_OUTPUT_PATH, eventData);
		}
);
```
