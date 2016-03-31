# chapter{Postprocesando archivos ODB}

## Procesando información básica

### Partes

Las partes o geometrías son las entidades básicas en Abaqus, y a partir las cuales se construye el ensamble 
o modelo. Las partes pueden ser bidimensionales o tridimensionales, deformables o rígidas, dependiendo 
de las características del cuerpo físico a representar.

Para leer información acerca de las partes incluidas en un archivo ODB, debemos primeramente leer el archivo 
y enseguida acceder al diccionario `parts`.

En el siguiente código se imprimen en consola todas las partes que contiene el archivo **ejemplo.odb**, 
y adicionalmente se imprime el tipo de la parte en cuestión (Deformable, Analítica,...).

	from odbAccess import openOdb

	dbpath = "ejemplo.odb"
	odb = openOdb(path=dbpath)
	for _name,_prt in odb.parts.items():
		print _name, _prt.type

Pero claro, siempre que sea posible es mejor escribir código que pueda ser reutilizado, en forma de funciones y/o clases 
que puedan almacenarse en módulos y posteriormente importarse en un script donde sean utilizadas.

En el siguiente código se define una función `get_parts` que básicamente lee la información de las partes que 
componen el archivo de salida, devolviendo una lista de tuplas con los nombres y tipos de las partes.

	from odbAccess import *

	def get_parts(dbpath):
		odb = openOdb(path=dbpath)
		_parts = []
		for _name,_prt in odb.parts.items():
			_type = _prt.type
			_parts.append((_name,_type))
		return _parts


### Secciones

### Materiales

### Pasos de carga

### Interacciones

### Instancias
