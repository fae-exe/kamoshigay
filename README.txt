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
    building cost increase:115%
    building cost refund:50%
    spritesheet:icons, 16 by 16, https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/icon-spritesheet.png
    stylesheet:stuff/bigBlue.css

Layout
*gachabox
    contains:tag:gachamachine

*kamoshikabox
    header:KAMOSHIKAS
    contains: coldbox, sadbox, hungrybox, lonelybox, angrybox

*sadbox
    	contains:tag:sad

*coldbox
	contains:tag:cold

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

*upgradebox
    contains:Upgrades
    header:Upgrades
    costs:hide
    names:hide

*cappynessbox
    	contains:tag:crystals, tag:cappynessres
    	header:GACHA CURRENCIES

        
Buttons
    *kamoshiGacha
        name:KAMOSHIGACHA
        desc:Click to spend capriCrystalS and gain sad caprinae.
        on click:
		if (capriCrystals >= 120) 
			anim icon wobble
			lose 120 capriCrystals
			do gachagacha
		end
	end
	on gachagacha:
		if (chance(1%))
			yield 1 lonelyGoat
		else if (chance(3%))
			yield 1 angryTahr
		else if (chance(7%))
			yield 1 hungryMarkhor
		else if (chance(20%))
			yield 1 sadSerow
		else
			yield 1 coldKamoshika
		end
	end
	tags:gachamachine
	cost:120 capriCrystals
        icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/gacha.PNG
        no text
        class:bigButton hasFlares
        icon class:shadowed
        tooltip origin:bottom
        tooltip class:red

    *capriCrystalarium
	name:The Capricrystalarium
	desc:Click to gain capriCrystalS to spend on the KAMOSHIGACHA.
	tags:crystals
	on click:yield 1 capriCrystal
        
Resources
    *capriCrystal|capriCrystals
        name:Capricrystals
	class:bigIcon
        desc:Fell from heaven with the KAMOSHIGACHA MACHINE. You can spend those on the KAMOSHIGACHA. (And some other things.)
        icon:icons[0,1]
	show earned
	tags:crystals
	on tick:yield 1 capriCrystal
	on start:yield 120 capriCrystals

    *cappyness
	name:Cappyness
	icon class:mediumIcon
	desc:Caprine happiness! You'll earn it every time you send a caprinae for adoption!
	icon:icons[3,0]
	show earned
	tags:cappynessres

    *coldKamoshika|coldKamoshikas
        name:Kamoshiglace|Kamoshiglaces
	class:mediumIcon
	tags:caprine, cold
        desc:These kamoshikas are so cold they turned to ice and need to be warmed up. <//> <b>Rarity:</b> Common.
        icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/kamoshiglace.PNG

    *sadSerow|sadSerows
	name:Sad serow|Sad serows
	class:mediumIcon
	tags:caprine, sad
	desc:These taiwanese serows are sad because they want to play! <//> <b>Rarity:</b> Uncommon.
	icon:https://upload.wikimedia.org/wikipedia/commons/1/16/%E9%95%B7%E9%AC%83%E5%B1%B1%E7%BE%8A.jpg

    *hungryMarkhor|hungryMarkhors
	name:Hungrhor|Hungrhors
	class:mediumIcon
	tags:carpine, hungry
	desc:These Markhors are always hungry. You could be shoveling grass into them all day long. <//> <b>Rarity:</b> Rare.

    *angryTahr|angryTahrs
	name:Fulminatahr|Fulminatahrs
	class:mediumIcon
	tags:caprine, angry
	desc:These tahrs are very angry and need to calm down. Maybe some meditation, or a punching-ball. <//> <b>Rarity:</b> Extra rare.

    *lonelyGoat|lonelyGoats
	name:Goatlitaire|Goatlitaires
	class:mediumIcon
	tags:caprine, lonely
	desc:These mountain goats have lives alone on their big mountains for so long, they want a little company. <//> <b>Rarity:</b> Secret rare.

