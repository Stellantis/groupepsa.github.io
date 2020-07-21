# EXAMPLES

This Quick Start contains examples of curl requests to Groupe PSA's web api for {% if page.section == 'webapib2b' %}Fleet Owners{% elsif page.section == "webapib2c" %}End-Users{% endif %}. These examples will show you how to deal with single objects, collections, geo-json objects and an example of POST and DELETE HTTP request.

To retrieve {% if page.section == 'webapib2b' %} authentication information refer to [this section]({{site.baseurl}}/webapi/b2b/authentication).{% elsif page.section == 'webapib2c' %} connection information refer to [this section]({{site.baseurl}}/webapi/b2c/connect).{% endif %}

## GET YOUR INFO

Web API base endpoint {% if page.section == 'webapib2b' %}'/fleets'{% elsif page.section == "webapib2c" %}'/user'{% endif %} allow you to retrieve info about your account in Groupe PSA's Network.

{% include_relative content/webapi-cUrl.md apiEndpointB2B='/fleets' apiEndpointB2C='/user' referenceURLResssourceB2C='/#/User/getUser' referenceURLResssourceB2B='/#/Fleet/getFleets' httpVerb='GET' displayApiURL=true %}

{% if page.section == 'webapib2b' %} 
**{version}** depends on your subscription:
- v2: *delegation publique*
- v3: *connected fleet* / *TMTS* / *UBI*
{% endif %}

## GET A LIST OF VEHICLES

The {% if page.section == 'webapib2b' %}'/fleets/{fid}/vehicles'{% elsif page.section == "webapib2c" %}'/user/vehicles'{% endif %} endpoint allow you to retrieve a list of your vehicles. 

