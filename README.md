bagger
======

Bagger is a simple script to aid in compressing files via the command line using `zip`. Bagger was initially created to streamline the compression of chrome application folders, but can easily be ported to _any_ project at all!

##Features
- Utilizes the `zip` command; does not require anything else
- Automatically ignores files and folders listed in a `baggerignore` file in the target directory, if it exists -- similar to the way a `.gitignore` file works. This allows you to easily and consistently control which files are ignored.

##Installation
This method doesn't clone the repository, which means less clutter for you. Assuming you keep your local bash scripts in `/usr/local/bin`, run the commands:

    $ curl -L https://github.com/bddenhartog/bagger/raw/master/bagger > /usr/local/bin/bagger
    $ chmod +x /usr/local/bin/bagger

You may need to use `sudo` (run as root). Repeat the process to update it if ever needed.

##Usage
Bagger is pretty simple.
    
    $ bagger newfile /path/to/some/folder

The example above will run `zip -rq` (recursive, quiet) on `/path/to/some/folder`, compressing it and its contents into a file called `newfile.zip`, which will be automatically placed inside the directory that it compressed.

_Note that bagger automatically adds the `.zip` extension - avoid typing it in when running the command!_

##baggerignore
You can create a file, called `baggerignore`, which will work like a `.gitignore` file; it will be fed into the `zip` command, and any files/folders within the `baggerignore` file will be excluded from the new .zip file.

__Example baggerignore__
    
    private/
    *.zip
    *.DS_Store
    somefile.txt

If you run `bagger new /path/to/some/folder` and a `baggerignore` file exists (in the _/path/to/some/folder_ directory), the files and folders listed within `baggerignore` will be excluded from the compressed output (which will be _/path/to/some/folder/new.zip_).

##A note about relativity
In the command `bagger somefile ~/path/to/folder`, note that `somefile` is the filename of the zipped folder you are creating. One neat thing is that this is relative to the project's directory! For example, if you run:

`bagger zipped_project/somefile ~/path/to/folder`

You will end up with: `~/path/to/folder/zipped_project/somefile.zip`. Pretty neat!

Issues?
=======
- [Report an Issue](https://github.com/bddenhartog/bagger/issues)
