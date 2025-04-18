# Control de movimiento clase 20/03/25
# Introducción
En el ámbito del control de sistemas, los perfiles de movimiento son herramientas fundamentales para describir el desplazamiento de un mecanismo a lo largo del tiempo. Estos perfiles permiten analizar el recorrido total y los tiempos de trabajo en cada etapa del proceso, lo cual es esencial para garantizar precisión, eficiencia y un comportamiento predecible del sistema. Entre los tipos más comunes de perfiles se encuentran los lineales y los que presentan curvas en “S”, cada uno con sus propias ecuaciones para calcular parámetros como velocidad, posición, aceleración e incluso jerk (la derivada de la aceleración), el cual puede provocar cambios bruscos que afectan a componentes como motores o actuadores.
Estos perfiles pueden aplicarse tanto en sistemas de un solo eje como en configuraciones multieje. En el caso del movimiento multieje, se identifican tres modos de funcionamiento: movimiento en un solo eje, slew motion y movimiento interpolado. Cada uno responde a diferentes prioridades, ya sea maximizar la velocidad en un eje específico o sincronizar los tiempos de movimiento entre varios ejes. Esta clasificación permite adaptar el perfil a los requerimientos específicos del sistema, asegurando un desplazamiento preciso y eficiente.

# 1. Perfiles de movimiento
Como su nombre lo indica, es la trayectoria de la carga desde un punto A hasta un punto B, este movimiento puede variar según el sistema utilizado. En un solo eje, el movimiento es lineal y sigue una dirección única, mientras que en sistemas multieje las trayectorias se vuelven más complejas, combinando movimientos en diferentes direcciones. El perfil de movimiento describe el comportamiento del sistema en términos de posición, velocidad, aceleración e incluso el jerk (tasa de cambio de la aceleración), lo que permite optimizar la suavidad del desplazamiento.

# 2. Cinemática
Estudia el comportamiento de la posición s(t), la velocidad v(t) y la aceleración a(t) en función del tiempo. En un sistema de un solo eje s(t) describe la posición en cualquier instante, v(t) el cambio de posición respecto al tiempo (derivada de la posición) y a(t) define la variación de la velocidad en un lapso (derivada de la velocidad).Sin embargo, no basta con conocer únicamente las posiciones inicial (A) y final (B), sino que también es crucial analizar la trayectoria del sistema y cómo se lleva a cabo el movimiento, ya que esto determina la dinámica, eficiencia y suavidad del proceso.

* Matematicamente :

$$\color{Orchid} v(t)=\frac{ds}{dt}$$

$$\color{Yellow}  a(t)=\frac{dv}{dt}$$

Ahora bien, si se desea analizar estas funciones de manera inversa, se realizarian por medio de integrales, como por ejemplo: 

$$s = \int_{}^{} v(t)dt$$

$$v = \int_{}^{} a(t)dt$$


![Figura 1](lol.png)

Figura 1. Cinemática de la posición, la velocidad y la aceleración.

* Se puede inferir por medio de la anterior imagen que el perfil de movimiento de la posición con respecto al tiempo, tendrá un movimiento parabólico; El area bajo la curva del perfil de movimiento de la velocidad es el punto B (Punto final) del perfil de movimiento de posicion en ese instante de tiempo; Y, 
Mediante el análisis de las imágenes, se pueden deducir ecuaciones gobernadas por reglas geométricas.

## 2.1 Reglas geométricas
La trayectoria del sistema depende de los tiempos de proceso, mientras que su perfil de movimiento se obtiene analizando el perfil de velocidad (espacio/tiempo). A partir de esto, se establecen las siguientes ecuaciones: 

$$v = v_{0}+ \color{Magenta} a \color{Yellow} (t- t_{0})$$

* $$\color{Magenta} a$$ es la pendiente del perfil de velocidad.
* El perfil tiene varias etapas de proceso. por esa razón se tiene en cuenta $$t_{0}$$ . En alguna otra etapa este valor ya no será 0, y afecta el valor de velocidad obtenido.

$$s= s_{0}+\frac{1}{2}\color{Red} (t-t_{0})\color{Cyan} (v_{0}+a(t-t_{0}))$$

## 💡Ejemplo 1:
Encontrar la posición y la aceleración en t= 5 segundos.

![Figura 2](C_1.png)

Figura 2. Perfiles de movimiento Ejemplo 1.

Solución:

$$a =(10 in/s)/(5s) = 2 s^{2}$$

Ahora para la posición:

$$s = 0+\frac{1}{2}(5)(10) = 25 in$$

