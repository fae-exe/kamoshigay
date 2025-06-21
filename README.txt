Let's make a game!
    name:Fairy Shelter for Cutiepie Comfort & Rescue
    by:fae.exe & Alyyyd
    desc:Alid was bored so we made a game.<//>Make cute crying critters happy.
    created:25/7/2017
    updated:24/10/2017
    version:1

Settings
    background:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/background.PNG
    building cost increase:115%
    building cost refund:50%
    spritesheet:icons, 48 by 48, stuff/bunnyIcons.png
    stylesheet:stuff/bigBlue.css

Layout
*main
    contains:gachabuttons, needsbuttons
    header:BUTTONS
	*gachabuttons
	     contains:tag:gachamachine
	     class:fullWidth
	*needsbuttons
	     contains:tag:needsfulfiller
	     class:fullWidth
*res
    contains:currencyResources, sadCaprines, needsResources, buttons
    *currencyResources
    	contains:tag:currencies
    	header:GACHA CURRENCIES
	class:fullWidth
     *sadCaprines
    	contains:tag:caprine
    	header:SAD CAPRINAES
	class:fullWidth
     *needsResources
    	contains:tag:needs
    	header:FULFILL THEIR NEEDS
	class:fullWidth

*store
  contains:buildings, upgrades
  *buildings
    contains:BulkDisplay, Buildings
    header:Buildings
    tooltip origin:left
  *upgrades
    contains:Upgrades
    header:Upgrades
    costs:hide
    names:hide
        
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
		if (chance(50%))
			yield 1 coldKamoshika
		else
			yield 1 sadSerow
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
        desc:Fell from heaven with the KAMOSHIGACHA MACHINE. You can spend those on the KAMOSHIGACHA. (And some other things.)
        icon:icons[0,1]
	show earned
	tags:crystals
	on tick:yield 1 capriCrystal
	on start:yield 120 capriCrystals

    *cappyness
	name:Cappyness
	desc:Caprine happiness! You'll earn it every time you send a caprinae for adoption!
	icon:icons[3,0]
	show earned
	tags:cappyness
        hidden when 0

    *coldKamoshika|coldKamoshikas
        name:Kamoshiglace|Kamoshiglaces
	tags:caprine
        desc:These kamoshikas are so cold they turned to ice and need to be warmed up.
        icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/kamoshiglace.PNG

    *sadSerow|sadSerows
	name:Sad serow|Sad serows
	tags:caprine
	desc:These taiwanese serows are sad because they want to play!
	icon:https://upload.wikimedia.org/wikipedia/commons/1/16/%E9%95%B7%E9%AC%83%E5%B1%B1%E7%BE%8A.jpg

    *angryTahr|angryTahrs
	name:Fulminatahr|Fulminatahrs
	tags:caprine
	desc:These tahrs are very angry and need to calm down. Maybe some meditation, or a punching-ball.

    *lonelyGoat|lonelyGoats
	name:Goatlitaire|Goatlitaires
	tags:caprine
	desc:These mountain goats have lives alone on their big mountains for so long, they want a little company.

Buildings
    *TEMPLATE
        on click:anim glow
        
    *heater
        name:Heater
        desc:Generates a little heat, which will make your Kamoshiglace generate a little cappyness.
        cost:20 capriCrystals
	tags:cold
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
	tags:cold
	on tick:yield 0.2*(coldKamoshikas) cappyness
	req:10 coldKamoshikas
