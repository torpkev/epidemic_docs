## Potion Effects

[Home](https://torpkev.github.io/epidemic_docs)

Potion effects are used for both ailments and remedies.

They are used in the add_effects and remove_effects part of the configuration files, in the example below, SLOW is added for 60 seconds with an amplifier of 2, and weakness is added for 5 seconds with an amplifier of 1.


    ailment_effects:
      SLOW:
        time: 60
        amplifier: 2
      WEAKNESS
        time: 5
        amplifier: 1

The list of possible effects are below, use the name on the left for each effect.  Using this list, we can see the example above has SLOW = Decreases movement speed, and WEAKNESS = Decreases damage dealt by an entity.

    ABSORPTION 				- Increases the maximum health of an entity with health that cannot be regenerated, but is refilled every 30 seconds.
    BAD_OMEN 				- Bad Omen
    BLINDNESS 				- Blinds an entity.
    CONDUIT_POWER 			- Effects granted by a nearby conduit.
    CONFUSION 				- Warps vision on the client.
    DAMAGE_RESISTANCE 		- Decreases damage dealt to an entity.
    DOLPHINS_GRACE 			- Dolphins Grace
    FAST_DIGGING			- Increases dig speed.
    FIRE_RESISTANCE 		- Stops fire damage.
    GLOWING 				- Outlines the entity so that it can be seen from afar.
    HARM 					- Hurts an entity.
    HEAL					- Heals an entity.
    HEALTH_BOOST 			- Increases the maximum health of an entity.
    HERO_OF_THE_VILLAGE 	- Hero of the Village
    HUNGER 					- Increases hunger.
    INCREASE_DAMAGE 		- Increases damage dealt.
    INVISIBILITY 			- Grants invisibility.
    JUMP 					- Increases jump height.
    LEVITATION 				- Causes the entity to float into the air.
    LUCK 					- Loot table luck.
    NIGHT_VISION 			- Allows an entity to see in the dark.
    POISON 					- Deals damage to an entity over time.
    REGENERATION 			- Regenerates health.
    SATURATION 				- Increases the food level of an entity each tick.
    SLOW 					- Decreases movement speed.
    SLOW_DIGGING 			- Decreases dig speed.
    SLOW_FALLING 			- Slows entity fall rate.
    SPEED 					- Increases movement speed.
    UNLUCK 					- Loot table unluck.
    WATER_BREATHING 		- Allows breathing underwater.
    WEAKNESS 				- Decreases damage dealt by an entity.
    WITHER 					- Deals damage to an entity over time and gives the health to the shooter.
