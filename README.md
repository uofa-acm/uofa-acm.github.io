# uofa-acm.github.io

For small edits like adding a talk, simply fork, add your
talk based off the template given in the next section. Getting
your changes back upstream only requires a pull request
to uofa-acm master. For more in depth work, you'll need to
read the making big edits section below.


## Quick Start to Making (big) Changes on uofa-acm.github.io

While you could fork, change, pull request, and pray you didn't
break anything, you *can* run the uofa-acm site locally to verify.
If this interests you, keep reading.

We use the Ruby package manager [RVM](https://rvm.io/) to install and
manage the site dependencies. While RVM is not strictly necessary, it will
keep your site-wide Ruby installation (if it exists) pristine.

Getting RVM installed is a single command:

    $ \curl -sSL https://get.rvm.io | bash -s stable

You should now have access to `rvm` commands in your shell. Go ahead
and install a local copy of Ruby:

    $ rvm install ruby

Now grab the [Jekyll](http://jekyllrb.com/) microblogging framework that
allows you to run uofa-acm locally on your machine:

    $ gem install jekyll rdiscount

All done! Fork uofa-acm and clone your fork down to your machine:
```
$ git clone git@github.com:$USER/uofa-acm.github.io.git
$ cd uofa-acm.github.io
$ jekyll serve --watch
```

From a browser you can load [localhost:4000](http://localhost:4000) and
view your local copy of uofa-acm. As you make edits the Jekyll serve
will reload, so just hit refresh in the browser. Done and done.


## Adding Your Talk

The filename of your post should be YYYY-MM-DD-Some-Title.md, where YYYY-MM-DD is the date of your talk.
The file you create should go in the _posts directory of the project.

###the file should have the following layout:

```
---
layout: post
title: Title of your talk
smalltext: Your name
summary: A brief sentence about your talk
tags: talk
---

A full description of your talk goes here.

You can link to your website or presentation like this: [example link](http://example.com/)
```
Any other Markdown styling will work.  See [here](http://daringfireball.net/projects/markdown/syntax)
for additional Markdown syntax


## Adding Your Member Bio

The filename of your post should be YYYY-MM-DD-firstname-lastname.md, where YYYY-MM-DD is the current date.
The file you create should go in the _post/members directory of the project.

***We are currently working on fixing this so it is not in the posts directory and does not require a date in the filename. Stay tuned!***

###the file should have the following layout:

```
---
layout: member
name: First and Last name
email: email@address.com
tags: members
---

Your full bio goes here.

You can link to your website, github, or linkedin profiles like this: [example link](http://example.com/)
```
Any other Markdown styling will work.  See [here](http://daringfireball.net/projects/markdown/syntax)
for additional Markdown syntax
