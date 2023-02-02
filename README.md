# Kali linux vagrant

## Prerequisite

Tools: **Virtualbox** and **Vagrant**

Vagrant Plugin: disksize (via ```vagrant plugin install vagrant-disksize```)

## How to launch

Has this vagrant file need a password, as it creates a basic user, you will need to launch it like so:

```
PASSWORD=<your_password> vagrant up
```

## Warning

This is a 'template', please pay attention to what is inside the Vagrantfile as you may not have the necessary configuration to do the same as me, for instance I change the default layout to an azerty.

You should also change the hostname var, the tools that I install in the provisioner shell, as well as the username I added in the shell.

## For future
I will add more configuration in the future, as well as other tools in the provisioner shell so be cautious about that