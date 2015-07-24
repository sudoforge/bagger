bagger
======

Bagger is a simple script to aid in compressing files via the command line using `zip`. Bagger was initially created to streamline the compression of chrome application projects (which need to be delivered to the chrome web store in a .zip folder) - but it can easily help streamline any project that requires zip compression.

###Features
- Utilizes the `zip` command; nothing else is required!
- Automatically ignores files and folders listed in a `.baggerignore` file in the target directory, if it exists -- similar to the way a `.gitignore` file works. This allows you to easily and consistently control which files are ignored.


##Installation
This method doesn't clone the repository, which means less clutter for you. Assuming you keep your local bash scripts in `/usr/local/bin`, run the commands (you may need to use `sudo`):

    $ curl -L https://github.com/bddenhartog/bagger/raw/master/bagger > /usr/local/bin/bagger
    $ chmod +x /usr/local/bin/bagger

###Updating
You can run the commands above to update, but why bother? There's a built-in method for updating!

    $ bagger --update

###Using Bagger
Bagger is pretty simple to use. Here's an example:
    
    $ bagger newfile /path/to/folder

Explanation of command:
- `bagger` fires up the script.
- `newfile` is the filename you want for your compressed folder. You can add relative paths (relative to the target directory, not your current location) to it, like `somedirectory/newfile`. If you do not end it with the .zip extension (like `newfile.zip`), Bagger will automatically add it.
- `/path/to/folder` is the path to the folder you want to compress. If you are _in_ the directory you want to compress, you can replace this path with `.` - which means "my current directory".

###Auto-ignoring with .baggerignore
You can create a file, called `.baggerignore`, which will work like a `.gitignore` file; any files/folders within the `.baggerignore` file will be excluded from the new .zip file. For example:
    
    private/*
    *.zip
    *.DS_Store
    somefile.txt

If you run `bagger new /path/to/some/folder` and a `.baggerignore` file exists in the target directory, the files and folders listed within `.baggerignore` will be excluded from the compressed folder. Note the asterisk after the folder's backslash - this is the only sure way to exclude the entire directory!

###Issues
- [Report an Issue](https://github.com/bddenhartog/bagger/issues)
