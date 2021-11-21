## 5.- Diseña una estrategia de despliegue que se base en ”Blue Green”.

Generar los dos deployments blue y green:            
kubectl apply -f deployment_blue_exercise_5.yaml              
kubectl apply -f deployment_green_exercise_5.yaml             

Crear un servicio que apunte al deployment blue y otro al green para poder hacer las pruebas         
kubectl apply -f service_blue-exercise_5.yaml        
kubectl apply -f service_green-exercise_5.yaml             

Cambiar el trafico del blue deployment al green             
kubectl patch service nginx-serviceblue-exercise5 -p '{"spec":{"selector":{"version":"v2.0"}}}'         


Una vez se ha cambiado el trafico al deployment green se puede borrar el deployment blue            
kubectl delete deployment nginx-deployment-blue