---
layout: api-reference
section: webportal
subsection: v1
categorie: API Reference
title: References
name: Car.driverDistractionOn
domain: Car
supported:
  - 2
  - 3
  - 4
type: event
---
Event triggered when the distraction status is changed to ON (display driver distraction popup).

>**Note:** This event is triggered when the speed goes below 5km/h.

### Example

```javascript
try {
	
	// Car
	if ((typeof Car !== "undefined") && (typeof Car.addEventListener !== "undefined")) {
		Car.addEventListener("driverDistractionOn", function(){
			alert("The driver distraction mode is now turned on.");
		});
	}
}catch(e) {
	DealWithCarError(e);
}
```

*Appeared in Software version 5.14.11.30*