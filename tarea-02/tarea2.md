| Campo                       | Significado                                                 |
| --------------------------- | ----------------------------------------------------------- |
| Architecture                | Tipo de arquitectura (ej. `x86_64`, `aarch64`).             |
| CPU op-mode(s)              | Modos soportados: 32-bit, 64-bit o ambos.                   |
| Byte Order                  | Orden de bytes en memoria (*Little Endian* o *Big Endian*). |
| CPU(s)                      | Número total de CPUs lógicas (hilos).                       |
| On-line CPU(s) list         | Lista de CPUs activas.                                      |
| Vendor ID                   | Fabricante del procesador (Intel, AMD).                     |
| Model name                  | Nombre comercial del procesador.                            |
| Thread(s) per core          | Número de hilos por núcleo.                                 |
| Core(s) per socket          | Núcleos físicos por socket.                                 |
| Socket(s)                   | Número de procesadores físicos instalados.                  |
| NUMA node(s)                | Nodos de memoria (en servidores multiprocesador).           |
| CPU MHz / max MHz / min MHz | Velocidad actual, máxima y mínima.                          |
| BogoMIPS                    | Valor aproximado de rendimiento usado por el kernel.        |
| Virtualization              | Extensiones soportadas (VT-x, AMD-V).                       |
| Caches (L1, L2, L3)         | Tamaños de caché por nivel.                                 |
| Flags                       | Instrucciones soportadas (SSE, AVX, AES, etc.).             |


| Campo                | Significado                                                     |
| -------------------- | --------------------------------------------------------------- |
| Bus/Device/Function  | Dirección del dispositivo en el bus PCI.                        |
| Vendor               | Fabricante del dispositivo (ej. Intel, NVIDIA).                 |
| Device               | Tipo de dispositivo (ej. controlador de red, tarjeta gráfica).  |
| Subsystem            | Información adicional del fabricante OEM.                       |
| Class                | Clase del dispositivo (ej. Network controller, VGA controller). |
| IRQ                  | Número de interrupción asignado.                                |
| Memory address       | Rango de memoria usado por el dispositivo.                      |
| I/O ports            | Puertos de entrada/salida asignados.                            |
| Kernel driver in use | Driver que está usando el sistema.                              |
| Kernel modules       | Módulos disponibles para ese dispositivo.                       |

| Campo          | Significado                                        |
| -------------- | -------------------------------------------------- |
| Range          | Rango de direcciones de memoria física.            |
| Size           | Tamaño de cada bloque de memoria.                  |
| State          | Estado de la memoria (online/offline).             |
| Removable      | Indica si el bloque de memoria puede ser removido. |
| Block count    | Número de bloques de memoria detectados.           |
| Online memory  | Cantidad de memoria activa y disponible.           |
| Offline memory | Cantidad de memoria detectada pero no activa.      |

| Campo         | Significado                                            |
| ------------- | ------------------------------------------------------ |
| Description   | Descripción del dispositivo (ej. `System`, `CPU`).     |
| Product       | Modelo del hardware (ej. Dell Inspiron).               |
| Vendor        | Fabricante del dispositivo.                            |
| Physical id   | Identificador físico en el sistema.                    |
| Bus info      | Información del bus (PCI, USB, etc.).                  |
| Version       | Versión del hardware.                                  |
| Serial        | Número de serie del dispositivo.                       |
| Size          | Tamaño (ej. RAM instalada, capacidad de disco).        |
| Capacity      | Capacidad máxima soportada.                            |
| Width         | Ancho de bus en bits.                                  |
| Clock         | Frecuencia de reloj (ej. CPU MHz).                     |
| Configuration | Parámetros de configuración detectados.                |
| Capabilities  | Funciones soportadas (ej. multitarea, virtualización). |
