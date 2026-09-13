# VECES

Cuántas veces más vas a ver a la gente que quieres.

Una calculadora interactiva del tiempo compartido que os queda. Metes tu edad, la
edad de las personas que te importan y cada cuánto os veis de verdad, y sale un
número: cuántos encuentros quedan, cuántas semanas enteras suman, y cuánto
cambia si subes la frecuencia.

Hecho por **Kai**.

---

## Cómo funciona

Un solo archivo HTML. Sin dependencias, sin build, sin servidor, sin base de
datos. Abres `index.html` en un navegador y funciona.

Todo el cálculo ocurre en el navegador. No se envía nada a ningún sitio y no se
guarda nada: al cerrar la pestaña desaparece.

### El cálculo

- Horizonte de referencia: **90 años = 4.680 semanas** (una casilla por semana).
- Semanas compartidas restantes = `min(90 − tu edad, 90 − su edad) × 52`
- Encuentros restantes = `frecuencia anual × años compartidos`
- **Una casilla = 7 encuentros = una semana entera juntos**, porque siete
  encuentros equivalen a los días de una semana de contacto.

Son medias de población. No es una predicción de nadie en concreto.

### Lo que hay dentro

- Gráfico de reparto del tiempo por edad, con marcador arrastrable, reproducción
  automática de una vida entera y aislamiento de series.
- Rejilla de vida en semanas en `<canvas>`, que **se reorienta según el
  dispositivo**: años en horizontal en pantalla ancha, años en vertical por
  debajo de 620 px.
- Vista desde la perspectiva de la otra persona.
- Simulador de rescate con sliders en vivo.
- Generador de mensajes con descarga de `.ics` para bloquear la fecha.
- Banda sonora **generativa** compuesta con la Web Audio API (Am–F–G–Em, pads,
  bajo, campanas aleatorias). Sin archivos de audio.
- 8 idiomas: castellano, català, English, français, Deutsch, italiano, 日本語, 中文.

---

## Editar los textos

Todos los textos están en un único objeto `window.I18N` al principio del
archivo, ordenado alfabéticamente y con un idioma por bloque. Para cambiar una
frase, busca su clave y cambia el valor.

```js
"es": {
  "gTitle": "Puede que no te guste el resultado.",
  "in3s":   "Ahora tú, {n}. Vamos a restar lo que ya has gastado...",
}
```

Llaves disponibles dentro de los textos:

| Llave | Significado            | Llave | Significado                 |
|-------|------------------------|-------|-----------------------------|
| `{n}` | nombre del usuario     | `{p}` | nombre de la otra persona   |
| `{a}` | edad de la otra persona| `{s}` | semanas compartidas         |
| `{c}` | semanas juntos         | `{m}` | número de encuentros        |
| `{r}` | todo el tiempo seguido | `{y}` | años                        |
| `{w}` | semanas                | `{u}` | unidad humana (cafés, cenas)|

Claves por grupo:

- `sec0`–`sec7`: nombres de las secciones de la barra superior.
- `in2t`/`in2s` … `in7t`/`in7s`: título y cuerpo de cada pausa entre pantallas.
- `ph0n`–`ph5n` y `ph0r`–`ph5r`: nombre y lectura de cada etapa del gráfico.
- `rf1`–`rf5`: las frases del cierre.
- `frq_*`: las ocho frecuencias. `rel_*`: los vínculos. `unit_*`: la unidad
  humana de cada vínculo. `ser_*`: las series del gráfico.
- `mw_*` / `md_*`: plantillas de mensaje, tono cálido y tono directo.

**Añadir un idioma:** copia el bloque `"es"` entero, cámbiale la clave a tu
código de idioma, traduce los valores, y añade el código a `LANGS` y una bandera
SVG a `FLAG` en el segundo `<script>`.

---

## Tu propia música

Si prefieres una pista en vez de la partitura generativa, pon un archivo llamado
`ambient.mp3` junto al HTML. La web lo detecta sola y lo reproduce en bucle.

Usa solo música de la que tengas los derechos o con licencia libre.

---

## Fuentes de los datos

Las curvas de reparto del tiempo están aproximadas a la forma de:

- [American Time Use Survey](https://www.bls.gov/tus/) — Bureau of Labor
  Statistics (EE. UU.)
- [Time Use](https://ourworldindata.org/time-use) — Our World in Data

---

## Créditos

La experiencia original que inspira este proyecto es **Kairós Project**, de
**@javiyawe**:

- Instagram: [@javiyawe](https://www.instagram.com/javiyawe)
- Sus proyectos: [links.javiyawe.es](https://links.javiyawe.es/)

Si te ha gustado la idea, la idea es suya. Ve a verle.

**Esta versión está escrita desde cero por Kai.** Código, textos, diseño,
paleta, tipografía, sonido y estructura son propios. No reutiliza código ni
textos del original: es un tratamiento distinto de la misma pregunta, con
mecánicas añadidas (rejilla que se reorienta según el dispositivo, banda sonora
generativa, unidades humanas por vínculo, exportación de calendario, ocho
idiomas).

La idea más amplia de contar una vida en semanas viene de una tradición larga:
los cuadernos *life in weeks* y el ensayo
[The Tail End](https://waitbutwhy.com/2015/12/the-tail-end.html) de Tim Urban.

---

## Licencia

Código y textos bajo licencia MIT — ver [LICENSE](LICENSE).

Los datos enlazados arriba pertenecen a sus respectivas fuentes. Si añades
música o imágenes, comprueba que puedes licenciarlas antes de subirlas.
