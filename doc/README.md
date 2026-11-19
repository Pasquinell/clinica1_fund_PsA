# Documentación del proyecto · Clínica I: Freud en el orden del programa

Registro de qué se construyó, con qué criterios, qué decisiones se tomaron y cómo seguir editándolo. Pensado para retomar el trabajo en otra sesión (humana o con Claude) sin tener que reconstruir el contexto.

---

## 1. Qué es

Un sitio de una sola página (`index.html`) con un **scrollytelling** pedagógico sobre la bibliografía básica del curso **Clínica I: Fundamentos psicoanalíticos** (Facultad de Psicología, UDELAR, Uruguay, 2026). El Parcial 1 y los textos fuera de parciales se leen en el **orden del programa de la cátedra** (tema → tópico → texto). El **Parcial 2 se lee en orden cronológico** (rama `parcial2-cronologico`, nov. 2026), en tres épocas. Los diagramas se arman a medida que se avanza.

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
| `doc/tools/check.py` | Chequeos estáticos (copiado de `tcc_terapia`): balance de etiquetas, `data-s` vs pasos, ids duplicados, `#enlaces` rotos, imágenes. |
| `fuentes/` | Material de la cátedra y bibliografía con copyright (imagen de temas del 2.º parcial, guía de lectura de *La interpretación de los sueños*, muestra del *Diccionario* de Laplanche-Pontalis). **Ignorado por git; no publicar.** |


Durante la construcción el HTML se armó concatenando 8 partes en un directorio temporal; esas partes **ya no existen**. Desde ahora se edita `index.html` directamente.

## 3. Pedido original (resumen)

- HTML (no artefacto de Claude), archivo local, luego hosteable en GitHub.
- Scrollytelling dinámico; diagramas y conceptos que **aparezcan de a poco** y tengan sentido en el relato.
- Respetar el orden de las dos tablas de la cátedra (tema → tópico), aunque vaya y venga en el tiempo.
- Parcial 1: de «¿Qué es el psicoanálisis?» a «Primera teoría pulsional». Parcial 2: de «Síntoma» a «Relación entre pulsión y cultura».
- Traducción Amorrortu (Etcheverry): pulsión, investidura, sepultamiento, etc.
- No confiar 100 % en los `.md` provistos; las Conferencias 17, 18, 19 y 23 debían tratarse con más profundidad.
- El diagrama de la Conf. 23 (series complementarias / formación de síntoma) como modelo de buen diagrama. Fuente: video del canal de YouTube *Lo inconsciente* (ver § 5), no la cátedra.
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

**Parcial 2** (según la lista de temas del 2.º parcial 2026, `fuentes/tesxtos_segundo_parcial.jpeg`). Se presenta en **orden cronológico**, no en el del programa. Los ids y los números de bloque (`.bnum`) siguen siendo los del programa: el glosario, el mapa y `#mapa2` enlazan por id.
- Época 1 · 1900-1901 (encabezado `#tema3`, reutiliza `header.tema-h`): `b11` *Interpretación de los sueños* VI A-B-C (1900, Tema 3), `b13` VI D, I y VII (1900, Tema 4 · Primera tópica), `b12` *Psicopatología de la vida cotidiana* I y II (1901, Tema 3).
- Puente `call rec` 1900 → 1901 y 1901 → 1915.
- Época 2 · 1915 (`#tema4`, con tarjetas `.rgrid` de lo que pasó entre 1905 y 1915): `b14` *La represión* (Tema 4), `b16` *Lo inconciente* (Tema 4).
- Época 3 · 1915-1917 (`#epoca3`): `cs` Conferencias 7, 9, 11 y 14 (1916 [1915-16], Tema 3, sin scrolly), `b10` Conferencias 17, 18, 19 y 23 (1916-17, Tema 3, cuatro sub-scrollies), puente 23ª → 25ª, `b15` Conf. 25 (1916-17, Tema 4).
- `r4` Repaso del Tema 3 (ahora al final, `data-year="1917"`), `r5` Repaso integral.
- En el índice, `data-tema` de los bloques del Parcial 2 es la época, no el tema. Cada encabezado de época dice a qué tema del programa pertenece cada bloque. `#como-usar`, `#mapa` y `#vaivien` siguen describiendo el orden del programa y avisan que el Parcial 2 se lee cronológicamente.
- `b13` ampliado (nov. 2026): en `.lectura`, «Por qué cambia la pregunta», el sueño del niño que arde con la lectura de Freud en tres pasos, Fechner en VII-B, y los dos inconscientes en VII-F. Se agregaron una «Nota · quién era Fechner» y una Anticipación (Fechner en 1920, Lacan y «la otra escena»).
- Mapa conceptual del Parcial 2: `#mapa2`, después de `r5`. Scrolly de 8 pasos (svg `.cmap`, viewBox 640×480, 13 nodos `.cm-n` con `data-k`/`data-n` vecinos/`data-l` bloques/`data-d` descripción; aristas `.cm-e` con `data-a`/`data-b`). En el último paso, clic o Enter sobre un nodo resalta sus conexiones y llena `.cmap-info` (oculto en móvil). Debajo, `details.fold` con el mapa en texto y tres recorridos de parcial. El JS va en un `<script>` propio al final del `<body>`.

