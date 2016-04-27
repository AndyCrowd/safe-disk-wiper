## safe-device-wiper
### Using additional security checks to avoid wiping of the mounted partitions.

#### It is dangerous to wipe a device directly from your working system because if you occasionally will do typo of the destination device it will destroy it!

# The script contains no activated patterns but you can add own or uncommend existing by editing the script.

# The script will help you by doing checks before starting to wipe them.

# wipe-safe [options] "/dev/path_to_device"

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

WARNING !!!!!! 
PLEASE KEEP SAFETY SYNTAX WHEN ADDING OWN WIPING TOOLS'


