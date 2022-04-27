---
layout: page
title: <plane-name>
parent: Planes
summary: <plane-summary>
---

# {{ page.title }}
<plane-description>

![{{ page.title }} Top Down]({{ site.baseurl }}/assets/<plane-folder>/top_down.jpg)

### Vehicle Specifications

| Stat | Value |
|:-----|:-----:|
| Nationality | - |
| Speed Class | - |
| Engine Class | - |
| Airbrake | - |
| Radar | - |
| Seats | - |
| Takeoff Speed | 0 km/h |
| Landing Speed | 0 km/h |
| Tailhook | - |
| Retract Wings | - |

# Vehicle Capabilities

| Role | Availability |
|:-----|:------------:|
| Fighter | - |
| Ground Attack | - |
| Bomber | - |
| Reconnaissance | - |
| Transport | - |
| Cargo | - |

# Vehicle Pylons

![{{ page.title }}} Pylons]({{ site.baseurl }}/assets/<plane-folder>/pylons.jpg)

{%- assign munitions = "" | split: "" -%}

{%- for current_page in site.pages -%}
{%- assign page_used_by = current_page.used_by | split: ", " -%}
{%- if page_used_by contains page.title -%}
{%- assign munitions = munitions | push: current_page -%}
{%- endif -%}
{% endfor %}

| Pylon Type | Number of Pylons |
| :---: | :---: |
{%- assign munition_types = "Air-to-Air, Ground Attack" | split: ", " -%}
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
{%- endfor %}

