---
layout: post
title: Predicción de registros diarios en el RUNT
published: true
---
Este es un trabajo para el curso de aprendizaje estadístico de la universidad Nacional de Colombia sede Medellín, cuyo objetivo es poder construir un modelo estadistico que permita predecir el número de vehiculos registrados diariamente en el Registro Único Nacional de Tránsito (RUNT).

## Introducción
En el año 2014, tiempo en el que los colombianos se preparaban para ir nuevamente a votaciones para Congreso y Presidente Durante el primer semestre del año, los niveles de comercialización mensuales preveían un cierre de mercado entre las 310.000 a 315.000 unidades. A partir de septiembre, los registros superan los 30.000 ejemplares al mes, llegando a los 32.355 carros entregados en diciembre por efecto del Salón del Automóvil. Así, el promedio por mes fue de 28.305 automotores (Mantilla, 2018). 

A partir del 2015 empezaron los problemas. Aunque el primer trimestre fue bueno gracias al impulso del Salón del Automóvil, desde abril las ventas de carros se fueron a pique, dando como resultado una caída del 15,2% y la comercialización de 283.870 unidades. Las marcas se vieron muy golpeadas cuando el dólar pasó de $1.900 a más de $3.000 en menos de un año (Mantilla, 2018).

Aunque en 2016 el dólar logró treparse a los $3.400 en el primer trimestre, logró estabilizarse finalmente en el orden de los $3.000. La depreciación de nuestra moneda y la consiguiente alza de la inflación hizo que el Banco de la República, en una decisión tardía, aumentara los intereses al 7,75%. Al hacer costosa la financiación, las matrículas de carros llegaron a 253.698, una disminución de 11,7% (Mantilla, 2018).


## Descripcion de las variables
**1.** Se decide crear variables a partir de la fecha, obteniendo variables como día, mes y año, también se obtuvo el dia de la semana: lunes, martes, miercoles, jueves, viernes, sabado o domingo.

**2.** Se crearon variables indicadoras para los días festivos, semana santa y para la semana del salón internacional del automovil el cual es celebrado cada dos años. 

**3.** Se decide incluir 3 variables macroeconómicas importantes a la hora de vender un vehículo y estas son: 

   **-** La TRM que es la tasa representativa de mercado.

se calcula como el promedio aritmético de las tasas ponderadas de las operaciones de compra y de venta de dólares de los Estados Unidos de América a cambio de moneda legal Colombiana (Banco de la República,s.f.)

   **-** Las tasas de colocación del banco de la república.

   **-** El PIB.

Estas variables macro son registradas con las siguientes periodicidades:

   **-** PIB: trimestral
 
   **-** TRM: diaria
 
   **-** TC: mensuaL



## Análisis descriptivo
Se realiza una revisión del comportamiento historico del numero de registros teniendo en cuenta el mes, el dia de la semana y el año. Los resultados obtenidos se muestran a continuación:

![_config.yml]({{ site.baseurl }}/images/img_1.png)
En la figura 1 se evidencia el total de registros diarios para cada mes, evidenciando que los meses de junio, octubre, noviembre y diciembre tienen una mayor dispersion en los datos, tambien se muestra el comportamiento creciente con el paso de los meses a partir de septiembre; siendo diciembre el mes del año con mayor numero de registros. Las primas de mitad y final de año pueden ser un indicador de este comportamiento.


![_config.yml]({{ site.baseurl }}/images/img_2.png)
La figura 2 es muy similar a la que se presento en el item anterior, se evidencia el comportamiento creciente en los ultimos tres meses de cada año, pero a su vez, nos muestra como los años 2012 y 2013 presentan una mayor concentración y los años 2016 y 2017 tienen presencia de algunos valores extremos.


![_config.yml]({{ site.baseurl }}/images/img_3.png)
En la figura 3 se tiene en cuenta el numero de registros mensuales en el RUNT y se desagrega para cada uno de los años de historia, aca se puede evidenciar como los años 2014 y 2016 tienen un pico de crecimiento mas pronunciado que los demas años. Tambien se ve que en el 2017 (periodo de validación) no es tan drastico el crecimiento de noviembre a diciembre.



