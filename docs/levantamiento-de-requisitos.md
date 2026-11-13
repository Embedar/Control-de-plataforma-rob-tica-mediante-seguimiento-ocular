# Requisitos del sistema

**Estado:** propuesta de diseño · **Actualización:** 2026-11-13.

Este documento reúne las funciones necesarias y los parámetros recomendados para seleccionar e integrar los equipos. Los valores son referencias iniciales, no límites absolutos ni prestaciones comprobadas: podrán ajustarse según los recursos disponibles y las pruebas piloto, conservando la función prevista y registrando los cambios antes de la validación definitiva.

## 1. Alcance

Controlar una plataforma móvil mediante selección y confirmación ocular de destinos predefinidos, para posicionar, transportar y entregar un objeto previamente cargado en un escenario interior de aproximadamente **2,5 × 2,5 m**, plano y sin obstáculos.

Se utilizará una cámara externa, sin montaje en la cabeza ni mentonera, y se evaluarán la interacción ocular, el desplazamiento y la tarea completa. La entrega será simple, mediante soporte, bandeja o contenedor; quedan fuera el agarre autónomo, los brazos y pinzas, la navegación en entornos desconocidos y la operación sobre pendientes, escaleras o superficies irregulares.

## 2. Requisitos funcionales

| Requisito propuesto | Verificación prevista |
| --- | --- |
| Estimar la mirada y seleccionar un destino de la interfaz. | Comparar el destino solicitado con el seleccionado. |
| Confirmar la selección antes de enviar una orden al robot. | Comprobar que observar una opción sin confirmarla no produce una orden. |
| Convertir la selección confirmada en el destino correspondiente. | Comparar la selección con la orden recibida por la plataforma. |
| Ejecutar el desplazamiento sin exigir control ocular continuo de cada movimiento. | Confirmar un destino y observar el recorrido completo. |
| Conservar el objeto durante el transporte y realizar la entrega al llegar. | Comprobar permanencia en el soporte y entrega sin corrección manual. |

## 3. Metas de desempeño

Son metas preliminares para el conjunto integrado; se comprobarán con el montaje y el procedimiento de prueba definidos.

| Requisito propuesto | Verificación prevista |
| --- | --- |
| Selección correcta ≥ 90 %. | Calcular aciertos sobre intentos válidos, contando errores y selecciones agotadas por tiempo como fallos. |
| Ninguna activación involuntaria en 10 min sin intención de seleccionar. | Contar órdenes emitidas durante ese período. |
| Tiempo medio de selección ≤ 3 s. | Medir desde la instrucción hasta la confirmación; registrar aparte los intentos fallidos. |
| Seguimiento con ≥ 95 % de muestras válidas. | Calcular muestras válidas sobre muestras adquiridas con el criterio de validez fijado en piloto. |
| Error medio final de posicionamiento ≤ 10 cm. | Medir externamente la distancia entre destino y posición final; informar también dispersión y máximo. |
| Latencia media de respuesta ≤ 1 s. | Medir desde la confirmación ocular hasta el inicio físico del movimiento. |
| Éxito de tarea ≥ 90 %. | Contar tareas que completan selección, recorrido y entrega sin corrección manual. |

## 4. Plataforma robótica y cómputo

### 4.1. Escenario y dimensiones

Se recomienda una base compacta, capaz de girar sobre su posición y alojar el soporte de carga sin comprometer la estabilidad. Las dimensiones de referencia corresponden a la base; el montaje completo deberá medirse nuevamente.

| Requisito propuesto | Verificación prevista |
| --- | --- |
| Operar entre cinco destinos predefinidos sin salir del área útil de aproximadamente 2,5 × 2,5 m. | Medir el espacio y observar los recorridos con el montaje completo. |
| Base de aproximadamente 0,14 × 0,18 × 0,20 m y masa cercana a 1 kg, con batería y sensores propios. | Medir y pesar la base disponible. |
| Conjunto con soporte y carga preferiblemente dentro de 0,30 × 0,30 m en planta y 0,40 m de altura. | Medir la envolvente máxima, incluida la posición de entrega. |
| Realizar giros de 180° dentro de una zona libre de 0,50 m de diámetro. | Medir el espacio barrido durante el giro con carga. |

La ubicación de los destinos deberá reservar margen para el tamaño completo del robot, la desviación de trayectoria y la distancia de detención. El error medio de llegada no garantiza por sí solo que el robot permanezca dentro del área.

### 4.2. Movimiento y respuesta

La capacidad de referencia es de **hasta 0,22 m/s de traslación y 2,84 rad/s de giro**, mientras que para este escenario se recomiendan velocidades operativas menores, ajustables según la estabilidad del objeto.

