![](https://img.shields.io/github/downloads/No3371/SPT_ThatsLit/total) ![](https://img.shields.io/github/downloads/No3371/SPT_ThatsLit/latest/total)

# That's Lit - Logical AI Vision

This is a mod for Single Player Tarkov for tuning bot vision logics to make bots mimic realistic human perception capabilities.

[\[Showcase\]](https://streamable.com/rbvo7q) [\[Showcase\]](https://streamable.com/n889vs) [\[Showcase\]](https://streamable.com/1z135g)
[\[Showcase\]](https://streamable.com/eco0yr) [\[Showcase\]](https://streamable.com/unrili)
[\[Showcase\]](https://imgur.com/a/ORTSSWO) [\[Showcase\]](https://imgur.com/a/ia7FYdS) [\[Showcase\]](https://streamable.com/lhdbbs)
[\[Showcase\]](https://streamable.com/1as7m4) [\[Showcase\]](https://streamable.com/00td1z) [\[Showcase\]](https://streamable.com/810ese)

Let’s define ***unfair***: When your bullet hits or whizzes past a bot, it knows your exact position. They can see you perfectly fine in the dark as long as you are within its vision range. They don’t care how dense are the foliage and grasses around you.

Yet we struggle to locate bots with our human eyes.

This is why That’s Lit exists: **in SPT, we no longer play against human players, bots need to make human-like mistakes just like how real players do.**

That’s Lit let AIs overlook you when you are blended in the shadow, or spots you faster when you are lit up by lighting. Imaging ratting in Night Factory?

It also allows you to traverse the fields through grasses and bushes without always getting engaged from afar. Imagine to prone in the Woods?

Additionally, randomness is applied to AIs vision check, so they are no longer machines which 100% spots you in their configured distance or 0% out of range.

The goal is to give bots vision restrictions and imperfect reaction similar to human, so you can sneak around in night time without always getting spotted by bots from a distance, dash into trees and plants to interrupt bots’ aim, or maybe get surprised by the fact that, bot no longer shoot at the very first moment you pop out of cover.

By default 2 meters are displayed at the top left corner for you to learn the mechanic, and they can be disabled.

The first is brightness meter showing how dark (left) and how bright (right) you are, the second meter (factor) tells you how much AIs are actually affected by your brightness. Factor value is just squared Score. In other words, the second meter is the final effectiveness of the first meter.

The meters only give you a rough idea about the impact of your brightness, ingame the bots are affected individually according to their positions, directions or other conditions.

To directly feel the effect of That’s Lit, just go to Night Factory and look at the meters as you move, or sit in the darkness and wait for innocent AIs coming to you.

The mod is developed with SAIN and Realism, it works fine without them, but the default experience could feel easier if your setup is different.

**It’s very important to have a loadout mod that properly gives bots NVG or Flashlights in night raids to keep the game balanced.**

The positive and negative impact from the mod is fully configurable, so when you feel the game becomes too easy maybe adjust those to your liking, but I suggest try harder SAIN presets or hardcore mods like Realism, before tuning the mod, because the mod is more like a post-processor which is based on vanilla and other mods.

**Some setting adjustment is required for SAIN, Check “Recommended Mods” below.**

Keep reading to get the most out of the mod.

# Explanation

In short: The mod delays bots reaction, in a way that how a human would see you but fail to recognize you.

Most parts of the mod are about modifying one value called *SeenCoef*, which determines how long the an AI needs to have you in their vision to recognize you, in other word, time to visual confirmation.

The *SeenCoef* is modified by some calculation withall these factored in\*:\*

- The mod factors in all sorts of data to adjust AIs, minor mechanics are not listed. Direction, distance, height, indoor/outdoor, weather, season, devices/goggles/scopes, movement… A lot of stuff could have a impact on the gameplay.
- Time and cloudiness determine the ambience lighting in raid. Lighting matters a lot! Try to sneak in shadows and avoid lights.
    - This also means weathers now affects gameplay! Sunny days are much brighter than cloudy days and makes you more visible, thus you’d prefer cloudy days for low profile raids.
    - In the brightest hours of clear nights you could be as visible as day time raids of normal weather.
    - When outside, you will want to stick to shadows, especially in the brightest hours (clear days&nights). It helps.
        - Top half of some Ground Zero skyscrapers do not have proper colliders thus Ambience Shadow check is not working stably for these. This only mess with you if you are not covered by nothing else or the bottom of the skyscrapers. (Maybe Streets have the same issue too, not tested)
    - Some balance changes are applied in winter raids, and overall makes you slightly easier to be spotted. Try to avoid empty snowy ground.
    - ![iyCbmNa.png](https://imgur.com/iyCbmNa.png)
    - ![yXk3Wpo.png](https://imgur.com/yXk3Wpo.png)
- Getting lit up by any lights including flashlights, gun flashes or thunder, will hinder your stealth, especially when the lighting is unstable.
- Active flashlight or laser is very likely to expose you (including IR if the AI is using NVGs)
    - A lot of the features are much less effective with flashlights on, some even get impacted by lasers. Try to toggle them wisely!
- AIs using NVGs are quite unaffected by darkness, especially at close distance. If the player is in really dark areas, their NVGs will be somewhat less effective.
- AIs using Thermal goggles are pretty much unaffected, and can actually spot the player faster.
    - Taking stims like SJ9 actually nullify this and grants you stealth against them.
- AIs using Night Vision scopes and Thermal scopes can ignore your stealth, given you are in front of them, especially when the bot is not moving.
- Forest blending: Staying close to foliage grants a small chance for AI vision check to fail from afar.
    - Requires the nearest foliage to be between the AI and you (effectiveness scale down with the relative angle up to 90 degree).
        - It’s configurable up to 5 candidates instead of just the nearest foliage, which can helps you against multiple bots from different directions
    - By **afar** I mean this has no effect for AIs within 10m, and the effectiveness gradually scales up by distance up to 110m. (It’s a low curve, much weaker at close range, only 25% effective at 50m but reach 100% at 110m)
- AIs have a chance to overlook players up high, especially when the player is in low poses.
- There’s a small chance for bots outside to fail spotting players inside. Does not work when the bot is looking straight toward the player, or at closer distances.
    - “Inside” is defined by BSG. Proper buildings with walls and ceilings usually count… of course, there are weird exceptions.
- There’s a possibility AIs will continuously overlook when you hide nicely inside foliage, even at close distance, just like how we can rat in bushes on live.
    - You may still become exposed anytime, especially when they get close or turn to you. Don’t feel too safe in there.
    - Different foliage have different characteristics, different poses may be required for a foliage to take effect, and the effectiveness may vary against AIs at different heights.
    - This even applies to short trees or tall bushes, while they are usually useless against AIs at close or maybe mid range, It’s not a bad idea to stick to foliage as much as possible, It does has an effect against AIs far away.
    - [Preview](https://streamable.com/01r3pb)
- Grasses are now proper visual covers, surrounding grasses contributes to AIs overlooking you.
    - ![vIcDGZB.png](https://imgur.com/vIcDGZB.png)
    - You can actually get close to enemies without being noticed in day time by crawling through dense grasses.
    - The only thing to note is only grasses in the direction to the AI within ~3.5m participate in the calculation. Otherwise, common sense applies.
    - Warning: there are some rare [exceptions](https://imgur.com/a/W6Z2HaF) (ex: the plant in the center), these are probably decorations manually placed by BSG. They are not rendered by the terrain detail system so are not detectable.
- Distance matters. Most of the features are more effective to AIs far away from you. Once you are spotted, you lost the distance bonus and will need to get out of the sight for a short while to regain the bonus.
    - For AIs at 110m+ away you need to stay out of sight for about 1.5 seconds; the required time is much longer for closer AIs. If the AI is actively targeting you, it’d take longer.
    - Physical obstacles are always better than grasses and foliage. If you are caught off guard and really have no choice but some nice dense grasses around you, you can try to prone and hope it works.
- Player and bot movement are applied as final modifiers.
    - Sprinting bots are less likely to spot players not in front.

    - The player will be spotted faster by movement speed, unless it’s really dark.

    - Bots staying still will spot the player faster.

- Like SAIN’s Personality system, That’s Lit has a **caution** mechanic that diversify bots’ immunity against some mechanics.
    - 1 or 2 bots out of 10 have better resistance, they are defined to be cautions and are less likely to overlook the player in stealth.
    - 3 to 5 bots out of 10 have weaker resistance, they are defined to be careless and are more likely to overlook the player in stealth.
- To simulate bots remembering your presence, many mechanics are greatly nerfed if the bot has seen you recently, or has seen you at the same spot. Keep moving!
- By default, all the features don’t affect bosses (optional). Bush Ratting does not work for bosses even if the option is turned on, for balance reason.

**TL;DR**: Out of fights, utilize the environment and choose path wisely. When engaged, be strategic and flexible, try to stay out of sight as much as possible… When you pop up, you kill.

The mod also include some small patches to make bots more reasonable:

- Bots’ aim will be delayed if they encounter you when sprinting, because in vanilla they sometimes head,eye us at the first moment they end inertia slide, while we players can’t even ADS when sprinting.

- In situations a bot is told to “see” you but it’s actually not facing your way, by a chance That’s Lit will cancel the visibility. Instead, the bot will be told it’s spotted from the player’s direction, so it may finds covers first instead of instant returning fire,

    - If that doesn’t happen, there’s still a fallback chance for it to happen if it’s a surprise attack (the bot haven’t seen you for quite a while and you are far away)
    - Basically, this helps bots to behave like human being clueless when surprise attacked.
- Compensation to bots vision distance to at least a reasonable amount:

    - When the ambience is very bright
    - When the ambience is dark but the player is lit up
    - When the player is in the dark but the bot is using NVG
    - When the bot is using Thermal goggles
    - These compensations are especially important with SAIN, because it scales down bots’ vision distance simply by time and weather. Vision distance decides whether vision check happens, this means, no matter how much the player is lit up, bots remains unable to see the player if the distance exceeds the SAIN modified value. The patch balances out SAIN’s vision distance scaling.
- When the Brightness module is disabled, an optional fluctuation to visual confirmation is applied (optional, enabled by default). For the most part there will not be noticeable difference, only that you may get lucky or unlucky.

- Bot aim point is forced to randomly jump when blind firing. This is because I got shot in the head from the sawmill (Woods)… and I was at RUAF Gate.


That’s Lit is unlikely to conflict with other mods. The mod only modifies specific values out of the whole AI system, it does not add or change AI behavior pattern. An analogy would be… Given a formula **A+B**, That’s Lit changes the value of B instead of makes it **A+B+C** or **B+C**.

## Notes

- AIs don’t always rely on their vision to detect you, especially with SAIN installed, they may act in response to noises you make.

- An unintended interesting side-effect of the mod: Because vision checks are performed per body part, with the randomness from That’s Lit, somehow *head,eyes* is reduced as a result (my personal observation).

- It’s well known that That’s Lit takes away some fps especially on weaker CPUs. I’ve seen all sorts of feedbacks, your mileage may vary. Check “Performance” below for more info.

    - If you set your games to have a lot of bots, performance issue is unavoidable. Check “Recommended Mods” for mods to control bot spawning.
- Night Factory is a very special experience (With brightness module on). It’s a dark hunting ground… only shadow walkers survive.

    - You don’t need NVGs to run Night Factory.

## Installation

Decompress the zip file into SPT folder. Bandizip or 7zip is recommended.

## Configuration

…is provided through regular F12 menu. If That’s Lit is not listed there then it’s not in correct folder.

## Maps

All maps are supported, but Brightness module is disabled on Day Factory and The Lab because it’s bright and visible everywhere in these maps and it’d be a waste of fps.

## Compatibility

### Custom lights, lasers, Night Vision/Thermal Scopes, Goggles

…can be supported through thatslitcompat.json files. It’s simple and intuitive to add compatibility, for reference, check out the default and blank thatslitcompat.json files. Any thatslitcompat.json anywhere in plugins will be loaded, feel free to create your own and distribute them!

If the gear is not defined in any thatslitcompat.json, you don’t get debuff when you leave custom lights/lasers on, and bots don’t get buffed by custom scopes and goggles.

So yes, you won’t lose anything with unsupported custom items, it just opens up opportunities to cheese which I am personally not a fan of.

### Mods substantially changing game world and visual

Needless to say, mods or reshade setups that make the scenes look much brighter, remove darkness or drastically change the presented visual, will make the experience inconsistent.

For example, if you play with a mod that make the game looks (visually) bright everywhere, you may feel bots are unreasonably weak when your character is in a “dark” area. Basically anything that only change the visual instead of the actual game world will have similar issues.

On the other hand, for example, the GrassCutter mod just turn off the whole terrain detail system thus all the grass data are not provided anymore, so it’s fine.

## Recommended Mods

### [SAIN](https://hub.sp-tarkov.com/files/file/1062-sain-2-0-solarint-s-ai-modifications-full-ai-combat-system-replacement)
- **Try harder presets** (I’d say just crank up at least 1 tier of SAIN preset). Bots reaction time can be much worse when under the effect of That’s Lit.
- I Like Pain is a nice choice. And I actually recommend Death Wish if you want **a true versus human experience**. Every encounter is a showdown… And you gain upper hand by perform correct movement and concealment.
- **Basically, SAIN difficulty decides bots’ best performance they clearly see you. That’s Lit decides how bad they become when you utilize the mechanics.**
- Recommended preset: [PMC Terminators](https://hub.sp-tarkov.com/files/file/1624-pmc-terminators-a-custom-sain-preset/?highlight=pmc%20ter)
- Latest tweaking recommendation (Tested with 3.9 I Like Pain without Realism):
    - Optional: Adjust night vision modifier in General - Look - Time Settings when you feel bots are blind in nights. Try increase 0.1~0.2 at a time.
        - *[![KxPdS1A.jpeg](https://i.imgur.com/KxPdS1A.jpeg)](https://i.imgur.com/KxPdS1A.jpeg)*
    - Tweak Not Looking At Bot Settings: SAIN now nerfs bots when you are not facing them, this is a very comfortable feature but could make the game too easy especially when stacked with That’s Lit, **disable or adjust** these to your liking:
        - ![CnscljG.jpeg](https://i.imgur.com/CnscljG.jpeg)
    - Tweak Vision Speed settings:
        - **For movement: You need to choose one**. Stacking both will results in overly buff/debuff against sprinting players.
            - That’s Lit’s implementation is balanced around That’s Lit enabled gameplay. It factors in vision angle, speed, poses and brightness.
            - SAIN’s implementation scales the vision time by your speed.
            - That being said, in actual gameplay it’s not necessarily better than SAIN’s implementation, it’s your call.
            - **You can disable it or adjust it if you turn on Advanved settings.** By default bots takes 50% time to see you when you sprint fast.
                - ![RjKIxTu.jpeg](https://i.imgur.com/RjKIxTu.jpeg)
        - For **Elevation** modifiers, **it’s fine to leave both enabled, but you can tweak** if it’s too much for you. There’s some difference between how That’s Lit and SAIN use elevation to affect bot vision, and That’s Lit does not makes higher bots see faster, so it’s not a full overlap. From my playtest, it surprisingly works alright with both at default values.
            - ![ED6FFhz.jpeg](https://i.imgur.com/ED6FFhz.jpeg)
        - Tweak Peripheral Vision:
            - In That’s Lit, the angle difference between *the direction from bot to you* and *the bot’s vision direction* is used only to scale the impact separately in each mechanics. In SAIN, it’s used to simply scale the vision time regardless of situations.
            - It seems alright in my playtests, but if you feel like bots are not aware enough in their surrounding, **you can disable it or play with the advanvaed settings**.
                - START\_ANGLE: the default 30 means when it’s effective when the bot is looking away, starting from 30 degree
                - REDUCTION\_COEF: the default 2 means at the bot type’s max visible angle (usually 75~90 degrees), the bot takes 2x time to spot you.
            - ![zhgljRQ.jpeg](https://i.imgur.com/zhgljRQ.jpeg)
        - **For Pose modifiers,** you can disable or tweak **if lowering pose is too effective.**
            - In That’s Lit, your pose is used to scale the impact **separately in each mechanics**. In SAIN, it’s used to simply scale the vision time regardless of situations.
            - ![Z3KkF0r.jpeg](https://i.imgur.com/Z3KkF0r.jpeg)
    - Headshot Protection: Headshot Protection is much less needed with That’s Lit. Due to a side effect of the introduced randomness, headshots happens much rarely with That’s Lit.
    - That’s Lit contains an optional patch that when a bot is close to the player, it gets a chance to ignore SAIN’s No Bush ESP, so bots won’t be blind at meters away just because it or you are touching a bush. DO NOT COMPLAIN ABOUT BUSH TO Solarint WHEN YOU HAVE THIS ENABLED.
### [SWAG+DONUTS](https://hub.sp-tarkov.com/files/file/878-swag-donuts-dynamic-spawn-waves-and-custom-spawn-points/)
- Configure DONUTS to load the **starting-pmcs-only** or similar presets, so you get a live-like experience and better performance
- DONUTS now spawns only “normal” tier AI by default, so all same bots have average abilities. Find “PMC Difficulty” and “Scav Difficulty” and tweak them to your liking. I use **asonline** because I like randomness and variation (which is why That’s Lit exist), **asonline** randomly configure bots ability from all options, this plus SAIN personality system gives a mixed bag of AIs.
- The mod has a nature of keeping bots near you, as it despawns bots far away to prevent CPU being wasted on bots you’ll never meet.
    - It’s not intended, but with newer SAIN, which make bots smarter and hear all sorts of sounds you make, there are inevitable side effects:
        - You can’t really clear out a zone, bots will keep coming, this is extremely noticeable in ULTRA.
        - It makes you feel like EVERY scav has a death wish and are willing to get you instead of running for their lives. This does not make sense to me.
    - From my personal experience with full Realism, this easily gets out of hands.
    - After enabling Bot Hard Cap, the game is fixed for me. It should be noted that I’m running default Realism (all features on). The author of DONUTS plays Realism with increased health, which is also a way to balance it out.
        - **If you are going to turn on Bot Hard Cap, remember to also check out Hot Spot Spawn Boost & Hot Spot Ignore Hard Cap**.
    - **Needless to say with the option enabled raids are quieter than with out, especially on bigger maps. Because bots are naturally distributed across the whole map instead of kept together. Depends on bots movement, both chill and hot raids are still possible.**
### [Questing Bots](https://hub.sp-tarkov.com/files/file/1534-questing-bots/)
- It makes bots to actually go to places where real players would go for questing, giving your questing trips a twist.
- It makes the whole raid much more busy and unpredictable. Clearing out an area no longer means the area is safe now, you never know when a bot would come or pass by.
- It’s known to be a heavy mod just like That’s Lit, try enable the AI limiter option to reduce the performance overhead.
### [Looting Bots](https://hub.sp-tarkov.com/files/file/1096-looting-bots/)
- Realistic bot looting behavior; let your prey brings loot to you.
- I recommend turning on Sight Checks except for containers, so they don’t magically get attracted to loots & corpses.
### [Realism](https://hub.sp-tarkov.com/files/file/606-spt-realism-mod/)
- Your mileage may vary but I play with all Realism features enabled and enjoy the extra challenges with balanced bots reaction from That’s Lit
- Besides, It contains a Loadout system that gives bots proper loadout based on map/time. (Do not use with other Loadout mods)
- Warning: Realism is a challenging experience! Do not just install Realism without reading through the description first.Many people instantly regret and had to go through restoring from profile backups.
### [Softcore](https://hub.sp-tarkov.com/files/file/998-softcore-proper-singleplayer-experience-for-spt/#overview)
- The economy overhaul transform the game from simple “No I can always buy this with cash” to “Hmm this could be useful”.
- This combined with Realism’s **hardcore flea market** feature creates a flavorful experience and works very well with That’s Lit.
    - NVGs are rare asset but low level bots don’t have access to NVGs too, so overall a very balanced experience.
    - Make sure to follow Realism’s compatibility instruction.
- Any Loadout Mod that gives bots NVG & Flashlights in night raids.
    - Do not use any along side Realism’s loadout changes.
- [Raid Overhaul](https://hub.sp-tarkov.com/files/file/1673-raid-overhaul/)
- The random blackout event spices things up with That’s Lit.
- It’s a feature rich mods but very configurable.
- The “Raid Start Events” option randomly open/close doors and lights on raid start, which is very interesting for night raids.
- (Not a mod) [Lossless Scaling](https://store.steampowered.com/app/993090/Lossless_Scaling/): a software providing Frame Generation technology.
- An alternative way to deal with low fps from CPU bottleneck. Requires idle GPU power.
    - On the other hand, Upscaling helps with GPU bottleneck, which is rarely the case for SPT.
- The Frame Generation feature tries to generate fake predicted frames between real frames on the fly with your GPU.
- This means: up to 3x fps, with input latency and ghosting of hard-to-predict stuff on screen like UIs. Take it or leave it.
- ![VffAWom.png](https://i.imgur.com/VffAWom.png)

## Performance

- TL;DR: Only Brightness module cost considerable FPS.
- Brightness module use an additional camera to observe the player, this cause some unavoidable fps loss, the number depends on the CPU, some lose 5, some lose 20… Some even said it improves the performance retardadothinking
    - If you don’t care about night raids, you can disable Brightness module, all other features still work.
    - On my end (Ryzen 5800x), turning it off yields about 1.9ms frame time in Woods, which can be translated to roughly 70->60 fps.
- Starting every raid, the mod reads and caches terrain details (most are grasses), this process is sliced into pieces and only takes up a tiny bit of time per frame. Once the caching is done, it won’t cost any frame time.
- The mod periodically checks grasses/foliage around the player, but these works are nothing to any modern CPU.
- Quite a lot of math is performed to combine all the available data and calculate values to apply per bot, these works are only performed for bots who is in range, and math is nothing to modern CPUs.
- Let’s just say most of performance cost comes from that camera. If you are interested you can turn on Debug Info and Benchmark optinos to take a look, the time spent on That’s Lit’s code path is negliable. Unfortunately the camera is a game engine thing and not measurable by That’s Lit.

## Fun facts

- What we see in game is not what is actually observed by cameras. The presented visual is heavily processed, raw cameras would observe a much darker and paler scene.
- The first person character got no thorax (for real, you are just a running pair of arms and legs), so a light that should have be projected on the thorax can not be observed.
- The above 2 combined, is the reason why the light detection can’t be die accurate. But thanks to the countless hours put in, current system works good enough.
- I knew nothing about how modding works for this game, like even how mod files should be organized and how BepInx works, so I just downloaded Solarint’s SAIN then removed most his stuff and started to work on it. In the begining I also read SAIN’s code to locate AI stuff in EFT codebase, so a lot thanks to Solarint.
