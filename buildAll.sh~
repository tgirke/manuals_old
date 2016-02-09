#!/bin/bash
## Script that runs typical workflow when updating site
## Author: Thomas Girke
## Last update: Feb 9, 2016

## (1) All changes should be made from master branch. Note, the script
##     should be run from the root directory of the repo.
git checkout master  

## (2) Edit existing pages and/or add new ones, usually in ./mydoc

## (3) Commit edits made in master branch (assumes you have added/deleted files as needed)
git commit -am "some edits"
git push -u origin master
echo "Committed/pushed changes to master branch on GitHub"

## Build site with changes you made
kill -9 $(ps aux | grep '[j]ekyll' | awk '{print $2}')
clear
echo "Building Mydoc Designers website..."
jekyll build --config configs/mydoc/config_designers.yml
# jekyll serve --config configs/mydoc/config_designers.yml
echo "done"
echo "Finished building all the web outputs!!!"
echo "Now the builds are pushed to github."

## Sync changes to gh-pages branch
git checkout gh-pages
rsync -avh --stats --progress ~/Dropbox/Websites/doc_outputs/mydoc/designers/ ~/Dropbox/Websites/manuals/t add .
git commit -am "some edits"; git push -u origin gh-pages
echo "Committed/pushed changes to gh-pages branch on GitHub"
git checkout master 
echo "Switched back to master branch on local repo."

