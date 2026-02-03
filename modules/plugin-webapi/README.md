# Plugin WebAPI

This plugin fetches live game and match data from the Riot Games API.

## Features

- Fetch live game data for a summoner
- Fetch completed match data
- Fetch league/rank information for a summoner
- Get server/region location information

## Important Note: Custom Games (5v5 Custom Matches)

### Limitation

As of League of Legends patch 14.1, **custom games (queueId: 0) are only accessible via the Riot Games SpectatorV5 API if someone is actively spectating the game through the League client**.

This means:
- If you try to fetch live game data for a custom 5v5 match, the API will not return data unless someone has clicked "Spectate" in the League client
- The game must be actively spectated for the duration you need the data
- This is a known limitation from Riot Games and affects all applications using their public API

### Workarounds

1. **Manual Spectate (Recommended for API usage)**
   - Have someone open the League client
   - Click "Spectate" on the custom game
   - Keep the spectator connected while you need the data
   - The plugin will then be able to fetch the live game data via the API

2. **Use League Observer Tool (Recommended for production environments)**
   - The [League Observer Tool](https://github.com/RCVolus/league-observer-tool) connects directly to the League client and sends game data to the toolkit
   - This bypasses the need for the Riot API entirely for live game data
   - This is the recommended solution for production broadcasts

3. **Tournament Code System**
   - For organized competitive play, use Riot's Tournament Code system
   - Tournament code games have full API access

### Error Messages

If you see these error messages:
- `Failed to get spectator game information` - This may indicate:
  - The summoner is not in a game
  - The game is a custom match without an active spectator via the client
  - Network or API issues

The plugin will now provide additional guidance in the logs when fetching fails, specifically mentioning the custom game spectator requirement.

## References

- [Riot Developer Relations - Custom Games API Issue](https://github.com/RiotGames/developer-relations/issues/884)
- [League Observer Tool](https://github.com/RCVolus/league-observer-tool)
