---
layout: api-reference
section: webportal
subsection: v1
categorie: API Reference
title: References
name: Media.GetFolderName()
domain: Media
supported:
  - 2
  - 3
  - 4
type: api
---

### `Media.GetFolderName()`

| **Description** | Gets the name of the current folder.
| **Response** | *String*  The current folder name < 255 characters.
| **Parameter**   | *Void*

#### Example

```javascript
//Check the state of the media

if (Media.GetMediaState() === 2) {
	// Media currently playing
	
	var foldername = Media.GetFolderName()
}
```

*Appeared in Software version 30.10.10.00*