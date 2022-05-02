---
layout: page
title: A-6A Intruder
parent: Planes
summary: An American twinjet all-weather attack aircraft designed for Marine close air support.
---

# {{ page.title }}
The **A-6A Intruder** is an American twinjet all-weather Navy long-range attack/interdiction aircraft designed for Marine close air support. It has short takeoff and landing (STOL) capability allowing it to be used for carrier-based operations. Pilot and gunner are sat in a side-by-side-seating configuration.

![{{ page.title }} Top Down]({{ site.baseurl }}/assets/A-6A_Intruder/top_down.jpg)

### Vehicle Specifications

| Stat | Value |
|:-----:|:-----:|
| Nationality | American |
| Speed Class | Subsonic |
| Engine Class | Jet |
| Airbrake | ✔️ |
| Active Radar | ✔️ |
| Seats | 2 |
| Takeoff Speed | 180 km/h |
| Landing Speed | 145 km/h |
| Tailhook | ✔️ |
| Retract Wings | ✔️ |

# Vehicle Capabilities

| Role | Availability |
|:-----:|:------------:|
| Fighter | ❔ |
| Ground Attack | ✔️ |
| Bomber | ✔️ |
| Reconnaissance | ❌ |
| Transport | ❌ |
| Cargo | ❌ |

# Vehicle Pylons

![{{ page.title }}} Pylons]({{ site.baseurl }}/assets/A-6A_Intruder/pylons.jpg)

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

