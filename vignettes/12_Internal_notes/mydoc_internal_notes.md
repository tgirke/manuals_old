---
title: Administration of site
keywords: navigation tabs, hide sections, tabbers, interface tabs
last_updated: February 06, 2016
summary: "Internal notes for maintaining this site."
---

## How to create a new instance of this site

1. Create a new project repository on GitHub and give it any name. For instance, the project 
described here was named `manuals`. This initial setup will be the project's `master` branch. After this is done, clone the new repostitory to your 
local computer. If you are new to GitHub [here](https://guides.github.com/activities/hello-world/) are some basic instructions for creating 
and managing GitHub repositories

2. Download or clone the [Jekyll Documentation Theme](https://github.com/tomjohnson1492/documentation-theme-jekyll)
from Tom Johnson. Then copy the directory's content to your new project repository (here `manuals` directory).
Subsequently, commit and push its entire content to the `master` branch on GitHub.

3. Add a `gh-pages` branch to your newly created GitHub project repository.
By adding a `gh-pages` branch to a GitHub project, one can host from this branch 
a web site (here Jekyll site) for a GitHub project repository. The `master` branch of this
project contains the source code of the site and its `gh-pages` branch the pre-built web 
site components. Instruction for setting up a `gh-pages` branch for an existing project 
are available [here](https://help.github.com/articles/creating-project-pages-manually/).

## Edit a page

### Built and test site locally
Run following command within the root directory of the project's git repository
(here `~/Dropbox/Websites/manuals`) and then preview the site at the URL
printed to the terminal. Note, all paths are given here relative to this
directory.

{% highlight bash %}
jekyll serve --config configs/mydoc/config_designers.yml
{% endhighlight %}

{{site.data.alerts.note}} 
The built directory of the site is '../doc_outputs/mydoc/designers'. The changes are 
committed automatically when previewing the site with 'jekyll serve' or by executing the 'mydoc_*.sh' bash 
script(s) located in the root directory of the project.
{{site.data.alerts.end}}

### Edit site in `master` branch
Edits should be made in the project's [master](https://github.com/tgirke/manuals/tree/master) 
branch and then committed from there to the corresponding branch on GitHub.

{% highlight bash %}
git checkout master
vim ./mydoc/mydoc_some_page.md # Make changes to *.md pages in ./mydoc/
git commit -am "some edits"; git push -u origin master
{% endhighlight %}

### Sync changes to `gh-pages` branch
Currently, the changes to `../doc_outputs/mydoc/designers` need to be synced into the 
[gh-pages](https://github.com/tgirke/manuals/tree/gh-pages) branch of the project repository. The following accomplishes this with
`rsync`. The last two lines add, commit and push all changes to the `gh-pages` branch.
After this the changes should show up in the life version of the web site. Note, prior to
the syncing, one usually wants to shut down the locally running Jekyell server with
`Ctrl-c` in its terminal window.

{% highlight bash %}
git checkout gh-pages
rsync -avh --stats --progress ~/Dropbox/Websites/doc_outputs/mydoc/designers/ ~/Dropbox/Websites/manuals/
git add -A :/
git commit -am "some edits"; git push -u origin gh-pages
git checkout master
{% endhighlight %}

### Bash script for automation
To automate the above workflow, run the following `buildAll.sh` bash script
from the root directory of the repository's master branch.
{% highlight bash %}
./buildAll.sh
{% endhighlight %}

## Adding a new page

### Create page
The easiest is usually to copy an existing page in `\mydoc` and then make the necessary 
changes to its Jekyll front matter section and content.

### Sidebar and URL configuration
Next, the new page needs to be registered properly in the sidebar and URL configuration 
files.

{% highlight bash %}
vim _data/mydoc/mydoc_sidebar.yml
vim _data/mydoc/mydoc_urls.yml
{% endhighlight %}

After this the new page should be viewable in the local preview of your
browser.  This requires a running session of `jekyll serve ...` in the root
directory of the repository as shown above.

### Commit to GitHub
Similar as above add, commit and push changes to the `master` and `gh-pages` branches 
of the local and remote repositories or just run `buildAll.sh`.

{% highlight bash %}
git checkout master
git commit -am "some edits"; git push -u origin master
git checkout gh-pages
rsync -avh --stats --progress ~/Dropbox/Websites/doc_outputs/mydoc/designers/ ~/Dropbox/Websites/manuals/
git add -A :/
git commit -am "some edits"; git push -u origin gh-pages
git checkout master
{% endhighlight %}

## Set theme color
Pick you favorite color [here](http://www.december.com/html/spec/color3.html), then apply changes at the proper 
lines in `./css/theme-blue.css`. This task can be greatly simplified by using `vimdiff`:

{% highlight bash %}
vimdiff css/theme-blue.css css/theme-blue_orig.css
{% endhighlight %}

## R markdown integration

(1) Write R markdown vignette (`*.Rmd` file) in `./vignettes` directory (*e.g.* `./vignettes/Rbasics`).

(2) Render vignette to `.md` and `.html` files with `rmarkdown::render()`.

(3) Append `.md` file (here `Rbasics.knit.md`) to corresponding `.md` file in `./mydoc` directory.

(4) Remove front matter genereted by R markdown, but leave the one required for Jekyll

(5) Replace chode chunk tags to the ones required by Jekyll Doc Theme

(6) Move images into proper directory and adjust their path in the `.md` file

Run steps (2)-(6) with one command using the `render()` function and the `md2jekyll.R` script:

{% highlight bash %}
echo "rmarkdown::render('Rbasics.Rmd', clean=FALSE)" | R --slave; R CMD Stangle Rbasics.Rmd; Rscript ../md2jekyll.R Rbasics.knit.md 3
{% endhighlight %}

## Usage of custom domain

+ Register a domain name with a provider such as [GoogleDomains](https://domains.google) or [GoDaddy](https://www.godaddy.com). 
+ Next, configure the domain settings on your provider's website to point to GitHub pages. Sample instructions for GoogleDomains and GitHub pages are given on [Curtis Larson's Blog](http://www.curtismlarson.com/blog/2015/04/12/github-pages-google-domains/). Note, if you run a web site under the `gh-pages` branch of a GitHub project repository then you will still just use `username.github.io.` under the CNAME entry (see table below) without appending the name of the project repository. Also adding a dot at the end of this entry is important. The table below is an example how the settings would look like under the `DNS` tab on GoogleDomains. The two IP addresses in the first two lines of the table should be the same for all sites hosted on GitHub.


    |Name   |Type     | TTL | Data                |
    |---------------------------------------------|
    |   @   |    A    | 1h  | 192.30.252.153      |
    |       |         |     | 192.30.252.154      |
    |  www  |  CNAME  | 1h  | username.github.io. |
    |---------------------------------------------|


+ Subsequently, add the domain name (_e.g._ `mydomain.org`) associated with this entry to the CNAME file in the `gh-pages` branch of your GitHub project repository. 
+ Very important, if you experience any rendering problems on GitHub, check whether the `_config.yml` file of your Jekyll site contains a line starting with `baseurl: "..."`. If so remove this line or the page will not render properly on GitHub. 

## Favicon icon

A favicon is an icon displayed in the web site tabs of a browser or next to the site name in a 
bookmark list. The source image can be generted with most graphics programs (_e.g._ in SVG 
format in Inkscape). To generate the final favicon, the image needs to be exported in bitmap format
(_e.g._ PNG format) to a file. Subsequently, this file is converted to the final `favicon.ico` file 
using one of the many favicon generation tools such as [FavIcon Generator](http://tools.dynamicdrive.com/favicon). 
The `favicon.ico` file is then placed into the `images` directory of the Jekyll Doc Theme. 


## Useful utilities

### Site-wide configurations
Edit this file accordingly.

{% highlight bash %}
configs/mydoc/config_designers.yml
{% endhighlight %}

### Change sidebar behavior
The fixed sidebar is a nice feature of this theme. However, if there are too many
section entries then it may be desirable to switch contitionally to a floating behavior 
depending on the size of the viewport available on a system. This can be achieved by 
changing the height value in 'js/customscripts.js' to a larger value (_e.g._ 800 to 1200): 

{% highlight bash %}
if (h > 800) {
    $( "#mysidebar" ).attr("class", "nav affix");
}
{% endhighlight %}

### Check differences in directories
One can also double-check by downloading the changes from GitHub and then run `diff`

{% highlight bash %}
diff -r ~/Dropbox/Websites/doc_outputs/mydoc/designers/ ~/Dropbox/Websites/manuals/
{% endhighlight %}




