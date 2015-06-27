---
layout: post
title:  "Setup your free Github Account"
date:   2014-08-12 10:30:00
categories: git github how-to
comments: true
share: true
---

Setting up an account on github is the first thing you should do if you want to join the open source community and start contributing to it.
This article is written to help the students to have a smooth landing to the open source world from their academics.

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
![Create a free Github Account](/images/setup-your-free-github-account/create-an-account-in-github.png)
</span>

<br/>

### STEP 2 : Create your first repository ###

- Login to https://github.com/
- Click on the *New Repository* button located in the bottom right of the page

<span class="image">
![New repository button](/images/setup-your-free-github-account/new-repository-button.png)
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
![Create your first repository](/images/setup-your-free-github-account/create-your-first-repository.png)
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
![Clone the repository](/images/setup-your-free-github-account/clone-the-repository.png)
</span>

- Open your Console / Terminal / Command line Interface
- Create a workspace in your home folder
- MAC, Linux

{% highlight css %}
mkdir ~/workspace
{% endhighlight %}

- Go to the workspace in console

{% highlight css %}
cd ~/workspace
{% endhighlight %}

- Type git clone and Paste the copied repo URL
  - This should look like
{% highlight css %}
git clone git@github.com:username/repo-name.git
{% endhighlight %}

- Press Enter

Now you have the repository cloned in your workspace.
Happy Coding!

<br>
<br>