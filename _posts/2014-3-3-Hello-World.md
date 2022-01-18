---
layout: post
title: Registros de vehículos en el RUNT
published: true
---
## Introducción
Este es un trabajo para el curso de aprendizaje estadístico de la universidad Nacional de Colombia sede Medellín, cuyo objetivo es poder construir un modelo estadistico que permita predecir el número de autos registrados diariamente en el Registro Único Nacional de Tránsito (RUNT).

La venta de vehículos en el año 2013 a 2018, se vio marcada por la venta de vehículos con un comportamiento en el marcado bajo e inestable, ciertas causas que explican esto son las políticas rígidas de la industria ensamble y autopartes (comprende la actividad del montaje de motores, la fabricación de partes y piezas de vehículos utilizadas en el ensamble y como repuestos) y finalmente la llegada de vehículos híbridos y eléctricos (Mantilla, 2018) (A., 1989)
En el año 2013 las ventas de autos no fueron nada buenas en la mayoría de los meses, aunque el sector asegura, que es lógica una caída de este tipo tras dos años de comercialización récord de unidades, en donde se percibieron pequeños indicios perpetuar esta tendencia negativa en lo que resta del año; excepto en el último trimestre en donde el banco de la republica tuvo que reducir la tasa de interés, pero esto no evito en decreciente 5,2% en la venta de vehículos. La venta de vehículos nuevos de enero y febrero de 2013 fue menor a los mismos meses del año pasado, un 4,96% y 11,98% respectivamente. (Diaz, 2013)
Llegamos a 2014, tiempo en el que los colombianos se preparaban para ir nuevamente a votaciones para Congreso y Presidente Durante el primer semestre del año, los niveles de comercialización mensuales preveían un cierre de mercado entre las 310.000 a 315.000 unidades. A partir de septiembre, los registros superan los 30.000 ejemplares al mes, llegando a los 32.355 carros entregados en diciembre por efecto del Salón del Automóvil. Así, el promedio por mes fue de 28.305 automotores (Mantilla, 2018). 
A partir del 2015 empezaron los problemas. Aunque el primer trimestre fue bueno gracias al impulso del Salón del Automóvil, desde abril las ventas de carros se fueron a pique, dando como resultado una caída del 15,2% y la comercialización de 283.870 unidades. Las marcas se vieron muy golpeadas cuando el dólar pasó de $1.900 a más de $3.000 en menos de un año. (Mantilla, 2018)
Aunque en 2016 el dólar logró treparse a los $3.400 en el primer trimestre, logró estabilizarse finalmente en el orden de los $3.000. La depreciación de nuestra moneda y la consiguiente alza de la inflación hizo que el Banco de la República, en una decisión tardía, aumentara los intereses al 7,75%. Al hacer costosa la financiación, las matrículas de carros llegaron a 253.698, una disminución de 11,7%. (Mantilla, 2018)




## DESCRIPCION DE VARIABLES
1.Se decidio crear variables a partir de la fecha, obteniendo variables como día, mes y año, también se obtuvo el dia de la semana: lunes, martes, miercoles, jueves, viernes, sabado o domingo.

2.Se crearon variables indicadoras para los días festivos, semana santa y para la semana del salón internacional del automovil el cual es celebrado cada dos años. 

3.Se decide incluir 3 variables macroeconómicas importantes a la hora de vender un vehículo y estas son: 
-La TRM que es la tasa representativa de mercado

se calcula como el promedio aritmético de las tasas ponderadas de las operaciones de compra y de venta de dólares de los Estados Unidos de América a cambio de moneda legal Colombiana (Banco de la República,s.f.)

-Las tasas de colocación del banco de la república
-El PIB.

Estas variables macro son registradas con las siguientes periodicidades:
 -PIB: trimestral
 -TRM: diaria
 -TC: mensuaL



## ANÁLISIS DESCRIPTIVO
Se realiza una revisión del comportamiento historico del numero de registros teniendo en cuenta el mes, el dia de la semana y el año. Los resultados obtenidos se muestran en las figura 1, figura 2, figura 3 y figura 4

![_config.yml]({{ site.baseurl }}/images/img_1.png)
En la figura 1 se evidencia el total de registros diarios para cada mes, evidenciando que los meses de junio, octubre, noviembre y diciembre tienen una mayor dispersion en los datos, tambien se muestra el comportamiento creciente con el paso de los meses a partir de septiembre; siendo diciembre el mes del año con mayor numero de registros.

![_config.yml]({{ site.baseurl }}/images/img_2.png)

![_config.yml]({{ site.baseurl }}/images/img_3.png)

![_config.yml]({{ site.baseurl }}/images/img_4.png)

![_config.yml]({{ site.baseurl }}/images/img_5.png)

![_config.yml]({{ site.baseurl }}/images/img_6.png)

![_config.yml]({{ site.baseurl }}/images/img_7.png)


## MODELAMIENTO
Para hacer las pruebas respectivas al modelo se toma desde 2012 hasta 2016 para hacer el entrenamiento del modelo y el 2017 para hacer el test.


## BIBLIOGRAFIA
Banco de la República. (s.f.). Tasa de cambio del peso colombiano. Colombia. Obtenido de https://www.banrep.gov.co/es/glosario/trm

A., L. M. (1989). Determininates de la demanda de vehiculos en Colombia. Bogota.

Diaz, V. P. (2013). La Republica. 

Mantilla, Ó. J. (2018). El carro colombiano revista virtual. Obtenido de https://www.elcarrocolombiano.com/industria/2010-2018-el-sector-automotor-colombiano-en-tiempos-de-juan-manuel-santos/



