ThreatSim Rails Applications
=============
[![Code Climate](https://codeclimate.com/repos/5639332b1787d70f5b00060e/badges/396d79ff568a33501a97/gpa.svg)](https://codeclimate.com/repos/5639332b1787d70f5b00060e/feed)

[![Test Coverage](https://codeclimate.com/repos/5639332b1787d70f5b00060e/badges/396d79ff568a33501a97/coverage.svg)](https://codeclimate.com/repos/5639332b1787d70f5b00060e/coverage)

[![Codeship Status for wombatsecurity/threatsim-rails](https://codeship.com/projects/3dc40200-649f-0133-4717-4a7e5d8c8004/status?branch=master)](https://codeship.com/projects/113208)

Currently, this repository hosts our Rails app - threatsim (the main site that
our customers use).  Within each subfolder, there should be a README.md file to
explain what each folder contains. Since we're pretty much a Mac shop, the
documentation will be flavored for Mac environments.

Prepare
-------

Before you run any Threatsim code, you're going to need to set up your
development environment.

    * Homebrew
    * Editor
    * Ruby 2.2.8
    * MySQL
    * Redis
    * Other odds and ends

### Homebrew

Just install [homebrew](http://brew.sh). It's cool.

### Editor

Any code editor will likely be fine. Vim, Sublime Text, Emacs, etc. More
importantly is that you configure if for with a few code editing preferences.
Specifically, indent with spaces, rather then tabs, and set the indent depth to
two spaces.

Keep line lengths reasonably short. Our guideline is "short enough to be read
in github with out scrolling left and right". That translates to a max line
length somewhere between 80 and 120 characters.

### Ruby 2.3.7

We currently run on Ruby 2.3.7. You can install it directly, but we recommend
using a Ruby version manager. rbenv and chruby are both available on brew, and
rvm can be installed from it's website. Additionally, you may want to install
ruby-build to simplify the ruby build process. It can also be found on brew.

    % brew install rbenv ruby-build

### MySQL

We use MySQL for our database and primary persistence. There are a few ways to
install it, but I recommend brew.

    % brew install mysql@5.7

### Redis

We heavily leverage Redis, both for caching and queuing for background processing.

    % brew install redis

### Other odds and ends

#### Mailcatcher

    % gem install mailcatcher

#### NodeJS

    % brew install nodejs

#### Phantomjs
After installing nodejs, install phantomjs

    % npm install -g phantomjs-prebuilt
    ...
    % phantomjs -v # should output 2.2.1


#### Other libraries need before running bundle install

You may find your self needing to install additional libraries over time. Many
of these are already available from brew. For example, I also needed to install
mcrypt before I could install all the gems I needed for threatsim-rails.

    % brew install mcrypt

PV: I had to install ruby-mcrypt gem after installing mcrypt via Homebrew, but I had
to tell it where my installation of mcrypt was.

```
gem install ruby-mcrypt --source=http://gems.github.com \
      -- --with-mcrypt-dir=/usr/local/Cellar/mcrypt/2.5.8/
```

Develop
-------

Now that your system is ready, you should check out this repository from
github. The rails app is located in the sub-directory named threatsim.
Instructions for its care and feeding will be in the README file in that
directory.

Similarly, you will also need to clone threatsim-workers (background
processing) and threatsim-lp (landing pages).

You will need all three to run a full campaign, and that's our bread and
butter: Run email campaigns and capture clicks.

### [threatsim-rails](https://github.com/threatsim/threatsim-rails)

The management application, threatsim-rails is where we handle account,
user, target, and campaign management.

### [threatsim-workers](https://github.com/threatsim/threatsim-workers)

This is our backend processing. Writen in Ruby using sidekiq, this is where we
process mailings, aggregate click data, and any other heavy lifting that needs
to get done.

### [threatsim-lp](https://github.com/threatsim/threatsim-lp)

This is our landing pages. Whenever anyone clicks a link, this is where we
capture it. It is also where we finger print their browsers and check for
vulnerabilities.

A Note About Readme
-------------------

The READMEs are living documentation. Feel free to correct or enhance them as
you go along.
