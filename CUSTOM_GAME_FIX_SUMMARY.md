# Custom Game Fetch Fix - Summary

## Problem Solved / Problema Resuelto

**Español:**
El plugin-webapi no devolvía datos para partidas personalizadas 5v5. Este problema era causado por una limitación de la API de Riot Games desde el parche 14.1.

**English:**
The plugin-webapi was not returning data for custom 5v5 games. This issue was caused by a Riot Games API limitation since patch 14.1.

## Solution / Solución

### What Changed / Qué Cambió

1. **Código Mejorado / Improved Code**
   - Mensajes de error más claros que explican el requisito de espectador
   - Detección automática de partidas personalizadas (queueId: 0)
   - Lógica de reintentos mejorada
   - Logging informativo cuando se detecta un juego personalizado

2. **Documentación Completa / Complete Documentation**
   - `docs/CUSTOM_GAMES.md` - Guía bilingüe (Español/Inglés)
   - `modules/plugin-webapi/README.md` - Detalles técnicos
   - README principal actualizado

### How to Use / Cómo Usar

Para que funcione el fetching de partidas personalizadas, tienes **3 opciones**:

#### Opción 1: Espectador Manual (La Más Simple)
1. Abre el cliente de League of Legends
2. Haz clic en "Espectador" en el juego personalizado
3. Mantén el espectador conectado mientras usas el toolkit
4. ¡Ahora el plugin-webapi podrá obtener los datos!

#### Opción 2: League Observer Tool (Recomendado para Producción)
- Usa el [League Observer Tool](https://github.com/RCVolus/league-observer-tool)
- Se conecta directamente al cliente (no usa la API de Riot)
- **Esta es la solución recomendada para broadcasts profesionales**

#### Opción 3: Códigos de Torneo
- Para torneos organizados, usa el sistema de Códigos de Torneo de Riot
- Proporciona acceso completo a la API

## Important Notes / Notas Importantes

### API Limitation / Limitación de la API
**Español:**
- Desde el parche 14.1, la API de Riot SOLO devuelve datos de partidas personalizadas si alguien está espectando
- Esto NO es un bug de este toolkit, es una limitación conocida de Riot Games
- Ver: https://github.com/RiotGames/developer-relations/issues/884

**English:**
- Since patch 14.1, Riot's API ONLY returns custom game data if someone is spectating
- This is NOT a bug in this toolkit, it's a known Riot Games limitation
- See: https://github.com/RiotGames/developer-relations/issues/884

## Files Changed / Archivos Modificados

```
- modules/plugin-webapi/plugin.ts (código mejorado)
- modules/plugin-webapi/README.md (nuevo)
- docs/CUSTOM_GAMES.md (nuevo, bilingüe)
- README.md (actualizado con referencia)
- .gitmodules (plugin-webapi convertido de submodule a directorio)
```

## Testing / Pruebas

Para probar los cambios:

1. Configura tu API key de Riot
2. Crea una partida personalizada 5v5
3. Haz que alguien use "Espectador" en el cliente
4. Intenta hacer fetch desde el toolkit
5. Deberías ver logs informativos incluyendo el queueId

## Next Steps / Próximos Pasos

1. **Lee la documentación**: `docs/CUSTOM_GAMES.md`
2. **Elige tu solución**: Espectador manual, Observer Tool, o Códigos de Torneo
3. **Prueba tu setup**: Verifica que puedes obtener datos de partidas personalizadas
4. **Para producción**: Considera usar el League Observer Tool

## Support / Soporte

Si tienes problemas:
1. Verifica que alguien está espectando el juego en el cliente
2. Revisa los logs del plugin-webapi
3. Consulta `docs/CUSTOM_GAMES.md` para más detalles
4. El toolkit ahora te dará mensajes claros cuando detecte un problema

---

## Technical Details / Detalles Técnicos

### Code Quality Improvements / Mejoras de Calidad

- ✅ Removed duplicate TR1 case
- ✅ Fixed retry logic (proper attempt counting)
- ✅ Efficient conditional logging
- ✅ Clear variable naming (attempts vs retries)
- ✅ Proper error handling
- ✅ TypeScript compilation passes

### Backward Compatibility / Compatibilidad

- ✅ No breaking changes
- ✅ Existing functionality preserved
- ✅ Optional retry parameter still works
- ✅ All existing integrations continue to work

---

**Created by:** GitHub Copilot
**Date:** 2026-02-03
**Issue:** Custom games not fetching in plugin-webapi
