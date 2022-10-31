# tutorialspoint_learn_rails
https://www.tutorialspoint.com/ruby-on-rails/index.htm

Found a simple tutorial that didn't seem to worry about the version of Ruby or Rails. Just wanted something with a beginning, a middle, and an end.


# Linode VM Setup
## Update Linux libs
 I am running all of this as the ROOT user. I usually create the `~/bin/update.sh` script with these commands:
* `sudo apt upgrade`
* `sudo apt update -y`
* `sudo apt autoremove`
* `sudo apt autoclean`

## Install RVM
Using the [RVM Install](https://rvm.io/rvm/install) page, I was directed to [this GitHub page](https://github.com/rvm/ubuntu_rvm) for instructions on how to install RVM on Ubuntu Linux. Here are the steps I did:
* `gpg --keyserver hkp://pgp.mit.edu --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB`
* `apt-get install software-properties-common`
* `apt-add-repository -y ppa:rael-gc/rvm`
* if needed, update the Linux libs
* `apt-get install rvm`
* `usermod -a -G rvm $USER`

I need to figure out how to get the Visual Studio Code to open a terminal as a login session. Until I do that, I will need to
`/bin/bash --login`

Update RVM to the latest version with this command
* `rvm get stable`

You can uninstall RVM with the command:
* `rvm implode`

## Install Ruby
I wanted to install a newer version of ruby. I had 2.6.6 and wanted to install 2.7.2. When I used the command `rvm install 2.7` I got an error. I think the problem was that RVM needed a specific version of openssl to build parts of ruby 2.7.2. I ran this command `rvm pkg install openssl` and was told to use the `autolibs`option and not `pkg` option.

I tried this command:
* `rvm install 2.7`. => ERROR
* `rvm install --autolibs=packages 2.7` => ERROR

These two seemed to work: 
* `rvm pkg install openssl`
* `rvm reinstall 2.7.2 --force -C --with-openssl-dir=/usr/share/rvm/usr`

To get `rvm use 2.7.2` to work I had to open the shell with `--login` option
  * `/bin/bash --login`

