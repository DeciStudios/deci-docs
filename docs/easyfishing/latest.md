---
layout: default
title: '1.1.0 (latest)'
parent: EasyFishing
nav_order: 2

has_children: false
has_toc: true
---

<img class='cover-img' src='./././assets/img/fishing.png' alt='Fishing Job' draggable='false'>



# EasyFishing!
{: .no_toc}

A guide to installing "EasyFishing" onto your FiveM server!

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

[<img class='cover-img' width="21px" style="vertical-align: middle;" src='./././assets/img/prime.png' alt='Tebex' draggable='false'> Tebex Store](https://store.prime-modifications.tk/){: .btn .btn-blue}

[<img class='cover-img' width="25px" style="vertical-align: middle;" src='./././assets/img/discord.png' alt='Discord' draggable='false'> Prime Modifications](https://dc.prime-modifications.tk){: .btn .btn-discord}

## Downloading the resource

Upon purchasing the resource, head to [your Keymaster,](https://keymaster.fivem.net/asset-grants) find the resource, and click "Download"
<img class='cover-img' style="vertical-align: middle;" src='./././assets/img/granted_assets.png' alt='Granted Assets' draggable='false'>

## Installing the resource

1. Drag the resource into your resources folder.

2. Ensure or start all resources in server.cfg. Example:
```lua
ensure easyfishing
```

## Configuring the resource

We try to make our resources as easy to understand as possible, however, they can be quite confusing without an explanation. Follow along with this guide to have a full understanding of how to configure this resource!

1. ### Commands
    ```lua
    FishCommand = "fish",   
    InvCommand = "inventory",
    ```
    This one is pretty self-explanatory. 
    * "FishCommand" refers to the command that is entered to start fishing. 
    * "InvCommand" refers to the command entered to display the fish and bait you currently have.
2. ### KeyBinds
    ```lua
    KeyBinds = {
        KeepFish = 44, 
        ThrowBackFish = 48,
        CancelFishing = 44,
        ReelIn = 46,
        ShopAndSellInteract = 46 
    },
    ```
    The control IDs for each ingame action. See [FiveM Controls](https://docs.fivem.net/docs/game-references/controls/) for a list.
    * "KeepFish" keeps the fish you caught when pressed.
    * "ThrowBackFish" throws back the fish you caught when pressed.
    * "CancelFishing" stops fishing when pressed at any point.
    * "ReelIn" is the button that you mash when catching a fish.
    * "ShopAndSellInteract" is the button you press to interact with all shops and sell places.
3. ### Fish
    ```lua
    Fish = {
        {name="NAME", model="MODEL", clickCount=0, minWeight=0, maxWeight=0, timeToCatch = 0, legal=false, illegalReason="REASON"}
    },
    ```
    This one can be a little confusing, due to the amount of fields.
    * "name" is the name of the fish.
    * "model" is the model of the ped that will spawn for the fish. (Leave this blank for no model to spawn)
    * "clickCount" refers to the amount of times the [E] key will have to be pressed before you catch the fish. (See showcase to understand this better)
    * "minWeight" and "maxWeight" are the minimum and maximum values for the weight of the fish you catch. (in kg) When a fish is caught, a random value inbetween these two values will be picked as the fish weight.
    * "legal" refers to if the fish is legal or not.
    * "illegalReason" is the reason that will displayed if the fish is illegal. (Leave empty if the fish is set as legal)
    
4. ### Sell Places
    ```lua
    SellPlaces = {
        {name="NAME", colour=0, icon=0, pos= vector3(0,0,0)}
    },
    ```
    * "name" is the name of the sell site. (e.g. "Pipeline Inn")
    * "colour" refers to the color id of the blip. (Go [here](https://docs.fivem.net/docs/game-references/hud-colors/) for a list)
    * "icon" refers to the icon id of the blip. (Go [here](https://docs.fivem.net/docs/game-references/blips/) for a list)
    * "pos" refers to the position of the blip/site, in a format of "vector3(X,Y,Z)".

5. ### Shops
    ```lua
    Shops = {
        {name="Farlows Travel",showNameInMenu= false, slogan="This is a slogan!",colour=30, icon=529, customTitleTexture="https://i.imgur.com/KGnCujw.png", id="fishShop1", pos= vector(-2188.49, -400.14, 13.31)}
    },
    ```
    * "name" is the name of the shop
    * "showNameInMenu" decides wether the name of the shop will be shown in the menu.
    * "slogan" is the slogan that will appear in the menu below the name.
    * "colour" refers to the color id of the blip. (Go [here](https://docs.fivem.net/docs/game-references/hud-colors/) for a list)
    * "icon" refers to the icon id of the blip. (Go [here](https://docs.fivem.net/docs/game-references/blips/) for a list)
    * "customTitleTexture" refers to the image that will be loaded and used as the banner for the shop's UI.
    * "id" defines the id that will be used to assign products to the shop.
    * "pos" refers to the position of the blip/shop, in a format of "vector3(X,Y,Z)".
    Additionally, you can add a "customSubheading" field to your shop. This replaces the message below the shop name. if you include "|key|" in the message then it will replace that with the interaction key, making configuration a little easier. 

6. ### Products
    ```lua
    Products = {
        {name="10x Fishing Bait", description="",amount=10,price=20.00, shops={"fishShop1"}},
        {name="5x Fishing Bait", description="",amount=5,price=10.00, shops={"fishShop1"}}
    },
    ```

    * "name" is the name of the product.
    * "description" is the description of the product.
    * "amount" is the amount of bait you get when purchasing the product.
    * "price" is the price of the product.
    * "shops" is the IDs of the shops that the product can be purchased from.
    Additionally, a "customMessage" field can be added. This replaces the notification shown when you purchase the bait, to a custom message of your choice. Currently, if you want to add the price, then it has to be included manually in the message.
    
7. ### Webhook
    ```lua
    Webhook = { 
        url="URL",
        color=11111111,
        img="IMG"
    },
    ```

    * "url" is the url of the Discord webhook you wish to connect the resource to. (Leave blank to disable webhooks)
    * "color" refers to embed colour of the webhook messages. Take a look at [this](https://www.checkyourmath.com/convert/color/rgb_decimal.php) for converting RGB to decimal.
    * "img" refers to the profile picture url of the webhook message.
    
8. ### Misc
    ```lua
    MenuPos = {100,100}, -- THE POSITION OF THE MENU ON THE SCREEN
    DistanceFromWater = 10,
    MaxBlipInteractDistance = 5,
    MaxBlipDrawDistance = 10, 
    Currency = "£",
    MoneyPerKilo = 1,
    SecsTillCatchMin = 10,
    SecsTillCatchMax = 30
    ```

    * "MenuPos" refers to the positioning of the shop menu.
    * "DistanceFromWater" refers to the max distance between the player and the water to be able to fish.
    * "MaxBlipInteractDistance" refers to the max distance between the player and the blip to be able to interact with the blip. (shop/sell place)
    * "MaxBlipDrawDistance" refers to the max distance between the player and the blip to draw the text for the blip.
    * "Currency" refers to the currency that will be displayed when purchasing a product, or selling a fish.
    * "MoneyPerKilo" refers to the amount of money you will recieve per kilo when selling fish.
    * "SecsTillCatchMin" and "SecsTillCatchMax" are the minimum and maximum values for the time taken for a fish to get caught on your line. When you start fishing, a random value between these two numbers will be picked, and it will wait that time for the fish to get caught in the line.
9. ### Functions
    ***WARNING - THIS SECTION IS INTENDED FOR DEVELOPERS***
    ```lua
    function Purchase(price)
        print("PURCHASE")
        return true 

    end

    function RodCheck()
        print("ROD CHECK")
        return true

    end

    function Payout(money)
        print("PAYOUT")

    end

    function IllegalFish()
        print("ILLEGAL FISH")
        ShowNotification("You have been caught in possesion of an illegal fish! You have lost all your fish.")
        ResetInventory()
    end
    ```
    These should all be pretty self-explanatory.
    * "Purchase" is called when attempting to purchase bait. It must return either true or false ("price" is the cost of the product)
    * "RodCheck" is called when attempting to check if the user has a fishing rod. It must return either true or false.
    * "Payout" is called when you sell your fish. "money" is the money you sold the fish for.
    * "ResetInventory" is called when you attempt to sell an illegal fish.

    You also have access to a few functions to use. (as seen in the "IllegalFish" example above.)
    * "ShowNotification" - Displays a default FiveM notification.
    * "InventoryReset" - Resets your inventory, sets all of their values back to their original state.

    *Support will be provided for these functions however it is advised that you have a basic understanding of Lua.*
## Support

Read through the instructions again if you have not managed to install or configure the resource. Can’t get it to work still? Create a ticket through our dedicated support system in Discord:

[<img class='cover-img' width="25px" style="vertical-align: middle;" src='./././assets/img/discord.png' alt='Discord' draggable='false'> Prime Modifications](https://dc.prime-modifications.tk){: .btn .btn-discord}