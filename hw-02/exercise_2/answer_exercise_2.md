## 2.- Crear un objeto de tipo replicaSet a partir del objeto anterior con las siguientes especificaciones:
### Debe tener 3 replicas
Contenido del fichero pod-exercise02.yaml:

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_2/images/ReplicaSet.png)

Crear el replicaSet:          
kubectl apply -f pod-exercise02.yaml

### �C�al ser�a el comando que utilizar�as para escalar el n�mero de replicas a 10?
kubectl scale --replicas=10 rs nginx-replicaset-exercise02

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_2/images/Escalar10.png)


### Si necesito tener una replica en cada uno de los nodos de Kubernetes, �qu� objeto se adaptar�a mejor? (No es necesario adjuntar el objeto)
Un DaemonSet (https://kubernetes.io/es/docs/concepts/workloads/controllers/daemonset/): 
"Un DaemonSet garantiza que todos (o algunos) de los nodos ejecuten una copia de un Pod. Conforme se a�ade m�s nodos al cl�ster, nuevos Pods son a�adidos a los mismos. Conforme se elimina nodos del cl�ster, dichos Pods se destruyen. "