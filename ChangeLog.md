# ChangeLog

Items should be sorted roughly in order of most to least important, with 
model-specific changes at the bottom.  Most items should use one of these 
formats:

  - Breaking change:
  - Added
  - Fixed
  - Removed
  - Changed
  - Documented
  - &brand-model: Hardware-specific change (NNNN, NNNN, ...)

# Next

# 2024-04-01

It has been a long time coming, but today marks a monumental leap forward in
the world of illumination, and I'm proud to announce an upgrade which will
usher in a new era of lighting technology. You spoke, we listened, and now
after a long and grueling development process, it's here!

## 🌟 A Heartfelt Thank You!

Before we dive into the details, I must extend my deepest appreciation to each
and every contributor who poured their passion, creativity, and expertise into
this project. We wouldn't be here today without your unwavering dedication,
and for that, I am eternally grateful.

## 🔦 What is it?

I don't want to over-hype anything, but this may perhaps be the single most
popular feature ever. According to extensive market research and numerous
studies, it is preferred by anywhere from 80% to 95% of all users globally,
and has become an industry standard on nearly all platforms. Again and again,
one feature shines above all others as the most highly requested:

Say hello to Dark Mode, the sleek and sophisticated new Anduril interface that
transforms your flashlight experience into an immersive journey through the
shadows.

## 🌙 Why Dark Mode?

Imagine navigating through the night with the elegance and ease of darkness at
your fingertips. Dark Mode isn't just a trend; it's a lifestyle. Here's why
you'll love it:

  - **Enhanced Comfort**: Say goodbye to harsh glare! Dark Mode offers a
    softer, more comfortable lighting experience, perfect for late-night
    walks, camping trips, or simply getting to the bathroom in the middle of
    the night.

  - **Modern Aesthetics**: Embrace a fresh, modern look that's easy on the
    eyes and effortlessly stylish. Black is the new black, because it never
    goes out of style.

  - **No More Blue Light Interference**: The modern world is full of light
    pollution and other ocular hazards which disrupt the circadian rhythm and
    can even cause severe health problems like chronic fatigue and macular
    degeneration. LEDs are particularly egregious thanks to their high
    intensity blue wavelengths. But with Dark Mode, you can leave all those
    troubles in the past and get a good night's sleep, every night.

  - **Environmental Consciousness**: Embrace sustainability with Dark Mode's
    energy-efficient design. By conserving power, you contribute to a
    brighter, greener future for generations to come.

  - **Unprecedented Lighting Quality**: With a simple firmware update, you can
    turn your ugly old torch beam into an ideal blackbody radiator with
    industry-leading 100 CRI, zero duv for a neutral tint, and a perfectly
    smooth beam with no artifacts. It emits a truly radiant, ultra-warm,
    never-seen-before color temperature of 300 Kelvin, which imbues colors
    with such authentic warmth and richness, it's positively incandescent.

  - **Extended Battery Life**: This innovative feature provides nearly
    unlimited runtime, so never again will you have to fumble around trying to
    change a battery in the dark.

  - **Industry Compatibility**: Seamlessly integrate with the latest industry
    standards, ensuring optimal performance across all devices.  Inspired by
    Android's Material You engine, it uses an intuitive touch interface based
    on advanced thermodynamic transfer technology, to continuously adjust its
    beam and perfectly match each user and each situation. The best part is,
    it's automatic so you don't even have to change any system preferences.

  - **Stealth and Night Vision**: For truly distinguished soldiers of fortune,
    this release comes with a special new feature just for you: Turbo Stealth!
    You thought turbo mode and stealth were mutually incompatible... but you
    were wrong. So wrong. When you point this baby at an attacker and unleash
    a blinding burst of darkness, your target will be so confused and
    disoriented that they won't know what hit them! Freelance mall security
    has never looked so good.

  - **Cutting-Edge AI and LLM Technology**: You've heard the buzzwords, you've
    seen the news that AI is going to change the world, you've tried the
    latest LLMs from OpenAI, Microsoft, and other tech giants. Now you can
    have your own Artificial Illumination solution right there in your pocket
    at all times, with the latest in Low Light Modeling technology. No cloud
    account required!

But wait, there's more! Included is a bonus feature called **Moonlighting
Mode**: When you're not busy pretending to illuminate things, your Anduril
flashlight can now generate passive income with a part-time job as a stylish
doorstop or paperweight, adding a touch of whimsy to any room.

So don't wait one more minute. Dive into an immersive realm where darkness
takes center stage, offering a sense of depth and wonder unlike anything
you've seen before.

To experience Dark Mode for yourself, simply update your firmware to the
latest version. This feature is available today across all platforms, ensuring
a consistent experience for all users, regardless of brand, make, or model. We
encourage you to explore this exciting new feature and share your feedback
with us.