**Fuera de parciales** (`data-parcial="3"`, color `--p3`; divisor `#fuera` y encabezado `#tema4b`)
- Tema 4 · Narcisismo: `b17` *Introducción del narcisismo* (1914) + Conf. 26.
- Tema 4 · Segunda teoría pulsional: `b18` *Más allá del principio de placer* II, III, VI, VII (1920).
- Tema 4 · Segunda tópica: `b19` *El yo y el ello* (1923).
- Tema 4 · Edipo / identificaciones: `b20` *Psicología de las masas* VII (1921), `b21` *El sepultamiento del complejo de Edipo* (1924).
- Tema 4 · Segunda angustia: `b22` *Inhibición, síntoma y angustia* II, III, IV, VIII (1926) + *Nuevas conferencias* 31 y 32 (1933).
- Tema 5 · Pulsión y cultura: `b23` *El malestar en la cultura* (1930).

Secciones de apoyo: portada (`hero`), cómo usar, mapa del programa (tabla con enlaces; filas `p1`, `p2`, `p3`), «Un programa que va y viene» (gráfico año × orden del programa, con corte «Fuera →»), cuatro tesis + léxico Amorrortu con año de aparición de cada término, repasos `r1`…`r5`, «Cinco hilos» finales (`hilos`), **glosario** (`#glosario`) y pie con fuentes.

### Anatomía de cada bloque

1. Encabezado: número, chips (año, tomo, tópico del programa), título.
2. **Dónde estamos** (contexto de época y de la obra) y **El problema** (la pregunta que el texto resuelve).
3. **Scrollytelling**: pasos de texto a un lado, diagrama SVG fijo al otro, que se arma paso a paso.
4. Recuadros: **Caso / observación**, **Anticipación** (concepto posterior, fechado), **Recontextualización** (cuando el programa salta en el tiempo), **Nota**, **Trampa**.
5. **Freud en sus palabras**: citas con marca ⚑ (literalidad confiable) o ≈ (fiel al sentido; verificar antes de entrecomillar).
6. **Trampas de examen**.
7. **Pregunta** con respuesta modelo desplegable (`<details>`).

Complementos agregados en nov. 2026 (no reemplazan nada):

- Al inicio de cada bloque, después del encabezado: `.lectura` con **Primera lectura** (resumen narrativo del texto, con sus ejemplos y hallazgos), `.nucleo` (**el texto en un párrafo**: qué introduce y cómo se relaciona) e `.ideas` (bullets).
- Al final de cada bloque: `.desarrollo` con 3-4 **preguntas de desarrollo** (`details.preg.dev`) y respuesta ideal de parcial; el último párrafo (`p.clave`) dice qué evalúa la pregunta y el error típico.
- **Preguntas de orientación** (`#orientacion`, nov. 2026): sección después de `#mapa2`, última del Parcial 2 (`data-tema="Repaso"`). Una guía por texto del parcial, en orden cronológico, 150 `details.preg.dev`:
  - **Guías oficiales de la cátedra** (`fuentes/preguntas-oficiales-de-orientacion/`), respondidas en el orden de cada guía: *La interpretación de los sueños* 1-11 (`#po-ids-a`) y 12-48 (`#po-ids-b`), Conf. 17 (`#po-c17`, 9), 18 (`#po-c18`, 11), 19 (`#po-c19`, 13), 23 (`#po-c23`, 15) y 25 (`#po-c25`, 13). Las 48 de IdS estaban antes en `b11` y `b13`; se movieron y en su lugar quedó una `call nota` con enlace (después se corrigió en ellas una cita de la 17ª; ver § 5).
  - **Guías del sitio** (no oficiales; el `h4` dice «guía del sitio») para los textos sin guía de la cátedra: *Psicopatología* I-II (`#po-psico`, 9), *La represión* (`#po-rep`, 10), *Lo inconciente* (`#po-icc`, 10) y Conf. 7, 9, 11 y 14 (`#po-c7`, 12). No repiten las preguntas de desarrollo de `b12`, `b14`, `b16` y `cs`.
  - Las 109 preguntas de las guías oficiales llevan al comienzo del `<summary>` una etiqueta `span.po-of` («★ Oficial»); las de las guías del sitio no. La nota «Cómo usarlas» explica la etiqueta.
  - Cada guía es un `.desarrollo.guia` con `p.po-obj` (objetivo), `h5.po-sub` (apartados) y `p.clave` solo en la pregunta de integración. Arriba, `nav.po-idx` con enlaces a cada guía.
  - Cotejo: Conf. 17-18 y las cuatro guías del sitio, contra Amorrortu (t. VI, XIV, XV y XVI, PDF de psicopsi.com, no incluidos en el repo); Conf. 19 y 23, contra el texto alemán; Conf. 25, contra fuentes secundarias y puntos sueltos del t. XVI. Las citas cotejadas palabra por palabra llevan ⚑; lo no cotejado, ≈.
