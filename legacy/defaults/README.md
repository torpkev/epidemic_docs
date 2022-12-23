## Default Files

[Home](https://torpkev.github.io/epidemic_docs)

Epidemic has a config.yml file created in the Epidemic plugin folder which can be modified as needed.  However, the key "v" should never be changed manually.  It looks like this:

    v: 1.6.5


This key is used during upgrades and conversions to move things into their proper version.

The rest of the config can be modified to suit your own purposes.  If you ever need to due to a mistake, you can simply delete the config.yml and it will regenerate, or, you can pull a copy from here: [config.yml](https://torpkev.github.io/epidemic_docs/defaults/config.yml)

The language file lang.yml is also created in the Epidemic plugin folder.  This file contains a code<>text list of messages sent to the player in-game.  All player facing messages are listed in this file (if you find text in game you can't modify, please let me know!).  
You can modify this file as needed in order to properly translate the game for yourself.  Please do NOT change anything in <% %> tags as these are placeholders for game data.  For example <%ailments%>.  If you translate the word ailments in the tag, the plugin will not know what to substitute the tag for.
If an entry is missing, it will default to the English translation.
(Note: If you translate the lang.yml file completely and would like it hosted here for others to use, please let me know).  You can get a copy of the lang.yml file here: [lang.yml](https://torpkev.github.io/epidemic_docs/defaults/lang.yml)

Ailments - Ailment files are created during startup (if upgrading, they are converted and will not include the defaults).  You can view the defaults here: [Ailments](https://torpkev.github.io/epidemic_docs/defaults/ailments)

Remedies - Remedy files are created during startup )if upgrading, they are converted from your current Ailment cures, and will not include the defaults).  You can view the defaults here: [Remedies](https://torpkev.github.io/epidemic_docs/defaults/remedies)
