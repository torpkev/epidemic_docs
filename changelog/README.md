![Epidemic](../images/header.png)

[Home](https://torpkev.github.io/epidemic_docs)

# Change Log

## 1.7.6 - New time limited invincibility

This update allows you to give a player time limited invincibility. But first a little history.

When Epidemic was first written, the epidemic.invincible permission existed - this would protect the player from all harm. But, people kept leaving themselves in op and had the permission, so never got sick. Following on from Domain I changed the behavior to use bypass mode. So a staff member would actively have to type in /epidemic bypass in order to become invincible.

This new invincible functionality gives players time limited invincibility via a command, it also includes a config option which will give new players some time to get acclimated to the server before being afflicted. It does NOT impact /epidemic bypass which is still in use.

###New commands

Both new commands REQUIRE epidemic.admin permission.

    /epidemic invincible <player uuid or name (if online)> <number of days>

If using player name, the player MUST be online at the time.

Number of days is the number of days from the in-game days - so if it is day 14, and you pick number of days = 7, they couldn't be afflicted until day 21

    /epidemic day

This simply returns the in-game day according to Epidemic (this is NOT the same as server day due to some plugins moving that around as they expand out days/seasons/time etc.) It is simply an arbitrary day that Epidemic will use to track game days.

###Configuration Changes

If you do not have a plugins\Epidemic\config\server.yml file, please create one like so

    day: 0
    main_world: world

Use the name of whatever your main world is if it is not world - this is the world that Epidemic will pull the current time from.

Add the following to config.yml - set to 0 to disable

    new_player_invincible_days: 7

If you translate Epidemic into another language, add the following to lang.yml (and then translate as needed)

    command_invalid_player: "&cERROR &r- Invalid player"
    command_epiinvicible_usage: "&lUsage: &r/epidemic &binvincible <player name or uuid> <number of days>"
    command_epiinvicible_invaliddays: "&cERROR &r- You must enter a valid number of days (at least 1)"
    command_epiinvicible_success: "&aPlayer has been set as invincible for <%days%> game days"
    command_infect_invincible: "&cERROR &r- Player is invincible"
    command_day: "&rIt is day <%day%>"

## 1.7.5 - Consumables Bug Fix

This update addresses a single bug that prevents consumable remedies from being consumed if they are food or drink based.

For example, boiled water has drink: true, and item_consumed: true - but was not reading item_consumed, and incorrectly setting to false.

This resulted in consumable items never running out.

## 1.7.4 - 1.20 support added

Support added for Minecraft 1.20

Removed some mutation/vaccine code and notes (its still coming, just split the branches)

Startup spam has been cleanup - comma delimited lists of ailments and remedies instead of 1 line per

Hotspots with no particles were throwing warnings on startup - now they don't

## 1.7.3 - Bug Fix

This update addresses a bug that threw a null exception error if you did not have a world called world

Please add the following to \plugins\Epidemic\config\server.yml and replace WORLDNAME with the name of your main world

    main_world: WORLDNAME

## 1.7.2 - Natural Healing

This update enables the natural cures for ailments (as well as laying the groundwork for vaccines)

Up until now, if you get a wound, a burn, a cold, or whatever ailments you have set up, you're stuck suffering with them until either you have them cured, or if the rare chance of healing while sleeping kicks in.

This update adds a new option in the ailments files that gives a maximum number of days a player will have the ailment for

    # Number of days until the ailment naturally heals - set to 0 if it does not naturally heal
    natural_cure_days: 2

Leave this value as 0 to have it not apply

## 1.7.1 - Hotspots!

What IS a hotspot?
- A hotspot is a block from which an ailment can spread over a set distance

For example, if your server was to have a crashed meteorite, you could set a hotspot in the center of the impact crater and have the ailment spread over a 10-20 block radius, and anyone coming within that area could come down with radiation sickness or space rabies

Do I HAVE to use a hotspot?
- No, of course not, if you don't want to use hotspots, just don't set any up

How do the users know where the hotspot is?
- Right now, when the player gets close, (optional) particle effects can show the hotspot center. In the future, there may be an optional message to screen, but for now, just particles, it'll be a nice surprise for them!

Do the players automatically get sick in that area?
- No, you set up the chance of ailment in the same way you do for other ailments, if you want it to just be a minor chance they get sick in this area, set it low, if you want them always to get sick, set it high

What kind of sickness do they get?
- Any you want to set up - for the sample, I included radiation sickness - this ailment can't be gotten by any other means except by the hotspot, however, you can give them any ailment you choose

How do you get cured from the hotspot ailments?
- In the exact same way you do currently, create a remedy (in the sample, potassium iodide)

Why hotspots and not vaccines!?
- The vaccine code is taking longer than I'd like (BECAUSE IT'S AWESOME btw), and the hotspot code was already ready to go, so releasing 1.7.1 as a short term update, with vaccines coming!

How do I set up a hotspot?
- If you're a new user, a blank hotspot file is created.  If you're an existing player, you'll need to create the folder and file manually - head over to default files for samples!

## 1.7.0.3 - Bug fix

---
Fixes an issue which caused an item to be removed from the hand of someone being healed, instead of the remedy being removed from the person applying it

## 1.7.0.2 - Bug fix

---
Fixes a NullPointerException in PlayerInteractEvent that did not impact gameplay, but did spam the console

## 1.7.0.1 - Bug fix

Hazmat suit could throw a null error during ailment checking if there was something in the armor slots that was not the hazmat suit

Equipment files will now auto-generate if they do not exist.

