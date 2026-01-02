# Comando para seleccionar un banner del inventario
El **trigger/prefijo** que utilizo aquí es `rbanner` (puedes cambiar este por el que desees).

```
$nomention
$var[eleccion;$toLowercase[$message]]

$if[$var[eleccion]==esquele]
    $if[$getUserVar[banner esquele]>=1]
        ✅ Has equipado el banner **Esquele Squad**.
        $setUserVar[banner_equipado;esquele]
    $else
        ❌ No tienes este banner. Cómpralo en la tienda.
    $endif

$elseif[$var[eleccion]==fx]
    $if[$getUserVar[banner fx]>=1]
        ✅ Has equipado el banner **FX**.
        $setUserVar[banner_equipado;fx]
    $else
        ❌ No tienes este banner. Cómpralo en la tienda.
    $endif
    
    $elseif[$var[eleccion]==versus]
    $if[$getUserVar[banner versus]>=1]
        ✅ Has equipado el banner **Versus**.
        $setUserVar[banner_equipado;versus]
    $else
        ❌ No tienes este banner. Cómpralo en la tienda.
    $endif

$elseif[$var[eleccion]==ninguno]
    ✅ Has quitado tu banner. Ahora verás el fondo por defecto.
    $setUserVar[banner_equipado;ninguno]

$else
    ❓ Uso: `rbanner <esquele | fx | ninguno>`
$endif
```
