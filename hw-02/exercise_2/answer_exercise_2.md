## 2.- Crear un objeto de tipo replicaSet a partir del objeto anterior con las siguientes especificaciones:
### Debe tener 3 replicas
Contenido del fichero pod-exercise02.yaml:

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_2/images/ReplicaSet.png)

Crear el replicaSet:          
kubectl apply -f pod-exercise02.yaml

### ¿Cúal sería el comando que utilizarías para escalar el número de replicas a 10?
kubectl scale --replicas=10 rs nginx-replicaset-exercise02

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_2/images/Escalar10.png)


### Si necesito tener una replica en cada uno de los nodos de Kubernetes, ¿qué objeto se adaptaría mejor? (No es necesario adjuntar el objeto)
Un DaemonSet (https://kubernetes.io/es/docs/concepts/workloads/controllers/daemonset/): 
"Un DaemonSet garantiza que todos (o algunos) de los nodos ejecuten una copia de un Pod. Conforme se añade más nodos al clúster, nuevos Pods son añadidos a los mismos. Conforme se elimina nodos del clúster, dichos Pods se destruyen. "