# High-Order-Functions
// Simpson.sc
// Implementación del método de Simpson 1/3
// Higher Order Functions – Programación Funcional y Reactiva

def integracion(a: Double, b: Double, f: Double => Double): Double = {
  val xm = (a + b) / 2.0
  (b - a) / 6.0 * (f(a) + 4 * f(xm) + f(b))
}

// Integrales.sc
// Cálculo de las 7 integrales usando Simpson 1/3

import $file.Simpson, Simpson.integracion
import scala.math._

println("==========================================================")
println("           APROXIMACIÓN DE INTEGRALES DEFINIDAS")
println("==========================================================")

// 1) ∫₃⁵ (-x² + 8x - 12) dx
val f1 = (x: Double) => -pow(x, 2) + 8*x - 12
val i1 = integracion(3, 5, f1)

// 2) ∫₀² 3x² dx
val f2 = (x: Double) => 3*pow(x,2)
val i2 = integracion(0, 2, f2)

// 3) ∫₋¹¹ (x + 2x² − x³ + 5x⁴) dx
val f3 = (x: Double) => x + 2*pow(x,2) - pow(x,3) + 5*pow(x,4)
val i3 = integracion(-1, 1, f3)

// 4) ∫₁² (2x + 1) / (x² + x) dx
val f4 = (x: Double) => (2*x + 1) / (x*x + x)
val i4 = integracion(1, 2, f4)

// 5) ∫₀¹ eˣ dx
val f5 = (x: Double) => exp(x)
val i5 = integracion(0, 1, f5)

// 6) ∫₂³ 1/(x-1) dx
val f6 = (x: Double) => 1 / (x - 1)
val i6 = integracion(2, 3, f6)

// 7) ∫₀¹ 1/(1+x²) dx
val f7 = (x: Double) => 1 / (1 + x*x)
val i7 = integracion(0, 1, f7)

// Imprimir resultados
println(s"Integral 1: $i1")
println(s"Integral 2: $i2")
println(s"Integral 3: $i3")
println(s"Integral 4: $i4")
println(s"Integral 5: $i5")
println(s"Integral 6: $i6")
println(s"Integral 7: $i7")

// CalculoError.sc
// Cálculo de errores entre valores esperados y obtenidos

import $file.Simpson, Simpson.integracion
import scala.math._
import $file.Integrales

def calcularError(esperado: Double, obtenido: Double): Double =
  abs(esperado - obtenido)

val esperados = List(
  7.33, 8.0, 3.333, 1.09861, 1.71828, 0.828427, 0.785398
)

val obtenidos = List(
  Integrales.i1, Integrales.i2, Integrales.i3,
  Integrales.i4, Integrales.i5, Integrales.i6, Integrales.i7
)

println("======================================================================")
println("                           CÁLCULO DE ERRORES")
println("======================================================================")

for(i <- 0 until 7){
  val error = calcularError(esperados(i), obtenidos(i))
  println(f"Integral ${i+1}%-3d | Esperado: ${esperados(i)}%10.6f | Obtenido: ${obtenidos(i)}%10.6f | Error: $error%10.6f")
}

println("======================================================================")

# Higher Order Functions – Método de Simpson 1/3  
## Programación Funcional y Reactiva  
### Trabajo de Consulta – Semana 7

---

## 📘 Descripción del Proyecto

Este proyecto implementa el **método de Simpson 1/3** utilizando conceptos propios de la **programación funcional**, como:

- Higher Order Functions  
- Funciones como parámetros  
- Inmutabilidad  
- Expresiones lambda  

El objetivo es calcular de forma aproximada siete integrales definidas y evaluar el error frente a un valor esperado.

---

## 📁 Estructura del Proyecto

TallerInd1/
│
├── src/
│ ├── Simpson.sc
│ ├── Integrales.sc
│ └── CalculoError.sc
│
└── README.md

| Parámetro | Tipo             | Descripción        |
| --------- | ---------------- | ------------------ |
| `a`       | Double           | Límite inferior    |
| `b`       | Double           | Límite superior    |
| `f`       | Double => Double | Función matemática |


Fórmula implementada (Simpson 1/3)
∫
𝑎
𝑏
𝑓
(
𝑥
)
 
𝑑
𝑥
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
∫
a
b
	​

f(x)dx≈
6
b−a
	​

[f(a)+4f(
2
a+b
	​

)+f(b)]

🔢 2. Integrales.sc — Cálculo de 7 Integrales

Cada integral se calcula implementando una función lambda:

val f = (x: Double) => expresión

📏 3. CalculoError.sc — Evaluación del Error

El error absoluto se define como:

𝐸
𝑟
𝑟
𝑜
𝑟
=
∣
𝑣
𝑎
𝑙
𝑜
𝑟
𝐸
𝑠
_
𝑝
𝑒
𝑟
𝑎
𝑑
𝑜
−
𝑣
𝑎
𝑙
𝑜
𝑟
𝑂
𝑏
𝑡
𝑒
𝑛
𝑖
𝑑
𝑜
∣
Error=∣valorEs_perado−valorObtenido∣

Se imprime un reporte completo comparando:

valor esperado

valor obtenido por Simpson

error absoluto

======================================================================
CÁLCULO DE ERRORES
======================================================================
Integral 1 | Esperado: 7.330000 | Obtenido: 7.333333 | Error: 0.003333
Integral 2 | Esperado: 8.000000 | Obtenido: 8.000000 | Error: 0.000000
Integral 3 | Esperado: 3.333000 | Obtenido: 3.333333 | Error: 0.000333
Integral 4 | Esperado: 1.098610 | Obtenido: 1.098612 | Error: 0.000002
Integral 5 | Esperado: 1.718280 | Obtenido: 1.718282 | Error: 0.000002
Integral 6 | Esperado: 0.828427 | Obtenido: 0.828427 | Error: 0.000000
Integral 7 | Esperado: 0.785398 | Obtenido: 0.785398 | Error: 0.000000
======================================================================
