# Control de plataforma robótica mediante seguimiento ocular

Proyecto de grado de Lorenzo Martínez Sandoval, Ingeniería Electrónica, Universidad Santo Tomás.

El sistema permitirá seleccionar y confirmar un destino con la mirada para que una plataforma móvil transporte un objeto previamente cargado y realice una entrega simple en un escenario interior de aproximadamente **2,5 × 2,5 m**, plano y sin obstáculos.

## Documentación

El documento de **[requisitos del sistema](docs/levantamiento-de-requisitos.md)** reúne alcance, funciones, metas de desempeño y recomendaciones de plataforma y cómputo, con su verificación prevista. Los parámetros orientan la selección de equipos y podrán ajustarse durante las pruebas piloto; aún no representan resultados validados.

| Archivo | Contenido |
| --- | --- |
| [Requisitos del sistema](docs/levantamiento-de-requisitos.md) | Funciones y parámetros recomendados con tablas de verificación. |
| [LICENSE](LICENSE) | Licencia Apache 2.0. |

## Laboratorio de seguimiento ocular

El laboratorio local se encuentra en `../pruebas`, dentro de la carpeta `PROYECTO DE GRADO` y fuera de este repositorio. Conserva pruebas de WebGazer, MediaPipe, GazeTracking/Dlib y L2CS-Net, junto con instaladores, lanzadores y documentación; para utilizarlo, consulta su `README.md` y abre `INICIAR.cmd`. Esta carpeta no se incluye al clonar el repositorio.

## Referencias técnicas

La documentación se organiza con requisitos breves y verificables, tomando como referencia la distinción entre requisitos y recomendaciones de [Nav2](https://github.com/ros-navigation/navigation2/blob/main/doc/requirements/requirements.md). Los parámetros de hardware se orientan mediante documentación oficial, sin imponer un equipo concreto:

- [Movilidad, dimensiones y autonomía de bases compactas](https://emanual.robotis.com/docs/en/platform/turtlebot3/features/).
- [Cómputo embebido con aceleración por GPU: memoria, interfaces y potencia](https://www.nvidia.com/es-la/autonomous-machines/embedded-systems/jetson-orin/nano-super-developer-kit/).
- [Inferencia optimizada con TensorRT](https://docs.nvidia.com/deeplearning/tensorrt/latest/).

Las metas de desempeño y las condiciones de ensayo son propuestas del proyecto; las especificaciones comerciales no garantizan el comportamiento del montaje integrado. Referencias consultadas el 2026-11-13.
