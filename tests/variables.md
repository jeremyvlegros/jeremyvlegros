---
title                : null
content_description  : null
date_of_creation     : null
date_of_modification : null
post_color           : null
category             : null
tags                 : null
meta_image_url       : null
---

<!-- LIQUID -->

<!--   DECLARATION -->

{% assign title                = page.title %}
{% assign content_description  = page.content_description %}
{% assign date_of_creation     = page.date_of_creation %}
{% assign date_of_modification = page.date_of_modification %}
{% assign tags                 = page.tags %}
{% assign meta_image           = null %}
{% assign page_url             = site.url | append :"/" | append : site.name | append : "/" | append : page.url%}

<!--   INITILISATION -->

<!-- default date
-->
{% if not date_of_creation %}
{% assign date_of_creation      = "2023-05-19T00:00:00+00:00"%}
{% endif %}

{% if not date_of_modification %}
{% assign date_of_modification  = "2023-05-19T00:00:00+00:00"%}
{% endif %}

<!-- title
-->
{% if title %}
{% assign title = title | escape | replace : " &gt;","&nbsp;&gt;" %}
{% endif %}


<!--   PROCESSING
 -->

{% assign title                = title | escape %}

<!--   PROCESSING > DATE
 -->

<!--     input                        = "#date 2023-06-28 05:16 1687914994970097614 GMT"
         output                       =       "2023-06-28T05:16:00+00:00"

-->

<!--     removing "#date " and " GMT"
                                 => "2023-06-28 05:16 1687914994970097614"
-->
{% assign date_of_creation       =  date_of_creation     | replace : "#date ","" | replace " GMT",""%}
{% assign date_of_modification   =  date_of_modification | replace : "#date ","" | replace " GMT",""%}

<!--     split date in array
                                => "[2023-06-28, 05:16, 1687914994970097614]"
-->
{% assign date_of_creation      =  date_of_creation     | split:" "%}
{% assign date_of_modification  =  date_of_modification | split:" "%}

<!--     getting time
                                => 05:16
-->

{% assign time_of_creation      =  date_of_creation[1]    %}
{% assign time_of_modification  =  date_of_modification[1]%}

<!--    hour with seconds and Time difference
I won't calculate the seconds ... for now ?
                               => "05:16:00+00:00"
-->

{% assign time_of_creation     =  time_of_creation     | append :":00+00:00" %}
{% assign time_of_modification =  time_of_modification | append :":00+00:00" %}

<!--      adding 'T' and hour to date
                               => "2023-06-28T05:16:00+00:00"
                      reference   "2023-06-28T05:16:00+00:00"
-->
<!--                               2023-06-28                          T             05:16:00+00:00
-->
{% assign date_of_creation      =  date_of_creation[0]     | append : "T" | append : time_of_creation%}
{% assign date_of_modification  =  date_of_modification[0] | append : "T" | append : time_of_modification%}


<!-- META IMAGE
-->

{% if meta_image_url %}
{% meta_image = "<meta name='twitter:image' content='{{meta_image_url}}'/>"%}
{% endif %}


<!-- END LIQUID -->

<!DOCTYPE html>
<!--suppress ALL -->
<html lang="en'">

<head>
    <!--suppress HtmlUnknownAttribute -->

    <!-- META COMMON -->

    <meta charset="utf-8">

    <meta http-equiv="X-UA-Compatible"
          content="IE=edge">

    <meta name="viewport"
          content="width=device-width, initial-scale=1">

    <meta name="description"
          content="{{page.content_description}}"/>

    <meta property="article:published_time"
          content="{{date_of_creation}}"/>

    <!--  META OPEN GRAPH  -->

    <meta property="og:title"
          content="{{title|escape}}"/>

    <meta property="og:locale"
          content="en_US"/>

    <meta property="og:description"
          content="{{page.content_description}}"/>

    <meta property="og:url"
          content="{{page.url}}"/>

    <meta property="og:site_name"
          content="{{site.name}}"/> <!-- need to check that -->

    <meta property="og:type"
          content="article"/>

    <!--  META TWITTER  -->

    <meta name="twitter:card"
          content="summary"/>
    <meta property="twitter:title"
          content="{{page.title|escape}}"/>

    <!--  LINK CANONICAL -->

    <link rel="canonical"
          href="{{page.url}}"/>

    <!--  STYLE SHEET -->

    <link rel="stylesheet"
          href="/assets/main.css">

    <!--  PAGE TITLE -->

    <title>{{page.title|escape}}</title>

</head>

<body>

<main class="page-content" aria-label="Content">

    <article class="post {{page.post_color}}" itemscope itemtype="http://schema.org/BlogPosting">

        <header class="post-header">
            <h1 class="post-title" itemprop="name headline">{{ page.title | escape }}</h1>
        </header>

        <div class="post-content" itemprop="articleBody">
            {{ content }}
            {% if page.date_of_creation %}
            <span class='date date_of_creation'>Created&nbsp;&nbsp;: {{ page.date_of_creation }} </span>
            {% endif %}

            <br>
            {% if page.date_of_modification %}
            <span class="date date_of_modification">Modified&nbsp;: {{ page.date_of_modification }} </span>
            {% endif %}
        </div>

    </article>

</main>

</body>

</html>
