# redenv

Python has [virtualenv](http://www.virtualenv.org/en/latest/index.html), which
generates a simple directory structure and shell configuration implementing an
isolated Python environment using a system-provided Python interpreter.  Ruby
has both [rvm](https://rvm.io/) and
[rbenv](https://github.com/sstephenson/rbenv), but both expect to build and
install their own copies of Ruby, barely support a system-provided Ruby, and
only support a single system-provided Ruby version.

Hence `redenv` – simple `virtualenv`-like enviroments, for Ruby.

## Installation

Just drop the `redenv` `bash` script somewhere in your `PATH`.  Package and
distribute as you see fit.  The `redenv` script is only necessary when creating
new environments.  Enviroments created with it depend only on the referenced
system-provided Ruby installation.

## Usage

Create a new environment:

    $ redenv ./env
    
Create a new environment with a particular Ruby:

    $ redenv -r ruby1.9.1 ./env
    
Activate the environment for your current shell:

    $ . ./env/bin/activate
    
Then run whatever Ruby commands you want:

    $ gem install --no-ri --no-rdoc bundler
    $ bundle install
    
Deactivate it when finished:

    $ redenv-deactivate
    
Fix-up Rubygems binstubs to automatically run in the isolated environment:

    $ ./env/bin/redenv-fixup
    
Or fix-up to refer to e.g. an ultimate intallation path:

    $ ./env/bin/redenv-fixup /opt/company-name/lib/project

## Limitations

Probably only works on Debian.  Pull requests supporting other OSes welcome.

## License

Copyright © 2012 Marshall T. Vandegrift <llasram@gmail.com>

Distributed under the MIT License.
