# GT6-Modding-Notes
Some helpful notes for myself and other people looking into modding Gran Turismo 6. This goes beyond Nenkai's Modding Hub and specializes in strictly GT6 files and data.

# Intro
While GT6 uses many of the same types of file types and features and many of the same tables in its databases, the way it uses them can be very different than previous titles. Nenkai's Modding Hub mostly focuses on on GT4 specifications, which GT5, and to a lesser extent, GTPSP shares a lot in common with. GT6 is the weird middle child between GT4 and GTSport. It uses standard SQL database files instead of proprietary ones, plus it uses a knockoff of JavaScript for all its scripting, as opposed to whatever the previous titles used. GT Sport uses very similar formats to GT6, however I've not attempted GT Sport modding since I don't own a PS4. GT7 switched to using Swift for all its databases and scripting. These notes won't go over stuff already covered in GT Modding Hub unless there's something to add or it's radically different in GT6. I won't tell you how to install mods and whatnot or how to mod your PS3, that's on you to find and figure out. This is for the people who actually plan to get into the nitty gritty of GT6 modding!

# PDIPFS and GT.VOL
Always make sure you've copied your **PDIPFS** folder from your GT6 install and not from sources online. If your **PDIPFS** source folder isn't around 20GB or so, you'll be missing a lot of files! If your GT6 install is disc based, you'll have **GT.VOL**, the disc file, and **PDIPFS**, the updates plus whatever mods you previously installed and are basing your new mod on. Digital GT6 installs will only have **PDIPFS**.

Either way, you'll want to copy **GT.VOL** and **PDIPFS** off your PS3 and to your PC (just use FTP, PS3 only supports FAT32 and the exFAT and NTFS mods don't really work too well when copying off the PS3). After that, you'll extract both into separate folders via **GTToolsSharp.exe**. You can extract them in whatever folder name you want, but make sure you always keep **GT.VOL** and **PDIPFS** in the **GTToolsSharp** folder. Never touch add or remove anything from the **PDIPFS** folder, as it's what **GTToolsSharp** references in order to pack your mod.

You can and probably should copy files from that folder into your mod if needed. Feel free to copy stuff from **GT.VOL** (if you have it) for stuff not included in **PDIPFS** (just be aware that the files in **PDIPFS** are newer, so if stuff copied from **PDIPFS** asks to overwrite files, let it do so). *Just remember this rule: **PDIPFS** is untouchable, it's like a valued book, you can look and copy from it, but never write to it.* You'll instead be writing your own **PDIPFS** in either its own folder or renamed as **PDIPFSxxx** (xxx being whatever you want to call it).

Your mod's **PDIPFS** will always have at least two folders, but it can have more. There will always be a **9** and **K** folder. The **9** folder is where your mod actually resides, **K** is basically the update header so the game knows what version/mod your mod is based on. Always install **9** first, then **K**. Forgetting **K** can cause the game to crash upon boot. This is what causes most GT6 crashes, but other things can cause that (as I'll eventually get to). In my experience, it's possible for **GTToolsSharp** to spit out more than just **9** and **K** folders for your mod. As far as I'm aware, there's no harm in not installing those files, but there's absolutely zero harm in installing them. If you install them, it's possible that reversing your mod back to the previous install would be trickier. I'd have to ask Nenkai or ddm about that one.

# SpecDB
This is where 90% of GT6 modding takes place. Most of the game references this database for just about everything, though there are a few other databases that'll be mentioned later on. If you haven't already, you'll need to decrypt the **DB0106.db** file in order to view it. GT6 Spec II and all other mods use decrypted databases, but vanilla GT6 encrypted them. Just run **GTToolsSharp** with the appropriate command found at the GT Modding Hub. Honestly SpecDB could be its entire page, and I may actually do that in the future as I finish this page up. In order to read .db files, you'll need a SQL editing tool. I highly recommend DB Browser for SQLite since it works extremely well, is FOSS, and is available on multiple platforms. With your SQL tool of choice open, let's explore the various tables found in **DB0106.db**. If it's not listed below, it's not used in GT6 and can be ignored.

Two very important numbers you'll be referencing a lot are **ID** and **UseCar/CarID**. **ID** is the number for the individual column (ie brake part br_xj13_gts_66_a being **ID** 16375). **CarID** is the number that every part and table will use to reference itself to said car. If you forget or use the wrong number for this, bad things can happen! **LabelID** is a remnant from previous games and you can ignore this value altogether unless otherwise stated.

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
This is where you configure how the car will be shown when using the search menu. Obviously you should try to keep all values consistent with other tables. Every column is featured elsewhere and is far more relevant there, so I'll talk about it there instead.
