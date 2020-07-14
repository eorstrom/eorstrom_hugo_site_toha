---
title: "How I Converted My Existing Website to Use Hugo"
date: 2020-05-14T11:30:00-05:00
draft: false
hero: /assets/images/background/sunrise.jpg
author:
    name: Erin Orstrom
    image: /images/2016_05_19_NSS_Cohort_12_0274_T_cropped_246x246.jpg
---

I wanted to write this post as a guide on how I converted my website to use <a href='https://gohugo.io/' target='_blank'>Hugo</a>, a static site generator, in order to host blog posts without using a CMS like WordPress. When I was looking for resources and guides on how to build a Hugo site, nearly every resource I ran across was a guide on how to build a Hugo site from scratch. Which is great because that's where most people start from. However, because I already had an existing site, I couldn't follow many of these guides step-by-step and get the desired results. I scrapped and started over so many times I lost count. This guide may not work for everyone who wants to convert their site to use Hugo, and some of it is a little hackey I'll admit, but it's what worked for me.

These two blog posts were invaluable resources for me during this process:

<a href='https://medium.com/@pritamp/hugo-site-for-github-pages-end-to-end-guide-797de62b9892' target='_blank'>Hugo Site for Github pages — End to End Guide</a>
<a href='https://inside.getambassador.com/creating-and-deploying-your-first-hugo-site-to-github-pages-1e1f496cf88d' target='_blank'>Creating and deploying your first Hugo site to Github pages</a>
I'm not going to go step by step, since both blogs above do a really good job of walking you through how to create a Hugo site from scratch and the different commands you'll need to use, but I will point out differences in my process.

First, I saved the content from my current site that I wanted to transfer to the new site. I saved the files into a separate local folder so I could easily copy and paste what I wanted (text, etc.) without having to retype everything (even though I largely didn't use much of the content from the old site in the end anyway).

Next, I started a new Hugo site in a folder called eorstrom_hugo_site, and implemented the theme I wanted to use, which ended up being the <a href='https://themes.gohugo.io/personal-web/personal-web' target='_blank'>personal-web</a> theme. *Note*: once you pick a theme try to stick with it, as it's not easy to switch themes since each one is structured a bit differently, has different naming conventions, and other differences that make it a nuisance to switch themes. Try a few out on test Hugo sites before committing to one for your site.

Also, I would suggest forking the theme from its Github repo to your own and use that repo, so that you can make any changes you want to the theme. If you use the creator's repository, you can't make any changes without making a Pull Request.

Now, a bit of explanation before the next step, because this is something that confused me initially. You will need 2 separate repositories, one for your site changes with Hugo, and one for hosting your site on Github pages, since Github pages doesn't natively understand Hugo, which is written in <a href='https://golang.org/' target='_blank'>Google's Go programming language</a>. I already had the repository for hosting the static files for my site, so I just had to create the repo for the Hugo site changes and push my starting changes

I then deleted pretty much everything from my current site except for the CNAME and ReadMe.md files, since the structure wouldn't play well with Hugo's site structure and were no longer needed.

After you've made changes to your Hugo site, you have to generate new static files to push to your site's repository. To do this, the steps I took were to clone my site repo (https://github.com/eorstrom/eorstrom.github.io) into my Hugo site project, name the folder to public, and used the command

    hugo -t personal-web

Which generates the static files needed for your site, using the -t flag and the specified theme name to build the files with.

At this point, I am managing 3 different repositories within one project:

* Site repo (hosted with Github pages): https://github.com/eorstrom/eorstrom.github.io

* Hugo site repo: https://github.com/eorstrom/eorstrom_hugo_site

* Personal-web forked theme: https://github.com/eorstrom/personal-web

At first it was confusing because any changes I made showed up in the root of the project and I had to pay really close attention when grouping them in commits and make sure I was pushing the changes to the correct repositories, but it's gotten a lot easier to work with as I've made more changes to the site.

I added the public/ and themes/personal-web folders to my .gitignore file at the root of the project to help manage tracking the changes. Changes for each folder are still tracked in their individual repositories.

After pushing the newly generated static files to my eorstrom.github.io repository, and giving a few minutes for the site to refresh, boom! There was my website using Hugo with a new theme, fresh look, and updated content! 🎉 What a great feeling that was after two weeks of struggling with it! And I learned quite a bit in the process.

I'm not going to go into how I created blog posts or anything in this post, but this was how I got the Hugo structure and theme implemented and pushed to their respective repositories. Hopefully this helps others out there that are trying to convert an already existing site to use Hugo so they don't face the same struggles I did.

If anything in this post is unclear or if you have questions, please feel free to <a href="/contact/">contact me</a> or leave a comment on the LinkedIn post.
