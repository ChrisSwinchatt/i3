# i3-groups

A fork of i3-gaps which allows the user to assign i3bar blocks to an arbitrary number of groups which collectively fill all space on the bar.

## Configuration

Configuration is the same as i3 and i3-gaps, the sole difference being the addition of a new command-line switch for i3bar which can be placed in the `i3bar_command` command of the `bar` section in `.config/i3/config`.

Grouping is configured with the `-g`/`--group` command-line option to `i3bar`, which takes a comma-separated list of the number of blocks to assign to each group. Groups are assigned an equal portion of the available bar space and are pinned to start at `x_start + px_per_group*group_number` which means a block whose size changes doesn't affect blocks in other groups.

The range of legal values for the group list is `[1,LONG_MAX)` - the number of blocks in a group is arbitrary and can exceed the number of blocks. There is also no set limit to the number of groups in the list. Blocks are assigned to groups on a 'first-come, first-served' basis, so setting a high group size or number of groups can starve blocks further down the list, which may or may not be desirable.

Any blocks that aren't allocated to a specified group are anchored to the right hand side of the bar, as in the default behaviour of `i3bar`.

**NB:** If the `-g` option is not passed, the behaviour of `i3bar` is identical to the `i3-gaps` version.

### Example

This `i3` config creates two groups containing one block each, which anchors the first `i3status` block to the left of the bar (immediately after the workspaces) and the second block to the centre. Any remaining blocks anchor to the right of the bar as usual.

```
bar {
    i3bar_command  "i3bar -g 1,1"
    # ...
}
```

