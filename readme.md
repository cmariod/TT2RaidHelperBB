# TT2RaidHelper

Sets of command for blargbot to help planning for Raid in Tap Titan 2 Game.

Blargbot is a discord bot that can do plenty of things included custom script using bbtag (BlargBotTag) that looks like custom built javascript.

[How to invite Blargbot](https://blargbot.xyz/)

## RaidHelper Setup
For Optional QoL purposes, I personally change the default prefix (`b!`) used by bb to something shorter, for example: `.`. This can be done by executing below command in discord where bb exists.

`b!prefix add .`

Once blargbot is invited to your discord server, you can start copy pasting script in this repo into blargbot by using [BBTag IDE](https://blargbot.xyz/tags/editor). Note that file name in this repo indicated the cc (custom command) name.

Or you can manually do that in discord by executing command below, replace commandname with filename and code with file contents.

`.cc set <commandname> <code>`

## Required CC
- .haspermissions
- .loadraiddata
- .seed
- .previewseed
- .raidbuffs
- .raiddebuffs
- .raidset
- .summary

## Permissions
Open up `.haspermissions` and change the hasrole value accordingly to your intended role audience.

You can get the list of role name and it's id by using `.roles` and copy out the numeric id into `.haspermissions` command.

## Setup and Titan Strategy

First you'll need to execute `.loadraiddata` to uh load raid data.

Set up a new hidden/dummy channel to subscribe to GH weekly seed. Whenever you want to switch seed, go to this channel and copy the message link and run `.seed <message-link-here>`.

Titan default strategy, if you think that you are adopting unorthodox strategy for particular titan, you should check and probably change `.titan default` this will list the default strategy for each titan ignoring debuff.

When you need to be creative to be efficient in killing certain titan like mohaca limbs only in let's say raid 4-4. You can check if the strategy for that debuff by running `.titan 4-4`. Default mohaca is to attack head and for this debuff you don't have to attack head, so run `.titan moh 4-4 00111111` then run `.titan 4-4` to confirm. The shortform of titan name can be 2 or more characters so long match the starting of titan name. And that will set the strategy for any zone with that debuff.

## Operations

Typically you need have unbuff average of your clan inclusive of loyalty, if you don't have already or if you think it's inaccurate, you might want to burn 1 close to neutral buff debuff raid to get your unbuff with this algorithm. 

When you are planning raid for next week post reset, you'll need to load next week reset by using `.seed` (see Setup above), then find which raid zone is best for the clan and then start the raid. So this process can be broken down to 5 steps.

1. `.raidbuffs` to see which raid currently have the best buff debuff. e.g. `.raidbuffs 4-10` will show 8 raid buff and debuffs starting from 4-10.

2. `.previewseed` to simulate your raid in particular zone with the default titan strategy. e.g. `.previewseed -r 4-25 -d 16.25 -m 45` will simulate 4-25 with 16.25 unbuffed average with 45% morale. There's no mechanics to adopt team tactics, but generally adding extra the average would work. Example if you use tactics for first 3 cycle in 6 cycle raid = 0 2 4 4 4 4 it will average to additional 3% per cycle, and with max starting morale (45%) you should get quite accurate estimate with 48%. *at least this works for me*

3. When you need to be creative with strategy for titan in a particular raid do so first then rerun `.previewseed` with all same parameters.

4. once you found the zone that fits the bill, executes `.raidzone <tierzone>`, e.g. `.raidzone 3-49`. This will mark the last previewed 3-49 as active started raid, and will enable `.summary` command.

5. `.summary` is to print out predictions on when certain phases will come in the cycle like prism, iv, vm. Optional parameter -d might be used with `.summary` to adjust predictions mid raid with the current trending average in case there's major event like bundle drops or dust promo titan chest opening tournament.

## Help

General help of each command can be read by either running the command with no parameter (generally) or with -h if that doesn't work. This is because `.summary` is designed to run without parameters by default.