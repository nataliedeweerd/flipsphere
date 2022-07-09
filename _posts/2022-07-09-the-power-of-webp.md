---
layout: post
title: "The Power of WebP"
subtitle: "How WebP can make your site load faster, and help save the planet."
date: 2022-07-09
---

## What is WebP?

WebP is an image format for the web created by Google. It provides superior compression which outputs high quality images on average 25% smaller than other formats.

## How to save as WebP

You can save straight to WebP in Photoshop by going to File > Saves as... > and selecting WebP from the file type dropdown.

If you don't have Photoshop, you can use an online converter such as [cloudconvert.com](https://cloudconvert.com/).

## Real Example

I've recently relaunched my wallpaper design site [divine-designs.net](https://www.divine-designs.net/). The homepage is very image heavy, and whilst the site was loading very quickly in my local environment, when I pushed it to production it slowed to a crawl. 

I'm running on a shared hosting server, so I knew it was always going to be slow (hence the decision to go purely frontend), however at almost 10 seconds loading time it was _too_ slow. 

I could just move it onto a different hosting provider, maybe even host it on AWS, however that doesn't solve the crux of the problem. So I needed to review and optimise my code, and as it's an image heavy site, I decided to start there.

**The homepage was loading 53MB of images.**

That number needed to come down. I was loading the wallpapers at their full size, in JPG format. So I opened photoshop, resaved them all at only 1000px wide (which is the largest the thumbnails sit at) and also saved them as WebP.

**This dropped the image load to 1.68MB!** That's a reduction of 96.84%!!

The site now loads in around 1 second.

## Why is this important?

Aside from the obvious of making your website load quicker, it also reduces the amount of CO2 required to load your website and with the communications industry predicted to use 20% of all the world’s electricity by 2025, as developer's we all have a duty to keep our CO2 as low as possible.

Currently divine-designs.net produces only [0.41g of CO2 per page load](https://www.websitecarbon.com/website/divine-designs-net/).
