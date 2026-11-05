# IusHistorIA

Sistema de aprendizaje de la asignatura **1193 Historia del Derecho** (Grado en Derecho, Universidad Miguel Hernández de Elche), construido a partir de su Guía Docente 2026-2027. Aplicación web de un solo fichero: funciona en el navegador, sin servidor ni cuentas.

**Usar la app:** https://fborrasumh.github.io/iushistoria/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23830365.svg)](https://doi.org/10.5281/zenodo.23830365)

**Idiomas:** español (por defecto), inglés y portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

- **Diagnóstico inicial**: una pregunta por cada uno de los 10 resultados de aprendizaje (RA) de la guía.
- **Práctica adaptativa**: un banco de 63 ítems (opción múltiple y ordenación cronológica; 13 de nivel «evaluar»), cada uno vinculado a un RA, a una unidad y a un nivel de la taxonomía de Bloom revisada. El código corrige, actualiza un modelo de dominio por RA (tipo Rasch/Elo, con olvido) y elige la siguiente actividad con reglas deterministas: repasos vencidos (cajas de Leitner, con prioridad para los fallos cometidos con mucha seguridad), RA más flojo, intercalado de temas y mantenimiento periódico. Opcionalmente, el estudiante indica el tema que se ve en clase (dos de cada tres preguntas salen de él) y la fecha del examen (cuenta atrás). Encima de cada pregunta se explica por qué toca.
- **Seguridad y calibración**: antes de comprobar, el estudiante puede indicar su seguridad (poca, media, mucha). En el progreso ve si su seguridad se corresponde con sus aciertos.
- **Comentario de texto**: doce textos histórico-jurídicos (Fuero Real, Partidas I, 2, 4, Ordenamiento de Alcalá, Decreto de Nueva Planta de 1707, decreto de 1711 para Aragón, Nueva Planta de Cataluña de 1716, Constitución de 1812, constituciones de 1845, 1869, 1876 y 1931, art. 258 de 1812), con enlace a una edición consultable cuando la hay y una estructura guiada (clasificación, contexto, análisis, valoración). El código cuenta palabras, detecta conceptos clave y comprueba que las citas del estudiante son literales.
- **Simulacro de preguntas de desarrollo**: seis preguntas de un banco de 13 y se eligen cuatro, como en el examen (70 % de la nota), con una rúbrica orientativa visible. Se aplica la regla de la guía: una respuesta en blanco impide aprobar.
- **Comentario de la IA (opcional)**: feedback formativo sobre comentarios y respuestas. Cada cita que la IA hace de la redacción del estudiante se verifica por código (⚠ si no existe); si la IA dice que falta un concepto que sí aparece, gana el código; las frases en las que la IA pone nota se eliminan.
- **Progreso**: dominio estimado por RA, repasos pendientes, copia de seguridad (JSON), CSV y un fichero anónimo y voluntario para el profesorado.
- **Cronología** del siglo XI a 2016, con autoevaluación (ocultar los años).
- **Laboratorio** (siete actividades, corregidas por código):
  - *El mismo pleito en cinco épocas*: el estudiante hace de juez en 1350, 1510, 1690, 1720 y 1890 y aplica la fuente y el orden de prelación de cada momento.
  - *Arqueología de una norma vigente*: ordena las capas históricas del art. 149.1.8.ª CE o del art. 1 CC, relaciona qué aportó cada una y escribe su interpretación.
  - *Mapa vivo de la España jurídica*: qué derecho regía en cada territorio en 1500, 1720, 1890 y hoy, con preguntas sobre Elche y la Comunitat Valenciana.
  - *Detective de anacronismos*: respuestas de examen con errores sembrados que hay que localizar.
  - *¿De qué constitución es?*: identificar artículos por sus huellas y construir un cuadro comparativo.
  - *Cortes en el aula*: modo para proyectar en clase con votación, discusión por parejas y segunda votación (instrucción entre pares), sin servidor; guarda recuentos sin nombres y los exporta a CSV.
  - *Entrevista en las Cortes de Cádiz* (IA opcional): dos diputados **ficticios**, uno liberal y otro absolutista; las citas que hacen se verifican contra los textos de la app.
- **Panel del profesorado**: matriz de alineación RA–unidades–actividades, analítica de ítems a partir de los ficheros anónimos (dificultad, discriminación biserial-puntual, distractores que nadie elige) y exportación del banco a Moodle (GIFT y XML) y a Word.

Sin clave y sin conexión funcionan el diagnóstico, la práctica, la cronología, el progreso, el laboratorio (salvo la entrevista) y el panel del profesorado. Hay un ejemplo de comentario con feedback precalculado que no usa la IA.

## Cómo se usa la IA

