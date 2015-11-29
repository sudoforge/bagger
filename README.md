## bagger

Bagger is a wrapper around the `zip` utility. It streamlines the process of compression with a simpler command structure, as well as the ability to automatically ignore files and directories by reading a file named `.baggerignore` in your targets' directory, if it exists.

**History**  
Bagger was initially created to bypass the tedious process of ignoring directories and files when compressing Chrome Applications (Google requires projects to be uploaded to its Web Store in a `.zip` file). Upon realizing its utility as a general-purpose tool, it was released publicly.

#### Features
- Utilizes the `zip` command; nothing else is required!
- Automatically ignores files and folders listed in a `.baggerignore` file in the target directory, if it exists -- similar to the way a `.gitignore` file works. This allows you to easily and consistently control which files are ignored without having to worry about typing in the exclusion list each time you need to compress your project.


#### Installation
This method doesn't clone the repository, which means less clutter for you. Assuming you keep your local bash scripts in `/usr/local/bin`, run the commands (you may need to use `sudo`):

    $ curl -L https://github.com/bddenhartog/bagger/raw/master/bagger > /usr/local/bin/bagger
    $ chmod +x /usr/local/bin/bagger

Change the destination directory if you want to have the script located somewhere else.

## Commands and Options
```
bagger {-v | -u | -h} DESTINATION TARGET {ADDITIONAL TARGETS}

    -v | -V | --verbose:
        Prints out files that are added to the compressed directory

    -u | -U | --update:
        Updates bagger from this repository

    -h | -H | --help:
        Displays this help text
```

#### Auto-ignoring with .baggerignore
You can create a file, called `.baggerignore`, which will work like a `.gitignore` file; any files/folders within the `.baggerignore` file will be excluded from the new .zip file. For example:

    private/*
    *.zip
    *.DS_Store
    somefile.txt

If you run `bagger foo /path/to/target` and a `.baggerignore` file exists in the target's directory, the files and folders listed within `.baggerignore` will be excluded from the compressed folder.

Note that the directory we want to exclude in this example, `private/*`, has an asterisk at the end. This is required to exclude directories and their contents from being included in the compressed output.

### Issues
- [Report an Issue](https://github.com/bddenhartog/bagger/issues)
