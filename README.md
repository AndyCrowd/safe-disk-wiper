# safe-disk-wiper
Using additional security checks to avoid wiping of mounted partitions.

It is dangerous to wipe a device directly from your working system because if you occasionally will do typo of the destination device it will destroy it!

# The script contains no activated patterns but you can add own or uncommend existing by editing the script.

The script will help you by doing checks before starting to wipe them.

Options:
wipe-safe [options] "/dev/path_to_device"

-a , --add-wipe-loop [number]	- set amount of additional loops

		Defaut = 0

-c , --confirm [yes/1 , no/0]	- disable confirmation before continue

		Default = yes

-s , --safety [0/disable , 1/low , 2/max]	- set safety level

	0/disable	- will not check if any of the partitions is mounted

	1/low       - will stop only if destination partition is mounted

	2/max       - will stop if at least one partition is mounted

		Default = max
