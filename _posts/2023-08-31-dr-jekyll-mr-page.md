---
title: Publish your blog using Jekyll and GitHub Pages
published: true
---

### Intro

If you'd want to create a portfolio, or share technical notes, you might start writing a blog. There are various ways to do this, so go ahead and explore the options. I didn't want to spend too much time, so I went with Jekyll and GitHub Pages combo.

[Jekyll](https://jekyllrb.com/docs/){:target="_blank"} is a static site generator. Basically, there is no database, everything is stored in the files. If you keep your notes in Markdown format, this duo just might be a perfect choice for you. You can easily customize your site's look and feel. Or just choose from plenty of templates that are already available for you.

[GitHub pages](https://github.com/){:target="_blank"} is a hosting service for static files (HTML, CSS, JS) straight from your GitHub repository. (How cool is that?)

So, with these two tools you have everything you need to host your website. In addition to that, you may buy your own domain and make things even more interesting.


### Prerequisites

A Linux machine (Windows and Mac, you're on your own.) and a GitHub account. That's it.


### Installation Process

Installation process is described in the docs files, but here's the summary:

```bash
sudo apt-get install ruby-full build-essential zlib1g-dev
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
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

Run `sudo sysctl -p` or restart your terminal. You should be good to go. Check the [link](https://www.itzgeek.com/how-tos/linux/debian/how-to-disable-ipv6-on-debian-9-ubuntu-16-04.html){:target="_blank"} for more information.

Back to Jekyll. If you want to use a predefined theme, the process is slightly different. In my case, I'm using [The Hacker-Blog Theme](https://github.com/tocttou/hacker-blog){:target="_blank"} which, in turn, is based on the [Hacker Theme](https://github.com/pages-themes/hacker){:target="_blank"}. 

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
git status
git add .
git commit -m "initial commit"
git remote add origin <git@github.com:copy-this-from-your-repo>
git branch -M master
git push -u origin master
```


### Summary

In summary, if you want to start blogging, for whatever the reason, be sure that you have a good enough reason. Just kiddin'. But, if you do like Markdown, and you don't really need a proper database for your data, you may want to use Jekyll and GitHub Pages combo. It's free, easy to use, and if you're ready to put some time and effort, you may build a professionally looking portfolio or blog.

For me, I really enjoyed this initial interaction with Jekyll. My plan is to continue playing with it to see how far I can get. I'm even considering using Docker next time. That could be fun.


### Additional Links

[Markdown docs](https://www.markdownguide.org/basic-syntax/){:target="_blank"}  
[Hacker Blog](https://jamstackthemes.dev/theme/jekyll-theme-hacker-blog/){:target="_blank"}  
[The Hacker Theme](https://github.com/pages-themes/hacker){:target="_blank"}  
