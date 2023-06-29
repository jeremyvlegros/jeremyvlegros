---
title                    : "Custom page"
layout                   : "custom_page"
content_description      : "testing my custom layout"
date_of_creation         : "#date 2023-06-29 16:53 1688043201580071656 GMT"
date_of_modification     : null
color_background         : 2
category                 : "test"
tags                     : "#test #page #layout #post" 
meta_image_url           : null
type                     : "post"
---

# Getting the first image URL

{% assign string_image_color_urls = site.string_image_color_urls %}

{% assign array_image_color_urls = string_image_color_urls | split : "," %}

<!-- images start at 1 for covenience -->
`{{ array_image_color_urls[1] }}`


# Title 2
