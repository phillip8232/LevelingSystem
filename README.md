# How to use a data driven approach to create a leveling system.

###### This is a Test Project I designed to help other people looking for a super fast approach to a leveling system without getting a headache later on adjusting stats.

##### Step 1

First you will need to create a structure I named mine F_LevelData but you can name it just about anything and will still work fine.

![01WhatYouNeed](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/01WhatYouNeed.png)

You'll need to have an idea of what members you need for me I've created **XpToLevel** = The required XP before leveling up
**HP** = Health points Value

**Energy** = Stamina System Or Mana System, up to you.

**Str** = The flat damage to be added on top of base damage.

**Int** = Skill flat Damage system.

**Dex** = Auto attack speed, or something similar.

**Mob** = Mobility added on top of your character default speed of 600.

**CritRate** = Chances to hit a critical ( you might want CritDamage as well depending on what you will be using it for )


![02LevelStruct](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/02LevelStruct.png)

##### Step 2

You'll want to create a spreadsheet using any program then export it as a csv, for me I used Google's spreadsheet, having knowledge with spreadsheets will help create data tables faster.

![03ConstructSpreadSheet](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/03ConstructSpreadSheet.png)

##### Step 3

You'll then want to import the csv you have created into unreal, and select the structure you have created.

![04Import](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/04Import.png)

![05YourStruct](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/05YourStruct.png)

You're pretty much done at this point any steps from here on out will just explain my process of how I use the data I've imported.

##### Step 4

1. ##### Create 3 Variable

   **Level_Stats** which is a struct of F_LevelData
   **CurrentLevel** which is integer, I set the default value to 1
   **CurrentXP** which is a float with a default value of 0.0

2. ##### Construction

   Get Data table Row and set the row name to the Current Level by converting it into a string then converting the string into a name, this approach will  allow other designers to adjust starting level.

   Then Pass the output from Data table row to Level_Stats as you will be using this from now on.

![06Variable&Consturction](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/06Variable%26Consturction.png)

##### Step 5

Create a Level up Function you'll just be incrementing current level and double converting.

![07LevelUpFunction](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/07LevelUpFunction.png)

You'll want to set the stats as you level up. The print Statements are optional for debugging purposes.

![08LevelUpOutput](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/08LevelUpOutput.png)

##### Step 6

Create a gain XP function you'll want an Input mines just called **XP** and it's type is a float, you'll then want to pass this XP to **current XP**, You'll need to grab Level Stats and break it and use **XP to level** to and check if the **Current XP** is Greater Than or equal to **XP To Level** If so you'll want use a while loop and set Current XP to 0 and level up if you want to grab the remainder XP like I did you'll just need to  subtract **Current XP** by **XP to Level** using a clamp float to make the min 0 and max however much you want it to be.

This is done because subtraction will always occur and you wouldn't want the players **Current XP** to drop into the negatives, this also prevents you from having use a branch. 

![09GainEXP](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/09GainEXP.png)

##### Finished

You're done you can test this functionality out by creating a keybind, and using the gain XP function.

![10Test](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/10Test.png)

![11OutputShowcase](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/11OutputShowcase.png)

Also Now your Free to use The data From the data table however you please.

![12FreeToUse](https://github.com/phillip8232/LevelingSystem/blob/main/Photo/12FreeToUse.png)

Thanks for dropping by Stay safe.

Documentation Provided by - [phillip8232](https://github.com/phillip8232)
