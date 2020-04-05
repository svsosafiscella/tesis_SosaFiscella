# Tesis de Lincenciatura de Sofía Valentina Sosa Fiscella

Partimos de una carpeta que contenga el archivo.par con los parámetros del modelo de timing y dos directorios llamados A1 y A2, que contienen las observaciones .pfd que vamos a usar junto a sus correspondientes .polycos y .bestprof.

-----------------------------
Crear los templates
-----------------------------

Lo primero que necesitamos para poder calcular residuos es un template. En este trabajo optamos por tomar la observación de mayor S/N de cada antena y sacarle ruido para usarla como template. Ello está implementado en el programa "generate_templates.ipynb", el cual busca de entre todas las observaciones .pfd de cada antena aquella de mayor S/N, la convierte en un .fits mediante Psrchive, y le quita ruido por medio de la rutina psrsmooth. Los templates resultantes son almacenados dentro de una nueva carpeta, creada por el programa, llamada templates. Los nombres de las observaciones usadas como templates son guardas en archivos de salida aparte, de modo que después puedan ser levantadas por los programas que calculan TOAs, y que así sean excluídas del cálculo de TOAs.

-----------------------------
Timing según S/N
-----------------------------

1) Corremos el programa "sn_TOAs.ipynb", el cual carga todas las observaciones dadas a Pypulse y las separa en distintos conjuntos según su relación S/N. Después, para cada uno de esos conjuntos, calcula los TOAs de las observaciones y las guarda en archivos .tim.

2) Corremos el programa "sn_residuos.ipynb", el cual a partir de los archivos .tim generados en el paso anterior, calcula (para cada conjunto de S/N) el error sistemático que sumado a los errores de los TOAs resulta en un cálculo de residuos con un chi²~1. Luego calcula el correspondiente valor de RMS, y grafica ambas cantidades en función del S/N de cada conjunto.


-----------------------------
Timing según nbins
-----------------------------

1) Corremos el programa "arrugado.ipynb". Este creará 6 nuevas carpetas por antena, las cuales contendrán copias de las observaciones originales pero arrugadas a nbins=512,256,128,64,32. Adicionalmente también copia a las nuevas carpetas los archivos .polycos y .bestprof de cada observacin, junto al archivo .par del púlsar en cuestión.

2) Corremos el programa "arrugado_templates.ipynb", el cual crea copias arrugadas de los templates, los cuales son guardados a su vez dentro de la misma carpeta templates.

3) Corremnos el programa "nbins_timing.ipynb", el cual calcula los TOAs para las observaciones de cada de uno de los conjuntos generados en el paso anterior, y las guarda en archivos .tim. A partir de estos TOAs, calcula los residuos de las observaciones dentro de cada conjunto y el valor de RMS correspondiente a los mismos. Luego, grafica los valores de RMS obtenidos en función del nbins de las observaciones de cada conjunto.
