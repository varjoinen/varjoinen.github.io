---
title: 'Updating the site'
slug: 'updating-the-site'
#image: 'images/bg.jpg'
date: '2018-06-16T00:00:00'
description: 'It is time to refresh'
---

# Time to refresh

I have updated the site, once again. There has been some bigger changes under
the hood:

  * The site has been moved to [Github pages](https://pages.github.com/)
  * I have migrated content from my [Medium account](https://medium.com/@varjoinen)
    to the site
  * I have automated publishing with [Hugo](https://gohugo.io/),
    [Github](https://github.com/) & [Travis](https://travis-ci.org/)

## Want hear about the migration?

Lately I have been pondering about publishing new writings and how to do that
easily. Medium is kind of an easy platform for writing & publishing but I don't
like their tkae on [GDPR](https://www.eugdpr.org/) "compliance". On the other
hand I do not like overly complicated blogging or CMS platforms.

After some searching I stumbled upon [Hugo](https://gohugo.io/). Long story
short I created a deployment pipeline with [Travis](https://travis-ci.org/)
and [Github](https://github.com/).

There is a great [how-to](https://www.metachris.com/2017/04/continuous-deployment-hugo---travis-ci--github-pages/)
by Chris Hager, I just decided to put my source codes to different branch and
publish the compiled files to master because Github does not allow to use
gh-pages branchs for publishing individuals sites.