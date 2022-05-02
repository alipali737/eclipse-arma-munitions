---
layout: page
title: O-2A Skymaster
parent: Planes
summary: Military version of the Cessna 337 Super Skymaster.
---

# {{ page.title }}
The **O-2A Skymaster** is a military version of the Cessna 337 Super Skymaster. It is a twin-engine piston-powered aircraft. Often used for reconnaissance missions or psychological operations.

![{{ page.title }} Top Down]({{ site.baseurl }}/assets/O-2A_Skymaster/top_down.jpg)

### Vehicle Specifications

| Stat | Value |
|:-----:|:-----:|
| Nationality | American |
| Speed Class | Propeller |
| Engine Class | Propeller |
| Airbrake | ❌ |
| Active Radar | ❌ |
| Seats | 4 |
| Takeoff Speed | 110 km/h |
| Landing Speed | 90 km/h |
| Tailhook | ❌ |
| Retract Wings | ❌ |

# Vehicle Capabilities

| Role | Availability |
|:-----:|:------------:|
| Fighter | ❌ |
| Ground Attack | ❌ |
| Bomber | ❌ |
| Reconnaissance | ✔️ |
| Transport | ✔️ |
| Cargo | ❌ |

# Vehicle Pylons

![{{ page.title }}} Pylons]({{ site.baseurl }}/assets/O-2A_Skymaster/pylons.jpg)

{%- assign munitions = "" | split: "" -%}

{%- for current_page in site.pages -%}
{%- assign page_used_by = current_page.used_by | split: ", " -%}
{%- if page_used_by contains page.title -%}
{%- assign munitions = munitions | push: current_page -%}
{%- endif -%}
{% endfor %}

| Pylon Type | Number of Pylons |
| :---: | :---: |
{%- assign munition_types = "Air-to-Air, Ground-Attack" | split: ", " -%}
{%- for munition_type in munition_types -%}
{%- assign count = 0 -%}
    {%- for munition in munitions -%}
        {%- if munition.parent == munition_type -%}
            {%- assign count = count | plus: 1 -%}
        {%- endif -%}
    {%- endfor %}
    | {{ munition_type }} | {{ count }} |
{%- endfor %}

{% assign munitions = munitions | sort: "parent" %}

| Name | Purpose | Details |
| :---: | :---: | :---: |
{% for munition in munitions -%}
| [{{ munition.title }}]({{ munition.url | relative_url }}) | {{ munition.parent }} | {{ munition.summary }} |
{% endfor %}

