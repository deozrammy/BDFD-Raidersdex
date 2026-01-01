# Comando para CAPTURAR
El **trigger** o **prefijo** que utilizo aquí es `rcatch` (puedes cambiar este por el que desees).

```
$nomention
$if[$getServerVar[ball_actual]==none]
    ❌ No hay ninguna RaiderBall activa en este momento.
$else
    $c[--- 1. VERIFICACIÓN DE TIEMPO ---]
    $if[$second>$getServerVar[spawn_control]]
        $setServerVar[ball_actual;none]
        ❌ ¡El tiempo se agotó! La RaiderBall ha escapado antes de que pudieras atraparla.
    $else
        $c[--- 2. VERIFICACIÓN DE NOMBRE ---]
        $if[$toLowercase[$message]==$getServerVar[ball_actual]]
            
            $c[--- 3. PROCESO DE RECOMPENSAS ---]
            $var[pago;$random[25;51]]
            $c[Suma al inventario local (Solo este servidor)]
            $setUserVar[$getServerVar[ball_actual];$sum[$getUserVar[$getServerVar[ball_actual]];1]]
            
            $c[Suma a Capturas Totales Globales (Para el Rango Global)]
            $setVar[capturas_totales;$sum[$getVar[capturas_totales;$authorID];1];$authorID]
            
            $c[Suma al dinero global]
            $setVar[dinero;$sum[$getVar[dinero;$authorID];$var[pago]];$authorID]

            $c[--- 4. EMBED DE ÉXITO DE CAPTURA ---]
            $title[✅ ¡Captura Exitosa!]
            $description[¡Increíble, **$username**! Acabas de atrapar a **$getServerVar[ball_actual]**.
            
💵 **Ganancia:** `$var[pago]` raidcoins globales.
📦 **Inventario Local:** Ahora tienes `$getUserVar[$getServerVar[ball_actual]]` en este servidor.]
            $color[00ff00]
            $thumbnail[$userAvatar[$authorID]]
            $footer[Usa rinv para ver tu colección local]

            $c[--- 5. LIMPIEZA DE LA VARIABLE ---]
            $setServerVar[ball_actual;none]

$else
            ❌ Ese no es el nombre correcto. ¡Rápido, inténtalo de nuevo!
        $endif
    $endif
$endif
```
