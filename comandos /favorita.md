# Comando para establecer una ball de su inventario como favorita
El **trigger/prefijo** que utilizo aquí es `rfav` (puedes cambiar este por el que desees).

```
$nomention
$argsCheck[>1;❌ Escribe el nombre de la RaiderBall. Ejemplo: `rfav lazarus`]
$var[nombre;$toLowercase[$message]]

$c[--- Verificamos si tiene la ball en el inventario ---]
$if[$getUserVar[$var[nombre]]>0]
    $setUserVar[favorita;$var[nombre]]
    ✅ Has establecido a **$var[nombre]** como tu favorita.
$else
    ❌ No puedes elegir esa ball porque aún no la has capturado o no existe.
$endif
```
