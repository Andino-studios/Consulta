🌐 Proyecto: Integración Numérica con el Método de Simpson 1/3
Programación Funcional • Funciones de Orden Superior • Scala

Este repositorio contiene una implementación funcional del método de Simpson 1/3, una técnica clásica de integración numérica usada para aproximar el valor de integrales definidas.
El desarrollo se realizó aplicando funciones de orden superior, enviando funciones como parámetros dentro de Scala.

📘 ¿Qué es el Método de Simpson 1/3?

Es una estrategia que permite aproximar el valor de:

∫
𝑎
𝑏
𝑓
(
𝑥
)
 
𝑑
𝑥
∫
a
b
	​

f(x)dx

Usando la fórmula:

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
𝑎
+
𝑏
2
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

[f(a)+4f(
2
a+b
	​

)+f(b)]

Este método utiliza un punto intermedio:

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

🎯 Propósitos del Trabajo

Comprender y aplicar funciones de orden superior.

Enviar funciones como argumentos en Scala.

Implementar un método de integración numérica.

Evaluar integrales específicas y compararlas con valores de referencia.

Medir el error de aproximación mediante una función dedicada.

📂 Estructura del Repositorio
ProyectoSimpson/
├── src/
│   ├── Simpson.sc
│   ├── Integrales.sc
│   └── Error.sc
└── README.md

🧩 1. Función Principal de Integración (Simpson.sc)
// Método Simpson 1/3 implementado como función de orden superior
def simpson(a: Double, b: Double, f: Double => Double): Double = {
  val xm = (a + b) / 2.0
  (b - a) / 6.0 * (f(a) + 4 * f(xm) + f(b))
}

🧩 2. Evaluación de las 7 Integrales (Integrales.sc)
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

println(s"Resultado 1: $r1")
println(s"Resultado 2: $r2")
println(s"Resultado 3: $r3")
println(s"Resultado 4: $r4")
println(s"Resultado 5: $r5")
println(s"Resultado 6: $r6")
println(s"Resultado 7: $r7")

🧩 3. Función de Cálculo de Error (Error.sc)
def error(esperado: Double, obtenido: Double): Double =
  math.abs(esperado - obtenido)

// Ejemplo de uso:
// println(error(7.33, r1))

📊 Valores de Referencia
| # | Integral                     | Valor Esperado |
| - | ---------------------------- | -------------- |
| 1 | ∫₃⁵ (−x² + 8x − 12) dx       | 7.33           |
| 2 | ∫₀² 3x² dx                   | 8              |
| 3 | ∫₋¹¹ (x + 2x² − x³ + 5x⁴) dx | 3.333          |
| 4 | ∫₁² (2x+1)/(x²+x) dx         | 1.09861        |
| 5 | ∫₀¹ eˣ dx                    | 1.71828        |
| 6 | ∫₂³ 1/(x−1) dx               | 0.828427       |
| 7 | ∫₀¹ 1/(1+x²) dx              | 0.785398       |


Este proyecto demuestra la combinación entre programación funcional y métodos numéricos, permitiendo reutilizar funciones y aplicar operaciones matemáticas de forma modular.
Además, el cálculo del error facilita la comparación con valores reales para evaluar la precisión del método de Simpson.
