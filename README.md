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

8 - No Node-RED, vá na barra de configurações, e clique em “Manage palette”

![image](https://user-images.githubusercontent.com/25162231/101772516-3613bc80-3aca-11eb-8c63-e9d15800d424.png)

E depois instale o MySQL Node, na figura, ele já está instalado

![image](https://user-images.githubusercontent.com/25162231/101772543-3f048e00-3aca-11eb-8fee-b4b7657b0fee.png)

9 - Crie um flow, mais ou menos assim:

![image](https://user-images.githubusercontent.com/25162231/101772559-42981500-3aca-11eb-9685-18ef5d19d2c6.png)

O node function precisa ter uma Query SQL, um exemplo da qual está sendo usada

'''

msg.topic="INSERT INTO ‘schema_test_nodered’.’thermometer’ (`temperature1`, `temperature2`) VALUES (‘25’, ‘26’)"
return msg;

'''

![image](https://user-images.githubusercontent.com/25162231/101772574-4a57b980-3aca-11eb-9e5f-2be8952fdd32.png)

Preencha o node MySQL mais ou menos assim de acordo com o seu banco, colocando o usuário, senha, e nome do banco:

![image](https://user-images.githubusercontent.com/25162231/101772585-4d52aa00-3aca-11eb-874e-9d84079ffd3e.png)

10 - Clique no node Inject para inserir os dados na sua tabela SQL, e verifique se a sua tabela está com os dados corretos.

11 - No Grafana, vá em Configuration → Data Sources → Add Data Source → MySQL

E depois, preencha mais ou menos assim

![image](https://user-images.githubusercontent.com/25162231/101772598-504d9a80-3aca-11eb-8cb0-4da4fb73ea36.png)

12 - Depois, crie um Dashboard e um Panel

13 - No panel que você vai usar, crie um gráfico com o Data Source que você criou, configure os dados que serão lidos, e deixe eles ordenados pelo timestamp

![image](https://user-images.githubusercontent.com/25162231/101772604-53e12180-3aca-11eb-9442-7c448b3e7910.png)

14 - Terminado, você pode mexer em mais algumas configurações para definir como visualizar os dados, e também marcar o tempo, para o intervalo de datas que definirá quais dados serão exibidos no panel.