Experience the magic of Dark Mode with Anduril flashlight firmware version
r2024-04-01. Upgrade now and step into a world where darkness becomes your
greatest ally!


# 2023-12-03

This release is somewhat higher risk than usual, because so many large things
changed deep in the code.  I did major restructuring and refactoring across the
entire project.  It should work fine, but be on the lookout for any weird
problems.

General:

- Moved from Bzr + Launchpad to **Git + GitHub**, by popular request.
- **Completely reorganized the project** files.  Really, a *massive* amount of
  restructuring.  The flashlight end-user interface is still the same, but
  expect to have to learn the code layout from scratch.  Read the [README.md]
  for info about getting started with the new project layout.
- Added support for AVR DD MCUs like **avr32dd20**.  This is the recommended
  MCU to use in new flashlights.
- Added ability to use turbo in momentary mode.
- Upgraded **battery voltage resolution** from 0.1V steps to **0.025V** steps.
  Battery check has an extra digit which can be 0, 2, 5, or 7 (for example, for
  3.70V, 3.725V, .3.75V, and 3.775V).
- Made Battery Check more consistent, so it's less likely to give different
  values on the 1st and 2nd readout.
- Re-calibrated timing on each MCU type, so a 1-second beacon flasher should be
  closer to 1 actual second now... mostly.  Timing still varies significantly
  from one light to another.
- Fixed default bike flasher brightness on some builds.  It was sometimes way
  too high.
- Fixed RGB aux turning on during momentary mode sometimes.
- Converted documentation to markdown format, and rewrote a lot of it.
- Fixed some build issues with specific compile-time options.
- Changed the format of **version numbers**.  It now uses the most recent
  release tag instead of the build date, and **may have additional numbers at
  the end** to indicate distance from the last official release, and whether
  the repo was clean or dirty.  Today's release is `MODEL-2023-12-03`.  A
  derivative built 52 commits later in a dirty repo would look like
  `MODEL-2023-12-03-52-1`.

New lights:

- Added &thefreeman-avr32dd20-devkit.  It's only used for development purposes,
  but otherwise it's pretty neat.  It'll be the basis for many new lights in
  the future.  (model 1632dd20)

Hardware-specific changes:

- Improved idle efficiency on attiny1616, which was spending entirely too much
  time doing math it didn't actually need.
- &hank-\*-boost: Fixed flicker while holding button at moon level.  Reduced
  ripple on low modes. (0216, 0253, 0273)
- &lumintop-blf-gt: Added smooth steps.  Removed a couple other things to make
  room.  (0321)
- &lumintop-fw3x: Multiple fixes and upgrades...  (0314, 0315)
  - Fixed thermal regulation.  Also fixed the external temperature sensor.
  - Made moon much lower, and made ramp much smoother, by upgrading to DSM.
  - Fixed the aux RGB pinouts because Lumintop got the wiring backward.
  - Added a second build target for people who fixed the wires manually.
  - Added red/blue police color strobe.
  - Made low modes more efficient with underclocking.  Moon should run at least
    4X as long as it did before.
  - Fixed party strobe being blurry.
  - Added documentation for the FW3X's multiple, uh, quirks.
- &sofirn-lt1s-pro: Disabled manual memory, memory timer, and extended simple
  UI by default.  Simple mode is simpler, and the factory settings should be
  more consistent with other lights now.  (0623)

# 2023-10-31

General:

- Finally finished converting all lights to the multi-channel API.
  (but a few are untested due to hardware being unavailable)
- Enabled smooth steps on almost all supported lights, including old ones.
  (in some cases, on old t85 lights, some other things may have been removed
   to make room)
- Made smooth steps work better, and fixed several bugs.
- Added/fixed RGB aux voltage on dual-fuel AA/li-ion drivers.
- Fixed delay timing on all supported MCUs, so 1 "second" is closer to an
  actual second (like in beacon mode or biking mode).
  (especially attiny1616, which was 17% too slow)
- Raised default thermal limit to 50C on attiny1616-based lights, since
  it doesn't need as big an error margin as older MCUs.
- Fixed missing item in globals menu on some lights.
- Misc internal improvements and per-light tweaks.
- Added a ChangeLog.md, to periodically summarize changes in a format which is
  more readable than the raw commit logs.

New lights:

- &thefreeman-boost21-6a: Added.  (1631)
  (very nice HDR boost driver which fits into a FW3A)
- &thefreeman-boost-fwaa: Added.  (1632)
  (very nice AA/li-ion HDR boost driver which fits into a FWAA)

Hardware-specific changes:

