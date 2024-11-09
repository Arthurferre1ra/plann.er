
# API de Gerenciamento e Organização de Viagens

## Descrição

Esta API foi desenvolvida para facilitar o planejamento, organização e gerenciamento de viagens. Com ela, é possível criar, atualizar e gerenciar detalhes de viagens, incluindo itinerários, destinos, datas, atividades e muito mais. Além disso, a API permite convidar outras pessoas para participarem da viagem, enviando convites diretamente por e-mail.

## Funcionalidades

- **Criar Viagens**: Crie uma nova viagem com informações sobre o destino, datas e descrição.
- **Gerenciar Participantes**: Adicione ou remova pessoas de uma viagem.
- **Convidar Pessoas para a Viagem**: Envie convites por e-mail para convidar outras pessoas a participarem da viagem.
- **Atualizar Detalhes da Viagem**: Modifique dados como datas, locais e atividades da viagem.
- **Listar Viagens**: Exiba todas as viagens cadastradas, com seus respectivos detalhes.
- **Consultar Viagem Específica**: Obtenha informações detalhadas de uma viagem específica.

## Endpoints

### Autenticação
Autenticação é necessária para acessar a API. Utilize um token JWT (JSON Web Token) para autenticar as requisições.

### Criar uma nova viagem

- **Endpoint**: `/trips`
- **Método**: `POST`
- **Descrição**: Cria uma nova viagem com dados de destino, datas, descrição e outras informações relevantes.
- **Exemplo de requisição**:
  ```json
  {
    "destination": "Paris, França",
    "startDate": "2024-07-15",
    "endDate": "2024-07-22",
    "description": "Viagem de férias para Paris",
    "activities": [
      "Visitar a Torre Eiffel",
      "Museu do Louvre",
      "Passeio de barco pelo Sena"
    ]
  }
  ```

### Atualizar detalhes da viagem

- **Endpoint**: `/trips/{tripId}`
- **Método**: `PUT`
- **Descrição**: Atualiza os detalhes de uma viagem específica.
- **Exemplo de requisição**:
  ```json
  {
    "description": "Viagem de férias para Paris com amigos",
    "activities": [
      "Visitar a Torre Eiffel",
      "Museu do Louvre",
      "Passeio de barco pelo Sena",
      "Disneyland Paris"
    ]
  }
  ```

### Listar viagens

- **Endpoint**: `/trips`
- **Método**: `GET`
- **Descrição**: Retorna uma lista de todas as viagens cadastradas pelo usuário autenticado.

### Obter detalhes de uma viagem

- **Endpoint**: `/trips/{tripId}`
- **Método**: `GET`
- **Descrição**: Retorna informações detalhadas de uma viagem específica.

### Convidar pessoa para a viagem

- **Endpoint**: `/trips/{tripId}/invite`
- **Método**: `POST`
- **Descrição**: Envia um convite por e-mail para uma pessoa específica.
- **Parâmetros**:
  - **email**: Endereço de e-mail da pessoa a ser convidada.
- **Exemplo de requisição**:
  ```json
  {
    "email": "exemplo@email.com"
  }
  ```

### Remover uma pessoa da viagem

- **Endpoint**: `/trips/{tripId}/participants/{participantId}`
- **Método**: `DELETE`
- **Descrição**: Remove um participante da viagem.

## Configuração

1. Clone o repositório.
   ```bash
   git clone https://github.com/seu-usuario/sua-api-de-viagens.git
   ```
2. Instale as dependências do Maven.
   ```bash
   cd sua-api-de-viagens
   mvn install
   ```
3. Configure as variáveis de ambiente no arquivo `application.properties`.

4. Execute a aplicação.
   ```bash
   mvn spring-boot:run
   ```

## Tecnologias Utilizadas

- Java
- Spring Boot
- Spring Data JPA
- Spring Security para autenticação
- JWT para autenticação
- JavaMailSender para envio de e-mails

## Autenticação

Para utilizar a API, é necessário autenticar-se. A autenticação é feita via JWT, onde cada requisição deve conter o token no cabeçalho `Authorization`:

```plaintext
Authorization: Bearer <seu_token>
```

## Exemplo de Resposta

### Exemplo de resposta para o endpoint `/trips`

```json
[
  {
    "tripId": "12345",
    "destination": "Paris, França",
    "startDate": "2024-07-15",
    "endDate": "2024-07-22",
    "description": "Viagem de férias para Paris",
    "participants": [
      {
        "name": "João",
        "email": "joao@email.com"
      }
    ]
  }
]
```

## Contribuição

Contribuições são bem-vindas! Para contribuir, faça um fork deste repositório, crie uma branch com sua funcionalidade ou correção, e abra um pull request.

---

Este README fornece uma visão geral da API de Gerenciamento e Organização de Viagens, descrevendo suas principais funcionalidades e instruções de uso para integração com clientes.