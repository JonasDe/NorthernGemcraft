# Northern Gemcraft

**Sitting on a pile of Ancient Coins and gemstones you can only sell? Put them to work.**

The Deep North showers you with Ancient Coins and four kinds of gemstone: Grimvarn, Solryth,
Veydris and Draumyx. Vanilla only lets you sell them. Northern Gemcraft lets you set those gems
into your best armor and weapons at a fully upgraded black forge or Galdr table, and polish them
with Ancient Coins. Each gem gives a small benefit and a smaller drawback. No new buildings, no new
items: just a meaningful use for your Deep North loot that keeps the game's balance.

## Requirements

- Valheim 1.0.20 or newer, with BepInExPack for Valheim.
- **Multiplayer:** install on the server **and** on every player (see [Multiplayer](#multiplayer)).
- To use it in game:
  - a **fully upgraded black forge** (level 6, all extensions) or **Galdr table** (level 5, all
    extensions),
  - **Ashlands-tier gear or better** made at that station (Flametal, Ashlands weapons, Ashlands
    mage gear and staffs, and all Deep North gear),
  - Deep North gemstones and Ancient Coins.

## Getting started

1. **Find Ancient Coins and gemstones** in the Deep North.
2. **Discover enhancing:** open the crafting menu of a fully upgraded black forge or Galdr table
   while you carry (or have picked up before) an Ancient Coin and a gemstone. You get a
   "Discovered: Enhancing" message for each gem you know. This happens once per character.
3. **Open the ENHANCE tab** next to CRAFT and UPGRADE at that station. It lists your eligible gear
   made at that station, one row per action:
   - **Set a gem** (gems you have discovered): one gemstone plus Ancient Coins. The item gets the
     gem at grade I. Rows show even before you have the gem or coins; like vanilla recipes, they
     are greyed out and the missing cost blinks red until you can afford them.
   - **Polish**: more of the same gem plus more Ancient Coins, up to grade III. Each grade adds the
     gem's effects again.
   - **Remove**: Ancient Coins. The gem is destroyed (configurable).
4. Select a row, check the cost on the right, and press the button. The station-level icon shows
   the level enhancing needs.

## Gems

Each gem has a benefit and a smaller drawback. Values are per grade; grade III gives three times
as much.

| Gem | On armor | On a weapon (while in hand) |
| --- | --- | --- |
| **Grimvarn** (green) | +1% max health, -1% stamina regen | +10% durability, +1% stamina per attack |
| **Solryth** (orange) | +2% stamina regen, -0.5% max health | -3% stamina per attack, -5% durability |
| **Veydris** (purple) | +2% eitr regen, -1% stamina regen | -3% eitr per cast, -5% durability |
| **Draumyx** (black) | -1% physical damage taken, -0.5% movement speed | 1% life steal, -2% health regen |

- **Armor** (helmet, chest, legs, cape, shield) counts while worn, and all worn pieces add up.
- **Weapons** count while in your hands. Durability changes the item itself.
- **Caps:** a gem's main benefit (listed first) is capped for your whole kit: max health +10%,
  stamina regen +15%, eitr regen +15%, physical damage taken -8%. When a cap cuts a benefit, that
  gem's drawback is cut by the same share.
- **Life steal** heals you for a share of the damage you deal, up to the enemy's remaining health.
  Hitting players or tamed creatures heals nothing.

## Costs

| Step | Gems | Ancient Coins |
| --- | --- | --- |
| Set (grade I) | 1 | 20 |
| Polish to II | +1 of the same gem | 60 |
| Polish to III | +2 of the same gem | 150 |
| Remove | - | 30 |

One piece at grade III takes 4 gems and 230 Ancient Coins.

## What you see in game

- **Item tooltips** show the gem and grade, with its effects: benefits in green, drawbacks in red.
- Tooltips also list **your totals from all gems together**, with each cap and whether it is
  reached.
- Weapons show their enhanced stamina and eitr cost in parentheses next to the normal value, e.g.
  `Use eitr: 20 (17.4)`.
- The movement speed total includes gem effects.

## Good to know

- **Gems belong to the individual item**, not to the item type.
- **Saved with the item:** gems last through logouts, and stay on the item in chests, on the
  ground, and in your tombstone when you die. Equip the item again and its gem works again.
- **Upgrading** an enhanced item keeps its gem.
- Mistlands and earlier gear, and other stations, can't take gems (by default).
- Nothing changes for players who never enhance anything.

## Configuration

The config file is created the first time you start the game with the mod installed:

```
BepInEx/config/com.jonasd.valheim.northerngemcraft.cfg
```

- **Mod manager** (r2modman, Thunderstore Mod Manager, Gale): open your profile's config editor
  and pick `com.jonasd.valheim.northerngemcraft`.
- **By hand:** the `BepInEx` folder is in your Valheim folder, or in your mod manager profile
  folder. Open the file with any text editor.
- **Dedicated server:** edit the same file in the server's `BepInEx/config` folder.

The file is plain text: a `[Section]` heading, then one `Name = value` per line. Lines starting
with `#` are explanations. Restart the game (or server) after editing it.

### Costs (`1 - Costs`)

| Setting | Default | What it does |
| --- | --- | --- |
| `MaxGrade` | 3 | Highest grade (1 = no polishing) |
| `SetCoins`, `PolishToIICoins`, `PolishToIIICoins`, `RemoveCoins` | 20, 60, 150, 30 | Ancient Coins per step |
| `SetGems`, `PolishToIIGems`, `PolishToIIIGems` | 1, 1, 2 | Gems per step |
| `RemoveReturnsGem` | false | true = removing gives one gem back |

### Gem effects (`2 - Gem effects`)

Each gem has a list for armor and one for weapons, as `Effect:value-per-grade`, comma separated.
The first entry is the main benefit. Change the numbers, swap effects between gems, or give a gem
completely different effects.

```ini
GrimvarnOnArmor = MaxHealth:1, StaminaRegen:-1
SolrythOnArmor = StaminaRegen:2, MaxHealth:-0.5
VeydrisOnArmor = EitrRegen:2, StaminaRegen:-1
DraumyxOnArmor = PhysicalDamageTaken:-1, MoveSpeed:-0.5
GrimvarnOnWeapon = Durability:10, AttackStamina:1
SolrythOnWeapon = AttackStamina:-3, Durability:-5
VeydrisOnWeapon = EitrCost:-3, Durability:-5
DraumyxOnWeapon = LifeSteal:1, HealthRegen:-2
ArmorCaps = MaxHealth:10, StaminaRegen:15, EitrRegen:15, PhysicalDamageTaken:8
```

Values are percent with their natural sign: `StaminaRegen:2` is +2%, `AttackStamina:-3` is 3% less
stamina per attack, and `PhysicalDamageTaken:-1` is 1% less damage taken.

| Effect | What it changes | Used by default |
| --- | --- | --- |
| `MaxHealth` | max health | yes |
| `HealthRegen` | health regen | yes |
| `StaminaRegen` | stamina regen | yes |
| `EitrRegen` | eitr regen | yes |
| `PhysicalDamageTaken` | blunt, slash and pierce damage you take | yes |
| `MoveSpeed` | walk and run speed | yes |
| `AttackStamina` | stamina per attack | yes |
| `EitrCost` | eitr per cast | yes |
| `LifeSteal` | heals you for a share of the damage you deal | yes |
| `Durability` | the enhanced item's max durability | yes |
| `CarryWeight` | max carry weight (flat, not %) | no |
| `RunStamina` | stamina used while running | no |
| `Damage` | the enhanced weapon's damage | no |

`ArmorCaps` caps the helpful total of a main benefit from all worn armor (`PhysicalDamageTaken:8`
means at most 8% less). Weapon effects are not capped. Entries the mod can't read are skipped and
named in the BepInEx log.

### General (`3 - General`)

| Setting | Default | What it does |
| --- | --- | --- |
| `Stations` | `$piece_blackforge:max:3, $piece_magetable:max:2` | Where enhancing works, as `station:stationLevel:gearLevel`. The station must be upgraded to at least stationLevel (`max` = fully upgraded in vanilla: black forge 6, Galdr table 5; extensions from other mods don't raise it). Only gear whose recipe needs at least gearLevel there can take a gem. |
| `EnhanceableSlots` | Helmet,Chest,Legs,Cape,Shield,Weapon | Which gear can hold a gem |
| `Enabled` | true | Turns the mod on or off |
| `RequireOnClients` | true | Server only: players without the mod (or with another version) can't join |
| `LogDetails` | false | Writes enhancements to the BepInEx log |

## Multiplayer

- Install on the **server and every player**.
- **Server settings apply to everyone:** the server sends its settings to every player, so all
  players enhance with the same costs and effects. `LogDetails` stays each player's own.
- **No join without the mod:** a server with the mod turns away players who don't have it, or have
  a different version, with the game's normal "Incompatible version" message. Turn this off with
  `RequireOnClients = false` in the server's config.
- **Without the mod on the server:** a player with the mod can still join servers without it. The
  mod then uses that player's own settings.
- **Each player's own game:** enhancing and effects run on each player's own game. Enhanced items
  can be traded and dropped like any other item.

## Compatibility

- Adds no items, pieces or recipes, and doesn't change loot.
- Crafting-from-chests mods (such as AzuCraftyBoxes) also cover enhancing: gems and Ancient Coins
  in nearby chests count, just like for crafting.
- Mods that change spawn tables or add station extensions don't affect it.
- Other mods that change the same stats (regen, carry weight, movement) stack with it.
- Gear sorting and crafting UI mods that replace the crafting panel may hide the ENHANCE tab.
