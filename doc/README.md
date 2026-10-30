# Documentación del proyecto · Clínica I: Freud en el orden del programa

Registro de qué se construyó, con qué criterios, qué decisiones se tomaron y cómo seguir editándolo. Pensado para retomar el trabajo en otra sesión (humana o con Claude) sin tener que reconstruir el contexto.

---

## 1. Qué es

Un sitio de una sola página (`index.html`) con un **scrollytelling** pedagógico sobre la bibliografía básica del curso **Clínica I: Fundamentos psicoanalíticos** (Facultad de Psicología, UDELAR, Uruguay, 2026). Se lee Freud en el **orden del programa de la cátedra** (tema → tópico → texto), no en orden cronológico, y los diagramas se arman a medida que se avanza.

Se publica como sitio estático en GitHub Pages: `https://pasquinell.github.io/clinica1_fund_PsA/` (repo `Pasquinell/clinica1_fund_PsA`, rama `main`, raíz).

## 2. Archivos

| Ruta | Qué es |
|---|---|
| `index.html` | **Fuente única de verdad.** Todo el material: HTML, CSS y JS inline. ~370 KB. |
| `img/freud.jpg` | Retrato de Freud, Max Halberstadt c. 1921, dominio público (Wikimedia Commons: `Sigmund_Freud,_by_Max_Halberstadt_(cropped).jpg`, ancho 960). |
| `.nojekyll` | Evita que GitHub Pages procese el sitio con Jekyll. |
| `README.md` | Presentación del repo. |
| `doc/README.md` | Este archivo. |
| `doc/tools/cdp.mjs` | Script Node que abre Chrome headless, scrollea de verdad y saca capturas (para probar el scrollytelling). |
| `doc/tools/figs_preview.py` | Genera páginas con todos los diagramas en su estado final, para revisar solapamientos. |
Material de entrada (resumen extenso). No hace falta para la página. Decidir si se publica. |


Durante la construcción el HTML se armó concatenando 8 partes en un directorio temporal; esas partes **ya no existen**. Desde ahora se edita `index.html` directamente.

## 3. Pedido original (resumen)

- HTML (no artefacto de Claude), archivo local, luego hosteable en GitHub.
- Scrollytelling dinámico; diagramas y conceptos que **aparezcan de a poco** y tengan sentido en el relato.
- Respetar el orden de las dos tablas de la cátedra (tema → tópico), aunque vaya y venga en el tiempo.
- Parcial 1: de «¿Qué es el psicoanálisis?» a «Primera teoría pulsional». Parcial 2: de «Síntoma» a «Relación entre pulsión y cultura».
- Traducción Amorrortu (Etcheverry): pulsión, investidura, sepultamiento, etc.
- No confiar 100 % en los `.md` provistos; las Conferencias 17, 18, 19 y 23 debían tratarse con más profundidad.
- El diagrama de la Conf. 23 (series complementarias / formación de síntoma) como modelo de buen diagrama.
- Sin datos inventados: basarse en los textos o en búsqueda web.
- **Temporalidad estricta:** no usar conceptos posteriores (p. ej. segunda tópica) en textos anteriores; si se mencionan, marcarlos como anticipación.
- Muy pedagógico: qué dice Freud, de qué observación o caso sale, en qué contexto escribía, repasos y recontextualizaciones.
- Correcciones posteriores: crédito UDELAR en la portada, foto de Freud sólo en la portada, formato para GitHub Pages.

## 4. Estructura del contenido

Orden exacto de la tabla de la cátedra (23 bloques, ids `b1`…`b23`):

**Parcial 1**
- Tema 1 · ¿Qué es el psicoanálisis? / Historia / Método / Histeria: `b1` *Estudios sobre la histeria* cap. 4 (1895), `b2` Carta 69 (1897).
- Tema 1 · Transferencia / Asociación libre / Atención flotante / Ética / Repetición: `b3` *Dinámica de la transferencia* (1912), `b4` *Consejos al médico* (1912), `b5` *Puntualizaciones sobre el amor de transferencia* (1915 [1914]), `b6` *Recordar, repetir y reelaborar* (1914).
- Tema 2 · Sexualidad / cuerpo erógeno: `b7` *Mis tesis…* (1906), `b8` *Tres ensayos* II y III (1905).
- Tema 2 · Primera teoría pulsional: `b9` *Pulsiones y destinos de pulsión* (1915).

