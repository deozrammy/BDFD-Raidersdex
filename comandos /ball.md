# Comando para ver la ball capturada
El **trigger/prefijo** que utilizo aquí es `rball` (puedes cambiar este por el que desees).

```
$nomention
$c[--- Convertimos el mensaje a minúsculas para evitar errores ---]
$var[nombre;$toLowercase[$message]]

$c[--- Verificamos si el usuario tiene la ball ---]
$if[$getUserVar[$var[nombre]]==0]
  ❌ No tienes a **$message** en tu colección todavía.
$elseif[$getUserVar[$var[nombre]]==none]
  ❌ Esa RaiderBall no existe en nuestros datos.
$else
  $c[--- Mostramos la imagen con Stats ---]
  $title[🎴 Carta **$message**]
  
  $if[$var[nombre]==lazarus]
     $image[https://cdn.discordapp.com/attachments/1455012649476817028/1455013719586242650/image.png]
  $elseif[$var[nombre]==imperio lazarus]
     $image[https://cdn.discordapp.com/attachments/1455012649476817028/1455013772975538237/image.png]
  $elseif[$var[nombre]==sarca lazarus]
     $image[https://cdn.discordapp.com/attachments/1455012649476817028/1455013855926292552/image.png]
$endif

$color[d18b22]
$footer[Colección de $username]
$endif
```
