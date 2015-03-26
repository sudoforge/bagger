bagger
======

Bagger is a simple script to aid in compressing files via the command line using `zip`. Bagger was initially created to streamline the compression of chrome application folders, but can easily be ported to _any_ project at all!

##Features
- Utilizes the `zip` command; nothing else is required!
- Automatically ignores files and folders listed in a `.baggerignore` file in the target directory, if it exists -- similar to the way a `.gitignore` file works. This allows you to easily and consistently control which files are ignored.

##Installation
This method doesn't clone the repository, which means less clutter for you. Assuming you keep your local bash scripts in `/usr/local/bin`, run the commands:

    $ curl -L https://github.com/bddenhartog/bagger/raw/master/bagger > /usr/local/bin/bagger
    $ chmod +x /usr/local/bin/bagger

You may need to use `sudo` (run as root). Repeat the process to update it if ever needed.

##Usage
Bagger is pretty simple.
    
    $ bagger newfile /path/to/some/folder

_Note that bagger automatically adds the `.zip` extension if you don't include it._

The example above will run `zip -r` (recursive) on `/path/to/some/folder`, compressing it and its contents into a file called `newfile.zip`, which will be automatically placed inside the target directory.

If you are _in_ the directory you wish to compress, you can simply type `bagger newfile .` - the period means "my current directory".

##.baggerignore
You can create a file, called `.baggerignore`, which will work like a `.gitignore` file; any files/folders within the `.baggerignore` file will be excluded from the new .zip file.

__Example .baggerignore__
    
    private/
    *.zip
    *.DS_Store
    somefile.txt

If you run `bagger new /path/to/some/folder` and a `.baggerignore` file exists in the target directory, the files and folders listed within `.baggerignore` will be excluded from the compressed folder (which will be _/path/to/some/folder/new.zip_).

##A note about relativity
In the command `bagger somefile ~/path/to/folder`, note that `somefile` is the filename of the zipped folder you are creating. One neat thing to note is that this is relative to the project's directory! For example, if you run:

`bagger zipfiles/somefile-v1.0 ~/path/to/folder`

You will end up with: `~/path/to/folder/zipfiles/somefile-v1.0.zip`. Pretty neat! I personally use a directory called "packaged" in my projects that contain all of my `bagger`-fied projects.

Issues?
=======
- [Report an Issue](https://github.com/bddenhartog/bagger/issues)