En la anterior ecuación se puede apreciar como la posición es el área del triangulo que se forma en el perfil de velocidad. Y el area no es más que $$(base*altura)/2$$ y se suma por la posición inicial. En alguna otra etapa del proceso u otro proceso, este valor ya no será 0. 

## 💡Ejemplo 2:
Un eje está viajando a una velocidad de 10 cm/s. En t=5 s empieza a disminuir la velocidad como se ve en el perfil. Cual es la posición del eje cuando se detiene? Asuma que empieza a acelerar a 25 cm.

![Figura 3](C_2.png)

Figura 3. Perfiles de movimiento Ejemplo 2.

Solución: 

$$a = \frac{0-10}{15-5} = -1 cm/s^{2}$$

$$s = 25 + \frac{10*10}{2}= 75 cm$$

## 2.2 Perfiles de movimiento comunes

En el diseño de perfiles de movimiento, los dos enfoques más comunes son el trapezoidal (ampliamente utilizado por su facilidad de análisis, basado en las ecuaciones geométricas mencionadas) y la curva S (sigmoidal o gaussiana). Mientras el perfil trapezoidal prioriza la rapidez, la curva S ofrece mayor suavidad a costa de un tiempo de recorrido ligeramente mayor. Sin embargo, un factor crítico en ambos casos es el jerk (cambio brusco de aceleración), representado matemáticamente como pulsos o deltas de Dirac. Este fenómeno genera fuerzas repentinas que pueden dañar componentes mecánicos, como los ejes de un motor, debido a tensiones o flexiones indeseadas. Por ello, los sistemas de control modernos permiten ajustar y minimizar el jerk, optimizando así la durabilidad y precisión del movimiento.

![Figura 4](C_3.png)

Figura 4. Perfiles de movimiento comunes.

### 2.2.1 Perfil de velocidad trapezoidal Geométrico 

![Figura 5](C_4.png)

Figura 5. Perfil de velocidad trapezoidal.

Como se aprecia en la imagen, el modelo asume tiempos iguales para las fases de aceleración y desaceleración. No obstante, en aplicaciones reales esta simetría no siempre se cumple: existen sistemas que requieren una desaceleración más rápida por requisitos de seguridad, o una aceleración prolongada para alcanzar velocidades críticas. Estas variaciones responden a necesidades específicas de desempeño del sistema. 

$$t_{a}=t_{d}=\frac{V_{m}}{a}$$

El tiempo total del movimiento sería entonces:

$$t_{TOTAL}=t_{a}+t_{m}+t_{d}$$

Ahora bien, para conocer el recorrido total L:

$$L= \frac{t_{a}v_{m}}{2}+t_{m}v_{m}+\frac{t_{d}v_{m}}{2}$$

$$L= v_{m}(t_{a}+t_{m})$$

Y despejando de la ecuación anterior se puede conocer el tiempo de movimiento, que sería:

$$t_{m}=\frac{L}{v_{m}}-t_{a}$$

### 2.2.2 Perfil de velocidad trapezoidal Analítico 

![Figura 6](C_4.png)

Figura 6. Perfil de velocidad trapezoidal.

Según la grafica de velocidad, se tomarán unos intervalos para conocer cada punto con más exactitud, continuidad y suavidad:

$$0 < t < t_{a}$$

Para este intervalo el tiempo, la velocidad y la posicion iniciales serán 0

$$s(t)= \int_{0}^{t_{a}}= at dt$$

$$s(t)= \frac{1}{2}a(t_{a})^{2}$$

Para el siguiente tramo se tiene en cuenta que el tiempo inicial, la posiicion inicial y la velocidad inicial cambian debido a que es una nueva etapa en donde estos valores corresponden a la posición, tiempo y velocidad resultante de la anterior etapa de movimiento:

$$t_{a} < t < (t_{a}+t_{m})$$

Entonces: 

$$s(t) = s(t_{a})+\int_{t_{a}}^{t} Vm dt$$

$$s(t_{a})+V_{m}(t-t_{a})$$

Para el siguiente tramo se tiene en cuenta vuelve a cambiar los valores iniciales:

Intervalo: $$t_{a}+t_{m}\lt t\lt Ttotal$$

$$s(t)= s(t_{a}+t_{m})+\int_{t_{a}+t_{m}}^{t}-a(t-(t_{a}+t_{m}))+V_{m} dt$$

$$s(t) = s(t_a + t_m) + \left. \left( V_m t - \frac{1}{2} a (t - (t_a + t_m))^2 \right) \right|_{t_a + t_m}^{t}$$

