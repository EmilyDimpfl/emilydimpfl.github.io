---
layout: post
title:  Tactics Design, part 1 of ???
published: true
---

## Welcome!

I've been working on my game for about a year now, working in my spare time in the evenings, and I've put a lot of time and thought into what I want to make, and writing documentation to help me keep track of my thoughts. This post started out as documentation, so I hope it isn't too dry!

## Tactics Inspiration:

I've loved video games since I was a kid, and I really like how technical they can become, and how different play styles can be represented. Because I'm making a grid based, turn based tactics game, I want to talk about a couple examples in particular:

* Dofus
* Divinity Original Sin 2
* Fire Emblem

Part of the reason I started developing my game was because I felt like there were aspects of otherwise fantastic tactics games that I wanted to improve on that weren't going to be solved because of forces of economics, history, or simply vision. So, let's take a look at some of the ways these games typically work:

## Turns

Some tactics games in the vein of Fire Emblem force the player to move, and then act, and only (typically) allow a unit to move once a turn. Fire Emblem Dancers and Wargroove's Caesar special ability give units the ability to move a second time, but those are special powers, and require the sacrifice of one unit's turn to give other units a turn. Typically, they also force their entire team to take their turns simultaneously.

![](../../../content/wandertale/fe3h.jpg)
*Fire Emblem: 3 Houses uses limited attack ranges and single-action turns to force players to commit to attacks. (via [nintendo.com](https://ec.nintendo.com/AU/en/titles/70010000007605))*

This turn dynamic of forcing the player to hard-commit in order to attack (and, depending on the system, potentially immediately be counter-attacked) works well in systems where there are many units. This forces the player to evaluate how many resources must be committed to preventing counter-attacks for each unit on the board, and increases the complexity of turns.

Smaller scale tactics roleplaying games like as Divinity Original Sin 2 tend to have a turn order, determined by initiative. This shifts the focus of which units to move with first to the turn order, which can allow players to address more imminent threats, and shifts the focus to what characters do (rather than what the team as a whole does). This style of play emphasizes individual characters' strengths, at the expense of having a somewhat contrived turn order (what does it even mean to go before another character in the turn order?).

Some games compound the contrived-ness of the turn order by using "speed" to affect how often characters can take their turns. I don't like "speed" affecting turn order, because it makes it difficult to plan turns ahead of time, forces the player to pay attention to the turn order *just to know when they get to go*, and is opaque to the player in general. Instead, giving the player more resources on their turn allows players to plan around having those resources, with a predictable turn order that doesn't require much attention as it stays the same throughout a fight.

## Player Resources

Giving a player more resources on their turn also allows for more flexibility in terms of defining a character's abilities - if they're fleet of foot, they could have more movement points, or if they're a glass cannon of magical bombardment, they could have more ability points to spend.

Constraining a character's resources to the Fire Emblem paradigm of attacking following movement can force certain player behaviors that make for exciting, stressful situations, but also constrains the sorts of abilities that can be designed, and limits the interactions between abilities. This can also encourage passivity as a player tries to only take safe engagements (especially early on, when they don't have many tools) and slow play, and generally limits the decision tree of what to do significantly (which is boring!).

In other systems like Dungeons and Dragons where encounters take place in more constrained areas (rather than an entire battlefield, like in Fire Emblem), players are strongly encouraged to get value out of their actions. I think this is due to several things:

* the odds are numerically stacked against the players
* players have a limited ability to control the map
* players have limited resources (spell slots)
* health is difficult to recover

I think this works well for D&D type settings, because it makes it cool when fantasy kickflips do happen - often requiring limited resources like spell slots to make happen. Giving individual characters the spotlight in these instances is really cool and good!

On the other side of the coin, characters in games like Dofus and Divinity have enough ability points (particularly at higher levels) that they can move, use multiple abilities and cause many unique effects with their abilities, in arbitrary order. Enemies typically also have powerful abilities, deep health pools, and more raw numbers on their side than player characters do. This forces players to fight at a disadvantage, necessitating clever play.

Between fights, Dofus makes the player spend resources (which early on can be quite limited) to recover health (which also gives meaning to professions like farmer, fisherman, and so on which craft out-of-combat healing items). More generically, games often try to encourage players to worry about health maintenance between fights and budgeting healing potions, but in tactics games (like Final Fantasy games) this simply encourages the player to fight meaningless battles to farm up enough money to have infinite potions they can use to heal themselves between fights. I'm more inclined to just have the player heal automatically, because I think it's more interesting to have the player spend proportionally more of their time on content that has more meaning.

## Stat Systems

Fire Emblem has a relatively straightforward stat system (although it has a long term progression of randomized stat gains, which I'll ignore here - suffice to say, I won't have random stat growth). I actually like this fairly well. Damage formulas aren't usually too complex, and it's fairly intuitive as a system, although the complexity of building characters to fit into a niche for an army can be overwhelming. I do think the combat systems can be a little too deterministic since it's possible to calculate exact damage before making a move. I like damage ranges (even if they're pretty small) because they introduce unknowns that the player has to account for, and provide opportunities for things to ✨go wrong✨.

