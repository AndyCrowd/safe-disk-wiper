# ``Wipe safe! Avoid typo!``
### Using additional security checks to avoid wiping of the mounted partitions.

###### It is dangerous to wipe a device directly from your working system because it is easy to do a typo of the destination device that will damage the system!

###### The script will help you by doing checks before starting the wiping.
###### Only to preview what can be done don't use one of the following options: ``--no-dry-run`` or ``--nd`` with combination of ``--order``or ``-o``. If one of them is missing it will not start wiping.
###### First use option ``--order`` to chose which of the tools you want to use. To see currently available use as the first option:
```wipe-safe --show-me -e NO_DRY -e methods```
###### Then preview how it will look like when starting wiping. This example will start wiping first with ``dd`` and ``/dev/urandom`` as a source, after that will start ``dd`` with the source ``/dev/zero``. The order of tools must be separated with: ```,```
```wipe-safe --order ddr,ddz /dev/sdX(Y)```
###### To use same order of tools more than once you can use option ``--add-wipe-loop`` or ``-a``. This example will preview wiping with additional 33 rounds the combination of `urandom/zero/urandom`:
```wipe-safe --order ddr,ddz,ddr --add-wipe-loop 33 /dev/sdX(Y)```

## You are allowed to add own patterns or tools inside the script.
#### To get an overview of code parts where you can add own or show available use:
#### wipe-safe --show-me -e methods -e NO_DRY -e OPTIONS
>### WARNING !!!!!! 
>### PLEASE KEEP SAFETY SYNTAX WHEN ADDING OWN WIPING TOOLS

```
wipe-safe [options] "/dev/path_to_device"

The device path must be used as the last option!

-a , --add-wipe-loop [number]	- set amount of additional loops for order
		Defaut = 0
-o , --order [order of methods] - set order of wiping commands
	Example: -o dd,ddz,cp,cpz
--sm , --show-me [grep pattern]   - searching content in this script, 
    supporting grep syntax and should be used as the first option.
	Helpful to list available patterns that can be used with command "--order"
	and find places where you can add own tools.
	Example:	
	  --show-me -e methods -e NO_DRY -e OPTIONS
	  
-c , --confirm [yes/1 , no/0]	- disable confirmation before continue
		Default = yes
-s , --safety [0/disable , 1/low , 2/max]	- set safety level
	0/disable	- will not check if any of the partitions is mounted
	1/low       - will stop only if the destination partition is mounted
	2/max       - will stop if at least one partition is mounted
		Default = max
--nd , --no-dry-run	- By default it only shows what can be done
```
