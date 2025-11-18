# Producto_consumidor-Ping-Pong
# 🔄 Sincronización de Hilos: Productor-Consumidor (Ping-Pong)

Este proyecto es una implementación en **Java** del clásico problema de concurrencia **Productor-Consumidor**. El objetivo es coordinar dos hilos (threads) para que impriman una secuencia ordenada de "PING" y "PONG" indefinidamente, utilizando un objeto compartido sincronizado.

## 🛠️ Conceptos Clave
* **Hilos (Threads):** Ejecución concurrente de procesos.
* **Monitor (Synchronized):** Control de acceso exclusivo a recursos compartidos.
* **Coordinación (wait / notifyAll):** Comunicación entre hilos para gestionar pausas y reactivaciones según el estado de la cola.

## 📂 Estructura del Código

El proyecto consta de 4 clases principales:

| Clase | Responsabilidad |
| :--- | :--- |
| **`Cola.java`** | Recurso compartido. Gestiona la sincronización usando `synchronized`. Bloquea al consumidor si no hay datos y al productor si la cola está llena. |
| **`Productor.java`** | Hilo que genera las cadenas "PING" y "PONG" de forma alterna, simulando un tiempo de producción con `sleep`. |
| **`Consumidor.java`** | Hilo que recoge los datos de la cola tan pronto están disponibles y los imprime en pantalla. |
| **`Principal.java`** | Clase main que inicializa la cola y lanza los hilos. |

## 🚀 Cómo Funciona

1. El **Productor** genera "PING", lo pone en la `Cola` y avisa (`notifyAll`). Luego se duerme un momento.
2. El **Consumidor** (que estaba esperando) despierta, recoge el "PING", lo imprime y avisa de que la cola está libre.
3. El **Productor** despierta, genera "PONG", lo pone en la `Cola` y vuelve a avisar.
4. El ciclo se repite indefinidamente garantizando el orden gracias a los bloqueos `wait()`.

## 💻 Ejecución

Para compilar y ejecutar el proyecto desde la terminal:

```bash
# Compilar todos los archivos
javac *.java

# Ejecutar la clase principal
java Principal
