---
layout: doc-article
permalink: /webapi/b2b/quickstart/authentication/
redirect_from: 
    - /webapi/b2b/quickstart/
    - /webapi/b2b/authentication/
section: webapi
subsection: b2b
categorie: Quickstart
title: Authentication
description: "In this tutorial you will find an explanation about getting your B2B authentication in PSA network. It is required in order to consume Groupe PSA’s API."
---
{% include  content/get-your-certificate.md %}

# 5. REQUEST EXAMPLE
In order to use PSA Groupe web API B2B, you must authenticate yourself as a partner in Groupe PSA's network! Look further for more info about [B2B authentication](#authentication-b2b).
Once you get what you need for authentication, you can try to send your first request to Groupe PSA's API.

Here is an example with cURL:

{% include webapi-curl.md apiEndpointB2B='/fleets' httpVerb='GET' referenceURLResssourceB2B='/#/Fleet/getFleets' displayApiURL=true %}

**{version}** depends on your subscription:
- v2: *delegation publique*
- v3: *connected fleet* / *TMTS* / *UBI*

Type|Name|Value|Description|Required
-|-|-|-|-
Path param |`{version}`|`<v2>` or `<v3>`|Depends on your subscription.|Yes
Query Parameter|`client_id`|`<App_ID>`|Id of the application.|Yes
File|Client Certificate|`path/to/client_certificate.pem`|Your [SSL certificate](#authentication-b2b) for authentication in groupe PSA network.|Yes
File|Private Key|`path/to/key.pem`|Your Private Key file.|Yes
File|CA Certificate|`path/to/ca_certificate.pem`|PSA CA Cert for peer verification.|Yes
Header|`accept`|`application/json`| Advertises that you accept JSON content type. |Yes
Header|`authorization`|`Basic <BASIC_AUTH> `|Indicate that authentication is Basic Auth and *&lt;BASIC_AUTH&gt;* is *user:password* in Base64.  |Yes


# SEE ALSO

##### TUTORIAL

A [Quick Start guide]({{ site.baseurl }}/webapi/b2b/quickstart/examples/) is provided to help you understand the basics and get started.

##### TESTING THE API

To test the API you can check the [API List]({{ site.baseurl }}/webapi/b2b/api-reference/specification/) directly.
