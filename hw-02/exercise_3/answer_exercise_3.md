## 3.- Crea un objeto de tipo service para exponer la aplicación del ejercicio anterior de las siguientes formas:
### Exponiendo el servicio hacia el exterior (crea service1.yaml)
Hay que utilizar un servicio de tipo LoadBalacer. Necestiamos una DNS

### De forma interna, sin acceso desde el exterior (crea service2.yaml)
Hay que utilizar un servicio de tipo ClusterIP

### Abriendo un puerto especifico de la VM (crea service3.yaml)
Hay que utilizar un servicio de tipo NodePort especificando el puerto especifico que se desea abrir