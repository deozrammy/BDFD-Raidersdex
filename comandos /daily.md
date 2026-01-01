# Comando para otorgar una recompensa cada `x` tiempo
El **trigger/prefijo** que utilizo aquí es `rdaily` (puedes cambiar este por el que desees).

```
$nomention

$c[--- 1. BLOQUEO GLOBAL (12h = 43200000 milisegundos) ---]
$if[$sub[$getTimestamp;0$getUserVar[daily_cooldown]]<43200000]
<:shocked_skull:1164459995958612050> **¡NO TAN RÁPIDO, ESPÉRATE CABRÓN!**
Ya reclamaste tu recompensa, puedes volver a reclamarlo después.

$else
    $c[--- 2. GUARDAR EL MOMENTO DEL RECLAMO ---]
    $setUserVar[daily_cooldown;$getTimestamp]

    $c[--- 3. ENTREGAR RECOMPENSAS ---]
    $var[monedas;$random[50;201]]
    $setVar[dinero;$sum[0$getVar[dinero];$var[monedas]]]

    $if[$random[1;11]==1]
        $setUserVar[nitro;$sum[0$getUserVar[nitro];1]]
        $var[extra;🚀 **¡BONUS!** 1 Nitro añadido.]
    $else
        $var[extra; ]
    $endif

    $title[🎁 Recompensa Semidiaria]
    $color[00ff00]
    $description[
¡Hola **$username**! Has recibido tus premios:

💰 **$var[monedas] raidcoins**
$var[extra]

*Puedes volver a reclamar en 12 horas.*]
    $footer[Balance: $getVar[dinero] dinero]
$endif
```
