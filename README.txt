Let's make a game!
    name:Fairy Shelter for Cutiepie Comfort & Rescue
    by:fae.exe & Alyyyd
    desc:Alid was bored so we made a game.<//>Make cute crying critters happy.
    created:25/7/2017
    updated:24/10/2017
    version:1

Settings
    background:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/background.PNG
    stylesheet:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/stylesheet.txt
	spritesheet:icons, 48 by 48, https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/icon-spritesheet.png
    building cost increase:115%
    building cost refund:50%
    stylesheet:stuff/bigBlue.css

Layout
*gachabox
    contains:tag:gachamachine

*kamoshikabox
    header:KAMOSHIKAS
    contains:coldbox, sadbox, hungrybox, lonelybox, angrybox

*coldbox
	icons:show
	contains:tag:cold

*sadbox
    	contains:tag:sad

*hungrybox
	contains:tag:hungry

*lonelybox
	contains:tag:lonely

*angrybox
	contains:tag:angry

*buildingbox
    contains:BulkDisplay, Buildings
    header:Buildings
    tooltip origin:left
	ps:show

*kamosmilesbox
    contains:tag:crystals, tag:kamosmilesres
    header:GACHA CURRENCIES

*upgradebox
    contains:Upgrades
    header:Upgrades
    costs:hide
    names:hide

        
Buttons
    *kamoshiGacha
        name:KAMOSHIGACHA
        desc:Click to spend Capricoins and gain sad kamoshikas.
        on click:
			if (capriCoins >= 120) 
				anim icon wobble
				lose 120 capriCoins
				do gachagacha
			end
		end
		on gachagacha:
			if (chance(1%))
				yield 1 lonelyShika
			else if (chance(3%))
				yield 1 angryShika
			else if (chance(7%))
				yield 1 hungryShika
			else if (chance(20%))
				yield 1 sadShika
			else
				yield 1 coldKamoshika
			end
		end
		tags:gachamachine
		cost:120 capriCoins
        icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/gacha.PNG
        no text
        class:bigButton hasFlares
        icon class:shadowed
        tooltip origin:bottom
        tooltip class:red

    *capriCoinbank
		name:The Capricoinbank
		desc:Click to gain Capricoins to spend on the KAMOSHIGACHA.
		tags:crystals
		on click:yield 1 capriCoin
        
Resources
    *capriCoin|capriCoins
        name:Capricoin|Capricoins
        desc:Fell from heaven with the KAMOSHIGACHA MACHINE. You can spend those on the KAMOSHIGACHA. (And some other things.)
        icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/capricrystals.PNG
		show earned
		icon class:kamoIcon
		tags:crystals
		on tick:yield 1 capriCoin
		on start:yield 120 capriCoins

    *kamosmile|kamosmiles
		name:Kamosmile|Kamosmiles
		icon class:mediumIcon
		desc:The happiness from Kamoshikas! You'll earn it by satisfying their needs!
		icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/capricrystals.PNG
		show earned
		tags:cappynessres

    *coldKamoshika|coldKamoshikas
        name:Kamoshiglace|Kamoshiglaces
		class:cold
		icon class:kamoIcon
		tags:caprine, cold
        desc:These kamoshikas are so cold they turned to ice and need to be warmed up. <//> <b>Rarity:</b> Common.
        icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/kamoshiglace.PNG
		hidden when 0

    *sadShika|sadShikas
		name:Sadmoshika|Sadmoshikas
		class:sad
		icon class:kamoIcon
		tags:caprine, sad
		desc:These kamoshikas are sad because they want to play! <//> <b>Rarity:</b> Uncommon.
		icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/sadserow.PNG
		hidden when 0

    *hungryShika|hungryShikas
		name:Hungrishika|Hungrishikas
		icon class:kamoIcon
		tags:carpine, hungry
		desc:These kamoshikas are always hungry. You could be shoveling grass into them all day long. <//> <b>Rarity:</b> Rare.
		hidden when 0

    *angryShika|angryShikas
		name:Kaboomshika|Kaboomshikas
		icon class:kamoIcon
		tags:caprine, angry
		desc:These kamoshikas are very angry and need to calm down. Maybe some meditation, or a punching-ball. <//> <b>Rarity:</b> Extra rare.
		hidden when 0

    *lonelyShika|lonelyShikas
		name:Kaloneshika|Kaloneshikas
		icon class:kamoIcon
		tags:caprine, lonely
		desc:These mountain goats have lives alone on their big mountains for so long, they want a little company. <//> <b>Rarity:</b> Secret rare.
		hidden when 0

