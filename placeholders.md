![Epidemic](/images/header.png)

[Home](https://torpkev.github.io/epidemic_docs)

## Placeholders

Placeholders available via PlaceholderAPI

    %epidemic_thirst% - Gives the thirst amount as a number
    %epidemic_thirst_text% - Gives the thirst amount as text (depending on lang.yml)
    %epidemic_temp_meter% - Shows the thermometer
    %epidemic_temp% - Gives the temperature as a number
    %epidemic_ailments% - Lists all the players ailments
    
It is important to note that to reduce the load on the server, Epidemic only updates its values that are accessible to PlaceholderAPI every 10 seconds. So even if you have a scoreboard that updates every second, it will still be 10 seconds until your values update. You can modify this in the config.yml file (papi_update_time [in seconds - defaults to 10[), however, depending on busy your server is, this could make load a little high as it has to pull values for every online player
