# clientes

Projeto Spring Boot para gestão de clientes, com persistência em PostgreSQL e API REST.

## Tecnologias
- Java 21
- Spring Boot 3.4.4
- Spring Data JPA
- Spring Web
- Lombok
- PostgreSQL
- Docker Compose (serviço externo)

## Estrutura
- `src/main/java`: código-fonte principal
- `src/test/java`: testes automatizados
- `src/main/resources`: configurações (ex: application.properties)

## Comunicação

### API REST
O serviço expõe endpoints REST para cadastro, consulta e exclusão de clientes.
- **Cadastro:** Criação de clientes via POST (`/clientes`).
- **Consulta:** Busca de clientes por código via GET (`/clientes/{codigo}`).
- **Exclusão:** Remove um cliente via DELETE (`/clientes/{codigo}`).

#### Exemplo de uso dos endpoints
- `POST /clientes` - cadastra um novo cliente (JSON no corpo da requisição)
- `GET /clientes/{codigo}` - retorna os dados do cliente pelo código
- `DELETE /clientes/{codigo}` - exclui o cliente pelo código

#### Exemplo de entidade Cliente
```java
@Entity
@Table(name = "clientes")
public class Cliente {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long codigo;
    private String nome;
    private String email;
    // ...
}
```

## Requisitos
- Java 21+
- Maven
- Docker e Docker Compose (para PostgreSQL)

## Como executar
1. **Suba o PostgreSQL:**
   - `docker-compose -f ../database/docker-compose.yml up -d`
2. **Compile e rode o projeto:**
   ```sh
   mvn clean install
   mvn spring-boot:run
   ```

## Testes
Execute:
```sh
mvn test
```

## Observações
- Dados sensíveis e arquivos temporários estão protegidos pelo `.gitignore`.
- Ajuste as configurações de banco conforme o ambiente.

