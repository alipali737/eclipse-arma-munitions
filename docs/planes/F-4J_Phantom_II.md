---
layout: page
title: F-4J Phantom II
parent: Planes
summary: American two-seater, twin-engine, all-weather, long-range supersonic jet interceptor and fighter-bomber.
---

# F-4J Phantom II
This jet is an american two-seater, twin-engine, all-weather, long-range supersonic jet interceptor and fighter-bomber.

![F-4J Phantom II Top Down]({{ site.baseurl }}/assets/F-4J_Phantom_II/top_down.jpg)

### Vehicle Specifications

| Stat | Value |
|:-----:|:-----:|
| Nationality | American |
| Speed Class | Supersonic |
| Engine Class | Jet |
| Airbrake | ✔️ |
| Active Radar | ✔️ |
| Seats | 2 |
| Takeoff Speed | 250 km/h |
| Landing Speed | 130 km/h |
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

![F-4J Phantom II Pylons]({{ site.baseurl }}/assets/F-4J_Phantom_II/pylons.jpg)

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
