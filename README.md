# tutorialspoint_learn_rails
https://www.tutorialspoint.com/ruby-on-rails/index.htm

Found a simple tutorial that didn't seem to worry about the version of Ruby or Rails. Just wanted something with a beginning, a middle, and an end.


# Linode VM Setup
## Update Linux libs
 I usually create the `~/bin/update.sh` script with these commands:
* `sudo apt upgrade`
* `sudo apt update -y`
* `sudo apt autoremove`
* `sudo apt autoclean`

## Install RVM and Ruby
I already installed RVM and didn't write down the staps I used.

Update RVM to the latest version with this command
* `rvm get stable`

## Install Ruby
I wanted to install a newer version of ruby. I had 2.6.6 and wanted to install 2.7.2. When I used the command `rvm install 2.7` I got an error. I think the problem was that RVM needed a specific version of openssl to build parts of ruby 2.7.2. I ran this command `rvm pkg install openssl` and was told to use the `autolibs`option and not `pkg` option.

I tried this command:
* `rvm install 2.7`. => ERROR
* `rvm install --autolibs=packages 2.7` => ERROR

These two seemed to work: 
* `rvm pkg install openssl`
* `rvm reinstall 2.7.2 --force -C --with-openssl-dir=/usr/local/rvm/usr`

To get `rvm use 2.7.2` to work I had to open the shell with `--login` option
  * `/bin/bash --login`