| Requisito propuesto | Verificación prevista |
| --- | --- |
| Regular la velocidad lineal, con un intervalo inicial de ensayo de 0,05–0,15 m/s y detención. | Medir distancia y tiempo en tramos rectos para distintas consignas. |
| Limitar inicialmente la velocidad angular a 0,80 rad/s durante los ensayos. | Registrar la velocidad de giro con carga. |
| Aplicar rampas de aceleración y desaceleración normal de hasta 0,20 m/s². | Revisar consignas y respuesta física, comprobando la estabilidad del objeto. |
| Alcanzar los destinos con error medio final ≤ 10 cm. | Comparar posiciones finales con referencias externas en los cinco destinos. |
| Iniciar el movimiento con latencia media ≤ 0,20 s desde la recepción de una orden válida, estando preparado. | Registrar recepción e inicio físico con una referencia temporal común. |

La respuesta robótica forma parte de la meta integrada de 1 s; el tiempo de recorrido y el de entrega se medirán por separado.

### 4.3. Carga y autonomía

Se recomienda una autonomía nominal del orden de **2 h 30 min** y una batería recargable de referencia de **11,1 V y aproximadamente 20 Wh**, aunque la autonomía efectiva dependerá de la carga, los recorridos y el consumo del montaje.

| Requisito propuesto | Verificación prevista |
| --- | --- |
| Transportar inicialmente 0,50 kg adicionales, incluyendo objeto, soporte y mecanismo de entrega. | Pesar la carga añadida y realizar recorridos, giros y detenciones. |
| Mantener el objeto sin caída y el conjunto sin vuelco durante la tarea. | Observar el comportamiento con la distribución de carga prevista. |
| Disponer de fijaciones para el soporte y una entrega simple. | Inspeccionar el montaje y ejecutar la entrega sin interferencias. |
| Alcanzar al menos 60 min de operación efectiva sin recarga con los equipos embarcados activos. | Alternar 1 min de movimiento y 1 min de espera durante 60 min, con carga y registros activos. |
| Supervisar el nivel de batería e impedir nuevas tareas al alcanzar el umbral de batería baja. | Simular el umbral correspondiente a la batería seleccionada y comprobar el bloqueo. |

Los 60 min son una meta inicial del montaje real, distinta de la autonomía nominal. Si el cómputo se instala a bordo, su alimentación, masa y consumo se incluirán en la verificación; no se presupone que la batería de la base pueda alimentarlo directamente.

### 4.4. Cómputo, localización y comunicación

Se recomienda cómputo de 64 bits con CPU multinúcleo, **8 GB de memoria y GPU compatible con CUDA**, junto con TensorRT para acelerar la inferencia cuando el modelo lo permita. Esta configuración orienta la selección, pero se admiten otras arquitecturas que cumplan las metas de respuesta y estabilidad.

| Requisito propuesto | Verificación prevista |
| --- | --- |
| Ejecutar adquisición, estimación de mirada, interfaz y comunicación sobre Linux, con bibliotecas de visión y aprendizaje compatibles. | Instalar y ejecutar el flujo completo con versiones de dependencias registradas. |
| Acelerar la inferencia mediante CUDA y, cuando sea compatible, TensorRT y precisión FP16. | Comparar latencia, memoria y calidad de selección antes y después de optimizar. |
| Disponer de almacenamiento ampliable y conexiones para cámara y red; se recomiendan USB 3 y Ethernet o Wi-Fi. | Comprobar adquisición, envío de órdenes y guardado de registros simultáneos. |
| Mantener los módulos asignados a cada equipo funcionando durante 30 min sin reinicios ni agotamiento de memoria. | Registrar CPU, GPU, memoria, temperatura y latencia bajo la carga real. |
| Actualizar el control de movimiento a ≥ 20 Hz y la posición y orientación a ≥ 10 Hz. | Registrar los intervalos de actualización durante los recorridos. |
| Localizar el robot en el escenario conocido mediante odometría y sensores de orientación, con apoyo de referencias externas si resulta necesario. | Contrastar la posición estimada con mediciones externas. |
| Intercambiar destinos y estados desde toda el área sin cables que invadan los recorridos. | Enviar órdenes y comprobar recepción y estado durante el movimiento. |
| Registrar destino, tiempos de recepción, inicio y fin del movimiento, posición final y batería. | Revisar que los registros permitan reconstruir cada ensayo. |

La alimentación y refrigeración del cómputo se dimensionarán para la configuración elegida; como referencia, un módulo de esta clase puede trabajar en modos de 7–25 W, a los que se suman placa, cámara y periféricos. El procesamiento podrá ubicarse junto al usuario o a bordo, siempre que se mantenga la latencia integrada y se comprueben consumo, comunicación y estabilidad.
