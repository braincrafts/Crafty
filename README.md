# Crafty JS [![Travis Build Status](https://travis-ci.org/craftyjs/Crafty.svg?branch=develop)](https://travis-ci.org/craftyjs/Crafty) [![AppVeyor Build Status](https://ci.appveyor.com/api/projects/status/github/craftyjs/Crafty?svg=true&branch=develop)](https://ci.appveyor.com/project/starwed/crafty) [![Sauce Test Status](https://saucelabs.com/buildstatus/mucaho)](https://saucelabs.com/u/mucaho)

Crafty is a JavaScript game library that can help you create games in a structured way…

Key Features:

* Entities & Components - A clean and decoupled way to organize game elements. No inheritance needed!
* Eventbinding - Event system for custom events that can be triggered whenever, whatever and bound just as easily.
* No dom manipulation or custom drawing routines required.

Other Goodies:

* Thriving community - Help is readily available in the forum.
* Community modules - A growing collection of user-generated code you can use.
* Pure JavaScript - No magic. Works in all major browsers and can be combined with your favorite js library.


## Using Crafty

A simple game of pong:
```javascript
Crafty.init(600, 300);
Crafty.background('rgb(127,127,127)');

//Paddles
Crafty.e("Paddle, 2D, DOM, Color, Multiway")
    .color('rgb(255,0,0)')
    .attr({ x: 20, y: 100, w: 10, h: 100 })
    .multiway(200, { W: -90, S: 90 });
Crafty.e("Paddle, 2D, DOM, Color, Multiway")
    .color('rgb(0,255,0)')
    .attr({ x: 580, y: 100, w: 10, h: 100 })
    .multiway(200, { UP_ARROW: -90, DOWN_ARROW: 90 });

//Ball
Crafty.e("2D, DOM, Color, Collision")
    .color('rgb(0,0,255)')
    .attr({ x: 300, y: 150, w: 10, h: 10,
            dX: Crafty.math.randomInt(2, 5),
            dY: Crafty.math.randomInt(2, 5) })
    .bind('UpdateFrame', function () {
        //hit floor or roof
        if (this.y <= 0 || this.y >= 290)
            this.dY *= -1;

        // hit left or right boundary
        if (this.x > 600) {
            this.x = 300;
            Crafty("LeftPoints").each(function () {
                this.text(++this.points + " Points") });
        }
        if (this.x < 10) {
            this.x = 300;
            Crafty("RightPoints").each(function () {
                this.text(++this.points + " Points") });
        }

        this.x += this.dX;
        this.y += this.dY;
    })
    .onHit('Paddle', function () {
        this.dX *= -1;
    });

//Score boards
Crafty.e("LeftPoints, DOM, 2D, Text")
    .attr({ x: 20, y: 20, w: 100, h: 20, points: 0 })
    .text("0 Points");
Crafty.e("RightPoints, DOM, 2D, Text")
    .attr({ x: 515, y: 20, w: 100, h: 20, points: 0 })
    .text("0 Points");
```
_Left paddle is controlled by `W` & `S`, right paddle by `UpArrow` & `DownArrow`._   
[Check it out online and try to modify it yourself here](https://jsfiddle.net/mucaho/yL3v48r6/).

## Developing

If you want to fix a bug, please submit a pull request against the development branch.  Some guides to help you can be found [on the wiki](https://github.com/craftyjs/Crafty/wiki)

If you would like to make larger contributions please catch us in the [forum](https://groups.google.com/forum/?fromgroups#!forum/craftyjs) and we will help you get started. Much appreciated :-)


### Quick build instructions

The easiest way to build crafty is to use [gruntjs](http://gruntjs.com/), which requires [node](nodejs.org/) and [npm](https://npmjs.org/).  If you have grunt, node, and npm already installed, then run `npm install` from Crafty's root directory.  (This will pull down about 30MB of node packages.)  From then on, just run `grunt` to build.

You can also use [yarn](https://yarnpkg.com/) instead of npm.

([Full instructions here](https://github.com/craftyjs/Crafty/wiki/Building).)


## 🌐 Web Resources & Interactive Index
- [GEOMETRY STARS](https://ilearnworldpt.pages.dev/geometry-stars.html)
- [CATEGORY DEEP IMMERSIVE24](https://learnquester.github.io/category-deep-immersive24.html)
- [UNICORN PRINCESS DRESS UP](https://themindzone.pages.dev/unicorn-princess-dress-up.html)
- [SECRETS OF CHARMLAND](https://studyquesthub.web.app/secrets-of-charmland.html)
- [CATEGORY FASHION](https://quizverses.pages.dev/category-fashion.html)
- [TROPICAL MATCH](https://quizverses.github.io/tropical-match.html)
- [SHAPE SHIFTING](https://quizverses.pages.dev/shape-shifting.html)
- [CATEGORY WATER39](https://quizverses.pages.dev/category-water39.html)
- [POWERWASH SIMULATOR 3D WASH](https://quizverses.pages.dev/powerwash-simulator-3d-wash.html)
- [STACKTRIS 2048](https://quizverses.pages.dev/stacktris-2048.html)
- [DARTS JAM](https://thequizzone.pages.dev/darts-jam.html)
- [BOBBLEHEAD BALL](https://iskillquest.pages.dev/bobblehead-ball.html)
- [CATEGORY ART32](https://thequizzone.pages.dev/category-art32.html)
- [CATEGORY CASUAL 9](https://themindplay.pages.dev/category-casual-9.html)
- [HOLE AND FILL COLLECT MASTER](https://studyquesthub.web.app/hole-and-fill-collect-master.html)
- [BUNNY BLOX](https://quizverses-9d2f2.web.app/bunny-blox.html)
- [HAPPY GLASS GAME](https://quizverses.pages.dev/happy-glass-game.html)
- [COSMO VOID](https://quizverses.github.io/cosmo-void.html)
- [WATER SORT](https://quizverses.github.io/water-sort.html)
- [CATEGORY JIGSAW](https://themindzone.pages.dev/category-jigsaw.html)
- [BUTTERFLY TRIPLE](https://themindplay.github.io/butterfly-triple.html)
- [TOILET PIN](https://thequizzone.pages.dev/toilet-pin.html)
- [CATEGORY SIMULATION 4](https://quizverses.github.io/category-simulation-4.html)
- [KINGS AND QUEENS MAHJONG](https://iskillquest.pages.dev/kings-and-queens-mahjong.html)
- [REALDRIVE FEEL THE REAL DRIVE](https://quizverses-9d2f2.web.app/realdrive-feel-the-real-drive.html)
- [ECHOLOCATION SHOOTER](https://iskillquest.pages.dev/echolocation-shooter.html)
- [TILE LIVING](https://themindplay.github.io/tile-living.html)
- [TRANSFORMERS BATTLE FOR THE CITY](https://studyquesthub.web.app/transformers-battle-for-the-city.html)
- [OBBY PARKOUR RACING](https://quizverses-9d2f2.web.app/obby-parkour-racing.html)
- [KICK THE NOOBIK 3D](https://quizverses.pages.dev/kick-the-noobik-3d.html)
- [STICKMAN ARCHER SHOOTING ARROWS AT REDS](https://quizverses.pages.dev/stickman-archer-shooting-arrows-at-reds.html)
- [CAR VS ZOMBIES](https://themindplays.pages.dev/car-vs-zombies.html)
- [SIBERIAN ASSAULT](https://themindplays.pages.dev/siberian-assault.html)
- [PECKSHOT](https://themindplay.pages.dev/peckshot.html)
- [CONSTRUCTION TRUCK BUILDING GAMES FOR KIDS](https://thequizzone.pages.dev/construction-truck-building-games-for-kids.html)
- [DISASSEMBLE THE PICTURE PUZZLE](https://quizverses.github.io/disassemble-the-picture-puzzle.html)
- [SUPERWINGS COLORSWITCH](https://themindplay.pages.dev/superwings-colorswitch.html)
- [ROAD RACE 3D](https://themindplay.pages.dev/road-race-3d.html)
- [FUNNY BALLS 2048](https://quizverses.pages.dev/funny-balls-2048.html)
- [PIMPLE SQUEEZE](https://studyquests.pages.dev/pimple-squeeze.html)
- [CATEGORY MONSTER](https://quizverses.pages.dev/category-monster.html)
- [MAJESTIC DRAGONS MERGE](https://thequizzone.pages.dev/majestic-dragons-merge.html)
- [ACCURATE 2D](https://themindplay.github.io/accurate-2d.html)
- [POPPYTILE](https://quizverses.github.io/poppytile.html)
- [SNAP FIX](https://quizverses-9d2f2.web.app/snap-fix.html)
- [HIDE AND LUIG](https://studyquests.pages.dev/hide-and-luig.html)
- [GOODS TRIPLE MATCH 3D](https://quizverses-9d2f2.web.app/goods-triple-match-3d.html)
- [DONT PANIC DUDE](https://thequizzone.pages.dev/dont-panic-dude.html)
- [ASMR NAIL TREATMENT](https://quizverses.github.io/asmr-nail-treatment.html)
- [SUPERMARKET SORT N MATCH](https://thelearnquesters.pages.dev/supermarket-sort-n-match.html)
- [SUPERPIXELINT](https://thelearnquesters.pages.dev/superpixelint.html)
- [BUILD A QUEEN 2025](https://studyquests.pages.dev/build-a-queen-2025.html)
- [STICKMAN ESCAPE SCHOOL](https://themindplays.pages.dev/stickman-escape-school.html)
- [THE DRAG RACING CHALLENGE](https://themindplay.github.io/the-drag-racing-challenge.html)
- [BARBEE BLACK FRIDAY FASHION](https://studyquests.pages.dev/barbee-black-friday-fashion.html)
- [CATEGORY IDLE445](https://quizverses.pages.dev/category-idle445.html)
- [GEOMETRY PLATFORMER](https://quizverses.pages.dev/geometry-platformer.html)
- [MINI GRAND THEFT CITY](https://studyquesthub.web.app/mini-grand-theft-city.html)
- [CATEGORY BATTLE523](https://quizverses-9d2f2.web.app/category-battle523.html)
- [AIRPORT CONTROLLER](https://studyquesthub.web.app/airport-controller.html)
- [PARK FEVER](https://iskillquest.pages.dev/park-fever.html)
- [SUPER RACING GT DRAG PRO](https://studyquesthub.web.app/super-racing-gt-drag-pro.html)
- [CATEGORY ESCAPE187](https://themindplay.github.io/category-escape187.html)
- [DINOSAUR RAMPAGE](https://thequizzone.pages.dev/dinosaur-rampage.html)
- [AIRPORT MASTER PLANE TYCOON](https://theskillquest.pages.dev/airport-master-plane-tycoon.html)
- [COUNTRYSIDE DRIVING QUEST](https://studyquests.pages.dev/countryside-driving-quest.html)
- [SKIP LOVE](https://quizverses.github.io/skip-love.html)
- [ANIMAL BLOCKS](https://studyquests.pages.dev/animal-blocks.html)
- [CUPID UNCHAINED](https://themindplay.github.io/cupid-unchained.html)
- [CATEGORY ESCAPE 2](https://thequizzone.pages.dev/category-escape-2.html)
- [WORDMIX](https://quizverses.pages.dev/wordmix.html)
- [WHEEL OF BINGO](https://thelearnquesters.pages.dev/wheel-of-bingo.html)
- [HUNTER UNDERWATER SPEARFISHING](https://iskillquest.pages.dev/hunter-underwater-spearfishing.html)
- [ZIG SNAKE](https://studyquesthub.web.app/zig-snake.html)
- [TICTOC URBAN OUTFITS](https://themindplay.pages.dev/tictoc-urban-outfits.html)
- [CATEGORY THIRD PERSON SHOOTER80](https://themindplay.github.io/category-third-person-shooter80.html)
- [CAPYBARA SUIKA](https://studyquests.pages.dev/capybara-suika.html)
- [ARROW ESCAPE PUZZLE](https://thelearnquesters.pages.dev/arrow-escape-puzzle.html)
- [TRAIN DRIFT](https://studyquesthub.web.app/train-drift.html)
- [CATEGORY MISSION207](https://themindplay.github.io/category-mission207.html)
- [MADNESS DRIVER VERTIGO CITY](https://quizverses.github.io/madness-driver-vertigo-city.html)
- [PURSUIT RAMPAGE](https://studyquests.pages.dev/pursuit-rampage.html)
- [TOW N GO](https://quizverses.github.io/tow-n-go.html)
- [BLOCK UP](https://quizverses.github.io/block-up.html)
- [SCREW NUTS BOLTS WOOD SOLVE](https://thelearnquesters.pages.dev/screw-nuts-bolts-wood-solve.html)
- [CATEGORY PUZZLE 2](https://themindzone.pages.dev/category-puzzle-2.html)
- [EMOJI CHALLENGE](https://themindplay.pages.dev/emoji-challenge.html)
- [HUNGRY CORGI CUTE MUSIC GAME](https://quizverses.github.io/hungry-corgi-cute-music-game.html)
- [SIGMA BOY MUSICAL CLICKER](https://thelearnquester.web.app/sigma-boy-musical-clicker.html)
- [NITRO SPEED CAR RACING](https://learnquesters.pages.dev/nitro-speed-car-racing.html)
- [THE PATAGONIANS](https://themindplays.pages.dev/the-patagonians.html)
- [CATEGORY THIRD PERSON SHOOTER80](https://studyquests.pages.dev/category-third-person-shooter80.html)
- [PET SALON SIMULATOR](https://studyplayings.pages.dev/pet-salon-simulator.html)
- [CRAZY 2248 LINK MATCHING PUZZLE GAME](https://themindplaying.web.app/crazy-2248-link-matching-puzzle-game.html)
- [CATEGORY SHOOTER 2](https://quizverses.pages.dev/category-shooter-2.html)
- [SAND SORT COLOR PUZZLE GAME](https://learnquesters.pages.dev/sand-sort-color-puzzle-game.html)
- [CATEGORY PUZZLE](https://themindzone.pages.dev/category-puzzle.html)
- [FLOWER COLLECTION](https://thequizzone.pages.dev/flower-collection.html)
- [SAVE MY PET PARTY](https://quizverses.github.io/save-my-pet-party.html)
- [ESCAPE ROOM MYSTERY KEY](https://studyplayings.pages.dev/escape-room-mystery-key.html)
- [WORDS WITH OWL](https://studyplayings.web.app/words-with-owl.html)
- [INDEX33](https://quizverses.github.io/index33.html)
- [SUPER TANK WRESTLE](https://studyquests.pages.dev/super-tank-wrestle.html)
- [CATEGORY BOARDGAMES](https://quizverses.github.io/category-boardgames.html)
- [GO TO ZERO](https://studyplayings.web.app/go-to-zero.html)
- [CROCODILO TRALALERO RUN](https://themindzone.pages.dev/crocodilo-tralalero-run.html)
- [MINICRAFT CHEF CAKE WARS](https://themindplay.pages.dev/minicraft-chef-cake-wars.html)
- [CATEGORY ART32](https://themindplay.github.io/category-art32.html)
- [CHAOS ROAD COMBAT CAR RACING](https://learnquesters.pages.dev/chaos-road-combat-car-racing.html)
- [PAPAS BURGER COOK](https://studyquesthub.web.app/papas-burger-cook.html)
- [LUNAR PHASE BATTLE](https://theskillquest.pages.dev/lunar-phase-battle.html)
- [PET FALL](https://themindplays.pages.dev/pet-fall.html)
- [RED STICKMAN VS MONSTER SCHOOL](https://quizverses.github.io/red-stickman-vs-monster-school.html)
- [MEMEVOIO](https://studyquests.pages.dev/memevoio.html)
- [CATEGORY STRATEGY](https://themindplaying.web.app/category-strategy.html)
- [PIECE OF CAKE MERGE AND BAKE](https://studyquesthub.web.app/piece-of-cake-merge-and-bake.html)
- [CHICKEN BANANA RUN](https://studyquesthub.web.app/chicken-banana-run.html)
- [FIGHT TO THE END](https://quizverses.github.io/fight-to-the-end.html)
- [COUNT AND BOUNCE](https://themindplay.pages.dev/count-and-bounce.html)
- [ROYAL JIGSAW](https://themindplays.pages.dev/royal-jigsaw.html)
- [IDLE DRIVE MERGE UPGRADE DRIVE](https://themindplay.github.io/idle-drive-merge-upgrade-drive.html)
- [VALLEY OF WOLVES AMBUSH](https://themindplay.github.io/valley-of-wolves-ambush.html)
- [MY ARCADE CENTER](https://studyquesthub.web.app/my-arcade-center.html)
- [BASKETBALL STARS 2026](https://studyplayings.pages.dev/basketball-stars-2026.html)
- [ARROW SORTING](https://themindzone.pages.dev/arrow-sorting.html)
- [MALL ANOMALY](https://studyplayings.web.app/mall-anomaly.html)
- [4 COLORS CARD MANIA](https://thelearnquesters.pages.dev/4-colors-card-mania.html)
- [STICKMAN KOMBAT 2D](https://studyplayings.pages.dev/stickman-kombat-2d.html)
- [FALLING MAN](https://thelearnquesters.pages.dev/falling-man.html)
- [SMART DOTS RELOADED](https://theskillquest.pages.dev/smart-dots-reloaded.html)
