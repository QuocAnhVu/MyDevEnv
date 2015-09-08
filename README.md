# MyDevEnv
This is my setup for development.

## Host Machine Prereqisites
* Git with keys set up
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [Vagrant](https://www.vagrantup.com/downloads.html)
* [Vagrant plugin - Librarian-Chef](https://github.com/jimmycuadra/vagrant-librarian-chef)

## Instructions
1. git -T git@github.com
2. mkdir \<dev directory\> && cd \<dev directory\>
3. git clone git@github.com:QuocAnhVu/MyDevEnv.git 
4. vagrant plugin install vagrant-librarian-chef
5. cd MyDevEnv && vagrant up