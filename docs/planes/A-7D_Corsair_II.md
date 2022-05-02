---
layout: page
title: A-7D Corsair II
parent: Planes
summary: American carrier-capable light attack aircraft.
---

# {{ page.title }}
The **A-7D Corsair II** is a single-seat carrier-capable light attack aircraft that can be used for close air support or air-to-air combat operations.

![{{ page.title }} Top Down]({{ site.baseurl }}/assets/A-7D_Corsair_II/top_down.jpg)

### Vehicle Specifications

| Stat | Value |
|:-----:|:-----:|
| Nationality | American |
| Speed Class | Subsonic |
| Engine Class | Jet |
| Airbrake | ✔️ |
| Active Radar | ✔️ |
| Seats | 1 |
| Takeoff Speed | 180 km/h |
| Landing Speed | 140 km/h |
| Tailhook | ✔️ |
| Retract Wings | ✔️ |

# Vehicle Capabilities

| Role | Availability |
|:-----:|:------------:|
| Fighter | ✔️ |
| Ground Attack | ✔️ |
| Bomber | ✔️ |
| Reconnaissance | ❔ |
| Transport | ❌ |
| Cargo | ❌ |

# Vehicle Pylons

![{{ page.title }}} Pylons]({{ site.baseurl }}/assets/A-7D_Corsair_II/pylons.jpg)

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

