Il y a plusieurs raisons techniques et pédagogiques pour lesquelles il est **fortement recommandé** de n’allouer que le strict minimum en termes de ressources (ici, 1 CPU et 512 Mo/1 Go de RAM) dans ce type d’exercice, et chacune a son intérêt :

---

### 1. **Optimisation et portabilité des environnements de dev**

* **Vagrant est conçu pour automatiser et faciliter la création de machines reproductibles.**

  * Un Vagrantfile qui démarre une VM “légère” (peu de CPU/RAM) pourra tourner sur **presque n’importe quel PC**, y compris des machines modestes, ou en parallèle de plusieurs VMs (important pour les cas de cluster ou de CI/CD).
  * Si tu mets des valeurs élevées (genre 4 CPU/8Go), tu risques de rendre l’environnement inutilisable pour toi ou tes coéquipiers ayant moins de ressources sur leur poste.

---

### 2. **Bonnes pratiques : tester la résilience et le minimalisme**

* **K3s est justement une version “light” de Kubernetes, pensée pour tourner sur du matos contraint.**

  * Si ton cluster K3s tourne bien avec 512 Mo, il sera d’autant plus robuste et portable pour du dev, du test, de l’embarqué ou même du cloud à petit budget.
  * Ça t’oblige à configurer “propre”, sans installer de paquets inutiles, et à garder un OS et des process minimalistes, ce qui est *toujours* une bonne pratique (sécurité, maintenance, attaque de surface réduite…).

---

### 3. **Éviter les effets de bord des sur-provisionnements**

* **Allouer beaucoup de ressources masque souvent des bugs ou des problèmes de configuration** (fuites de mémoire, process zombies, services qui ne redémarrent pas bien, etc).

  * Si ton cluster survit avec peu de ressources, il sera en général bien plus stable et prévisible.
  * Cela force à monitorer, à optimiser, et à comprendre l’utilisation réelle des ressources.

---

### 4. **Rapidité et efficience**

* **Les VMs plus “légères” démarrent et s’arrêtent beaucoup plus vite.**

  * Idéal pour itérer rapidement, automatiser les tests, ou recréer/résilier des environnements à la volée.
  * Moins de charge sur ton hyperviseur (VirtualBox, libvirt…), donc moins de risques de freeze, de swap, etc.

---

### 5. **Esprit DevOps / Cloud / Conteneurisation**

* Dans le monde réel, on travaille de plus en plus avec des containers/VMs **éphémères et sous-dimensionnées par défaut** (le fameux “cloud cost cutting”).

  * Savoir déployer et faire tourner des services “petits” (footprint minimal) est très recherché.

---

### Tangente fun :

Historiquement, de nombreux bugs et failles n’ont été découverts que parce que les devs/testeurs ont imposé des environnements “pourris” (très peu de RAM, CPU, disque lent, etc). Par exemple, beaucoup de distros Linux “live” (Slax, TinyCore) ou des appliances réseaux sont des mines d’astuces pour faire tourner un OS moderne avec moins de 128 Mo de RAM… C’est souvent là qu’on apprend les vraies limites d’un stack logiciel.

---

**En résumé :**

> *Allouer le strict minimum oblige à produire des environnements reproductibles, robustes, efficaces et vraiment portables, tout en t’apprenant à diagnostiquer et optimiser le moindre octet consommé. C’est à la fois une exigence technique, pédagogique, et une bonne habitude à garder dans la durée.*