## 💡Ejemplo 3:
El eje x de un robot Gantry debe moverse 10 cm, La máxima aceleración permitida en este eje es de $$1cm/s^{2}$$. Si se desea mover el eje a una velocidad máxima de 2 cm/s, cuanto tiempo tomará hacer este movimiento.

![Figura 7](C_5.png)

Figura 7. Robot Gantry.

$$t_{a}= t_{d}=\frac{2 cm/s}{1 cm/s^{2}} = 2 s$$

$$t_{m}= \frac{10 cm}{2 cm/s}-2 s = 3s$$

$$t_{TOTAL}= 2s+3s+2s = 7s$$

![Figura 8](mio2.png)

Figura 8. Perfil de velocidad trapezoidal para Robot Gantry.

En la imagen se pueden observar los tiempos de aceleración, movimiento y desaceleración correspondientes. 

# 📚 Ejercicio 1
Dado el perfil de velocidad de la figura, calcule $$S_{A},S_{B},S_{C}$$ usando las reglas geométricas y el método analítico del perfil del movimiento.

![Figura 9](C_6.png)

Figura 9. Perfil de velocidad.

   Solución:

   * Método Geométrico
     
     $$S_{A}= \frac{(0.5)(4)}{2}+0 = 1cm$$
     
     $$S_{B}= 2\frac{(4)(5)}{2}+1 = 21cm$$
     
     $$S_{C}= \frac{(0.5)(4)}{2}+21 = 22cm$$

   * Método analítico

     $$S_{A}= \frac{1}{2}(8)(0.5)^{2}= 1cm$$

     $$S_{B}= 1+4(5.5-0.5)= 21cm$$

     $$S_{C}= 21+\left[4(6)-\frac{1}{2}(-8)(6-5.5)^{2} \right]=22 cm$$

Se confirma que con ambos métodos la posicion A será en 1 cm, la posición B en 21 cm y la posición c en 22 cm.

# 📚 Ejercicio 2
El eje z de un robot seguidor de linea debe moverse 500 m, La máxima aceleración permitida en este eje es de $$200 m/s^{2}$$. Si se desea mover el eje a una velocidad máxima de 300 m/s, cuanto tiempo tomará hacer este movimiento.

$$t_{a}= t_{d}=\frac{300 m/s}{200 m/s^{2}} = 1.6 s$$

$$t_{m}= \frac{500 m}{300 m/s}-1.6 s = 0.066 s$$

$$t_{TOTAL}= 1.6s+0.066s+1.6s = 3.26 s$$

*El ejercicio demuestra que en la industria hay sistemas en los que el tiempo de movimiento es casi nulo debido a los cambios/conmutaciones tan rápidas que este deba ahcer para cumplir su función. 

![Figura 10](xd.png)

Figura 10. Perfil de velocidad.

# Conclusiones
Los perfiles de movimiento sirven para observar y predecir el comportamiento de muchos sistemas industriales. Aunque pueden parecer complejos, es posible simplificarlos mediante ecuaciones geométricas o analíticas, establecidas a partir de perfiles generales o similares ya conocidos. Se puede evidenciar que existen sistemas que no son simétricos, por ejemplo, cuando el tiempo de aceleración y el tiempo de desaceleración son diferentes. Esto puede deberse a que un motor necesita reducir su velocidad más rápidamente para cumplir con una tarea específica, o a que un actuador debe alcanzar un punto de operación (setpoint) con mayor rapidez que la empleada para descender de él, dependiendo de la etapa del proceso en la que se encuentre. Se concluye que el análisis detallado de estos perfiles permite adaptar el comportamiento dinámico del sistema a las exigencias del proceso, optimizando tanto la eficiencia como la seguridad operativa. Asimismo, se concluye que el tiempo total de movimiento (Tm) variará en función del tipo de trabajo a realizar, ya que cada aplicación impone condiciones particulares de aceleración, velocidad y frenado. 

# Referencias
[1] Login aulas 2025. (s/f). Edu.co. Recuperado el 12 de abril de 2025, de https://aulas.ecci.edu.co/mod/resource/view.php?id=217550

[2] J. Villagrá, V. Milanés, J. Pérez y T. de Pedro, "Control basado en PID inteligentes: aplicación al control de crucero de un vehículo a bajas velocidades," Revista Iberoamericana de Automática e Informática Industrial, vol. 7, no. 4, pp. 44–52, oct. 2010. Enlace. [Accedido: 12-abr-2025].​ 
