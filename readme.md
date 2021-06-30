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
- .preview
- .raidbuffs
- .raidset
- .summary

## Permissions
Open up `.haspermissions` and change the hasrole value accordingly to your intended role audience.

You can get the list of role name and it's id by using `.roles` and copy out the numeric id into `.haspermissions` command.

## Operations
Typically you need to already have unbuff average of your clan including loyalty. first you'll need to execute `.loadraiddata` to uh load raid data.

Occassionally you might need to run `.raidbuffs` to get list of known buff and debuff to be used as input for `.preview`.

After weekly seed reset, you'll need to find which raid zone is best for the clan and then start the raid with or without morale in. So this process can be broken down to 3 commands.

1. `.preview` few important parameter required for this command to work: r,b,d,1,2,3,s and some optional parameter like m for non minimum morale and p for clan member count. For full list of detail of what each parameters means executes `.preview -h` for help. Long story short the full parameters looks something like below

`.preview -r 3-49 -d 5.5 -m 29.2 -b spe -1 afc|11111111 -2 bsd|10111111 -3 rd|01111111 -s 31123 -p 50`

- raid zone: 3-49
- unbuff average: 5.5M
- morale: 29.2%
- buff: support effect
- debuff titan 1 on raid screen: affliction chance
- strategy titan 1: kill all part
- debuff titan 2 on raid screen: burst damage
- strategy titan 2: no torso
- debuff titan 3 on raid screen: armor damage
- strategy titan 3: no head
- titan sequence on raid screen: 3 1 1 2 3
- clan with 50 member

2. once you found the zone that fits the bill, executes `.raidzone <tierzone>`, e.g. `.raidzone 3-49`. This will mark the last previewed 3-49 as active started raid, and will enable `.summary` command.

3. `.summary` is to print out predictions on when certain phases will come in the cycle like prism, iv, vm. Optional parameter -d might be used with `.summary` to adjust predictions mid raid with the current trending average in case there's major event like bundle drops or dust promo titan chest opening tournament.