# EBL
EarthOS BootLoader

You can use this in your PowerSlash-based operating systems.

Use the `entries.list` file to define boot entries.
Example:
```
/path/to/earthos.conf
/path/to/somethingelse.conf
```
Config file example:
```
name=EarthOS
continue=/init.smc
arg=something
```
