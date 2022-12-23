![Epidemic](/images/header.png)

[Home](https://torpkev.github.io/epidemic_docs)

## Remedies

Remedies are items in-game that can be used to affect the player with one or more of a number of player effects including curing ailments, providing potion effects, modifying health/hunger/thirst, providing symptom relief and more.

The primary purpose of a Remedy is to cure a player of an ailment.  For example, a bandage that would cure the player of an open wound.  However, remedies are NOT tied directly to ailments, so you could have one remedy that cures multiples (a cure-all), or you could have multiple remedies that cure a single ailment or anywhere in between.

Remedies are also used to modify a players thirst and temperature with boiled water, cooling compresses etc.  These remedies could still cure an ailment or not.  You can combine any of the configurations options below to create the perfect set of remedies for your server.

Each remedy can have 1 recipe, it is on the server owner to ensure that the recipe does NOT overwrite a default or recipe created by another plugin.

Remedies can be triggered by right clicking with one in-hand, or consuming a food/drink item.  You can use the return_item configuration option to modify what the player receives after using a remedy (for example, if you wanted
the player to receive a stick after using a splint, you could put that in  return_item) - If you don't want them to receive anything after using the remedy, you can simply set it to AIR.

Remedy recipes can be either a crafting table recipe or a furnace recipe, each has their own configuration options which are outlined below.

**Remedy Configuration**

Remedy files are .yml files stored in the remedies folder.  They should be named as the key (details below) .yml -  For example: bandage.yml

Remedy file version, this MUST match the currently required version and should not ever be modified by hand.  If the remedy configuration ever needs to update, it will replace this value automatically.

    v: 1.0

Unique key for the remedy

    key: "bandage"

Display name of the remedy

    display_name: "&bBandage"

Item lore, shown when hovering over the item

    lore:
      - "&fA sterile bandage for wounds"

Text displayed to the player when using the item

    used_text: "You wrap the bandage around your wound and wait for it to heal"

Base item is the item it is displayed as in-game

    base_item: PAPER

Return item is the item that should be returned to the player ONLY to be used for non-edible items (potions/food do not need a return item and they will not be used

    return_item: AIR

Color is the potion color (only if base_item is POTION) in name, OR red/green/blue If both exist, name will always take priority

    potion_color:
      name: AQUA

-OR-

    potion_color:
      red: 72
      green: 32
      blue: 152

If set, will apply an enchantment glow to the item

    enchanted_glow: false

Item Recipe

You can have either craft OR furnace, not both  If both are included, only the craft recipe will be read.
recipe.amount is the number of items given when crafting
recipe.require_craft_perms is a true/false flag to indicate if the player requires epidemic.craft.<key> to craft

CraftRecipe:

    recipe:
      craft:
        top:
          left: AIR
          center: PAPER
          right: AIR
        middle:
          left: PAPER
          center: WHITE_WOOL
          right: PAPER
        bottom:
          left: AIR
          center: PAPER
          right: AIR
      amount: 1
      require_craft_perm: false

-OR-

FurnaceRecipe:

    recipe:
      furnace:
        item: POTION
          experience: 0
          time: 3
      amount: 1
      require_craft_perm: false

If set, item is food (MUST BE edible).  Remedy will trigger after consuming it.

    food: false

If set, item is a drink (must be drinkable).  Remedy will trigger after consuming it.

    drink: false

item_consumed is for NON-FOOD/DRINK ONLY - (items, not edible)
If item_consumed is true, then the item is removed/replaced from the player
after use.  if return_item is AIR, removed, if not AIR, then replaced. If item_consumed is false, then the item is not taken from the player after
use, for example, a knee brace that isn't ruined on use.  Can only be used if not food or drink

    item_consumed: true

**item_uses is for NON-FOOD/DRINK ONLY - (items, not edible)**
**item_uses is ONLY for 1.14+**
**item_uses is ONLY considered if item_consumed = false**
item_uses is the number of times an item can be used before breaking
if the item is not consumable.  For example, if you use a cane to heal a broken leg 10 times, and item_uses = 10, then after the 10th time, it will break.  Set to 0 for infinite uses. Comment out if not an item, or if item is consumed.

    item_uses: 10

List of ailments that the remedy cures

    cures:
      - wound

Effects to add - matches on potion effect type, then adds the time to the number of seconds left on the timer (IF the potion effect is already active, if not, will set it as a new effect for the number of seconds).  Will set the amplifier to the amplifier number here IF the current amplifier is < than this (or not set).  Potion effects information can be found here: [Potion Effects](https://torpkev.github.io/epidemic_docs/potioneffects)

    add_effects:
      WEAKNESS:
        time: 10
        amplifier: 1


Effects to remove - matches on potion effect type, then removes the time from the number of seconds left on the timer, and removes amplifier from current amplifier.  If number of seconds is <= 0 or if amplified <= 0, then the potion effect is completely removed.  Potion effects information can be found here: [Potion Effects](https://torpkev.github.io/epidemic_docs/potioneffects)

    remove_effects:
      SLOW:
        time: 10
        amplifier: 1

Health is the number of health points restored (if negative, points removed)

    health: 0

Hunger is the number of hunger points restored (if negative, points removed)

    hunger: 0

Thirst is the number of thirst points restored (if negative, points removed)

    thirst: 0

Number of seconds to apply symptom relief for

    symptom_relief_seconds: 0

Number of seconds to apply cold relief for

    cold_relief_seconds: 0

Number of seconds to apply heat relief for

    heat_relief_seconds: 0