**Parcial 2**
- Tema 3 · Síntoma: `b10` Conferencias 17, 18, 19 y 23 (1916-17), tratadas en profundidad con cuatro sub-scrollies.
- Tema 3 · Formaciones de compromiso: `b11` *Interpretación de los sueños* VI A-B-C (1900), `b12` *Psicopatología de la vida cotidiana* I y II (1901).
- Tema 4 · Primera tópica: `b13` *Interpretación de los sueños* VI D, I y VII (1900).
- Tema 4 · Represión, primera angustia: `b14` *La represión* (1915), `b15` Conf. 25 (1916-17).
- Tema 4 · Inconsciente: `b16` *Lo inconciente* (1915).
- Tema 4 · Narcisismo: `b17` *Introducción del narcisismo* (1914) + Conf. 26.
- Tema 4 · Segunda teoría pulsional: `b18` *Más allá del principio de placer* II, III, VI, VII (1920).
- Tema 4 · Segunda tópica: `b19` *El yo y el ello* (1923).
- Tema 4 · Edipo / identificaciones: `b20` *Psicología de las masas* VII (1921), `b21` *El sepultamiento del complejo de Edipo* (1924).
- Tema 4 · Segunda angustia: `b22` *Inhibición, síntoma y angustia* II, III, IV, VIII (1926) + *Nuevas conferencias* 31 y 32 (1933).
- Tema 5 · Pulsión y cultura: `b23` *El malestar en la cultura* (1930).

Secciones de apoyo: portada (`hero`), cómo usar, mapa del programa (tabla con enlaces), «Un programa que va y viene» (gráfico año × orden del programa), cuatro tesis + léxico Amorrortu con año de aparición de cada término, repasos `r1`…`r5`, «Cinco hilos» finales (`hilos`) y pie con fuentes.

### Anatomía de cada bloque

1. Encabezado: número, chips (año, tomo, tópico del programa), título.
2. **Dónde estamos** (contexto de época y de la obra) y **El problema** (la pregunta que el texto resuelve).
3. **Scrollytelling**: pasos de texto a un lado, diagrama SVG fijo al otro, que se arma paso a paso.
4. Recuadros: **Caso / observación**, **Anticipación** (concepto posterior, fechado), **Recontextualización** (cuando el programa salta en el tiempo), **Nota**, **Trampa**.
5. **Freud en sus palabras**: citas con marca ⚑ (literalidad confiable) o ≈ (fiel al sentido; verificar antes de entrecomillar).
6. **Trampas de examen**.
7. **Pregunta** con respuesta modelo desplegable (`<details>`).

Cifras: 23 bloques, 32 diagramas con scroll, 23 preguntas, ~20 anticipaciones, ~15 recontextualizaciones.

## 5. Decisiones de contenido y correcciones al material de entrada

Correcciones verificadas contra la estructura de los textos o con búsqueda web:

- *La interpretación de los sueños*, cap. VI: **C = «Los medios de figuración»**, **D = «El miramiento por la figurabilidad»**, I = elaboración secundaria. La guía confundía C y D.
- Fórmula de la masa («un objeto, uno y el mismo, en el lugar de su ideal del yo») está en el **cap. VIII** de *Psicología de las masas*, no en el VII.
- Ganancia primaria / secundaria de la enfermedad: **Conferencia 24**, no 23 (se menciona como complemento).
- Protofantasías (coito parental, seducción, castración) confirmadas en la Conf. 23.
- El banco de preguntas atribuía el principio de placer «al ello» en textos de 1900-1917 y describía mal el «esquema del peine»: se reemplazó por la serie P – Mn – Icc – Prec – M del cap. VII.
- «Padre, ¿no ves que estoy ardiendo?»: Freud no lo soñó ni analizó; se lo contó una paciente.
- Katharina: nota de 1924 que revela que el agresor era el padre.

