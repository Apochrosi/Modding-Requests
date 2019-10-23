# Modding-Requests
Modding requests that I have for Paradox to make it possible to create better mods











1 - custom policy cooldowns

Policies should have a default cooldown period, but you should also be able to give a policy a custom cooldown different from the default. 


2 - More government requirements

In the readme_requirements.txt in the governmets folder of the game is a list of which values can be used to restrict authorities, civics and species classes.
What I would like to see is that each of them gets som new values that can be used with them.

New values listed below:

# Authorities support:
#   - country_type
#   - ethics

#   - traits
#   - civics
#   - authority
#   - country_flag
#   - species_class
#   - archetype
#


# Civics support:
#   - country_type
#   - ethics
#   - authority
#   - civics

#   - traits
#   - country_flag
#   - species_class
#


# Species classes support:
#   - country_type
#   - ethics
#   - authority
#   - civics

#   - traits
#   - country_flag
#


3 - Scripted images

While we do have scripted localisation granting us text that can change depending on a given condition, what I would like to see would be the same thing done with images. What I mean by this is that you could for example say the mining guilds civing showed one icon if you are democratic and a different one if you are dictatorial. That was just an example but there are lots of scenarios where I would like for certain, traits, civics and and other stuff to show a different image than default in a given scenario.



4 - scriptable species rights

Currently we have the ability to edit already implemented species rights but we have no way of implementing our own into the game.



5 - technology feature flags

Feature falgs for technologies are currenlty hard locked to vanilla ones and new ones cannot be created, this creates some problems when dealing with special technologies that should enable or disable certain features.



6 - Custom personality behaviours

There are currently a bunch of personality behaviours implemeted in the game that we can use as we wish, and new personalities can be created without too much trouble. The problem lies rather with influencing the behavior of personalities beyond what the game offers by default. What I would like to see is us being able to add in our own behavoirs that we can use to make personalities more unique, as there multiple times where I have wanted to used them but found it unable to be cahnged. Take for example the robot_exploiter and the robot_liberator behaviours. Those are used to influence whether an empire give robots free will and equal rights or enslave them. One scenario I have encountered is when I implemeted a new species class called ethreals that where one caould say the spiritual answer to robots in the form of psionic energy beings. What I liked to do woulb be to give some personlites a ethereal_exploiter = yes behaviour but since behaviours cannot be added that didn't happen.



7 - Zero point ethics

Depending on whether some features get implemted in the future (backgrounds) this is something that I need for some things to work. This is just about wanting the ability to have an ethic cost 0 ethic points. With this ability one could creat "fake" ethics that only exists in the game show a different set of authorites in the empire creation menu deppending on which was chosen. Other uses also exists.



8 - A way to divide authorities

While the game keeps getting bigger and bigger, new authorites seems to be popping up more often. What we need is a way to divide authorites into types and being able to choose how and when which authorites appear in the main species creation menu. Currently the only way to make something like this possible is to make custom ethics that take the role of buttons in this menu, but that solution just causes problems later on.



9 - Trait folding

This would be the ability for us define instances where if a specific set of traits are on a species you will instead of seeing both those traits listed see a new third on instead. For example Say a species has the quick learners trait and you genemod Intelligent onto it. Then when the gene edit is done the species appers to have a new trait Talented Learners instead of the parts that make up for it. You should be able to define what modifers this new folded trait should have but it should also be cosmetic only. By that I mean that the species in the code is registered to still have the components of the folded trait on it and that the new trait is just 

The reason for me wanting this is a scenario where a species has multiple traits that give similar effects like immortality.

There was one mod where I made a custom ascension path where your species ended up both Psionic and Cybernetic, what I wanted was to have one Psibernetic trait listed on the species instead of those two at the same time. The problem is that by introducing a new trait adn replacing those two I would have to go back throughout the rest of the game files and edit them to now effect the new trait.

By having a Psibernetic still being both Psionic and Cybernetic in the code, files that deal with events related to psionic species or cybernetic species will need minimal if any code changes.



10 - climate Habitability modifiers

Currently in the game there are two ways to get better habitability for a planet. The first is a generic pop_environment_tolerance that gives a flat habitability bonus to all planets and a pc_***_habitability modifier that gives bonus habitability for a certain planet.

The problem with this system is when you want to add different habitability modifiers for different planets you end with very many modifiers. This isn't really a problem in the vanilla game but when playing a modded game with 30 planet classes the list of planet habitability modifiers added to each species starts getting really long and confusing.

My solution for this problem would be to add a "climate_***_habitability". Each planet class in the game can be given a special climate category that it is considered to be part of.

