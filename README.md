# Control de movimiento clase 20/03/25
# Introducción


# Perfiles de movimiento
Como su nombre lo indica, es la trayectoria de la carga desde un punto A hasta un punto B, este movimiento puede variar según el sistema utilizado. En un solo eje, el movimiento es lineal y sigue una dirección única, mientras que en sistemas multieje las trayectorias se vuelven más complejas, combinando movimientos en diferentes direcciones. El perfil de movimiento describe el comportamiento del sistema en términos de posición, velocidad, aceleración e incluso el jerk (tasa de cambio de la aceleración), lo que permite optimizar la suavidad del desplazamiento.

# Cinemática
Estudia el comportamiento de la posición s(t), la velocidad v(t) y la aceleración a(t) en función del tiempo. En un sistema de un solo eje s(t) describe la posición en cualquier instante, v(t) el cambio de posición respecto al tiempo (derivada de la posición) y a(t) define la variación de la velocidad en un lapso (derivada de la velocidad).Sin embargo, no basta con conocer únicamente las posiciones inicial (A) y final (B), sino que también es crucial analizar la trayectoria del sistema y cómo se lleva a cabo el movimiento, ya que esto determina la dinámica, eficiencia y suavidad del proceso.

(imagen de matematicamente como son)
(imagen de las curvas)

Mediante el análisis de las imágenes, se pueden deducir ecuaciones gobernadas por reglas geométricas.

## Reglas geométricas
La trayectoria del sistema depende de los tiempos de proceso, mientras que su perfil de movimiento se obtiene analizando la gráfica de velocidad (espacio/tiempo). A partir de esto, se establecen las siguientes ecuaciones: 

$$v = v_{0}+ \color{Magenta} a \color{Yellow} (t- t_{0})$$

* $$\color{Magenta} a$$ es la pendiente de la gráfica velocidad.
* El perfil tiene varias etapas de proceso. por esa razón se tiene en cuenta $$t_{0}$$ . En alguna otra etapa este valor ya no será 0, y afecta el valor de velocidad obtenido.

$$s= s_{0}+\frac{1}{2}\color{Red} (t-t_{0})\color{Cyan} (v_{0}+a(t-t_{0}))$$


