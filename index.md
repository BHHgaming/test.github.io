# Core Functions

API Documentation for Infinite Yield FE Edition
(Credits to Greenman for writing some of the documentation.)

## getstring
    string getstring(int argumentindex)
This function is used to combine the arguments after a certain index into one string. This is useful when you have a string argument that might include spaces.

Tip: Always make an argument that contains spaces your last argument

Example:

    --Note: This is just a snippet
    ["Function"] = function(args,speaker)
        print(args[1])  
    end
If we do this, every space will indicate a separate argument.

Example:

User Input: print Hello World! The command will only get "Hello" because Infinite Yield sees the space and thinks "World!" is a separate argument.

    --Note: This is just a snippet
    ["Function"] = function(args,speaker)
      print(getstring(1))  
    end
If we do this, we get the full message.

Example: User Input: print Hello World! The command will get "Hello World!" because it takes all the arguments after argument 1 and concatenates it to argument 1.

## getPlayer
    table getPlayer(string playername, Player speaker)
This is used to correct shorthand names to full player names. It can also be used to make names like me, others, all work.

Example:

Target Player: mrcoolkid123 User Input: mrcool IY Correction: mrcoolkid123

The first argument should be args[index]. The index should be the index that contains the player name. For the second argument you can just pass in speaker (it's an argument in the function for the command).

Example:

    --Note: This is just a snippet
    --Command: printname [plr]
    ["Function"] = function(args,speaker)
      local players = getPlayer(args[1], speaker)  
    end
Remember that getPlayer() will return a table so you want to use a for pairs loop to run code for all of the returned players.

Example:

    --Note: This is just a snippet
    --Command: printname [plr]
    ["Function"] = function(args,speaker)
      local players = getPlayer(args[1], speaker) 
      for k,v in pairs(players) do
        local Player = Players[v]
        print(Player.name)
      end 
    end
If you are wondering where the global Players is from, you can find it defined inside IY's source code:

(Line 4): Players = game:GetService("Players")

This is not the best way to write this and is to make it simple for beginners. If you want to do this with less code, you can do it like this:

    --Note: This is just a snippet
    --Command: printname [plr]
    ["Function"] = function(args,speaker) 
      for k,v in pairs(getPlayer(args[1], speaker)) do
        print(Players[v].Name)
      end 
    end
Now you can make your player argument work like it does with normal IY commands!

## notify
    void notify(string title, string message)
The notify function is used to make an Infinite Yield message box appear.

[Example](https://vgy.me/NsSwPu.png)

The first argument is the notification title (in the image it's "Notification Title"). If you don't specify this argument, the default title is "Notification Title".

The second argument is the notification text (in the image it's "Hi").

Let's see this in a plugin:

    --Note: This is just a snippet
    --Command: printusername
    ["Function"] = function(args,speaker) 
      notify("Username",speaker.Name) 
    end
This is a great alternative to using game.StarterGui:SetCore() to make notifications.

## randomString
    string randomString()
Generates a random string with a length of 10-19 characters.

## splitString
    table splitString((string) string, (string) separator/deliminator)
Splits a string by a deliminator. The results are stored in the returned table.

Example Usage:

    --Note: This is just a snippet
    --Command: getRGBcolor
    --User Input: getRGBColor 255,0,100
    ["Function"] = function(args,speaker) 
      local colors = splitString(args[1],",")
      local r = colors[1] --255
      local g = colors[2] --0
      local b = colors[3] --100
    end

## Time
    string Time()
Returns the current time as the following string: Hour:Minute:Second AM/PM

## FindInTable
    boolean FindInTable(table table, (any) value)
Checks if a value exists in a table. Returns true if the value is found and false if the value is not found.

## GetInTable
    any GetInTable((table) table, (any) value)
Returns the index of a value in a table. Returns the index if the value is found and false if the value is not found. Keep in mind that this function only works with sorted tables.

## writefileExploit
    boolean writefileExploit()
Returns true if writefile exists.

## isNumber
    boolean isNumber(any value)
Returns a boolean depending on whether the input is a number.

## tools
    boolean tools(Player player)
Returns true if the player has tools.

## r15
    boolean r15(Player player)
Returns true if the player is r15.

## Match
    boolean Match(string name, string str)
Returns true if name contains str

## respawn
    void respawn(Player plr)
Respawns the player

## refresh
    void refresh(Player plr)
Refreshes the player

## execCmd
    void execCmd(string cmdStr, Player speaker)
Executes the command `cmdstr` from speaker's perspective.

## addbind
    void addbind(string cmd, Key key)
Binds a command to a key.

## addspawn
    void addspawm(string cmd, number sDelay)
Adds a spawn command

## onlyIncludeInTable
    void onlyIncludeInTable(table tab, table matches)
Unknown

## removeTableMatches
    void removeTableMatches(table tab, table matches)
Unknown

## getPlayersByName
    table getPlayersByName(string name)
Returns a table of players all with the same name

## round
    number round(number num, number numDecimalPlaces)
Rounds number num to numDecimalPlaces or 0

## ESP
    void ESP(Player plr)
ESp's a player

## CHMS
    void CHMS(Player plr)
Cham's a player

## unkeybind
    void unkeybind(string cmd, Key key)
Unkeybinds the key from the command

## 
