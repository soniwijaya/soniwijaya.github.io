---
layout: post
title:  "Instalation Jekyll on Ubuntu 16.04"
date:   2018-02-23 11:18:23
author: soniwijaya
categories: personal
header-img: "images/blog/jekyll-logo.png"
---
I am currently challenged to create my own personal blog by choosing one of the cms of which there is wordpress, blogspot, and github pages. I chose github pages as my personal blog with my system operation ubuntu 16.04. 
the thing I need to prepare is to install Ruby, RubyGems and Jekyll via terminal:

<!-- adding image -->
<!-- ![My helpful screenshot]({{ "/images/blog/jekyll-logo.png" | absolute_url }}) -->

**Instalation Ruby, RubyGems, Jekyll, Check Version**

```
$ sudo apt-get install ruby-full
$ ruby -v
$ gem install rubygems
$ gem -v
$ gem install jekyll
$ jekyll --version
```

Move to directory for instalation Jekyll:
For example: `cd Document\home\`

**Built Directory Jekyll**
```
$ jekyll new < name directory >
```

**Move to Directory**

```
$ cd < name directory > 
```

**Run Server with Jekyll**

```
$ jekyll serve
```

**Open the first Jekyll in Browser**

For open Jekyll index.html, just typing this in URL "http://localhost:4000".