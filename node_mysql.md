#### 1.- Crear carpeta de inicio del proyecto
````
    mkdir miproyecto
    cd miproyecto
````
#### 2.- Iniciar node
````
    npm init -y
````
#### 3.- Crear el archivo principal ( index.js )

#### 4.- Instalar componente Express
````
    npm i express
````
#### 5.- Habilitar un servidor
````
    a)  En el archivo package.json crear una nueva linea.
        "type": "module"
    b)  Instalar el paquete nodemon.
        npm i nodemon -D
    c)  Crear un script de ejecucion en el archivo package.json seccion "Scripts"
        "dev": "nodemon index.js"
    d)  Correr el servidor
        npm run dev
````
#### 6.- En index.js habilitar express
````
    import express from 'express'
    const app = express()
    app.listen(3000)
````
#### 7.- Crear rutas (endPoint )
````
    app.get('/miruta', (req, res) => res.send('datos del metodo get') )
    app.post('/rutapost', .........)
    .....
````
#### 8.- Instalar componente mysql2
````
    npm i mysql2
````
#### 9.- Crear archivo de Coneccion
#### 10.- Crear los archivos (cotroladores, routes, ....)
#### 11.- instalar modulo dotenv.  Para control de variables de entorno
````
     npm i dotenv
````