- **Preguntas integradoras** dentro de los repasos: `r2` (Tema 1), `r3` (Parcial 1), `r4` (Tema 3), `r5` (Parcial 2), `hilos` (fuera de parciales).
- **Glosario** final basado en Laplanche y Pontalis. El PDF disponible es solo una muestra (pp. 23-44, entradas A): las entradas cotejadas con ella llevan ⚑; el resto (≈) son paráfrasis según el *Diccionario*, no cotejadas con el texto.

Cifras: 23 bloques, 32 diagramas con scroll, 23 preguntas, ~20 anticipaciones, ~15 recontextualizaciones.

## 5. Decisiones de contenido y correcciones al material de entrada

Correcciones verificadas contra la estructura de los textos o con búsqueda web:

- La definición «el propósito a que sirve, y su ubicación dentro de una serie psíquica» es de la **3ª conferencia** (actos fallidos, t. XV), no de la 17ª, que no forma parte de la bibliografía del parcial. Se quitó de `b10`, `r4`, `#mapa2` y las respuestas de la 17ª. En su lugar se usan las fórmulas de las propias conferencias, cotejadas en el t. XVI: el síntoma «es rico en sentido y se entrama con el vivenciar del enfermo» y «poseen un sentido, lo mismo que las operaciones fallidas y los sueños, y […] están en vinculación íntima con el vivenciar del paciente» (17ª); el «desde dónde» y el «hacia dónde» o «para qué» del síntoma (18ª, ahora la cita ⚑ de `b10`). La pregunta 3 de `r4` usa la fórmula de la 18ª.
- `b15`, paso 4: se quitó «como el vino en vinagre» (texto y rótulo del diagrama). No aparece en el texto de la 25ª.
- `cs`: el sueño del beso del tío en el automóvil («autoerotismo») es de la **15ª** conferencia, no de la 7ª. Se reemplazó por el ejemplo del «canal» y el Paso de Calais (7ª, ej. b).
- `b16`: la cita es «en alto grado lagunosos» (sin «muy»).
- **Cotejo de citas ⚑ contra Amorrortu (nov. 2026)**, con los t. VI, XIV, XV y XVI en PDF (psicopsi.com, no incluidos en el repo). Varias citas ⚑ venían de otra traducción y se reemplazaron por el texto de Amorrortu:
  - 19ª: la imagen es «un gran **vestíbulo** donde las mociones anímicas pululan como individuos», no «antesala». Se cambió «antesala» por «vestíbulo» en todo lo que se refiere a la 19ª (texto, diagrama de `b10`, repasos y respuestas). Coincide con el término de la guía de la cátedra.
  - 23ª: «Ya sabemos que los síntomas neuróticos son el resultado de un conflicto que se libra en torno de una nueva modalidad de la satisfacción pulsional. Las dos fuerzas que se han enemistado vuelven a coincidir en el síntoma; se reconcilian, por así decir, gracias al compromiso de la formación de síntoma». La de la fantasía como reserva: «La creación del reino de la fantasía dentro del alma halla su cabal correspondiente en la institución de “parques naturales”, de “reservas”…».
  - 25ª: «la libido de las mociones pulsionales reprimidas se muda en angustia» **no está** en Amorrortu; la tarjeta usa ahora «el destino más inmediato de ese afecto es el de ser mudado en angustia…». «Esta angustia es, entonces, la moneda corriente por la cual se cambian o pueden cambiarse todas las mociones afectivas cuando el correspondiente contenido de representación ha sido sometido a represión». Nacimiento: «el acto del nacimiento es la fuente y el modelo del afecto de angustia». Las paráfrasis de esas frases en el texto pasaron de ⚑ a ≈.
  - `b14`: «…su esencia consiste en rechazar algo de la conciencia y mantenerlo alejado de ella» y «No tenemos que imaginarnos el proceso de la represión como un acontecer que se consumaría de una sola vez […]. No, sino que la represión exige un gasto de fuerza constante».
  - `b16`: «Resumamos: ausencia de contradicción, proceso primario…» (no «Exención mutua»). La cita «El psicoanálisis no puede situar la esencia de lo psíquico en la conciencia…» es de *El yo y el ello* (1923), no de *Lo inconciente*: pasó a ≈.
  - `b12`: «Ha ocurrido, pues, un olvido motivado; una represión» no está en el texto; se reemplazó por «Por tanto, yo quise olvidar algo, había reprimido algo».
  - Las paráfrasis sin comillas marcadas ⚑ que no se cotejaron pasaron a ≈.
  - No se cotejaron las citas de *La interpretación de los sueños* (`b11`, `b13` y las 48 respuestas de `#po-ids-a`/`#po-ids-b`; faltan los t. IV y V), ni las de Parcial 1 y «Fuera de parciales».

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
- Organizaciones pregenitales oral y sádico-anal: agregado de 1915 a los *Tres ensayos*; **fase fálica: 1923**. El diagrama de la Conf. 23, tomado del video [«Conferencia 23. Los caminos de la formación de síntoma. Sigmund Freud»](https://www.youtube.com/watch?v=4akbGVw21t4) del canal de YouTube *Lo inconsciente* (no es material de la cátedra), rotula «etapa fálica»: se conservó con un asterisco y un aviso de anacronismo.
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
- Glosario: cotejar las entradas ≈ contra el *Diccionario* completo de Laplanche-Pontalis.
- Bloque `cs` (Conf. 7, 9, 11, 14): sin diagrama ni citas literales; los resúmenes son paráfrasis.
- `b22`: el sitio ubica «inhibición ≠ síntoma» en el cap. II de *Inhibición, síntoma y angustia*; probablemente esté en el cap. I. Verificar en el tomo XX.
- Ejemplos de los complementos (nov. 2026) citados de memoria, a cotejar: sueño de las entradas de teatro (Conf. 7), «servicios de amor» (Conf. 9), Silberer y Maury (IdS VI), el sueño de la madre con los picos de pájaro (VII-D), la paciente que desea ser besada (Estudios, cap. 4), el chiste del pastor y el agente de seguros (Puntualizaciones), el niño que dice ser el gatito (Masas VII), Tancredo y Clorinda (Más allá III).
- Datos del Parcial 2 cronológico verificados en la web (nov. 2026): el niño que arde (preámbulo del cap. VII, antes de A; texto en psychclassics.yorku.ca: paciente que lo oyó en una conferencia, el anciano, la vela, «paths lead into darkness», Freud vuelve al sueño en B y C), la cita de Fechner en el cap. I-E, y los doce ensayos metapsicológicos de 1915 (cinco publicados, el resto perdido; borrador hallado en 1983). Sin verificar contra el tomo (marcados ≈ o redactados con cautela): la redacción Amorrortu de la frase de Fechner; «poca repercusión» del libro de los sueños; los detalles del sueño de Maury (Terror, tribunal, cabecera de la cama sobre el cuello); Revisión posterior (SE V) confirmó: las inscripciones de *Fliegende Blätter* (VI-I), la palabra vulgar aprendida de Philipp en el sueño de los picos de pájaro, que las tres regresiones son un párrafo de 1914, los sueños punitorios agregado de 1919, Silberer agregado posterior (1909 su publicación), y que la frase «guardianes del dormir» es del cap. V, C; Lacan y «la otra escena» (≈). Fechner en *Más allá* (principio de tendencia a la estabilidad) sí está confirmado.
- Ortografía: «inconsciente» en la prosa; «inconciente» sólo en citas de Amorrortu y en el título *Lo inconciente*.
