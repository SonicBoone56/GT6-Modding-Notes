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
