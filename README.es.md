# ULTRAI

Una aplicación de escritorio para Windows para trabajo con IA que no se detiene. Cuatro modos en una sola ventana — conversar, construir en una carpeta de proyecto real, diseñar en un lienzo, generar imágenes y video — además de programación de tareas, ejecuciones multiagente y tu teléfono como segunda pantalla.

[English](./README.md) | [中文(简体)](./README.zh.md) | [中文(繁體)](./README.zht.md) | [한국어](./README.ko.md) | [Deutsch](./README.de.md) | [Español](./README.es.md) | [Français](./README.fr.md) | [Dansk](./README.da.md) | [日本語](./README.ja.md) | [Polski](./README.pl.md) | [Русский](./README.ru.md) | [العربية](./README.ar.md) | [Norsk](./README.no.md) | [Português (Brasil)](./README.br.md) | [ไทย](./README.th.md) | [Bosanski](./README.bs.md) | [Türkçe](./README.tr.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)

> Este repositorio es solo para **distribución de versiones**. El código fuente no se publica aquí.

---

## Descarga

Windows 10 / 11 (x64). Requiere el runtime de WebView2, que ya está presente en la mayoría de las instalaciones de Windows.

**[Descarga la última versión](https://github.com/UltraK18/ULTRAI/releases/latest)** — obtén `ULTRAI_x.y.z_x64_en-US.msi` y ejecútalo.

A partir de ahí la aplicación se encarga de todo: comprueba si hay nuevas versiones al iniciar y de forma periódica, te avisa cuando hay una disponible y la instala en el mismo lugar.

## Cuatro modos, una sola ventana

Cada modo es una pantalla diseñada para su propósito, con sus propias herramientas y sus propios agentes — pero una sola aplicación, un único conjunto de ajustes, un único lugar donde vive tu historial.

| Mode | La pantalla | Qué haces ahí |
| :--- | :--- | :--- |
| **Chat** | Conversación | Cualquier proveedor y modelo, nivel de esfuerzo de razonamiento por mensaje, investigación profunda con citas, archivos e imágenes de entrada |
| **Code** | Una carpeta de proyecto real | Árbol de archivos, diffs en un panel de revisión, una terminal junto al chat, solicitudes de permiso antes de que algo toque el disco |
| **Design** | Lienzo en vivo + agente de diseño | Las pantallas se renderizan junto al chat a medida que se construyen; el trabajo terminado pasa a Code como archivos reales |
| **Studio** | Lienzo libre + chat | Genera imágenes y video, colócalos y reorganízalos, añade tus propios archivos y sigue iterando sobre lo que ya está ahí |

Cambiar de modo no reinicia nada — cada modo conserva sus propias conversaciones, y la barra lateral muestra las que pertenecen a donde estás.

## La interfaz es lo que importa

La mayoría de las herramientas en este espacio son una terminal o una página web dentro de un envoltorio. ULTRAI es una aplicación de escritorio que fue diseñada, no ensamblada.

- **Vidrio que es realmente vidrio** — las superficies flotantes ejecutan un pequeño motor de renderizado, no un filtro de desenfoque. Genera un mapa de normales para el bisel y calcula reflejos especulares a partir de él, y desplaza lo que hay detrás de la superficie para que los bordes refracten. Controles como el interruptor y el deslizador van más allá y resuelven la refracción de Snell con un índice de refracción y un grosor, de modo que el pulgar curva la pista debajo de él. Un desenfoque CSS no puede lograr eso, y la diferencia se nota en cada borde.
- **Esquinas squircle** — los paneles usan una superelipse, no un arco circular, de modo que la curva entra en el borde recto sin el punto plano que se obtiene con `border-radius`.
- **Dos temas, ambos deliberados** — el claro y el oscuro se construyen sobre una misma paleta de tonos concreto con un ligero matiz frío, ajustada para que nada resulte deslumbrante en ningún extremo. Cada superficie es un token, así que toda la aplicación se mueve en conjunto en lugar de desviarse pantalla por pantalla.
- **Contención deliberada** — sin emojis en ningún lugar del producto, sin signos de exclamación, sin ánimo triunfalista. Cada panel tiene una única superficie; la separación viene de la luz de contorno y la sombra, no de cajas dibujadas dentro de cajas.
- **Ventana continua** — una barra de título de 32px con la métrica de Windows 11 que comparte el fondo de la aplicación, de modo que el marco no se percibe como una franja separada sobre el contenido.
- **Móvil es una disposición distinta, no una más pequeña** — hojas inferiores, controles de ancho completo y áreas táctiles de tamaño adecuado, decididas por el dispositivo y no por el ancho de la ventana.

## Generación, con modelos reales

Studio no es un único endpoint de imágenes. Elige de un catálogo para cada tarea y te indica qué modelo usó y por qué.

- **Video** — Veo 3.1 y Veo 3.0 (además de sus variantes rápidas), Sora 2 y Sora 2 Pro, Grok Imagine Video, Gemini Omni Flash
- **Imagen** — GPT Image 2 y 1.5, Gemini 3 Pro Image, Gemini 3.1 Flash Image (y Flash Lite), Grok Imagine Image
- **Video de entrada, video de salida** — dale un clip existente como entrada, no solo un prompt
- **Revisa su propio trabajo** — extrae fotogramas de lo que generó, los examina y decide si debe reintentar
- **La duración, la relación de aspecto y la calidad son tuyas** — si pediste 30 segundos, se construyen 30 segundos, con la forma que pediste

A qué modelos puedes acceder depende de las cuentas de proveedor que conectes (Vertex AI, OpenAI, xAI).

## Modo ULTRA — muchos agentes, una sola tarea

Para trabajo demasiado grande para un solo contexto. ULTRA divide la tarea en subtareas, las ejecuta entre varios agentes por fases, y hace que los resultados **se verifiquen de forma independiente antes de integrarse** — un crítico y comprobaciones adversariales, no el mismo agente calificándose a sí mismo. Puedes observar la ejecución e intervenir en cualquier momento. El modelo y el esfuerzo de razonamiento se configuran por rol, de modo que un trabajador económico y un verificador costoso pueden ser proveedores distintos, a propósito.

## Cumple sus citas

Di "cada día laborable a las 9" o "en dos horas" y se convierte en una tarea real, no en una nota. Cuando se activa, la tarea llega como un turno en esa conversación y la IA empieza a trabajar en ella.

- Un calendario y una lista muestran todo lo registrado; la próxima ejecución aparece en la parte inferior de la barra lateral
- ¿Estaba cerrada la app cuando algo vencía? Calcula lo que se perdió y lo agrupa en una sola ejecución de recuperación
- `/loop` repite una tarea durante tantas rondas como establezcas

## Objetivos que la IA no puede declarar cumplidos

Define un objetivo para una conversación y una evaluación independiente controla su finalización. El agente que hace el trabajo no decide por sí mismo cuándo terminó.

## Investigación que profundiza, y preguntas antes de trabajar

**Deep research** planifica los ángulos de investigación, luego busca y lee en paralelo entre subagentes y cita lo que encontró. La búsqueda cotidiana también es inusualmente estricta: se le indica al modelo que busque en lugar de suponer, que use la fecha de hoy en lugar de un año heredado del entrenamiento, y que verifique las afirmaciones en tiempo presente antes de responder. Los hallazgos se presentan de forma equilibrada, con las fuentes incluidas en el texto.

**Deep interview** — cuando una solicitud está poco especificada, convierte la conversación en una entrevista estructurada y define exactamente lo que quieres antes de que empiece cualquier trabajo.

## Trabajo que se ejecuta mientras haces otra cosa

Las tareas largas no secuestran la ventana.

- **Ejecuciones en segundo plano** — delega una tarea y se ejecuta de forma aislada, como una bifurcación de la conversación o como un subagente, y puede pedir más permisos a mitad de la ejecución si se topa con un obstáculo.
- **Un monitor en vivo** — una barra en la parte inferior muestra todo lo que está en curso a la vez: tus propias tareas en segundo plano, las iniciadas en otro lugar, llamadas a subagentes en ejecución, ejecuciones de ULTRA y cualquier comando de shell que lleve un rato corriendo. Haz clic para acceder a la que quieras observar.
- **Bifurca una conversación** — ramifica desde cualquier punto para probar algo sin perder el original, y salta entre ramas desde el índice de mensajes.

## Traspaso entre modos

El trabajo no se queda atrapado en el modo donde empezó. Design entrega las pantallas terminadas a Code como archivos reales en disco. Las sesiones de Code se pasan preguntas y resultados entre sí. Studio coloca lo que un agente produjo directamente en el lienzo. Cada traspaso mueve archivos reales o turnos reales, no un bloque de texto copiado.

## Un espacio de trabajo que la IA puede usar sin tocar tus archivos

El modo Chat tiene su propio espacio de trabajo temporal en disco. La IA puede escribir, leer, ejecutar y revisar cosas ahí libremente — borradores, scripts, archivos intermedios — sin pedirte permiso en cada paso y sin acceder a tus carpetas. Nunca tienes que pensar dónde está eso; simplemente obtienes el resultado, y tus propios directorios permanecen intactos a menos que tú los señales.

## Sesiones que se hablan entre sí

En el modo Code, una sesión puede pasarle una pregunta o un resultado a otra — la que trabaja en el backend puede preguntarle a la que conoce el frontend. Los mensajes llegan como un turno real en la otra conversación. Tú abres el canal; nada se conecta por sí solo.

## Tu teléfono es una segunda pantalla

Activa el servidor y abre ULTRAI desde el navegador del teléfono en la misma red. La disposición móvil está construida para el tacto — hojas inferiores y controles de ancho completo — no es un escritorio reducido. Las conversaciones, los modelos y los ajustes son compartidos, así que continúas exactamente donde lo dejaste.

## Hazlo tuyo

Todo lo que sigue es un archivo de texto plano en tu disco que puedes leer, editar y versionar.

- **Agentes** — `~/.ultrai/agents/*.md`. El frontmatter lo decide todo: en qué modos aparece, qué herramientas puede usar, qué secciones del prompt recibe, qué funciones (investigación, objetivos, entrevista) tiene permitidas. Se edita desde Settings, y los agentes integrados pueden restaurarse a su estado original en cualquier momento.
- **Skills** — `~/.ultrai/skills/*/SKILL.md`. Instrucciones reutilizables que el modelo puede incorporar, o que tú puedes invocar como un comando de barra. Activa o desactiva cada una individualmente.
- **Módulos de prompt** — el system prompt se ensambla a partir de un catálogo, y el frontmatter de cada agente elige qué secciones recibe. Si no declaras nada, el prompt del agente es idéntico byte a byte al predeterminado; puedes optar por activarlos para cambiar cómo piensa. Cada modo trae su propio prompt construido para ese tipo de trabajo, en lugar de un único prompt forzado a servir para todo.
- **Servidores MCP** — declarados en `ultrai.jsonc`. Locales o remotos, con autenticación cuando se necesita, activables o desactivables por servidor.
- **Memoria** — se guarda en tres categorías (sobre ti, temas, áreas), con resúmenes inyectados y detalles obtenidos bajo demanda, además de una limpieza periódica que combina duplicados y contradicciones. Solo en el modo Chat, y puedes ver y eliminar cada entrada desde Settings.
- **Proveedores** — Anthropic, OpenAI, Google, Google Vertex, xAI, OpenRouter y endpoints personalizados, con tus propias claves.

## Tus datos permanecen en tu PC

Las conversaciones y los ajustes se guardan **únicamente en tu equipo**. No existe un servidor de ULTRAI — tus conversaciones solo van al proveedor de IA que tú mismo conectaste, usando tu propia clave.

No se recopila nada, y no hay telemetría.

## Inicio rápido

1. **Conecta un proveedor** — añade tu clave de API en Settings → Providers.
2. **Elige un modelo** — el modelo y el esfuerzo de razonamiento están a la derecha de la barra de entrada.
3. **Elige un modo** — las pestañas en la parte superior de la barra lateral.
4. **Empieza a trabajar** — abre una carpeta en el modo Code; en los demás modos, simplemente empieza a hablar.
5. **Delega algo** — di "resume mi día cada noche" y la aplicación se encargará de ello por su cuenta.

## Stack tecnológico

Una aplicación nativa de Windows construida sobre Tauri 2. La interfaz está hecha con SolidJS; el backend se ejecuta como un único binario incluido con la aplicación.

## Comentarios

Los errores y solicitudes de funciones van a [Issues](https://github.com/UltraK18/ULTRAI/issues).

## Licencia

ULTRAI es freeware. Gratuito para uso personal y comercial. El código fuente no está disponible públicamente.

ULTRAI comenzó como un fork de [opencode](https://github.com/sst/opencode) y ha sido reconstruido mucho más allá de él, pero todavía incluye código de opencode, que tiene licencia MIT — Copyright (c) 2025 opencode. La licencia MIT se cita en su totalidad en los avisos incluidos con la aplicación.
