# Comando para comprar items con dinero
El **trigger/prefijo** que utilizo aquí es `rbuy` (puedes cambiar este por el que desees).

Aquí dejé 2 items para que puedas visualizar la estructura en la que se añaden:
- Item consumible que se guarda en su inventario local para poder usarse después.
- Item **banner** para desbloquear la posibilidad al usuario de cambiar su banner que se muestra al usar `rperfil`


```
$nomention
$var[item;$toLowercase[$message]]

$c[--- OPCIÓN 1: NITRO (250 coins) ---]
$if[$var[item]==nitro]
    $if[$getVar[dinero;$authorID]>=250]
        $setVar[dinero;$sub[$getVar[dinero;$authorID];250];$authorID]
        $setUserVar[nitro;$sum[$getUserVar[nitro];1]]
        ✅ ¡Compra exitosa! Has obtenido **1 Nitro**.
    $else
        ❌ No tienes suficientes Raidcoins (250).
    $endif

$c[--- OPCIÓN 2: BANNER FX (200 coins) ---]
$elseif[$var[item]==banner fx]
    $if[$getUserVar[banner fx]>=1]
        ⚠️ Ya posees este banner en tu inventario.
    $else
        $if[$getVar[dinero;$authorID]>=200]
            $setVar[dinero;$sub[$getVar[dinero;$authorID];200];$authorID]
            $setUserVar[banner fx;1]
            ✅ ¡Compra exitosa! Has obtenido el **Banner FX**. Usa `rbanner fx` para equiparlo.
        $else
            ❌ No tienes suficientes Raidcoins (200).
        $endif
    $endif
```
