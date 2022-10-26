---
layout: api-reference
section: webportal
subsection: v1
categorie: API Reference
title: References
name: Connectivity.connectivityOn
domain: Connectivity
supported:
  - 2
  - 3
  - 4
type: event
---
Event triggered when the Internet connectivity status changes to `True`.

### Example

```javascript
try{
	// Connectivity
	if ((typeof Connectivity !== "undefined") && (typeof Connectivity.addEventListener !== "undefined")) {
		Connectivity.addEventListener("connectivityOn", function(){
			alert("The internet connectivity is now on");
		});
	}
} catch(e) {
	DealWithConnectivityError(e);
}
```

*Appeared in Software version 5.14.06.10*