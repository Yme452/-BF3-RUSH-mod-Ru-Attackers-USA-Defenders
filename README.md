Russia as Attackers, USA as Defenders in Rush Mode

This mod changes the team roles in Rush Mode so that:

:russia: Russia (RU) becomes the attacking team.
:united_states: USA (US) becomes the defending team.
Installation

Install BotSpawner.lua
Place the BotSpawner.lua file into your FunBot directory:

FunBot\ext\Server

Install the RU Mod
Extract the RU archive into your VU mod directory.

After extracting the files, launch the game normally. No additional configuration should be required.

Files
BotSpawner.lua — Required for changing the Rush team roles.
RU archive — Required mod files.

Enjoy, and I hope this mod is useful for anyone who wants to play Rush with Russia as the attacking team and the USA as the defending team.


Since the botspawner.lua file gets reset after every update to the funbot mod, there might also be changes, so you can modify it yourself as well 
Mainly modifying these

Here is the translation of those modification instructions into clear, professional English:

***

### Modification 1: Swap Weapons (1st Location)
**Search for:** `function BotSpawner:_SelectLoadout(p_Bot)`
Find `local s_Team = "US"` inside the function, and change `% 2 == 0` to `% 2 == 1`:

**Original Code:**
```lua
	local s_Team = "US"

	if p_Bot.m_Player.teamId % 2 == 0 then
		s_Team = "RU"
	end
```

**Change to:**
```lua
	local s_Team = "US"

	-- ✅ [Faction Swap] Original RU (Even) uses US weapons, Original US (Odd) uses RU weapons
	if p_Bot.m_Player.teamId % 2 == 1 then
		s_Team = "RU"
	end
```

---

### Modification 2: Swap Weapons (2nd Location)
**Search for:** `function BotSpawner:_SpawnBot(p_Bot, p_Transform, p_SetKit)`
Again, find `local s_Team = "US"` inside the function, and change `% 2 == 0` to `% 2 == 1`:

**Original Code:**
```lua
	local s_Team = "US"

	if p_Bot.m_Player.teamId % 2 == 0 then
		s_Team = "RU"
	end
```

**Change to:**
```lua
	local s_Team = "US"

	-- ✅ [Faction Swap] Original RU (Even) uses US weapons, Original US (Odd) uses RU weapons
	if p_Bot.m_Player.teamId % 2 == 1 then
		s_Team = "RU"
	end
```

---

### Modification 3: Swap Appearances and Kits
**Search for:** `function BotSpawner:_SetKitAndAppearance(p_Bot, p_Kit, p_Color)`
Find the `if` statement below `-- Get Kit and Appearance.`, and change `s_TeamId % 2 == 1` to `s_TeamId % 2 == 0`:

**Original Code:**
```lua
	-- Get Kit and Appearance.
	if s_TeamId % 2 == 1 then      -- US
```

**Change to:**
```lua
	-- Get Kit and Appearance.
	-- ✅ [Faction Swap] Original RU (Even) uses US appearance, Original US (Odd) uses RU appearance
	if s_TeamId % 2 == 0 then      -- US
```
