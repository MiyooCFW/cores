# MiyooCFW cores

Continuous Integration layer for generating libretro cores. List of auto-generated cores can be found at `cores_list` file in topdir.

## Cross-Compile build (MiyooCFW):

- fetch & compile & build & generate index's list
```
make release
```
NOTES:
- to not rebuild the same cores add `SKIP_UNCHANGED=1` flag to make, which generated revisions files (if needed) for build checks
- don't use jobs parallel mode in make (it will be auto invoked in build process of cores)
- build logs can be found at `$TOPDIR/logs/`
- to build specific core pass `CORES=<list cores>"` flag to make

## Native TEST build (linux):

- fetch & compile & build
```
make CORES=<list cores> CROSS_COMPILE="" PLATFORM="" dist
```
NOTES:
- the `PLATFORM=` var. is unset on purpose for test results (which are gitignored from `$TOPDIR/cores/latest` content.

- release dir pkg (zip, move, index)
```
make release
```

## INDEX:

- to manually rebuild .index file from host run:
```
make CORES_TARGET_DIR=<dirpath> INDEX=<filepath> index-rebuild
```
NOTES:
- this method is ill-advised, since git fetching files by host's different UTC locale setup can change date stat(1)
- using docker container can also ovewrite host's current date(1)