Temporalidad (anticipaciones marcadas en el texto):

- Sin «sistema Icc» en 1895 (grupo psíquico separado, defensa).
- Edipo: Carta 71, no 69.
- Principio de placer / de realidad: 1911 (en 1900, «principio de displacer»).
- Organizaciones pregenitales oral y sádico-anal: agregado de 1915 a los *Tres ensayos*; **fase fálica: 1923**. El diagrama de la Conf. 23 de la cátedra rotula «etapa fálica»: se conservó con un asterisco y un aviso de anacronismo.
- Narcisismo 1914; ello/yo/superyó 1923; pulsión de muerte 1920; angustia señal 1926; masoquismo primario 1924.
- El «yo» de 1906-1917 no es la instancia de 1923.

Fuentes web usadas en la verificación: aacademica.org (Conf. 23 y 24, Conf. 17), ficha de cátedra UNLP de *Psicología de las masas*, Encyclopedia.com (*primal fantasies*). Detalle en la respuesta de la sesión; las fuentes primarias son los tomos de Amorrortu.

## 6. Diseño

- Paleta «papel de edición vienesa»: fondo `#f5f0e6`, tinta `#1f1b16`, acentos oxblood `--ox`, teal `--teal`, ocre `--ochre`, ciruela `--plum`, azul `--blue`. Parcial 1 = teal (`--p1`), Parcial 2 = oxblood (`--p2`).
- Tipografías (Google Fonts): **Fraunces** (títulos), **Source Serif 4** (cuerpo), **IBM Plex Sans** (etiquetas y diagramas). Sin conexión caen a Georgia / system-ui.
- Modo oscuro: automático por `prefers-color-scheme` y botón ◐ (se guarda en `localStorage`, con try/catch).
- Responsive: en ≤ 900 px el diagrama queda fijo arriba (50 vh) y los pasos pasan por debajo.
- Portada: retrato de Freud en marco de arco con filtro sepia suave y crédito.

## 7. Cómo funciona el código

Todo inline en `index.html`.

**Scrollytelling** (`.scrolly`):
```html
<div class="scrolly">            <!-- o class="scrolly flip" para diagrama a la izquierda -->
  <div class="steps">
    <div class="step"><div class="sc"><h5>1 · Título</h5><p>…</p></div></div>
    …
  </div>
  <div class="fig"><div class="frame">
    <svg viewBox="0 0 600 430">
      <g data-s="1">…aparece en el paso 1…</g>
      <path pathLength="1" class="lo draw" data-s="3" d="…"/>   <!-- se "dibuja" en el paso 3 -->
    </svg>
    <div class="cap">Pie del diagrama</div>
  </div></div>
</div>
```
- Un `IntersectionObserver` por scrolly activa el paso que cruza la franja central de la pantalla (en móvil, la franja inferior). Todo elemento del SVG con `data-s ≤ paso activo` recibe la clase `.on`.
- Clases útiles: `.up` (sube al aparecer), `.draw` + `pathLength="1"` (trazo animado), `.pulse`.
- **Regla:** el `data-s` máximo de un diagrama no puede superar la cantidad de `.step` del scrolly (si no, hay capas que nunca aparecen). Al cerrar la sesión: 32 scrollies, 0 desajustes.
- Vocabulario SVG: cajas `.box .boxs .bt .bo .bc .bp .bb`; líneas `.ln .lnd .lo .lt .lc .lp .lb`; texto `.ti .sm .xs .ser`; flechas `marker-end="url(#ar|#aro|#art|#arc|#arp|#arb)"` (definidas una sola vez al inicio del `<body>`).

**Barra de tiempo (header):** cada sección con `data-title` (y opcionalmente `data-year`, `data-parcial`) actualiza el año, mueve el punto en la regla 1890-1935, deja un «fantasma» en la posición anterior y muestra «↩ retrocede N años» / «→ avanza N años». El rótulo del año sale del primer `.chip.yr` de la sección.

