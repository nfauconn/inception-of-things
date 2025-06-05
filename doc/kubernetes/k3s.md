# K3S

Great for:
- Edge : réseau local / de proximité
- Homelab
- Internet of Things (IoT)
- Continuous Integration (CI) : ensemble de pratiques visant à éviter toute régression grâce à des tests d'intégration
- ...

> *What's with the name ?*
> We wanted an installation of Kubernetes that was half the size in terms of memory footprint. Kubernetes is a 10-letter word stylized as K8s. So something half as big as Kubernetes would be a 5-letter word stylized as K3s. There is no long form of K3s and no official pronunciation.

## Controller mode

Controller mode (= "server mode") :

- Le nœud K3s server joue le rôle de control plane.
- Il gère l’API Kubernetes, l’orchestrateur, l’état du cluster, les déploiements, etc.
- Il peut aussi exécuter des pods/applications (par défaut, il joue à la fois control-plane + worker, sauf si on le met en mode “ha” ou “dedicated controller”).

## Agent mode

Agent mode (= "worker mode") :

- Le nœud K3s agent ne fait que tourner des workloads/pods.
- Il s’enregistre auprès du K3s server, reçoit les instructions de scheduling, exécute les conteneurs.
- Pas de composants de gestion du cluster (API server, etcd, scheduler…) sur ce nœud.
