# Pistoleros de Chatarra 3D

Juego de tiros del Oeste en 3D con robots pistoleros y **mapas grandes en forma de laberinto** (con minimapa).

**Modos**
- **Niveles (campaña):** 10 niveles cada vez más difíciles hasta el jefe final, El Gran Tornillo. El progreso se guarda entre niveles.
- **Infinito:** oleadas sin fin, con récord por mapa.
- **Multijugador online · Duelo:** todos contra todos, sin límite práctico de jugadores. Construye, pica y rompe las bases rivales.
- **Multijugador online · Cooperativo:** juntos contra las oleadas. Si caes quedas **abatido** 30 segundos y un compañero puede **curarte** manteniendo E (◯ en el mando). Construís la base entre todos.

Se puede **construir en todos los modos**.

Mapas, cada uno con **su propia música original**:
- **Tornillo Gulch:** western silbado.
- **Cañón Rojo:** épica, con tambores graves y trompeta.
- **Mina abandonada:** de noche, con caja de música y gotas.
- **Estación del tren:** ritmo de tren, banjo, armónica y silbato.

## Construir (B, o L1 en el mando)

| Pieza | Coste | Aguante | Para qué |
|---|---|---|---|
| Sacos terreros | 5 | 250 | Cobertura baja |
| Muro de madera | 10 | 500 | Muro barato |
| Muro de piedra | 20 | 1000 | Muro resistente |
| Muro de metal | 35 | 1800 | El más duro |
| Puerta de saloon | 15 | 500 | Tú y tus compañeros pasáis; los bandidos y los rivales del duelo, no |
| Plataforma | 15 | 600 | Suelo en altura, con postes |
| Rampa | 15 | 600 | Para subir un piso |
| Torreta | 40 | 400 | Dispara sola a bandidos o rivales (máximo 3) |
| Trampa de pinchos | 20 | 300 | Daña a quien la pisa |
| Farol curativo | 15 | 150 | Cura poco a poco a los tuyos cerca (máximo 4) |

- **Elegir la pieza:** Q o las teclas 1-0, o △ y L2 en el mando.
- **Girar:** R.
- **Colocar:** clic o R2.

**En altura:**
- Pon una rampa, súbela y coloca plataformas arriba.
- Los muros se apilan si los pones en el mismo sitio.
- Estando arriba, los muros se colocan en el borde de la plataforma.

Los bandidos no suben rampas, pero golpean lo que te sostiene; si lo rompen, caes. Desde lo alto se dispara por encima de los muros del laberinto.

**Romper:** el **pico** (F o 4, o △ en el mando) va siempre contigo:
- Rompe cualquier construcción. Si la pieza es tuya, te devuelve la mitad del material.
- Saca materiales de cajas, rocas, cactus, barriles y muros.

Las armas y los misiles rompen las construcciones rivales; las tuyas y las de tus compañeros solo frenan tus balas. Los muros protegen de la onda expansiva de los misiles.

## Inventario y mejoras (botón Armería del menú, o T > Inventario)

Las armas que compras son **tuyas para siempre** y se guardan en el navegador. Llevas 3 equipadas más el pico.

Cada arma sube hasta el **nivel 5**. Cada nivel le da:
- **+45 % de daño** (a nivel 5 hace casi el triple).
- **+25 % de cargador**.
- Más cadencia y recarga más rápida.

Rareza por nivel: común (gris), poco común (verde), rara (azul), épica (morada) y legendaria (dorada). Las de nivel alto brillan en la mano. Las monedas son del juego: no hay pagos reales.

**Tienda** (T, o Crear/View en el mando): botiquines, armadura, munición, materiales, kits de reanimación y armas nuevas.

**Armas en el suelo:** acércate y pulsa E (◯ en el mando). Las que coges del suelo son solo para esa partida.

## Armas (nivel 1)

