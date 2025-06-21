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
    spritesheet:icons, 48 by 48, stuff/bunnyIcons.png
    stylesheet:stuff/bigBlue.css

Layout
*gachabox
    contains:tag:gachamachine

*kamoshikabox
    header:KAMOSHIKAS
    contains:sadbox, coldbox, hungrybox, lonelybox, angrybox

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
    	contains:tag:crystals, cappyness
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
	name:capriCrystalARIUM
	desc:Click to gain capriCrystalS to spend on the KAMOSHIGACHA.
	tags:crystals
	on click:yield 1 capriCrystal
        
Resources
    *capriCrystal|capriCrystals
        name:capriCrystals
	class:bigIcon
        desc:Fell from heaven with the KAMOSHIGACHA MACHINE. You can spend those on the KAMOSHIGACHA. (And some other things.)
        icon:icons[0,1]
	show earned
	tags:crystals
	on tick:yield 1 capriCrystal
	on start:yield 120 capriCrystals

    *cappyness
	name:Cappyness
	class:mediumIcon
	desc:Caprine happiness! You'll earn it every time you send a caprinae for adoption!
	icon:icons[3,0]
	show earned
	tags:cappynessres

    *coldKamoshika|coldKamoshikas
        name:Kamoshiglace|Kamoshiglaces
	tags:caprine, cold
        desc:These kamoshikas are so cold they turned to ice and need to be warmed up. <//> <b>Rarity:</b> Common.
        icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/kamoshiglace.PNG

    *sadSerow|sadSerows
	name:Sad serow|Sad serows
	tags:caprine, sad
	desc:These taiwanese serows are sad because they want to play! <//> <b>Rarity:</b> Uncommon.
	icon:https://upload.wikimedia.org/wikipedia/commons/1/16/%E9%95%B7%E9%AC%83%E5%B1%B1%E7%BE%8A.jpg

    *hungryMarkhor|hungryMarkhors
	name:Hungrhor|Hungrhors
	tags:carpine, hungry
	desc:These Markhors are always hungry. You could be shoveling grass into them all day long. <//> <b>Rarity:</b> Rare.

    *angryTahr|angryTahrs
	name:Fulminatahr|Fulminatahrs
	tags:caprine, angry
	desc:These tahrs are very angry and need to calm down. Maybe some meditation, or a punching-ball. <//> <b>Rarity:</b> Extra rare.

    *lonelyGoat|lonelyGoats
	name:Goatlitaire|Goatlitaires
	tags:caprine, lonely
	desc:These mountain goats have lives alone on their big mountains for so long, they want a little company. <//> <b>Rarity:</b> Secret rare.

Buildings
    *TEMPLATE
        on click:anim glow
        
    *heater
        name:Heater
        desc:Generates a little heat, which will make your Kamoshiglace generate a little cappyness.
        cost:20 capriCrystals
	tags:healcold
	on tick:yield 0.1*(coldKamoshikas) cappyness
        req:1 coldKamoshika

    *coldExplorer
	name:Cold explorer
	desc:Gives a very heavy coat to a kamoshika so it can face its fear and explore the wilds in search of Capricrystals!
	cost:100 capriCrystals, 1 coldKamoshika
	tags:job
	on tick:yield 0.5 capriCrystal

     *bigBlanket
	name:Big blanket
	desc:The caprinaes can all huddle under this big blanket for warmth. It is woven from a thread synthesized using cappyness.
	cost:10 cappyness
	tags:healcold
	on tick:yield 0.2*(coldKamoshikas) cappyness
	req:10 coldKamoshikas

    *toyBox
	name:Toy box
	desc:For a fleeting moment, the sad serows will be very happy to have toys to play with.
	cost:20 capriCrystals
	tags:healsad
	on tick:yield 0.2*(sadSerows) cappyness
	req:1 sadSerow

    *goatMovies
	name:Goat movies
	desc:This goat-cinema will allow your taiwanese serows to enjoy fun movies together, distracting them from the dread of existence. Goat moviemakers need cappyness to create new films, though.
	cost:10 cappyness
	tags:healsad
	on tick:yield 0.4*(sadSerows) cappyness
	req:10 sadSerows

    *coldMutator
	name:Cold-mutation
	desc:This process can turn a cold kamoshita into a sad serow, taking the cold from outside the goat and injecting it inside the goat.
	cost:1 coldKamoshita, 120 capriCrystals
	tags:transmutation
	on earn:yield 1 sadSerow
	req:1 sadSerow
	cost increase:100%
