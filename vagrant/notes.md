# Notes

- regarder une box d'OS simple 
PUIS regarder box k8s

```
Bringing machine 'server' up with 'virtualbox' provider...
Bringing machine 'serverWorker' up with 'virtualbox' provider...
==> server: Box 'debian/bookworm64' could not be found. Attempting to find and install...
    server: Box Provider: virtualbox
    server: Box Version: >= 0
==> server: Loading metadata for box 'debian/bookworm64'
    server: URL: https://vagrantcloud.com/api/v2/vagrant/debian/bookworm64
==> server: Adding box 'debian/bookworm64' (v12.20250126.1) for provider: virtualbox (amd64)
    server: Downloading: https://vagrantcloud.com/debian/boxes/bookworm64/versions/12.20250126.1/providers/virtualbox/amd64/vagrant.box
The box failed to unpackage properly. Please verify that the box
file you're trying to add is not corrupted and that enough disk space
is available and then try again.
The output from attempting to unpackage (if any):

x metadata.json
x Vagrantfile
x box.vmdk: Write failed: No space left on device
x box.ovf: Can't create 'box.ovf': No space left on device
bsdtar: Error exit delayed from previous errors.
```
-> in `.zshrc`, `export VAGRANT_HOME="$HOME/sgoinfre/Vagrant/"`
-> in preferences of VirtualBox, set default machine folder to `$HOME/sgoinfre/VirtualboxVMs/`
