# Comando para visualizar el inventario del usuario
Yo utilicé de **trigger/prefijo** `rinv`, pero tú puedes usar el prefijo que desees para ejecutar este código.

```
$nomention
$c[--- 1. REINICIAR Y CALCULAR PROGRESO ---]
$setVar[progreso_temp;0]

$c[Conteo de capturas para el % de progreso]
$if[0$getUserVar[lazarus]>=1]$setVar[progreso_temp;$sum[$getVar[progreso_temp];1]]$endif
$if[0$getUserVar[imperio lazarus]>=1]$setVar[progreso_temp;$sum[$getVar[progreso_temp];1]]$endif
$if[0$getUserVar[sarca lazarus]>=1]$setVar[progreso_temp;$sum[$getVar[progreso_temp];1]]$endif

$c[--- 2. MOSTRAR EL INVENTARIO ---]
$title[📦 Inventario de **`$username`**]
$description[
> 🔰 **RAIDER GENERAL**
$if[0$getUserVar[lazarus]>=1]<:lazarus:1455020139069309009> **Lazarus** (x$getUserVar[lazarus])$else ⚪ *Bloqueado*$endif
$if[0$getUserVar[imperio lazarus]>=1]<:imperio_lazarus:1455020212075102413> **Imperio Lazarus** (x$getUserVar[venus])$else ⚪ *Bloqueado*$endif
$if[0$getUserVar[sarca lazarus]>=1]<:sarca_lazarus:1455081318030512169>  **Sarca Lazarus** (x$getUserVar[ichyros])$else ⚪ *Bloqueado*$endif

---
🎒 **Mochila de Objetos**
🚀 **Nitro:** `$getUserVar[nitro]` unidades
---
💡 *Usa `rball <nombre>` para ver la carta con stats.*]
$color[d18b22]
$footer[Progresión: $round[$divide[$multi[$getVar[progreso_temp];100];3]]% completado | $getVar[progreso_temp]/3 especies]

$c[Arriba después de "Progresión:" vas a editar el número 3 por el número que vas a tener de balls, esto irá sumando al progreso del usuario según las que tenga en su inventario a comparación de las totales]
```
