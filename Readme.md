# Ejemplo de aprovisionamiento de dos máquinas (Dev) y (Test)

#### Descripción:

Desplegamos el aprovisionamiento de dos máquinas que se llaman igual que las branch del proyecto:

[https://github.com/xavimf87/covid-stats](https://github.com/xavimf87/covid-stats)

Se usa Vagrant, Ansible, Git y docker para aprovisionar las máquinas.


#### Requisitos:

  
- [x] Vagrant
- [x] Ansible
- [x] VirtualBox



#### Puesta a punto:

1. `git clone https://github.com/xavimf87/ejemplo-entornos-test-dev.git && cd ejemplo-entornos-test-dev`

2. `vagrant plugin install vagrant-docker-compose`

3. `vagrant up`

4. Acceder al proyecto web:

   `Dev` = `http://192.168.33.139:5000`

   `Test` = `http://192.168.33.140:5000`
5. Acceder por ssh:

   `Dev` = `vagrant ssh dev`

   `Test` = `vagrant ssh test`

#### Ejemplo de rebuild de una de las máquinas

`vagrant destroy test -f && vagrant up test`

`vagrant destroy dev -f && vagrant up dev`
