# kubernet-declarativo

## Comandos de Kubertnetes usando kubectl:

### Nodes:

Listar todos os nodes:

    kubectl get nodes -o wide --watch 

---

### Pods:

Listar todos os pods:
    
    kubectl get pods -o wide

Criar um pod:

    kubectl run nginx-pod --image=nginx:latest

Detalhar um pod:
    
    kubectl describe pods nginx-pod

Editar um pod:  

    kubectl edit pod nginx-pod

Excluir um pod:

    kubectl delete pod nginx-pod

Criar um pod de maneira declarativa:

    kubectl apply -f ./alura-noticias/portal-noticias.yaml

Acessar remotamente o pod:

    kubectl exec -it portal-noticias -- bash

Excluir um pod pelo nome do arquivo:
    
    kubectl delete -f ./alura-noticias/portal-noticias.yaml

Excluir todos os pods ativos:

    kubectl delete pods --all


---

### Services

Listar todos os services (2 modos):

    kubectl get service -o wide
    kubectl get svc -o wide

Criar um service de maneira declarativa:

    kubectl apply -f ./exemplos/svc-pod-2.yaml

Excluir um service (3 modos):

    kubectl delete service svc-pod-2
    kubectl delete svc svc-pod-2
    kubectl delete -f ./exemplos/svc-pod-2.yaml

Excluir todos os services ativos (2 modos):

    kubectl delete service --all
    kubectl delete svc --all

---

### Load Balancer

Listar todos os load balancers (2 modos):
    
    kubectl get loadbalancer -o wide
    kubectl get lb -o wide

Criar um load balancer de maneira declarativa:
    
    kubectl apply -f ./exemplos/svc-pod-1-loadbalancer.yaml

Excluir um load balancer (3 modos):
    
    kubectl delete loadbalancer svc-pod-1-loadbalancer
    kubectl delete lb svc-pod-1-loadbalancer
    kubectl delete -f ./exemplos/svc-pod-1-loadbalancer.yaml

Excluir todos os load balancers (2 modos):
    
    kubectl delete loadbalancer --all
    kubectl delete lb --all
    
---

### ConfigMap

Listar todos os configmaps (2 modos):

    kubectl get configmap -o wide 
    kubectl get cm -o wide

Criar um configmap de maneira declarativa:
    
    kubectl apply -f ./alura-noticias/db-configmap.yaml

Excluir um configmap (3 modos):

    kubectl delete configmap db-configmap
    kubectl delete cm db-configmap
    kubectl delete -f ./alura-noticias/db-configmap.yaml

Excluir todos os configmaps ativos (2 modos):

    kubectl delete configmap --all
    kubectl delete cm --all

---

### ReplicaSet

Listar todos os replicasets (2 modos):

    kubectl get replicasets -o wide 
    kubectl get rs -o wide 

Criar um replicaset de maneira declarativa:

    kubectl apply -f ./alura-noticias/portal-noticias-replicaset.yaml

Excluir um replicaset (3 modos):

    kubectl delete replicaset portal-noticias-replicaset
    kubectl delete rs portal-noticias-replicaset
    kubectl delete -f ./alura-noticias/portal-noticias-replicaset.yaml

Excluir todos os replicasets (2 modos):

    kubectl delete replicasets --all
    kubectl delete rs --all
 
---

### Deployments

Listar todos os deployments (2 modos):

    kubectl get deployments -o wide 
    kubectl get deploy -o wide 

Criar/Alterar um deployment de maneira declarativa (--record gravará uma anotação no histórico):

    kubectl apply -f ./alura-noticias/portal-noticias-deployment.yaml --record

Verificar todo o histórico de mudanças de um deployment:

    kubectl rollout history deployment portal-noticias-deployment
 
Criar uma anotação na última linha do histórico:

    kubectl annotate deploy portal-noticias-deployment kubernetes.io/change-cause="Criando portal de noticias na versao 1"

Voltar o deploy para uma versão específica:

    kubectl rollout undo deployment portal-noticias-deployment  --to-revision=3
 
Excluir um deployment (3 modos):

    kubectl delete deployment portal-noticias-deployment
    kubectl delete deploy portal-noticias-deployment
    kubectl delete -f ./alura-noticias/portal-noticias-deployment.yaml

Excluir todos os replicasets (2 modos):

    kubectl delete deployment --all
    kubectl delete deploy --all

---

### IMPORTANTE

Executar a criação de todos os recursos do Kubernets de uma vez só: 
 
    kubectl apply -f './alura-noticias/*.yaml'

 

