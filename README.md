# PokéSurvivor — port para New 3DS / New 3DS port

LA UNICA PAGINA OFICIAL DEL JUEGO ES: https://pokesurvivor.com/ de **JPTER78**
THE ONLY OFFICIAL WEBSITE OF THE GAME IS: https://pokesurvivor.com/ by **JPTER78**

[Español](#español) · [English](#english)

## Traer tu partida de la web a la 3DS · Bring your web save to the 3DS

**Español.** Desde la versión 1.10 puedes pasar tu partida de pokesurvivor.com a
la 3DS. Se **fusiona** con la de la consola: se juntan los Pokémon, shinies y
logros, se suman monedas y tickets, y de los récords y mejoras se queda el mayor.

1. En un ordenador, abre [pokesurvivor.com](https://pokesurvivor.com/) e
   **inicia sesión** con tu cuenta. Espera a ver el menú del juego.
2. Pulsa **F12**, ve a la pestaña **Consola**, pega la línea de abajo y pulsa
   **Intro**. Si el navegador no deja pegar, escribe antes `allow pasting` (o
   `permitir pegar`) e Intro. Se descarga `pokesurvivor-web.json`.
3. Copia ese archivo a la tarjeta SD, en la carpeta `sdmc:/3ds/pokesurvivor/`.
4. Abre el juego en la 3DS: en el título te pregunta. **A** fusiona, **B** no.
   Antes de fusionar se guarda una copia en `sdmc:/3ds/pokesurvivor/save-antes-web.bin`.

**English.** Since version 1.10 you can move your pokesurvivor.com save to the
3DS. It is **merged** with the console save: Pokémon, shinies and achievements
are combined, coins and tickets are added up, and for records and upgrades the
highest value is kept.

1. On a computer, open [pokesurvivor.com](https://pokesurvivor.com/) and **log
   in** with your account. Wait until you see the game menu.
2. Press **F12**, go to the **Console** tab, paste the line below and press
   **Enter**. If the browser does not let you paste, first type `allow pasting`
   and press Enter. The file `pokesurvivor-web.json` is downloaded.
3. Copy that file to the SD card, into the folder `sdmc:/3ds/pokesurvivor/`.
4. Open the game on the 3DS: the title screen asks you. **A** merges, **B** skips.
   Before merging, a backup is saved as `sdmc:/3ds/pokesurvivor/save-antes-web.bin`.

```js
(async()=>{const u=firebase.auth().currentUser;if(!u){alert('Inicia sesión primero');return}const d=await firebase.firestore().collection('saves').doc(u.uid).get();const s=d.exists&&d.data().save;if(!s){alert('No se encontró la partida');return}const a=document.createElement('a');a.href=URL.createObjectURL(new Blob([JSON.stringify(s,function(k,v){const o=this[k];return o&&o.toMillis?o.toMillis():v})],{type:'application/json'}));a.download='pokesurvivor-web.json';a.click()})()
```

(Si sale «Inicia sesión primero», aún no has entrado o la página no ha terminado
de cargar. · If you get "Inicia sesión primero", you are not logged in yet or the
page has not finished loading.)

---

## Español

Port no oficial a **Nintendo 3DS** (pensado para New 3DS / New 2DS) de
**PokéSurvivor**, el juego web de **JPTER78**. Port y mods: **Tomakoku**.

Trae mods propios, **todos opcionales** (Configuración → Mods):
Modo evolución en plena partida, Megaevoluciones con su animación de X / Y,
Sustituto señuelo, cámara ajustable, minimapa, panel de ataques en rombo y
menús con estilo nuevo (la paleta «Clásica» los deja como el original).

### Descargar e instalar

Necesitas una consola con custom firmware (Luma3DS) y **FBI**.

**Con el QR (FBI → Remote Install → Scan QR Code):**

<img src="https://api.qrserver.com/v1/create-qr-code/?size=260x260&margin=12&data=https%3A%2F%2Fgithub.com%2FTomakoku%2FPokesurvivor-port-n3ds%2Freleases%2Flatest%2Fdownload%2Fpokesurvivor.cia" alt="QR para instalar con FBI / QR to install with FBI" width="260">

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

### Controles

| | |
|---|---|
| Círculo, C-stick o cruceta | Moverse |
| X, Y, B, A | El movimiento de cada hueco (se cambian en Configuración) |
| L / R | Movimiento anterior / siguiente |
| ZL / ZR | Megaevolucionar (con la energía mega llena) |
| SELECT | Panel o minimapa |
| START | Pausa |
| Pantalla táctil | Usar una esfera de Mundo Misterioso (también con el botón que le pongas en Configuración → Esferas) |

### Novedades

Lo que trae cada versión: [CAMBIOS.txt](CAMBIOS.txt).

### Créditos y licencias

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
  [makerom](https://github.com/3DSGuy/Project_CTR),
  [bannertool](https://github.com/Steveice10/bannertool) y
  [pycgfx](https://github.com/skyfloogle/pycgfx).

Pokémon y todos los nombres y personajes relacionados son marcas de Nintendo,
Creatures Inc., GAME FREAK y The Pokémon Company. Este es un proyecto de fans
sin ánimo de lucro, no afiliado ni aprobado por ellos. No se vende ni se cobra
por él.

---

## English

Unofficial **Nintendo 3DS** port (made for New 3DS / New 2DS) of
**PokéSurvivor**, the web game by **JPTER78**. Port and mods: **Tomakoku**.

It comes with its own mods, **all optional** (Settings → Mods): evolution mode
during a run, Mega Evolutions with their X / Y animation, decoy Substitute,
adjustable camera, minimap, diamond move panel and restyled menus (the
"Clásica" palette makes them look like the original).

### Download and install

You need a console with custom firmware (Luma3DS) and **FBI**.

**With the QR code (FBI → Remote Install → Scan QR Code):** use the QR in the
Spanish section above. It always points to the latest version.

Direct link to the latest version:
`https://github.com/Tomakoku/Pokesurvivor-port-n3ds/releases/latest/download/pokesurvivor.cia`

**Manually:** download `pokesurvivor.cia` from
[Releases](https://github.com/Tomakoku/Pokesurvivor-port-n3ds/releases), copy it
to the SD card and install it with FBI. To update, install the new one over it:
your save is kept. You can also use `pokesurvivor.3dsx` from the Homebrew
Launcher (copy it to `sdmc:/3ds/`) or in the Azahar emulator.

- Your save is stored in `sdmc:/3ds/pokesurvivor/save.bin`.
- **Sound:** it needs `sdmc:/3ds/dspfirm.cdc`, which you dump from your own
  console with the **DSP1** homebrew app. Without it the game works, but silent.
- If you had the old port installed (title `0xD5A7E`), uninstall it: it uses the
  same save, cannot read the new version and would start from scratch.
- The game can be played in English: Settings → Options → Language.

### Controls

| | |
|---|---|
| Circle Pad, C-stick or D-pad | Move |
| X, Y, B, A | The move in each slot (change them in Settings) |
| L / R | Previous / next move |
| ZL / ZR | Mega Evolve (with the mega energy full) |
| SELECT | Panel or minimap |
| START | Pause |
| Touch screen | Use a Mystery Dungeon orb (also with the button you give it in Settings → Orbs) |

### What's new

What each version brings: [CAMBIOS.txt](CAMBIOS.txt) (in Spanish). The release
notes on the [Releases](https://github.com/Tomakoku/Pokesurvivor-port-n3ds/releases)
page are in Spanish and English.

### Credits and licenses

- **Original game:** PokéSurvivor by JPTER78. Its code and music are under the
  MIT license (see [LICENSE-juego.txt](LICENSE-juego.txt)).
- **Pokémon sprites:** [SpriteCollab](https://github.com/PMDCollab/SpriteCollab),
  CC BY-NC 4.0 license (non-commercial use, with attribution). The artists are
  listed in [CREDITS-sprites.md](CREDITS-sprites.md).
- **Mods (interface and Mega Evolution graphics):**
  [PokeRogue](https://github.com/pagefaultgames/pokerogue) (windows, types and
  mega sprites), La Base de Sky, the Pokémon Essentials kit (orb, background and
  Mega Evolution symbol), and
  [pokesprite](https://github.com/msikma/pokesprite) (item icons).
- **Data:** [PokeAPI](https://pokeapi.co/).
- **Font:** Pixelify Sans, SIL Open Font License 1.1.
- **Tools:** [devkitPro](https://devkitpro.org/) (libctru, citro2d),
  [makerom](https://github.com/3DSGuy/Project_CTR),
  [bannertool](https://github.com/Steveice10/bannertool) and
  [pycgfx](https://github.com/skyfloogle/pycgfx).

Pokémon and all related names and characters are trademarks of Nintendo,
Creatures Inc., GAME FREAK and The Pokémon Company. This is a non-profit fan
project, not affiliated with or endorsed by them. It is not sold and nothing is
charged for it.
