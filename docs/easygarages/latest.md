---
layout: default
title: 1.0.0 (latest)
parent: EasyGarages
nav_order: 1
color_scheme: dark
has_children: false
has_toc: true
---
<img class='cover-img' src='../../../assets/img/packages/easygarages-thumb.png' alt='EasyGarages Thumb' draggable='false'>



# EasyGarages!
{: .no_toc}

A guide to installing "EasyGarages" onto your FiveM server!

{: .fs-5 .fw-300 }

---
<details open markdown="block">
<summary>
table of contents
</summary>
{: .text-delta }
1. TOC
{:toc}
</details>
---

## Purchasing the resource

Firstly, you must purchase the product from either our Tebex or Discord. (We offer cheaper prices on our discord due to Tebex not taking a cut.)
If you wish to make the purchase on our discord, create a ticket, and state that you wish to purchase this resource.

[<img class='cover-img' width="21px" style="vertical-align: middle;" src='../../../assets/img/icons/prime.png' alt='Tebex' draggable='false'> Tebex Store](https://store.decidev.tk/){: .btn .btn-blue}

[<img class='cover-img' width="25px" style="vertical-align: middle;" src='../../../assets/img/icons/discord.png' alt='Discord' draggable='false'> Deci Scripting](https://ds.decidev.tk){: .btn .btn-discord}

## Downloading the resource

Upon purchasing the resource, head to [your Keymaster,](https://keymaster.fivem.net/asset-grants) find the resource, and click "Download"
<img class='cover-img' style="vertical-align: middle;" src='../../../assets/img/screenshots/granted_assets.png' alt='Granted Assets' draggable='false'>

## Installing the resource

1. Drag the resource into your resources folder.

2. Ensure or start all resources in server.cfg. Example:
```lua
ensure easygarages
```

## Configuring the resource

We try to make our resources as easy to understand as possible, however, they can be quite confusing without an explanation. Follow along with this guide to have a full understanding of how to configure this resource!


1. ### KeyBinds
    ```lua
    InteractionKey = 46,
    ```
    The control ID for interacting with garages. See [FiveM Controls](https://docs.fivem.net/docs/game-references/controls/) for a list.
    * "InteractionKey" opens the garage when pressed.

2. ### Distances
    ```lua
    GarageDrawDist = 20,
    GarageInteractDist = 5,
    ```
    These are pretty self-explanatory.
    * "GarageDrawDist" is the max distance where the garage markers/text is still rendered.
    * "GarageInteractDist" is the max distance where that the garage can be opened from.

3. ### Locations
    ```lua
    Locations = {
        {name="Police Garage", id="pol", color=29, icon=50, positions={ {position = vector3(442,-1021.78,28.54), heading = 90}, {position= vector3(532,-26,70.63), heading = 210} }, garages= {"response","fbi"}},
        {name="Ambo Garage", id="ambo", color=60, icon=50, positions={ {position = vector3(290,-591,43.19), heading = 340} }, garages= {"lsa_ambo"}}
    },
    ```
    This one can be a little confusing, due to the amount of fields.
    * "name" is the name of the locatiob.
    * "id" is the identifier of the location for usage with permissions.
    * "color" refers to the color id of the blip and marker. (Go [here](https://docs.fivem.net/docs/game-references/blips/#blip-colors/) for a list)
    * "icon" refers to the icon id of the blip. (Go [here](https://docs.fivem.net/docs/game-references/blips/) for a list)
    * "positions" refers to the each position that the garage is available from. 
        * "position" is the blip/marker position, and where the vehicle will spawn. It must be in a format of "vector3(X,Y,Z)".
        * "heading" is the heading/yaw rotation that the vehicle will spawn with.
    * "garages" refers to the garage categories that can be accessed through the garage.
    
4. ### Garages/Garage Categories
    ```lua
    Garages = {
        {name="Response", id="response", image="https://www.pngkey.com/png/full/912-9123331_gta-gtav-grandtheftautov-police-cop-cops-policedepartment-president.png"},
        {name="FIB", id="fbi", image="https://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Seal_of_the_Federal_Bureau_of_Investigation.svg/800px-Seal_of_the_Federal_Bureau_of_Investigation.svg.png"},
        {name="Ambulances", id="lsa_ambo", image="http://lossantosfire1.weebly.com/uploads/1/1/8/3/118376042/p500_orig.png"},
    },
    ```
    * "name" is the name of the category.
    * "id" is the identifier of the category. (for use with locations and vehicles)
    * "image" is the image that will be displayed on the button in the UI.


5. ### Vehicles
    ```lua
    Vehicles = {
        {name="Police Cruiser", model="police",garages = {"response"}, image="https://static.wikia.nocookie.net/gtawiki/images/b/bd/PoliceCruiser-GTAV-front.png/"},
        {name="Police Cruiser 2", model="police2",garages = {"response"}, image="https://static.wikia.nocookie.net/gtawiki/images/b/b1/PoliceCruiser2-GTAV-front.png/"},
        {name="Police Cruiser 3", model="police3",garages = {"response"}, image="https://static.wikia.nocookie.net/gtawiki/images/6/6b/PoliceCruiser3-GTAV-front.png/"},
        {name="Police Unmarked Cruiser", model="police4",garages = {"response"}, image="https://static.wikia.nocookie.net/gtawiki/images/7/7b/UnmarkedCruiser-GTAV-front.png/"},
        {name="Police Bike", model="policeb",garages = {"response"}, image="https://static.wikia.nocookie.net/gtawiki/images/7/70/PoliceBike-GTAV-front.png/"},
        {name="FIB Van", model="fbi",garages = {"fbi"}, image="https://i.ytimg.com/vi/Xyx37H3v4Ak/maxresdefault.jpg"},
        {name="FIB Van 2", model="fbi2",garages = {"fbi"}, image="https://i.ytimg.com/vi/Xyx37H3v4Ak/maxresdefault.jpg"},
        
        {name="Ambulance", model="ambulance",garages = {"lsa_ambo"}, image="https://i.guim.co.uk/img/media/e44ebc954ac83a0cd28c664625344ee9fd27954e/0_133_4000_2401/master/4000.jpg?width=1200&height=1200&quality=85&auto=format&fit=crop&s=b767b0545eac273b043c4bed28209d4a"}

    },
    ```
    * "name" is the name of the vehicle that will be displayed in the webhook and UI.
    * "model" is the model of the vehicle that will be spawned when clicked.
    * "garages" are the garages/categories that the vehicle will be available from. 
    * "image" is the image that will be displayed on the button in the UI.


6. ### Webhook
    ```lua
    Webhook = {
        url="",
        color="11111111",
        img="",
        name="EasyGarages",
        message="|PLAYER| retrieved a |VEHICLE| from the |LOCATION| in the |GARAGE| garage!"
    }
    ```

    * "url" is the url of the Discord webhook you wish to connect the resource to. (Leave blank to disable webhooks)
    * "color" refers to embed colour of the webhook messages. Take a look at [this](https://www.checkyourmath.com/convert/color/rgb_decimal.php) for converting RGB to decimal.
    * "img" refers to the profile picture url of the webhook message.
    * "name" is the username displayed for the webhook message.
    * "message" is the message that will be displayed in the webhook message. `|PLAYER|` will become the player name, `|VEHICLE|` will become the vehicle name, `|LOCATION|` will become the location name, and `|GARAGE|` will become the garage name.
    
7. ### CSS
    ```css
    :root{
        --fontColor: white;
        --background: #4b4b4b;
        --buttonBG: #434343;
        --buttonHoverBG: #414141;
        --buttonBoxShadow: #0000001a;
        --buttonHoverBoxShadow: #00000033;
    }
    ```

    * "fontColor" refers to the color of the fonts and icons.
    * "background" refers to the background color.
    * "buttonBG" refers to the button color.
    * "buttonHoverBG" refers to the button color when hovered.
    * "buttonBoxShadow" refers to the box shadow color of the button.
    * "buttonHoverBoxShadow" refers to the box shadow color of the button when hovered.
9. ### Functions
    ***WARNING - THIS SECTION IS INTENDED FOR DEVELOPERS***
    ```lua
    function GaragePermCheck(garage)
        print("GARAGE",garage.name)
        return true
    end

    function LocationPermCheck(location)
        print("LOCO",location.name)
        return true
    end

    ```
    These should all be pretty self-explanatory.
    * "GaragePermCheck" is called when attempting to check if the user has access to a garage category. It must return either true or false. "garage" is the garage object.
    * "LocationPermCheck" is called when attempting to check if the user has access to a garage location. It must return either true or false. "location" is the location object.

    You also have access to a function to use.
    * "ShowNotification" - Displays a default FiveM notification.

    *Support will be provided for these functions however it is advised that you have a basic understanding of Lua.*
## Support

Read through the instructions again if you have not managed to install or configure the resource. Can’t get it to work still? Create a ticket through our dedicated support system in Discord:

[<img class='cover-img' width="25px" style="vertical-align: middle;" src='../../../assets/img/icons/discord.png' alt='Discord' draggable='false'> Deci Scripting](https://ds.decidev.tk){: .btn .btn-discord}