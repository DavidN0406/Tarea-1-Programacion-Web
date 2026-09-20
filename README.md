# Tarea 1 — Construcción de interfaces web adaptables con HTML y CSS

## Identificación

- **Nombre:** David
- **Curso:** SOFT-12 Programación web avanzada
- **Sección:** SCV2
- **Docente:** Álvaro Cordero Peña
- **Fecha de entrega:** 20 de setiembre de 2026

## Descripción de los casos

### Caso 1 — Centro de control de una expedición científica
Interfaz tipo dashboard para que el equipo coordinador de una expedición en Monteverde visualice de un vistazo el estado general de la operación: misiones activas, equipos científicos, alertas y agenda del día.

### Caso 2 — Panel público de información de un festival
Panel para que los asistentes de un festival cultural consulten desde el celular qué está pasando en cada momento, qué sigue y qué cambió, priorizando la sección "Ahora" en móvil.

## Estructura de carpetas

\`\`\`
Tarea1/
├── README.md
├── caso1/
│   ├── index.html
│   ├── css/
│   │   └── estilos.css
│   └── img/
└── caso2/
    ├── index.html
    ├── css/
    │   └── estilos.css
    └── img/
\`\`\`

## Instrucciones para abrir cada caso

Cada caso es independiente. Basta con abrir `caso1/index.html` o `caso2/index.html` directamente en el navegador.


## Decisiones de diseño

**¿Por qué se seleccionaron determinadas etiquetas semánticas?**
Se usó header para la identificación de cada página, nav para los menús de navegación, main para el contenido central, section para cada bloque temático (misiones, alertas, escenarios, etc.), article para elementos repetibles autocontenidos (una misión, un equipo, un escenario) y footer para el cierre. En el Caso 1 se usó aside para la agenda porque es información complementaria al flujo principal del centro de control.

**¿Cómo se organizó la jerarquía de encabezados?**
h1 se reservó para el título general de cada página (nombre de la expedición o del festival), h2 para el título de cada sección y h3 para elementos individuales dentro de una sección (una misión, un equipo, un escenario). No se saltó ningún nivel.

**¿Cómo se incorporó la accesibilidad básica?**
Ambos documentos declaran lang="es". Se usó aria-label en las navegaciones y aria-labelledby en las secciones para asociarlas con su encabezado. Los estados (pendiente, en progreso, completada, suspendida) se comunican con texto e íconos además de color. Se cuidó el contraste entre texto y fondo en ambos temas de color.

**¿Cómo funciona el modelo de caja en los componentes principales?**
Se definió box-sizing: border-box de forma global para que padding y border no alteren el ancho declarado. Las tarjetas usan padding consistente definido con variables, y los contenedores principales usan max-width implícito por el grid en vez de anchos fijos en píxeles.

**¿Dónde se usó posicionamiento, qué valor y por qué?**
Caso 1: la cabecera y la barra de navegación usan position: sticky para mantenerse visibles mientras se hace scroll. La etiqueta de prioridad de cada misión usa position: absolute dentro de una tarjeta con position: relative, para superponerse sin afectar el flujo del contenido.
Caso 2: la barra de navegación usa position: sticky en la parte superior. La etiqueta "En este momento" de cada actividad usa position: absolute sobre un contenedor con position: relative.

**¿Por qué algunos estilos prevalecen sobre otros?**
Se trabajó con selectores de clase simples (metodología tipo BEM abreviada, por ejemplo .mision__encabezado, .alerta--critica) para mantener una especificidad baja y predecible. No se usó !important en ningún caso.

**¿Dónde se usó Flexbox y por qué?**
En ambos casos: la navegación, los indicadores del resumen y los servicios del festival, el encabezado de cada misión y las alertas. Flexbox se aplicó donde la distribución es unidimensional.

**¿Dónde se usó CSS Grid y por qué?**
El contenedor principal de ambos casos usa CSS Grid para organizar las secciones en columnas que cambian según el tamaño de pantalla, incluyendo grid-template-areas en escritorio. También se usó Grid para la cuadrícula de equipos científicos (Caso 1) y de escenarios (Caso 2), donde se necesita una distribución bidimensional.

**¿Cómo cambia el layout entre teléfono, tableta y escritorio?**
En teléfono todo se apila en una columna y las secciones más urgentes se muestran primero. En tableta aparecen dos columnas. En escritorio se usa grid-template-areas para mostrar varias zonas en simultáneo.

**¿Cuáles media queries se utilizaron y por qué esos breakpoints?**
Se usaron min-width: 601px para tableta y min-width: 1024px para escritorio, siguiendo la referencia orientativa de la consigna.

**¿Cuáles unidades relativas se utilizaron?**
Se usó rem para tipografía y espaciados, % en las columnas flexibles, y fr en grid-template-columns. Los anchos de los contenedores no dependen de píxeles fijos.

**¿Para qué sirven las variables CSS definidas?**
Las variables en :root (colores, espaciado y radios de borde) permiten mantener consistencia visual y facilitan cambiar la paleta o el espaciado global modificando un solo valor.

## Resumen de commits

| # | Fecha | Hash | Mensaje | Caso | Cambio |
|---|---|---|---|---|---|
| 1 | 2026-09-19 | a75b77f | Estructura y HTML semántico del caso 1 | Caso 1 | Header, nav, main y secciones semánticas |
| 2 | 2026-09-19 | 5fcf659 | Estructura y HTML semántico del caso 2 | Caso 2 | Header, nav, main y secciones semánticas |
| 3 | 2026-09-19 | 2a971fe | Variables CSS, tipografía y cabecera sticky del caso 1 | Caso 1 | :root, reset, tipografía y cabecera fija |
| 4 | 2026-09-19 | 5d1eb63 | Flexbox en indicadores, misiones y alertas del caso 1 | Caso 1 | Distribución con Flexbox y posicionamiento en misiones |
| 5 | 2026-09-19 | c6b2eb2 | Grid de equipos científicos y agenda del caso 1 | Caso 1 | CSS Grid en tarjetas de equipos y lista de agenda |
| 6 | 2026-09-19 | 79b278d | Ajuste de scroll y posicionamiento sticky/absolute del caso 1 | Caso 1 | scroll-margin-top para evitar solapamiento con el nav |
| 7 | 2026-09-19 | edbfd9d | Media queries de tableta y escritorio del caso 1 | Caso 1 | Adaptación a 601px y 1024px con grid-template-areas |
| 8 | 2026-09-19 | 96e2d74 | Variables CSS, cabecera y nav sticky del caso 2 | Caso 2 | :root, reset, tipografía y navegación fija |
| 9 | 2026-09-19 | a101f9c | Layout mobile-first, Grid de escenarios y Flexbox de servicios del caso 2 | Caso 2 | Sección Ahora, Grid de escenarios y servicios |
| 10 | 2026-09-19 | 28534fc | Media queries de tableta y escritorio del caso 2 | Caso 2 | Adaptación a 601px y 1024px con grid-template-areas |
| 11 | 2026-09-20 | dba01b6 | Corrección de imágenes adaptables y desbordamiento horizontal | Ambos | Regla img adaptable y overflow-x: hidden |
| 12 | 2026-09-20 | d69368d | Documentación en README.md | Ambos | README completo con decisiones de diseño y esta tabla |