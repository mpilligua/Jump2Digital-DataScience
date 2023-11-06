# Jump2Digital DataScience - Maria Pilligua
## 1. Introduccion

En este projecto se han usado 2 datasets: 
- El principal propuesto que presenta información sobre la media del alquiler mensual (€/mes) y por superficie (€/m2) de la ciudad de Barcelona: Alquiler mensual medio (€/mes) y por superficie (€/m2) de la ciudad de Barcelona - 2017_Alquiler_precio_trim.csv - Open Data Barcelona
- El dataset propuesto que contiene información sobre la exposición a los ruidos de la población, del Mapa Estratégico de Ruido de la ciudad de Barcelona: Población expuesta en los niveles de ruido del Mapa Estratégico de Ruido de la ciudad de Barcelona - 2017_Poblacio_exposada_barris_Mapa_Estrategic_Soroll_BCN_LONG.csv - Open Data Barcelona

El objetivo era unir estos 2 datasets y processar los datos para poder hacer conclusiones y aplicar un pca (principal component analysis)



## 2. Depuración de los datos

El dataset principal data información del alquiler en funcion de cada barrio de barcelona, el segundo data información del ruido de cada barrio en funcion de el nivel de ruido y del componente que hacia el ruido, por tanto por cada barrio teniamos 260 filas. Para poder unirlos he agrupado los datos del segundo dataset en base de cada barrio y los he agregado al dataset principal, de manera que el dataset unido tiene el numero de columnas del primer dataset + 260

Como pasos para preprocessar lo datos, he convertido todas columnas categoricas a numericas usando un label encoder de sklearn, he eliminado algunas features como el año que no aportaban información (ya que solo tenemos datos de 2017), he eliminado todas las filas que tenian nan values porque habia muy pocos (38 filas), también he eliminado alguna feature que era redundante como el nombre del barrio ya que teniamos el codigo del barrio. 

## 3. Resultados

Como nos han quedado tantas dimensiones al unir los dos datasets podemos aplicar pca para reducir dimensiones. Para assegurarnos de no eliminar demasiada información al reducir dimensiones nos quedaremos con el numero de componentes que nos premita explicar un 95% de los datos del dataset original, esto ha resultado ser 25 features. Esto implica que con 25 columnas somos capaces de explicar los mismos datos manteniendo una varianza del 95%.

El dataset con los datos unidos nos permite hacer un pequeño estudio de la correlación entre el precio medio de alquiler y el nivel de ruido. Esto lo haremos en el dataset despues de aplicar pca. 

## 4. Conclusiones

Despues de esto, podemos ver que estos dos datasets no estan nada correlacionados y por tanto el nivel de ruido no es un factor muy importante para decidir el precio medio del alquiler en barcelona. 
Sin embargo el nivel de ruido puede ser relevante si lo tenemos en cuenta junto con otros datos, como por ejemplo, el nivel medio de insonorización de las viviendas o el nivel medio de altura de los edificios. Ya que el mismo nivel de ruido puede ser un factor importante si o no dependiendo de si tu vivienda esta bien insonorizada o si vives en un piso muy alto donde el ruido no se llega a apreciar.


En caso de querer ejecutar el codigo, he dejado un fichero llamado requierements.txt que permite installar el envirnment con las librerias necesarias para poder ejecutarlo. Para installarlo solo hay que poner: 

  conda create -n <environment-name> --file requirements.txt
