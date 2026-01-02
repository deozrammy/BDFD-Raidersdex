# Comando para reiniciar todo del usuario
Debes de poner tu ID o el ID de los que quieras que puedan utilizar este comando.

```
$nomention
$if[$authorID==TU ID AQUÍ]
    $c[--- RESETEO DE RAIDERBALLS ---]
    $setUserVar[lazarus;0;$mentioned[1]]
    $setUserVar[imperio lazarus;0;$mentioned[1]]
    $setUserVar[sarca lazarus;0;$mentioned[1]]

$c[--- RESETEO DE ECONOMÍA Y ESTADÍSTICAS ---]
    $setVar[dinero;0;$mentioned[1]]
    $setVar[capturas_totales;0;$mentioned[1]]
    $setUserVar[nitro;0;$mentioned[1]]

✅ La cuenta de **$username[$mentioned[1]]** ha sido completamente reiniciado por el Administrador.
**`-`** Raiderballs
**`-`** Raidcoins
**`-`** Capturas totales
**`-`** Nitro
$else
    ❌ Solo el dueño del bot puede ejecutar este comando.
$endif
$argsCheck[>1;❌ Debes mencionar a un usuario para resetearlo. Uso: `rreset-user @usuario`]
```
