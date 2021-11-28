## 1.- [Ingress Controller / Secrets] Crea los siguientes objetos de forma declarativa con las siguientes especificaciones:          
• Imagen: nginx    
• Version: 1.19.4        
• 3 replicas       
• Label: app: nginx-server          
• Exponer el puerto 80 de los pods          
• Limits:        
	CPU: 20 milicores      
	Memoria: 128Mi      
• Requests:      
	CPU: 20 milicores     
Memoria: 128Mi        
a. A continuación, tras haber expuesto el servicio en el puerto 80, se deberá acceder a la página principal de Nginx a través de la siguiente URL:      
	http://<student_name>.student.lasalle.com


# SOLUCION:    
- Crear un deployment (ver archivo Deployment.yaml)  
kubectl apply -f Deployment.yaml    
    
- Crear un service (ver archivo Service.yaml)   
kubectl apply -f Service.yaml    
    
- Crear un ingress (ver archivo Ingress.yaml)    
kubectl apply -f Ingress.yaml
      

- Iniciar minikube  
minikube start --vm-driver=hyperv    
    
- Habilitar el addons de ingress en minikube   
minikube addons enable ingress     
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_1/images/enableingress.png)

     
- Obtener la ip de minikube para poder añadirla al fichero hosts y enlazarla con el host raul.student.lasalle.com   
minikube ip   
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_1/images/hosts.png)
    
- Comprobar que se puede entrar con el navegador    
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_1/images/web01.png)
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_1/images/curl01.png)
      
      
## b. Una vez realizadas las pruebas con el protocolo HTTP, se pide acceder al servicio mediante la utilización del protocolo HTTPS, para ello:    
• Crear un certificado mediante la herramienta OpenSSL u otra similar   
• Crear un secret que contenga el certificado    

# SOLUCION:      
- Crear un certificado con OpenSSL    
openssl req -x509 -newkey rsa:4096 -keyout ingresskey.pem -out ingresscert.pem -nodes -sha256 -days 365 -subj "/C=ES/ST=Barcelona/L=Barcelona/O=raul.student.lasalle.com/CN=La Salle"     
    
- Crear un Secret con los datos del certificado creado (ver archivo Secret.yaml)     
kubectl apply -f Secret.yaml    
     
- Modificar el Ingress creado anteriormente para que use el secret (ver archivo Ingress-ssl.yaml)   
kubectl apply -f Ingress-ssl.yaml     
    
- Comprobar que se puede entrar con el navegador y detalles del certificado
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_1/images/web02.png)
![alt text](https://github.com/rcamison/kube-exercises/blob/main/hw-03/exercise_1/images/web03.png)