Divinity Original Sin 2 has a somewhat more involved D&D-esque stat system, and it's secondary stats have numerous spell schools and civic stats - more on this later, as I'm somewhat ambivalent about what the stats do, but I have words about scaling.

Meanwhile, Dofus has an extremely complex gearing system with dozens of different stats:

![Map Image](../../../content/wandertale/dofus_stats.png)

While each stat does it's own thing that's relatively easily understood conceptually within the game's systems, it makes gearing very complicated, and requires the developer implement many, MANY items (and the associated crafting/drop systems). It's taken a long time for Dofus to implement enough items that there are sufficient options for the various builds that players want to make.

Some of these stats, while conceptually easily understood, are difficult to quantify in terms of value. For example, ability point and movement point reduction/parry is probability based:

```
P = A/R * Pr/2
```

Where:
```
P: Probability to make someone lose an AP/MP
A: AP/MP Reduction of the attacker
R: AP/MP Resistance of the target
Pr: Percentage of AP/MP that the target has
```

Older versions of Dofus didn't have this percentage based system, and instead spells would remove fixed amounts of AP/MP. This caused problems both in PvP and PvE, in that it trivialized many fights. An element of randomness forced players to adapt to unforeseen circumstances and helped prevent fights from being completely trivialized.

That said, Dofus is also an old game that's grown significantly over time, with many band-aids on top of band-aids - for instance, in addition to this system, if you remove all the MP from a boss, the boss then gains 3 MP. This can sometimes happen if you just get very lucky (unlucky!) with MP reduction rolls. Furthermore, there's nothing to explain this mechanic in the game, and searching for explanations online I'm not even finding anything!! 🩹 It 🩹 just 🩹 happens 🩹, and you just have to know it'll happen!!! 😱

Additionally, AP typically caps at around 12, while MP typically caps at around 6, and removal spells typically only remove 3 (for both AP and MP). As such, it's difficult to remove enough AP that enemies are significantly hampered, while it's much easier to remove enough MP.

### A quick aside about silly stat systems...

