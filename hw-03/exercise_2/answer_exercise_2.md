## 1.- [StatefulSet] Crear un StatefulSet con 3 instancias de MongoDB (ejemplo visto en clase). Se pide:       
• Habilitar el clúster de MongoDB      
• Realizar una operación en una de las instancias a nivel de configuración y verificar que el cambio se ha aplicado al resto de instancias      

### SOLUCION:    
- Crear un service y un statefulset (ver archivo Statefulset.yaml)  
kubectl apply -f Statefulset.yaml    
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_2/images/statefulset.png)

    
- Abrir el bash del primer pod   
 kubectl exec -it mongodb-0 -c mongodb bash    
    
- Ejecutar el comando mongo para entrar en la shell de MongoDB    
mongo    
    
- Iniciar el replica set (cluster de MongoDB para replicacion)     
rs.initiate( { _id: "MainRepSet", version: 1, members: [ { _id: 0, host: "mongodb-0.mongodb.default.svc.cluster.local:27017"}, { _id: 1, host: "mongodb-1.mongodb.default.svc.cluster.local:27017"}, { _id: 2, host: "mongodb-2.mongodb.default.svc.cluster.local:27017" } ]});
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_2/images/shell01.png)

    
Los valores para el comando anterior se han obtenido mediante el siguiente comando        
hostname -f   
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_2/images/shell.png)
   
- Crear una db (dbPrueba) y una collection (tablaPrueba)    
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_2/images/createdb.png)

     
- Entrar en otro pod y comprobar que la db y la collection existen      
 kubectl exec -it mongodb-1 -c mongodb bash    
 mongo    
 
- Permitir las operaciones en los miembros secundarios        
 rs.secondaryOk()     

- Ir a la bd creada (dbPrueba) y comprobar si existe la collection (tablaPrueba) mediante los siguientes comandos      
 use dbPrueba   
 show collections    
  
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_2/images/pod2.png)

      
## Diferencias que existiría si el montaje se hubiera realizado con el objeto de ReplicaSet    
Las diferencias son:   
 - Con ReplicaSet el volumen que se monta se comparte entre todos los pods, con statefulset cada pod tiene su volumen
 - Con Statefulset los pods se nombran segun el nombre que se le ha dado mas un secuencial (0, 1, 2 ...), en cambio con ReplicaSet se nombran con el nombre asignado mas un hash
