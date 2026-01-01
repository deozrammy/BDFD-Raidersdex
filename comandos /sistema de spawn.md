# Sistema de spawn automático
Spawn automático por conteo de mensajes, muy atento ya que te explicaré cómo se van a registrar los mensajes ya que hay 2 maneras en BDFD:
- Utilizar este código en UN sólo comando usando de **trigger/prefijo** `$alwaysReply` (necesitarás puntos premium en BDFD).
- Utilizar este código y crear varios comandos usando de **trigger/prefijo** las letras de la A-Z y a-z (mayúsculas y minúsculas) para que registre todos los mensajes si no puedes usar `$alwaysReply`

## Explicación
**SI TIENES PUNTOS PREMIUM**
- Utilizarás `$alwaysReply` como **trigger/prefijo** en el comando donde coloques este código.

**ALTERNATIVA GRATUITA**
- Crearás +50 comandos con este código cada uno, y su **trigger/prefijo** será a, b, c, etc. (mayus y minus).

## ¿Qué hará este código?
**FUNCIONAMIENTO:**
- (Premium) Cada vez que detecte un nuevo mensaje con `$alwaysReply` sumará +1 a la condición de spawneo de ball
- (Gratis) Cada vez que detecte la primera letra de un mensaje envíado se sumará +1 a la condición de spawneo de ball

**LÓGICAS:**
- Reinicia el contador de mensajes una vez se llegue al límite (CONDICIÓN: MENSAJES).
- Hay una probabilidad de spawn, a pesar de llegar a los 20 pasará un filtro donde se decide si se envía o deben de volver a envíar más mensajes (Tiene 90% de aparecer por si lo quieres probar rápido).
- Si se va a envíar la ball, hay otro filtro de probabilidades que elige su rareza (más probable de aparecer o menos probable) puedes quitar las probabilidades si no quieres rarezas o agregar más.
- Envía una imágen que representa a la ball en cuestión para ser capturada.

---
```
$nomention

$c[--- 1. SUMAR MENSAJE ---]
$setServerVar[spawn_mensajes;$sum[$getServerVar[spawn_mensajes];1]]

$c[--- 2. CONDICIÓN: MENSAJES ---]
$if[$getServerVar[spawn_mensajes]>=20]
    
    $c[--- REINICIAR CONTADOR ---]
    $setServerVar[spawn_mensajes;0]

    $c[--- 3. PROBABILIDAD DE APARICIÓN (90%) ---]
    $if[$random[1;101]<=90]
        
        $c[--- 4. SORTEO POR RAREZA ---]
        $var[suerte;$random[1;101]]

        $if[$var[suerte]<=50]
            $c[--- COMUNES (50%) ---]
            $var[rareza;común <:rb_comun:1455782221012008992>]
            $var[elegida;$randomText[lazarus;fx;media luna;night club;imperio kumator;skyoe;ichyros;venus;ochub;darkness;sarca lazarus;ghostnaz;lux]]
        $else
            $if[$var[suerte]<=90]
                $c[--- ÉPICAS (40%) ---]
                $var[rareza;épica <:rb_epico:1455782267690680482>]
                $var[elegida;$randomText[imperio lazarus;ufaf;estirpe caesariana;baphometards;antiplague;space gang;rodskvadron;hell squad]]
            $else
                $c[--- LEGENDARIAS (10%) ---]
                $var[rareza;legendaria <:rb_legendario:1455782365140877488>]
                $var[elegida;$randomText[sdlg;legion holk;esquele squad;dead destroyers;imperio cactus;4chan]]
            $endif
        $endif

$c[--- 5. GUARDAR DATOS ---]
        $setServerVar[ball_actual;$var[elegida]]
        $setServerVar[spawn_control;$sum[$second;10]]

        $title[⚠️ ¡Una RaiderBall salvaje ha aparecido!]
        $description[Adivina quién es y usa `rcatch <nombre>` para capturarla.

✨ **Rareza:** $toUppercase[$var[rareza]]
⌛ **¡Tienes 10 segundos!**]
        $color[ffff00]

        $c[--- 6. IMÁGENES --- Vas a colocar una nueva línea con una imagen personalizada tuya por cada nueva ball, yo dejé 3 para que veas]
$if[$var[elegida]==lazarus]$image[https://cdn.discordapp.com/attachments/1455014579858968577/1455042486060974213/135_sin_titulo_20251228210143.png]$endif
$if[$var[elegida]==imperio lazarus]$image[https://cdn.discordapp.com/attachments/1455014579858968577/1455042503739834389/135_sin_titulo_20251228210903.png]$endif
$if[$var[elegida]==sarca lazarus]$image[https://cdn.discordapp.com/attachments/1455014579858968577/1455042507615371345/135_sin_titulo_20251228211825.png]$endif

$footer[¡Sé rápido antes de que desaparezca!]
$endif
$endif
```
