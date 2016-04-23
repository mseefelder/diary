---
layout: post
title:  "Setting up this blog: Jekyll + GitHub Pages"
date:   2016-04-23 15:59:00 -0300
categories: meta-blogging
---

While I was setting this blog up, all I wanted was a simple tutorial to set up a [jekyll](https://jekyllrb.com/) + gh-pages on a project page. So here it is, the simplest setup tutorial I could think of:

**Requisites**: You'll need [ruby](https://www.ruby-lang.org) installed on your machine, as well as [bundler](http://bundler.io/) and [git](https://git-scm.com/).

1. The github part:
	* Log into github;
	* Go to `New repository`
	* Choose a name and create it. No README, nor .gitignore or license
		* So that we can start the repository on gh-pages branch right away

2. The local part (on your personal computer):
	* Open the terminal;
	* Create your repository and point it to the remote. Should be something like:
			
			mkdir repository_name
			cd repository_name
			git init
			git checkout -b gh-pages
			git remote add origin https://github.com/your_username/repository_name.git
		
	* Create a *Gemfile* specifying to install jekyll and the [gh-pages gem](https://github.com/github/pages-gem), like this:
	
			echo "gem 'github-pages', group: :jekyll_plugins" > Gemfile

	* To install jekyll and pages-gem, run:

			bundle install

	* Now, to create the default blog structure:

			bundle exec jekyll new . --force

	* Now your folder should have a bunch of new files and folders. One of them shuld be `_config.yml` on the root of your project;
	* The last important step is opening `_config.yml` and editing the `baseurl` and `url` lines to:

			baseurl: "/repository_name" 
			url: "http://your_username.github.io"

		* This way, you shouldn't have problems with the html paths when the pages are generated

	* At last, but not least, we need to switch to the `gh-pages` branch, make it the default one and push it to github:

			git add .
			git commit -m "First commit"
			git push -u origin gh-pages

	* After that, your blog should be available at your_username.github.io/repository_name/
	* If you want to test you blog locally, the following should work:
		
			bundle exec jekyll serve

		* Which will make your blog preview available at http://127.0.0.1:4000/repository_name/