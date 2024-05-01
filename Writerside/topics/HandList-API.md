# HandList API

## `HandList` Class

This class represents a player's hand in a game of Mahjong.

### Constructors

- `HandList(string steamID)`: Initializes a new instance of the `HandList` class with the specified Steam ID.

### Methods

- `IsSteamIDCorrect(string steamID)`: Checks if the provided Steam ID matches the stored Steam ID.
- `AddFourPai(SPai[] pai)`: Adds a set of four tiles (pai) to the player's hand.
- `AddOnePai(SPai pai, int index)`: Adds a tile (pai) to the player's hand at a specified index.
- `AddOnePai(SPai pai)`: Adds a tile (pai) to the player's hand at the first index (0).
- `ReplaceOnePai(int index)`: Replaces a tile (pai) in the player's hand at a specified index with the tile at the first index (0).
- `GetHandList(out bool hasDrawedPai, out SPai[] currentHandList, out byte[] isPaired)`: Retrieves the current hand list of the player.
- `ClearHandList()`: Resets the player's hand.
- `GetHandList()`: Retrieves the current hand list of the player.
- `Clean()`: Resets the player's hand.
- `GetSortedHandList()`: Retrieves the sorted hand list of the player.
- `GetReverseSortedHandList()`: Retrieves the reverse sorted hand list of the player.
- `GetOriginHandList()`: Retrieves the original hand list of the player.
- `CheckCanChi()`: Checks if the player can perform a Chi operation in the game of Mahjong.
- `CheckCanChi(SPai pai)`: Checks if the player can perform a Chi operation with a specific tile in the game of Mahjong.
- `CheckCanPon()`: Checks if the player can perform a Pon operation in the game of Mahjong.
- `CheckCanPon(SPai pai)`: Checks if the player can perform a Pon operation with a specific tile in the game of Mahjong.
- `CheckCanKan()`: Checks if the player can perform a Kan operation in the game of Mahjong.
- `CheckCanKan(SPai pai)`: Checks if the player can perform a Kan operation with a specific tile in the game of Mahjong.
- `CheckCanAddKan()`: Checks if the player can perform an AddKan operation in the game of Mahjong.
- `CheckCanAddKan(SPai pai)`: Checks if the player can perform an AddKan operation with a specific tile in the game of Mahjong.
- `CheckCanAnKan()`: Checks if the player can perform an AnKan operation in the game of Mahjong.
- `DoPon(SPai pai, EPlayerRelativelyPosition type, params int[] indices)`: Performs the Pon operation in the game of Mahjong.
- `DoChi(SPai pai, EPlayerRelativelyPosition type, params int[] indices)`: Performs the Chi operation in the game of Mahjong.
- `DoAddKan(int index)`: Performs the AddKan operation in the game of Mahjong.
- `DoKan(SPai sPai, EPlayerRelativelyPosition type, params int[] indices)`: Performs the Kan operation in the game of Mahjong.
- `DoAnKan(params int[] indices)`: Performs the AnKan operation in the game of Mahjong.

Please note that the `HandList` class is not fully implemented yet.