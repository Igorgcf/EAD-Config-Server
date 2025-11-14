# Config Server – Microservice

## Servidor central de configuração da plataforma EAD, responsável por armazenar, versionar e distribuir propriedades para os microserviços.
## Implementado com Java, Spring Boot e Spring Cloud Config, com integração ao Eureka para descoberta de serviços.

### Descrição do Projeto

O Config Server é um componente fundamental da arquitetura distribuída da plataforma, responsável por garantir que todos os microserviços compartilhem configurações consistentes e atualizadas a partir de uma fonte centralizada.

* #### Ele oferece:

Servidor de configuração Spring Cloud Config.

Versionamento de configurações via repositório Git.

Integração com Eureka para que outros microserviços o encontrem automaticamente.

Centralização das propriedades de:

ead-authuser

ead-course

Recarregamento dinâmico de propriedades (caso o Spring Cloud Bus seja adicionado futuramente).

* #### Tecnologias Utilizadas

Java 17+

Spring Boot

Spring Cloud Config Server

Spring Cloud Netflix Eureka Client

Git (repositório de configuração)

Maven

* #### Funcionalidades
Centralização de Configurações

O Config Server expõe arquivos .properties ou .yml versionados em um repositório Git, permitindo que todos os microserviços mantenham configurações sincronizadas.

Integração com Eureka

Registra-se como cliente do Eureka para facilitar descoberta e comunicação entre microserviços.

Suporte a múltiplos ambientes

O Spring Config permite organizar configurações por perfil:

application.yml
ead-course-service.yaml
ead-course-service-h2.yaml
ead-authuser-service.yaml
ead-authuser-service-h2.yaml

* #### Atualização dinâmica (opcional)

Compatível com Spring Actuator + Cloud Bus para atualização automática de propriedades sem reiniciar instâncias.

* #### Estrutura do Repositório de Configuração

O repositório Git e GitHub deve conter arquivos como:

/config-repo

  ├── application.yaml
  
  ├── ead-authuser-service.yaml
  
  ├── ead-course-service.yaml
  
  ├── ead-authuser-service-h2.yaml
  
  ├── ead-course-service-h2.yaml
  
  └── ...

* #### Expondo Configurações

O Config Server expõe endpoints como:

```markdown
GET /{application}/{label}
```

```markdown
GET /{application}-{profile}/{label}
```

Exemplos:

```markdown
http://localhost:8888/ead-authuser-service/main
```

```markdown
http://localhost:8888/ead-course-service-h2/main
```

* #### Como Executar o Projeto

Certifique-se de que o Eureka Server está ativo.

Certifique-se de que o repositório GitHub com as configurações esteja acessível.

Clone o repositório do Config Server:

```markdown
git clone https://github.com/Igorgcf/EAD-Config-Server.git
```

Compile e execute:

```markdown
mvn clean install
```
ou

```markdown
mvn spring-boot:run
```


O serviço estará acessível em:

http://localhost:8888

![image](https://miro.medium.com/v2/resize:fit:720/format:webp/1*ae7ztydy0-O2tYOjhIgMSg.png)
