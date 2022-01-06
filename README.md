# ZeroNet
Neural Network AI Implementation for SWBF (2004)

ZeroNet is the official project under development by the SWBFSpy and SWBFModders community to create neural network artifical intelligence API for ZeroFront (the greatest PC expansion mod ever made for Star Wars Battlefront 2004), and will be implemented into ZF either before or (likely) after the release of ZeroFront v1.0. Future ZeroFront builds may eventually also include assembly code reversal of the ZeroEngine source and other features such as expanded Battlefront II source and VR support. Reinforcement learning servers will be hosted on SWBFSpy where the player emulation AI can train against players, bots, and other nets. Various ZeroNet NNUE files can be weighted and fine tuned with customizable CFG scripts as they are trained to eventually reach levels of skill and tactics beyond those of even the greatest players. This adds unlimited replay value to the game and will help our servers stay even more populated. New tournaments will feature mixed teams of ZeroNet bots vs players and stock AI. ZeroNet will be open source just like SWBFSpy, ZeroFront and ZeroBuilder. More news TBA

For more information, see this
https://swbfmodders.com/index.php?board=40.0

CFG Template Ideas
-
This is an example of some ideas for the CFG template script to be used by ZeroNet AIs. All settings are 0 by default for simplicity. The NNUEs are programmed to induce various handicaps or strategic adjustments based on the following settings. Each new generation of trained NNUE should (on average) allow for greater potential of skill improvement and strategic realism. ZeroNet AI will explore each map and build an understanding of its layout, observing how other AI and players interact, along with battle variables such as vehicles/units/weapons, and store this in its NNUE memory as tactical knowledge, which it improves at over time just as a player would. The CFG may be changeable mid-game or it might require the NNUE bot to leave and rejoin the server, this is not yet certain. Additional ideas listed @ https://swbfmodders.com/index.php?topic=388.0

FACTION = 0-2
- 0 is set to randomize choice
- 1 sets it to ALL/REP
- 2 sets it to IMP/CIS
- (note that this is overriden by the server if auto assign is enabled)

UNITS = 0-11
- 0 has the NNUE choose what it thinks is the best unit to use based on how a pro player would strategically analyze the battle environment, which might change frequently
- 1 has it play as only infantry units
- 2 vanguard, 3 pilot, 4 sniper, 5 special
- 6-11 will be ignored and default to 0 unless the mission LUA defines 6+ units as selectable for that faction
- 12 and above is ignored and defaults to 0

STYLE = 0-3
- 0 is balanced, the AI adjusts dynamically in the battle for any style
- 1 is aggressive, the AI prefers riskier attacks, charging command posts and being on the frontlines of battle
- 2 is defensive, the AI prefers defending important locations, healing troops, and flanking manuevers
- 3 is observational, the AI avoids combat and will camp inside a glitch or safe area to spectate, useful for AI that can be set to auto-record and spectate in freecam

DIFFICULTY = 0-10
- 0 is set to strongest overall strategic capabilities of the NNUE 
- 1-10 are increasingly weaker, with 1 being second strongest, and 10 being the weakest, about 10% maximum skill reduction per level
- (note that the ELO of each new NNUE build will be ranked on SWBFSpy ELO Leaderboards, and can be compared to player ELO ratings) http://elo.swbfspy.org/

AIM_REALISM = 0-1
- 0 is set to strongest aim possible, basically like a perfect aimbot accuracy, maximized headshots
- 1 toggles on a handicap which adds realistic player aim discrepancies, weakening the overall accuracy of attacks by varying percentages, this should be used when difficulty is set to anything above 0 or the AI will have poorer tactics but perfect aim

ZOMBIE_REALISM = 0-2
- 0 is for disabled
- 1 is for Normal Zombie, which makes the AI patrol regions of the map as zombies, and can use sound or vision to detect enemies which it then targets, they also never flinch from grenades or other weapons, and responds to map boundaries and objects differently than the stock AI
- 2 is for Feral Zombie, which is just like 1, but zombies can always sense enemy units location from anywhere on the map and hunt them down, and are more aggressive overall, unlimited radar

BOT_EMULATION = 0-1
- 0 is set to disabled, it will explore and travel the map as a player would, ignoring ZeroEditor boundaries and pathing routes which are used for stock battlefront AI
- 1 is set to emulate the behavior and pathing of stock SWBF AI bots, which are really stupid, used for testing purposes

IGNORE_VEHICLES = 0-1
- 0 has the AI use vehicles when strategically advantageous, even if it means camping 
- 1 the AI will not enter vehicles, but still target enemy vehicles

IGNORE_TURRETS = 0-1
- 0 has the AI use turrets when strategically advantageous, even if it means camping 
- 1 the AI will not enter turrets, but still target enemy turrets

IGNORE_JUMPS = 0-2
- 0 the AI will jump and bunny hop to travel faster or achieve map shortcuts like most high level players
- 1 the AI will not perform regular jumps, only jet jumps if it has JetJump in the ODF as in the case of dark troopers, and it won't use grenade boosts when it does
- 2 the AI will perform regular jumps but not sophisticated grenade + jet combo boost jumps, used for testing purposes

IGNORE_CROUCH = 0-2
- 0 the AI will intelligently crouch and, while rare, sometimes prone when it thinks there is a tactical advantage
- 1 the AI will never crouch or prone
- 2 the AI will crouch but never prone

IGNORE_COMBO_ATTACKS = 0-1
- 0 the AI uses combo attacks in a triggerbot style, aka fast swapping between syngergistic weapons such as blaster cannon and pistol, rifle and pistol, or wrist blaster and tri shot
- 1 the AI does not prefer super fast combo attacks, and is more reluctant to switch weapons like the stock AI, this may be better for some units such as sniper

IGNORE_RESPAWN_PROTECTION = 0-1
- 0 the AI will intelligently suicide and respawn at critical command points which are under attack when needed, as most often players will, if there is radar enabled
- 1 the AI will not respawn to defend command points, useful for certain tournament settings with radar disabled

DROIDEKA_MODE = 0-2
- 0 is for droidekas to use shield and rolling mode, along with bouncing height boost trick on slanted edges of maps
- 1 the droidekas won't use shields
- 2 the droidekas won't use rolling mode or bouncing boosts

ASSIST_PLAYERS = 0-1
- 0 the ZeroNet AI does not prioritize assisting players and prefers to operate on its own, considering other players to be just like the ZeroNet AI and stock AI
- 1 the ZeroNet AI prioritizes assisting human players and defending them as bodyguards, even at the cost of overall team advantages, with assistance of ZeroNet AI as secondary prioritization over stock AI, useful for certain situations

AI_COMMANDER = 0-3
- 0 is balanced, the ZeroNet AI  only sends commands to the Battlefront AI when it thinks there is a tactical advantage to doing so, such as telling the AI to hold position on some areas
- 1 has the ZeroNet AI command stock SWBF bots to Move Out or Exit Vehicles
- 2 has the ZeroNet AI command stock SWBF bots to Follow Me or Enter Vehicles
- 3 has the ZeroNet AI command stock SWBF bots to Hold Position
- (once the ZeroEngine is hacked there will be an option to unlock unlimited AI following, which is currently limited to just 2, while move out and hold position are unlimited by default)

Other settings that could be added once BF2 code is implemented include IGNORE_SPRINT, IGNORE_FLAG, etc.
