# syspol - System Policy ###############################################

System policy. Inspired by the [Rule of
Separation](http://www.catb.org/esr/writings/taoup/html/ch01s06.html#id2877777).

## Environment variables ###############################################

- `SYSPOL_IGNORE_PRESERVE_PATH`: Files and directories which basename includes
  this string will be ignored for backups, mirror, synchronization and version
  control.

### Mirrors

All paths must be absolute, delimited by platform dependent character: `:` on
POSIX, `;` on Windows.

- `SYSPOL_EXTERNAL_MIRROR_BACKUP_DESTINATION_PATH`

- `SYSPOL_EXTERNAL_MIRROR_BACKUP_SOURCE_PATH`

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

## Private Syspol

Define/maintain a private Syspol project that extends the public one; if
publishing a policy doesn’t create serious security risks, consider sharing it
by integrating it into the public Syspol (see
[this](http://pedroivanlopez.com/september-2015-in-review/#update-on-syspol)
blog post).
