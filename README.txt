Let's make a game!
    name:Fairy Shelter for Cutiepie Comfort & Rescue
    by:fae.exe & Alyyyd
    desc:Alid was bored so we made a game.<//>Make cute crying critters happy.
    created:21/6/2025
    updated:26/6/2025
    version:1

Settings
    background:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/background.PNG
	spritesheet:icons, 48 by 48, https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/icon-spritesheet.png
    building cost increase:115%
    building cost refund:50%
    stylesheet:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/stylesheet.txt
    stylesheet:stuff/bigBlue.css

Layout

*buttonsBox
	contains:coinBankBox, coinBox, gachaBox
	*coinBankBox
		contains:tag:coinBank
	*coinBox
		contains:tag:coin
		names:hide
	*gachaBox
    		contains:tag:gachamachine

*kamoshikaBox
    header:KAMOSHIKAS
    contains:coldBox, sadBox, hungryBox, lonelyBox, angryBox
	*coldBox
		contains:tag:cold
	*sadBox
		contains:tag:sad
	*hungryBox
		contains:tag:hungry
	*lonelyBox
		contains:tag:lonely
	*angryBox
		contains:tag:angry

*healingBox
	contains:tag:healangry, tag:healcold, tag:healhungry, tag:heallonely, tag:healsad
	header:Make your kamoshikas feel better :'(
	tooltip origin:left
	icons:show
	ps:show
*jobBox
	contains:tag:job
	header:Put them to work???
*smileConversionBox
	contains:tag:smileConverter
	header:Wait you can do that??????

*cappynessBox
    contains:tag:crystals, tag:kamosmilesres
    header:GACHA CURRENCIES

*upgradeBox
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

    *capriCoinButton
        name:Capricoin|Capricoins
	class:bigButton hasFlares
        desc:Fell from heaven with the KAMOSHIGACHA MACHINE. Click to gain Capricoins to spend on the KAMOSHIGACHA. 
        icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/capricrystals.PNG
	icon class:kamoIcon
	tags:coin
	on start:yield 120 capriCoins
	on click:yield 1 capriCoin

Resources

    *capriCoin|capriCoins
	name:The Capricoinbank
	desc:You can spend those on the KAMOSHIGACHA. (And some other things.)
	tags:coinBank
	on tick:yield 1 capriCoin
	show earned

    *kamosmile|kamosmiles
	name:Kamosmile|Kamosmiles
	icon class:mediumIcon
	desc:The happiness from Kamoshikas! You'll earn it by satisfying their needs!
	tags:kamosmilesres
	icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/capricrystals.PNG
	show earned

    *coldKamoshika|coldKamoshikas
        name:Kamoshiglace|Kamoshiglaces
	class:coldCaprine
	icon class:kamoIcon
	tags:caprine, cold
        desc:These kamoshikas are so cold they turned to ice and need to be warmed up. <//> <b>Rarity:</b> Common.
        icon:https://raw.githubusercontent.com/fae-exe/kamoshigay/refs/heads/main/kamoshiglace.PNG
	hidden when 0
	show earned

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
		class:hungry
		icon class:kamoIcon
		tags:carpine, hungry
		desc:These kamoshikas are always hungry. You could be shoveling grass into them all day long. <//> <b>Rarity:</b> Rare.
		hidden when 0

    *angryShika|angryShikas
		name:Kaboomshika|Kaboomshikas
		class:angry
		icon class:kamoIcon
		tags:caprine, angry
		desc:These kamoshikas are very angry and need to calm down. Maybe some meditation, or a punching-ball. <//> <b>Rarity:</b> Extra rare.
		hidden when 0

    *lonelyShika|lonelyShikas
		name:Kaloneshika|Kaloneshikas
		class:lonely
		icon class:kamoIcon
		tags:caprine, lonely
		desc:These mountain goats have lives alone on their big mountains for so long, they want a little company. <//> <b>Rarity:</b> Secret rare.
		hidden when 0

Buildings

