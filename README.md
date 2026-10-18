# ☕ Design Patterns com Java: Dos Clássicos (GoF) ao Spring Framework

API REST desenvolvida com **Java e Spring Boot** para gerenciamento de clientes com preenchimento automático de endereço via integração com a API pública do **ViaCEP**, aplicando na prática os Padrões de Projeto clássicos do GoF (*Gang of Four*).

---

## 🎯 Padrões de Projeto (GoF) Aplicados

1. **Singleton (`@Service`, `@RestController`, `@Autowired`):**
   O contêiner de Injeção de Dependências do Spring gerencia o ciclo de vida dos componentes, garantindo uma única instância compartilhada em memória para os serviços e repositórios.
2. **Strategy (`@Repository`, `@FeignClient`, `ClienteService`):**
   Uso de interfaces para definir contratos de negócio, persistência via Spring Data JPA e chamadas HTTP declarativas com Spring Cloud OpenFeign, permitindo que o framework injete dinamicamente as implementações em tempo de execução.
3. **Facade (`ClienteServiceImpl`):**
   A camada de serviço atua como uma Fachada que abstrai a complexidade entre o banco de dados local (H2) e o serviço externo (ViaCEP). O Controller interage apenas com métodos simples, sem precisar conhecer as regras de consulta ou cache de CEP.

---

## 🚀 Tecnologias Utilizadas

- **Java 17**
- **Spring Boot 2.7**
- **Spring Data JPA** (Persistência relacional)
- **H2 Database** (Banco de dados em memória)
- **Spring Cloud OpenFeign** (Consumo da API REST do ViaCEP)
- **OpenAPI / Swagger** (Documentação interativa dos endpoints)

---

## 📌 Endpoints Principais

| Método | Rota | Descrição |
| :--- | :--- | :--- |
| `GET` | `/clientes` | Lista todos os clientes cadastrados |
| `GET` | `/clientes/{id}` | Busca um cliente específico pelo ID |
| `POST` | `/clientes` | Cadastra um cliente e busca o endereço automaticamente pelo CEP |
| `PUT` | `/clientes/{id}` | Atualiza os dados e o endereço de um cliente existente |
| `DELETE` | `/clientes/{id}` | Remove um cliente pelo ID |

### Exemplo de Payload (`POST /clientes`):
```json
{
  "nome": "Yuri Cardoso",
  "endereco": {
    "cep": "60440900"
  }
}