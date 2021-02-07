---
title: "How product safety certification could save your life"
header:
tags: [engineering,product,management,hardware,startups]
---
Have you ever looked at the backside of a kid's toy, your toaster oven, or a pre-2014 iPhone like mine to find a series of strange icons or some alphanumeric code?
{% capture fig_img %}
![Foo]({{ "/assets/img/120502020/safety_certs.png" | relative_url }})
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>Welcome to the world of product safety certification! 👹</figcaption>
</figure>

Usually these marks are pretty boring, standard stuff that just confirms that a product has met basic requirements to be sold in-country. Now that I am in the middle of getting an electronic product certified, I am forced to think about worst-case-scenarios and how people will ultimately use my product. This gets me to thinking what the world would be like *without* the agencies that certify physical products. Taking a look at the stats from the Consumer Product Safety Commission, each year in the US there are [>20,000 deaths, 30 million injuries](https://krupplawfirm.com/dangerous-defective-products/) and [$1 trillion in economic losses](https://unctad.org/news/unsafe-consumer-products-cost-us-economy-1-trillion-each-year) due to defective or poorly designed products.

Imagine you just got up in the morning, your eyesight still blurred from a restful sleep, stumbling into the kitchen to pop a breakfast burrito into the microwave, when all of a sudden you're running for the fire extinguisher because you have never cleaned the microwave and 3 years of grease and crumbs have sparked and caused a fire! If only your microwave had been tested and certified to [UL923](https://www.intertek.com/standards-updates/ul-923-microwave-cooking-appliances/) you wouldn't be crying on your kitchen floor covered in fire extinguisher residue. The 125 year history of product safety standards are meant to prevent these sorts of incidents. In fact, Underwriters Laboratories was started to keep the 1893 Chicago World's Fair from burning down.

Most of the costliest product recalls in modern history occurred in just the last 20 years, often in the auto industry.
* Toyota accelerator pedals getting stuck in the floormat (2010, $3.2B)
* GM ignition switch failures, disabling power steering, brakes (2014, $4.1B)
* Samsung Galaxy Note 7 bursting into flames (2016, $5.3B)
* Firestone/Ford defective tires (2000, $5.6B)
* Volkswagen diesel cheating scandal (2015, $18.3B)
* Takata airbag recall (2008-present, $24B, 100 milllion airbags affected)

So how do you actually get a new product certified to be "safe" and who gives you the stamp of approval? In the mid-20th Century, OSHA regualtions made specific reference to two private testing bodies (UL & FM), but a lawsuit in 1983 forced them to remove those references and the Cambrian Explosion of Nationally Recognized Testing Laboratories (NRTLs) began. Now there are something like 16 NRTLs to choose from and 125 sites to get your new product tested and approved.

{% capture fig_img %}
![Foo]({{ "/assets/img/120502020/The-spread-of-flame-test.jpg" | relative_url }})
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>This test is going smoothly.</figcaption>
</figure>

Now the tricky part can be navigating the maze of regulations to determine what actually applies to your product, so you can do some in-house verification before you pay a lab to look at it and deny your application. There is a specialized world of safety certification consultants out there that can help identify the relevant regs and give you a pre-certification checklist on your design. Paying the premium for one of these consultants is definitely worth it, since it could save you many months and help get your product to market faster. Either way, expect at least a 3-6 month certification process, depending on lab availability and how many regulations apply. Certification will take longer if you plan to install your product in a hazardous environment, with explosive gases and the like.

One quirky gray area of meeting product certification requirements is the area of "reasonably forseeable misuse". Take, for example ISO 14971 for medical devices. Forseeable misuse was defined there as:
>Use of a product or system in a way not intended by the manufacturer, but which can result from readily predictable human behaviors.

Now, the casual reader might be skeptical, when noticing their toddler taking a carefully designed Apple AirPod and stuffing it up their nose. Prediction of human behavior is after all one of the cornerstones of psychology, in fact there's a whole field researching how human behavior affects interaction with physical and software products. It's called [Human Factors Engineering](https://www.apa.org/action/science/human-factors) and a quick search on Indeed turned up 2,543 listed openings. Ultimately it falls to the courts to determine if a manufacturer should have reasonably forseen use of their product, hence why I call this a quirky gray area.

At [Kuva Systems](www.kuvasystems.com), we need to be able to navigate these certification issues since we're installing equipment for use in the oilfield to reduce global methane emissions. In fact, any technology developer in the cleantech space needs to understand certification requirements if they want to scale and bring our energy infrastructure into the 21st Century. Everything from power generation equipment, new mobility systems (e.g. [electric bikes](https://time.com/5925286/e-bikes-parking-lanes/)), and low-carbon steel and concrete will all need to meet existing and future rules for safe operation over a 10, 20, 50 year lifespan.

Software may still be eating the world, but safety-certified hardware products are rebuilding it.
