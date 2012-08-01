# chruby

Simple Ruby switcher.

## Features

* Simply modifies `$PATH`.
* Correctly sets `$GEM_HOME` and `$GEM_PATH`.
* Adds `$GEM_HOME` and `$GEM_PATH` to `$PATH`.
* Additionally sets `$RUBY_PATH`, `$RUBY_VERSION` and `$RUBY_ENGINE`.
* Defaults to the system Ruby.
* Fuzzy matching of Rubies by name.
* Small (~80 LOC).

## Install

    wget https://github.com/postmodern/chruby/downloads/chruby-0.1.0.tar.bz2 \
         https://github.com/postmodern/chruby/downloads/chruby-0.1.0.tar.bz2.asc
    gpg --verify chruby-0.1.0.tar.bz2.asc churby-0.1.0.tar.bz2
    tar -xjvf chruby-0.1.0.tar.bz2
    cd chrub-0.1.0/
    make install

## Configuration

Add the lines following to your `~/.bashrc` or `~/.profile` file:

    . /usr/local/etc/profile.d/chruby.sh
    
    RUBIES=~/src/{ruby,jruby,rubinius}*

### System Wide

Create a `/etc/profile.d/chruby.sh` file, containing the following:

    . /usr/local/etc/profile.d/chruby.sh
    
    RUBIES=(
      /usr/local/ruby-1.8.7-p370
      /usr/local/ruby-1.9.3-p194
      /usr/local/jruby-1.6.7.2
      /usr/local/rubinius
    )

## Examples

List available Rubies:

    $ chruby
       ruby-1.8.7-p370
       ruby-1.9.3-p194
       jruby-1.6.7.2
       rubinius

Select a Ruby:

    $ chruby 1.8
    $ chruby
     * ruby-1.8.7-p370
       ruby-1.9.3-p194
       jruby-1.6.7.2
       rubinius
    $ echo $PATH
    /home/hal/.gem/ruby/1.8.7/bin:/usr/local/ruby-1.8.7-p370/lib/ruby/gems/1.8/bin:/usr/local/ruby-1.8.7-p370/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/hal/bin
    $ echo $GEM_HOME
    /home/hal/.gem/ruby/1.8.7
    $ echo $GEM_PATH
    /home/hal/.gem/ruby/1.8.7:/usr/local/ruby-1.8.7-p370/lib/ruby/gems/1.8

Switch back to system Ruby:

    $ chruby system
    $ echo $PATH
    /usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/hal/bin

Switch to an arbitrary Ruby on the fly:

    $ chruby_use /path/to/ruby
