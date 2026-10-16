# Levantamiento de requisitos

**Proyecto:** sistema asistivo para el control de una plataforma robótica móvil en tareas de posicionamiento, transporte y entrega de objetos mediante seguimiento ocular.

**Versión:** 0.1 · **Fecha:** 2026-10-16 · **Estado:** borrador para revisión.

## 1. Base del levantamiento

Se realizó una revisión documental de `DOCUMENTO/anteproyecto.tex`, ubicado en la carpeta local del proyecto, con énfasis en objetivos, alcance, metodología y criterios de evaluación. No se han realizado entrevistas ni se registra aprobación de esta especificación. Esta versión sustituye el catálogo genérico inicial y reorganiza sus identificadores; no conserva requisitos aprobados de aquella versión porque no los había.

Para localizar las fuentes se usan estas referencias internas:

| Fuente | Ubicación en el anteproyecto |
| --- | --- |
| A1 | Capítulo «Planteamiento del problema». |
| A2 | Capítulo «Objetivos»: objetivo general y objetivos específicos. |
| A3 | «Alcance y limitaciones»: alcance funcional, técnico, experimental y exclusiones. |
| A4 | «Metodología»: fases 1, 2 y 3. |
| A5 | «Metodología»: fase 4 y tablas de variables, criterios oculares, ensayos y umbrales preliminares. |

Versión local consultada: SHA-256 `5c1b55a7ec6b7f8057bd6b461b518026df5441ee09b7a53bfd9f700510d5d083`. El anteproyecto original se conserva fuera de este repositorio.