- Upgraded several builds to use delta-sigma modulation (DSM), for
  lower lows and smoother ramping with less flicker or ripple:
  - &blf-lt1  (0621)
  - &blf-lt1-t1616  (0622)
  - &emisar-d4k-3ch  (0151)
    (**dramatically** improves resolution and low modes on its 8-bit channel)
  - &noctigon-dm11-boost  (0273)
  - &noctigon-kr4-boost  (0216)
  - &noctigon-k1-boost  (0253)
  - &noctigon-m44  (0143)

- Upgraded some builds to use dynamic PWM, for lower lows and smoother ramping:
  - &blf-q8-t1616,  &sofirn-sp36-t1616  (0613, 0614)
  - &gchart-fet1-t1616  (1618)
  - &noctigon-k1-sbt90  (0252)

- &wurkkos-ts10, &wurkkos-ts10-rgbaux: Fixed too-high default ceiling.  (0713, 0714)

# 2023-10-01

General:

- Updated a bunch of lights to work with the new multi-channel API.
- Added "smooth steps" a.k.a. "soft start", to make on/off and step changes
  smooth.  (enabled by default, can be turned off in Ramp Extras menu)
- User can save a different channel mode for each strobe-group mode.
- Made strobes/blinkies more responsive in Tactical Mode.
- Fixed bug: Tactical Mode clobbers strobe group memory.
- Fixed some minor post-off voltage display bugs.
- Made RGB button brightness update faster in blinky modes.
- Fixed bug: Wrong channel after colored factory reset.
- &attiny1616, &attiny1634: Partially fixed oscillating aux LED voltage 
  colors while off.  Better than before, but can still happen in some cases.
- &attiny1616: Fixed spurious voltage warnings in sleep mode.  (it could 
  sometimes go from Lockout mode to Off mode by itself)
- Lots of internal refactoring.

New lights:

- &emisar-2ch-fet: Added.  (0136)
- &emisar-d4k-3ch: Added.  (0151)
- &noctigon-m44: Added.  (0143)
- &wurkkos-ts10-rgbaux: Added.  (0713)

Hardware-specific changes:

- &ff-e01, &ff-pl47, &ff-pl47g2: Enabled smooth steps instead of SOS mode.
  (0421, 0422, 0423, 0441)
- &emisar-2ch, &noctigon-m44: Added RGB aux channel modes.  (0135, 0143)
- &emisar-2ch-fet, &noctigon-k9.3: New ramps with better-calibrated shape.
  (0136, 0261)
- &emisar-d4v2-nofet: New ramp table.  (0115)
- &emisar-d4sv2-tintramp: Removed / renamed.  (0135, 0136)
- &noctigon-k9.3: Fixed years-old mess.  Merged builds, converted to
  multi-channel, removed old builds, generally got K9.3 working quite a bit
  better.  (0261, 0262, 0263, 0265, 0266, 0267)
- &noctigon-m44: Lower moon, and greatly reduced flicker.  (0143)
- &sofirn-lt1s-pro: Allow configuring the blink channel.  (0623)
- &wurkkos: Raised default temperature limit to 50 C.  (07xx)
- &wurkkos-ts10: Better / smoother ramp.  (0713, 0714)

# 2023-06-29

- Fixed red aux blink on 1st frame of post-off voltage display
- Removed Harry Potter references because its author (J.K. Rowling) spreads 
  hate
- &noctigon-kr4: Fixed thermal regulation (0211, 0212, 0213, 0214, 0215, 0216)

# 2023-05-30

- Breaking change: Changed version check from YYYYMMDDXXXX to XXXX.YYYY-MM-DD, 
  where the punctuation makes a "buzz" instead of number blinks.
- Fixed issue where some lights always thought they were overheating (when 
  cold, or after a factory reset)
- Fixed aux pre-flash
- Fixed a rare corner case where gradual brightness adjustments stopped at 99% 
  power instead of 100% power while going up from level 149/150 to 150/150 on 
  some lights
- Changed "0" digit readout to use the same timing as other short blinks, to 
  help ensure it works on all lights.
- Minor code changes with no runtime impact
- Documented new version check format
- &wurkkos: Added red+blue police strobe (0715, 0716, 0717)
- &noctigon-kr4: Broke thermal regulation (oops) (0211, 0212, 0213, 0214, 
  0215, 0216)
- &noctigon-kr4: Use 7 aux channel modes instead of 3 (0211, 0212, 0213, 0214, 
  0215, 0216)
- &emisar-d4v2: Changed number blinks from aux to main LEDs by default (0113, 
  0114, 0115, 0123)

# 2023-05-17

- &noctigon-dm11-12v: Renamed to noctigon-dm11-boost (0273)
- &noctigon-dm11-boost: Now supported in multi-channel branch (0273)

