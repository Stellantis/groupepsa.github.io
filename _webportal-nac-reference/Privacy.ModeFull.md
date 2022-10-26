---
layout: api-reference
section: webportal
subsection: v1
categorie: API Reference
title: References
name: Privacy.ModeFull
domain: Privacy
supported:
  - 2
  - 3
type: event
---
Event triggered when the Full privacy mode is selected.

### Example

```javascript
try {
	// Privacy
	if ((typeof Privacy !== "undefined") && (typeof Privacy.addEventListener !== "undefined")) {
		Privacy.addEventListener("ModeFull", function(){
			alert("The privacy full mode is now Active");
		});
	}
} catch(e) {
	DealWithPrivacyError(e);
}
```

*Appeared in Wave 4.1 - version 30.05.14.30*