// HEALING BUILDINGS

    *TEMPLATE
        on click:anim glow
        
    *heater
        name:Heater
        desc:<q>Generates a little heat to make your freezing kamoshikas warmer and happier.</q> <//> <.> Generates <b>0.1 kamosmile</b> per <b>kamoshiglace</b> per second.
        cost:20 capriCoins
		class:cold
        icon:icons[0,1]
		tags:healcold
		on tick:yield 0.1*(coldKamoshikas) kamosmiles
        req:1 coldKamoshika:earned

    *bigBlanket
	name:Big blanket
	desc:<q>The kamoshikas can all huddle under this big blanket for warmth.</q> <//> <.> Generates <b>0.2 kamosmile</b> per <b>kamoshiglace</b> per second.
	cost:100 capriCoins
	class:cold
	icon:icons[0,2]
	tags:healcold
	on tick:yield 0.2*(coldKamoshikas) kamosmiles
	req:10 coldKamoshikas:earned

    *toyBox
	name:Toy box
	class:sad
	desc:<q>For a fleeting moment, the sadmoshikas will be very happy to have toys to play with.</q> <//> <.> Generates <b>0.2 kamosmile</b> per <b>sadmoshikas</b> per second.
	cost:30 capriCoins
	icon:icons[0,3]
	tags:healsad
	on tick:yield 0.2*(sadShikas) kamosmiles
	req:1 sadShika:earned

    *goatMovies
	name:Goat movies
	class:sad
	desc:<q>This goat-cinema will allow your serows to enjoy fun movies together, distracting them from the pain of existence.</q> <//> <.> Generates <b>0.4 kamosmile</b> per <b>sadmoshikas</b> per second.
	cost:200 capriCoins
	icon:icons[0,4]
	tags:healsad
	on tick:yield 0.4*(sadShikas) kamosmiles
	req:10 sadShikas:earned

    *grassPatch
        name:Grass patch
	class:hungry
        desc:<q>Grow some grass to feed your hungrishikas! But this will not satiate them for long.</q> <//> <.> Generates <b>0.5 kamosmile</b> per <b>sadmoshikas</b> per second.
        cost:40 capriCoins
        icon:icons[0,5]
	tags:healhungry
	on tick:yield 1*(hungryShikas) kamosmiles
        req:1 hungryShika:earned

    *foodDelivery
        name:Food delivery
	class:hungry
        desc:<q>Get some food delivered directly to your goatstep! Shovel that right into the shikas' mouths.</q> <//> <.> Generates <b>4 kamosmile</b> per <b>hungrishika</b> per second.
        cost:500 capriCoins
        icon:icons[0,6]
	tags:healhungry, restaurant
	on tick:yield 5*(hungryShikas) kamosmiles
        req:10 hungryShika:earned

    *punchingBag
        name:Punching bag
	class:angry
        desc:<q>A punching (well more like headbutting) bag so your angriest goats can take it out on something.</q> <//> <.> Generates <b>5 kamosmile</b> per <b>kaboomshika</b> per second.
        cost:50 capriCoins
	tags:healangry
	on tick:yield 5*(angryShikas) kamosmiles
        req:1 angryShika:earned
        icon:icons[0,7]

    *meditationWaterfall
	name:Meditation waterfall
	class:angry
	desc:<q>A gorgeous waterfall that your tahrs can soak under while reflecting on the futile aspects of rage and the power of love.</q> <//> <.> Generates <b>25 kamosmile</b> per <b>kaboomshika</b> per second.
	cost:800 capriCoins
	tags:healangry
	on tick:yield 25*(angryShikas) kamosmiles
        req:10 grassPatch
        icon:icons[0,8]

    *headscritchDispenser
        name:Headscritch dispenser
	class:lonely
        desc:<q>A nice headscratch dispenser to help your loneliest kamoshikas feel a little loved.</q> <//> <.> Generates <b>10 kamosmile</b> per <b>kaloneshika</b> per second.
        cost:100 capriCoins
		tags:heallonely
		on tick:yield 10*(lonelyShikas) kamosmiles
        req:1 lonelyShika:earned
        icon:icons[0,9]

    *playPen
	name:Play pen
	class:hungrysad
	desc:A play pen for both your kaloneshikas and your sadshikas! Playing together means being together! <//> <.> Generates <b>0.5 kamosmile</b> per <b>sadmoshika</b> per second. <.> Generates <b>20 kamosmile</b> per <b>kaloneshika</b> per second.
	cost:1000 capriCoins
	tags:heallonely, healsad
	on tick:yield (20*(lonelyShikas) + 0.5*(sadShikas)) kamosmiles
	req:2 lonelyShika:earned
	req:20 sadShikas:earned
        icon:icons[0,10]

    *kamoshiKhebab
	name:Kamoshi-khebab
	class:hungrysad
	desc:<q>A cool comfort food chain for kamoshikas. The kebabs are vegetarian.</q>
	cost:5000 capriCoins
	tags:heallonely, healhungry, restaurant
	on tick:yield (20*(hungryShikas) + 1*(sadShikas)) kamosmiles
	req:5 angryShikas:earned
	req:40 sadShikas:earned
	req:1 foodDelivery:earned
        icon:icons[0,10]

    *gourmetRestaurant
	name:Gourmet restaurant
	class:hungrylonely
	desc:<q>A fine dining establishment kamoshikas can go to in order to eat and enjoy the company.</q>
	cost:20000 capriCoins
	tags:heallonely, healhungry, restaurant
	on tick:yield (100*(lonelyShikas) + 40*(angryShikas)) kamosmiles
	req:4 lonelyShikas:earned
	req:10 angryShikas:earned
	req:1 kamoshiKhebab:earned
        icon:icons[0,10]

    *kamoshiRevue
	name:Kamoshi-revue|Kamoshi-revues
	class:lonelysad
	desc:<q>A special revue kamoshikas can go to to watch kamoshidrag shows.</q>
	cost:10000 capriCoins
	icon class:kamoIcon
	tags:heallonely, healsad
	on tick:yield (50*(lonelyShikas) + 2*(sadShikas)) kamosmiles
	req:3 lonelyShika:earned
	req:40 sadShikas:earned
	icon:icons[0,10]

    *mentalHealthCenter
	name:Mental health center|Mental health centers
	class:angrylonelysad
	desc:<q>An extensive care facility to help kamoshikas struggling with mental health issues.</q> <//> <.> Generates kamosmiles for each of your sad, angry, and lonely kamoshikas.
	cost:20000 capriCoins
	icon class:mediumIcon
	tags:heallonely, healsad, mentalHealth
	on tick:yield (100*(lonelyShikas) + 40*(angryShika) + 5*(sadShikas)) kamosmiles
	req:3 lonelyShika:earned
	req:40 sadShikas:earned
        icon:icons[0,10]

