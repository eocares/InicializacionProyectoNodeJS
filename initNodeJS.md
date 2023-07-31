# Iniciar Proyecto NodeJS con NPM y dependencias básicas.
- Verifico version de node
```console
$> node -v
v7.9.0
```

- Verifico version de npm
```console
$> npm -v
4.2.0
```

- Si npm no esta instalado, el siguiente comando lo instala de forma global
```console
$> npm install -g npm
```

- Si npm no esta actualizado, el siguiente comando lo actualiza de forma global
```console
$> npm update -g npm
```

- Creo el directorio de mi proyecto
```console
$> mkdir my_app_node
```
- Me ubico en el directorio
```console
$> cd my_app_node
```

- NPM utiliza el archivo package.json para almacenar todos los datos relevantes a nuestra aplicación.
- Nos realizara varias preguntas para configurar adecuadamente la app.
- Este archivo también se guardarán las dependencias de paquetes del proyecto junto con su configuración básica (nombre del proyecto, versión, etc).
```console
$> npm init
```

- La consola mostrara algo similar a los siguiente:
```text
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg> --save` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
name: (my_app_node)
version: (1.0.0)
description: mi demo node app
entry point: (index.js)
test command: nodemon index.js
git repository:
keywords: ES
author: edgardo001
license: (ISC)
About to write to C:\Users\datasoft-edgardo\Desktop\my_app_node\package.json:

{
  "name": "my_app_node",
  "version": "1.0.0",
  "description": "mi demo node app",
  "main": "index.js",
  "scripts": {
    "test": "nodemon index.js"
  },
  "keywords": [
    "ES"
  ],
  "author": "edgardo001",
  "license": "ISC"
}


Is this ok? (yes) yes
```

- Instala las libreria en el directorio del app, y guarda su referencia en "package.json"
```console
$> npm install express --save
$> npm install body-parser --save
$> npm install nodemon --save
```

- Crear el archivo index.js el cual inicia el app, este se debe crear en la raiz del app
```text
var express = require('express');
var bodyParser = require('body-parser');

var app = express();
var port = process.env.PORT || 3525;

// Convierte una petición recibida (POST-GET...) a objeto JSON
app.use(bodyParser.urlencoded({extended:false}));
app.use(bodyParser.json());

app.get('/', function(req, res){
	res.status(200).send({
		message: 'GET Home route working fine!'
	});
});

app.listen(port, function(){
	console.log(`Server running in http://localhost:${port}`);
	console.log('Defined routes:');
	console.log('	[GET] http://localhost:3525/');
});
```

- Inicia el app desde "index.js" como indica el "package.json" en la seccion "scripts"
```console
$> npm test
```

REFERENCIAS:

http://expressjs.com/es/starter/installing.html

http://gorkamu.com/2017/06/aprender-nodejs-setup-inicial/

http://gorkamu.com/2017/07/como-organizar-un-proyecto-node-js/
