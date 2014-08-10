---
layout: post
title:  "How to build a blog in 30 minutes"
date:   2014-08-10 10:30:00
categories: jekyll github-pages how-to
---

This post is just on how I created this blog using [Jekyl][jekyll]{:target="_blank"} and hosted it on [Github Pages][github-pages]{:target="_blank"}. Since it is all there in my mind now, I thought I would write a post about it. This is an extract from the talk I gave on Jekyl at [Mysore Ruby User Group][mrug]{:target="_blank"}.

### Introduction ###

<br/>

#### GitHub ####

I chose to host the website on [Github Pages][github-pages]{:target="_blank"} because rather than serving a page directly it now uses a [Content Delivery Network][cdn]{:target="_blank"}. *Github* also protect the pages with the same kind of Denial of Service mitigation services used for gitHub.com. But the best thing I liked is that no `Devops` work needed. You just need to push your code to a branch named `gh-pages` and you are done.

Learn more about *Github Pages* [here][github-pages-more]{:target="_blank"}

#### Jekyll ####

I loved [Jekyl][jekyll]{:target="_blank"} ever since I started using it. [Jekyl][jekyll]{:target="_blank"} is a static site generator. Its quite easy to work with it as long as you are dealing with static sites and blogs.

Learn more about Jekyll [here][jekyll]{:target="_blank"}

#### GoDaddy ####

I registered this domain [kpvarma.com][kpvarma]{:target="_blank"} in GoDaddy and it was a pleasant experience with [GoDaddy][godaddy]{:target="_blank"} till now.

### Lets do it ###

<br/>

#### STEP 1 : Setup a free Github account ####

This part is covered in detail [here][]

#### STEP 2 : Setup Ruby and Jekyll ####

- Install Ruby - *https://www.ruby-lang.org/en/installation/*
- Install Jekyll
  - `gem install jekyll`.

#### STEP 3 : Create a Jekyll Application ####

- Go to your workspace directory *e.g: ~/Projects/MyWorkspace*
- Create a Jekyll Application
  - `jekyll new create_a_blog_in_30_minutes_using_jekyll`
- Run the Jekyll Application
  - `jekyll serve`
- Compile the Jekyll files to HTMLS
  - `jekyll build --watch`

It should now show a message like "*New jekyll site installed in path-to-workspace/ create_a_blog_in_30_minutes_using_jekyll*"

#### STEP 4 : Create your first post ####

Lets understand the folder structure of a Jekyll Application.

![Jekyll Application Structure](/assets/images/jekyl-application-structure.png)

##### Lets now create a post #####

- Create a new file in _posts.
- Put current date in the file name

#### STEP 5 : Preparing for Deploying ####

##### Use kramdown as the markdown language#####

- Open *_config.yml*
- Under the markup section, you will see 'redcarpet' by default.
- Change it to 'kramdown'
- More about kramdown here - http://kramdown.gettalong.org/syntax.html#inline-links

`markdown: kramdown`

##### Custom Permalink #####

By default Jekyll uses 'jekyll/update/year/:month/:day/:title'. </br>
Lets change it to '/blog/:year/:month/:day/:title/'

- Open *_config.yml*
- Add a permalink to it

`permalink: /blog/:year/:month/:day/:title/`

##### Base URL Issue with Github Pages #####

When you push this code to github pages, it fails to load CSS. Github Pages has a folder structure unless you host it against your profile / organisation.

`e.g: username.github.io/:repo_name`

/:repo_name cause the assets to fail as Jekyll doesn't know about this interim folder name

Lets solve this by letting jekyll know about the base url and base folder

- Open *_config.yml*
- Add the following there

{% highlight yaml %}
\# For Github Pages
\#base_folder: /repo_name
\#base_url: http://username.github.io
{% endhighlight %}

Note the we are now in master branch and we don't want to enable this untill we push gh-pages. We will defenitely uncomment this line while deploying it to github pages. Just wait and see.

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

<span class="image gallery">
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
[github-pages-more]: https://github.com/blog/1715-faster-more-awesome-github-pages