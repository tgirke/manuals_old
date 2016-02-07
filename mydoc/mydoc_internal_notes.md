---
title: Internal Notes
tags: [formatting]
keywords: navigation tabs, hide sections, tabbers, interface tabs
last_updated: February 06, 2016
summary: "Internal notes to maintain this site."
---

## Built and test site locally
Run following command within `~/Dropbox/Websites/manuals` directory and then preview the site at the preview URL shown.

{% highlight bash %}
jekyll serve --config configs/mydoc/config_designers.yml
{% endhighlight %}

## Site configuration
Edit this file accordingly.

{% highlight bash %}
configs/mydoc/config_designers.yml
{% endhighlight %}

## How to add a new page

1. Add page to `mydoc` *e.g.* `mydoc/mydoc_mypage.md`

2. Change sidebar and URL configuration files accordingly

{% highlight bash %}
_data/mydoc/mydoc_sidebar.yml
_data/mydoc/mydoc_urls.yml
{% endhighlight %}

## Sync changes with `gh-pages` branch using `rsync`

{% highlight bash %}
git checkout gh-pages
rsync -avh --stats --progress ~/Dropbox/Websites/doc_outputs/mydoc/designers/ ~/Dropbox/Websites/manuals/
git add .
git commit -am "some edits"; git push -u origin master
{% endhighlight %}

## Commit to GitHub
{% highlight bash %}
git checkout gh-pages
git commit -am "some edits"; git push -u origin master
git checkout master
git commit -am "some edits"; git push -u origin master
{% endhighlight %}


## Check differences in directories
One can also double-check by downloading the changes from GitHub and then run `diff`

{% highlight bash %}
diff -r ~/Dropbox/Websites/doc_outputs/mydoc/designers/ ~/Dropbox/Websites/manuals/
{% endhighlight %}





