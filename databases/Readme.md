## TUTORIAL SOBRE LO QUE HE APRENDIDO EN ESTA PRÁCTICA 

En esta práctica se ha aprendido a parsear un documento en RDF, un formato de XML, y convertirlo a JSON, un lenguaje de texto que permite visulizar la información de una forma mucho más jerárquica y estructurada que en XML. La herramienta que se ha usado para esta tarea es NODE.js, un framework de Javascript.

Se ha usado la versión de JSON conocidad Limited JSON, una versión que enfatiza mucho más la jerarquía en los datos. 

Una de las librerías de Node.js es Cheerio, que es de gran utilidad para manipular los datos, genera un Document Object Model de fácil manejo y comprensión.

En el proceso para obtener los datos en JSON, se ha aplicado el Behavioral Driven Development, o desarrollo guiado por comportamiento, una metodología de desarrollo que consiste en aplicar tres pasos para desarrollar cada unidad de software en un proyecto:

		-Primero definir un conjunto de pruebas para la unidad
		-Después implementar la unidad
		-Finalmente verificar que la implementación de la unidad haga exitosas las pruebas


Para aplicar el BDD, se han utilizado programas como Mocha y Chai.

Se ha hecho uso de la herramienta gulp, para automatizar tareas, como la descarga del fichero fuente en RDF (del proyecto Gutemberg) que posteriormente se iba a parsear, para instalarlo se aplicó el comando:

	npm install gulp@3.9.1

	npm install --save gulp-shell

Estas son las tareas definidas en el gulpfile.js:


	gulp.task("c5-get-guttenberg", shell.task(
	    /* curl option -O, --remote-name
	        Write  output to a local file named like the remote file we get. (Only the file part of the remote file is used, the path
	        is cut off.)
	        The file will be saved in the current working directory. If you want the file saved in a different directory,  make  sure
	        you change the current working directory before invoking curl with this option.
	        The remote file name to use for saving is extracted from the given URL, nothing else, and if it already exists it will be
	        overwritten.
	    */
	    'cd transforming-data-and-testing-continuously-chapter-5/data && ' +
	    'curl -O https://www.gutenberg.org/cache/epub/feeds/rdf-files.tar.bz2 &&' +
	    /*
	    -x      Extract to disk from the archive.  If a file with the same name appears more than once in the archive, each copy will be
	          extracted, with later copies overwriting (replacing) earlier copies.
	    -j      (c mode only) Compress the resulting archive with bzip2(1).  In extract or list modes, this option is ignored.  Note that,
	          unlike other tar implementations, this implementation recognizes bzip2 compression automatically when reading archives.
	    -f file
	            Read the archive from or write the archive to the specified file.  The filename can be - for standard input or standard
	          output.
	    -v      Produce verbose output.  In create and extract modes, tar will list each file name as it is read from or written to the
	         archive.  In list mode, tar will produce output similar to that of ls(1).  Additional -v options will provide additional
	         detail.
	    */
	    'tar -xvjf rdf-files.tar.bz2'
	));



Se ha creado una estructura de directorios, donde se implementó el código para transformar la información:
	
	mkdir databases
	mkdir data



El directorio databases contiene todos los programas y ficheros con código que hemos desarollado para convertir los datos de XML a JSON, las pruebas de BDD.

El directorio data contiene los ficheros de datos fuente, todos los libros del proyecto Gutemberg en formate RDF.

Dentro del directorio databases creamos el directorio test, 