# Overview
This addon dynamically changes PlayerNames inside user defined macros to name they would want to change it manually before entering arenas. To make this work I enhanced blizzard macro language and it has a little different syntax as default macros which will be explained later in documentation.

Addon **will be loaded** whenever number of players in party is **2** or **3**. In every other scenario addon will do **nothing**.
Addon is developed for **PvP only** and therefore PvE requests to enhance addon will be most likely ignored.

This addon is **developed for DPS classes** because Healers are using @party1/2 targetting macros and this would be worthless for them.

**SoloQueue is fully supported** and therefore in case protection paladins have been present in soloQ they will be considered as healers in DynamicMacros addon. Other tanks than protection paladins will be considered as damagers in DynamicMacros addon.

Addon **will not work** in 3v3 arenas where team compositions are: (Healer + prot paladin + anything)

*Just stop playing tank in PvP nobody wants **you**.*
___
### DynamicMacros usage:

**To open addon settings type in chat /dm**
Settings windows will be opened which is pretty simple to use. Here you will specify macro names which you want to behave as DynamicMacros. Bottom window will show you list of macro names which you already defined to behave as DynamicMacros. Once your macro name appears in this window we can proceed to macro syntax and create one.
**Warning: Do not create macro names with same names. Then it will do nothing.**

#### DynamicMacro Syntax

**Facts:** 
@target, @focus, mouseover, @partypet1, @partypet2, @arena1, @arena2, @arena3, @yourcharactername wont be touched and will behave as blizzard intended to.

I ll show here **4 examples** how this logic work what should help you create your own macros. 
In those examples you will see words **"healer"** and **"damager"**. They are just for clear presentation how it works. On creation of macro you can write there anything (table/mouse,dog,cat simply whatever comes to your mind.) This string will be anyway replaced with playername once you are in party with 2 or 3 members. This is just for initial setup.

Keep in mind those are just 4 examples from basic to advanced macros. First occurence with @anything(excluding facts above) will be considered as line for healer and then second occurence with @anything(excluding facts above) will be considered as line for dps. 

**Modifiers(nomod,shift..) which I use in examples are totally optional**. They work same way they do in default macros by Blizzard.

1. **cast on friendly healer without modifier and on friendly dps in team with shift modifier**

    *#showtooltip Regrowth*   
    */cast [nomod,@healer] Regrowth*   
    */cast [mod:shift,@damager] Regrowth*
   
    Lets say you are in soloQ. Second line would automatically replace "healer" with name of you healer in team. Same logic will be applied for dps and word "damager" at third line would be replaced with name of damager in team.
    That way you didnt have to touch your macros and they would still work.

2. **cast spell on friendly DPS in any situation 2v2/3v3/soloQ**
   
   *#showtooltip Void Shift*\
   */cast [nomod,@healer]*   
   */cast [@damager] Void Shift*
   
    Even tho nobody wants to cast anything on "healer" (maybe he is not even present in your team) he has to be written inside macro without specifying spell which should cast to make it work. 

3. **cast spell on friendly healer in any situation 2v2/3v3/soloQ**
   
    *#showtooltip Void Shift*   
    */cast [@healer] Void Shift*
   
    To cast on healer it is sufficient to specify just one line with healer as you can see above unlike for dps.

4. **nomodifier cast on me (krionel is my character name), shift modifier cast on healer and if he does not exists cast on target, ctrl modifier cast on damager and if he does not exists cast on focus**
   
    *#showtooltip*   
    */cast [nomod,@Krionel]Regrowth*   
    */cast [mod:shift,@healer,exists][mod:shift,@target]Regrowth*   
    */cast [mod:ctrl,@damager,exists][mod:ctrl,@focus]Regrowth*
   
___
### Useful information
Macros wont be updating while you have default blizzard macro window GUI opened. So simply once you create macro close this window to make it work. Then you can reopen it once you are in 2 or 3 membered party to see changes.

Keep in mind addon updates your macros 3 seconds after your party group is updated. This means somebody leaves/joins/wentOffline/wentOnline/loadIntoArena and at the same time number of player in group is still 2 or 3.

This is the logic how it works. This way your macros dynamically assign name of player you would overwrite manually and you never have to do that again.

Ctrl modifier for **friendly players is bugged** since launch of Dragonflight. It is actually **not an issue of addon but game itself**. Ctrl does not work in normal macros too. Workaround for that is to bind ctrl+letter directly into action bars and create macro without specified ctrl modifier in it.

### More random examples (some people still do not understand it)

1. **cast on friendly healer without any modifier at all**

    *#showtooltip Blessing of Protection*   
    */cast [@healer] Blessing of Protection*   

2. **cast spell on friendly DPS (NOT healer at all) without any modifer**
   
   *#showtooltip Leap of Faith*\
   */cast [@healer]*   
   */cast [@damager] Leap of Faith*

---
If you are still having an issue with creating your own macros. Contact me via discord: krionel@7188


**Credit for idea goes to Black**
