---
layout: api-reference
section: webportal
subsection: v1
categorie: API Reference
title: References
name: Device.GetCarBrand()
domain: Device
supported:
  - 2
  - 3
  - 4
type: api
---

### `Device.GetCarBrand()`

| **Description** | Get the brand of the vehicle
| **Response** | *Number* Car brand 

> Value | Car Brand
> ----|----
> 0 | Peugeot
> 1 | Citroen
> 2 | DS
> 3 | Toyota
> 4 | Opel
> 5 | Vauxhall

| **Parameter**   | *Void*

#### Example

```javascript
var carBrand = Device.GetCarBrand()
if (carbrand === 2) {
  DisplayMenuDS()
} else {
  DisplayMenu()
}
```

*Appeared in Software version 5.14.11.30*