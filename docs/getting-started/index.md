---
layout: getting_started
title: Getting Started

current: Overview
next: Why Vagrant?
next_url: /docs/getting-started/why.html
---
# Getting Started with Vagrant

Vagrant uses [Oracle's VirtualBox](http://www.virtualbox.org)
to build configurable, lightweight, and portable virtual machines dynamically.
The first couple pages serve to introduce you to Vagrant and what it has
to offer while the rest of the guide is a technical walkthrough for building a
fully functional Ruby on Rails development environment. The getting started
guide concludes by explaining how to package the newly created vagrant environment
so other developers can get up and running in just a couple commands.

## Get VirtualBox

Vagrant depends on [Oracle's VirtualBox](http://www.virtualbox.org) to create all of
it's virtual environments. VirtualBox is a general-purpose full virtualizer for
x86 hardware. Targeted at server, desktop and embedded use, it is now the only
professional-quality virtualization solution that is also Open Source Software.
VirtualBox runs on **Windows**, **Mac OS X**, **Linux**, and **Solaris**.

Here is a link directly to the [download page](http://www.virtualbox.org/wiki/Downloads).

<div class="info">
  <h3>Version 4.0.x!</h3>
  <p>
    Vagrant requires VirtualBox version 4.0.x (meaning 4.0.1, 4.0.2, etc.). If your package
    manager is still stuck on version 3.x or lower, then download the 4.0 installation package from
    the official VirtualBox <a href="http://www.virtualbox.org/wiki/Downloads">download page.</a>
  </p>
  <p>
    If you have no choice but to use VirtualBox 3.2.x, you can use the 0.6.x line of
    Vagrant, which is no longer supported but was stable for months prior to 0.7.x.
    Note that if you choose to go this route, small details between 0.6.x and 0.7.x
    are slightly different, so the docs may not be completely reliable. Installation
    of this specific version is straightforward through RubyGems:

    <pre>gem install vagrant -v 0.6.9</pre>
  </p>
</div>

## Setting up Ruby and RubyGems

Although Vagrant is written in Ruby, web developers from many different languages
come to use it (Python, Java, Clojure, etc.). Therefore, if you've never setup Ruby
or RubyGems before, please check out our basic guides, written for different
popular operating systems listed below:

* [Windows](/docs/getting-started/setup/windows.html)
* [Mac OS X](/docs/getting-started/setup/mac.html)
* [Ubuntu](/docs/getting-started/setup/ubuntu.html)

Is your OS not listed above? Feel free ask for help via our [support channels](/support.html).
Or if you figure it out on your own, let us know how and we'll gladly update the
website.

## Install Vagrant

Vagrant is packaged as a [RubyGem](http://rubygems.org/). Since Vagrant is written
in Ruby and RubyGems is a standard part of most Ruby installations, RubyGems is the
quickest and easiest way to distribute Vagrant to the masses, and it can be installed
just as easily:

{% highlight bash %}
$ gem install vagrant
{% endhighlight %}

## Your First Vagrant Virtual Environment

{% highlight bash %}
$ vagrant box add lucid32 http://files.vagrantup.com/lucid32.box
$ vagrant init lucid32
$ vagrant up
{% endhighlight %}

While the rest of the getting started guide will focus on explaining how to
build a fully functional virtual machine to serve rails applications, you
should get used to the above snippet of code. After the initial setup of
any Vagrant environment, the above is all any developer will need to create
their development environment! Note that the above snippet does actually
create a fully functional 512MB virtual machine running Ubuntu in the
background, although the machine doesn't do much in this state.
