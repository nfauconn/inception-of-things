# Vagrant boxes

Image de machine virtuelle préconfigurée :
- OS
- base logicielle
que Vagrant utilise comme point de départ pour créer un environnement.

Vagrant va :
- cloner la box pour créer une nouvelle VM
- appliquer la configuration définie par le `Vagrantfile` (réseau, dossiers partagés, environnement...)
- démarrer l'environnement prêt à l'emploi

[Catalogue de boxes](https://vagrantcloud.com/boxes/search)

## Boxes officielles

Ubuntu 18.04 64-bit box publiée par HashiCorp, disponible pour les use cases minimaux.
- optimisée ++
- légère
- supportée par VirtualBox, Hyper-V et VMware

```
vagrant init hashicorp/bionic64
```

Si on a un Vagrantfile, y ajouter `hashicorp/bionic64` :
```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"
end
```

Pour d'autres OS comme base, les [bento boxes](https://vagrantcloud.com/bento) sont recommandées

## Create our own box

For advanced Vagrant users.
See [box creation documentation](https://developer.hashicorp.com/vagrant/docs/boxes/base) and [box format documentation](https://developer.hashicorp.com/vagrant/docs/boxes/format)

