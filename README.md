# Personal Blog / Bio
Based on combination of Jekyll theme [landing-page-bootstrap-theme](http://startbootstrap.com/templates/landing-page/) and [mediumish-theme-jekyll](https://github.com/wowthemesnet/mediumish-theme-jekyll)


## How to create posts
 - Place images `/img/projects/`
 - Create posts for the bio and blog in the respective folders using yaml syntax.

```txt
---
layout: default
img: img.gif
category: projects
title: Awesome project<br>Year
description: |
  <p class="lead">description</p>
links: #List of links
  - title: title on page
    url: href

venue: where was this?
authors: who did this?
---
```

## How to run locally
To debug locall, the following code should work. 
```
#Install tools
brew install ruby
gem install bundler
bundle install #run in local folder
#Add this in bashrc
export LC_ALL="en_US.UTF-8"
export LANG="en_US.UTF-8"
#Serve locally. Should be available on http://localhost:4000/
bundle exec jekyll serve
```

## How to deploy
As long as this is pushed to a repo associated with Github pages it should be compiled and hosted.


# Mediumish - Jekyll Theme

[Live Demo](https://wowthemesnet.github.io/mediumish-theme-jekyll/) &nbsp; | &nbsp; [Download](https://github.com/wowthemesnet/mediumish-theme-jekyll/archive/master.zip) &nbsp; | &nbsp; [Documentation](https://bootstrapstarter.com/bootstrap-templates/template-mediumish-bootstrap-jekyll/) &nbsp; | &nbsp; [Buy me a coffee](https://www.wowthemes.net/donate/)

![mediumish](assets/images/mediumish-jekyll-template.png)
**Mediumish for Jekyll** is designed and developed by [Sal](https://www.wowthemes.net) and it is *free* under MIT license. 

<a href="https://www.wowthemes.net/donate/" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: auto !important;width: auto !important;" ></a>


### Copyright

Copyright (C) 2019 Zouhair Mahboubi