**Índice:** se genera solo a partir de los elementos con `data-toc` (agrupa por `data-parcial` y `data-tema`).

**Agregar un bloque nuevo:** copiar un `<section class="bloque" id="bN" data-year="…" data-title="…" data-parcial="…" data-tema="…" data-toc="…">` existente y respetar la anatomía del punto 4.

## 8. Verificación realizada

- Balance de etiquetas HTML (parser de Python): 0 errores.
- Chrome headless controlado por DevTools (`doc/tools/cdp.mjs`): scroll real en escritorio (1400×900) y móvil (390×844), capturas de pasos intermedios, 0 errores de JavaScript.
- Todos los diagramas en estado final (`doc/tools/figs_preview.py`): se corrigieron ~15 solapamientos de texto.
- Corrección de un bug en móvil: el diagrama quedaba debajo de los pasos; ahora queda fijo arriba.

Reproducir:
```bash
python3 -I doc/tools/figs_preview.py
node doc/tools/cdp.mjs "file://$PWD/index.html" shot 1400 900 "b10:4200" "b13:2600"
node doc/tools/cdp.mjs "file://$PWD/index.html" mob 390 844 "b10:16500"
```
(`cdp.mjs` necesita Node ≥ 22 y `google-chrome`; el formato de cada argumento es `idDeSección:desplazamientoEnPx`.)

## 9. Publicación en GitHub Pages

Publicado en `https://pasquinell.github.io/clinica1_fund_PsA/` (repo `Pasquinell/clinica1_fund_PsA`, Pages desde `main` / `(root)`).

Configuración de la máquina (ya hecha, no tocar):

- `~/.ssh/config`: `Host github.com` usa `~/.ssh/id_ed25519_dynamicdata` (cuenta de trabajo **pasqui-dynamicdata**, organización `Dynamic-Data-Agency`). Es el **default**.
- `Host github-pasquinell` → `github.com` con `~/.ssh/id_ed25519_pasquinell` (cuenta personal **Pasquinell**).
- Git global: `pasqui-dynamicdata <pasqui@dynamicdata.agency>`, más un `includeIf "hasconfig:remote.*.url:git@github-pasquinell:**/**"` que carga `~/.gitconfig-pasquinell` (`Pasquinell <purbanir@gmail.com>`) en cualquier repo con remoto personal.

Por eso el remoto de este repo es:

```bash
git remote -v    # origin  git@github-pasquinell:Pasquinell/clinica1_fund_PsA.git
```

**No** usar `git@github.com:Pasquinell/...` ni HTTPS con token: entran con la cuenta de trabajo o fallan.

Actualizar el sitio:

```bash
git add . && git commit -m "..." && git push
```

Pages se actualiza solo en 1-2 minutos.

Proyecto nuevo personal (mismo esquema):

```bash
git init -b main
git remote add origin git@github-pasquinell:Pasquinell/<repo>.git
git config user.email          # debe mostrar purbanir@gmail.com antes de commitear
git add . && git commit -m "..." && git push -u origin main
```

(Crear antes el repo vacío en github.com logueado como Pasquinell.)

Comprobar cuentas: `ssh -T git@github.com` → «Hi pasqui-dynamicdata!»; `ssh -T git@github-pasquinell` → «Hi Pasquinell!».

Nota: `doc/` y `prompt_tcc.md` quedan públicos si se suben. Para excluirlos, agregarlos al `.gitignore`.

## 10. Pendientes y límites conocidos

- Citas marcadas ≈ (en especial la Conf. 26): verificar literalidad contra el tomo.
- Textos fuera de la bibliografía básica que se mencionan como contexto: *Sobre la iniciación del tratamiento* (1913), Conf. 21, 22 y 24, caps. IV-V de *Más allá*, *Duelo y melancolía*, *La organización genital infantil*. Se señalan cada vez.
- Tamaño de letra de los diagramas en móvil: legible pero pequeño.
- Las fuentes dependen de Google Fonts.
