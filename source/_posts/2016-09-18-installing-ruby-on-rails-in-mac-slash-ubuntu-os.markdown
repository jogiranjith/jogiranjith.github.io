---
layout: post
title: "Installing Ruby On Rails in mac/ubuntu Os"
date: 2016-07-27 00:38:38 +0530
comments: true
categories: ["Ruby on Rails"]
---

To get your Ruby on Rails development environment set up get working on this right away using the guide i have provided below, broken down according to operating system.  Depending on your operating system and other system specific factors, additional steps may be required. If issues occur during the installation process, please refer to the following link, which may contain more up-to-date information: 

If you encounter any problems, don't give up, ask questions in the discussion forum, search the web for answers, etc.  If you can get your development environment set up and functioning properly, you will have taken the first big step towards becoming a web application developer!

#### Installing Ruby and Rails on Linux
   
  Install Dependencies

  Install build essentials by opening up a terminal window and typing the following command:

      sudo apt-get install build-essential

  Next, install curl. In the terminal window type:
   
      sudo apt-get install curl

  Then, install Git. In the terminal window type:

      sudo apt-get install git-core

  Installing RVM

  RVM stands for Ruby Version Manager and allows you to install multiple versions of Ruby and switch between them easily. Even if you are only going to use one version, it's probably the simplest way to install Ruby.

  To install RMV, in your terminal window run the command:

      curl -L https://get.rvm.io | bash -s stable --ruby

  In the terminal window, type the following in order to make RVM known in your bash sessions:

      echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"' >> ~/.bashrc

  Finally, restart your bash session by closing and then reopening your terminal window

  Using RVM

  You can get a list of Ruby versions by running the following command in your terminal window:

      rvm list known

  The version of Ruby we will use is 2.1.0 and you can install it by using the following command in your terminal window:

      rvm install ruby-2.1.0

  Set this version as the default using the following command in your terminal window:

      rvm use 2.1.0

  You can then make sure Ruby is installed by running the following command in your terminal window:

      ruby -v

  Installing Rails

    The latest version of Rails will be installed by issuing the following command.  From your terminal window type:

      gem install rails

  you can verify that it was installed correctly by running the following command in your terminal window:

          rails -v

  (This will check the current installed version of Rails, which should be 4.0 or later)

#### Installing Ruby and Rails on OSX

  First you must install Xcode with command line utilities  

  In order to do this, you must locate Xcode in the Apple app store and install it from there.

  Afterward, open Xcode, go to Preferences and click on the Downloads tab.

  Click install next to Command Line Tools.

  To install Git, go to http://git-scm.com and download the Mac OSX installer.

  Installing RVM

  RVM stands for Ruby Version Manager and allows you to install multiple versions of Ruby and switch between them easily. Even if you are only going to use one version it's probably the simplest way to install Ruby.

  Install RMV by running the following command in your terminal window:

      curl -L https://get.rvm.io | bash -s stable --ruby

  Next, cd to your home directory (using: cd ~) and open the .bashrc file in a text editor using the command:
      
      pico .bashrc

  Copy the following into this file and save it:

      PATH=$PATH:$HOME/.rvm/bin

  Finally, restart your bash session by closing and reopening your terminal window.

  Using RVM

  You can get a list of ruby versions by running the following command in your terminal window:

      rvm list known

  The version of Ruby we will use is 2.1.0 and you can install it by running the following command in your terminal window:

      rvm install ruby-2.1.0

  Set this version as the default by running the following command in your terminal window:

      rvm use 2.1.0

  Then, make sure Ruby is installed by running the following command in your terminal window:

      ruby -v

  Installing Rails

  The latest version of Rails will be installed by issuing the following command.  From your terminal window type:

      gem install rails -v 4.0

  You can verify that it was installed correctly by running the following command in your terminal window:

      rails -v

  (This will check the current installed version of Rails, which should be 4.0 or later)

#### Installing Ruby and Rails on Windows

  Installing Ruby

  Ruby can be installed simply by downloading the RubyInstaller executable: Ruby 2.0.0-p247

  Installing Rails

  Rails can be installed by typing the following into your terminal window:

      gem install rails

  You can verify that it was installed correctly by running the following command in your terminal window:

      rails -v

  (This will check the current installed version of Rails, which should be 4.0 or later)
