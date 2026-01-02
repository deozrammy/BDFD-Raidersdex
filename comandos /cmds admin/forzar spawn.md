# Comando para forzar la aparición de una ball
Debes de poner tu ID o el ID de los que quieras que puedan utilizar este comando.

```
$nomention
$c[--- 1. SOLO EL DUEÑO PUEDE USARLO ---]
$if[$authorID==TU ID AQUÍ]
    
    $c[--- 2. VERIFICAR SI ESCRIBIÓ EL NOMBRE ---]
    $if[$message==]
        ❌ Debes escribir el nombre de la RaiderBall que quieres forzar.
        Ejemplo: `rforce imperio kumator`
    $else
        $c[--- 3. CONFIGURAR LA BALL FORZADA ---]
        $var[elegida;$toLowercase[$message]]
        $setServerVar[ball_actual;$var[elegida]]
        $setServerVar[spawn_control;$sum[$second;15]]

        $c[--- 4. DISEÑO DEL SPAWN ---]
        $title[⚠️ ¡Una RaiderBall ha sido INVOCADA!]
        $description[El administrador ha forzado la aparición de **$var[elegida]**.
        
        Usa `rcatch $var[elegida]` para capturarla.
        ⌛ **¡Tienes 15 segundos!**]
        $color[ff0000]

        $c[--- 5. LÓGICA DE IMÁGENES ---]
        $if[$var[elegida]==lazarus]$image[https://cdn.discordapp.com/attachments/1455014579858968577/1455042486060974213/135_sin_titulo_20251228210143.png]$endif
        $if[$var[elegida]==imperio lazarus]$image[https://cdn.discordapp.com/attachments/1455014579858968577/1455042503739834389/135_sin_titulo_20251228210903.png]$endif
        $if[$var[elegida]==sarca lazarus]$image[https://cdn.discordapp.com/attachments/1455014579858968577/1455042507615371345/135_sin_titulo_20251228211825.png]$endif

$footer[Invocación manual por $username]
    $endif
$else
    ❌ Solo el dueño del bot puede forzar apariciones.
$endif
```
