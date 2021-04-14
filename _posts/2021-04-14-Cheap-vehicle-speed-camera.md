---
title: "Cheap vehicle speed camera with Raspberry Pi"
header:
  image: /assets/img/04142021/vehicle-speed-header.png
  caption: ""
tags: [electronics, projects, cities, transportation]
gallery_speeds:
  - url: /assets/img/04142021/vehicle-speed-plot.png
    image_path: /assets/img/04142021/vehicle-speed-plot.png
    alt: "vehicle speeds Boston"
    title: "Vehicle speeds Centre St West Roxbury, MA"
gallery_counts:
  - url: /assets/img/04142021/vehicle-count-plot.png
    image_path: /assets/img/04142021/vehicle-count-plot.png
    alt: "vehicle counts Boston"
    title: "Vehicle counts Centre St West Roxbury, MA"
---
Many people that live on or near busy streets share a similar concern: "Everyone drives too fast here." I hear it constantly from families with kids on my street (including my own), locals, newcomers, tourists, city officials, and even transportation planners. The problem is no one ever backs up these observations with any evidence. Occasionally when road design changes are proposed, the local transportation department will conduct a short-term, localized "speed study", which may or may not be representative of monthly average traffic speeds and volume. When it comes to local adherence to safe driving laws, as the old NASA slogan goes, "In God we trust, all others bring data."

> "When it comes to local adherence to safe driving laws, In God we trust, all others bring data."

After inspiration from [@balsama](https://twitter.com/balsama) on Twitter, who set up a similar project in Boston's North End, I decided to set up my own vehicle speed camera for monitoring my street in West Roxbury. The project is based on the work of [Claude Pageau on GitHub](https://github.com/pageauc/speed-camera).

## Parts List
Here are the components that I used to set up a quick-and-dirty speed camera at home (most parts I had laying around but the whole set could be bought new for ~$60):

1. Raspberry Pi 2B, 1GB, 900MHz
2. Raspberry Pi Camera v2
3. 32GB microSD card
4. USB WiFi dongle
5. Tape and cable ties

{% capture fig_img %}
![Foo]({{ "/assets/img/04142021/IMG_5381.JPG" | relative_url }})
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption></figcaption>
</figure>


## Setup Notes
Now, before we get to the findings, I should point out that there is a bit of setup required and room for improvement towards making this a friendlier setup experience and interface for anyone without command line and some programming experience. For example, the Raspberry Pi needs to be setup to run "headless" and a configuration script is available from Claude Pageau to change velocity units and tune the calibration of the camera to the world it is measuring.

The calibration process currently requires the user to enable the overlay of detection regions on the imagery so that you're actually measuring the cars on the road. Then the user can fine tune the estimated size of cars in the field-of-view until the measured velocity matches a few test images. For testing, I went ahead and drove past my camera a few times at a known speed and checked the timestamp of those images for the measurement, fine tuning some of those calibration parameters until it was accurately measuring 15/25/35 mph.

## Findings
{% capture fig_img %}
![Foo]({{ "/assets/img/04142021/centre-st-speeding-map.png" | relative_url }})
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption></figcaption>
</figure>

I continuously measured vehicle traffic along Centre Street in West Roxbury, MA, a busy arterial street that directly connects the neighborhood's business district to points North and into downtown Boston. Centre St was identified in Boston's "Safest Driver Competition" in 2019 as a problem speeding area and is on Boston's High Crash Network. Data was collected for approximately two weeks from March 28 to April 11. This section of street is lined with multi-family residences and there are many kids on my block in particular.

{% include gallery id="gallery_speeds" layout='' %}

[Link to Data](https://public.tableau.com/views/VehicleSpeeds-CentreStMontclair-WestRoxburyMA/Speed?:language=en&:display_count=y&:origin=viz_share_link)

The data shows a periodic pattern in vehicle speed statistics, with **median speeds > 35 mph** between midnight and 6am **every day**. During the morning rush hours into Boston, speeds generally decrease to 30-32 mph and drop further into the afternoon hours, before rising again for afternoon rush hours and higher still in the evenings. 25th to 75th percentile speeds on Centre St are well above the posted speed limit of 25 mph at all hours, 7 days a week. Few drivers are ever measured travelling below the posted speed limit. It should be noted that the speed camera does detect and measure bikes and, on occasion runners, but I have explicitly filtered out objects below 15 mph from this analysis.

> 25th to 75th percentile speeds on Centre St are well above the posted speed limit of 25 mph at all hours, 7 days a week.


{% include gallery id="gallery_counts" layout='' %}


[Link to Data](https://public.tableau.com/views/VehicleSpeeds-CentreStMontclair-WestRoxburyMA/Count?:language=en&:display_count=y&publish=yes&:origin=viz_share_link)

Vehicle counts in each direction clearly show the morning rush hour peak of **800 vehicles per hour** northbound, which levels off to ~400 per hour the rest of the day. Then there is the return peak of ~600 vehicles per hour southbound around the hours of 4-7pm. As expected, the morning rush spike is completely absent on Saturdays and Sunday has the lowest vehicle counts of the week in either direction. Keep in mind these vehicle counts are still during COVID, while everyone is writing about the permanence of remote work. It sure seems like gridlock is back in Boston (the former ["worst traffic congestion" winner of 2019 & 2020](https://www.bostonglobe.com/2020/03/09/metro/boston-ranks-worst-us-rush-hour-traffic-second-year-row/)).

I know others would love to be able to collect data like this at other locations. To really democratize use of a sensor setup like this, the project would need more work to simplify the setup, configuration and use. Currently the Raspberry Pi and camera need to be run indoors with access to a WiFi network. In order to install sensors outdoors at non-residential locations, the system would need to have a more rugged, IP-rated package, GPS receiver, battery power and a cellular link, possibly with a cloud connection to AWS/Azure for provisioning and access to the data. If you'd like a similar setup to take measurements at a location with WiFi access, find me on Twitter [@jasonbylsma](https://twitter.com/jasonbylsma?lang=en) or [email](mailto:bylsma.jason@gmail.com).

It should be mentioned that there is reluctance to automated enforcement cameras or traffic cameras generally in Massachusetts and other states. A red light camera bill was barely voted down in 2020 in MA and has been tabled to the next legislative session (tell your state senator to support [S.1376](https://malegislature.gov/Bills/191/S1376)). The reluctance towards traffic cameras could be avoided with the use of small, low-cost radar sensors instead of cameras. I'm working on amplifiers for the [HB100 module](https://theorycircuit.com/hb100-microwave-motion-sensor-interfacing-arduino/) separately.