Say you have a trait that has a "climate_dry_habitability = 10" modifier this trait would then give the species plus 10% habitability to all planet classes with dry habitability which in the vanilla game would correspond to Arid, Dessert and Savannah worlds.

With these new modifiers I could turn these complex habitability traits here

[CODE]trait_pc_desert_preference = {
    modifier = {
        # Primary
        pc_desert_habitability = @primary

        # Hot and Dry
        pc_arid_habitability = @secondary
        pc_savannah_habitability = @secondary
        pc_dune_habitability = @secondary
        pc_mesa_habitability = @secondary
        pc_oasis_habitability = @secondary
        pc_cambrian_habitability = @secondary
        pc_latteral_habitability = @secondary

        # Hot and Wet
        pc_continental_habitability = @tertiary
        pc_tropical_habitability = @tertiary
        pc_ocean_habitability = @tertiary
        pc_mangrove_habitability = @tertiary
        pc_atoll_habitability = @tertiary
        pc_tepui_habitability = @tertiary
        pc_lush_habitability = @tertiary
        pc_terrestrial_habitability = @tertiary

        # Cold and Dry
        pc_arctic_habitability = @tertiary
        pc_alpine_habitability = @tertiary
        pc_tundra_habitability = @tertiary
        pc_steppe_habitability = @tertiary
        pc_katpana_habitability = @tertiary
        pc_atacama_habitability = @tertiary
        pc_antarctic_habitability = @tertiary
        pc_gelid_habitability = @tertiary

        # Cold and Wet
        pc_boreal_habitability = @quaternary
        pc_cascadian_habitability = @quaternary
        pc_bog_habitability = @quaternary
        pc_crag_habitability = @quaternary
        pc_glacial_habitability = @quaternary
        pc_geothermal_habitability = @quaternary
        pc_retinal_habitability = @quaternary
        pc_marginal_habitability = @quaternary
    }
}[/CODE]

Into simple ones like the one below.

[CODE]trait_pc_desert_preference = {
    modifier = {
        # Primary
        pc_desert_habitability = 20

        # Hot and Dry
        climate_hotdry_habitability = @secondary

        # Hot and Wet
        climate_hotwet_habitability = @tertiary

        # Cold and Dry
        climate_colddry_habitability = @tertiary

        # Cold and Wet
        climate_coldwet_habitability = @quaternary
    }
}[/CODE]

The primary modifer does have to be set to 20 though for the total to end up at 80 since the secondary modifier already gives it 60.

All unimportant tags have been removed from these two traits to make it easier to show the important parts.



11 - possible/potential tags for spritetypes and container window icons

Give sprite icon like the arrows used in traditions to have possible and potential tags. This will give us the ability for arrows or other images in such menus to be able to appear and dissapear under certain conditions.

An example of this would be the ability to change which arrows appear in the tradition menu under a certain condition.

Or maybe just add a arrow/image swap file where we can do this. Under condition x show file A, if else show nothing.



12 - Moddable election types

Currently in the game there are two distinct election types with the democratic and oligarchic types. What I would like to do would be to change how these two worked and be able to create new ones. Maybe also be able to combine the has_heir with them to create a new election type would work correctly having both the dynastic heir attribute and the election attribute.



13 - possible_secondary tag in species classes

Would it be possible add a way for a species class to not show up in species appearance list in the beginning of the game but is able to show up when you go to the secondary species appearance selection screen when you have chosen a civic that enables that. The reason why I want this is that I have made some special civics that can only be chosen at start that gives the player a robotic secondary species. The problem is that for this to work correctly I would have to make the ROBOT species class available for species selection and it would thus be a category that you could choose a portrait from. There would thus be two categories for the robotic portraits one only made for playing as machines with machine inteligence and one category only for selecting the appearance for a robotic secondary species. Making it so a species class could show up in the secondary species selection but not in the main species collection would solve this issue. Currently I'm forced to have the player choose their secondary species from the Machine species class and that creates a bunch of other problems after the game has started. These problems could be solved if I found a way to convert a the spawned species class from MACHINE to ROBOT but I have not being able to do that successfully either.

To sumarize I would for a species class to have "possible_secondary" work even if "playable" is set to "has_global_flag = game_started".

possible_secondary = {
	civics = {
		OR = {
			value = civic_machine_irregular_uplifter
			value = civic_space_robotic_caretaker
		}
	}
	text = SECONDARY_SPECIES_CLASS_INVALID
}

playable = { has_global_flag = game_started }



14 - custom namelist useable in create_leader event 

Would it possible to have the create_leader use a specified namelist when it genereates a leader. This would make it possible to let the name list be in charge of choosing a name for the leader instead of us having to clone the whole create_leader sequence for each new name we want randomize.



15 - Let TRAIT_MODIFICATION_BASE_COST, TRAIT_MODIFICATION_COST_MULT and similar values be given to all species archetypes.