// JOBS

    *coldExplorer
	name:Train cold explorers
	class:cold
	desc:<q>Gives very heavy coats to a kamoshikas so they can face their fear and explore the wilds in search of capricoins!</q> <//> <.> Rescue 1 kamoshiglace every 50 seconds.
	cost:100 capriCoins, 1 coldKamoshika
	tags:job
	on tick:yield 0.5 capriCoin
	cost increase:200%
	req:5 coldKamoshikas:earned

    *goatRescuer
	name:Train shika rescuers
	class:sad
	desc:<q>Gives helicopters and pilot licenses to your sad kamoshikas. The fulfillment of saving kamoshikas from the cold distracts them from their awful sadness.</q> <//> <.> Rescue 1 kamoshiglace every 50 seconds.
	cost:250 capriCoins, 1 sadShika
	tags:job
	on tick:yield 0.02 coldKamoshika
	cost increase:200%
	req:5 sadShika:earned
	
    *goatChef
	name:Train goat chefs
	class:hungry
	desc:<q>Trains hungry kamoshikas to become chefs. In this way, they will find a life calling in saving all others from hunger as well.</q> <//> <.> Increases the efficiency of your restaurant facilities by 5%.
	cost:500 capriCoins, 1 hungryShika
	tags:job
	passive:multiply yield of tag:restaurant by 1.05
	cost increase:200%
	req:1 gourmetRestaurant:earned
	
    *goatPsychologist
	name:Train kamopsychologists
	class:lonely
	desc:<q>Trains lonely kamoshikas to become psychologists. After going to therapy a lot, they have become able to help others to heal as well.</q> <//> <.> Increases the efficiency of your mental health facilities by 5%.
	cost:5000 capriCoins, 1 lonelyShika
	tags:job
	passive:multiply yield of tag:mentalHealth by 1.05
	cost increase:200%

