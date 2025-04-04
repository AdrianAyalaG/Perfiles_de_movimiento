# Control de movimiento clase 20/03/25
# Introducción


# 1. Perfiles de movimiento
Como su nombre lo indica, es la trayectoria de la carga desde un punto A hasta un punto B, este movimiento puede variar según el sistema utilizado. En un solo eje, el movimiento es lineal y sigue una dirección única, mientras que en sistemas multieje las trayectorias se vuelven más complejas, combinando movimientos en diferentes direcciones. El perfil de movimiento describe el comportamiento del sistema en términos de posición, velocidad, aceleración e incluso el jerk (tasa de cambio de la aceleración), lo que permite optimizar la suavidad del desplazamiento.

# 2. Cinemática
Estudia el comportamiento de la posición s(t), la velocidad v(t) y la aceleración a(t) en función del tiempo. En un sistema de un solo eje s(t) describe la posición en cualquier instante, v(t) el cambio de posición respecto al tiempo (derivada de la posición) y a(t) define la variación de la velocidad en un lapso (derivada de la velocidad).Sin embargo, no basta con conocer únicamente las posiciones inicial (A) y final (B), sino que también es crucial analizar la trayectoria del sistema y cómo se lleva a cabo el movimiento, ya que esto determina la dinámica, eficiencia y suavidad del proceso.

(imagen de matematicamente como son)
(imagen de las curvas)

Mediante el análisis de las imágenes, se pueden deducir ecuaciones gobernadas por reglas geométricas.

## 2.1 Reglas geométricas
La trayectoria del sistema depende de los tiempos de proceso, mientras que su perfil de movimiento se obtiene analizando el perfil de velocidad (espacio/tiempo). A partir de esto, se establecen las siguientes ecuaciones: 

$$v = v_{0}+ \color{Magenta} a \color{Yellow} (t- t_{0})$$

* $$\color{Magenta} a$$ es la pendiente del perfil de velocidad.
* El perfil tiene varias etapas de proceso. por esa razón se tiene en cuenta $$t_{0}$$ . En alguna otra etapa este valor ya no será 0, y afecta el valor de velocidad obtenido.

$$s= s_{0}+\frac{1}{2}\color{Red} (t-t_{0})\color{Cyan} (v_{0}+a(t-t_{0}))$$

## 💡Ejemplo 1:
Encontrar la posición y la aceleración en t= 5 segundos.

(Insertar la imagen de las graficas)

Solución:

$$a =(10 in/s)/(5s) = 2 s^{2}$$

Ahora para la posición:

$$s = 0+\frac{1}{2}(5)(10) = 25 in$$

En la anterior ecuación se puede apreciar como la posición es el área del triangulo que se forma en el perfil de velocidad. Y el area no es más que $$(base*altura)/2$$ y se suma por la posición inicial. En alguna otra etapa del proceso u otro proceso, este valor ya no será 0. 

## 💡Ejemplo 2:
Un eje está viajando a una velocidad de 10 cm/s. En t=5 s empieza a disminuir la velocidad como se ve en el perfil. Cual es la posición del eje cuando se detiene? Asuma que empieza a acelerar a 25 cm.

(intertar imagen de las gráficas)

Solución: 

$$a = \frac{0-10}{15-5} = -1 cm/s^{2}$$

$$s = 25 + \frac{10*10}{2}= 75 cm$$

(Insertar la imagen de matlab)

## 2.2 Perfiles de movimiento comunes

En el diseño de perfiles de movimiento, los dos enfoques más comunes son el trapezoidal (ampliamente utilizado por su facilidad de análisis, basado en las ecuaciones geométricas mencionadas) y la curva S (sigmoidal o gaussiana). Mientras el perfil trapezoidal prioriza la rapidez, la curva S ofrece mayor suavidad a costa de un tiempo de recorrido ligeramente mayor. Sin embargo, un factor crítico en ambos casos es el jerk (cambio brusco de aceleración), representado matemáticamente como pulsos o deltas de Dirac. Este fenómeno genera fuerzas repentinas que pueden dañar componentes mecánicos, como los ejes de un motor, debido a tensiones o flexiones indeseadas. Por ello, los sistemas de control modernos permiten ajustar y minimizar el jerk, optimizando así la durabilidad y precisión del movimiento.

(Insertar grafica)

### 2.2.1 Perfil de velocidad trapezoidal Geométrico 

(Insertar mi grafica) 

Como se aprecia en la imagen, el modelo asume tiempos iguales para las fases de aceleración y desaceleración. No obstante, en aplicaciones reales esta simetría no siempre se cumple: existen sistemas que requieren una desaceleración más rápida por requisitos de seguridad, o una aceleración prolongada para alcanzar velocidades críticas. Estas variaciones responden a necesidades específicas de desempeño del sistema. 

$$t_{a}=t_{d}=\frac{V_{m}}{a}$$

El tiempo total del movimiento sería entonces:

$$t_{TOTAL}=t_{a}+t_{m}+t_{d}$$

Ahora bien, para conocer el recorrido total L:

$$L= \frac{t_{a}v_{m}}{2}+t_{m}v_{m}+\frac{t_{d}v_{m}}{2}$$

$$L= v_{m}(t_{a}+t_{m})$$

Y despejando de la ecuación anterior se puede conocer el tiempo de movimiento, que sería:

$$t_{m}=\frac{L}{v_{m}}-t_{a}$$

### 2.2.2 Perfil de velocidad trapezoidal Anlítico 

(Insertar grafica) 
(Poner ecuaciones analiticas) 

## 💡Ejemplo 3:
El eje x de un robot Gantry debe moverse 10 cm, La máxima aceleración permitida en este eje es de $$ 1cm/s^{2}$$. Si se desea mover el eje a una velocidad máxima de 2 cm/s, cuanto tiempo tomará hacer este movimiento.

(Insertar imagen)

$$t_{a}= t_{d}=\frac{2 cm/s}{\frac{2}{2}} = 2 s$$

$$t_{m}= \frac{10 cm}{2 cm/s}-2 s = 3s$$

$$t_{TOTAL}= 2s+3s+2s = 7s$$

(Insertar trapezoidal que hare yo)

# 📚 Ejercicios
1. Dado el perfil de velocidad de la figura, calcule $$S_{A},S_{B},S_{C}$$ usando las reglas geométricas y el método analítico del perfil del movimiento.
 (Insertar grafico)

   Solución:

   * Método Geométrico
     
     $$S_{A}= \frac{(0.5)(4)}{2}+0 = 1cm$$
     
     $$S_{B}= 2\frac{(4)(5)}{2}+1 = 21cm$$
     
     $$S_{C}= \frac{(0.5)(4)}{2}+21 = 22cm$$

   * Método analítico

     $$S_{A}= \frac{1}{2}(8)(0.5)^{2}= 1cm$$

     $$S_{B}= 1+4(5.5-0.5)= 21cm$$

     $$S_{C}= 21+\left[ 4(6)-\frac{1}{2}(-8)(6-5.5)^{2} \right]=22 cm$$

