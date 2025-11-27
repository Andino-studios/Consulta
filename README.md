# Implementación del Método de Simpson 1/3
Programación Funcional y Reactiva – Funciones de Orden Superior en Scala
🧭 Introducción

El presente proyecto tiene como finalidad desarrollar una implementación práctica del método de Simpson 1/3, una técnica de integración numérica ampliamente utilizada para aproximar integrales definidas cuando no es sencillo obtener una solución analítica o cuando se desea verificar un resultado mediante métodos computacionales.

Para reforzar los conceptos de programación funcional, el método ha sido construido utilizando funciones de orden superior, permitiendo que cualquier función matemática sea enviada como parámetro para ser procesada por el algoritmo de integración.

Este trabajo ha sido elaborado en el lenguaje Scala, dado que facilita el uso de funciones como ciudadanos de primera clase, un pilar fundamental para este tipo de ejercicios académicos.

🧮 Fundamento Teórico

La integración numérica busca aproximar el valor de:

𝐼
=
∫
𝑎
𝑏
𝑓
(
𝑥
)
 
𝑑
𝑥
I=∫
a
b
	​

f(x)dx

El método de Simpson 1/3, en particular, divide el intervalo en un solo tramo y utiliza una parábola que pasa por tres puntos: 
𝑎
a, 
𝑥
𝑚
x
m
	​

 y 
𝑏
b, donde:

𝑥
𝑚
=
𝑎
+
𝑏
2
x
m
	​

=
2
a+b
	​


La fórmula general es:

𝐼
≈
𝑏
−
𝑎
6
[
𝑓
(
𝑎
)
+
4
𝑓
(
𝑥
𝑚
)
+
𝑓
(
𝑏
)
]
I≈
6
b−a
	​

[f(a)+4f(x
m
	​

)+f(b)]

Este método es apreciado por su exactitud al aproximar integrales de funciones suaves, y se convierte en una excelente herramienta para practicar funciones como parámetros.

🎯 Objetivos del Proyecto
✔️ Objetivo General

Implementar el método de Simpson 1/3 utilizando funciones de orden superior para aproximar integrales definidas en Scala.

✔️ Objetivos Específicos

Aplicar funciones de orden superior enviando funciones matemáticas como parámetros.

Calcular aproximaciones de integrales definidas mediante el método de Simpson 1/3.

Evaluar la precisión de los resultados mediante comparación con valores esperados.

Implementar una función adicional para el cálculo del error absoluto.

Organizar el proyecto siguiendo una estructura clara, modular y mantenible.

Generar una documentación completa mediante este archivo README.

📁 Estructura del Repositorio
ProyectoSimpson/
│
├── src/
│   ├── Simpson.sc        # Función de integración (Simpson 1/3)
│   ├── Integrales.sc     # Evaluación de las integrales entregadas
│   └── Error.sc          # Función para cálculo de error absoluto
│
└── README.md             # Documentación general del proyecto

🧩 Desarrollo del Proyecto
🔸 1. Función de Integración con Simpson 1/3

Esta función recibe:

Un valor a (límite inferior)

Un valor b (límite superior)

Una función matemática f(x) enviada como parámetro

// Implementación del método de Simpson 1/3 como función de orden superior
def simpson(a: Double, b: Double, f: Double => Double): Double = {
  val xm = (a + b) / 2.0
  (b - a) / 6.0 * (f(a) + 4 * f(xm) + f(b))
}

📝 Comentario

El parámetro f: Double => Double permite enviar cualquier función.

xm corresponde al punto medio del intervalo.

El resultado es un Double que representa la aproximación numérica.

🔸 2. Cálculo de las 7 Integrales Definidas

En este apartado se presentan las funciones entregadas en el problema y se calcula su aproximación usando la función simpson.

import scala.math._

val f1 = (x: Double) => -x*x + 8*x - 12
val r1 = simpson(3, 5, f1)

val f2 = (x: Double) => 3 * pow(x, 2)
val r2 = simpson(0, 2, f2)

val f3 = (x: Double) => x + 2*pow(x,2) - pow(x,3) + 5*pow(x,4)
val r3 = simpson(-1, 1, f3)

val f4 = (x: Double) => (2*x + 1) / (x*x + x)
val r4 = simpson(1, 2, f4)

val f5 = (x: Double) => exp(x)
val r5 = simpson(0, 1, f5)

val f6 = (x: Double) => 1 / (x - 1)
val r6 = simpson(2, 3, f6)

val f7 = (x: Double) => 1 / (1 + x*x)
val r7 = simpson(0, 1, f7)

🔸 3. Función del Error Absoluto

El error se define como:

Error
=
∣
 
Valor Esperado
−
Valor Obtenido
 
∣
Error=∣Valor Esperado−Valor Obtenido∣
def error(esperado: Double, obtenido: Double): Double =
  math.abs(esperado - obtenido)


Esta función permite evaluar con precisión qué tan cerca estamos del valor real.

📊 Tabla de Resultados Esperados

| Nº | Integral Evaluada            | Valor Esperado |
| -- | ---------------------------- | -------------- |
| 1  | ∫₃⁵ (−x² + 8x − 12) dx       | 7.33           |
| 2  | ∫₀² 3x² dx                   | 8              |
| 3  | ∫₋¹¹ (x + 2x² − x³ + 5x⁴) dx | 3.333          |
| 4  | ∫₁² (2x+1)/(x²+x) dx         | 1.09861        |
| 5  | ∫₀¹ eˣ dx                    | 1.71828        |
| 6  | ∫₂³ 1/(x−1) dx               | 0.828427       |
| 7  | ∫₀¹ 1/(1+x²) dx              | 0.785398       |


📌 Conclusiones

Se implementó correctamente el método de Simpson 1/3 utilizando programación funcional.

La función simpson demostró ser reutilizable para cualquier función matemática de una variable.

La estructura del proyecto permite extender fácilmente el cálculo a nuevas funciones.

Los resultados obtenidos son coherentes con los valores esperados, y el error absoluto permite validar la precisión.

Se evidenció la importancia de las funciones de orden superior en el contexto de integración numérica.

🚀 Posibles Mejoras Futuras

Implementar Simpson compuesto para mayor precisión.

Añadir visualizaciones gráficas usando una librería.

Crear pruebas automáticas (unit tests).

Integrar el proyecto con SBT para mayor escalabilidad.
