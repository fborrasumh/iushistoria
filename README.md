# IusHistorIA

Sistema de aprendizaje de la asignatura **1193 Historia del Derecho** (Grado en Derecho, Universidad Miguel Hernández de Elche), construido a partir de su Guía Docente 2026-2027. Aplicación web de un solo fichero: funciona en el navegador, sin servidor ni cuentas.

**Usar la app:** https://fborrasumh.github.io/iushistoria/

**Idiomas:** español (por defecto), inglés y portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

- **Diagnóstico inicial**: una pregunta por cada uno de los 10 resultados de aprendizaje (RA) de la guía.
- **Práctica adaptativa**: un banco de 53 ítems (opción múltiple y ordenación cronológica), cada uno vinculado a un RA, a una unidad y a un nivel de la taxonomía de Bloom revisada. El código corrige, actualiza un modelo de dominio por RA (tipo Rasch/Elo, con olvido) y elige la siguiente actividad con reglas deterministas: repasos vencidos (cajas de Leitner), RA más flojo, intercalado de temas y mantenimiento periódico. Encima de cada pregunta se explica por qué toca.
- **Comentario de texto**: siete textos histórico-jurídicos (Constitución de 1812, Decreto de Nueva Planta de 1707, constituciones de 1845, 1869, 1876 y 1931, art. 258 de 1812), con una estructura guiada (clasificación, contexto, análisis, valoración). El código cuenta palabras, detecta conceptos clave y comprueba que las citas del estudiante son literales.
- **Simulacro de preguntas de desarrollo**: seis preguntas de un banco de 12 y se eligen cuatro, como en el examen (70 % de la nota). Se aplica la regla de la guía: una respuesta en blanco impide aprobar.
- **Comentario de la IA (opcional)**: feedback formativo sobre comentarios y respuestas. Cada cita que la IA hace de la redacción del estudiante se verifica por código (⚠ si no existe); si la IA dice que falta un concepto que sí aparece, gana el código; las frases en las que la IA pone nota se eliminan.
- **Progreso**: dominio estimado por RA, repasos pendientes, copia de seguridad (JSON), CSV y un fichero anónimo y voluntario para el profesorado.
- **Cronología** con autoevaluación (ocultar los años).
- **Panel del profesorado**: autopsia de la guía docente, matriz de alineación RA–unidades–actividades con reescrituras medibles de los RA, analítica de ítems a partir de los ficheros anónimos (dificultad, discriminación biserial-puntual, distractores que nadie elige) y exportación del banco a Moodle (GIFT y XML) y a Word.

Sin clave y sin conexión funcionan el diagnóstico, la práctica, la cronología, el progreso y el panel del profesorado. Hay un ejemplo de comentario con feedback precalculado que no usa la IA.

## Cómo se usa la IA

Con la propia clave de OpenAI, Google Gemini o Anthropic Claude, que se guarda solo en el navegador. Cada persona paga su propio uso. La IA responde en el idioma elegido; las citas se dejan en su idioma original para poder verificarlas.

## Privacidad

Todo (respuestas, comentarios, progreso, clave) se guarda en el navegador (IndexedDB y localStorage). Solo si se pide feedback a la IA salen hacia el proveedor el texto comentado o la pregunta y la redacción del estudiante, con correos, DNI/NIE y teléfonos enmascarados. Antes del primer envío de cada sesión se muestra una muestra de lo que sale y se pide confirmación. El fichero anónimo para el profesorado lleva un seudónimo aleatorio y solo las respuestas a la práctica (ítem, RA, acierto, opción, tiempo); no incluye nombres, textos ni claves.

## Límites

- **El banco de preguntas, los conceptos clave y las preguntas de desarrollo son un borrador** redactado a partir de la guía docente y **pendiente de revisión por el profesorado** antes de usarse para evaluar.
- Los textos históricos llevan la ortografía modernizada y algunos son fragmentos: hay que cotejarlos con la edición que use la asignatura.
- El dominio estimado es una orientación, no una nota. Con pocas respuestas es inestable.
- La detección de conceptos busca términos y sinónimos (en es/en/pt); no evalúa si se explican bien. No es una plantilla de corrección.
- La IA puede equivocarse en datos históricos; sus «posibles errores» deben comprobarse en el manual.
- La analítica de ítems con pocos estudiantes es poco fiable. La app genera datos, pero no produce por sí sola evidencia publicable: para investigar hacen falta la aprobación del comité de ética (en la UMH, la Oficina de Evaluación de Proyectos), el consentimiento informado y el RGPD.
- Accesibilidad: sin infracciones WCAG 2.2 A/AA detectadas por axe-core en las 8 pantallas y 3 idiomas, y la práctica se puede completar solo con el teclado. Es una comprobación automática: falta una revisión con lectores de pantalla y con usuarios.
- No hay integración LTI ni inicio de sesión institucional (necesitarían un servidor).
- Las pruebas se hicieron con IA simulada, no con una clave real.

## Adoptarla en otra asignatura o universidad

Todo el contenido está en `src/curriculum.js` (RA literales de la guía, unidades, evaluación, ítems, textos, preguntas de desarrollo y cronología). Para otra asignatura basta con cambiar ese fichero y ejecutar `python3 build.py`. La lógica (`src/nucleo.js`) se prueba con `node tests/nucleo_test.js` y la interfaz con `python3 tests/app_test.py`.

## Ciencia del aprendizaje en la que se basa

Práctica de recuperación (Roediger y Karpicke, 2006, doi:10.1111/j.1467-9280.2006.01693.x), práctica espaciada (Cepeda et al., 2006, doi:10.1037/0033-2909.132.3.354), técnicas de estudio eficaces (Dunlosky et al., 2013, doi:10.1177/1529100612453266), feedback (Hattie y Timperley, 2007, doi:10.3102/003465430298487), alineamiento constructivo (Biggs, 1996, doi:10.1007/BF00138871) y taxonomía de Bloom revisada (Krathwohl, 2002, doi:10.1207/s15430421tip4104_2).

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche), José Antonio Pérez Juan (Universidad Miguel Hernández de Elche) y Sara Moreno Tejada (Universidad Miguel Hernández de Elche).

A partir de la Guía Docente 2026-2027 de la asignatura 1193 Historia del Derecho (Grado en Derecho, UMH), de la que son responsables José Antonio Pérez Juan y Sara Moreno Tejada.

Roles (CRediT): Fernando Borrás Rocher: conceptualización, software, metodología. José Antonio Pérez Juan y Sara Moreno Tejada: recursos (guía docente y contenidos de la asignatura); la validación del banco de preguntas está pendiente.

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) · José Antonio Pérez Juan [0000-0002-9973-683X](https://orcid.org/0000-0002-9973-683X) · Sara Moreno Tejada [0000-0003-3154-7730](https://orcid.org/0000-0003-3154-7730)

## Cómo citar

Borrás Rocher, F., Pérez Juan, J. A. y Moreno Tejada, S. (2026). *IusHistorIA* (v1.0.0) [Software]. (DOI en trámite)

## Licencia

MIT. Véase [LICENSE](LICENSE). La licencia MIT es una licencia de software; si el profesorado prefiere publicar los contenidos pedagógicos (banco de preguntas) bajo CC BY 4.0, puede hacerse en una versión posterior.
