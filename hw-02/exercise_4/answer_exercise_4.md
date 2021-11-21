## 4.- Crear un objeto de tipo deployment con las especificaciones del ejercicio 1.
Ejecutar los siguientes comandos:            
- Crear el deployment:               
kubectl apply -f deployment_01_exercise_4.yaml

Comprobar los datos. Si no se especifica StrategyType por defecto es RollingUpdate          
kubectl get deployments          
kubectl get pods                
kubectl describe deployment nginx-deployment-exercise04             
 
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_4/images/Deployment01.png)

### Despliega una nueva versi�n de tu nuevo servicio mediante la t�cnica �recreate�
Ejecutar:                
kubectl apply -f deployment_02_recreate_exercise_4.yaml

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_4/images/Deployment02.png)

### Despliega una nueva versi�n haciendo �rollout deployment�
Ejecutar:                 
kubectl apply -f deployment_03_rollingupdate_exercise_4.yaml

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_4/images/Deployment03.png)

### Realiza un rollback a la versi�n generada previamente

Ejecutar:                  
kubectl rollout undo deployment nginx-deployment-exercise04

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_4/images/Deployment04.png)


### Traza del replicaset

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_4/images/DeploymentFull.png)