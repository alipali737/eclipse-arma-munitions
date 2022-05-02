---
layout: page
title: AH-1G Cobra
parent: Helicopters
summary: An American single-engined attack helicopter.
---

# {{ page.title }}
The **AH-1G Cobra** is a single-engine attack helicopter. It is primarily used for ground attack missions or providing escort to transport helicopters or other assets. It has a tandem cockpit, stub wings for weapons, and a chin-mounted gun turret.

![{{ page.title }} Top Down]({{ site.baseurl }}/assets/AH-1G_Cobra/top_down.jpg)

### Vehicle Specifications

| Stat | Value |
|:-----:|:-----:|
| Nationality | American |
| Rotor Count | 1 |
| Active Radar | ✔️ |
| Seats | 2 |

# Vehicle Capabilities

| Role | Availability |
|:-----:|:------------:|
| Fighter | ❌ |
| Ground Attack | ✔️ |
| Reconnaissance | ❌ |
| Transport | ❌ |
| Cargo | ❌ |

# Vehicle Pylons

**Pylons non-configurable**

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

