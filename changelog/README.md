![Epidemic](../images/header.png)

[Home](https://torpkev.github.io/epidemic_docs)

# Change Log

## 1/7/2 - Natural Healing

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
