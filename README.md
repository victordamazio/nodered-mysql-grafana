Como fazer um sistema Node-Red + MySQL + Grafana

Nesse relatório, é descrito como instalar o Node-RED, o MySQL e o Grafana, e fazer os 3 funcionarem em conjunto.
O Node-RED é uma plataforma de programação visual para conectar hardwares, útil para internet das coisas, com foco em flows, o MySQL é um sistema de banco de dados baseado em SQL, e o Grafana é uma aplicação para gráficos e dashboards.
A ideia é fazer um flow para coletar dados dos nossos dispositivos, passar os dados para um banco de dados MySQL, e depois visualizar os dados num dashboard Grafana, este é apenas um tutorial básico de como fazer os 3 funcionarem em conjunto, não entra em detalhes sobre funções mais complexas das 3 ferramentas.

Passos:

1 - Ter Linux/Ubuntu instalado, se estiver usando Windows, instalar uma máquina virtual usando o VirtualBox.

Guia para instalar Ubuntu: https://www.vmia.com.br/blog/index.php/2020/05/29/como-instalar-ubuntu-server-20-04-no-virtualbox/

2 - Instalar o Node-RED

Guia para instalar o Node-Red: https://nodered.org/docs/getting-started/local

3 – Instalar o MySQL

Guia para instalar o MySQL: https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04-pt

4 - Como recomendação, instale o MySQL Workbench, para facilitar o trabalho com uma interface gráfica do MySQL:

Guia para instalar o MySQL Workbench: https://dev.mysql.com/doc/workbench/en/wb-installing-linux.html

5 - Instalar o Grafana

Guia para instalar o Grafana: https://grafana.com/docs/grafana/latest/installation/debian/

6 - Abra o Node-RED no navegador, colocando http://localhost:1880 na barra de endereço, e também o Grafana, colocando http://localhost:3000, recomendo também abrir o MySQL Workbench.

7 - Crie uma tabela SQL, com Primary Key e uma Timestamp automática, como essa aqui:

![image](https://user-images.githubusercontent.com/25162231/101772504-32803580-3aca-11eb-8bde-7c60f89f270f.png)
