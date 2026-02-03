# Custom Games (Partidas Personalizadas) Setup Guide

## Problema / Problem

Las partidas personalizadas 5v5 no devuelven datos cuando se usa el plugin-webapi para hacer fetching de datos en vivo.

Custom 5v5 games don't return data when using the plugin-webapi to fetch live game data.

## Explicación / Explanation

**Español:**

Desde el parche 14.1 de League of Legends, la API de Riot Games (SpectatorV5) solo devuelve información de partidas personalizadas (queueId: 0) si alguien está espectando activamente el juego desde el cliente de League of Legends.

Esto significa que:
- El juego personalizado NO aparecerá en la API automáticamente
- DEBE haber alguien espectando a través del cliente durante toda la duración que necesites los datos
- Esto es una limitación conocida de la API de Riot Games

**English:**

Since League of Legends patch 14.1, the Riot Games API (SpectatorV5) only returns custom game information (queueId: 0) if someone is actively spectating the game through the League of Legends client.

This means:
- The custom game will NOT appear in the API automatically
- Someone MUST be spectating through the client for the entire duration you need the data
- This is a known limitation of the Riot Games API

## Soluciones / Solutions

### 1. Espectador Manual / Manual Spectator (Recomendado para uso con API / Recommended for API usage)

**Español:**
1. Abre el cliente de League of Legends
2. Haz clic en "Espectador" o "Spectate" en el juego personalizado
3. Mantén el espectador conectado mientras necesites los datos
4. El plugin-webapi ahora podrá obtener los datos del juego en vivo

**English:**
1. Open the League of Legends client
2. Click "Spectate" on the custom game
3. Keep the spectator connected while you need the data
4. The plugin-webapi will now be able to fetch the live game data

### 2. League Observer Tool (Recomendado para producción / Recommended for production)

El [League Observer Tool](https://github.com/RCVolus/league-observer-tool) se conecta directamente al cliente y envía datos del juego al toolkit, evitando completamente la necesidad de usar la API de Riot.

The [League Observer Tool](https://github.com/RCVolus/league-observer-tool) connects directly to the client and sends game data to the toolkit, completely bypassing the need to use the Riot API.

Esta es la solución recomendada para entornos de producción y transmisiones profesionales.

This is the recommended solution for production environments and professional broadcasts.

### 3. Sistema de Códigos de Torneo / Tournament Code System

Para juegos competitivos organizados, usa el sistema de Códigos de Torneo de Riot que proporciona acceso completo a la API.

For organized competitive games, use Riot's Tournament Code system which provides full API access.

## Mensajes de Error / Error Messages

Si ves estos mensajes de error en los logs:

If you see these error messages in the logs:

```
Failed to get spectator game information...
IMPORTANT: If this is a custom game (5v5 custom match), the Riot API only returns data if someone is actively spectating via the League client.
```

Esto confirma que necesitas tener a alguien espectando el juego desde el cliente.

This confirms you need to have someone spectating the game from the client.

## Cambios Realizados / Changes Made

Esta actualización incluye:

This update includes:

1. ✅ Documentación explicando la limitación de partidas personalizadas
   - Documentation explaining custom game limitations

2. ✅ Mensajes de error mejorados con guía clara
   - Improved error messages with clear guidance

3. ✅ Logging de queueId para identificar partidas personalizadas (queueId: 0)
   - QueueId logging to identify custom games (queueId: 0)

4. ✅ Corrección de la lógica de reintentos
   - Fixed retry logic

5. ✅ README completo en módulo plugin-webapi
   - Complete README in plugin-webapi module

## Referencias / References

- [Riot Developer Relations - Custom Games API Issue](https://github.com/RiotGames/developer-relations/issues/884)
- [League Observer Tool](https://github.com/RCVolus/league-observer-tool)
- [Plugin WebAPI README](../modules/plugin-webapi/README.md)