| Arma | Daño | Cargador |
|---|---|---|
| Pistola (la inicial) | 5 | 7 |
| Subfusil | 4 | 24 |
| Escopeta | 3 por perdigón · 20 si aciertan los 6 | 10 |
| Rifle | 20 | 5 |
| Rifle con mira | 50 · 100 a la cabeza (15 % de probabilidad) | 2 |
| Lanzamisiles | 150 en el centro de la explosión | 3 |
| Pico | 20 a cuerpo a cuerpo · triple contra construcciones | ∞ |

Los jugadores tienen **200 de vida**.

## Bases

Cada mapa tiene dos bases pequeñas de sacos terreros con una entrada. Los bandidos no pueden entrar ni te ven dentro, sus balas chocan contra los sacos y dentro van apareciendo armas cada 15 segundos.

## Qué hay en esta carpeta

| Archivo | Para qué sirve |
|---|---|
| `public/index.html` | El juego completo (gráficos 3D, sonido, música, controles) |
| `src/worker.js` | El servidor del modo online (un Worker de Cloudflare con un Durable Object) |
| `wrangler.jsonc` | La configuración que lee Cloudflare al publicar |
| `package.json` | Indica la herramienta de publicación (Wrangler) |

## Publicarlo (sin instalar nada en tu PC)

### 1. Súbelo a GitHub
1. Entra en [github.com](https://github.com) y pulsa **New** (repositorio nuevo). Nombre: `pistoleros-de-chatarra`. Puede ser público o privado. Pulsa **Create repository**.
2. En la página del repositorio vacío pulsa **uploading an existing file**.
3. Arrastra **el contenido** de esta carpeta (las carpetas `public` y `src` y los archivos `wrangler.jsonc`, `package.json`, `README.md` y `.gitignore`). No arrastres la carpeta entera, sino lo que hay dentro.
   - Si no ves `.gitignore` en Windows: Explorador → Ver → Mostrar → Elementos ocultos. Si no se sube, no pasa nada.
4. Pulsa **Commit changes**.

### 2. Publícalo en Cloudflare
1. Crea una cuenta gratis en [dash.cloudflare.com](https://dash.cloudflare.com) (o entra con la tuya).
2. En el menú, entra en **Workers & Pages** (o **Compute → Workers & Pages**) y pulsa **Create**.
3. Elige **Import a repository** / **Connect to Git** y autoriza a Cloudflare a ver tu cuenta de GitHub.
4. Selecciona el repositorio `pistoleros-de-chatarra`.
5. Deja los ajustes como vienen: sin build command, y el deploy command `npx wrangler deploy`. Pulsa **Deploy**.
6. Cuando termine (1-2 minutos) te da una dirección del tipo `https://pistoleros-de-chatarra.TU-USUARIO.workers.dev`. ¡Ese es tu juego!

### 3. Jugar online
- Abre tu dirección `…workers.dev`, pulsa **Multijugador online** y elige **Duelo** o **Cooperativo**, el mapa y tu nombre.
- Pasa esa misma dirección a tus amigos. Los que elijan **el mismo modo y el mismo mapa** entran en la misma partida.
- En el cooperativo, uno de los jugadores hace de anfitrión sin darse cuenta (mueve a los bandidos). Si se va, otro toma el relevo solo.
- No hace falta cuenta para jugar.

## Cambiar algo más adelante
Edita el archivo en GitHub (por ejemplo `public/index.html`) y guarda con **Commit changes**: Cloudflare lo vuelve a publicar solo en un par de minutos.

## Límites del plan gratuito de Cloudflare
El modo online usa Durable Objects, incluidos en el plan gratuito con un tope de peticiones diarias que se reinicia cada día a las 00:00 UTC. Cada jugador envía entre 7 y 15 mensajes por segundo (menos cuando hay mucha gente) y Cloudflare cuenta 20 mensajes como una petición, así que da para muchas horas de partidas al día. Si un día se superase el tope, el online dejaría de conectar hasta el día siguiente (el modo un jugador sigue funcionando).

## Probarlo en tu PC (opcional, para programadores)
Con Node.js instalado: `npm install` y luego `npx wrangler dev`, y abre `http://localhost:8787`.
