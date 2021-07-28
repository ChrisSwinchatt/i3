# i3-groups

A fork of i3-gaps which allows the user to assign i3bar blocks to an arbitrary number of groups which collectively fill all space on the bar.

Configuration is the same as i3 and i3-gaps, the sole difference being the addition of a new command-line switch for i3bar which can be placed in the `i3bar_command` command of the `bar` section in `.config/i3/config`.

## Example configuration

Configuration is with the `-g`/`--group` command-line option to `i3bar`, which takes a comma-separated list of the number of blocks to assign to each group.

```
bar {
    i3bar_command  "i3bar -g 1,1"
    # ...
}
```
This config creates two groups containing one block and a third group containing all remaining blocks. The first group is anchored to the left of the bar (immediately following the workspace list), the second is centred on the bar, and the final group is anchored to the right of the bar.
