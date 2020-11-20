# EBL
EarthOS BootLoader

You can use this in your PowerSlash-based operating systems.

## Configuring
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

## How to add EBL to PowerSlash-Builder
This has been already documented in PowerSlash-Builder readme, so please, read that first: https://github.com/adazem009/PowerSlash-Builder/blob/main/README.md

Here's a short guide on how to add EBL to your OS source tree.

Add the following lines to your `setup.sh` script:
```
rm -rf ./content/os/ebl
git clone https://github.com/adazem009/EBL ./content/os/ebl
rm -rf ./content/os/ebl/.git
rm ./content/os/ebl/LICENSE
rm ./content/os/ebl/README.md
```
You may want to add a boot entry for your OS:

If you want to use multiple boot entries:
```
echo "/boot/entry1.conf" > ./content/os/ebl/entries.list
echo "/boot/entry2.conf" >> ./content/os/ebl/entries.list
...
```
If you want to use 1 boot entry:
```
echo "/boot/entry.conf" > ./content/os/ebl/entries.list
```
As mentioned in the PowerSlash-Builder readme, you'll need to replace `os` with your partition's path.

Also make sure to include these lines in your `boot.pwsl` script to boot EBL:
```
print/"Loading EBL...",\n
run/"/ebl/init.smc"/"bg"
```