See {% if page.section == 'webapib2b' %}[preview]({{site.baseurl}}/webapi/b2b/preview#pagination){% elsif page.section == "webapib2c" %}[preview]({{site.baseurl}}/webapi/b2c/preview#pagination){% endif %} for explanation about `indexRange` and `pageSize`.

{% include_relative content/webapi-cUrl.md apiEndpointB2B='/fleets/{fid}/vehicles'  referenceURLResssourceB2B='/#/Vehicles/getVehiclesByDevice' apiEndpointB2C='/user/vehicles' referenceURLResssourceB2C='/#/Vehicles/getVehiclesByDevice' httpVerb='GET' queryParam='&indexRange=<element_per_page>&pageSize=<nb_of_pages>' %}

## GET A VEHICLE POSITION

The {% if page.section == 'webapib2b' %}'/fleets/{fid}/vehicles/{id}/lastPosition'{% elsif page.section == "webapib2c" %}'/user/vehicles/{id}/lastPosition'{% endif %} endpoint allow you to retrieve the last known position for a vehicle.

Note that the 'Accept' header is not `--header 'Accept: application/hal+json'` but `Accept: application/vnd.geo+json`.

{% include_relative content/webapi-cUrl.md apiEndpointB2B='/fleets/{fid}/vehicles/{id}/lastPosition' apiEndpointB2C='/user/vehicles/{id}/lastPosition' referenceURLResssourceB2B='/#/Vehicles/getCarLastPosition' referenceURLResssourceB2C='/#/Vehicles/getCarLastPosition' httpVerb='GET' %}

## GET ALERTS OF A VEHICLE

The {% if page.section == 'webapib2b' %}'/fleets/{fid}/vehicles/{id}/alerts'{% elsif page.section == "webapib2c" %}'/user/vehicles/{id}/alerts'{% endif %} endpoint allow you to retrieve a list of alerts for a vehicle.
- Path parameter **{id}** is the unique identifier of one of your vehicles. 
- Query parameter `locale` will change the language of the alert message.

{% include_relative content/webapi-cUrl.md apiEndpointB2B='/fleets/{fid}/vehicles/{id}/alerts' apiEndpointB2C='/user/vehicles/{id}/alerts' referenceURLResssourceB2B='/#/Vehicles/getVehicleAlerts' referenceURLResssourceB2C='/#/Vehicles/getVehicleAlerts' httpVerb='GET' queryParam='&indexRange=<element_per_page>&pageSize=<nb_of_pages>&locale=<language>' %}

## POST NEW MONITOR

The {% if page.section == 'webapib2b' %}'/fleets/{fid}/monitors'{% elsif page.section == "webapib2c" %}'/user/vehicles/{id}/monitors'{% endif %} endpoint allow you to create a new monitor. Have a look to the {% if page.section == 'webapib2b' %}[monitor section]({{site.baseurl}}/webapi/b2b/monitor){% elsif page.section == "webapib2c" %}[monitor section]({{site.baseurl}}/webapi/b2c/monitor).
- Path parameter **{id}** is the unique identifier of one of your vehicles.
{% endif %} 

{% include_relative content/webapi-cUrl.md apiEndpointB2B='/fleets/{fid}/monitors' apiEndpointB2C='/user/vehicles/{id}/monitors' httpVerb='POST' referenceURLResssourceB2B ='/#/Monitors/createFleetVehicleMonitor' referenceURLResssourceB2B='#/Vehicles/setVehicleMonitor' httpBody='{
   "label":"IDF Zone monitor With Data Triggering:[vehicle.energy.electric.level] OR on Mondays",
   "subscribeParam":{
      "refreshEvent":600,
      "retryPolicy":{
         "policy":"Always",
         "maxRetryNumber":3,
         "retryDelay":120
      },
      "batchNotify":{
         "size":10,
         "timeWindow":300
      },
      "callback":{
         "target":"http://my.dn/monitors/cb1",
         "name":"HTTP_CB",
         "attributes":[
            {
               "type":"Query",
               "key":"vin",
               "value":"$vin"
            },
            {
               "type":"Header",
               "key":"Authorization",
               "value":"Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ=="
            }
         ]
      }
   },
   "extendedEventParam":[
      "vehicle.alerts",
      "vehicle.status"
   ],
   "triggerParam":{
      "triggers": [
      {
         "name": "outOfParis",
         "zone": {
            "transition": "Out",
            "circle": {
               "radius": 20,
               "center": {
               "longitude": 2.333333,
               "latitude": 48.866667
               }
            }
         },
         "name": "onMonday",
         "time": {
            "times": [
               {
               "recurrence": "Daily",
               "start": "PT14H30M",
               "occurence": {
                  "day": [
                     "Mon"
                  ]
               },
               "duration": "PT04H30M"
             }
            ],
            "time.zone": "Europe/Paris"
         },
         "name": "batteryIsLow",
         "data": {
          "data": "vehicle.energy.electric.level",
          "op": "lowerThan",
          "value": [
            "50"
            ]
        }
      }
    ],
    "bool.exp": "((outOfParis & (batteryIsLow | onMonday)"
  }
}' %}

{% comment %} 
## PUT EDIT A MONITOR

The {% if page.section == 'webapib2b' %}'/fleets/{fid}/monitors/{mid}/status'{% elsif page.section == "webapib2c" %}'/user/vehicles/{id}/status'{% endif %} endpoint allow you to create a new monitor. Have a look to the {% if page.section == 'webapib2b' %}[monitor section]({{site.baseurl}}/webapi/b2b/monitor){% elsif page.section == "webapib2c" %}[monitor section]({{site.baseurl}}/webapi/b2c/monitor){% endif %}.
- Path parameter **{id}** is the unique identifier of one of your vehicles. 

{% if page.section == 'webapib2b' %}

{% assign apiEndpoint='/fleets/{fid}/monitors/{mid}/status'%}
{% assign referenceURLResssource ='/#/Monitors/setFleetVehicleMonitorStatus' %}

{% elsif page.section == "webapib2c" %}

{% assign apiEndpoint='/user/vehicles/{id}/status'%}
{% assign referenceURLResssource ='/#/Vehicles/setFleetVehicleMonitorStatus' %}

{% endif %}

{% assign httpVerb='POST'%}
{% assign httpBody='{

}'%}
{% include_relative content/webapi-cUrl.md %}
{% endcomment %}

## DELETE A MONITOR

The {% if page.section == 'webapib2b' %}'/fleets/{fid}/monitors/{mid}'{% elsif page.section == "webapib2c" %}'/user/vehicles/{id}/monitors/{mid}'{% endif %} endpoint allow you to retrieve a list of alerts for a vehicle.
- Path parameter **{id}** is the unique identifier of one of your vehicles. 
- Query parameter `locale` will change the language of the alert message.

{% include_relative content/webapi-cUrl.md apiEndpointB2B='/fleets/{fid}/monitors/{mid}' apiEndpointB2C='/user/vehicles/{id}/monitors/{mid}' referenceURLResssourceB2B='/#/Monitors/deleteFleetMonitor' referenceURLResssourceB2C='/#/Vehicles/deleteMonitordd' httpVerb='DELETE' queryParam='&indexRange=<element_per_page>&pageSize=<nb_of_pages>&locale=<language>' %}

# SEE ALSO

##### TRY OUT!

Retrieve all reference of this API, go to the {% if page.section == 'webapib2b' %}[API List]({{ site.baseurl }}/webapi/b2b/reference/){% elsif page.section == "webapib2c" %}[API List]({{ site.baseurl }}/webapi/b2c/reference/){% endif %}.

{% if page.section == 'webapib2b' %}
##### AUTHENTICATION

Groupe PSA's web API for fleet owner utilizes mutual authentication. Follow this step-by-step [tutorial]({{site.baseurl}}/webapi/b2b/authentication/) and obtain your own certificate.
{% elsif page.section == "webapib2c" %}
##### CONNECT

Groupe PSA's web API for end-users utilizes OAuth2 connection, follow this [link]({{site.baseurl}}/webapi/b2c/connect/) for connection tutorial. {% endif %}