Con la propia clave de OpenAI, Google Gemini o Anthropic Claude, que se guarda solo en el navegador. Cada persona paga su propio uso. La IA responde en el idioma elegido; las citas se dejan en su idioma original para poder verificarlas.

## Privacidad

Todo (respuestas, comentarios, progreso, clave) se guarda en el navegador (IndexedDB y localStorage). Solo si se pide feedback a la IA salen hacia el proveedor el texto comentado o la pregunta y la redacción del estudiante, con correos, DNI/NIE y teléfonos enmascarados. Antes del primer envío de cada sesión se muestra una muestra de lo que sale y se pide confirmación. El fichero anónimo para el profesorado lleva un seudónimo aleatorio y solo las respuestas a la práctica (ítem, RA, acierto, opción, tiempo y seguridad declarada); no incluye nombres, textos ni claves.

## Alcance

- El mapa es un esquema, no a escala, y agrupa territorios. El laboratorio resume la prelación de cada época (por ejemplo, la ley 1 de Toro) sin reproducir su texto literal.
- En la entrevista, los diputados son personajes inventados y sus opiniones son una interpretación de la IA: solo las citas entre «comillas» se comprueban.
- Los textos históricos son fragmentos; los constitucionales y los de la Edad Moderna llevan la ortografía modernizada, y los medievales, la grafía de la edición citada.
- El dominio estimado es una orientación, no una nota. Con pocas respuestas es inestable.
- La detección de conceptos busca términos y sinónimos (en es/en/pt); no evalúa si se explican bien. No es una plantilla de corrección.
- La IA puede equivocarse en datos históricos; sus «posibles errores» deben comprobarse en el manual.
- La analítica de ítems con pocos estudiantes es poco fiable. La app genera datos, pero no produce por sí sola evidencia publicable: para investigar hacen falta la aprobación del comité de ética (en la UMH, la Oficina de Evaluación de Proyectos), el consentimiento informado y el RGPD.
- Accesibilidad: sin infracciones WCAG 2.2 A/AA detectadas por axe-core en las 15 pantallas y 3 idiomas, y la práctica se puede completar solo con el teclado.
- No hay integración LTI ni inicio de sesión institucional (necesitarían un servidor).

## Adoptarla en otra asignatura o universidad

Todo el contenido está en `src/curriculum.js` (RA literales de la guía, unidades, evaluación, ítems, textos, preguntas de desarrollo y cronología). Para otra asignatura basta con cambiar ese fichero y ejecutar `python3 build.py`. La lógica (`src/nucleo.js`) se prueba con `node tests/nucleo_test.js` y la interfaz con `python3 tests/app_test.py`.

## Ciencia del aprendizaje en la que se basa

Práctica de recuperación (Roediger y Karpicke, 2006, doi:10.1111/j.1467-9280.2006.01693.x), práctica espaciada (Cepeda et al., 2006, doi:10.1037/0033-2909.132.3.354), técnicas de estudio eficaces (Dunlosky et al., 2013, doi:10.1177/1529100612453266), feedback (Hattie y Timperley, 2007, doi:10.3102/003465430298487), corrección de los errores cometidos con seguridad (Butterfield y Metcalfe, 2001, doi:10.1037/0278-7393.27.6.1491), instrucción entre pares (Crouch y Mazur, 2001, doi:10.1119/1.1374249), alineamiento constructivo (Biggs, 1996, doi:10.1007/BF00138871) y taxonomía de Bloom revisada (Krathwohl, 2002, doi:10.1207/s15430421tip4104_2).

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche), José Antonio Pérez Juan (Universidad Miguel Hernández de Elche) y Sara Moreno Tejada (Universidad Miguel Hernández de Elche).

A partir de la Guía Docente 2026-2027 de la asignatura 1193 Historia del Derecho (Grado en Derecho, UMH), de la que son responsables José Antonio Pérez Juan y Sara Moreno Tejada.

Roles (CRediT): Fernando Borrás Rocher: conceptualización, software, metodología. José Antonio Pérez Juan y Sara Moreno Tejada: recursos (guía docente y contenidos de la asignatura).

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) · José Antonio Pérez Juan [0000-0002-9973-683X](https://orcid.org/0000-0002-9973-683X) · Sara Moreno Tejada [0000-0003-3154-7730](https://orcid.org/0000-0003-3154-7730)

## Cómo citar

Borrás Rocher, F., Pérez Juan, J. A. y Moreno Tejada, S. (2026). *IusHistorIA* (v1.0.0) [Software]. DOI: [10.5281/zenodo.23830365](https://doi.org/10.5281/zenodo.23830365)

## Licencia

MIT. Véase [LICENSE](LICENSE).