**Criterio de redacción:** una obligación por requisito, fuente identificable y verificación prevista. Se adopta como guía la [lista de calidad de NASA](https://www.nasa.gov/reference/appendix-c-how-to-write-a-good-requirement/) y la [definición de requisitos de SEBoK](https://sebokwiki.org/wiki/System_Requirements), sin declarar certificación ni cumplimiento formal de una norma.

## 2. Necesidad y participantes

La necesidad es permitir que una persona con movilidad reducida severa de miembros superiores comunique una selección sin depender de controles manuales. El problema de interacción consiste en distinguir una observación de una selección deliberada antes de producir una acción física del robot. La intención se limita a confirmar una opción predefinida; no implica inferir estados mentales. **Fuente: A1 y A3.**

| Participante | Papel en el levantamiento |
| --- | --- |
| Lorenzo Martínez Sandoval, estudiante e investigador | Precisar escenarios, recursos y condiciones de prueba; consolidar requisitos. |
| Jaime Vitola Oyaga, director | Revisar coherencia con objetivos y alcance; acordar criterios de aceptación. |
| Armando Mateus Rojas, codirector | Revisar viabilidad técnica y criterios de evaluación. |
| Usuario de referencia | Persona con movilidad reducida severa de miembros superiores y control oculomotor voluntario suficiente para seleccionar y confirmar. Es un perfil de diseño, no un participante reclutado. |

Los nombres proceden del anteproyecto; las actividades de revisión están propuestas y aún no se han registrado. La validación técnica prevista utiliza al propio investigador y no permite generalizar resultados a la población objetivo. Replicar una restricción de uso de brazos no acredita representatividad clínica. **Fuente: A3 y A5.**

## 3. Alcance delimitado en el anteproyecto

- Prueba de concepto en laboratorio interior, sobre superficie plana, en un espacio delimitado y conocido.
- Selección ocular entre destinos o comandos predefinidos, con confirmación antes de transmitir una orden.
- Desplazamiento punto a punto; un único objeto cargado antes del inicio, transportado en bandeja, soporte o contenedor y entregado mediante una acción simple.
- Cámara externa al usuario; sin montaje en la cabeza ni mentonera, permitiendo movimientos suaves de cabeza dentro de condiciones que se caracterizarán.
- Evaluación de interacción ocular, plataforma robótica y funcionamiento integrado.

**Fuera del alcance:** agarre y recuperación autónoma de objetos, brazo o pinza, manipulación fina, selección de cualquier punto del espacio, navegación en entornos desconocidos, obstáculos dinámicos, exteriores, escaleras y superficies irregulares. No se pretende certificar un dispositivo médico ni demostrar eficacia clínica. **Fuentes: A3 y A4.**

La cámara, el algoritmo, el cómputo y la comunicación aún deben seleccionarse; el anteproyecto no obliga a una marca o tecnología concreta.

## 4. Requisitos funcionales

Todos los requisitos están **extraídos para revisión**. La columna de verificación indica cómo comprobarlos, no pruebas ya ejecutadas. Las condiciones pendientes de la sección 7 deben resolverse antes de aprobar los requisitos afectados.

| ID | El sistema deberá… | Fuente | Verificación prevista |
| --- | --- | --- | --- |
| RF-01 | Estimar la mirada para identificar una opción de la interfaz. | A3, A4 | Presentar objetivos conocidos y registrar opción estimada y disponibilidad de señal. |
| RF-02 | Permitir seleccionar mediante la mirada una opción del conjunto predefinido de destinos o comandos. | A3 | Solicitar cada opción y comparar lo solicitado con lo seleccionado. |
| RF-03 | Exigir el cumplimiento del mecanismo de confirmación antes de transmitir una orden robótica. | A3, A4 | Observar sin confirmar y luego confirmar; comprobar cuándo se transmite la orden. El mecanismo está pendiente. |
| RF-04 | Transformar cada selección confirmada en el comando correspondiente para la plataforma. | A3, A4 | Comparar selección confirmada, comando generado y comando recibido para cada opción. |
| RF-05 | Ejecutar el desplazamiento hacia el destino predefinido seleccionado sin exigir control ocular continuo de cada movimiento. | A3; estado del arte, interacción robótica | Confirmar un destino y observar la ejecución punto a punto. |
| RF-06 | Mantener el objeto previamente cargado en su soporte durante el desplazamiento. | A3 | Ejecutar recorridos con el objeto y verificar su permanencia en el soporte; carga y recorrido pendientes. |
| RF-07 | Ejecutar la acción simple de entrega o liberación del objeto al finalizar el posicionamiento. | A3, A4 | Verificar la entrega en el destino; mecanismo y condición de entrega pendientes. |
| RF-08 | Aplicar la respuesta definida para pérdida de seguimiento ocular, comando inválido y pérdida de comunicación. | A4, fase 2 | Provocar cada condición y comprobar la respuesta. El estado, tiempo de detección y recuperación deben definirse; todavía no es aprobable. |

**Escenario principal:** objeto cargado y sistema preparado → selección ocular → confirmación → comando → desplazamiento → posicionamiento → entrega. Se considera completado sin intervención manual correctiva; la preparación y carga inicial no forman parte de esa ejecución. **Fuente: A3.**

## 5. Requisitos de desempeño y restricciones

Los valores siguientes están en la tabla «Umbrales preliminares de aceptación del sistema» del anteproyecto. Son **metas de diseño pendientes de validar en piloto**, no resultados obtenidos ni umbrales definitivos. Se fijarán y justificarán antes de la validación definitiva y no se ajustarán después de observar sus resultados. **Fuente: A5.**

| ID | Métrica y requisito preliminar | Forma prevista de comprobarlo |
| --- | --- | --- |
| RNF-01 | Tasa de selección correcta ≥ 90 %. | Selecciones del objetivo solicitado con confirmación válida / intentos válidos × 100. Incluir selecciones erróneas y agotamientos de tiempo como fallos. |
| RNF-02 | Ningún comando involuntario durante 10 minutos sin intención de seleccionar. | Contar comandos emitidos durante el período de observación sin selección, aunque no produzcan movimiento. |
| RNF-03 | Tiempo medio de selección ≤ 3 s. | Medir desde la presentación de la instrucción hasta la confirmación. Acordar el tratamiento de intentos sin confirmación. |
| RNF-04 | Al menos 95 % de muestras de seguimiento válidas. | Muestras válidas / muestras adquiridas × 100. Definir validez y ventana; dispersión admisible aún pendiente. |
| RNF-05 | Error medio final de posicionamiento ≤ 10 cm. | Distancia euclidiana entre referencia del destino y posición final del robot. Definir punto de referencia y método de medición. |
| RNF-06 | Latencia media de respuesta ≤ 1 s. | Medir desde la confirmación hasta la primera respuesta observable del robot; no confundir con duración total de tarea. |
| RNF-07 | Tasa de éxito de tarea ≥ 90 %. | Tareas que completan selección, desplazamiento, posicionamiento y entrega sin corrección manual / tareas válidas intentadas × 100. Definir tolerancia por tarea. |

Las fórmulas operativas se proponen para concretar la medición; denominadores, tiempos máximos y reglas de cómputo deben revisarse antes de aprobarlas. Un error medio aceptable no asegura que cada ensayo cumpla la tolerancia de llegada.

| ID | Restricción de la prueba de concepto | Fuente | Comprobación |
| --- | --- | --- | --- |
| RES-01 | Operar en interior delimitado y conocido, sobre superficie plana y con destinos predefinidos. | A3 | Inspección del espacio, superficie y posiciones. |
| RES-02 | Transportar un objeto previamente cargado mediante bandeja, soporte o contenedor, sin brazo ni pinza. | A3 | Inspección del montaje y secuencia de ensayo. |
| RES-03 | Utilizar cámara externa, sin montaje en la cabeza ni mentonera. | A4, fase 2 | Inspección de instalación y comprobación en el rango de movimiento de cabeza por definir. |

## 6. Trazabilidad y evaluación prevista

Los objetivos específicos del anteproyecto son **OE1:** diseñar la arquitectura; **OE2:** implementar el prototipo; **OE3:** validar el desempeño. Los requisitos anteriores alimentan OE1, se materializan en OE2 y se verifican mediante OE3. Esta agrupación evita mantener una matriz separada.

| Grupo | Requisitos | Evidencia que deberá producirse |
| --- | --- | --- |
| Interacción ocular | RF-01 a RF-03; RNF-01 a RNF-04; RES-03 | Registro de objetivo solicitado, selección, confirmación, tiempos, muestras y activaciones involuntarias. |
| Plataforma | RF-05 a RF-07; RNF-05; RES-01 y RES-02 | Posición de referencia y final, conservación del objeto, tiempo de recorrido y entrega. |
| Integración | RF-04 y RF-08; RNF-06 y RNF-07 | Correspondencia selección–comando, tiempos, tarea completa y respuesta ante fallos. |

El anteproyecto propone **un participante: el investigador**, **cinco objetivos visuales** y **cinco destinos físicos**: 100 ensayos oculares (20 por objetivo), 50 robóticos (10 por destino) y 50 integrados (10 por destino), total 200. Es una propuesta experimental que debe confirmarse antes de ensayar; no representa pruebas realizadas. El período sin selección de RNF-02 se debe programar adicionalmente, pues su duración no queda resuelta por ese conteo. **Fuente: A5.**

Se conservarán fallos atribuibles al sistema como resultados; solo se excluirán interrupciones externas, fallos de registro o alteraciones accidentales documentadas que impidan medir. Registrar cada ensayo y sus condiciones, analizar tiempos y errores con dispersión y tasas con intervalos de confianza del 95 %, sin inferencia poblacional. **Fuente: A5.**

## 7. Decisiones necesarias para cerrar el levantamiento

| Pendiente concreto | Qué debe quedar definido | Requisitos afectados |
| --- | --- | --- |
| Confirmación ocular | Mecanismo, parámetros, calibración y tiempo máximo para seleccionar; comparar alternativas por exactitud, falsas activaciones, latencia y complejidad. | RF-01 a RF-03; RNF-01 a RNF-04 |
| Entorno e interfaz | Posición de los cinco objetivos y destinos, recorridos, iluminación, distancia de cámara y rango permitido de cabeza. | RF-01, RF-02, RF-05; RES-01, RES-03 |
| Objeto y entrega | Masa y dimensiones del objeto, soporte, mecanismo y criterio observable de entrega correcta. | RF-06, RF-07; RES-02; RNF-07 |
| Fallos y detención | Estado esperado ante cada fallo, tiempos máximos, forma de detener la plataforma y condiciones de reanudación. La detención es un punto propuesto para revisión, no un mecanismo ya especificado. | RF-08; afecta el escenario de RF-05 a RF-07 |
| Mediciones y aceptación | Confirmar metas tras el piloto, tolerancia de llegada por ensayo, instrumentos, sincronización, validez de muestras y cómputo de intentos fallidos. Resolver la distinta redacción de «falsa activación» entre alcance y tabla operacional. | RNF-01 a RNF-07 |
| Viabilidad | Revisar con dirección los recursos disponibles, costo y plazo; seleccionar tecnologías después de concretar las necesidades. | Conjunto de requisitos |

**Siguiente actividad:** revisar esta tabla con director y codirector, registrar las respuestas aquí y ajustar los requisitos afectados. Después, fijar por escrito los parámetros que requieran piloto antes de la validación definitiva. No es necesario abrir archivos adicionales para cada conversación.

**Cierre de la etapa:** cada requisito debe tener fuente, redacción clara, criterio comprobable y parámetros resueltos; las discrepancias deben quedar resueltas y los responsables deben revisar la versión. **Aprobación:** pendiente; registrar fecha, versión o commit y conformidad de estudiante, director y codirector cuando ocurra.
