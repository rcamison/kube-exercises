## 3. [Horizontal Pod Autoscaler] Crea un objeto de kubernetes HPA, que escale a partir de las métricas CPU o memoria (a vuestra elección). Establece el umbral al 50% de CPU/memoria utilizada, cuando pase el umbral, automáticamente se deberá escalar al doble de replicas.

#SOLUCION:    
- Crear un deployment y un service de nginx (ver archivo Deployment.yaml)  
kubectl apply -f Deployment.yaml    
       
- Crear un HorizontalPodAutoscaler (ver archivo HorizontalPodAutoscaler.yaml)    
kubectl apply -f HorizontalPodAutoscaler.yaml

![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_3/images/Createobjects.png)      
    
- Habilitar el addons de metrics en minikube   
minikube addons enable metrics-server     
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_3/images/metrics.png)

     
- Ejecutar el comando (**nota: he tenido que modificar lo que ponia en el enunciado y añadir un . antes de /bin/sh para que no me diera error (no encontraba sh)    
kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- ./bin/sh -c "while sleep 0.01; do wget -q -O- http://nginx; done"  

   
- Estado antes de comenzar 
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_3/images/inicio.png)

   
- Estado en el escalado 
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_3/images/escalado.png)

   
- Estado al para el busybox. El pod load-generator se borra     
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_3/images/final.png)