While thinking about opaque stats that are hard to evaluate the value of by numbers, I looked at Mastery in World of Warcraft. An except from the [WoW Gamepedia wiki](https://wow.gamepedia.com/Mastery):

> Each specialization has its own Mastery, offering benefits appropriate to that spec's role and abilities. Masteries' effects vary, increasing certain types of damage dealt, providing bonus DoT or HoT effects, or even generating free extra melee or spell attacks. 

> Mastery stat rating is unique as the effect of it depends both on the player's level and the specific mastery associated with their spec, with each mastery having a different amount of rating required to increase its effects.

🙃 what the heck is this lmao 🙃

## Equipment

Fire Emblem's equipment system reflects the scale of numbers in Fire Emblem games - the numbers are small, there are relatively few items, and weapons have limited uses, encouraging careful resource management. While Fire Emblem's itemization works at forcing the player to budget their resources with consideration for the future, it's a more difficult system to balance - a player that very carefully conserves resources for later battles can overwhelm otherwise challenging encounters by throwing large amounts of resources at it, and I'm more interested in creating tactical encounters with more a more immediate focus.

Divinity Original Sin 2's equipment system has more variety, and while the player can stockpile resources (such as potions, spell scrolls, and so on) they're still limited by the number of ability points their character has each turn, and combat usually boils down to effective use of skills, often enabled by bonus stats on armor. Getting gear in Divinity is pretty neat, in that giving a character a point or two in a new spell school might push characters into trying something new. However, as the game goes on, this becomes less relevant, and numbers become somewhat meaninglessly larger.

Dofus' gear has (somewhat) randomized stats, which can be "maged" to be better, favor specific stats, and add "exotic" stats (like an extra ability or movement point). Additionally, gear is (almost) all crafted, and all gear can be traded or sold on the market. Some quested gear is account-bound for several months after being obtained to maintain exclusiveness for a window after new content comes out), in the context of an MMO, this is quite neat - gear isn't disposable, because you can sell it to other players after out-leveling it, or finding another set of gear that works better for them.

![](../../../content/wandertale/sabres.png)
*Just an average piece of level 200 equipment.* 🙃 (*via [dofus.com](https://www.dofus.com/en/mmorpg/encyclopedia/weapons/17586-atcham-sabres)*)

I think this is actually quite cool in the context of an MMO. It's difficult for individual players to obtain all the resources they need to craft gear as well has leveling the many, many crafting professions to craft and mage gear. Dofus' maximum level is also very high, and high level characters have a huge variety of stats on their gear, and finding item combinations that work well together is an enormously complex undertaking. Some sites, such as [Dofus Fashionista](https://dofusfashionista.com/) have automated set builders that try to build item combinations focusing on user-selected stats in particular.

This sort of equipment system only works for a massively multiplayer game with tons of content like Dofus, and is outside of the scope of what I want to build. Instead, I want to reward individual characters unique items that allow them to build toward a niche.

## World Scaling

While Divinity Original Sin 2 allows all players to level up together, the world also levels up with them as they go. This is pretty goofy, as there's no in-world justification for a Fort Joy Knight (at the beginning of the game) having 300 health, and an Arx City Knight having 20,000 HP toward the end of the game. The health scaling ends up feeling pretty meaningless, and the main thing that changes as the player levels is their access to more spells. There's a lot of room for improvement in terms of mechanics-as-world-building or story here. 

Fire Emblem has a similar problem, compounded by a silly experience system that primarily rewards those that get final blows.

This is actually something Dofus does pretty well. When new content gets added to the game, they often have content for multiple level ranges, and tailor storylines to the level of experience that the player's level reflects. Now, this can be somewhat contrived, because random enemies wandering around in randomly generated packs on the world isn't particularly compelling from a "why are these beefy boys even here" kind of perspective, but it is an MMO, and MMOs love having guys wandering around in fields. 🤷‍♀️ 

However, Dofus' "main story" quests can be quite neat. They actively have the player revisit lower level areas, talk with old NPCs they've had interactions with before and know things about (who may have changed in the meantime), and send the player on new adventures on what they thought was well-trodden ground, revealing new lore. This is a great way of building on already existing setting, and telling new stories! Roleplaying games love to send you to new places to go into adventures into the unknown, but cities really have endless potential for stories, and it's neat to see this done in a tactics game. These sorts of quests also reinforce the experience points your character earns as actual, diegetic experience that your character has as an adventurer.

However, I'm not building a game that relies on monthly subscriptions to monetize itself, so I don't have to force players to grind repetitively to level up. I'm much more inclined to have player characters grow through story quests, though I'm also considering quest systems that allows for repetition, escalation, and a degree of randomness to challenge players, couched as ongoing exploration/defense/etc efforts to give players a way to explore the game systems outside of specific story encounters.

## Progression Systems

Dofus also has a number of mechanics that are endemic to MMOs, and it's power curve (and generally, the time it takes to level up) is certainly among them. While leveling up and becoming stronger (and smashing content that used to be challenging) is fun, the path to level 200(❗) is long. It's neat that there's *so much* to look forward to, from getting new gear, new spells/spell upgrades, . This is especially true when grouping up with higher level players, seeing them use new abilities in ways you can't yet.

Dofus gives all players in a fight exp relative to their level, the enemies' levels, and the cumulative levels of enemies and allies, which allows players of disparate levels to group up. However, because higher level characters get much more experience per fight (and the power curve isn't linear), mooching ends up being very lucrative for lower level characters. To make matters worse, the existence of the Wisdom stat (which primarily increases the experience a character gains), many low level players simply put all their characteristic points into Wisdom and beg higher level players to carry them so they can level up.

This is really bad! The developers know it's bad! They've been working on discouraging various farming methods for boosting characters, encouraging low level characters to fight appropriate level content, buffing the bonus experience from idols (optional challenge modes you can turn on for your fights, if you have the right items), and reducing the affect of wisdom while using idols. However, because it's an MMO economy, low level players have a hard time affording the equipment that would make them able to take on harder fights using idols, if they can even afford buying the idols from other players, and even with all these buffs, it's still often faster to just get carried. Again, 🩹.

On the other hand, Fire Emblem progression systems are primarily numerical and many Fire Emblem games devolve into farming up one of your tanky characters and letting them solo maps, which is from a tactics perspective, boring. There are a number of interesting niches (multiplied by the weapon triangle) that you can build characters for, and seeing a build take shape can be fun, but the depth of customization is in the army as a whole, rather than individual characters. However, while leveling up characters is fine, it's systems primarily gives experience for leveling to characters that land the final blow on enemies - which can cause problems for healers, who can easily be left behind if great pains aren't taken to weaken enemies for a healer to deal the finishing blow. This is pretty goofy, and the game is worse off for it.

Divinity Original Sin 2's stat systems aren't purely numerical, in that investing in spell schools unlocks more abilities, which allows the player to customize their play in interesting ways. I feel like characterization gets somewhat muddled in this system, as characters end up dipping into multiple spell trees and have a less unique identity for it - particularly if they end up overlapping with other characters in the party. However, there's lots of room here for interesting tactical play! Furthermore, characters gain experience together, so support characters aren't punished for not being focused on offense.

## Map Control

Map control as a concept in games like Fire Emblem is somewhat different from Dofus or Divinity Original Sin 2, in that there are very limited options to control the movement and attack ranges of enemy units, instead forcing the player to use terrain and preemptively positioning units to control areas of the map. The player has very few options for modifying the terrain (even temporarily) or forcing enemy units into new positions. As such, playing around terrain (and using terrain modifiers) can be crucial.

Additionally, Fire Emblem doesn't really have a concept of line of sight, but units can block one another from moving. This encourages the players to consider formations (and how to break the enemy's formation by exploiting the AI), and largely works because of the relatively limited movement ranges, and (in particular) the attack ranges of units.

In Divinity Original Sin 2, players typically can't affect the number of actions an enemy can take, but it is possible to snare enemies and make them move more slowly - and because movement requires ability points, this can result in enemies not being able to take actions, or using fewer actions.

The game's systems use environmental effects heavily, and positioning around them can be a primary way to mitigate damage. and while spells do various things, a lot of their mechanics cause environmental effects, and there are a number of established debuff types (bleeding, burning, poisoned, etc).

These environmental effects and canonized buffs/debuffs have the advantage of making combat more "readable", and pretty easy to scan the board for what's going on. This is great, especially in a turn based game, where players might look away from the board while other players take their turn.

![](../../../content/wandertale/dos2.jpg)
*Divinity: Original Sin 2's environmental effects can rapidly spiral out of control. (via [steampowered.com](https://store.steampowered.com/app/435150/Divinity_Original_Sin_2__Definitive_Edition/))*

In addition, characters can block movement, and many environmental effects have a large area of effect component. While some abilities have a projectile component (which means that it's possible to bodyblock some attacks), the system generally de-ephasizes very technical line of sight considerations because of splash damage, small tiles (they do exist, even if they try to hide them!) and fairly forgiving movement. However, it can be fairly finicky when it comes to positioning characters for backstabs and attacks of opportunity. Other tactics games (like Wakfu) also use positional spell effects and ask the player to care about the direction enemies are facing. I find that this can often end up making an already-technical system even more-so, so I'm currently torn on whether to include positionals or not. 

In contrast, Dofus uses a very technical implementation of line of sight, line of sight is generally required, the movement system is unforgiving of errors, turns are timed (forcing players to make decisions quickly with limited information), making misplays much more common than in Fire Emblem and Divinity.

Dofus also has MANY unique spell effects that might do something unexpected. To add to this, debuffs and buffs aren't indicated on player sprites or board state unless the player specifically clicks on their portrait in the timeline, which they'd have to do for each enemy on the board to get the complete board state. To make things even more opaque, ground effects don't indicate what they do, how long they'll persist, and so on. This makes it really, really hard to figure out the game, and forces the player to learn through trial and error.

Now, I actually think the opaqueness of mechanics can sometimes be good, because experimenting and figuring out what works (and doing mechanics wrong and trying to recover) can be dramatic and fun, but it isn't like Dofus has hidden tooltips until you learn what a mechanic does. It's just opaque forever, and you have to remember tons of details yourself (and relearn them if you come back to content later). It might be neat to have tooltips unveiled as the player finds out (the hard way 😈) what effects do.

## "The Spotlight"

One thing that character focused tactics games can do really well is to give the spotlight to individual characters. It can quickly become less cool and good when there's imbalance, as one character can get the spotlight to the exclusion of other characters - this can often happen when games don't manage to perfectly balance damage output, but it's also not uncommon to see MMO players decrying classes or specializations as garbage when they perform only a few percentage points behind their peers in raiding logs.

This occurs for a number of reasons, but particularly in raids, damage output is the primary means by which much of the group contributes to the win condition. This is also true to a lesser degree in smaller group content, but class diversity and composition can matter much more on a smaller scale, which also allows individual plays to contribute more to a win condition (or avoiding a loss condition).

One way to prevent this from happening is to give characters niches that don't closely overlap, or let the player build parties with characters that compliment each other.

Giving the player alternative win conditions like "reach the exit without being caught" or "protect the MacGuffin" can help de-emphasize damage as the ultimate tool for achieving win conditions, and emphasize the importance of other niches.

## Things characters focus on:

Different types of tactics games tend to separate the roles of various characters in different ways. Fire Emblem's niches often boil down to how and when they attack, and clever use of "player phase" units, and "enemy phase" units can allow players to use enemy AI against itself. However, this fundamentally doesn't work for traditional player versus player combat, as there's no way to force enemies to kill themselves on your enemy phase units, and battles could reach stalemates quickly with neither player willing to commit to a trade due to the relative symmetry of movement, attack ranges, and so on.

That said, without going into a lot of detail, they have cavalry, foot soldiers, armored units, and flying units. Because of the role terrain plays in Fire Emblem games, many of these work differently on different terrain, as well as having different attack ranges. Units can have physical melee weapons, magical melee weapons, physical ranged weapons, or magical ranged weapons, and units have different armor types for each type of damage. There are lots of possible combinations that can make characters a better choice than others in a given situation, especially when considering the weapon triangle. 

Divinity Original Sin 2 has a variety of roles:

* Fighter
* Inquisitor
* Knight
* Metamorph
* Ranger
* Rogue
* Shadowblade
* Wayfarer
* Witch
* Wizard

These roles are somewhat ambiguous, and it's not particularly clear what each role does from the name. Many of these are multi-school "roles" - for example, the Witch specializes in Necromancer and Scoundrel at level 1, while the Wayfarer specializes in Geomancer and Huntsman at level 1. Furthermore, the game doesn't say very much about what each "role" is "supposed" to do, and leaves things open-ended for the player to decide. Some schools combo better with others in practice, because spells do either magical or physical damage, and before many debuffs will take effect, the target has to lose it's magical or physical armor.

This has a number of nice properties - it makes it more difficult to chain crowd controls on characters, helping prevent characters from getting killed on the first round, and generally forces the player to strategize around which targets to disable, how to deal with a beefy enemy determined to disrupt your team, and so on. Different values of physical and magical armor can also make various enemies weaker to different players on the team, in that a mage character could have an easier time getting through a heavily physically armored target's magical defenses to disable or kill them, whereas a physical character might prioritize an enemy mage, with weak physical armor.

Dofus splits roles up differently, giving characters various "ratings" in a number of categories for how well they contribute to a specific role:

* Damage
* Summoning
* Buffing
* Debuffing
* Positioning
* Healing
* Protecting
* Tanking

Generally, a well rounded team will have a number of these categories represented in order to deal with the numerous types of mechanics found in a game of it's scale. However, I think this is an interesting way to break down roles, because there are *so many* different things to focus on, and any one character can only hope to do a good job in a handful of them.

Using one of the "meta" teams as an example, as according to the official character roles:

* Cra: damage, buffing, debuffing
* Eniripsa: healing, buffing, debuffing
* Enutrof: debuffing, summoning, buffing
* Pandawa: positioning, damage, tanking

The only category not represented here is "protecting", which is only represented by two of the eighteen classes in the game. This team generally plays at long range, debuffing enemies so they can't reach the team, and buffing damage dealers to take down enemies. However, other teams with other classes (even if there's some overlap in classes with the above team) play wildly differently. This is partially due to the number of spells characters have, the variety in stats the characters have, and so on, and is somewhat necessary in a game that expects all classes to be able to complete various solo encounters for quests.

That said, some quests still heavily favor certain characters and play styles, which can make for a frustrating experience for classes that don't have specific mechanics. It also expects all characters to be able to put out a certain amount of damage, and generally gates experience points (and progression) behind, ultimately, doing damage. 

There's an enormous discussion of how this ends up causing class numbers to be skewed, since players are inclined to pick classes that level quickly, and players that don't might end up literally paying other players to help them level. I don't plan on having traditional experience points, and I think there's a lot of cool tactical things that I can do if I de-emphasize damage dealing as the ultimate means of progression.

With that in mind, I do think the paradigm that Dofus uses to classify characters is quite neat, and they do a great job of making a variety of mechanics useful and desirable. The sheer size and complexity of the Dofus systems (and the 16 years of development into them since Dofus' release) is infeasible for my game, however, and somewhat simpler systems are needed.

## What does all this mean for Wandertale?

So, this has been quite the tour of various mechanics and systems, and while I've tried to give some commentary on the way, I wanted to boil down some of my thoughts in closing.

My game will have a fairly simple stat system. I'm currently thinking along the lines of:

* magical resistance
* physical resistance
* magical damage
* physical damage
* critical chance
* critical damage(?)
* grapple
* evasion
* movement points
* ability points
* initiative

Resistances will likely be flat damage reduction against a type of damage. Magical and physical damage are flat damage increases, combated by resistances. I also intend to have critical chance (which is further augmented by critical damage) as a way of encouraging randomness and making combat less predictable.

Grapple and evasion are competing flat stats. Grapple will cause movement away from melee to cost an enemy more resources, and evasion will cancel out grapple. This will allow evasive melee characters to do their jobs in melee, while hampering the movements of other, less evasive characters, and allowing protectors to hamper the movements of enemies.

Movement points and ability points will increase (somewhat) as characters develop, as a way of increasing the complexity of player's decision-making as they become more familiar with the characters they're playing.

Initiative will allow players to customize their strategies based turn orders, and provide variety in strategic options available.

I'm planning on having a number of characters that focus on different types of play so players can customize a team for various strategies, and characters will each have their own stories with solo and group encounters designed to put their skills to the test - as well as character-specific rewards and growth for overcoming them.

## A final note

There are a few topics I've been writing my own documentation and notes about that I may expand on for another post to follow this up - story, themes, worldbuilding, game loop structure, scope, art, music, and so on. I have a server that I use for development discussion and posting cat pictures, so if you're interested in joining the discussion, feel free to join us on Discord: [https://discord.gg/vkdKtCX](https://discord.gg/vkdKtCX).

![](../../../content/wandertale/sorc.png)
