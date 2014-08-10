---
layout: post
title:  "Solving Asset Issues with jekyl 1.5.x"
date:   2014-08-13 10:30:00
categories: jekyll jekyl-1-5-1
---

This post is for those who are working on jekyl 1.5.x series.
I have been working 1.5.1 for since its release in March 2014 and hence I have couple of sites running on it.

The problem I am narrating here is not there in the 2.x versions of Jekyl

[Click here][http://rubygems.org/gems/jekyll/versions] to see all the versions of Jekyl
[Click here][http://jekyllrb.com/docs/upgrading/] to read about upgrading Jekyl

### The problem ###

Unlike the Github User and Github Organisation Pages, Github Project Pages are kepy in the same repository as their project. The URL for a Project Page will look like the following

`http(s)://username.github.io/project_name`

When you push jekyl 1.5.x code to github pages, it fails to load CSS.
/:repo_name cause the assets to fail as Jekyll doesn't know about this interim folder name

Lets solve this by letting jekyll know about the base url and base folder

- Make sure that you are in your master branch
- Open *_config.yml*
- Add the following there

{% highlight yaml %}
\# For Github Pages
\#base_folder: /repo_name
\#base_url: http://username.github.io
{% endhighlight %}

Note that we are now in master branch and we don't want to enable this. We will defenitely uncomment this line while deploying it to github pages. Just wait and see.

Here is how your _config.yml file looks like after doing these changes:

{% highlight yaml %}
  name: Your New Jekyll Site
  markdown: kramdown
  pygments: true
  port: 5000
  permalink: /blog/:year/:month/:day/:title/

  # For Github Pages
  base_folder: /repo_name
  base_url: http://username.github.io
{% endhighlight %}


- Let us use these url fragments while generating links for CSS and blog posts
- open index.html and change the links to
  - `{ {site.base_url} }{ {site.base_folder} }{ { post.url } }`

{% highlight ruby %}
<div id="home">
  <h1>Blog Posts</h1>
  <ul class="posts">
    { % for post in site.posts % }
      <li><span>{ { post.date | date_to_string } }</span> &raquo; <a href="{ {site.base_url} } { {site.base_folder} } { { post.url } }">{ { post.title } }</a></li>
    { % endfor % }
  </ul>
</div>
{% endhighlight %}

#### STEP 6 : Configuring Git ####

- Initialise Git from your repository
  - cd path-to-workspace/create_a_blog_in_30_minutes_using_jekyll
  - `git init`
  - `git status`
    - You should see "On Branch Master" and some files in red color (if you have enabled git colors):
    - Refer Screenshots below
- Add Remote URL
  - Go to your Github page and copy the git URL for the repository you just created
  - Refer Screenshots below
  - `git remote add origin git@github.com:kpvarma/create_a_blog_in_30_minutes_using_jekyll.git`
  - type `git remote -v` and you should see
    - origin  git@github.com:kpvarma/create_a_blog_in_30_minutes_using_jekyll.git (fetch)
    - origin  git@github.com:kpvarma/create_a_blog_in_30_minutes_using_jekyll.git (push)
- Commit your changes
  - This will sync your local changes with github repository
  - `git add .` Add all the files recursivley to git
  - `git commit -m'Created Jekyll Application'` Commit all the files (-m is the message. Without message, git wont allow you to commit)
  - `git pull origin master` This is to first make sure that there is no conflict with the files in server and local
  - `git push origin master`
- Verify
  - Now go to your github page and you will see all your jekyll files there
  - Image: jekyll files in github

#### STEP 7 : Publishing to Github Pages ####

- Dealing with Github Repo name
  - Open _config.yml
  - Uncomment the base_folder and base_url
    - \# For Github Pages
    - base_folder: /create_a_blog_in_30_minutes_using_jekyll
    - base_url: http://kpvarma.github.io
- Preparing our Github Pages
  - Create a branch named gh-pages
    - `git checkout -b gh-pages`
  - Lets now push it to github
    - `git push origin gh-pages`
- Configure Github to make use of pages
  - Go to Github repository
  - Go to Settings
  - Under *Github Pages* section, you will see something like *Your site is published at http://kpvarma.github.io/create_a_blog_in_30_minutes_using_jekyll.*
- Click on the link and enjoy viewing your first blog post.

<br/>

### Jekyll Themes ###

http://jekyllthemes.org/

### Screen Shots ###

<span class="image-galery">
![Create a Github Account](/assets/images/create-a-github-account.png)
![Git Repository](/assets/images/git-repository-url.png)
![Git Status](/assets/images/git-status.png)
![Jekyll Application Structure](/assets/images/jekyl-application-structure.png)
![Jekyll Files Synced With Github](/assets/images/jekyl-files-synced-with-github.png)
![Jekyll Serve](/assets/images/jekyll-serve.png)
</span>

<br/>


> Feel free to leave your comment with respect and courtesy. I sincerely appreciate your support!

<div class="pull-right"><strong>Krishnaprasad Varma</strong></div>
<div class="clearfix"></div>


[mrug]: http://www.meetup.com/Mysore-Ruby-User-Group/events/195213512/ "Mysore Ruby User Group"
[cdn]: http://en.wikipedia.org/wiki/Content_delivery_network "Content Delivery Network"
[godaddy]: http://www.godaddy.com/ "GoDaddy makes registering Domain Names fast, simple, and affordable. Find out why so many business owners chose GoDaddy to be their Domain Name Registrar."
[gophercon]: https://gophercon.in "The official site of GopherConIndia. A Go programming language conference in India."
[qwinix]: http://qwinixtech.com "Qwinix Technologies - Innovative End to End IT Solutions for your Business"
[kpvarma]: http://kpvarma.com "kpvarma.com - My Thoughts"
[trello]: http://trello.com
[jekyll]: http://jekyllrb.com
[github-pages]: https://pages.github.com/