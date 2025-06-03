# Basics

Plateforme open-source qui orchestre les conteneurs:
- déploie
- met à l'échelle
- administre automatiquement
les applications conteneurisées sur un cluster

Configuration déclarative.

## Cluster

Un cluster Kubernetes est un ensemble de machines (physiques ou virtuelles) appelées *noeuds* qui fonctionnent ensemble pour exécuter des applications conteneurisées.

Un cluster Kubernetes est constitué de 2 types de ressources:
- le **Control Plane** qui coordine le cluster
- les **Nodes** qui sont les workers qui font tourner les applications

![Cluster diagram](https://kubernetes.io/docs/tutorials/kubernetes-basics/public/images/module_01_cluster.svg)

## Control Plane

Le Control Plane est responsable de la gestion du cluster et des noeuds.

Il coordonne les activités du cluster telles que:
- la planification des applications
- le maintien de leur état souhaité
- leur mise à l'échelle
- le déploiement des mises à jour

## Noeuds

Un noeud est une VM ou un ordinateur physique qui sert de machine de travail dans un cluster.

Chaque noeud a un **Kubelet**, qui est un agent qui permet de gérer le noeud et de communiquer avec le Control Plane

Chaque noeud a des outils pour gérer les opérations de container, comme [containerd](https://containerd.io/docs/) ou [CRI-O](https://cri-o.io/#what-is-cri-o)

Un cluster Kubernetes qui gère le traffic en prod devrait avoir un minimum de 3 nœuds:
- control plane
- etcd (sauvegarde)
- autre control plane
Comme ça si les 2 premiers sont down, c'est bon grâce au 3e
