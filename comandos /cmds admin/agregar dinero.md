# Comando para agregar dinero al usuario

Debes de poner tu ID o el ID de los que quieras que puedan utilizar este comando.
```
$nomention
$c[--- Solo tú puedes usar este comando (Reemplaza TU_ID por tu ID real) ---]
$if[$authorID!=TU ID AQUÍ]
  ❌ No tienes permiso para usar este comando de administrador.
$else
  $c[--- Verificamos que se mencionara a alguien y se pusiera una cantidad ---]
  $if[$message[2]==]
    ❓ Uso correcto: `radd @usuario <cantidad>`
  $else
    $c[--- Sumamos la cantidad a la variable dinero global ---]
    $setVar[dinero;$sum[$getVar[dinero;$mentioned[1;yes]];$message[2]];$mentioned[1;yes]]
    
    ✅ Se han añadido **$message[2]** Raidcoins a **$username[$mentioned[1;yes]]**.
    💰 Nuevo saldo: `$getVar[dinero;$mentioned[1;yes]]`
  $endif
$endif
```
