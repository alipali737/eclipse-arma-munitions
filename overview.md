---
layout: page
title: Overview
permalink: /
nav_order: 0
---

# Overview Page
This documentation contains all the useful knowledge for the arma campaigns.

## Planes
{% assign planes = site.pages | where:"parent","Planes" %}
| Plane | Summary |
| :---: | :---: |
{% for plane in planes -%}
| [{{ plane.title }}]({{ plane.url | relative_url }}) | {{ plane.summary }} |
{% endfor %}

## Helicopters
{% assign helicopter = site.pages | where:"parent","Helicopters" %}
| Helicopter | Summary |
| :---: | :---: |
| test | test |
{% for helicopter in helicopters -%}
| [{{ helicopter.title }}]({{ helicopter.url | relative_url }}) | {{ helicopter.summary }} |
{% endfor %}

## Missiles

{% assign munition_types = "Air-to-Air, Ground-Attack" | split: ", " %}
{% for type in munition_types %}
| {{ type }} | Summary |
| :---: | :---: |
{%- assign munitions = site.pages | where:"parent",type -%}
{%- for munition in munitions %}
| [{{ munition.title }}]({{ munition.url | relative_url }}) | {{ munition.summary }} |
{%- endfor %}
{% endfor %}


