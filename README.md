## Ejemplo de Replicación con Docker

Este ejemplo muestra 5 contenedores:
1) Angular
2) NodeJS
3) Mongo1 "Primario"
4) Mongo2 "Secundario"
5) Mongo3 "Arbitro" 

Primero, hay que configurar los host. 
```
 127.0.0.1       mongo1 mongo2 mongo3
```

Segundo, al descargar o clonar el ejemplo, se tiene que instalar las depencias en los proyectos de Node y Angular.

```
 npm install
```
Tercero, dentro de la carpeta del proyecto tiene que ejecutar el siguiente comando, para crear y conectar los contenedores.
```
docker-compose up --build
```

Cuarto, hay que acceder al contenedor y ejecutar:
```
docker exec -it mongo1 mongo
```

Por último, se configura la replicación.
```
cfg= { _id : 'rs0', members: [ { _id : 0, host : "mongo1:27017" }, { _id : 1, host : "mongo2:27017" }, { _id : 2, host : "mongo3:27017", arbiterOnly: true } ] }
rs.initiate(cfg)
```

BONUS: verificar los campos guardados con "Robo 3T" o "Mongo Compass"