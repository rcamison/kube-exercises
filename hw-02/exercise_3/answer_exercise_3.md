## 3.- Crea un objeto de tipo service para exponer la aplicación del ejercicio anterior de las siguientes formas:

Crear un replicaset para el ejercicio:      
kubectl apply -f pod-exercise03.yaml  

### Exponiendo el servicio hacia el exterior (crea service1.yaml)
Hay que utilizar un servicio de tipo LoadBalacer. Necestiamos un ip publica para poderlo ver desde el exterior.    
Como no tengo un proveedor de servicio cloud para poder alojarlo y obtener la ip publica voy a simular el acceso con:    
minikube service nginx-exercise3-service1

Crear el service:    
kubectl apply -f service1.yaml 

### De forma interna, sin acceso desde el exterior (crea service2.yaml)
Hay que utilizar un servicio de tipo ClusterIP     
Crear el service:    
kubectl apply -f service2.yaml  

### Abriendo un puerto especifico de la VM (crea service3.yaml)
Hay que utilizar un servicio de tipo NodePort especificando el puerto especifico que se desea abrir          
Crear el service:    
kubectl apply -f service3.yaml  