---
## 1.7.0 - Bio-Warfare update

This is a BIG update, and impacts multiple configuration files, language file, as well as significant gameplay updates.

Bio-Warfare is added with the introduction of Infected Arrows, Infected Splash Potions, and Infected blood filled syringes.

Protective Equipment has been added (Hazmat Suit & Gas Mask)

First (but not last) multi-block Epidemic equipment has been added with the Incubation Chamber (used to culture infected blood into workable samples)

New symptom:  Sudden Death - Players can now be at risk of randomly dropping dead from an illness

New Ailment Cause: Weapon damage - When a player is hurt with a weapon (sword, axe, stick) - Set this if you don't want people getting injured from being punched (for example, broken leg)

Health Command now reports no ailments correctly, previously, if you hadn't been told you're sick yet, it wouldn't list the ailment, but the No ailments found message was left off, which could alert the player they were sick with something.

Thirst damage is now configurable in config.yml

    #Amount of damage to inflict on the player if they reach 0 hydration left
    thirst_damage: 1

Biomes can now influence if a player gets sick - configurable in the ailment yml file (example: bubonic_plague.yml)

    # Applies a modifier based on biome.  A negative number would indicate less chance
    # while a positive number would indicate more chance.  If we had an infectious_chance
    # of 100, and a swamp modifier of 24900 it would jump to 25000 every minute. So a random
    # number of 1-100000 would now be <= 25000 would get you sick instead of the 100, so a
    # 1/4 chance instead of a 1/1000.  You could also have an infectious_chance of 0, and
    # a positive biome_infectious_chance for the biome you're in, meaning you could only
    # get sick in that particular biome.  If you use a negative biome infectious chance and
    # is less than the infectious chance, the overall infectious chance could drop below
    # 0, which would mean you cannot get that ailment in that biome.
    # In example below, being in a swamp would add 500 to the 100 already applied, so a
    # (500+100) = 600 in 100000 chance, but if you were in a desert, you'd have (100 + -100)
    # leaving a 0 chance and therefore meaning you could not get it in the desert. However,
    # if you were in Plains, your chance would be (100 + 0) = 100 as plains is not included
    # Note: example does not take contagious chance boost into consideration
    
    biome_infectious_chance:
      SWAMP: 500
      DESERT: -100

You can now cure some ailments by sleeping - configurable in the ailment yml file (example, wound.yml)


    # Chance of the ailment being cured while you sleep.  This number is out of 1000
    # Lower numbers have less chance of curing the player.  Set to 0 to never cure the
    # player, or 1000 to always cure them when sleeping
    
    cure_with_sleep_chance: 300

    # Message to send to the player when they are cured by sleeping
    
    cure_with_sleep_message: "The wound closed over while you were sleeping"

Adds full support for 1.19.*

Finally, a ton of bug fixes and optimizations, with massive amounts of code being rewritten

---
## Change Log 1.6.9.7 - Bug Fix

This is a very minor update which addresses changing API locations in the Domain plugin with Domain 1.9.12

No need to update unless you're also running Domain, and have updated Domain.

---
## Change Log 1.6.9.6 - Bug Fix

This update addresses a single bug which can cause an unhandled error message in console when using goop with the base installation and no changes.

The Remedies\goop.yml file should have its cure values changed as shown:

    # List of ailments that the remedy cures
    cures:
      - burn
      - broken_leg
      - typhus
      - common_cold

It was previously trying to cure some ailments that are not included in the base install, and was throwing an error.

This error is now handled gracefully, however, please update your goop.yml files accordingly anyway.

---
## Change Log 1.6.9.5 - Bug Fix

In my excitement to push out an update, I didn't check what would happen if a soft-depend was missing, causing some undue issues.

---
## Change Log 1.6.9.4 - Added WorldGuard integration

This update adds a feature requested by a user on Discord, and expands WorldGuard integration.

You can now specify in the config file if you want particular regions to always prevent new ailments or symptoms, regardless of which flag is on them.

To add this functionality, modify your config.yml file and add the following:

    # List of WorldGuard region names where players cannot gain an ailment
    prevent_ailment_worldguard_regions:
      - spawn
      - region2

    # List of WorldGuard region names where players will not experience symptoms
    prevent_symptom_worldguard_regions:
      - spawn
      - region 4
 
Obviously, modify the actual region names to suit your needs.

---
## Change Log 1.6.9.3 - 1.18 Support

This update marks Epidemic as 1.18 supported

This update REQUIRES Java 16 as a minimum version. I will continue to support versions prior to 1.6.9.3 with Java 8, but no more updates will be released with it.

WorldGuard PVP Deny areas will now be respected by Epidemic, so hitting someone in a protected area should no longer result in ailments being applied. You can enable/disable by adding the following to your config.yml file

    # If true, prevent_ailment_worldguard_pvp_deny will prevent players receiving symptoms or new ailments
    # while in a WorldGuard region that does not allow PVP
    
    prevent_ailment_worldguard_pvp_deny: true

Bug fixes:
Drinking from a water bottle was not emptying the bottle, this behavior has been corrected.

---
## Change Log 1.6.9.2 - Bug Fix

This release contains a small bug fix around the infectious flag in the ailment files. In some cases, the ailment might return as non-infectious when it should be infectious.

---
##  Change Log 1.6.9.1 - Bug Fix

This update addresses an issue with drinking from a cauldron in 1.17.* which was related to the change in item name.

---
## Change Log 1.6.9 - 1.17 Support

This update marks Epidemic as supported for 1.17

Also contains minor bug fixes