# 2023-05-02

- Added ability to set channel mode for number readouts (batt check, temp 
  check, version check). Press 3C in batt check mode to change the blink 
  channel.
- Changed post-off voltage display:
  - Display for 4s by default, not 5s
  - Made timing user-configurable in battcheck 7H menu item 2
    (1 click per second the display should last)
  - Use low brightness when torch was at moon level before
  - Skip the voltage display after UI actions which didn't change the mode 
    (like "Off -> 7C" to change aux LED settings)
- Changed RGB button behavior: While torch is on, use low mode below a 
  configured level for real-time voltage color display, instead of always 
  using high mode
- Fixed bug: Channel change could stick when activating a config menu from 
  battcheck (the blink function changed the channel, then the config menu 
  saved it, then the blink function restored it, then the config menu restored 
  it to the value it saved, which was wrong)
- Documented ramp 6C, ramp 4C, ramp 4H, lockout 3H, battcheck 3C, and post-off 
  voltage display config
- &emisar-d4v2: Added the rest of the aux RGB colors as channel modes, and set 
  aux "white" as the mode it uses to blink out numbers (0113, 0114, 0115, 
  0123)
- &wurkkos-ts10: Converted to multi-channel, and gave it a new ramp with 
  better low modes (0714)
- &wurkkos-ts25: Converted to multi-channel, and gave it a smoother ramp 
  (0715)
- &wurkkos: Added Wurkkos FC13 and TS11 (0716, 0717)

# 2023-04-29

- Changed lockout mode:
  - Fixed manual memory timer and tint
  - Added 3H for next channel (to change channels without unlocking, was 
    possible before but needed to be updated for the new channel system)
  - Made 3H+ use mem level instead of lowest moon (this is needed for
    making the channel discernible, and also helps make aux LED controls
    stand out more)
- &emisar, &noctigon: Added Extended Simple UI to Hank's config, so a few more 
  features are allowed in simple mode
- &emisar-d4v2, &noctigon-kr4: Slightly smaller ROM size
- &emisar-d4sv2: Converted to multi-channel, and updated it to use dynamic PWM 
  for a smoother ramp with lower lows (0133, 0134)
- &noctigon-kr4: Converted to multi-channel (0211, 0212, 0213, 0214)
- &noctigon-kr4: Don't blink at top of regulated power (0211, 0213, 0214)

# 2023-04-28

- Added voltage display (by color) on RGB aux LEDs after turning the main LEDs 
  off
- Changed RGB aux: Always preview in high mode while changing color or pattern
- Changed default RGB aux color in lockout mode: Uses blinking voltage, 
  instead of blinking disco (unless model-specific config defines a different 
  default)
- Changed tactical mode default config: only use 2-color strobe if it's on 
  main LEDs, not aux LEDs
- &emisar-d4v2: Smoother ramp (0113, 0114)
- &emisar-d4v2: Added hidden channel modes for RGB aux LEDs (0113, 0114, 0115)

# 2023-04-27

- Changed channel mode menu to preview channels during configuration
- Changed tactical mode default config: use 2-color police strobe if it 
  exists, instead of single-color strobe
- Fixed unnecessary flickering when changing channel modes from/to the same 
  value
- Fixed sleep voltage measurement on attiny1616
- &noctigon-kr4-tintramp: Converted to multi-channel, renamed to 
  noctigon-kr4-2ch (0215)

# 2023-04-25

- Fixed old old bug(s) with voltage measurement while asleep, while also 
  adding other improvements:
  - Fixed oscillating RGB aux colors while asleep in voltage mode, mostly.  
    Some much smaller oscillations are still possible, but the primary issue 
    has been fixed, I think.
  - Fixed old old bug which could cause spurious low-voltage warnings while 
    asleep (previously required a messy code workaround).
  - Reduced avg standby power by ~15uA.
  - Now measures voltage every 1s instead of 8s while asleep.
  - Changed RGB aux behavior: Puts aux LEDs in high mode for 3 seconds after 
    light goes to sleep (much easier to see the voltage this way)
    (this change was obsoleted soon by a better post-off voltage display)
  - Broke sleep voltage measurement on attiny1616 (oops)
- Changed internal details for how gradual ramping works
- &emisar-d4sv2-tintramp: Converted to multi-channel, renamed to emisar-2ch. 
  (0135)
- &sofirn-lt1s-pro: Updated to use today's new code internals (0623)

# 2023-04-19

- Added stepped tint ramping
- Documented new channel modes system
- &sofirn-lt1s-pro: Added white-only auto-tint mode (0623)

# Older: TODO

- Need to import old commit logs as changelog items


<!-- vim: set textwidth=78 shiftwidth=2 -->

