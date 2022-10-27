---
layout: api-reference
section: webportal
subsection: v1
categorie: API Reference
title: References
name: Car.GetBatteryLevel()
domain: Car
supported:
  - 4
type: api
---

### `Car.GetBatteryLevel()`

| **Description** | Gets the Battery level in percentage.
| **Response** | *Number*  Remaining battery percentage.
| **Parameter**   | *Void*

#### Example

```javascript
var BatteryLevel = Car.GetLevel();
// Batteryautonomy = 5 %
```

*Appeared in Software version 40.03.51.50*