# Vagrantfile

Outil :
- qui permet de **créer et de gérer des machines virtuelles**
- de manière **reproductible et portable** grâce à son fichier de configuration, le `Vagrantfile`

Versioning possible. 

Syntax: Ruby

## Lookup path

Vagrant va chercher dans le répertoire actuel, puis dans les répertoires parents de manière itérative. On peut donc lancer une commande vagrant dans n'importe quel répertoire du projet
```
/home/mitchellh/projects/foo/Vagrantfile
/home/mitchellh/projects/Vagrantfile
/home/mitchellh/Vagrantfile
/home/Vagrantfile
/Vagrantfile
```
On peut préciser le dossier de départ de recherche avec `VAGRANT_CWD`

## Ordre de chargement et merging

Vagrant va charger les `Vagrantfile` dans un certain ordre, en les mergeant au fur et à mesure qu'il les charge
-> permet aux configurations + spécifiques d'overrider les configurations générales

Ordre:
1. `Vagrantfile` de la [box](https://developer.hashicorp.com/vagrant/docs/boxes)
2. `Vagrantfile` du home directory (par défaut `~/.vagrant.d`)
3. `Vagrantfile` du project directory
4. [Multi-machine overrides](https://developer.hashicorp.com/vagrant/docs/multi-machine) if any
5. [Providers specific overrides](https://developer.hashicorp.com/vagrant/docs/providers/configuration) if any

Par défaut, les nouveaux settings sont écrasent les autres.
Si ce n'est pas le cas, comme pour les networks par exemple (qui sont ajoutés les uns aux autres), c'est spécifié dans la documentation.

## Boxes
