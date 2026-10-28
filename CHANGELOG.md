# Changelog

## 0.1.1

- The ENHANCE tab now lists a "Set" row for every discovered gem, even when you don't carry that
  gem or enough Ancient Coins yet. Like vanilla recipes, rows you can't afford are greyed out and
  the missing cost blinks red. Before, items only showed up while you carried the gem.
- Gear whose recipe your character never learned (traded, found or dropped gear) is now listed too.
- 0.1.0 and 0.1.1 can't play together: update the server and every player.

## 0.1.0

- First release. An ENHANCE tab at a fully upgraded black forge (level 6) or Galdr table (level 5)
  sets Deep North gemstones (Grimvarn, Solryth, Veydris, Draumyx) into Ashlands-tier and better
  armor and weapons, and polishes them with Ancient Coins up to grade III.
- Each gem gives a small benefit and a smaller drawback; armor benefits are capped for the whole
  kit. Gems are saved on the individual item and survive upgrades, death and logouts.
- Enhancing is discovered ("Discovered: Enhancing") at such a station once you know the Ancient
  Coin and a gem.
- Gem effects are fully configurable lists; CarryWeight, RunStamina and Damage are available but
  off by default.
- A server with the mod refuses players without it (or with another version) with the game's
  "Incompatible version" error (`RequireOnClients`).
- Everything is configurable; the server's settings apply to all players.
