## 1.- Crea un pod de forma declarativa con las siguientes especificaciones (ref. enunciado)

Contenido del fichero pod-exercise01.yaml:

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_1/images/Pod.png)
          
Crear el pod          
kubectl create -f pod-exercise01.yaml

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_1/images/01_CreatePod.png)
          
### 1.1.- ¿Cómo puedo obtener las últimas 10 líneas de la salida estándar (logs generados por la aplicación)?
Ejecutar:
kubectl logs nginx-pod-exercise01 --tail 10

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_1/images/02_Logs.png)


### 1.2.- ¿Cómo podría obtener la IP interna del pod? Aporta capturas para indicar el proceso que seguirías.
Opcion 1: Ejecutar:
kubectl describe pods nginx-pod-exercise01

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_1/images/03_IP_01.png)

Opcion 2: Ejecutar:
kubectl get pod -o wide

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_1/images/03_IP_02.png)

### 1.3.- ¿Qué comando utilizarías para entrar dentro del pod?
Ejecutar:
kubectl exec -it nginx-pod-exercise01 -- sh

### 1.4.- Necesitas visualizar el contenido que expone NGINX, ¿qué acciones debes llevar a cabo?
Ejecutar port-forward para redireccionar el puerto 8080 (o el que queramos) de nuestra máquina y el puerto 80 del pod de nginx
kubectl port-forward nginx-pod-exercise01 8080:80

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_1/images/04_PortForward_01.png)

Accediendo desde nuestra máquina a la siguiente ip podemos ver la página de nginx:
http://127.0.0.1:8080/

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_1/images/04_PortForward_02.png)

### 1.5.- Indica la calidad de servicio (QoS) establecida en el pod que acabas de crear. ¿Qué lo has mirado?
Ejecutar:
kubectl get pod nginx-pod-exercise01 --output=yaml

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-02/exercise_1/images/05_Qos.png)

Tambien se puede ver la descripcion del pod y encontrar la Qos con:
kubectl describe pods nginx-pod-exercise01