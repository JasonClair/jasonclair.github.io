---
title: "Dynamics CRM Cascading Drop Downs / Dependent Option Set"
last_modified_at: 2017-11-25T18:00:00-00:00
categories:
  - Dynamics
tags:
  - Useful Tips
  - JavaScript
header:
  teaser: /assets/images/posts/cascading_drop_down/CDD_FirstImage.png
classes: wide
---
A user asked if it would be possible to recreate cascading drop down lists like they had in SalesForce. I thought this would be an out of the box configuration and agreed that they could have it. Surprisingly, this doesn’t seem to be something that is out of the box – but handily Microsoft have published an excellent tutorial on MSDN about how to do this using JavaScript.

The tutorial by Microsoft is very useful, but I wanted to create one in my own words with a few more images to hopefully help newer members of the Dynamics community. I’ve not included the code in this blog in case Microsoft update the [MSDN](https://msdn.microsoft.com/en-us/library/gg594433.aspx){:target="_blank"} article with newer versions of the code.

In this example, I will be making a cascading drop down between the out of the box businesstypecode field and a new custom field called *new_businessspecialisation*.

## JSON

The code Microsoft provided uses JSON to manage the parent child relationships, this works well & is easy to create, but might become time consuming if the field values change regularly. It may be worth investigating whether there is another way to do this that provides the user with a front end to manage the relationships, but that was beyond the scope of this work.

## Setup

The JSON file will need to be uploaded as a web resource (of type JScript). The code provided by Microsoft will also need to be uploaded as a web resource.

{%
  include figure
  image_path="/assets/images/posts/cascading_drop_down/1_CDD_WebResource.png"
  alt="Adding the code as web resources"
  caption="Adding the code as web resources"
%}

Once the web resources have been created you will need to define the Form On Load functionality, to this simply add the library, enter the function name and pass in the name of your JSON file into the parameters. The script provided by Microsoft this will then concatenate this into a URL to load the source from.

{%
  include figure
  image_path="/assets/images/posts/cascading_drop_down/2_CDD_FormOnload.png"
  alt="Setting the onLoad event"
  caption="Setting the onLoad event"
%}

Once the Form On Load event has been created you will then need to create the On Change event for the parent field. This time you will need to pass in the name of the parent field & the name of the child field. In the Microsoft example they do this another as they have an extra level.

{%
  include figure
  image_path="/assets/images/posts/cascading_drop_down/3_CDD_OnChangeEvent.png"
  alt="Setting the field OnChange event"
  caption="Setting the field OnChange event"
%}

Once this has been done, everything should be good to go. The next couple of images show the functionality in action.

{%
  include figure
  image_path="/assets/images/posts/cascading_drop_down/4_CDD_NoValue.png"
  alt="Field locked because no parent Business Type has been chosen"
  caption="Field locked because no parent Business Type has been chosen"
%}

{%
  include figure
  image_path="/assets/images/posts/cascading_drop_down/5_CDD_Manufacturing.png"
  alt="Metal & Plastics showing for Manufacturing"
  caption="Metal & Plastics showing for Manufacturing"
%}

{%
  include figure
  image_path="/assets/images/posts/cascading_drop_down/6_CDD_AppDev.png"
  alt="Dynamics & SharePOint showing for Application Development"
  caption="Dynamics & SharePOint showing for Application Development"
%}

## Summary

Overall, thanks to the Microsoft sample code this proves to be a relatively simple piece of functionality to add that potentially provides a lot of value to the end user.
