# Do something if a command block *wasn't* successful

(This is for command blocks only. For functions, [see here](/questions/functionconditions))

When a command block runs, its `SuccessCount` tag is updated. This is the value used by comparators to decide how strong a signal to output from that command block. If the command block does not succeed, its `SuccessCount` will be `0`.

We can use another command block to check whether the first block has `SuccessCount:0` after running, so that this second block will be successful when the first block fails, then run our conditionals off of this second block. The commands would look like:

    testfor @a[r=5]
    testforblock ~ ~ ~1 command_block * {SuccessCount:0}
    say Nobody is within 5 blocks!

[Example image](http://i.imgur.com/Syq4crm.png).

The first command is whatever you want to check wasn't successful.  
In the second command you must adjust `~ ~ ~1 command_block` to match the location and type of the first block. For example, it may be `~-1 ~ ~ chain_command_block`.  

The third command is conditional, and is whatever you want to happen when the first command fails.