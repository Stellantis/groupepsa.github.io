---
layout: api-reference
section: webportal
subsection: v1
categorie: API Reference
title: References
name: Phone.LaunchPhoneCall()
domain: Phone
supported:
  - 2
  - 3
  - 4
type: api
---

### `Phone.LaunchPhoneCall(String phoneNumber)`

| **Description** | Intiates a phone call.
| **Response** | *Boolean*  True if the number passed contains only digits, False otherwise.

Parameter | Type | Description | Required
----|----|----|----
`phoneNumber` | String | The phone number to be called, Should be comprised of only Digits and have a length < 16 characters. | Required

#### Example

The following example tries to call a phone number and then reacts acordingly to the outcome.

```javascript
var PhoneNumber = '0123456789';
if (Phone.LaunchPhoneCall(PhoneNumber) === False) {
	//Cannot Launch the phone call
	GoBackToactivity();
} else {
	//Phone call will start soon
	Changeactivity();
}
```

#### KNOWN ISSUES

> The returned value does not represent the fact that the phone is present nor that the call was actually initiated.Indeed *True* might be returned even though the phone appaired by bluetooth doesn't have a Hands Free Profile.

*Appeared in Wave 4.1 - version 30.10.08.00*