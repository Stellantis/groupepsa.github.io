---
layout: doc-article
permalink: /webportal/
section: webportal
title: Overview
description: "WebPortal is the browser allowing users to launch authorized Web Applications directly from the media system of their car."
---

# ABOUT WEBPORTAL

The WebPortal is the browser allowing users to launch authorized Web Applications directly from the media system of their car.
All the applications function on a subscription basis and their presence on the welcome page is automatically managed by the WebPortal.

![Image of Main Screen]({{ site.baseurl }}/assets/images/WebPortal_pic.jpg)

The WebPortal relies on [REST API](https://restfulapi.net/) and [MQTT protocol](http://mosquitto.org/man/mqtt-7.html).

![WebPortal Schema]({{ site.baseurl }}/assets/images/schema.svg)

# HOMESCREEN
When the system starts, a menu appears where the user can choose to access the Connected Apps:

![Image of Main Screen]({{ site.baseurl }}/assets/images/Mainscreen_portal.png)

They then reach the main menu containing the applications they are subscribed to:

![App Wall]({{ site.baseurl }}/assets/images/AppWall.png)

## SCREEN SIZE
Usually in-board screen is located on the dashboard of the car between driver and passenger.

There are 3 different screen resolutions depending on car model and generation.

The screen is divided in 3 areas: one is for your app while two others areas are dedicated to car system info.
Here is actual available screen size: **SD** = 800 x 363 px ; **HD** = 1280 x 582 px ; **WHD** = 1280 x 620 px.


<table class="largertable">
  <thead>
    <tr>
      <th>COLOR</th>
      <th>LEGEND</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><span class="verb" style="background-color: #A6A6A6 !important; color: white">&nbsp;Grey&nbsp;</span></td>
      <td>Total screen size.</td>
    </tr>
    <tr>
      <td><span class="verb get" style="background-color:#1E2335 !important">&nbsp;Blue&nbsp;</span></td>
      <td>Area of the screen dedicated to the infotainment system.</td>
    </tr>
    <tr>
      <td><span class="verb post" style="background-color:#94CE58 !important">Green</span></td>
      <td>Area of the screen available for your app</td>
    </tr>
  </tbody>
</table>


**Standard-Definition**
![screen-res-sd]({{site.baseurl }}/assets/images/webportalPresentationScreenSD.png)

**High-Definition**
![screen-res-hd]({{site.baseurl }}/assets/images/webportalPresentationScreenHD.png)

**Wide High-Definition**
![screen-res-whd]({{site.baseurl }}/assets/images/webportalPresentationScreenWHD.png)

## APP VALIDATION

The WebPortal will manage resources for your application to have access to data regarding the Car or the media.
To start deploying your Application, you have to create the html, css and js files and send them to PSA for validation first.

>**Be careful**: your app is a single page application. It means that you must have only one html file ('index.html') in your project.

Using the provided WebPortal API your App will be able to get information about:
- Radio: the current channel, the text displayed...
- Navigation: the position, the destination, important milestones...
- Privacy: the preferences of the user regarding their privacy
- Car: the speed, the autonomy of the car...

>Some functionalities are restricted and so may require special permission from PSA in order to be used in your application.

## REQUIREMENTS

Knowledge of:
- MQTT protocol
- HTML5 window.postMessage APIs
- JSON Serialization format

## NAC

The NAC, from the french "NAvigation Connectée" - Connected Navigation, is the system on which the WebPortal is running.  

There exists 3 differents generations of the NAC each new one coming with its own new functionalities:  

**NAC wave 2.1** - using QtWebKit 5.2.1 
based on WebKit from July 2013 (r153112).

**NAC wave 3** - using QtWebKit 5.5.0
based on the upstream trunk subversion revision 153112.

**NAC wave 4**- using QtWebKit 5.5.0
based on the upstream trunk subversion revision 153112.

## SOFTWARE VERSIONS

### WAVE 2
{% assign arrowUp='<span class="icon has-text-success"><i class="fas fa-arrow-up"></i></span>'%}
{% assign arrowDown='<span class="icon has-text-danger"><i class="fas fa-arrow-down"></i></span>'%}
{% assign equals='<span class="icon "><i class="fas fa-equals"></i></span>'%}

SW version	| Percentage of vehicles|Build date| Trend of use
-|-|-
21.07.16.32_NAC-r0 | 26%  |01/04/2018| {{arrowUp}}
21.07.67.32_NAC-r0 | 17%  |19/06/2019| {{arrowUp}}
10:90:42 | 12%  |07/09/2017| {{arrowDown}}
10:47:34 | 11%  |08/03/2018| {{arrowDown}}
10:82:12 | 6%  || {{arrowDown}}
10:68:24 | 4%  || {{arrowDown}}

### WAVE 3

SW version	| Percentage of vehicles |Build date | Trend of use
-|-|-
31.09.46.62_NAC-r0   | 14%  |19/11/2018| {{arrowUp}}
31.08.05.86_NAC-r0 |3% |15/05/2018  | {{arrowDown}}
10:50:42 | 1%  | | {{arrowDown}}


### WAVE 4

SW version	| Percentage of vehicles|Build date| Trend of use
-|-|-
42.01.21.42_NAC-r0 | 2% |01/02/2020 | {{arrowUp}}
40.04.20.22_NAC-r0 | 1%  | | {{arrowUp}}
42.01.37.32_NAC-r0 | 1% |18/09/2019 | {{arrowUp}}
40.04.33.12_NAC-r0 | 0%  | | {{arrowUp}}

## TUTORIAL

A [Quick Start guide]({{ site.baseurl }}/webportal/quick-start/) is provided to help you get started.

## API DOCUMENTATION

The complete API Documentation can be found [here]({{ site.baseurl }}/webportal/reference/).