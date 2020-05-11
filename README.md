## Ejemplo de persistencia Poliglota en Docker

Este es un ejercicio que muesta como contenedor docker puede persistir en distintos motores de base de datos.

Primero hay que configurar los host
```
 127.0.0.1       mongo1 mongo2 mongo3
```


Despues de descargar el ejemplo, se tiene que instalar las depencias en los proyectos de Node y Angular

```
 npm install
```
Luego dentro de la carpeta del proyecto tiene que ejecutar el siguiente comando.

```
docker-compose up -d
docker exec -it mongo1 mongo


cfg= { _id : 'rs0', members: [ { _id : 0, host : "mongo1:27017" }, { _id : 1, host : "mongo2:27017" }, { _id : 2, host : "mongo3:27017", arbiterOnly: true } ] }
rs.initiate(cfg)
```