Buildings
    *TEMPLATE
        on click:anim glow
        
    *heater
        name:Heater
        desc:<q>Generates a little heat to make your freezing kamoshikas warmer and happier.</q> <//> <.> Generates 0.1 kamosmile per kamoshiglace per second.
        cost:20 capriCoins
		icon class:mediumIcon
		class:cold
        icon:icons[0,1]
		tags:healcold
		on tick:yield 0.1*(coldKamoshikas) kamosmiles
        req:1 coldKamoshika:earned

    *bigBlanket
		name:Big blanket
		desc:The kamoshikas can all huddle under this big blanket for warmth.
		icon class:mediumIcon
		class:cold
        icon:icons[0,2]
		tags:healcold
		on tick:yield 0.2*(coldKamoshikas) kamosmiles
		req:10 coldKamoshikas:earned

    *toyBox
		name:Toy box
		desc:For a fleeting moment, the sad serows will be very happy to have toys to play with.
		cost:30 capriCoins
		icon class:mediumIcon
        icon:icons[0,3]
		tags:healsad
		on tick:yield 0.2*(sadShikas) kamosmiles
		req:1 sadShika:earned

    *goatMovies
		name:Goat movies
		desc:This goat-cinema will allow your serows to enjoy fun movies together, distracting them from the pain of existence.
		cost:200 capriCoins
		icon class:mediumIcon
        icon:icons[0,4]
		tags:healsad
		on tick:yield 0.4*(sadShikas) kamosmiles
		req:10 sadShikas:earned

    *grassPatch
        name:Grass patch
        desc:Grow some grass to feed your hungry markhors! But this will not satiate them for long.
        cost:40 capriCoins
		icon class:mediumIcon
        icon:icons[0,5]
		tags:healhungry
		on tick:yield 0.5*(hungryShikas) kamosmiles
        req:1 hungryShika:earned

    *foodDelivery
        name:Food delivery
        desc:Get some food delivered directly to your goatstep! Shovel that right into the Shika's mouth.
        cost:500 capriCoins
		icon class:mediumIcon
        icon:icons[0,6]
		tags:healhungry
		on tick:yield 4*(hungryShikas) kamosmiles
        req:10 hungryShika:earned

    *punchingBag
        name:Punching bag
        desc:A punching (well more like headbutting) bag so your angriest goats can take it out on something.
        cost:50 capriCoins
		icon class:mediumIcon
		tags:healangry
		on tick:yield 1*(angryShikas) kamosmiles
        req:1 angryShika:earned
        icon:icons[0,7]

    *meditationWaterfall
		name:Meditation waterfall
		desc:A gorgeous waterfall that your tahrs can soak under while reflecting on the futile aspects of rage and the power of love.
		cost:800 capriCoins
		icon class:mediumIcon
		tags:healangry
		on tick:yield 10*(angryShikas) kamosmiles
        req:1 angryShika:earned
        icon:icons[0,8]

    *headscritchDispenser
        name:Headscritch dispenser
        desc:A nice headscratch dispenser to help your loneliest goat feel a little loved.
        cost:100 capriCoins
		icon class:mediumIcon
		tags:heallonely
		on tick:yield 5*(lonelyShikas) kamosmiles
        req:1 lonelyShika:earned
        icon:icons[0,9]

    *playPen
		name:Play pen
		desc:A play pen for both your goatlitaires and your sad serows! Playing together means being together!
		cost:1000 capriCoins
		icon class:mediumIcon
		tags:heallonely, healsad
		on tick:yield (20*(lonelyShikas) + 0.5*(sadShikas)) kamosmiles
		req:2 lonelyShika:earned
		req:20 sadShikas:earned
        icon:icons[0,10]

    *coldExplorer
		name:Train a cold explorer
		desc:Gives very heavy coats to a kamoshikas so they can face their fear and explore the wilds in search of capriCoins!
		cost:100 capriCoins, 1 coldKamoshika
		tags:job
		on tick:yield 0.5 capriCoin
		cost increase:200%
		req:5 coldKamoshikas:earned

    *goatRescuer
		name:Train a serow rescuer
		desc:Gives helicopters and pilot licenses to your sad serows. The fulfillment of saving kamoshikas from the cold distracts them from their awful sadness.
		cost:250 capriCoins, 1 sadShika
		tags:job
		on tick:yield 0.02 coldKamoshika
		cost increase:200%
		req:5 sadShika:earned

	*smileCondensator
		name:Smile condensator
		desc:<q>A machine to turn the happiness of kamoshikas into kamoshicoins.</q> <//> <.> Gives 0.1 kamoshicoin per second at base. <.> Decreases kamosmile income by 1 kamosmile per second.
		cost:20 kamosmiles
		tags:smileConverter
		on tick:yield 0.1 kamoshicoin
		on tick:yield -1 kamosmile
		req:(kamosmile:ps) >= 1
		req:(kamosmiles:earned) >= 10

	*kamoshiParty
		name:Kamoshiparty harvester|Kamoshiparty harvesters
		desc:<q>The happy kamoshikas are partying! Their residual smiles can be converted into a lot of kamoshicoins.</q> <//> <.> Gives 1 kamoshicoin per second at base. <.> Decreases kamosmile income by 2 kamosmiles per second.
		cost:100 kamosmiles
		tags:smileConverter
		on tick:yield 1 kamoshicoin
		on tick:yield -2 kamosmile
		req:(kamosmile:ps) >= 2
		req:(kamosmiles:earned) >= 50

	*kamoshiRevue
		name:Kamoshi-revue|Kamoshi-revues
		desc:<q>A special revue kamoshikas can go to to watch kamoshidrag shows.</q>

	*gourmetRestaurant
		name:Gourmet restaurant
		desc:<q>A fine dining establishment kamoshikas can go to in order to eat and enjoy the company.</q>
	
	*wishResonator
		name:Wish resonator|Wish resonators
		desc:<q>The happier the kamoshikas, the more potent are their wish for others to experience the same.</q> <//> <.> Gives 5 kamoshicoin per second at base. <.> Decreases kamosmile income by 5 kamosmiles per second.
		cost:1000 kamosmiles
		tags:smileConverter
		on tick:yield 5 kamoshicoin
		on tick:yield -5 kamosmile
		req:(kamosmile:ps) >= 5
		req:(kamosmiles:earned) >= 500

	*smileReactor
		name:Smile reactor|Smile reactors
		desc:<q>The happiness of the kamoshikas is growing too potent - it has to be canalyzed.</q> <//> <.> Gives 10 kamoshicoin per second at base. <.> Decreases kamosmile income by 8 kamosmiles per second.
		cost:5000 kamosmiles
		tags:smileConverter
		on tick:yield 10 kamoshicoin
		on tick:yield -8 kamosmile
		req:(kamosmile:ps) >= 8
		req:(kamosmiles:earned) >= 2500

    *coldMutator
		name:Cold-mutation
		desc:This process can distillate 5 cold kamoshita into a sad serow, taking the cold from <i>outside</i> the goats and concentrating it within a single goat.
		cost:5 coldKamoshita, 500 capriCoins
		tags:transmutation
		on earn:yield 1 sadShika
		req:1 sadShika
		cost increase:100%
