bagger
======

Bagger is a simple script to aid in compressing files via the command line using `zip`. Bagger was initially created to streamline the compression of chrome application folders, but can easily be ported to _any_ project at all!

##Features
- Utilizes the `zip` command; does not require anything else
- Automatically ignores files and folders listed in a `baggerignore` file in the target directory, if it exists -- similar to the way a `.gitignore` file works. This allows you to easily and consistently control which files are ignored.

##Installation
Clone the repository to your local machine:
    
    $ git clone git@github.com:bddenhartog/bagger.git

Create a symlink in a directory in your PATH (e.g. /usr/local/bin/):
    
    # you may need to run as root (or use sudo)
    $ ln -s /path/to/bagger/bagger /usr/local/bin/bagger

That's it!

##Usage
Bagger is pretty simple.
    
    $ bagger newfile /path/to/some/folder

The example above will run `zip -r` on `/path/to/some/folder`, compressing it and its contents into a file called `newfile.zip`. The compressed file(s) will be automatically placed inside the directory that it compressed.

_Note that bagger automatically adds the `.zip` extension - avoid typing it in when running the command!_

##baggerignore
You can create a file, called `baggerignore`, which will work like a `.gitignore` file; it will be fed into the `zip -r` command and any files/folders within the `baggerignore` file will be excluded from the new .zip file.

###Example baggerignore
Here's a quick example of a baggerignore file:

baggerignore
    
    private/*
    *.zip
    *.DS_Store
    somefile.txt

If `bagger new /path/to/some/folder` is ran and a `baggerignore` file exists, the files and folders listed within will be excluded from the compressed output.

Questions? Bugs?
================
    - [Report an Issue](https://github.com/bddenhartog/bagger/issues)
