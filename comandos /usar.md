# Comando para usar un item del inventario
El **trigger/prefijo** que utilizo aquí es `rusa` (puedes cambiar este por el que desees).

Este es el comando para utilizar el item **nitro** que hay en la tienda, nitro comprado con `rbuy nitro` para almacenarse en el inventario local del usuario
```
$nomention
$if[0$getUserVar[nitro]>0]
    $c[--- 1. CONSUMIR ÍTEM ---]
    $setUserVar[nitro;$sub[0$getUserVar[nitro];1]]

    $c[--- 2. SORTEO POR RAREZA (50/40/10) ---]
    $var[suerte;$random[1;101]]

    $if[$var[suerte]<=50]
        $c[--- COMUNES (50%) ---]
        $var[elegida;$randomText[lazarus;fx;media luna;night club;imperio kumator;skyoe;ichyros;venus;ochub;darkness;sarca lazarus;lux;ghostnaz]]
        $var[tipo;Común <:rb_comun:1455782221012008992>]
    $else
        $if[$var[suerte]<=90]
            $c[--- ÉPICAS (40%) ---]
            $var[elegida;$randomText[imperio lazarus;ufaf;estirpe caesariana;baphometards;antiplague;space gang;rodskvadron;hell squad]]
            $var[tipo;Épica <:rb_epico:1455782267690680482>]
        $else
            $c[--- LEGENDARIAS (10%) ---]
            $var[elegida;$randomText[sdlg;legion holk;esquele squad;dead destroyers;imperio cactus;4chan]]
            $var[tipo;Legendaria <:rb_legendario:1455782365140877488>]
        $endif
    $endif

$c[--- 3. CONTROL DE SPAWN ---]
    $setServerVar[ball_actual;$var[elegida]]
    $setServerVar[spawn_control;$sum[$second;10]]

    ✨ **$username** ha activado un **Nitro**... ¡Algo está apareciendo!
    *(Rareza detectada: $var[tipo])*

    $title[⚠️ ¡Una RaiderBall salvaje ha aparecido!]
    $description[Adivina quién es y usa `rcatch <nombre>` para capturarla.
    
    ⌛ **¡Tienes 10 segundos antes de que escape!**]
    $color[ffff00]

    $c[--- 4. LÓGICA DE IMÁGENES ---]
    $if[$var[elegida]==lazarus]$image[https://cdn.discordapp.com/attachments/1455014579858968577/1455042486060974213/135_sin_titulo_20251228210143.png]$endif
    $if[$var[elegida]==imperio lazarus]$image[https://cdn.discordapp.com/attachments/1455014579858968577/1455042503739834389/135_sin_titulo_20251228210903.png]$endif
    $if[$var[elegida]==sarca lazarus]$image[https://cdn.discordapp.com/attachments/1455014579858968577/1455042507615371345/135_sin_titulo_20251228211825.png]$endif

$footer[¡Nitro de $username! ✨]
$else
    ❌ No tienes **Nitro** en tu inventario.
$endif
```
