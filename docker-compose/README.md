# Ejercicio - Lab 02 

Trabjar un docker-compose, especificando configuración y comandos para despliegue. Debe permitir lo siguiente:

- 3 copias de una API build local
- Configuración BD
- Uso de volúmenes
- Uso de variables de entorno 
- Responder los tipos de redes y los tipos de volumenes que existen en docker (README)

## STACK

- Node.js (para la creación de las API)
- Express
- Docker

## ESTRUCTURA

- LAB02/
    docker-compose/ 
        - api/
            - node_modules
            - src/
                 index.js
        - package-lock.json
        - package.json
    .gitignore
    README.md

## COMANDOS

```bash
npm init -y    
```
Se uso para poder generar el archivo package.json, en la cual se guardarala información y dependencias del proyecto.

```bash
npm install express
```
Se aplico para poder instalar el framework que se uso para implementar el servidor web y definir los endpoints HTTP de la API.

```bash
node src/index.js
```
Sirve para ejecutar el el archivo principal de la API, la cual está úbicada en el src dentro de api, ayuda a comprobar que este en funcionamiento local en el puerto que se le coloco, 3000 en este caso.

# INDICADORES

-y: Se uso cuando se ejecuto npm init, para poder aceptar automáticamente los valores predeterminados durante la creación del package.json.

## ENTORNOS




# CREDITOS

- Paredes Cajo Jeffry
- ID: 000241130