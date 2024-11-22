# docker-estudos
O **Docker** é uma plataforma de software que permite criar, testar e implantar aplicações em containers. Ele facilita o desenvolvimento de aplicações ao permitir que o software, suas dependências e bibliotecas sejam empacotados de forma padronizada, garantindo que o ambiente de desenvolvimento seja o mesmo em todas as etapas do ciclo de vida da aplicação, desde a criação até a produção.

### Principais características do Docker:
1. **Containers**: O Docker utiliza containers, que são ambientes isolados para rodar aplicações. Cada container inclui a aplicação, suas dependências, bibliotecas e configurações, permitindo que ela seja executada de maneira consistente em qualquer sistema que tenha o Docker instalado.

2. **Portabilidade**: Como os containers isolam a aplicação do sistema operacional subjacente, uma aplicação em Docker pode ser executada em diferentes sistemas operacionais (Linux, Windows, macOS) e diferentes ambientes (desenvolvimento, testes, produção), sem a necessidade de ajustes manuais.

3. **Eficiência**: Containers são mais leves e rápidos do que máquinas virtuais, pois compartilham o mesmo núcleo do sistema operacional, mas mantêm um nível de isolamento.

4. **Escalabilidade e Orquestração**: O Docker facilita a escalabilidade e a orquestração de containers, permitindo o gerenciamento de múltiplos containers de forma eficiente, frequentemente utilizando ferramentas como o **Docker Compose** para definir e rodar aplicativos de múltiplos containers e o **Kubernetes** para orquestração em larga escala.

5. **Versionamento e Reusabilidade**: Docker utiliza imagens, que são versões imutáveis de containers. Essas imagens podem ser armazenadas em repositórios (como o **Docker Hub**) e reutilizadas em diferentes ambientes.

### Vantagens do Docker:
- **Consistência entre ambientes**: Desenvolvedores podem garantir que o aplicativo rodará da mesma forma em qualquer ambiente.
- **Isolamento**: Problemas em um container não afetam outros containers ou o sistema operacional subjacente.
- **Agilidade no desenvolvimento**: O Docker permite que os desenvolvedores criem, testem e compartilhem facilmente as aplicações.

### Fluxo básico de uso do Docker:
1. **Criação de uma imagem**: Você escreve um `Dockerfile` para definir a configuração do seu container (por exemplo, qual sistema operacional, quais dependências e o código da aplicação).
2. **Criação de um container**: A partir da imagem criada, você pode iniciar um ou mais containers.
3. **Execução da aplicação**: A aplicação roda dentro do container de forma isolada.
4. **Distribuição**: A imagem do Docker pode ser compartilhada em repositórios para ser executada em outros sistemas.

O Docker tem se tornado uma ferramenta essencial para desenvolvedores, especialmente em ambientes de microserviços e em sistemas com escalabilidade dinâmica.

---
# Para instalar o Docker no **Arch Linux**, você pode seguir os seguintes passos:

### 1. Atualizar o sistema
Antes de instalar qualquer pacote, é recomendável garantir que o sistema esteja atualizado. Abra o terminal e execute o comando abaixo:

```bash
sudo pacman -Syu
```

Isso irá atualizar todos os pacotes do sistema.

### 2. Instalar o Docker
O Docker está disponível no repositório oficial do Arch Linux, então você pode instalá-lo diretamente usando o **pacman**:

```bash
sudo pacman -S docker
```

Este comando irá instalar o Docker e suas dependências.

### 3. Iniciar o serviço Docker
Após a instalação, é necessário iniciar o serviço Docker. Você pode fazer isso com os seguintes comandos:

```bash
sudo systemctl start docker
```

Isso iniciará o serviço Docker imediatamente.

### 4. Habilitar o Docker para iniciar automaticamente no boot
Se você deseja que o Docker inicie automaticamente a cada reinicialização do sistema, execute:

```bash
sudo systemctl enable docker
```

### 5. Verificar se o Docker está funcionando
Para verificar se o Docker foi instalado e está funcionando corretamente, execute o seguinte comando:

```bash
sudo docker --version
```

Isso deve retornar a versão do Docker instalada.

Além disso, você pode rodar um contêiner de teste para verificar se tudo está funcionando bem:

```bash
sudo docker run hello-world
```

Esse comando irá baixar uma imagem de teste e executar um container simples que exibe uma mensagem de sucesso.

### 6. Adicionar seu usuário ao grupo Docker (opcional)
Se você quiser executar o Docker sem precisar usar `sudo` toda vez, pode adicionar seu usuário ao grupo Docker com o comando:

```bash
sudo usermod -aG docker $USER
```

Após rodar esse comando, você precisará sair e entrar novamente para que as mudanças tenham efeito.

### 7. (Opcional) Instalar o Docker Compose
Se você também precisar do **Docker Compose** (uma ferramenta para definir e rodar multi-containers), você pode instalá-lo com:

```bash
sudo pacman -S docker-compose
```

### Conclusão
Esses são os passos básicos para instalar e configurar o Docker no Arch Linux. Agora você pode começar a trabalhar com containers no seu sistema!

---

# Para rodar o MySQL no Docker, você pode seguir os seguintes passos:

1. **Instalar o Docker** (se ainda não tiver):

2. **Baixar e rodar o MySQL com Docker**:

   No terminal, utilize o comando abaixo para baixar e iniciar o MySQL no Docker.

   ```bash
   docker run --name mysql -e MYSQL_ROOT_PASSWORD=minhasenha -d mysql:latest
   ```

   **Explicação**:
   - `--name mysql`: Dá o nome "mysql" ao container.
   - `-e MYSQL_ROOT_PASSWORD=minhasenha`: Define a senha do usuário root como "minhasenha".
   - `-d`: Roda o container em segundo plano (modo "detached").
   - `mysql:latest`: Usa a imagem mais recente do MySQL disponível no Docker Hub.

4. **Verificar se o container está rodando**:

   Para verificar se o MySQL foi iniciado corretamente, execute:

   ```bash
   docker ps
   ```

   Isso exibirá uma lista dos containers em execução. O MySQL deve aparecer na lista.

5. **Acessar o MySQL dentro do container**:

   Se você quiser acessar o MySQL no seu container, use o comando:

   ```bash
   docker exec -it mysql mysql -u root -p
   ```

   Isso vai iniciar uma sessão do MySQL, pedindo a senha que você definiu (no caso, "minhasenha").

6. **Mapear portas (opcional)**:

   Se você quiser acessar o MySQL a partir de sua máquina (não apenas de dentro do container), você pode mapear a porta 3306 do MySQL para uma porta da sua máquina:

   ```bash
   docker run --name mysql -e MYSQL_ROOT_PASSWORD=minhasenha -p 3306:3306 -d mysql:latest
   ```

   Isso faz o MySQL no container ficar acessível na porta 3306 da sua máquina local.

### Dicas extras:

- **Parar o container**:
  
  Para parar o MySQL em execução:

  ```bash
  docker stop mysql
  ```

- **Excluir o container**:

  Para remover o container após parar:

  ```bash
  docker rm mysql
  ```

- **Verificar logs**:

  Se algo deu errado ou para visualizar os logs do MySQL, você pode usar:

  ```bash
  docker logs mysql
  ```

Agora você tem o MySQL rodando em um container Docker!

---

#### procura uma imagem
```bash
docker search ubuntu
```

