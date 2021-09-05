---
layout: post
title: Solving a few problems while setting up a blog with jekyll
published: true
tag: Blog
---



## Instructions

[Instructions](https://jekyllrb.com/docs/)  to install `jekyll` are listed, but some problems arise.

1. Install all [prerequisites](https://jekyllrb.com/docs/installation/).

   > For Fedora we have to do `sudo dnf -y install ruby ruby-devel openssl-devel redhat-rpm-config @development-tools`

2. Install the `jekyll` and `bundler` gems.    

   ```bash
   gem install jekyll bundler
   ```

3. Create a new Jekyll site at

   ```bash
   jekyll new myblog
   ```

4. Change into your new directory.    

   ```
   cd myblog
   ```

5. Build the site and make it available on a local server.    

   ```bash
   bundle exec jekyll serve
   ```

6. Browse to http://localhost:4000 to check out your site!!

## Problems

### Step 2

Step 2 does not work. In [here](https://tartansandal.github.io/fedora/ruby/2020/02/05/installing-ruby-gems-on-fedora.html) a wise man explains the mess and how to properly install gems on Fedora by adding the next lines to your `.bashrc`.

```bash
# Install Ruby Gems to the default Fedora locations
export GEM_HOME=$HOME/.gem/ruby
if [[ ! -e $HOME/.gem/ruby/bin ]]
then
    ln -s $HOME/bin $HOME/.gem/ruby/
fi
```

Even after that, trying to install `jekyll` fails miserably, the problem seems to be that `g++` is needed but it is not installed by default with `@development-tools`.

```bash
[murphy@fedora ~]$ whereis bundler
bundler: /usr/bin/bundler
# So note that bundler gets installed alongside ruby or something
# because we already did step 1
[murphy@fedora ~]$ gem install jekyll # This will fail!
Fetching terminal-table-2.0.0.gem
Fetching safe_yaml-1.0.5.gem
Fetching rouge-3.26.0.gem
Fetching forwardable-extended-2.6.0.gem
Fetching liquid-4.0.3.gem
Fetching unicode-display_width-1.7.0.gem
Fetching pathutil-0.16.2.gem
Fetching mercenary-0.4.0.gem
Fetching rexml-3.2.5.gem
Fetching kramdown-2.3.1.gem
Fetching ffi-1.15.1.gem
Fetching rb-inotify-0.10.1.gem
Fetching rb-fsevent-0.11.0.gem
Fetching listen-3.5.1.gem
Fetching kramdown-parser-gfm-1.1.0.gem
Fetching jekyll-sass-converter-2.1.0.gem
Fetching jekyll-watch-2.2.1.gem
Fetching eventmachine-1.2.7.gem
Fetching sassc-2.4.0.gem
Fetching concurrent-ruby-1.1.8.gem
Fetching i18n-1.8.10.gem
Fetching http_parser.rb-0.6.0.gem
Fetching public_suffix-4.0.6.gem
Fetching jekyll-4.2.0.gem
Fetching em-websocket-0.5.2.gem
Fetching colorator-1.1.0.gem
Fetching addressable-2.7.0.gem
Successfully installed unicode-display_width-1.7.0
Successfully installed terminal-table-2.0.0
Successfully installed safe_yaml-1.0.5
Successfully installed rouge-3.26.0
Successfully installed forwardable-extended-2.6.0
Successfully installed pathutil-0.16.2
Successfully installed mercenary-0.4.0
Successfully installed liquid-4.0.3
Successfully installed rexml-3.2.5
Successfully installed kramdown-2.3.1
Successfully installed kramdown-parser-gfm-1.1.0
Building native extensions. This could take a while...
Successfully installed ffi-1.15.1
Successfully installed rb-inotify-0.10.1
Successfully installed rb-fsevent-0.11.0
Successfully installed listen-3.5.1
Successfully installed jekyll-watch-2.2.1
Building native extensions. This could take a while...
ERROR:  Error installing jekyll:
	ERROR: Failed to build gem native extension.

    current directory: /home/murphy/.gem/ruby/gems/sassc-2.4.0/ext
/usr/bin/ruby -I /usr/share/rubygems -r ./siteconf20210529-2680-q2tc5b.rb extconf.rb
creating Makefile

current directory: /home/murphy/.gem/ruby/gems/sassc-2.4.0/ext
make DESTDIR\= clean
rm -f 
rm -f libsass.so  *.o  *.bak mkmf.log .*.time

current directory: /home/murphy/.gem/ruby/gems/sassc-2.4.0/ext
make DESTDIR\=
g++ -I. -I/usr/include -I/usr/include/ruby/backward -I/usr/include -I. -I./libsass/include   -fPIC -O2  -fexceptions -g -grecord-gcc-switches -pipe -Wall -Werror=format-security -Wp,-D_FORTIFY_SOURCE=2 -Wp,-D_GLIBCXX_ASSERTIONS -specs=/usr/lib/rpm/redhat/redhat-hardened-cc1 -fstack-protector-strong -specs=/usr/lib/rpm/redhat/redhat-annobin-cc1  -mtune=generic -fasynchronous-unwind-tables -fstack-clash-protection -fcf-protection -std=c++11 -DLIBSASS_VERSION='"3.6.4"' -m64 -o ast.o -c ./libsass/src/ast.cpp
make: g++: No such file or directory
make: *** [Makefile:238: ast.o] Error 127

make failed, exit code 2

Gem files will remain installed in /home/murphy/.gem/ruby/gems/sassc-2.4.0 for inspection.
Results logged to /home/murphy/.gem/ruby/extensions/x86_64-linux/3.0.0/sassc-2.4.0/gem_make.out
# So why g++ is not installed with @development-tools???
[murphy@fedora ~]$ g++
bash: g++: command not found...
Install package 'gcc-c++' to provide command 'g++'? [N/y] y


 * Waiting in queue... 
The following packages have to be installed:
 gcc-c++-11.1.1-1.fc34.x86_64	C++ support for GCC
 libstdc++-devel-11.1.1-1.fc34.x86_64	Header files and libraries for C++ development
The following packages have to be updated:
 cpp-11.1.1-1.fc34.x86_64	The C Preprocessor
 gcc-11.1.1-1.fc34.x86_64	Various compilers (C, C++, Objective-C, ...)
 gcc-gdb-plugin-11.1.1-1.fc34.x86_64	GCC plugin for GDB
 libgcc-11.1.1-1.fc34.x86_64	GCC version 11 shared support library
 libgomp-11.1.1-1.fc34.x86_64	GCC OpenMP v4.5 shared support library
 libstdc++-11.1.1-1.fc34.x86_64	GNU Standard C++ Library
Proceed with changes? [N/y] y


 * Waiting in queue... 
 * Waiting for authentication... 
 * Waiting in queue... 
 * Downloading packages... 
 * Requesting data... 
 * Testing changes... 
 * Installing updates... 
 * Installing packages... 
 * Installing updates... 
 * Installing packages... 
 * Installing updates... 
 * Cleaning up packages... 
 * Installing updates... 
 * Cleaning up packages... 
 * Installing updates... 
 * Cleaning up packages... 
 * Installing updates... 
 * Cleaning up packages... 
 * Installing updates... 
 * Cleaning up packages... 
 * Installing updates... 
 * Cleaning up packages... 
 * Installing updates... 
g++: fatal error: no input files
compilation terminated.

[murphy@fedora ~]$ gem install jekyll # This will succeed!
Building native extensions. This could take a while...
Successfully installed sassc-2.4.0
Successfully installed jekyll-sass-converter-2.1.0
Successfully installed concurrent-ruby-1.1.8
Successfully installed i18n-1.8.10
Building native extensions. This could take a while...
Successfully installed http_parser.rb-0.6.0
Building native extensions. This could take a while...
Successfully installed eventmachine-1.2.7
Successfully installed em-websocket-0.5.2
Successfully installed colorator-1.1.0
Successfully installed public_suffix-4.0.6
Successfully installed addressable-2.7.0
Successfully installed jekyll-4.2.0
Parsing documentation for sassc-2.4.0
Installing ri documentation for sassc-2.4.0
Parsing documentation for jekyll-sass-converter-2.1.0
Installing ri documentation for jekyll-sass-converter-2.1.0
Parsing documentation for concurrent-ruby-1.1.8
Installing ri documentation for concurrent-ruby-1.1.8
Parsing documentation for i18n-1.8.10
Installing ri documentation for i18n-1.8.10
Parsing documentation for http_parser.rb-0.6.0
unknown encoding name "chunked\r\n\r\n25" for ext/ruby_http_parser/vendor/http-parser-java/tools/parse_tests.rb, skipping
Installing ri documentation for http_parser.rb-0.6.0
Parsing documentation for eventmachine-1.2.7
Installing ri documentation for eventmachine-1.2.7
Parsing documentation for em-websocket-0.5.2
Installing ri documentation for em-websocket-0.5.2
Parsing documentation for colorator-1.1.0
Installing ri documentation for colorator-1.1.0
Parsing documentation for public_suffix-4.0.6
Installing ri documentation for public_suffix-4.0.6
Parsing documentation for addressable-2.7.0
Installing ri documentation for addressable-2.7.0
Parsing documentation for jekyll-4.2.0
Installing ri documentation for jekyll-4.2.0
Done installing documentation for sassc, jekyll-sass-converter, concurrent-ruby, i18n, http_parser.rb, eventmachine, em-we
```

Also, as you can see in the comments above, `bundler` gets installed previously. So you don't need to do `gem install jekyll bundler` but only `gem install jekyll` or you will end up having two `bundler`s.

### Step 5

Step 5 does not work either. [Here](https://github.com/jekyll/jekyll/issues/8686) is the issue and a link to the solution. This seems to happen only with building the blog with `bundle exec jekyll serve`, if the blog is built with `github-pages` there is no problem at all.



> Update: both problems happen in Fedora 33 and Fedora 34.
