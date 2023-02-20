# charge-threshold
Set charge thresholds on System76 laptops

On some System76 laptops it is possible to set battery charge-thresholds,
which will start/stop the battery charging at certain levels.
For example, the threshold can configured to limit the
battery to only charging to 80%. This can be used to prolong
the life of the battery.

System76 makes a utility, [system76-power](https://github.com/pop-os/system76-power),
which can be used to set these thresholds. This comes with
Pop!_OS by default, and can be installed manually on other
distros. If, however, a particular distribution is not
supported, or a user does not want to add the System76
repos/install the utility (which comes with other unrelated
functionality), the charge-thresholds can also be set via
writing to specific sysfs files (See "Via Sysfs" on
https://support.system76.com/articles/laptop-battery-thresholds/)

This simple script takes advantage of that fact, and provides a
simplee interface for reading/writing those values.

# Install

Copy the `charge-threshold` script to your `/usr/local/bin` directory.

# Basic usage:

Run `charge-threshold` with no arguments to see the current values.

Run `charge-threshold <VALUE>`, e.g. `charge-threshold 80` to set an
upper limit.

Run `charge-threshold -h` to see more details:

```
$ charge-threshold -h

Usage:

charge-threshold [LOWER_LIMIT] UPPER_LIMIT
charge-threshold [-h]

If no arguments are supplied, this will print the current lower and upper limits.

-h    Display this usage message.

LOWER_LIMIT and UPPER_LIMIT should be integers between 0 and 100. If supplied,
LOWER_LIMIT must be less than UPPER_LIMIT. If only UPPER_LIMIT is supplied, it
must be greater than the current LOWER_LIMIT.
```

