# vagrant-symfony

1. Open Vagrantfile in you text editor and chenge ip address

```
config.vm.network :private_network, ip: "33.33.33.14"
```

2. Open provision/inventory/vagrant in your text editor and chage ip address. Use the same address as in Vagrantfile

```
33.33.33.14 ansible_become=True
```

3. In root of this reposiotry create link `project` to your source coude on the host machine and that folder will be exposed to virtual machine /vagrat folder.

```
ln -s /home/repo/someproject project
```