The next few issues has to do with the NSpecies part of the defines.

Currenlty in the game all these values are divided into two types, those used by artificial species and those used by non-artificial species. The problem lies with fact that if you try to implement a new species into the game it will have to share these values with one of those groups instead of belonging to its own.

Currently in the game these values here: "TRAIT_MODIFICATION_BASE_COST", "TRAIT_CLIMATE_MODIFICATION_COST", "TRAIT_MODIFICATION_COST_MULT", "MODIFICATION_COST_MULT" are use for all species except robots which use these here instead: "ROBO_TRAIT_MODIFICATION_BASE_COST", "ROBO_TRAIT_MODIFICATION_COST_MULT", "ROBO_MODIFICATION_COST_MULT".

What I would like to see is these defines here being opened up a bit more and make it possible for us modders to create custom entries for these values that affect certain species. What I mean by that is that I would like for each list of these tags should affect a specific species archetype. we could thus have a BIOLOGICAL_TRAIT_MODIFICATION_BASE_COST and a LITHOID_TRAIT_MODIFICATION_BASE_COST at the same time one for species classes with the BIOLOGICAL archetype and one for species classes with the LITHOID archetype. This would make it much easier to create new species classes with specific and unique rules.

The main reason for why I want this is that I have made a new buildable pop and implemented it in a mod thats called bio-constructs. These are genetically engineered lifeforms made from the bottom that has uniwue traits that make them different from standart biological species. When implemented correctly these would be an laternative to robobts and one that empires that chooses biological ascenstion to be more likely to choose. The uniwue feature of these beingsshould be that they would be a lot easier to modify the traits for. As have alsready said this isn't possible right now as they would get the standard "TRAIT_MODIFICATION_BASE_COST" value since it isn't possible create a nex exclusive one for the BIO_CONSTRUCT archetype. If i also do modify the "TRAIT_MODIFICATION_BASE_COST" it would affect both bio constructs and regular biological species something that I would like to avoid.

I would also like to see a define value that defines the defualt value for changing species portrait. Such a define should also be given to name changes. Changing only the species name shouldn't take 5000 society points for example. Maybe a child define tag that give a percentage of the species modification if only the portrait or name is changed.

Adding these features would let modders more easily add species classes and archetypes that are supposed to represent species that aren't biological but also not robotic either.

Another feature that I would like to see implemented that has a lot to to with these things here is for us to create or own technologies that enable special features for a species. I would for example like to be able to create a new technology that enables species modification for a species instead of it defaulting to the Gene tailoring tech or the Machine Template System tech. This would make it easier to make new custom buildable species as you could gain the ability earlier or later than your ability to modify your own species and robots. I would like for this to also affect planet preferences and allow us to change the tech needed to unlock this for a speciees as well.



16 - Conditional Modifiers

I would like to have the ability to give conditions to the modifiers of civics and ethics.

For example make it possible to code the Idealistic Foundation civic so That if you have the democratic authority it grants +5% pop happiness while if you have the oligarchic authority it grants +5% influence from factions instead. The same should also apply to ethics as well.



17 - Custom ethics icons in faction menu if pop ethic following is above certain percentage

Would it be possible to make it for ethics in the faction menu that we have more than 0 pops following to turn change color or use a different icon. Currently it's a bit hard to at a glance see which ethics actually have any followers. This is especisally true when you are playing with a mod that add many more ethics into the game.



18 - authority trait restrictions

In the authorities.txt file you can specify if an authority starts with one ore more specified traits by using the "traits = {" tag. What I would to see is to be able to add conditions for these traits to appear. Such as for example if you choose a species appearance from the Arthropoid category and choose imperial authority your species gets a special hive_like trait.m

[CODE]

traits = {
	if = {
		limit = {
			is_species_class = ART
		}
	}
	trait = trait_hive_like
}

[/CODE]



19 - Editable game files while the game is running and seeing the changes being made without restarting the game

Will we ever have the ability to directly modify the files of a mod that is loaded in an open game and have the update to show the change without needing to restart the game. This would be really great to have when working on the guis as that is a really taxing part of modding the game as one would need to restart the game and update the mod each time one changes a value.



20 - Let us use AND in the civic and authority files for better restricions

Woud it be possible to add AND to the civic and authority creation file. Some restriction are currently very hard to make and also very spaghetti cody without this option. This would also let us make more specific authority restrictions like making a new authority that can be chosen if you have either ethic A or B but not a combination of them. This is not currently possible do in the game.

