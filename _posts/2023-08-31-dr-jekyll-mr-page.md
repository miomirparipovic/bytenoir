---
title: Publish your blog using Jekyll and GitHub Pages
published: true
---

### Disclaimer

This is my very first post, and I want to start it with a disclaimer. This blog/portfolio venture is a product of my own experimentation and learning-kind of a personal endeavor to dive into the world of programming and explore its treacherous depths and beyond. If you're into comprehensive tutorials or in-depth documentation, you're in the wrong place. There is plethora of resources that might serve you better (just ask Google). If you happen to stumble upon this place by chance, just be warned that this is nothing more than an incomplete record of my learning process-a chronicle of trial and error. My main goal is to try and learn more about these topics, and to be able to explain them plainly to others-and myself (The Feynman Technique). Take nothing for granted. Try it, explore it, experiment, and play with it. But then again, you should use this approach for (almost) anything in life.


### Intro

If you feel that you have something important to say (you really don't), you want to make yourself more 'visible' (but, why?), or, like me, you want to make your technical notes available online for whatever purpose (I'm already regretting this)-you might start blogging. There are so many ways and approaches to do this, so feel free to do your own research on the topic. I didn't want to waste too much time, so I chose Jekyll and GitHub Pages combo.

[Jekyll](https://jekyllrb.com/docs/) is a static site generator. Basically, there is no database, everything is stored in the files. If you keep your notes in Markdown format, this duo just might be a perfect choice for you. You can easily customize your site's look and feel. Or just choose from plenty of templates that are already available for you.

[GitHub pages](https://github.com/) is a hosting service for static files (HTML, CSS, JS) straight from your GitHub repository. (How cool is that?)

So, with these two tools you have everything you need to host your website. In addition to that, you may buy your own domain and make things even more interesting.


### Prerequisites

A Linux machine (Windows and Mac, you're on your own.) and a GitHub account. That's it.


### Installation Process

Installation process is described in the docs files, but here's the summary:

```bash
gem install jekyll bundler
jekyll new myblog
cd myblog
bundle exec jekyll serve
```

Browse to http://localhost:4000

I did encounter problems during the installation process. Apparently, because my Linux is hosted as a virtual machine (KVM), there were problems 

If you host your Linux as a virtual machine (KVM), you might encounter some networking related problems. Long story short, you'll need to disable the IPv6 or play with NATing.

Check if you have the problem with the command below.

```bash
wget -6 google.com
```

With `ifconfig` check for 'inet6'. Then:

```bash
sudo vim /etc/sysctl.conf
```

Set the following to disable IPv6 for all adapters:

```
net.ipv6.conf.all.disable_ipv6 = 1
```

Run `sudo sysctl -p` or restart your terminal. You should be good to go. Check the [link](https://www.itzgeek.com/how-tos/linux/debian/how-to-disable-ipv6-on-debian-9-ubuntu-16-04.html) for more information.

Back to Jekyll. If you want to use a predefined theme, the process is slightly different. In my case, I'm using [The Hacker-Blog Theme](https://github.com/tocttou/hacker-blog) which, in turn, is based on the [Hacker Theme](https://github.com/pages-themes/hacker). 

```bash
touch Gemfile
```

Then add these line to the file:

```bash
source "https://rubygems.org"

gem "jekyll", "~> 4.2"  # Use the version of Jekyll you prefer
gem "jekyll-feed"
gem "jekyll-sitemap"
gem "jekyll-paginate"   # Add this line if you want pagination
gem "jekyll-seo-tag"
```

Then run:

```bash
bundle install
jekyll serve
# if you add more gems, you may run
bundle update
# to start your server run the command below and check localhost on the port 4000
jekyll serve
```

I won't in detail customization for now, but you might want to check `_config.yml` file and made some changes.

You write your posts in `_posts` directory. I plan to write more about this, but this is enough to get you going.

The next step is to create a git repo and name it like this: 'your-github-username.github.io'. Upload your files to the repo and you're done. It's just easy as this.

```bash
git init
# check your files
git status
# add everything
git add .
# commit
git commit -m "initial commit"
git remote add origin <git@github.com:copy-this-from-your-repo>
git branch -M master
git push -u origin master
```


### Summary

In summary, if you want to start blogging, for whatever the reason, be sure that you have a good enough reason. Just kiddin'. But, if you do like Markdown, and you don't really need a proper database for your data, you may want to use Jekyll and GitHub Pages combo. It's free, easy to use, and if you're ready to put some time and effort, you may build a professionally looking portfolio or blog.

For me, I really enjoyed this first interaction with Jekyll, so my plan is to continue improving on my basic knowledge and playing with it to see how far I can get. I might use Docker next time. That could be fun.


### Additional Links

[Markdown docs](https://www.markdownguide.org/basic-syntax/)  
[Hacker Blog](https://jamstackthemes.dev/theme/jekyll-theme-hacker-blog/)  
[The Hacker Theme](https://github.com/pages-themes/hacker)  
