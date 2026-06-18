# Player Events

Common patterns for handling players joining, leaving, and interacting.

---

## Player Joined — Print Name

Fires when a player joins and prints their name to the output.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.271 ChildBlocks Print1 ElseChildBlock nil Inputs Outputs Player player  Block Type GetObjectProperty Name Get Name1 VisualPosition -0.36B,0 ChildBlocks Print1 ElseChildBlock nil Inputs Object 1 player Property 0 Name Outputs Value player_name  Block Type Print Name Print1 VisualPosition -0.36B,0.271 ChildBlocks ElseChildBlock nil Inputs Text 1 player_name Outputs
```

**What it does:**
1. `PlayerAdded` fires and outputs the `player` object
2. `GetObjectProperty` reads the `Name` property from `player`
3. `Print` outputs the player's name

---

## Player Joined — Create Leaderstat

Creates a "Coins" leaderstat for every player that joins.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.271 ChildBlocks Create Leaderstat1 ElseChildBlock nil Inputs Outputs Player player  Block Type CreateLeaderstat Name Create Leaderstat1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs StatName 0 Coins InitialValue 0 0 Outputs
```

**What it does:**
- When a player joins, creates a leaderstat named "Coins" with an initial value of 0

---

## Player Left — Print Goodbye

Fires when a player leaves and prints a farewell message.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerRemoving Name Player Removing1 VisualPosition -0.36B,-0.271 ChildBlocks Print1 ElseChildBlock nil Inputs Outputs Player player  Block Type Print Name Print1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 0 A player left the game Outputs
```

---

## Kick a Player on Touch

When a part is touched by a player's character, kick them.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PartTouched Name Part Touched1 VisualPosition -0.36B,-0.5DC ChildBlocks Get Player1 ElseChildBlock nil Inputs Part 2 game.Workspace.KickPart Outputs otherPart other_part  Block Type GetPlayerFromCharacter Name Get Player1 VisualPosition -0.36B,-0.2EE ChildBlocks Kick1 ElseChildBlock nil Inputs Character 1 other_part Outputs Player player  Block Type KickPlayer Name Kick1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Player 1 player Outputs
```

**What it does:**
1. `PartTouched` fires when anything touches `KickPart` in Workspace
2. `GetPlayerFromCharacter` gets the `Player` from the touching part (if it belongs to a character)
3. `KickPlayer` removes that player from the game

---

## Add Coins on Touch

Give 10 coins to a player when they touch a reward part.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PartTouched Name Part Touched1 VisualPosition -0.36B,-0.5DC ChildBlocks Get Player1 ElseChildBlock nil Inputs Part 2 game.Workspace.CoinPart Outputs otherPart other_part  Block Type GetPlayerFromCharacter Name Get Player1 VisualPosition -0.36B,-0.2EE ChildBlocks Add Coins1 ElseChildBlock nil Inputs Character 1 other_part Outputs Player player  Block Type AddToLeaderstat Name Add Coins1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Player 1 player StatName 0 Coins Amount 0 A Outputs
```

> `A` in hex = 10 coins

---

## Character Spawned

Fires each time a player's character loads (initially or after death).

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.5DC ChildBlocks Character Added1 ElseChildBlock nil Inputs Outputs Player player  Block Type CharacterAdded Name Character Added1 VisualPosition -0.36B,0 ChildBlocks Print1 ElseChildBlock nil Inputs Player 1 player Outputs Character character  Block Type Print Name Print1 VisualPosition -0.36B,0.2EE ChildBlocks ElseChildBlock nil Inputs Text 0 Character spawned! Outputs
```