Buildings
    *TEMPLATE
        on click:anim glow
        
    *heater
        name:Heater
        desc:Generates a little heat to make your freezing kamoshikas warmer and happier.
        cost:20 capriCrystals
	tags:healcold
	on tick:yield 0.1*(coldKamoshikas) cappyness
        req:1 coldKamoshika:earned
        icon:icons[0,1]

    *bigBlanket
	name:Big blanket
	desc:The caprinaes can all huddle under this big blanket for warmth. It is woven from a thread synthesized using cappyness.
	cost:100 capriCrystals
	tags:healcold
	on tick:yield 0.2*(coldKamoshikas) cappyness
	req:10 coldKamoshikas:earned
        icon:icons[0,2]

    *toyBox
	name:Toy box
	desc:For a fleeting moment, the sad serows will be very happy to have toys to play with.
	cost:30 capriCrystals
	tags:healsad
	on tick:yield 0.2*(sadSerows) cappyness
	req:1 sadSerow:earned
        icon:icons[0,3]

    *goatMovies
	name:Goat movies
	desc:This goat-cinema will allow your serows to enjoy fun movies together, distracting them from the pain of existence.
	cost:200 capriCrystals
	tags:healsad
	on tick:yield 0.4*(sadSerows) cappyness
	req:10 sadSerows:earned
        icon:icons[0,4]

    *grassPatch
        name:Grass patch
        desc:Grow some grass to feed your hungry markhors! But this will not satiate them for long.
        cost:40 capriCrystals
	tags:healhungry
	on tick:yield 0.5*(hungryMarkhors) cappyness
        req:1 hungryMarkhor:earned
        icon:icons[0,5]

    *foodDelivery
        name:Food delivery
        desc:Get some food delivered directly to your goatstep! Shovel that right into the Markhor's mouth.
        cost:500 capriCrystals
	tags:healhungry
	on tick:yield 4*(hungryMarkhors) cappyness
        req:10 hungryMarkhor:earned
        icon:icons[0,6]

    *punchingBag
        name:Punching bag
        desc:A punching (well more like headbutting) bag so your angriest goats can take it out on something.
        cost:50 capriCrystals
	tags:healangry
	on tick:yield 1*(angryTahrs) cappyness
        req:1 angryTahr:earned
        icon:icons[0,7]

    *meditationWaterfall
	name:Meditation waterfall
	desc:A gorgeous waterfall that your tahrs can soak under while reflecting on the futile aspects of rage and the power of love.
	cost:800 capriCrystals
	tags:healangry
	on tick:yield 10*(angryTahrs) cappyness
        req:1 angryTahr:earned
        icon:icons[0,8]

    *headscritchDispenser
        name:Headscritch dispenser
        desc:A nice headscratch dispenser to help your loneliest goat feel a little loved.
        cost:100 capriCrystals
	tags:heallonely
	on tick:yield 5*(lonelyGoats) cappyness
        req:1 lonelyGoat:earned
        icon:icons[0,9]

    *playPen
	name:Play pen
	desc:A play pen for both your goatlitaires and your sad serows! Playing together means being together!
	cost:1000 capriCrystals
	tags:heallonely, healsad
	on tick:yield (20*(lonelyGoats) + 0.5*(sadSerows) cappyness
	req:2 lonelyGoat:earned
	req:20 sadSerows:earned
        icon:icons[0,10]

    *coldExplorer
	name:Train a cold explorer
	desc:Gives very heavy coats to a kamoshikas so they can face their fear and explore the wilds in search of Capricrystals!
	cost:100 capriCrystals, 1 coldKamoshika
	tags:job
	on tick:yield 0.5 capriCrystal
	cost increase:200%
	req:5 coldKamoshikas:earned

    *goatRescuer
	name:Train a serow rescuer
	desc:Gives helicopters and pilot licenses to your sad serows. The fulfillment of saving kamoshikas from the cold distracts them from their awful sadness.
	cost:250 capriCrystals, 1 sadSerow
	tags:job
	on tick:yield 0.02 coldKamoshika
	cost increase:200%
	req:5 sadSerow:earned

    *coldMutator
	name:Cold-mutation
	desc:This process can distillate 5 cold kamoshita into a sad serow, taking the cold from <i>outside</i> the goats and concentrating it within a single goat.
	cost:5 coldKamoshita, 500 capriCrystals
	tags:transmutation
	on earn:yield 1 sadSerow
	req:1 sadSerow
	cost increase:100%
