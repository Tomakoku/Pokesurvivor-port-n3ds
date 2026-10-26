# PokéSurvivor — port para New 3DS

Port no oficial a **Nintendo 3DS** (pensado para New 3DS / New 2DS) de
**PokéSurvivor**, el juego web de **JPTER78**. Port y mods: **Tomakoku**.
LA UNICA PAGINA OFICIAL DEL JUEGO ES: https://pokesurvivor.com/ de **JPTER78**

Trae mods propios, **todos opcionales** (Configuración → Mods):
Modo evolución en plena partida, Megaevoluciones con su animación de X / Y,
Sustituto señuelo, cámara ajustable, minimapa, panel de ataques en rombo y
menús con estilo nuevo (la paleta «Clásica» los deja como el original).

## Descargar e instalar

Necesitas una consola con custom firmware (Luma3DS) y **FBI**.

**Con el QR (FBI → Remote Install → Scan QR Code):**

<img src="https://api.qrserver.com/v1/create-qr-code/?size=260x260&margin=12&data=https%3A%2F%2Fgithub.com%2FTomakoku%2FPokesurvivor-port-n3ds%2Freleases%2Flatest%2Fdownload%2Fpokesurvivor.cia" alt="QR para instalar con FBI" width="260">

Enlace directo de la última versión:
`https://github.com/Tomakoku/Pokesurvivor-port-n3ds/releases/latest/download/pokesurvivor.cia`

**A mano:** descarga `pokesurvivor.cia` de
[Releases](https://github.com/Tomakoku/Pokesurvivor-port-n3ds/releases), cópialo
a la SD e instálalo con FBI. Para actualizar, instala el nuevo encima: la partida
se conserva. También vale `pokesurvivor.3dsx` desde el Homebrew Launcher
(cópialo a `sdmc:/3ds/`) o en el emulador Azahar.

- La partida se guarda en `sdmc:/3ds/pokesurvivor/save.bin`.
- **Sonido:** hace falta `sdmc:/3ds/dspfirm.cdc`, que se saca de tu propia
  consola con la app homebrew **DSP1**. Sin él el juego funciona, pero mudo.
- Si tenías instalado el port antiguo (título `0xD5A7E`), desinstálalo: usa la
  misma partida, no lee la versión nueva y empezaría de cero.

## Traer tu partida de la web

Desde la versión 1.10 puedes pasar tu partida de pokesurvivor.com a la 3DS. Se
**fusiona** con la de la consola: se juntan los Pokémon, shinies y logros, se
suman monedas y tickets, y de los récords y mejoras se queda el mayor.

1. En [pokesurvivor.com](https://pokesurvivor.com/), con tu cuenta abierta,
   pulsa **F12 → Consola**, pega esta línea y pulsa Intro (Chrome puede pedir
   que escribas antes `allow pasting`). Se descarga `pokesurvivor-web.json`:

   ```js
   (async()=>{const u=firebase.auth().currentUser;if(!u){alert('Inicia sesión primero');return}const d=await firebase.firestore().collection('saves').doc(u.uid).get();const s=d.exists&&d.data().save;if(!s){alert('No se encontró la partida');return}const a=document.createElement('a');a.href=URL.createObjectURL(new Blob([JSON.stringify(s,function(k,v){const o=this[k];return o&&o.toMillis?o.toMillis():v})],{type:'application/json'}));a.download='pokesurvivor-web.json';a.click()})()
   ```

2. Copia el archivo a la SD, en `sdmc:/3ds/pokesurvivor/`.
3. Abre el juego: en el título te pregunta. **A** fusiona, **B** no.

Antes de fusionar se guarda una copia en `sdmc:/3ds/pokesurvivor/save-antes-web.bin`.

## Controles

| | |
|---|---|
| Círculo, C-stick o cruceta | Moverse |
| X, Y, B, A | El movimiento de cada hueco (se cambian en Configuración) |
| L / R | Movimiento anterior / siguiente |
| ZL / ZR | Megaevolucionar (con la energía mega llena) |
| SELECT | Panel o minimapa |
| START | Pausa |

## Novedades

Lo que trae cada versión: [CAMBIOS.txt](CAMBIOS.txt).

## Créditos y licencias

- **Juego original:** PokéSurvivor de JPTER78. Su código y su música tienen
  licencia MIT (ver [LICENSE-juego.txt](LICENSE-juego.txt)).
- **Sprites de Pokémon:** [SpriteCollab](https://github.com/PMDCollab/SpriteCollab),
  licencia CC BY-NC 4.0 (uso no comercial, con atribución). Los artistas están en
  [CREDITS-sprites.md](CREDITS-sprites.md).
- **Mods (gráficos de interfaz y megaevolución):**
  [PokeRogue](https://github.com/pagefaultgames/pokerogue) (ventanas, tipos y
  sprites de megas), La Base de Sky, el kit de Pokémon Essentials (orbe, fondo
  y símbolo de la megaevolución), y
  [pokesprite](https://github.com/msikma/pokesprite) (iconos de objetos).
- **Datos:** [PokeAPI](https://pokeapi.co/).
- **Fuente:** Pixelify Sans, SIL Open Font License 1.1.
- **Herramientas:** [devkitPro](https://devkitpro.org/) (libctru, citro2d),
  [makerom](https://github.com/3DSGuy/Project_CTR) y
  [bannertool](https://github.com/Steveice10/bannertool) y
  [pycgfx](https://github.com/skyfloogle/pycgfx).

Pokémon y todos los nombres y personajes relacionados son marcas de Nintendo,
Creatures Inc., GAME FREAK y The Pokémon Company. Este es un proyecto de fans
sin ánimo de lucro, no afiliado ni aprobado por ellos. No se vende ni se cobra
por él.
