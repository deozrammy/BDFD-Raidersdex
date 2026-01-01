# Comando para ver el perfil (del juego) del usuario
El **trigger/prefijo** que utilizo aquí es `rperfil` (puedes cambiar este por el que desees).

## ¿Qué se va a mostrar con este código?
- "Rango" que se muestra y evoluciona según las capturas totales del usuario.
- Su cantidad de dinero total.
- Se mostrará el emoji y nombre de su ball favorita.
- Se mostrará un banner elegido por el usuario al ejecutar el comando.
- Si no tiene un banner seleccionado, se mostrará uno por defecto.


```
$nomention
$var[id;$mentioned[1;yes]]

$c[--- 1. OBTENCIÓN DE DATOS ---]
$var[total;$getVar[capturas_totales;$var[id]]]
$var[plata;$getVar[dinero;$var[id]]]
$var[fav_nombre;$getUserVar[favorita;$var[id]]]
$var[banner;$getUserVar[banner_equipado;$var[id]]]

$c[--- LÓGICA DE BANNERS --- Definimos el banner por defecto primero]
$var[url_banner;https://cdn.discordapp.com/attachments/1455832821120630905/1455832838778912872/150_sin_titulo_20251231015944.png]

$c[Cambiamos la URL si hay uno equipado]
$if[$var[banner]==esquele]
  $var[url_banner;https://cdn.discordapp.com/attachments/1455832821120630905/1455832847037235250/images_1_1.jpeg]
$elseif[$var[banner]==fx]
  $var[url_banner;https://cdn.discordapp.com/attachments/1455832821120630905/1455832854801158266/150_sin_titulo_20251231015906.png]
$elseif[$var[banner]==versus]
  $var[url_banner;https://cdn.discordapp.com/attachments/1455832821120630905/1455843048507441258/150_sin_titulo_20251231023952.png?ex=695632ff&is=6954e17f&hm=11b0fd931ef03b2d067e019bfd8e67fbbfa19b3ffc8dd08fed066c6200c417ca&]
$endif

$c[--- 2. LÓGICA DE EMOJI ---]
$var[fav_emoji;$var[fav_nombre]]
$var[fav_emoji;$replaceText[$var[fav_emoji];lazarus;<:lazarus:1455020139069309009>]]
$var[fav_emoji;$replaceText[$var[fav_emoji];imperio lazarus;<:imperio_lazarus:1455020212075102413>]]
$var[fav_emoji;$replaceText[$var[fav_emoji];sarca lazarus;<:sarca_lazarus:1455081318030512169>]]

$c[--- 3. LÓGICA DE TEXTO FINAL ---]
$if[$var[fav_nombre]==ninguna]
  $var[texto_estrella;NINGUNA]
$else
  $var[texto_estrella;$var[fav_emoji] $toUppercase[$var[fav_nombre]]]
$endif

$c[--- 4. LÓGICA DE RANGO ---]
$var[rango;🥚Aspirante]
$if[$var[total]>10]$var[rango;⚔️Domador]$endif
$if[$var[total]>25]$var[rango;🎖️Capitán Raider]$endif
$if[$var[total]>40]$var[rango;⭐General Raider]$endif
$if[$var[total]>65]$var[rango;👑Maestro Raider]$endif
$if[$var[total]>80]$var[rango;🗿Deidad Raider ]$endif

$c[--- 5. CONSTRUCCIÓN DEL EMBED ---]
$title[👤 Perfil de $username]
$color[d18b22]
$footerIcon[$userAvatar[$var[id]]]

$addField[<:mastermind:1455140637572595888> **Rango**;$var[rango];true]
$addField[<:checado:1455141008982413334> **Capturas Totales**;$var[total] Raider Balls;true]
$addField[💵 **Dinero Global**;`$var[plata]` raidcoins;true]
$addField[**Estrella del Equipo**;<a:medalla:1455141718780285055> $var[texto_estrella];false]

$c[--- AQUÍ SE MUESTRA EL BANNER ---]
$image[$var[url_banner]]

$footer[Explorando la región de $serverName[$guildID]]
$addTimestamp
```
