---
layout: api-reference
section: webportal
subsection: v1
categorie: API Reference
title: References
name: Media.GetTrackName()
domain: Media
supported:
  - 2
  - 3
  - 4
type: api
---

### `Media.GetTrackName()`

| **Description** | Gets the current track's name.
| **Response** | *String*  The name of the current track, 32 characters long max.
| **Parameter**   | *Void*

#### Example

```javascript
//Check the state of the media

if (Media.GetMediaState() === 2) {
	// Media currently playing
	var currentTrack = Media.GetTrackName()
}
```

*Appeared in Software version 30.10.10.00*