// SMILE CONVERSION FACILITIES

    *smileCondensator
	name:Smile condensator
	desc:<q>A machine to turn the happiness of kamoshikas into capriCoins.</q> <//> <.> Gives 0.1 capricoin per second at base. <.> Decreases kamosmile income by 1 kamosmile per second.
	cost:20 kamosmiles
	tags:smileConverter
	on tick:yield 0.1 capriCoin
	on tick:yield -1 kamosmile
	req:(kamosmile:ps) >= 1
	req:(kamosmiles:earned) >= 10

    *kamoshiParty
	name:Kamoshiparty harvester|Kamoshiparty harvesters
	desc:<q>The happy kamoshikas are partying! Their residual smiles can be converted into a lot of capricoins.</q> <//> <.> Gives <b>1 capricoin</b> per second. <.> Decreases kamosmile income by <b>2 kamosmiles</b> per second.
	cost:100 kamosmiles
	tags:smileConverter
	on tick:yield 1 capriCoin
	on tick:yield -2 kamosmile
	req:(kamosmile:ps) >= 2
	req:(kamosmiles:earned) >= 50
	
    *wishResonator
	name:Wish resonator|Wish resonators
	desc:<q>The happier the kamoshikas, the more potent are their wish for others to experience the same.</q> <//> <.> Gives <b>5 capricoin</b> per second. <.> Decreases kamosmile income by <b>5 kamosmiles</b> per second.
	cost:1000 kamosmiles
	tags:smileConverter
	on tick:yield 5 capriCoin
	on tick:yield -5 kamosmile
	req:(kamosmile:ps) >= 5
	req:(kamosmiles:earned) >= 500

    *smileReactor
	name:Smile reactor|Smile reactors
	desc:<q>The happiness of the kamoshikas is growing too potent - it has to be canalyzed.</q> <//> <.> Gives <b>10 capricoin</b> per second. <.> Decreases kamosmile income by <b>8 kamosmiles</b> per second.
	cost:5000 kamosmiles
	tags:smileConverter
	on tick:yield 10 capriCoin
	on tick:yield -8 kamosmile
	on earn:show this
	req:(kamosmile:ps) >= 8
	req:(kamosmiles:earned) >= 2500

    *coldMutator
		name:Cold-mutation
		desc:<q>This process can distillate the essence of kamoshiglaces into a singular sadmoshika, taking the cold from <i>outside</i> the goats and concentrating it within a single one of them. The others are released into the wild.</q> <//> <.> Gives you 1 sadmoshika.
		cost:5 coldKamoshika, 500 capriCoins
		tags:transmutation
		on earn:yield 1 sadShika
		req:1 sadShika

	*autoGacha
		name:Auto gacha
		desc:<q>A machine that will insert kamoshicoin into the kamoshigacha for you! You don't need to pull manually anymore!</q> <//> <.> Spends 120 kamoshicoin every second to pull from the gacha machine.
		cost:1000 capriCoins
		on tick:yield -120 capriCoins
		on tick:do gachagacha with kamoshiGacha
		req:(capriCoins:ps) >= 120

Upgrades
    *TEMPLATE
        on click:anim glow
    
    //food upgrades
    //inspiration : http://rabbit.org/suggested-vegetables-and-fruits-for-a-rabbit-diet/
    
    *betterConductors
        name:Better conductors
        desc:<q>An improvement in heating technology. Doubles the efficiency of your heaters.</q>.<//><b>Effect:</b><.>Heaters generate twice as much <b>kamosmiles</b>.
        icon:icons[1,1]
        cost:100 kamosmiles
        passive:multiply kamosmile yield of heater by 2
        req:10 heater
