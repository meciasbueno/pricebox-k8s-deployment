# pricebox-k8s-deployment
Arquivos de deploy da aplicação Pricebox (apenas landingpage) no Kubernetes com o objetivo de estudos

### Instalações
 - Instalação do wsl2 e minikube: https://github.com/codeedu/wsl2-kubernetes
 - Instalação do kubectl: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

### Passos iniciais para deploy

 - Criar a namespace, caso não existir:
	> kubectl create namespace pricebox

 - Criar a secret para o K8S ter acesso ao registry e baixar a imagem docker:
	> kubectl create secret --namespace=pricebox docker-registry docker-gitlab --docker-server=you-registry.com --docker-username=*you-user-name* --docker-password=*you-password*


### Deploy via templates do K8S (yamls)
   ~/k8s/pricebox-landpage:
   > kubectl --namespace=pricebox apply -f .

### Deploy via helm-chart
   ~/k8s-helm-charts/pricebox-landpage:
   > helm upgrade --install --namespace=pricebox pricebox-landpage .

### Acessar serviço localmente (gera url para acesso local)
   Para gerar uma url local para acessar o serviço, é necessário acessar o ip do minukube (https://minikube.sigs.k8s.io/docs/commands/ip/)
   > minikube service --url pricebox --namespace pricebox

### Dns local no minikube (ingress)
  - https://minikube.sigs.k8s.io/docs/handbook/addons/ingress-dns/