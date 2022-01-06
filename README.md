# ZeroNet
Neural Network AI Implementation for SWBF (2004)

ZeroNet is the official project under development by the SWBFSpy and SWBFModders community to create neural network artifical intelligence API for ZeroFront (the greatest PC expansion mod ever made for Star Wars Battlefront 2004), and will be implemented into ZF either before or (likely) after the release of ZeroFront v1.0. Future ZeroFront builds may eventually also include assembly code reversal of the ZeroEngine source and other features such as expanded Battlefront II source and VR support. Reinforcement learning servers will be hosted on SWBFSpy where the player emulation AI can train against players, bots, and other nets. Various ZeroNet NNUE files can be weighted and fine tuned with customizable CFG scripts as they are trained to eventually reach levels of skill and tactics beyond those of even the greatest players. This adds unlimited replay value to the game and will help our servers stay even more populated. New tournaments will feature mixed teams of ZeroNet bots vs players and stock AI. ZeroNet will be open source just like SWBFSpy, ZeroFront and ZeroBuilder. More news TBA

For more information, see this
https://swbfmodders.com/index.php?board=40.0

CFG Template Ideas
-
This is an example of some ideas for the CFG template script to be used by ZeroNet AIs. All settings are 0 by default for simplicity. The NNUEs are programmed to induce various handicaps or strategic adjustments based on the following settings. Each new generation of trained NNUE should (on average) allow for greater potential of skill improvement and strategic realism. The CFG may be changeable mid-game or it might require the NNUE bot to leave and rejoin the server, this is not yet certain. Additional ideas listed @ https://swbfmodders.com/index.php?topic=388.0

FACTION = 0-2
- 0 is set to randomize choice
- 1 sets it to ALL/REP
- 2 sets it to IMP/CIS

UNITS = 0-11
- 0 has the NNUE choose what it thinks is the best unit to use based on how a pro player would strategically analyze the battle environment
- 1 has it play as only infantry units
- 2 vanguard, 3 pilot, 4 sniper, 5 special
- 6-11 will be ignored and default to 0 unless the mission LUA defines 6+ units as selectable for that faction
- 12 and above is ignored and defaults to 0

STYLE = 0-2
- 0 is balanced, the AI adjusts dynamically in the battle for any style
- 1 is aggressive, the AI prefers riskier attacks and being on the frontlines of battle
- 2 is defensive, the AI prefers defending important locations, healing troops, and flanking manuevers

DIFFICULTY = 0-10
- 0 is set to strongest overall strategic capabilities of the NNUE 
- 1-10 are increasingly weaker, with 1 being second strongest, and 10 being the weakest, about 10% maximum skill reduction per level
- (note that the ELO of each new NNUE build will be ranked on SWBFSpy ELO Leaderboards, and can be compared to player ELO ratings) http://elo.swbfspy.org/

AIM_REALISM = 0-1
- 0 is set to strongest aim possible, basically like a perfect aimbot accuracy, maximized headshots
- 1 toggles on a handicap which adds realistic player aim handicaps, weakening the overall accuracy of attacks by varying percentages, this should be used when difficulty is set to anything above 0 or the AI will have poorer tactics but perfect aim

ZOMBIE_REALISM
- 0 is for disabled
- 1 is for Normal Zombie, which makes the AI patrol regions of the map as zombies, and can use sound or vision to detect enemies which it then targets, they also never flinch from grenades or other weapons, and responds to map boundaries and objects differently than the stock AI
- 2 is for Feral, which is just like 1, but zombies can always sense enemy units location from anywhere on the map and hunt them down, and are more aggressive overall, unlimited radar

BOT_EMULATION = 0-1
- 0 is set to disabled
- 1 is set to emulate the behavior of stock SWBF AI bots, which are really stupid, used for testing purposes

IGNORE_VEHICLES = 0-1
- 0 has the AI use vehicles when strategically advantageous, even if it means camping 
- 1 the AI will not enter vehicles, but still target enemy vehicles

IGNORE_TURRETS = 0-1
- 0 has the AI use turrets when strategically advantageous, even if it means camping 
- 1 the AI will not enter turrents, but still target enemy turrets

IGNORE_JUMPS = 0-1
- 0 the AI will jump and bunny hop to travel faster or achieve map shortcuts like most high level players
- 1 the AI will not perform regular jumps, only jet jumps if it has JetJump in the ODF as in the case of dark troopers 
- 2 the AI will perform regular jumps but not sophisticated grenade + jet combo boost jumps, used for testing purposes

IGNORE_COMBO_ATTACKS = 0-1
- 0 the AI uses combo attacks in a triggerbot style, aka fast swapping between syngergistic weapons such as blaster cannon and pistol, rifle and pistol, or wrist blaster and tri shot
- 1 the AI does not prefer super fast combo attacks, and is more reluctant to switch weapons like the stock AI, this may be better for some units such as sniper

AI_COMMANDER = 0
- 0 is balanced, the ZeroNet AI  only sends commands to the Battlefront AI when it thinks there is a tactical advantage to doing so, such as telling the AI to hold position on some areas
- 1 has the ZeroNet AI command stock SWBF bots to Move Out or Exit Vehicles
- 2 has the ZeroNet AI command stock SWBF bots to Follow Me or Enter Vehicles
- 3 has the ZeroNet AI command stock SWBF bots to Hold Position
- (once the ZeroEngine is hacked there will be an option to unlock unlimited AI following, which is currently limited to just 2, while move out and hold position are unlimited by default)