![_config.yml]({{ site.baseurl }}/images/img4.png)
En la figura 4 se hace la separación por día de la semana, donde se evidencia una disminución en los registros muy significativa para los días sábado y domingo, por el contrario los dias en los que se registran mas vehiculos son los jueves y los viernes.

### Criterio de seleccion de variables:
Para la selección de variables se utiliza el criterio del mejor subconjunto que tiene en cuenta todas las variables y muestra los resultados del R cuadrado ajustado, el BIC y el Cp de Mallows.

![_config.yml]({{ site.baseurl }}/images/img5.png)

![_config.yml]({{ site.baseurl }}/images/img6.png)

![_config.yml]({{ site.baseurl }}/images/img7.png)
 
  **-** En la figura 5 se observa que el mejor subconjunto es el de la tasa de colocación y el PIB con un rezago, la indicadora de festivos y semana santa y por el lado de los factores los días de la semana y los meses, teniendo asi un R cuadrado del 74%.

  **-** En la figura 6 se evidencia que el conjunto de variables que tiene el menor BIC es el mismo que el mencionado para el R2 pero incluyendo ademas la TRM rezagada 8 días.

  **-** En la figura 7, el conjunto de variables que tiene el menor Cp de Mallows es el mismo que para el del BIC.

Teniendo en cuenta los resultados obtenidos las variables que se incluyen en los modelos son las mostradas en la tabla 1.

![_config.yml]({{ site.baseurl }}/images/tabla1.png)


## Modelamiento
Para hacer las pruebas respectivas al modelo se toma desde 2012 hasta 2016 para hacer el entrenamiento del mismo y el 2017 para hacer la validación. 

Se decide usar tres metodologias diferentes y ponerlas en competencia para seleccionar el modelo con mejor desempeño teniendo en cuenta: R cuadrado para los datos de entrenamiento y validación, la consistencia del mismo para tener en cuenta el criterio de revisión y prevenir que haya una diferencia mayor al 10%.

### Metodologias:
**1.** Modelos lineales. 

**2.** Modelos lineales generalizados (GLM): familia Poisson.

**3.** Modelos aditivos generalizados para locación, escala y forma (GAMLSS): familia ZANBI.

Las familias que se tuvieron en cuenta para los modelos GLM y GAMLSS son discretas, es decir la variable respuesta proviene de  conteos (Amat Rodrigo, 2020).


![_config.yml]({{ site.baseurl }}/images/tabla2.png)
En la tabla 2 se evidencia que para el conjunto de entrenamiento todos los modelos propuestos presentan un R cuadrado superior al 82%, siendo el de mejor desempeño el modelo GLM con un 87.6% para este conjunto. Luego, para el conjunto de validacion se evidencia que el modelo lineal presenta una disminución significativa del R cuadrado con un valor del 66.7% mientras que los modelos GLM y GAMLSS presentan una metrica superior al 75%.

Finalmente se elige el modelo GAMLSS dada sus consistencia entre ambos conjuntos pues su cambio o disminucion en el desempeño es del 8.7%.




## Bibliografia
Banco de la República. (s.f.). Tasa de cambio del peso colombiano. Colombia. Obtenido de https://www.banrep.gov.co/es/glosario/trm

A., L. M. (1989). Determininates de la demanda de vehiculos en Colombia. Bogota.

Diaz, V. P. (2013). La Republica. 

Mantilla, Ó. J. (2018). El carro colombiano revista virtual. Obtenido de https://www.elcarrocolombiano.com/industria/2010-2018-el-sector-automotor-colombiano-en-tiempos-de-juan-manuel-santos/

Amat Rodrigo, J. (2020). GAMLSS: modelos aditivos generalizados para posición, escala y forma. Recuperado 14 de enero de 2022, de https://rpubs.com/Joaquin_AR/603234 



