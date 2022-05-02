---
layout: page
title: A-1H Skyraider
parent: Planes
summary: American piston-engine, single-seat attack aircraft used from 1946 to early 1980s.
---

# {{ page.title }}
This aircraft is an old aircraft developed in the 1940s as a single-seat, long-range, high performance dive/torpedo bomber attack aircraft. It is powered by a piston-engine propeller but is still a very capable aircraft for its age.

![{{ page.title }} Top Down]({{ site.baseurl }}/assets/A-1H_Skyraider/top_down.jpg)

### Vehicle Specifications

| Stat | Value |
|:-----:|:-----:|
| Nationality | American |
| Speed Class | Subsonic |
| Engine Class | Propeller |
| Airbrake | ✔️ |
| Active Radar | ❌ |
| Seats | 1 |
| Takeoff Speed | 100 km/h |
| Landing Speed | 90 km/h |
| Tailhook | ✔️ |
| Retract Wings | ✔️ |

# Vehicle Capabilities

| Role | Availability |
|:-----:|:------------:|
| Fighter | ✔️ |
| Ground Attack | ✔️ |
| Bomber | ✔️ |
| Reconnaissance | ✔️ |
| Transport | ❌ |
| Cargo | ❌ |

# Vehicle Pylons

![{{ page.title }}} Pylons]({{ site.baseurl }}/assets/A-1H_Skyraider/pylons.jpg)

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

