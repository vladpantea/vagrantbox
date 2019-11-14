1. vagrant up
2. vagrant ssh
3. sudo minikube start vm-driver "none"
4. helm list
5. kubectl get po
6. kubectl get svc
7. cd /vagrant_data
8. cd local_mimecast
9. e.g. helm install --name mssql-linux charts/stable/mssql-linux --set acceptEula.value=Y --set edition.value=Developer --set service.type=NodePort --set service.port=31234