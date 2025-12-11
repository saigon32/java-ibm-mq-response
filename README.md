# Java mq response

video: https://www.youtube.com/watch?v=ZTXQq9hxlV8

microservicio que permite recibir, procesar y responder mensajeria sobre colas mq, es necesario subirlo para que se orqueste con java-ibm-mq

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/158ef467-2fff-4844-a2c8-eade0eb5dd73" />


```sh
docker run -e LICENSE=accept -e MQ_QMGR_NAME=QM1 -p 1414:1414 -p 9443:9443 -d --name ibmmq -e MQ_APP_PASSWORD=passw0rd ibmcom/mq
```

https://localhost:9443/ibmmq/console/login.html#

- admin
- passw0rd

- Colas temporales

setmqaut -m QM1 -n SYSTEM.DEFAULT.MODEL.QUEUE -t queue -p app +get +put +inq +dsp

```sh
docker container exec -it ibmmq setmqaut -m QM1 -n SYSTEM.DEFAULT.MODEL.QUEUE -t queue -p app +get +put +inq +dsp
```

input-queue: "DEV.QUEUE.2"



```sh
docker container exec -it ibmmq sh
/opt/mqm/samp/bin/amqsgetc DEV.QUEUE.1 QM1
```

- Comandos
```sh
# Display queue manager
dspmq

# Ejecutar comandos dentro del QM
runmqsc QM1

  # Display queue 
  dis qlocal(DEV.QUEUE.1)
  dis qlocal(AMQ.6503235B256C1301)
  
  # Delete queue (Si no esta en uso)
  delete qlocal(AMQ.6503235B256C1301)
  
  # Obtener conexión
  DIS CONN(*)  WHERE(OBJNAME EQ AMQ.6503235B256C1301)
  stop conn(441F036500130240)

```

