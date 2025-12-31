# VARIABLES Y SUS USOS

## Explicación breve sobre el uso de variables en este bot
Utilizamos variables para:
- Crear una ball.
- Conteo de números.
- Sistema de spawn.
- Sistema de guardado.
- Sitema de economía (opcional).
- Sistema de personalización (opcional).
> *Estas no son las variables que crearemos, solo son una explicación del funcionamiento de las mismas.*

---

# VARIABLES PRINCIPALES
| VARIABLE | VALOR | DESCRIPCIÓN |
|---|---|---|
| spawn_mensajes | 0 | Contador de mensajes necesarios para spawnear |
| spawn_control | 0 | Registra el tiempo límite (en segundos) antes de que escape la ball |
| ball_actual | none | Guarda el nombre de la raiderball que está activa para capturar |
| nombredetuball| 0 | Debes crear una por cada ball que hagas (ej: `lazarus`, `venus`). Almacena la cantidad que posee el usuario |

# VARIABLES DE CONTEO/ESTADÍSTICA
| VARIABLE | VALOR | DESCRIPCIÓN |
|---|---|---|
| progreso_temp | 0 | descripción breve |
| capturas_totales | 0 | descripción breve |

# VARIABLES DE ECONOMÍA
| VARIABLE | VALOR | DESCRIPCIÓN |
|---|---|---|
| dinero | 0 | cantidad de dinero que posee el usuario |
| daily_cooldown | 0 | tiempo que debe de esperar para reclamar una recompensa diaria |
| tuitem | 0 | Debes crear una por cada item que hagas para la tienda (ej: `nitro`, `boost`). Almacena la cantidad que posee el usuario|

# VARIABLES DE PERSONALIZACIÓN
| VARIABLE | VALOR | DESCRIPCIÓN |
|---|---|---|
| favorita | ninguna | Registra la ball favorita del usuario en su perfil |
| banner_equipado | ninguno | Registra el banner que portará el usuario en su perfil |
| banner nombredeltuyo | 0 | Debes crear una por cada banner que hagas (ej: `banner versus`, `banner fx`). |

## ¿Son variables globales, de usuario o de servidor?
Son de los 3 tipos, pero no te preocupes, que en el código de cada comando ya se especifica si es:
- `$setVar`/`$getVar` (Global).
- `$setUserVar`/`$getUserVar` (Usuario).
- `$setServerVar`/`$getServerVar` (Servidor).
