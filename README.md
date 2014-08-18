XVIM 0.1.0
==========

XVIM is a light wrapper around vim designed to make writing scripts extremely
convenient, giving you a vim buffer that's already set up with a correct
filetype and shebang line. It was especially designed for writing quick, experimental
scripts.

When you give xvim a filename, it will try and figure out its filetype and add the
correct shebang line to the top of the file. If the file extension is absent or
unknown, xvim will default to using filetype=sh and using `#!/bin/bash` as a
shebang. Of course, all of this can be overridden from the command line, so it's
perfectly possible to create a script in another language without being bound to
file extensions.

Xvim also creates files with correct permissions, so that when you've finished
editing your file, it's immediately ready for invocation. If you want, you can
even save those keystrokes: simply pass -e to xvim, and your script will be run
automatically when you exit vim.

If no filename is present, xvim will load the 'scratch' file. The scratch file is an
out of the way file (by default it is located at /tmp/xvim) that allows for writing
quick scripts to accomplish one off tasks or small experiments. The scratch file
is assumed to be a shell script: if you wish to use a different language, invoke
xvim with the -f flag.

###Basic usage:

    With filenames:
    $ xvim myscript.py              # open vim with filetype=python and #!/usr/bin/env python
    $ xvim -e dostuff               # edit the bash script dostuff, execute it upon exiting vim
    $ xvim -E 'foo bar' dostuff     # same as above, passing foo bar on the shell
    $ xvim -f ruby barefile         # write a ruby script, skip the extension

    Scratch file usage:
    $ xvim                          # edit the current scratch file
    $ xvim -o                       # edit the scratch file, overwriting the current one
    $ xvim -e                       # execute the current scratch file
    $ xvim --rm                     # deletes the current scratch file
    $ xvim -f coffee                # use coffeescript in the scratch file


