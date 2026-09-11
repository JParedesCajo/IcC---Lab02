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

```bash
docker build -t lab02-api .
```
`lab02-api` corresponde al nombre asignado a la imagen y `.` indica que se utiliza el directorio actual como contexto de construcción.

```bash
docker run -d --rm -p 3000:3000 --name lab02-api-container lab02-api
```
Se uso para la ejecución de la imagen que se construyo.

```bash
docker compose up -d --build
```
Se aplico para la creación e inicio de los servicios definidos en el archivo docker-compose.yml

```bash
docker ps
```
Permite visualizar los contenedores actualmente en ejecución, se uso luego del docker run -d --rm -p.

```bash
docker compose ps
```
Permite visualizar estados de los servicios.

```bash
docker compose up -d --scale api=3
```
Permite definir la cantidad de contenedores que se ejecutarán para un servicio determinado, con lo pedido en el ejercicio, serán 3 instancias de servicio.

# INDICADORES

### `-y` 
Se uso cuando se ejecuto npm init, para poder aceptar automáticamente los valores predeterminados durante la creación del package.json.

### `-t`

El indicador `-t` permite asignar un nombre o etiqueta a la imagente durante el proceso de construcción.

### `-d`

Ejecuta el contenedor en segundo plano.

### `--rm`

Hace que docker elimine automáticamente el contenedor cuando se detenga.

### `-p 3000:3000`

Publica el puerto donde el primer 3000 es el puerto de la PC local (JPC) y el segundo el puerto del contenedor.

### `--name`

Sirve para asignar un nombre al contenedor.

### `--scale api =3`

Asigna las cantidades de contenedores (3).

## TIPOS DE REDES - DOCKER

**Bridge:** Permite la comunicación entre los contenedores dentro de una misma red Docker.

**Host:** Permite que el contenedor utilice directamente la red del host, reduciendo el aislamiento entre ambos

**None:** Deshabilita la conectividad de red del contenedor:

**Overlay:** Permite la comunicación entre contenedores que se encuentran en diferentes hosts Docker

**Macvlan:** Permite asignar una dirección MAC a los contenedores, haciendo que puedan aparecer dentro de la misma red como dispositivos independientes.

**IPvlan:** Permite integrar los contenedores directamente con una red existente utilizando direccionamiento IP.

**docker-compose_default**: Fue creado por Docker Compose, permitiendo la comunicación entre los servicios definidos. 

## TIPOS DE VOLUMENES - DOCKER

Docker dispone de diferentes mecanismos para almacenar y compartir información:

**Named Volumes:** Son volumenes administrados directamente por Docker y poseen un nombre definido.

**Anonymous Volumes:** Son volumenes administrados por Docker que no reciben un nombre definido por el usuario.

**Bind Mounts:** Permiten montar directamente un archivo o directorio existente del sistema host dentro de un contenedor.

**tmpfs:** Almacena temporalmente información en la memoria del host en lugar de escribirla de forma persistente en el disco.

Según el ejercicio se uso el volumen llamnado postgres_data para persistir la información generada por PostgreSQL

## CAPTURAS DE RESULTADOS - DESPLIEGUE

### SERVICIOS DESPLEGADOS

Se agrega evidencia de la ejecución de las tres instancias de la API y el servicio de PostgreSQL.

![Servicios desplegados](./capturas/compose-ps.png)

### VOLUMEN PERSISTENTE

Se agrega evidencia de la ejecución del volumen utilizado par la persistencia de PostgreSQL.

![Volumen Docker](./capturas/volume-ls.png)

### RED DOCKER

Se agrega evidencia de la red creada por Docker Compose para la comunicación entre los servicios.

![Red Docker](./capturas/network-ls.png)

# CREDITOS

- Paredes Cajo Jeffry
- ID: 000241130