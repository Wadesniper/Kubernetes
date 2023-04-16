# Kubernetes

# EN - Deploying a WordPress Blog on Kubernetes
This project aims to demonstrate the deployment of a WordPress blog on Kubernetes, including exposing the application externally, managing sensitive information using secrets, and persisting data.

## Prerequisites
A Kubernetes cluster

kubectl CLI tool

kustomize CLI tool

## Usage
1- Clone this repository to your local machine.

2- Navigate to the project directory.

3- Apply the Kubernetes resources using kustomize:

`kustomize build . | kubectl apply -f -`

4- Verify that the resources are created and running:

`kubectl get pods,services -n wordpress`

5- Access the WordPress blog at `http://<node-ip>:<node-port>`, where <node-ip> is the external IP address of a node in the cluster, and <node-port> is the node port assigned to the WordPress service (default is 30008).

6- To delete the resources created by this project, run:

`kustomize build . | kubectl delete -f -`

## Resources
`app-wordpress-namespace.yml`: Namespace for the WordPress application.

`mysql-deployment.yml`: Deployment for the MySQL database used by WordPress.

`wordpress-deployment.yml`: Deployment for the WordPress application.

`app-wordpress-secret.yml`: Secret for storing sensitive information (database password).

`service-nodeport-wordpress.yml`: Service of type NodePort for exposing the WordPress application externally.

`service-clusterip-mysql.yml`: Service of type ClusterIP for internal communication between the WordPress application and the MySQL database.


# FR - Déploiement d'un blog WordPress avec Kubernetes
Ce projet a pour but de vous montrer comment déployer un blog WordPress sur un cluster Kubernetes en utilisant les fonctionnalités de gestion des secrets et de persistance des données.

## Prérequis
Un cluster Kubernetes en fonctionnement

L'outil kubectl installé sur votre machine

## Étapes

1- Clonez ce dépôt Git sur votre machine locale.

2- Assurez-vous que votre contexte kubectl est bien configuré pour votre cluster Kubernetes.

3- Ouvrez un terminal et placez-vous dans le répertoire du projet.

4- Créez un namespace pour notre application WordPress :

kubectl apply -f app-wordpress-namespace.yml

5- Créez un secret Kubernetes pour stocker le mot de passe de la base de données MySQL :

``kubectl apply -f app-wordpress-secret.yml``

6- Créez un déploiement Kubernetes pour la base de données MySQL :

`kubectl apply -f mysql-deployment.yml`

7- Créez un déploiement Kubernetes pour l'application WordPress :

`kubectl apply -f wordpress-deployment.yml`

8- Créez un service de type ClusterIP pour exposer le service MySQL à l'intérieur du cluster :

`kubectl apply -f service-clusterip-mysql.yml`

9- Créez un service de type NodePort pour exposer l'application WordPress à l'extérieur du cluster :

`kubectl apply -f service-nodeport-wordpress.yml`

### Vérifiez que tout fonctionne correctement en récupérant l'adresse IP de votre machine et le numéro de port associé au service NodePort WordPress, puis ouvrez un navigateur Web et allez sur cette adresse :

`http://<IP de votre machine>:<numéro de port>/`

## Conclusion
Vous avez maintenant déployé un blog WordPress sur un cluster Kubernetes en utilisant les fonctionnalités de gestion des secrets et de persistance des données. Vous pouvez maintenant personnaliser votre blog et commencer à publier des articles !


