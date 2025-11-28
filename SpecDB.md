# SpecDB
The **DB0106.db** file is where 90% of GT modding takes place, with GT6 being no exception. Most of the game references this database for just about everything, though there are a few other databases that'll be mentioned later on. Because of that, its size and complexity are enough to require its own separate section. It's not the only database file you can or need to edit, but it's easily the main and most important one. The game references this database for just about everything.

# Getting Started

If you haven't already, you'll need to decrypt the **DB0106.db** file in order to view it. GT6 Spec II and all other mods use decrypted databases, but vanilla GT6 encrypted them. Just run **GTToolsSharp** with the appropriate command found at the GT Modding Hub. In order to read .db files, you'll need a SQL editing tool. I highly recommend DB Browser for SQLite since it works extremely well, is FOSS, and is available on multiple platforms. With your SQL tool of choice open, let's explore the various tables found in **DB0106.db**. If it's not listed below, it's not used in GT6 and can be ignored.

Two very important numbers you'll be referencing a lot are **ID** and **UseCar/CarID**. **ID** is the number for the individual column (ie brake part br_xj13_gts_66_a being **ID** 16375). **CarID** is the number that every part and table will use to reference itself to said car. If you forget or use the wrong number for this, bad things can happen! **LabelID** is a remnant from previous games and you can ignore this value altogether unless otherwise stated.

# Tables

## ASCC
Stability control parameters. You probably won't be messing with this.

## AVATAR_MET
Driver suits. I don't believe you can do anything with this.

## AVATAR_SET
Same sort of stuff as the previous table.

## AVATAR_SUIT
Same.

## BIRTHDAY_PRESENT
This configures what cars the game will give you depending on your year of birth set in your driver profile. Sometimes the game completely ignores this and just gives you a car randomly. For example, I've had the Lancia Delta, a car from 1992, given to me, somebody born after that year.

## BRAKE
Configures the brakes the cars use. Every car has to have a default brake. Category 0 is stock brakes, Category 1 is racing brakes. The last four columns are all related to brake strength and brake grip. Obviously racing brakes will have higher values.

## BRAKECONTROLLER
ABS (anti-lock brake) config. Don't mess with this.

## CAR_CUSTOM_INFO
This controls what custimization options are available for a car in GT Auto. I used to have a detailed note of this table before I lost my hard drive. Will come back to this one later.

## CAR_NAME_ALPHABET
A table that actually has no affect on the game at all. It's for the developer/mod creator's benefit. It's where the car label template, it's name and short name, and ID number can be referenced from. You can freely add anything you want here, great for if you have ideas for future cars.

## CAR_NAME_JAPAN
Same as previous, except Japanese.

## CAR_SEARCH
This is what the game references when you search for cars via the search tool. Afaik, nothing bad will happen if there's a mismatch here, but obviously it'd be useless to have data here not be accurate. People who are unfamiliar with the game will most likely use the search tool to find a car they need for a particular event due to the sheer amount of cars available in GT6.

## CAR_TAG
A potential remnant from GT5, however GT6 could be using it as well. In the dealership section of GT6, there are recommended cars based on category such as Rally or SuperGT. However, there are a few missing categories and some unused ones here that seem to imply that it may not be used. More research is needed on this.

## CAR_TAG_RELATION
This is where you add cars to be listed via the categories listed in the dealership section. May or may not reference **CAR_TAG** in GT6 despite its name. More research needed.

## CAR_VIEW
UI info for every car in the game. Doesn't have to be accurate to a car's actual data ironically (aside from the required IDs). In vanilla GT6 and prior games, Polyphony used this file to hide car specs or straight up lie about car specs. A lot of concept cars and even some production cars had their specs hidden from the player for whatever reason. And in terms of lying about specs, the most famous example is JDM cars made before 2004 being limited to 276HP unofficially through the famous "Gentlemen's Agreement" in an effort to most likely not piss off Japanese car companies.

# CATALYST

Sports catalytic converter part table. In GT6 and all other games, there's only the single upgrade, so the table is rather simple. Since it's the first power upgrade table used in GT6, it's a great introduction to the columns you'll come across.

**torquemodifier(1)** increases the upper 33% of a car's torque curve by x %. 100% means no power increase, 101 would mean a 101% of the original engine torque, 99% would be 99% of the original engine torque.

**torquemodifier2** increases the middle 33% of a car's torque curve.

**torquemodifier3** increases the lower 33% of a car's torque curve.

**category** is the type of part the entry is.

**shiftlimit** increases the automatic transmission shift limit by x RPM. 0 means no increase, 100 would mean a 100 RPM increase.

**revlimit** increases the maximum RPM of the engine by x RPM. 0 means no increase, 100 would mean a 100 RPM increase.

**rpmeffect** I believe tells the game to change the listed RPM on the car specs. Not confirmed.

Other power upgrades will have more columns potentially. In vanilla GT6, all upgrades except for turbos and superchargers have a flat torquemodifier, ie all three columns have the same value, meaning the entire torque curve is increased by that amount and is the equivalent of raising the torque curve up. You can, of course, stray from this. In fact, my mod, the GT6 Performance Mod, adds variable RPM upgrades to NA tunes and exhausts in an effort to be more realistic and allow for more than just high speed tunes be created.
