# Projeto Docker Nginx - Meu Primeiro Contêiner Web

Este projeto é um estudo inicial prático do Docker, focando em como podemos isolar e executar aplicações de forma portátil utilizando contêineres. Como demonstração, implementamos e configuramos um servidor web Nginx.

---

## O que é o Nginx?

**Nginx** (pronuncia-se "engine-ex") é um servidor web de alto desempenho, proxy reverso e proxy de e-mail. É amplamente utilizado por sua eficiência, estabilidade e baixo consumo de recursos, sendo ideal para servir conteúdo estático e atuar como balanceador de carga. Sua escolha para este projeto demonstra a facilidade de subir um serviço complexo em um ambiente controlado.

---

## Pré-requisitos

Para replicar este projeto, você precisará ter o **Docker Desktop** (para Windows/macOS) ou **Docker Engine** (para Linux) instalado e configurado na sua máquina.

* **Verifique a instalação do Docker:**
    ```bash
    docker --version
    ```
    Caso o comando não seja reconhecido ou a instalação não esteja completa, siga as instruções oficiais para o seu sistema operacional:
    * [Instalação do Docker Desktop no Windows](https://docs.docker.com/desktop/install/windows-install/)
    * [Instalação do Docker Desktop no macOS](https://docs.docker.com/desktop/install/mac-install/)
    * [Instalação do Docker Engine no Linux](https://docs.docker.com/engine/install/)

---

## Código de Exemplo Funcional (Como Executar)

Siga os passos abaixo para iniciar e testar o servidor Nginx em seu contêiner Docker:

1.  **Abra o Terminal com Privilégios Elevados:**
    * **No Windows:** É **fundamental** executar o Prompt de Comando ou PowerShell **como Administrador**. Isso garante que o cliente Docker possa se comunicar corretamente com o Docker Daemon.
    * **No macOS/Linux:** Geralmente, um terminal comum é suficiente. Em algumas configurações, pode ser necessário usar `sudo` para comandos específicos do Docker.

2.  **Inicie o Contêiner Nginx:**
    Execute o comando abaixo. Ele fará o download da imagem oficial do Nginx (se ainda não estiver em cache), criará um novo contêiner e o iniciará em segundo plano.

    ```bash
    docker run --name meu-primeiro-nginx -p 8080:80 -d nginx
    ```
    * `--name meu-primeiro-nginx`: Atribui um nome descritivo ao contêiner.
    * `-p 8080:80`: Mapeia a porta `8080` do seu host (máquina local) para a porta `80` do contêiner, onde o Nginx está escutando.
    * `-d`: Executa o contêiner em modo "detached" (em segundo plano), liberando seu terminal.
    * `nginx`: Especifica a imagem do Nginx a ser utilizada.

3.  **Verifique o Status do Contêiner:**
    Para confirmar que o contêiner foi iniciado com sucesso e está em execução:

    ```bash
    docker ps
    ```
    Você deverá ver uma entrada para `meu-primeiro-nginx` com o `STATUS` como `Up`.

4.  **Acesse o Nginx no Navegador:**
    Abra seu navegador web e digite o seguinte endereço:

    ```
    http://localhost:8080
    ```
    Uma página de "Welcome to nginx!" será exibida, confirmando que o servidor está online.

---

## O que foi testado

Neste projeto, focamos nos seguintes aspectos práticos do Docker:

* **Instalação:** Confirmação da correta instalação e configuração do Docker Desktop no ambiente de desenvolvimento.
* **Execução local:** Levantamento de um contêiner Docker contendo um servidor Nginx, acessível a partir da máquina local.
* **Integração com outro serviço (implícito):** Embora Nginx seja um único serviço, a execução de um servidor web já demonstra a capacidade do Docker de empacotar e rodar softwares complexos que dependem de um sistema operacional base, bibliotecas, etc. (o Nginx se integra com a rede do host).
* **Logs e outputs:** Verificação dos logs do contêiner para depuração inicial (`docker logs meu-primeiro-nginx`).
* **Configuração básica:** Mapeamento de portas (`-p 8080:80`) e nomeação do contêiner (`--name`) como configurações essenciais para o uso do serviço.

---

## Dificuldades Enfrentadas

Durante a fase inicial de aprendizado e execução deste projeto, as principais dificuldades foram:

* **Problemas de Permissão no Windows:** O erro mais comum foi `docker: error during connect: in the default daemon configuration on Windows, the docker client must be run with elevated privileges to connect...`. Isso ocorreu por não executar o Prompt de Comando/PowerShell como **Administrador**, impedindo a comunicação com o Docker Daemon.
* **Docker Desktop não Iniciado:** A necessidade de garantir que o aplicativo Docker Desktop estivesse completamente inicializado antes de tentar executar qualquer comando Docker, pois ele é o responsável por gerenciar o ambiente de virtualização no Windows e macOS.
* **Compreensão Inicial dos Comandos e Conceitos:** Assimilação de termos como "imagem", "contêiner", "mapeamento de portas" (`-p`), e modos de execução (`-d`) que são novos para quem não está familiarizado com a conteinerização.
* **Depuração de Erros Genéricos:** Mensagens de erro iniciais do Docker que, para um iniciante, não são imediatamente claras sobre a causa raiz do problema.

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

Este README foi criado por [Seu Nome/Usuário] como parte de um estudo prático e documentação do aprendizado inicial em Docker.
