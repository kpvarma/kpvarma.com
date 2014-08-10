---
layout: post
title:  "Setup your free Github Account"
date:   2014-08-12 10:30:00
categories: git github how-to
---

Setting up an account on github is the first thing you should do if you want to get into the open source world!

### Introduction ###

Github is a code sharing platform used by millions of people to work collaborately. It offers all what git gives you and even more. Unlike Git, github gives you a GUI with a web interface.

GitHub has become such a staple among the open-source development community that many developers have begun considering it a replacement for a conventional resume and some employers require applicants to provide a link to and have an active contributing GitHub account in order to qualify for a job. [Courtesy: Wikipedia]

<br/>

### STEP 1 : Sign Up ###

Let us create a free account in Github.com

- Go to https://github.com/
- Enter username, email address and the password.
- Click on *Sign Up for Github* button

<span class="image">
![Create a free Github Account](/assets/images/setup-your-free-github-account/create-a-free-account-in-github.png)
</span>

<br/>

### STEP 2 : Create your first repository ###

- Login to https://github.com/
- Click on the *New Repository* button located in the bottom right of the page

<span class="image">
![New repository button](/assets/images/setup-your-free-github-account/new-repository-button.png)
</span>

<br/>

- You will be taken to a page where it ask you to enter some details about the new repository you want to create.
- Enter your repository name
  - Github will create a url with this name to access the repository
  - `https://www.github.com/username/repo_name`
- Let it be a *public* repository i.e Anyone can see this repository. But You choose who can commit.
- Check Initialize this repository with a README
- Skip gitignore and LICENCE part
- Click on the *Create Repository* button

<span class="image">
![Create your first repository](/assets/images/setup-your-free-github-account/create-your-first-repository.png)
</span>

<br>

### STEP 3 : Clone your repository to your machine ###

- Install Git
- Copy the repo URL to the clip board
  - Go to your repository page in github
  - On the right side of the page, you will see *SSH Clone URL*
  - Click on the *Paste* link below it
  - The repository URL is copied to your clipboard

<span class="image">
![Clone the repository](/assets/images/setup-your-free-github-account/clone-the-repository.png)
</span>

- Open your Console / Terminal / Command line Interface
- Create a workspace in your home folder
- MAC, Linux

`mkdir ~/workspace`

- Go to the workspace in console

`cd ~/workspace`

- Type git clone and Paste the copied repo URL
  - This should look like

`git clone git@github.com:username/repo-name.git`

- Press Enter


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