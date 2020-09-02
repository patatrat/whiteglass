---
layout: post
title: "Building static sites with Jekyll on AWS S3"
categories: Projects
tags: AWS Website
keywords: AWS, jekyll, whiteglass, Cloud Native
author: Patrick
excerpt_separator: <!--more-->
---

My goal with this website was to have something simple, easy to set up and that didn't require a whole lot of attention, maintenance or on-going cost. So, now that I've got it going - I thought I'd do a quick write up of it all. 

<!--more-->

## Ingredient list
The simplest way to achieve this was to use a server-less approach with a static site hosted in AWS S3 buckets. These are the main ingredients to doing something like this yourself:

 - A static site hosted on [AWS S3 buckets](https://aws.amazon.com/s3/?did=ft_card&trk=ft_card) and served with CloudFront. Following this [simple AWS developer guide](https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html) will get you up and running quickly.
 - [Jekyll](https://jekyllrb.com/), a [Ruby](https://www.ruby-lang.org/en/) based, static website generator. If you are completely new to this stuff, there are a number of things to install first. There are handy, [operating specific guides](https://jekyllrb.com/docs/installation/#requirements) which lay out everything you need to do.  
 - A Jekyll Template - there are [plenty](http://jekyllthemes.org/) out there, I used [Whiteglass](https://github.com/yous/whiteglass), as it was super simple design with little faffing about.
 - Source code management from github. This makes it ultra simple to use most Jekyll themes - simply fork the theme you want and then clone it to your desktop to start building. 
 - A [contact me form](/contact/) provided by [GetForm.io](https://getform.io/). This is a great free way to add forms to static websites without having to mess around with custom CSS, iframes etc. and you can set up email notifications for each submission. This is a simple solution to avoiding putting your email address out on the web for spammers to pick up. 
 - [s3_website](https://github.com/laurilehmijoki/s3_website) - a handy way to manually deploy your Jekyll site to your s3 buckets. There are other ways to do this - you could get fancy with a pipeline from github to AWS and run automated builds, but this was a fairly simple way for me to do it. One word of caution - the config file for the s3_website contains secret information - you'll want to keep that safe and exclude it from being included in any public repository, otherwise anyone could get control of your site. 
 
## Getting started with Jekyll

Once everything is installed, open up a terminal window and type

 ```code
 jekyll new myblog
  ```
This will create the site called 'myblog' (go ahead and change that to whatever you want) in the directory myblog. 

Change to that directory:

 ```code
 cd myblog
  ```

And then build the new site:

 ```code
 bundle exec jekyll serve
  ```
 
 This will create the site and host it locally on [http://localhost:4000](http://localhost:4000). You can then start playing around with themes, making changes to the design etc and seeing the results as soon as you make them on your local machine. 
 
 
## Cost
 
 In terms of cost - I am well within the '[free tier](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc)' for S3 bucket usage and barring me suddenly becoming much more popular, I'll probably never go out of it - so hosting is pretty much free. It does cost me around about $25 USD per year for the domain and 50 cents US a month for the Route 53 hosted zone. The other great thing is, because it is globally distributed with CloudFront, if I did suddenly become massively popular, the site will automatically scale and not get hugged to death. 
 
## Alternative ways of doing this 
There is probably a simpler way of doing this- using [github pages](https://pages.github.com/), and if all you are after is a quick and easy site, then this would be the best way - but I wouldn't have learnt about buckets, cloudfront logging and a bunch of other AWS stuff if I did that...

## Future plans
 - Fun with subdomains. Since these sites are so simple to get up and running, I'd like to try making a few subdomain sites, maybe a cv.radomski.co.nz for a CV site I can share, or a stand-alone photoblog.
 - Extend the site - there are plenty of plugins for Jekyll (although none of these will work on Github pages) to extend the functionality of your site. 
 - Other AWS services. I'm keen to try out some of the other serverless platforms and try some personal projects.