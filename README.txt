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
  *resources
    contains:Resources
    header:These are your resources.
  *buildings
    contains:Buildings
    header:These are things you can build.
    tooltip origin:left
  *unlockables
    contains:Upgrades, Achievements
    names:hide
        
Buttons
    *kamoshiGacha
        name:KAMOSHIGACHA
        desc:Click to spend CAPRICRISTALS and gain sad caprinae.
        on click:anim icon wobble
        on click:yield 1 coldKamoshika
	cost:120 capriCristals
        icon:stuff/bunny.png
        no text
        class:bigButton hasFlares
        icon class:shadowed
        tooltip origin:bottom
        tooltip class:red

    *cuteBlanket
	name:CUTE BLANKET
	desc:Click on this CUTE BLANKET to generate warmth!
	on click:anim icon wobble
	on click:yield 1 warmth
        
Resources
    *coldKamoshika|coldKamoshikas
        name:KAMOSHIGLACE|KAMOSHIGLACES
        desc:These kamoshikas are so cold they turned to ice and need to be warmed up. <//> If you do, they'll get happy and be adopted!
        icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/kamoshiglace.PNG
        class:noBackground
        show earned
        hidden when 0

    *capriCristal|capriCristals
        name:CAPRICRISTALS
        desc:Fell from heaven with the KAMOSHIGACHA MACHINE. <//> You can spend those on the KAMOSHIGACHA. (And some other things.)
        icon:icons[0,1]
	show earned
	on tick:yield 1 capriCristal
	on start:yield 120 capriCristals

    *warmth
        name:WARMTH
        desc:The WARMTH you'll need to heat back up any cold caprinae from the KAMOSHIGACHA. <//> When you do, they'll get adopted!
        icon:icons[2,0]
        class:noBackground

    *cappyness
	name:CAPPYNESS
	desc:Caprine happiness! You'll earn it every time you send a caprinae for adoption!
	icon:icons[3,0]
	show earned
        hidden when 0

Buildings
    *TEMPLATE
        on click:anim glow
        
    *warmUpKamoshika
        name:Warm up a KAMOSHIKOLD
	tags:adoptionAction
        desc:A tiny little cage.<//><b>Effect:</b><.>Produces 1 rabbit every 10 seconds.
        icon:icons[3,0]
        cost:1 coldKamoshika, 100 warmth
        on click:yield 120 capriCristals
	on tick:yield 0.1 cappyness
        req:1 coldKamoshika:earned
