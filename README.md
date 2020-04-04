# Tesis de Lincenciatura de Sofía Valentina Sosa Fiscella

Partimos de una carpeta que contenga el archivo .par con los parámetros del modelo de timing, un directorio llamado templates (que contiene los templates de cada antena que vamos a usar) y dos directorios llamados A1 y A2 (que contienen las observaciones .pfd que vamos a usar, junto a sus correspondientes .polycos y .bestprof).

-----------------------------
Para hacer timing según nbins
-----------------------------

1) Corremos el programa "arrugado.ipynb". Este creará 6 nuevas carpetas por antena, las cuales contendrán copias de las observaciones originales pero arrugadas a nbins=512,256,128,64,32. Adicionalmente también copia a las nuevas carpetas los archivos .polycos y .bestprof de cada observacin, junto al archivo .par del púlsar en cuestin.

2)
