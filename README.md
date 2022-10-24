<h1 align="center">Desafio Tech (DevOps)</h1>
<h2 align="center">Processo Seletivo Estágio Frexco</h2>
<br><br>
<div align="center">
<img src = "https://github.com/edsondearaujo/deployReact_EdsonSoares/blob/master/assets/gifs/devOps.gif" width="680" height="180px"/></div><br><br>


<h2 align="center"><b>Introdução</b></h2>
 
<p>Essa aplicação é destinada ao desafio Tech (DevOps) do processo seletivo para estágio da <a href="https://frexco.com.br" target="_blank">Frexco</a>. 
O desafio consiste em realizar a preparação do ambiente de deploy para uma aplicação em React. Além de observar e entender o básico da infraestrutura de um processo de deploy. Levando esses pontos em consideração, o desafio foi desenvolvido sobre a aplicação básica do <a href="https://create-react-app.dev/docs/getting-started/" target="_blank">ReactJS</a>, seguindo sua documentação para a criação do projeto com create-react-app.</p>
<br><br>
 
<h2 align="center" ><b>Rodar na sua máquina</b></h2>
 <p>Para rodar o projeto no seu computador, basta seguir os passos seguintes.</p>

<h3 align="center" ><b>Pré-requisitos</b></h3>


<div >
<img src = "https://github.com/edsondearaujo/deployReact_EdsonSoares/blob/master/assets/gifs/compose.gif" width="220" height="250px" align="right"/>
<p>As versões do Docker e Docker-compose utilizadas no projeto foram: <i>(Sugiro utilizar as mesmas versões ou mais atuais)</i> 

- <a href="https://www.docker.com" target="_blank">docker</a> >= 20.10.12;
- <a href="https://docs.docker.com/compose/install/" target="_blank">docker-compose</a> >= 1.29.2;</p>

</div>
<br>

<h3 align="center"><b>Construir e subir o container</b></h3>
 
<p align="left">Para construir e subir os containers</p>
 
    docker-compose up --build
 
<p align="left">Parar todos os serviços em execução</p>

    docker-compose down
 
<p align="right">Você pode ver a aplicação rodando no endereço '<a href="http://localhost:8008/" target="_blank">http://localhost:8008/</a>'</p>
<br><br>
 
<h2 align="center" ><b>Infra-estrutura</b></h2>
<div >
<img src = "https://github.com/edsondearaujo/deployReact_EdsonSoares/blob/master/assets/gifs/process.gif" width="220px" height="250px" align="left"> 

<p align="right">O docker é responsável por dar o start na aplicação, baixando a imagem oficial do <a href="https://hub.docker.com/_/node" target="_blank">NodeJS</a> disponível no <a href="https://hub.docker.com" target="_blank">DockerHub</a> e ao executar o comando "<i>npm install</i>" e "<i>npm start</i>" dentro do dockerfile, a aplicação é iniciada. E pelo fato do comando "<i>npm install</i>" ser executado dentro do dockerfile, podemos deixar a pasta "<i>node_modules</i>" sendo criada dentro do container, deixando a estrutura do projeto mais limpa.</p></a>
</div>

<p align="right">O docker-compose está fazendo o papel de orquestrar os containers do <a href="https://www.nginx.com" target="_blank">Nginx</a> e da aplicação React. Dentro do docker-compose é possível fazer esses dois containeres se comunicarem usando o conceito de "<i>bridge</i>", fazendo a ponte de comunicaçãoe entre os "<i>services</i>" definidos no arquivo "<i>.yml</i>" sendo definidos dentro da mesma rede, "<i>networks</i>". Nesse projeto a rede criada no "<i>docker-compose</i>" está nomeada como "<i>production-network</i>". </p>
</div>

<p align="left">O <a href="https://www.nginx.com" target="_blank">Nginx</a> tem papel fundamental para direcionar um serviço para um ou mais servidores, com a técnica de load balance, por exemplo. Nesse projeto o Nginx está ouvido a porta 80, que é sua porta padrão, assim como a 443, geralmente usada em protocolos HTTPS, no caso desse desafio, o arquivo de configuração do Nginx, "<a href="https://github.com/edsondearaujo/deployReact_EdsonSoares/blob/master/docker/config/nginx.conf" target="_blank"><i>nginx.conf</i></a>", foi configurado para o HTTP. Dessa forma o Nginx recebe a aplicação que chega na porta 3000 e direciona a aplicação para a porta <a href="http://localhost:8008/" target="_blank">8008</a>. Assim a aplicação abre em um caminho diferente da porta padrão do React, que é a porta 3000.</p>
</div>

<br><br>

<h2 align="center" ><b>Tecnologias</b></h2>

<div align="center">

<img src="https://github.com/edsondearaujo/deployReact_EdsonSoares/blob/master/assets/images/dockerlogo.jpeg" width="80px" height="70px" alt="Docker"/>

<img src="https://github.com/edsondearaujo/deployReact_EdsonSoares/blob/master/assets/images/docker-compose.png" width="80px" height="70px" alt="Docker-compose"/>

<img src="https://github.com/edsondearaujo/deployReact_EdsonSoares/blob/master/assets/images/nginx.png" width="80px" height="70px" alt="Nginx">

</div>

<div align="center">
<img src="https://github.com/edsondearaujo/deployReact_EdsonSoares/blob/master/assets/images/ubuntu.png" width="80px" height="70px" alt="Linux (Ubuntu 20.04.3 LTS)">

<img src="https://github.com/edsondearaujo/deployReact_EdsonSoares/blob/master/assets/images/git.jpg" width="80px" height="70px" alt="Git">

<img src="https://github.com/edsondearaujo/deployReact_EdsonSoares/blob/master/assets/images/reactImg.png" width="80px" height="70px" alt="React">

</div>