# Installation and Setup

## Setting Up a Ruby Version Manager with `rvm`

A Ruby Version Manager is a program that sets up multiple versions of Ruby in your system allowing you to switch versions between projects. In this case we will be using `rvm`.

### Mac OS X or Linux

Install `rvm` via: [https://rvm.io/](https://rvm.io/)

### Windows

We can install `rvm` via [https://github.com/magynhard/rvm-windows](https://github.com/magynhard/rvm-windows) which will require [NodeJS](https://nodejs.org/en).

Another option would be to install `WSL2` or [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/install) which basically allows you to install `rvm` the normal way (see `Mac OS X or Linux` section). If on Linux, check out `Command Line Basics` for common commands to work with a shell / terminal.

### Basic Usage

**Check for Currently Installed Versions**

Checks for the currently installed versions of Ruby in the system.

```bash
rvm ls
```

Indicators for a version are as follows:

```
# => - current
# =* - current && default
#  * - default
```

**Check Available Versions for Installation**

Lists all available Ruby installations.

```bash
rvm list known
```

**Install / Remove a Version**

Installs a version of Ruby in the system.

```bash
rvm install [version]
```

Similarly, removing a version would be:

```bash
rvm remove [version]
```

**Use a Version**

Activate an installed version of Ruby

```bash
rvm use [version]
```

Or if you want to use a certain version by default:

```bash
rvm use [version] --default
```

## Gems

A ruby library is called a `gem`. Gems are managed by a command line prompt called `gem` and are hosted in a remote repository called [RubyGems](https://rubygems.org/).

To install a gem in your current Ruby installation and all its dependencies, issue the following command:

```bash
gem install [gem-name]
```

Because `rails` itself is also a `gem`, we can install Ruby on Rails by issuing the command:

```bash
gem install rails
```

Verify that Rails is installed:

```bash
rails -v
```

Take note that gems are installed for your Ruby installation (globally). Which means all Ruby scripts ran within the Ruby installation that has a particular gem can use that gem. We can use a gem by the code snippet:

```ruby
require 'gemname'
```

Although this will allow us to use multiple gems for all sorts of usecases, in a Rails project, we would want gems and their corresponding versions to be managed independently per project and not use the globally installed ones.

## Exercise

1. Install version `3.4.2` of Ruby
2. Use version `3.4.2` as your default Ruby version
3. Install `rails`
4. Create a new Rails project called `test`:

```bash
rails new test
```

5. Enter that project:

```bash
cd test
```

6. Run the Rails server

```bash
rails server
```
