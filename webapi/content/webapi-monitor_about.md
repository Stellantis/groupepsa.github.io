# FEATURES
With Stellantis {% if page.subsection == 'b2b' %}Fleet Owner{% elsif page.subsection == 'b2c' %}End User{% endif %} API for Citroën, DS, Peugeot, Opel and Vauxhall, you can access and browse data about your vehicles.
But moreover our API allow you to set-up **events** that we will track for you.
Monitors are a way to design events tracking patterns for vehicles.
When the even is triggered, we will send a notification to your server.

**Available features:**

![monitors-features]({{site.baseurl}}/assets/images/monitors-features.png)

- **Zone Triggering**: The monitor will be triggered with an area condition, it could be leaving or entering somewhere.
- **Time Triggering**: The monitor will be triggered with an time condition, it could be using the vehicle during the night.
- **Data Triggering**: The monitor will be triggered with a vehicle data condition, it could be opening of the doors, using the AC, oil temperature increasing too much etc.

# HOW DOES IT WORK?

![monitor-system]({{site.baseurl}}/assets/images/monitor-system.png)

Once the monitor is created, our **event engine** will continuously check for the realization of your pattern.

When our server are receiving data from your car the **event engine** will check if the conditions of your monitor is satisfied. If the condition is met, our event engine will send a callback to your endpoint located in your system.

It is possible to set a retry policy with a specific number and frequency, it's useful in case of your webhook is temporary unavailable. 

![monitor-sequence]({{site.baseurl}}/assets/images/monitor-sequence.png)


# WEBHOOK TEMPLATE

What we offer with monitor is a simple way to process large amount of vehicle data. Although, you have to develop on your side a **dedicated webhook** able to receive our events.

This web server needs to be configured to read & process our events in order that you get informed about what's happening to your vehicles in real time. Below is the webhook template specification, it describes the HTTP callback you will receive.

> **Note:** HTTPS must be supported and a certificate issued by a trusted public and known CA must be provided. Indeed, the URL of your webhook must be the same as the one specified in when you created the callback.


# SEE ALSO

##### QUICK-START

Need to see examples of request to the API? Browse our {% if page.subsection == 'b2b' %}[Quick-Start]({{site.baseurl}}/webapi/b2b/quickstart/examples/){% elsif page.subsection == 'b2c' %}[Quick-Start]({{site.baseurl}}/webapi/b2c/quickstart/examples/){% endif %}.

##### TRY OUT!

Retrieve reference of this API, go to the {% if page.subsection == 'b2b' %}[API List]({{ site.baseurl }}/webapi/b2b/api-reference/specification/){% elsif page.subsection == 'b2c' %}[API List]({{ site.baseurl }}/webapi/b2c/api-reference/specification/){% endif %}.