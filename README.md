# Dicey Dungeons Accessibility

A mod that makes [Dicey Dungeons](https://store.steampowered.com/app/861540/Dicey_Dungeons/)
playable with a screen reader. Menus, the dungeon map and battles are spoken, and the whole
game is played from the keyboard or a controller.

**[Download the latest release](https://github.com/gomods1/dicey/releases/latest)** ·
[Full manual: install, keys, settings](DiceyA11y/README.md)

## The game

Dicey Dungeons is a roguelike deckbuilder by Terry Cavanagh (the maker of VVVVVV and Super
Hexagon), with art by Marlowe Dobbe and music by Chipzel. You are a contestant on a game show
run by Lady Luck, turned into a giant walking dice, and you fight your way down a dungeon one
floor at a time.

Every fight is a small puzzle. Each turn you roll a handful of dice and place them on your
cards: a Sword does damage equal to the dice, a Fireball takes only even numbers and sets the
enemy's dice on fire, a Lockpick splits one dice into two, a Spatula flips a 1 into a 6. Between fights you walk the floor's map, open chests, shop,
upgrade your cards and level up, until you reach the boss at the bottom.

There are six contestants, and each plays differently: the Warrior, the Thief (steals an
enemy card every turn), the Robot (calls for dice against a target number, blackjack style),
the Inventor (turns a card into a gadget after every fight), the Witch (casts spells from a
spellbook) and the Jester (plays from a deck instead of fixed cards). Each has six episodes
that change the rules, and the free Reunion and Halloween updates add more.

## What the mod does

The game has no keyboard controls of its own: it is played with a mouse or a gamepad. The mod
plugs a virtual gamepad into the game and connects your keyboard to it, so every key press
goes through the game's own navigation, and it reads the game's state directly rather than
the screen. What you hear focused is what Enter will act on.

- **Battles**: your cards with their text and the dice they take, what each dice would do on
  the chosen card, damage, healing, status effects, what the enemy plays, whose turn it is.
  Tab moves between the enemy's cards, both sides' status effects and your actions.
- **The map**: a cursor that explores the paths without moving you, jumps between points of
  interest (exits, enemies, chests, shops, the way down), marks a space and walks you to it.
- **Every other screen**: shops, upgrades, trades, the inventory grid, level-ups, the
  contestants' own mechanics, episode and character select, options, challenges, mods.
- **Reading keys**: F1 explains the keys on any screen, F2 to F12 read the last announcement,
  the whole screen, your cards, the enemy's, status effects and recent events. Anything only
  a mouse could reach has a screen cursor.
- **Controllers**: any pad the game accepts works, with the reading keys on Back plus a button.
- **21 languages**: the mod's own words are translated into every language the game ships
  (English and Spanish by hand, the others machine translated); game text follows the game's
  language setting.

It speaks through NVDA, JAWS or a SAPI voice on Windows (via
[Prism](https://github.com/ethindp/prism)), and through the system voice on macOS.

## Install, in short

On Windows: close the game, run `DiceyDungeonsAccessibilityInstaller.exe` from the
[releases page](https://github.com/gomods1/dicey/releases/latest), then press Play in Steam.
The installer works with a screen reader, finds the game through Steam and installs or
removes the mod. It touches only one file of the game (`lime.ndll`, kept as `lime_orig.dll`)
and adds a `DiceyA11y` folder.

The [manual](DiceyA11y/README.md#install) covers the recommended Steam launch options, what
to do after a game update, installing from the zip by hand, and the Mac version.

## Status

Every contestant, every kind of map stop, the bosses, the finale against Lady Luck, the
Bonus Round, the menus and the Reunion and Halloween episodes have been played from the
keyboard with the speech checked. [SCREENS.md](DiceyA11y/SCREENS.md) lists each screen and
what was verified on it. Tested on the Steam version 2.1 on Windows and the GOG version 1.12
on a Mac.

Bug reports are very welcome, especially from blind players. Attach `diceya11y.log` from the
`DiceyA11y` folder (it is overwritten each launch, so copy it before playing again).

## In this repository

| Path | What it is |
|---|---|
| `DiceyA11y/bridge/` | The in-game half: a stand-in `lime.ndll` that loads the game's real one and gives the mod a way in |
| `DiceyA11y/companion/` | The mod itself (C#, plus a Swift helper on macOS): speech, keys, screens |
| `DiceyA11y/installer/` | The installer attached to each release |
| `DiceyA11y/tools/` | Build, packaging and test scripts |
| `DiceyA11y/CLAUDE.md` | How it all works and the facts found about the game; read this before changing code |

Building is described under [For developers](DiceyA11y/README.md#for-developers) in the manual.

## Licence

MIT for the mod's own code ([LICENSE](DiceyA11y/LICENSE)). Dicey Dungeons and its data are
© Terry Cavanagh and are not redistributed here: the bridge contains no game code and forwards
to the copy of the game's files already on your machine. You need your own copy of the game.
