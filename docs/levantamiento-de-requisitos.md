# Levantamiento de requisitos

**Proyecto:** sistema asistivo para el control de una plataforma robótica móvil en tareas de posicionamiento, transporte y entrega de objetos mediante seguimiento ocular.

**Versión:** 0.2 · **Fecha:** 2026-10-19 · **Estado:** borrador para revisión; requisitos de plataforma propuestos para pruebas piloto.

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
| U1 | Definición del investigador, 2026-10-19: escenario interior de aproximadamente 2,5 × 2,5 m, totalmente plano y sin obstáculos; especificación inicial de una plataforma móvil compacta sin seleccionar marca ni modelo. |
| D1 | Propuestas de ingeniería de la sección 6, derivadas del escenario U1 y del alcance A3–A5; pendientes de revisión y caracterización en piloto. |
| T1 | [Documentación técnica oficial de plataformas móviles compactas](https://emanual.robotis.com/docs/en/platform/turtlebot3/features/), consultada el 2026-10-19, como referencia de viabilidad; sus especificaciones comerciales no se adoptan automáticamente como requisitos. |

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

Los requisitos de esta sección están **extraídos para revisión**. La columna de verificación indica cómo comprobarlos, no pruebas ya ejecutadas. Las condiciones pendientes de la sección 8 deben resolverse antes de aprobar los requisitos afectados.

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

## 6. Requisitos de la plataforma robótica móvil

La plataforma deberá ejecutar desplazamientos punto a punto, transportar un objeto previamente cargado y permitir su entrega simple dentro del escenario de laboratorio. Esta especificación describe las capacidades necesarias sin seleccionar marca, modelo, tipo de procesador ni tecnología de localización. La elección del equipo se realizará al comparar alternativas con estos requisitos. **Fuentes: A3, A4 y U1.**

El escenario indicado por el investigador constituye la base actual del diseño. Los valores numéricos nuevos se identifican como **propuestas D1**, no como datos extraídos del anteproyecto ni prestaciones ya comprobadas. Las metas de posicionamiento y latencia conservan su carácter preliminar de A5. Todos los requisitos PR están pendientes de aprobación; sus valores se revisarán en piloto y se fijarán antes de la validación definitiva.

### 6.1. Escenario y geometría de operación

Se interpreta el espacio indicado como un cuadrado de **aproximadamente 2,5 m de lado**, equivalente a **6,25 m²**. Antes de diseñar los recorridos se medirán sus dimensiones útiles. Se trabajará sobre piso interior horizontal, firme, continuo y seco, sin obstáculos, escalones ni pendientes. Los límites del cuadrado son límites operativos y no se presume que existan paredes u otras referencias detectables por sensores. El usuario, los equipos externos y los cables permanecerán fuera del área de desplazamiento. **Fuentes: U1 y D1.**

| ID | Requisito propuesto | Fuente y justificación | Verificación prevista |
| --- | --- | --- | --- |
| PR-01 | La plataforma deberá completar los recorridos entre los cinco destinos predefinidos dentro del área útil medida, sin que su envolvente cruce el límite del escenario. | U1, A3 y A5; D1 concreta la contención espacial. | Medir el área y registrar la trayectoria con el soporte y la carga instalados. |
| PR-02 | La envolvente del conjunto móvil, incluyendo soporte, carga y extensión del mecanismo de entrega, deberá ser como máximo de 0,30 × 0,30 m en planta y 0,40 m de altura. | D1: propuesta de tamaño compacto para reservar espacio de maniobra; T1 apoya la viabilidad de una base pequeña, no estas dimensiones del montaje final. | Medir las dimensiones exteriores máximas en todas las posiciones del mecanismo. |
| PR-03 | La plataforma deberá poder realizar un cambio de orientación de 180° dentro de una zona circular libre de 0,50 m de diámetro. | D1: maniobra local sin exigir una arquitectura de tracción concreta. | Observar y medir la envolvente barrida durante el giro con la carga de prueba. |

Como disposición inicial **ilustrativa**, con origen en una esquina del cuadrado, se proponen los destinos D1 = (0,50; 0,50), D2 = (2,00; 0,50), D3 = (2,00; 2,00), D4 = (0,50; 2,00) y D5 = (1,25; 1,25), en metros. Estos nombres de destino son independientes del código de fuente D1. No constituyen todavía el protocolo experimental: se documentarán el origen de cada recorrido, la orientación de entrega y las coordenadas definitivas tras medir el espacio. Se conservará el orden de ejecución establecido en el protocolo.

Para una envolvente de 0,30 × 0,30 m centrada en la referencia del robot, el radio circunscrito es aproximadamente 0,212 m. Una separación de 0,50 m entre el centro y el límite permite presupuestar ese radio, 0,10 m de desviación y 0,15 m de detención, con un margen restante aproximado de 0,038 m. Es una comprobación geométrica inicial: RNF-05 solo limita el error **medio final**, por lo que no garantiza una cota instantánea de 0,10 m durante el recorrido. La contención de PR-01 debe verificarse directamente y ampliarse el margen si la localización o el frenado medidos lo requieren.

### 6.2. Movimiento, posicionamiento y respuesta

| ID | Requisito propuesto | Fuente y justificación | Verificación prevista |
| --- | --- | --- | --- |
| PR-04 | La plataforma deberá permitir consignas de velocidad lineal entre 0,05 y 0,15 m/s en los tramos de traslación, además de la consigna de detención. | D1: intervalo inicial para recorridos cortos y observación del comportamiento con carga. | Medir distancia y tiempo en tramos rectos estabilizados para consignas de 0,05; 0,10 y 0,15 m/s. |
| PR-05 | El control deberá limitar la magnitud de la velocidad lineal a 0,15 m/s durante los ensayos. | D1: límite operativo inicial, independiente de la velocidad máxima que admita el hardware. | Registrar velocidad y provocar una consigna superior para comprobar la limitación. |
| PR-06 | El control deberá limitar la magnitud de la velocidad angular a 0,80 rad/s durante los ensayos. | D1: giro moderado para conservar la carga y facilitar la observación. | Registrar velocidad angular en giros y comprobar la saturación de consignas superiores. |
| PR-07 | El control deberá limitar la magnitud de la aceleración y desaceleración lineales comandadas en operación normal a 0,20 m/s². | D1: propuesta para reducir cambios bruscos con carga; no restringe una detención prioritaria. | Calcular la pendiente de las consignas temporizadas y caracterizar la respuesta física. |
| PR-08 | La plataforma deberá alcanzar un error medio final de posicionamiento ≤ 0,10 m en los ensayos robóticos previstos. | A5 y RNF-05; no se atribuye esta exactitud a un sensor o equipo comercial. | Medir externamente la distancia euclidiana entre destino y referencia del robot detenido; informar también dispersión, máximo y resultados por destino. |
| PR-09 | El sistema integrado deberá presentar una latencia media ≤ 1 s entre la confirmación ocular y el inicio observable del movimiento de la plataforma. | A5 y RNF-06; D1 concreta la respuesta observable para un comando de desplazamiento. | Registrar confirmación e inicio de movimiento con una referencia temporal común. |
| PR-10 | El subsistema robótico deberá presentar una latencia media ≤ 0,20 s entre la recepción de un destino válido y el inicio observable del movimiento, estando preparado y sin una detención activa. | D1: presupuesto inicial de respuesta dentro del segundo disponible para el sistema integrado. | Comparar el registro de recepción con el inicio físico medido; informar media y máximo. |

A 0,15 m/s, recorrer 2,5 m requiere aproximadamente 16,7 s a velocidad constante; la diagonal del cuadrado, de 3,54 m, requiere aproximadamente 23,6 s. Son estimaciones cinemáticas de referencia, no tiempos máximos de tarea: los recorridos reales dependen de los márgenes, el origen, los giros, las rampas y la entrega. La latencia de respuesta se medirá por separado del tiempo de desplazamiento y del tiempo total de tarea.

### 6.3. Carga, transporte y autonomía energética

| ID | Requisito propuesto | Fuente y justificación | Verificación prevista |
| --- | --- | --- | --- |
| PR-11 | La plataforma deberá transportar una carga adicional total de al menos 0,50 kg, incluyendo objeto, soporte y mecanismo de entrega añadidos a la base. | D1: carga de diseño inicial; la masa y dimensiones del objeto aún deben definirse y quedar dentro de este presupuesto. | Pesar los elementos añadidos y ejecutar recorridos, giros y detenciones con 0,50 kg en la distribución de carga declarada. |
| PR-12 | La plataforma deberá conservar el objeto en su soporte sin caída ni vuelco del conjunto durante los recorridos y detenciones previstos. | A3, RF-06 y D1; depende de la distribución de masa y altura del objeto. | Inspeccionar cada ensayo con carga; registrar caídas, desplazamientos del objeto y pérdida de estabilidad. |
| PR-13 | El montaje deberá disponer de una interfaz mecánica para fijar el soporte y el mecanismo de entrega simple. | A3, RF-07 y D1; no exige brazo ni pinza. | Inspeccionar fijaciones y comprobar que la entrega no interfiere con ruedas, sensores o maniobras. |
| PR-14 | La plataforma deberá operar al menos 60 min sin recarga ni sustitución de batería con todos los subsistemas embarcados activos y la carga de PR-11. | D1: duración inicial propuesta para una sesión; no equivale a la autonomía nominal comercial. | Ejecutar un ciclo reproducible de 1 min de traslaciones y giros y 1 min de espera, repetido 30 veces, con carga y registros activos. Documentar estado inicial de batería y toda interrupción. |
| PR-15 | El sistema deberá impedir el inicio de una nueva tarea al alcanzar el umbral de batería baja definido para la batería seleccionada. | D1: evitar interrupciones de tarea por agotamiento energético. | Simular el umbral y comprobar el bloqueo; fijar tensión o estado de carga según batería y caracterización antes de validar. |

La selección de batería deberá basarse en el consumo medido del montaje completo. Como cálculo inicial, **energía nominal requerida ≥ potencia media × duración / fracción utilizable**. Para 60 min, 10 W medios y una fracción utilizable supuesta de 0,80, el resultado sería 12,5 Wh. Estos valores son un ejemplo de dimensionamiento, no un consumo medido ni una batería prescrita. Se registrarán capacidad, tensión, masa, tiempo de recarga, protecciones y alimentación de periféricos al seleccionar el hardware.

### 6.4. Cómputo, localización y comunicación

La capacidad de cómputo se especifica por la carga de trabajo que deberá ejecutar: recepción de destinos, estimación de posición, control, supervisión y registro concurrentes. No se fija un mínimo arbitrario de GHz, núcleos, RAM o rendimiento de aceleración sin conocer los programas. Tampoco se presupone que el seguimiento ocular se ejecute en el computador embarcado: su ubicación y demanda se definirán en el diseño de la arquitectura. **Fuentes: A3, A4 y D1.**

| ID | Requisito propuesto | Fuente y justificación | Verificación prevista |
| --- | --- | --- | --- |
| PR-16 | El cómputo asignado al control de movimiento deberá actualizar las consignas a una frecuencia ≥ 20 Hz. | D1: período nominal ≤ 50 ms; a 0,15 m/s representa 7,5 mm de avance por período. No demuestra por sí solo exactitud de posicionamiento. | Registrar intervalos de actualización durante 30 min de ejecución concurrente; informar frecuencia efectiva, percentil 95 y máximo de los intervalos. |
| PR-17 | El subsistema de localización deberá proporcionar estimaciones de posición y orientación a una frecuencia ≥ 10 Hz durante los desplazamientos. | D1: referencia inicial para control punto a punto en el escenario conocido. No obliga a utilizar un tipo específico de sensor. | Registrar marcas temporales de las estimaciones y contrastar las posiciones con una referencia externa. |
| PR-18 | La plataforma deberá ejecutar control, localización, comunicación, supervisión y registro concurrentes durante 30 min sin reinicios ni terminaciones por falta de recursos. | D1: criterio inicial de capacidad real del conjunto hardware–software. | Ejecutar los módulos con la carga de trabajo prevista; comprobar PR-10, PR-16 y PR-17 y registrar CPU, memoria, temperatura y espacio de almacenamiento. |
| PR-19 | La plataforma deberá intercambiar destinos y estados con el subsistema ocular desde todas las posiciones del escenario sin cables que invadan el área de desplazamiento. | U1, A4 y D1: comunicación compatible con la movilidad. | Enviar órdenes y recibir estados en los cinco destinos y durante recorridos; medir pérdidas y tiempos de recepción. |
| PR-20 | La plataforma deberá informar el estado de cada orden mediante un identificador que permita relacionar su recepción, ejecución y finalización o fallo. | A4 y D1: trazabilidad del comando y de la tarea. | Comparar identificadores y estados en los registros de emisor y receptor, incluidos reenvíos. |
| PR-21 | El sistema deberá registrar por ensayo los tiempos de recepción, inicio y fin del movimiento, destino, posición final, estado de batería y eventos de fallo. | A5 y D1: evidencia para verificar desempeño y repetibilidad. | Revisar registros y comprobar su correspondencia con los ensayos y con la referencia temporal empleada. |

Tras la prueba de carga computacional se documentarán arquitectura y modelo de procesador, núcleos, RAM instalada y máxima utilizada, almacenamiento libre, interfaces, sistema operativo, dependencias, consumo y ubicación de cada módulo. Si la estimación ocular comparte esos recursos, deberá incluirse en PR-18 y repetirse la medición de RNF-06. Una ficha técnica de CPU o una capacidad nominal de aceleración no sustituye esta prueba. La tecnología de localización se seleccionará considerando que un espacio libre de obstáculos puede carecer de referencias geométricas suficientes; disponer de un sensor de distancia no garantiza por sí solo la localización.

### 6.5. Detención y supervisión

Estos requisitos concretan inicialmente la parte robótica de RF-08. La respuesta ante pérdida de seguimiento ocular seguirá pendiente hasta decidir si una tarea ya confirmada puede continuar sin señal ocular. La supervisión de comunicación se mantendrá activa durante el movimiento, aunque el envío del destino sea un evento único.

| ID | Requisito propuesto | Fuente y justificación | Verificación prevista |
| --- | --- | --- | --- |
| PR-22 | La plataforma deberá disponer de un medio de detención prioritario accionable por el supervisor e independiente del seguimiento ocular. | D1: supervisión del ensayo físico en laboratorio. | Accionarlo durante traslación y giro; comprobar su prioridad sobre las órdenes de movimiento. |
| PR-23 | La plataforma deberá quedar detenida en ≤ 1 s desde el accionamiento de la detención prioritaria, con un desplazamiento adicional ≤ 0,15 m desde una velocidad lineal inicial de 0,15 m/s y con la carga de PR-11. | D1: metas iniciales de frenado a verificar en el piso real; no son prestaciones certificadas. | Medir tiempo y distancia desde el accionamiento hasta el reposo; repetir con la distribución de carga prevista. |
| PR-24 | El supervisor embarcado deberá iniciar la detención al superar 0,50 s sin recibir la señal periódica de supervisión de comunicación. | A4, RF-08 y D1: detección inicial de pérdida de enlace. | Interrumpir la señal durante el movimiento y registrar última recepción e inicio de detención. |
| PR-25 | Ante pérdida de comunicación, la plataforma deberá quedar detenida en ≤ 1 s desde la última señal de supervisión recibida, con un desplazamiento adicional ≤ 0,15 m en las condiciones de PR-23. | D1: incluye detección y frenado, no solo el tiempo posterior al temporizador. | Medir tiempo y distancia desde la última señal hasta el reposo. |
| PR-26 | La plataforma deberá permanecer detenida después de una detención prioritaria o por pérdida de comunicación hasta recibir un rearme explícito del supervisor. | D1: impedir la reanudación al restablecerse el enlace. | Restablecer el enlace y reenviar órdenes antiguas; verificar que no se reanude el movimiento sin rearme. |
| PR-27 | La plataforma deberá rechazar órdenes con destino fuera del conjunto habilitado o con identificador de una orden ya ejecutada. | A4, RF-08 y D1: control de comandos inválidos y duplicados. | Enviar ambos tipos de orden y comprobar rechazo sin nuevo movimiento. |

Antes de validar se documentarán el criterio instrumental de reposo, las condiciones de rearme, el período de la señal de supervisión, la distribución de carga y el número de repeticiones de las pruebas de detención. Las pruebas anteriores no incorporan evitación de obstáculos ni amplían el alcance a navegación general.

### 6.6. Fundamento y estado de los parámetros

La documentación técnica T1 muestra la viabilidad de una base compacta de aproximadamente 0,14 × 0,18 × 0,19 m, con velocidad máxima publicada del orden de 0,22 m/s y autonomía esperada del orden de 2,5 h. Estos datos sirven únicamente como referencia de disponibilidad tecnológica. No garantizan el desempeño con soporte, mecanismo, carga y software añadidos, ni se exige reproducir la carga máxima comercial.

Los límites de 0,15 m/s, 0,80 rad/s, 0,30 × 0,30 × 0,40 m, 0,50 kg, 60 min, 20 Hz, 10 Hz y los tiempos de supervisión y detención son **propuestas de ingeniería D1 para este escenario**. No proceden del anteproyecto ni de una norma. El presupuesto de 0,20 s de respuesta robótica deja nominalmente 0,80 s para generación y transmisión del comando dentro de RNF-06; ambos deben comprobarse en integración. La precisión media de 0,10 m y la latencia media de 1 s sí conservan su origen A5. Una alternativa se seleccionará por el cumplimiento medido del conjunto, dejando registrados los parámetros aceptados y la justificación de cualquier ajuste previo a la validación.

## 7. Trazabilidad y evaluación prevista

Los objetivos específicos del anteproyecto son **OE1:** diseñar la arquitectura; **OE2:** implementar el prototipo; **OE3:** validar el desempeño. Los requisitos anteriores alimentan OE1, se materializan en OE2 y se verifican mediante OE3. Esta agrupación evita mantener una matriz separada.

| Grupo | Requisitos | Evidencia que deberá producirse |
| --- | --- | --- |
| Interacción ocular | RF-01 a RF-03; RNF-01 a RNF-04; RES-03 | Registro de objetivo solicitado, selección, confirmación, tiempos, muestras y activaciones involuntarias. |
| Plataforma | RF-05 a RF-07; RNF-05; RES-01 y RES-02; PR-01 a PR-08 y PR-11 a PR-18 | Geometría, trayectoria, velocidades, posición final, conservación del objeto, carga, autonomía y carga computacional. |
| Integración | RF-04 y RF-08; RNF-06 y RNF-07; PR-09, PR-10 y PR-19 a PR-27 | Correspondencia selección–comando, tiempos, tarea completa, registros y respuesta ante fallos. |

El anteproyecto propone **un participante: el investigador**, **cinco objetivos visuales** y **cinco destinos físicos**: 100 ensayos oculares (20 por objetivo), 50 robóticos (10 por destino) y 50 integrados (10 por destino), total 200. Es una propuesta experimental que debe confirmarse antes de ensayar; no representa pruebas realizadas. El período sin selección de RNF-02 se debe programar adicionalmente, pues su duración no queda resuelta por ese conteo. **Fuente: A5.**

Se conservarán fallos atribuibles al sistema como resultados; solo se excluirán interrupciones externas, fallos de registro o alteraciones accidentales documentadas que impidan medir. Registrar cada ensayo y sus condiciones, analizar tiempos y errores con dispersión y tasas con intervalos de confianza del 95 %, sin inferencia poblacional. **Fuente: A5.**

## 8. Decisiones necesarias para cerrar el levantamiento

| Pendiente concreto | Qué debe quedar definido | Requisitos afectados |
| --- | --- | --- |
| Confirmación ocular | Mecanismo, parámetros, calibración y tiempo máximo para seleccionar; comparar alternativas por exactitud, falsas activaciones, latencia y complejidad. | RF-01 a RF-03; RNF-01 a RNF-04 |
| Entorno e interfaz | Medir el área aproximada de 2,5 × 2,5 m; confirmar coordenadas, orígenes, orientaciones de entrega y recorridos. Definir iluminación, distancia de cámara y rango de cabeza. | RF-01, RF-02, RF-05; RES-01, RES-03; PR-01 a PR-03 |
| Objeto y entrega | Confirmar el presupuesto propuesto de 0,50 kg añadidos; definir masa, dimensiones y distribución del objeto, soporte, mecanismo y criterio observable de entrega. | RF-06, RF-07; RES-02; RNF-07; PR-02 y PR-11 a PR-13 |
| Fallos y detención | Revisar los tiempos propuestos de PR-22 a PR-27 y verificar frenado, criterio de reposo y rearme; definir la respuesta ante pérdida de mirada y localización. | RF-08; PR-22 a PR-27; afecta RF-05 a RF-07 |
| Selección de la plataforma | Verificar dimensiones, maniobra, velocidad con carga, estabilidad, energía y autonomía del montaje; aceptar o ajustar en piloto los valores D1. | PR-01 a PR-15 y PR-22 a PR-25 |
| Cómputo y comunicación | Definir ubicación de módulos, localización, protocolo y sincronización; dimensionar CPU, RAM, almacenamiento y alimentación mediante pruebas concurrentes. | PR-09, PR-10 y PR-16 a PR-21; RNF-06 |
| Mediciones y aceptación | Confirmar metas tras el piloto, tolerancia de llegada por ensayo, instrumentos, sincronización, validez de muestras y cómputo de intentos fallidos. Resolver la distinta redacción de «falsa activación» entre alcance y tabla operacional. | RNF-01 a RNF-07 |
| Viabilidad | Revisar con dirección los recursos disponibles, costo y plazo; seleccionar tecnologías después de concretar las necesidades. | Conjunto de requisitos |

**Siguiente actividad:** revisar esta tabla con director y codirector, registrar las respuestas aquí y ajustar los requisitos afectados. Después, fijar por escrito los parámetros que requieran piloto antes de la validación definitiva. No es necesario abrir archivos adicionales para cada conversación.

**Cierre de la etapa:** cada requisito debe tener fuente, redacción clara, criterio comprobable y parámetros resueltos; las discrepancias deben quedar resueltas y los responsables deben revisar la versión. **Aprobación:** pendiente; registrar fecha, versión o commit y conformidad de estudiante, director y codirector cuando ocurra.
