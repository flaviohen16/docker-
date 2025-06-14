# Projeto Docker Nginx - Meu Primeiro Contêiner Web

Este projeto é um estudo inicial prático do Docker, focando em como podemos isolar e executar aplicações de forma portátil utilizando contêineres. Como demonstração, implementamos e configuramos um servidor web Nginx.

## Índice

1. [Objetivos do Projeto](#objetivos-do-projeto)
2. [O que é o Nginx?](#o-que-é-o-nginx)
3. [Pré-requisitos](#pré-requisitos)
4. [Como Executar](#Código-de-Exemplo-Funcional)
5. [O que foi Testado](#o-que-foi-testado)
6. [Dificuldades Enfrentadas](#dificuldades-enfrentadas)
7. [Conclusão: Quando Usar Docker](#conclusão-quando-usar-docker)
---
## Objetivos do Projeto
O objetivo deste projeto é demonstrar os conceitos fundamentais de containerização com Docker, configurando um servidor web Nginx simples.

---

## O que é o Nginx?

**Nginx** (pronuncia-se "engine-ex") é um servidor web de alto desempenho, proxy reverso e proxy de e-mail. É amplamente utilizado por sua eficiência, estabilidade e baixo consumo de recursos, sendo ideal para servir conteúdo estático e atuar como balanceador de carga. Sua escolha para este projeto demonstra a facilidade de subir um serviço complexo em um ambiente controlado.

---

## Pré-requisitos

Pré-requisitos para Utilizar o Docker
Para replicar este projeto, você precisará ter o Docker instalado e configurado em sua máquina. Existem duas opções principais de instalação, dependendo do seu sistema operacional:

* **Docker Desktop:** Recomendado para usuários de Windows e macOS. Ele oferece uma experiência completa com uma interface gráfica e ferramentas adicionais.Docker Desktop: Recomendado para usuários de Windows e macOS. Ele oferece uma experiência completa com uma interface gráfica e ferramentas adicionais.

* **Docker Engine:** Ideal para usuários de Linux, sendo a forma mais comum de instalar e usar o Docker nesse ambiente.

* **Como Verificar a Instalação do Docker**
  Após a instalação, abra seu terminal ou prompt de comando e execute o seguinte comando para verificar se o Docker foi instalado corretamente:
    ```bash
    docker --version
    ```
    Se o comando retornar a versão do Docker (ex: Docker version 24.0.5, build 24.0.5-0ubuntu1), você está pronto para prosseguir!
  
    Caso o comando não seja reconhecido ou a instalação não esteja completa, siga as instruções oficiais para o seu sistema operacional:
    * [Instalação do Docker Desktop no Windows](https://docs.docker.com/desktop/install/windows-install/)
    * [Instalação do Docker Desktop no macOS](https://docs.docker.com/desktop/install/mac-install/)
    * [Instalação do Docker Engine no Linux](https://docs.docker.com/engine/install/)
  Certifique-se de seguir os passos de instalação e configuração cuidadosamente para garantir que o Docker esteja funcionando corretamente em sua máquina antes de tentar replicar o projeto.

---

## Código de Exemplo Funcional (Como Executar)

Siga os passos abaixo para iniciar e testar o servidor Nginx em seu contêiner Docker:

1.  **Abra o terminal:**
    * **No Windows:** É **fundamental** executar o Prompt de Comando ou PowerShell **como Administrador**. Isso garante que o cliente Docker possa se comunicar corretamente com o Docker Daemon.
    * **No macOS/Linux:** Geralmente, um terminal comum é suficiente. Em algumas configurações, pode ser necessário usar `sudo` para comandos específicos do Docker.

2. **Contruindo o contêiner:**
   ```bash
   docker build -t meu-site . 
   ```
   * `docker build`: Inicia o processo de construção de uma imagem.
   * `-t`: Indica que estamos nomeando e taggeando a imagem.
   * `meu-site`: É o nome que estamos dando à imagem.
   * ` . `: Indica que o `Dockerfile` (e os arquivos de contexto para a construção) está no diretório atual.
    ![imagem de criação do contêiner](images/imagem_build.jpg "imagem do terminal")

3.  **Execute o contêiner:**

    ```bash
    docker run  -p 80:80 meu-site
    ```
    * `docker run`: executa o contêiner.    
    * `-p 80:80`: Mapeia a porta `80` do seu host (máquina local) para a porta `80` do contêiner.
    * `-d`: executa em segundo plano.
    * `meu-site`: Especifica a imagem a ser utilizada
    ![imagem do comado para rodar o contêiner](images/imagem_run.jpg "imagem do terminal")

    ```bash
    docker run -p 80:80 --name meu-site-container -d meu-site
    ```
    * `--name meu-site-container`: atribui um nome especifico ao contêiner(facilitando o gerenciamento)
    * `-d `:Executa o contêiner em segundo plano. O Docker iniciará o contêiner e imediatamente retornará o controle do terminal para você.

4.  **Verifique o Status do Contêiner:**
    Para confirmar que o contêiner foi iniciado com sucesso e está em execução:

    ```bash
    docker ps
    ```
    Você deverá ver o contêiner listado com status `Up`.
    ![imagem da situação](images/docker-status.jpg "situação do contêiner")


5.  **Acesse o Nginx no Navegador:**
    Abra seu navegador web e digite o seguinte endereço:

    ```bash
    http://localhost:80
    ```
   Você verá a mensagem padrão: "Welcome to nginx!"
    ![imagem da situação](images/imagem-do-localhost.jpg "situação do contêiner")
    

6. **Usando website-templates:**
    depois de acessar o navegador,vai escolher o template desejavel e altera o endereço:

    ```bash
    http://localhost:80/3-col-portfolio/
    ```

     ![imagem do web site ](images/localhost-col-porfolio.jpg "web site col-portfolio")

7. **imagem do docker desktop:**
    mostrando a visão do usuario dentro do docker desktop.
    ![imagem do contêiner rodando no desktop](images/imagem_docker_desktop.jpg "imagem do docker desktop")

---

## O que foi testado

Neste projeto, focamos nos seguintes aspectos práticos do Docker:

* **Instalação e Configuração:** O primeiro passo foi garantir que o Docker Desktop estivesse corretamente instalado e configurado em seu ambiente de desenvolvimento. Uma base sólida é crucial para qualquer projeto Docker.
* **Execução Local de Contêineres:** Testamos a capacidade de levantar um contêiner Docker contendo um servidor Nginx. Este servidor se tornou acessível diretamente da sua máquina local, simulando um ambiente de produção.
* **Integração com outro serviço (implícito):** Embora Nginx seja um único serviço, a execução de um servidor web já demonstra a capacidade do Docker de empacotar e rodar softwares complexos que dependem de um sistema operacional base, bibliotecas, etc. (o Nginx se integra com a rede do host).
* **Logs e outputs:** Verificação dos logs do contêiner para depuração inicial (`docker logs meu-site`).
* **Configuração básica:** Implementamos o mapeamento de portas (-p 80:80), uma configuração básica, mas essencial, para direcionar o tráfego da sua máquina local para o contêiner Docker.

---

## Dificuldades Enfrentadas

Durante a fase inicial de aprendizado e execução deste projeto, as principais dificuldades foram:

1. **Docker Desktop não Iniciado / Docker Daemon Inativo:**

* Problema: Tentar executar comandos `docker` (como `docker run` ou ` docker ps`) e receber uma mensagem de erro como "Cannot connect to the Docker daemon. Is the docker daemon running on this host?" ou similar.
* Causa: Esquecer de iniciar o aplicativo Docker Desktop (no Windows/macOS) ou o serviço Docker (no Linux) antes de tentar usar os comandos. O Docker precisa de um "servidor" (o daemon) para rodar os contêineres.
* Docker Desktop não Iniciado:** A necessidade de garantir que o aplicativo Docker Desktop estivesse completamente inicializado antes de tentar executar qualquer comando Docker, pois ele é o responsável por gerenciar o ambiente de virtualização no Windows e macOS.
* Compreensão Inicial dos Comandos e Conceitos:** Assimilação de termos como "imagem", "contêiner", "mapeamento de portas" (`-p`), e modos de execução (`-d`) que são novos para quem não está familiarizado com a conteinerização.
* Depuração de Erros Genéricos:** Mensagens de erro iniciais do Docker que, para um iniciante, não são imediatamente claras sobre a causa raiz do problema.

2. **Erro de Imagem Não Encontrada (Unable to find image 'minha-imagem:latest' locally)**

* Problema: Ao tentar executar `docker run minha-imagem`, receber um erro dizendo que a imagem não foi encontrada localmente.
* Causa: A imagem não foi construída (docker build) ou o nome/tag especificado no docker run está incorreto ou a imagem não existe no Docker Hub (ou no registry configurado).
* Aprendizado/Solução: Entender que é preciso ter a imagem disponível localmente (seja construindo-a com docker build ou puxando-a com docker pull) antes de tentar executar um contêiner a partir dela. Verificar a lista de imagens locais com docker images.

3. **Confusão entre Imagem e Contêiner:**

* Problema: Dificuldade inicial em diferenciar o que é uma "imagem" (o molde, o pacote executável) e o que é um "contêiner" (a instância em execução de uma imagem).
* Causa: Conceitos novos e abstratos.
* Aprendizado/Solução: A prática com comandos como `docker build`  e  `docker run`  ajuda a solidificar o entendimento. Analogias como "imagem é o bolo, contêiner é a fatia que você come" ou "imagem é a classe, contêiner é o objeto" podem ser úteis

---

## Conclusão: Para que tipo de projeto essa tecnologia é ideal?

Recomendamos o uso do Docker para projetos que precisam de:

* **Consistência de Ambiente:** Garantir que uma aplicação funcione exatamente da mesma forma em diferentes ambientes (desenvolvimento, teste, produção), eliminando o famoso "funciona na minha máquina!".
* **Isolamento de Aplicações:** Executar múltiplos serviços ou versões de software no mesmo servidor sem conflitos de dependências ou portas.
* **Portabilidade:** Facilitar a migração de aplicações entre diferentes infraestruturas (nuvem, servidores on-premise) com mínimo esforço.
* **Escalabilidade e Implantação Rápida:** Agilizar o processo de implantação e escalonamento de aplicações através de contêineres leves e padronizados.
* **Desenvolvimento Ágil:** Proporcionar um ambiente de desenvolvimento rápido, onde novos desenvolvedores podem configurar um projeto rapidamente, sem a necessidade de instalar manualmente todas as dependências.
* **Microserviços:** É a base fundamental para arquiteturas de microserviços, permitindo que cada serviço seja empacotado e gerenciado de forma independente.

---

Este README foi criado pelo grupo,como parte de um estudo prático e documentação do aprendizado inicial em Docker.
