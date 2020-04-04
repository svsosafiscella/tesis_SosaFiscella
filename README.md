# Tesis de Lincenciatura de Sofía Valentina Sosa Fiscella

Partimos de una carpeta que contenga el archivo.par con los parámetros del modelo de timing, un directorio llamado templates (que contiene los templates de cada antena que vamos a usar) y dos directorios llamados A1 y A2 (que contienen las observaciones .pfd que vamos a usar, junto a sus correspondientes .polycos y .bestprof).

-----------------------------
Para hacer timing según S/N
-----------------------------

1) Corremos el programa "sn_TOAs", el cual carga todas las observaciones dadas a Pypulse y las separa en distintos conjuntos según su relación S/N. Después, para cada uno de esos conjuntos, calcula los TOAs de las observaciones y las guarda en archivos .tim

2) Corremos el programa "sn_residuos", el cual a partir de los archivos .tim generados en el paso anterior, calcula (para cada conjunto de S/N) el error sistemático que sumado a los errores de los TOAs resulta en un cálculo de residuos con un chi²~1. Luego calcula el correspondiente valor de RMS, y grafica ambas cantidades en función del S/N de cada conjunto.


-----------------------------
Para hacer timing según nbins
-----------------------------

1) Corremos el programa "arrugado.ipynb". Este creará 6 nuevas carpetas por antena, las cuales contendrán copias de las observaciones originales pero arrugadas a nbins=512,256,128,64,32. Adicionalmente también copia a las nuevas carpetas los archivos .polycos y .bestprof de cada observacin, junto al archivo .par del púlsar en cuestión.

2) Corremos el programa "arrugado_templates.ipynb", el cual crea copias arrugadas de los templates, los cuales son guardados a su vez dentro de la misma carpeta templates (los templates usados para este trabajo se encuentran dentro de la carpeta templates del repositorio).
