Desafío 5: Complejo inmobiliario de Natalia
===========================================
## Contexto:
Natalia es una ingeniera estructural y está diseñando un complejo inmobiliario en cerro Caŕcel. Tiene el objetivo de construir un cierto número de pisos minimizando el riesgo de caída frente a un terremoto y aluvión.

Se levanta el riesgo en cada suelo para el primer piso. Cada piso tendrá un 10% más de riesgo (o un 10% menos de seguridad) con respecto al piso inferior. No se trata de sólo sumar 0.1, sino que:
$$f_{r2} = 0.1 + 0.9 \cdot f_{r1}$$
Ya que del factor seguridad se da:
$$f_{r} = 1 - f_{s}$$
$$f_{s2} = 0.9 \cdot f_{s1}$$
A su vez el valor de piso será el producto entre $10.000.000, el coeficiente de seguridad (diferencia de 1 y el riesgo) y el número de piso n.
$$precio = 10.000.000 \cdot (1 - f_r) \cdot n$$ 
Ayuda a Natalia a edificar el complejo inmobiliario (en caso de que utilice bibliotecas externas debe agregarlas en requirements.txt)

## Parte 1: Planificar efificios
Implentar función place_floors en utils.py que recibe 2 parámetros
* risks: matriz (lista de listas) con el riesgo en cada sector
* planned_floors: Número de pisos a construir
y retorne una matriz con el número de pisos construido en cada parte
Si 2 o más lugares tienen la misma magnitud de riesgo, se prioriza en columna inferior y luego en fila superior (más al norte).

## Parte 2: Valorar precios de pisos
Implentar función value_floors en utils.py valorando el precio de cada piso . Se recibe 1 parámetro
* risks: matriz (lista de listas) con el riesgo en cada sector
* planned_floors: Número de pisos a construir
y retorne una matriz con el valor de cada piso construido en cada parte (matriz de 3d. El alto debe coincidir a número de pisos del edificio más alto)
 
## Parte 3: Grafico en 3D
En chart_floors  de utils.py genere gráfico 3D y pinte cada piso acorde a su valor en 8 colores en forma equidistante de acuerdo a los rangos de precios, siendo el valor mínimo inclusive y el valor máximo exclusive (excepto en el rango de más valor). Se muestra rango ejemplo si valor mínimo en 1000 y máximo 2600:
|Color|Rango ejemplo|
|-|-|
|\#EE0000|1000-1200|
|\#CC2200|1200-1400|
|\#AA4400|1400-1600|
|\#886600|1600-1800|
|\#668800|1800-2000|
|\#44AA00|2000-2200|
|\#22CC00|2200-2400|
|\#00EE00|2400-2600|
Parámetros de entrada:
* risks: matriz (lista de listas) con el riesgo en cada sector
* planned_floors: Número de pisos a construir
El piso 1 parte de altura 0 y su techo es valor 1, mientras que piso 2 tiene el suelo en valor 1 y techo en valor 2, etc. Los pisos deben estar emplazados con el centro en el valor y ancho y largo 1. Por ejemplo el piso en valor x=1 debe estar entr -0.5 y 0.5.

BONUS: ¿Y si la vista al mar genera valor? Establece un valor extra de $10.000.000 a los pisos que tenga linea vista al norte (primera fila). Considera que el plano de construcción es plano y no importa y da lo mismo si se ve la playa o mar adentro. ¿Y si generar otro valor extra de $10.000.000 a los que tienen línea vista a la playa (suponiendo que el plano de contrucción está a 1 km de distancia y a 100 metros sobre nivel del mar)?

Corre los tests con:

python inmobilaria.py