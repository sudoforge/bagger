bagger
======

Bagger is a simple script to aid in compressing files via the command line using `zip`. Bagger was initially created to streamline the compression of chrome application projects, but can easily be ported to _any_ project at all!

##Features
- Utilizes the `zip` command; nothing else is required!
- Automatically ignores files and folders listed in a `.baggerignore` file in the target directory, if it exists -- similar to the way a `.gitignore` file works. This allows you to easily and consistently control which files are ignored.


##Installation
This method doesn't clone the repository, which means less clutter for you. Assuming you keep your local bash scripts in `/usr/local/bin`, run the commands (you may need to use `sudo`):

    $ curl -L https://github.com/bddenhartog/bagger/raw/master/bagger > /usr/local/bin/bagger
    $ chmod +x /usr/local/bin/bagger

##Updating
You can run the commands above to update, but why bother? There's a built-in method for updating! Just type:

`bagger --update`

##Using Bagger
Bagger is pretty simple.
    
    $ bagger newfile /path/to/some/folder

The example above will run `zip -r` (recursive) on `/path/to/some/folder`, compressing it and its contents into a file called `newfile.zip`, which will be automatically placed inside the target directory.

If you are _in_ the directory you wish to compress, you can simply type `bagger newfile .` - the period means "my current directory". 

__Auto-ignoring files with .baggerignore__

You can create a file, called `.baggerignore`, which will work like a `.gitignore` file; any files/folders within the `.baggerignore` file will be excluded from the new .zip file. For example:
    
    private/
    *.zip
    *.DS_Store
    somefile.txt

If you run `bagger new /path/to/some/folder` and a `.baggerignore` file exists in the target directory, the files and folders listed within `.baggerignore` will be excluded from the compressed folder (which will be _/path/to/some/folder/new.zip_).

##Notes
- The filename can be relative, meaning that `bagger sub-folder/somefile .` will zip your current directory (. means current directory) into a compressed file at `sub-folder/somefile.zip`.
- Bagger will automatically add the `.zip` extension if you don't include it -- which is why it hasn't been included in the examples here.

Issues?
=======
- [Report an Issue](https://github.com/bddenhartog/bagger/issues)
