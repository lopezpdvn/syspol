# syspol - System Policy ###############################################

System policy. Inspired by the [Rule of
Separation](http://www.catb.org/esr/writings/taoup/html/ch01s06.html#id2877777).

Syspol extends standard Linux/Unix practice including the [File Hierarchy
Standard](http://www.linuxfoundation.org/collaborate/workgroups/lsb/fhs).

## Private Syspol

Define/maintain a private Syspol project that extends the public one; if
publishing a policy doesn’t create serious security risks, consider sharing it
by integrating it into the public Syspol (see
[this](http://pedroivanlopez.com/september-2015-in-review/#update-on-syspol)
blog post).

## Time based directory structure ######################################

A *time base directory structure* with resolution *X* is a simple hierarchy for
storing files in a predictable and manageable way. X can be one of *year*,
*month*, *day*, *minute* or *second*. It's not necessary for the structure to
have node directories for every time unit.

### Examples ###########################################################

The root of a time based directory structure with resolution `year`

    $ tree -d .
    .
    ├── 2014
    └── 2015

    2 directories

The root of a time based directory structure with resolution `month`

    $ tree -d .
    .
    ├── 2014
    │   ├── 01
    │   └── 09
    └── 2015
        ├── 01
        ├── 09
        ├── 10
        └── 11

    8 directories

## Logging

Let `APPROOT` be the root directory of application/environment data, log files
are stored in time based directory structure with resolution *month* in
`$APPROOT/var/log`. For example:

    $APPROOT
      /var
        /log
          /2015
            /01
            /02
            /03
            /04

Each month directory stores the log files.

## Application locks

Lock resources with files stored at `$APPROOT/var/lock`.

### Single application instances

Sometimes you need to be sure that at all times only one instance of an
application or script is running. Let `APPROOT` be the application root path of
an application named `xyz` that is currently running, then the lock files
exists `$APPROOT/var/lock/LCK..xyz`.

When `xyz` starts, it checks if the lock file exists. If the lock exists then
`xyz` fails and exits with an error code. Otherwise it creates the lock file
and executes normally. When finished `xyz` deletes the lock file.
