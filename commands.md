![Epidemic](/images/header.png)

[Home](https://torpkev.github.io/epidemic_docs)

## Commands

Epidemic commands are as listed below

/epidemic (or /epi) is the main command for the program, its usage is dependent on permission:

    /epidemic - Will return the usage available for the /epidemic command for the player
    
    /epidemic version - Will display the plugin version. Requires epidemic.admin
    
    /epidemic debug - Toggles debug mode. Requires epidemic.admin
    
    /epidemic reload - Reloads the config, ailments & remedies. Requires epidemic.admin
    
    /epidemic bypass - Toggles bypass mode for the player. Requires epidemic.admin or epidemic.bypass
    
    /epidemic recipes - Will display the available remedies. Requires epidemic.recipes.display

    /epidemic day - This will display the in-game day according to Epidemic.  Requires epidemic.admin

    /epidemic invincible <player uuid or player name (if online)> <number of days> - Makes a player invincible to any epidemic ailment for the number of days listed.  Requires epidemic.admin permission

/cure can be used to cure a player of an ailment


    /cure - Will return the usage

    /cure <player  name-  Will  cure  the  player  of  any  ailments  they  have.  Requires  epidemic.admin  or  epidemic.cure
    
    /cure <player  name  <ailment  name> - Will cure the player of that ailment only. Requires epidemic.admin or epidemic.cure

 /infect can be used to afflict a player with an ailment

    /infect - Will return the usage
    
    /infect <player name>  <ailment name> - Will afflict the player with that ailment. Requires epidemic.admin or epidemic.infect

/epigive can be used to give a player a remedy

    /epigive - Will return the usage
    
    /epigive <playername  <remedy key> - Will give the player the remedy. Requires epidemic.admin or epidemic.give

/health will display the players current health status

    /health - Will display the players current health status. Requires epidemic.admin or epidemic.health

/thirst can be used to modify a players thirst

    /thirst - Will display the usage
    
    /thirst add <player name>  <amount 0-100> Will add to the players hydration. Requires epidemic.admin or epidemic.thirst
    
    /thirst remove <player name>  <amount 0-100> Will remove from the players hydration. Requires epidemic.admin or epidemic.thirst
    
    /thirst set <player name>  <amount 0-100> Will set the players hydration. Requires epidemic.admin or epidemic.thirst

  

/temp can be used to view current temperature status

    /temp - Will display the players thermometer. Requires epidemic.admin or epidemic.temp
    
    /temp info - Will display the players thermometer with additional information. Requires epidemic admin or epidemic.temp.info

/epirecipes (or /er) can be used to display remedies. (Does the same thing as /epidemic.recipes) - Requires epidemic.recipes.display

    /epirecipes - Will display the available remedies. Requires epidemic.recipes.display
    
