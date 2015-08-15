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
