### This script handles the following known file and directory name problems: ###

  * Spaces anywhere including at the start/end of filenames ==> `_`'s
  * Newlines embedded in filenames            ==> RANDOM hexchar a-f0-9
  * Multibyte characters of any encoding type ==> RANDOM hexchar a-f0-9
  * Backslashes anywhere in filenames         ==> RANDOM hexchar a-f0-9
  * Other special characters in filenames     ==> RANDOM hexchar a-f0-9
    * Although technically legal, dashes can cause a lot of problems if
    * you don't expect them
  * Leading dashes in filenames               ==> RANDOM hexchar a-f0-9

This program will create scripts to rename all files and directories with special
characters in the directory where it is run.

The scripts by default are named:
> `.rename_<date>_<pid>.bsh`<br />`.unrename_<date>_<pid>.bsh`

It is recommended that you review them both to make sure everything is okay and
reversible before you run them.

The default permissions set are 400 so you usually will need to chmod the files
before running them. <br />e.g. `chmod +x ./.rename_<date>_<pid>.bsh`

<b>Get the latest copy here:</b> <a href='https://code.google.com/p/r-n-f-bash-rename-script/source/browse/ren_file.bsh'><code>ren_file.bsh</code></a>

After you download a copy, put it where you want it to live and make it executable:
> `chmod +x ren_file.bsh`

If you would like to type it easier you can create an alias for it in your
home `~/.bashrc` file:
> `alias rnf='/path/where/you/put/ren_file.bsh'`

Then test the functionality, with the built-in unit test:
> `rnf -t`

If it states that it should work from where you tested it, then its working!!

Go to `/tmp` and create a new test directory with some "awful" filenames and try out
some commands to get comfortable with it.

I recommend that you not get into the habit of consistently using the `-x` auto-execute option but in a test sandbox its fine.

E.g.
> `$ mkdir -p /tmp/test_renfile; cd /tmp/test_renfile`

> `$ touch ')#($)U)DFUS)#U%#LKJL#J'`

> `$ ls `
> > `)#($)U)DFUS)#U%#LKJL#J`


> `$ rnf -x `

> `Processing )#($)U)DFUS)#U%#LKJL#J ...`

> `Done building scripts.. `

> Executing .rename\_20150125\_10120.bsh ..

> `)#($)U)DFUS)#U%#LKJL#J' -> `32567U3DFUS2dU23LKJLbJ'

> Done!!