For example if I added the collectivist and individualist ethic pari back into the game and gave it the same restrictions that authoritarian currently has. If I made an empire that was fanatic authoritarian and materialist I could only choose between imperial or dictatorial. The same would apply if I choose fanatic collectivist and materialist and I could one agaoin only choose between those two. What I want is that if I then choose fanatic authoritarian and collectivist or fanatic collectivist and individualist I would only be able to choose imperial authority and not dictatorial. In short I would like to be able to restrict authorities to not only individual ethics but also specific ethic combinations.

If you added the ability to add AND to the civic area I would also be able make the ethic restrictions for this civic here much less complicated.

[CODE]
ethics = {
	OR = {
		value = ethic_gestalt_consciousness
		value = ethic_light_gestalt_consciousness
	}
	OR = {
		value = ethic_gestalt_consciousness

		value = ethic_fanatic_xenophobe
		value = ethic_fanatic_pacifist
		value = ethic_fanatic_isolationist

		value = ethic_pacifist
		value = ethic_xenophobe
	}
	OR = {
		value = ethic_gestalt_consciousness

		value = ethic_fanatic_xenophobe
		value = ethic_fanatic_pacifist
		value = ethic_fanatic_isolationist

		value = ethic_isolationist
		value = ethic_xenophobe
	}
	OR = {
		value = ethic_gestalt_consciousness

		value = ethic_fanatic_xenophobe
		value = ethic_fanatic_pacifist
		value = ethic_fanatic_isolationist

		value = ethic_isolationist
		value = ethic_pacifist
	}
}
[/CODE]

This would let us shorten this long and confusingly coded text above into a what I have written below. Certain ethics and civics restriction combinations that weren't possible before would also be possible now

[CODE]
ethics = {
	OR = {
		value = ethic_gestalt_consciousness
		AND = {
			value = ethic_light_gestalt_consciousness
			value = ethic_fanatic_xenophobe
		}
		AND = {
			value = ethic_light_gestalt_consciousness
			value = ethic_fanatic_pacifist
		}
		AND = {
			value = ethic_light_gestalt_consciousness
			value = ethic_fanatic_isolationist
		}
		AND = {
			value = ethic_light_gestalt_consciousness
			value = ethic_isolationist
			value = ethic_xenophobe
		}
		AND = {
			value = ethic_gestalt_consciousness
			value = ethic_isolationist
			value = ethic_pacifist
		}
		AND = {
			value = ethic_gestalt_consciousness
			value = ethic_xenophobe
			value = ethic_pacifist
		}
	}
}
[/CODE]

21 - Add delayed tooltip removal value

Create a NInterface tooltip define value that has to with how long after moving a mouse away from a tooltip it takes for the tooltip info window to go away.

NInterface = {
	TOOLTIP_TIME 					= 0
	TOOLTIP_DELAYED_TIME 			= 0
}



22 - value formulas

The ability for use to write mathematical formulas in the code or have values be different by more than one subvalue

Let us also be able to modify how values like tradition cost is calculated.



23 - resource tag question

What does the newly added resources tag in species classes do?


24 - Custom planet values

Let us create and make our own custom planet values like ammenities with modifiers.


25 - editable shift_ethic command

make shift_ethic customizable and let us change how it works.


26 - shift_ethic exclusion

let us exclude certain ethics from being affected by ethic shift. For example, lets make an Egalitarian, Materialist and Xenophobe empire with ethic attractions in that order from high to low. If this empire got an event that would shift its ethics to militarism, the xenophobe would be removed since it  has the lowest support in the empire and be replaced by the new militarist ethic.

If this event instead had a xenophobe exclusion tag, xenophobe would not be the ethic that would be replaced by militarist, but instead the second least popular government ethic, materialist would be replaced by militarist instead.


shift_ethic = {
	ethic_spiritualist
	exclude = {
		ethic_authoritarian
	}
}



27 - Multiple origins

Can it be possible to make it so that we can mod it to be possible to choose multiple origins?


28 - Multiple "origin" systems

Would it be possible to let modders "clone" the origin system and have this extra option be repurposed for giving the player more categories to choose from when designing an empire.


29 - Decoupling species classes from ship sets

Currently in the game all species classes need an acompanying ship set and vice versa. This leads to cases such as ship set mods where phantom species classes are added to the species class menu. In species class mods the problem is that any new species classes must share its shipset with another vanilla species class. This leads to a promlem regarding the name of the shipset, as the shipset gets its name from the alphabetical first species class that has that shipset as its preferred one. This leads to problems where the names of the vanilla shipsets have their names changed to something else because a mod implmenting new species classes has been used. Decoupling species classes from ship sets would fix all these problems.


30 - The ability to modify species archetypes and -classes.

Add a way to modify the archetype and species class of a species through an event.


31 - Ethics give traits

Make it so that ethics can grant traits to a species in the same way that civics and authorities can.









































































