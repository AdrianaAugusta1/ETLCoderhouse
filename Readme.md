Documentação do Projeto - ETL PokeAPI**

Código

1. **Organização**
- **Comentários**: Cada função e parte do código possui explicações detalhadas sobre seu propósito e funcionamento.
- **Seccionamento**: Dividido em etapas principais: extração, transformação e carregamento.

---

### 2. **Bibliotecas**
- Foram utilizadas bibliotecas padrão do Python e adicionais:
  - `requests`: Para requisições na API.
  - `pandas`: Manipulação e tratamento de dados.
  - `sqlite3`: Criação e manipulação do banco de dados `.db`.
  - `notifypy`: Para alertas e mensagens ao usuário.

---

### 3. **Alertas**
- Alertas implementados com a biblioteca `notifypy` para informar o usuário sobre falhas na conexão com a API ou erros durante o processamento.

---

### 4. **Funções**
- **`fetch_data(url)`**: Função genérica para buscar dados na API.
- **`get_pokemon_list(limit)`**: Busca os nomes e IDs dos Pokémon.
- **`get_pokemon_types(pokemon_name)`**: Retorna os tipos de cada Pokémon.
- **`get_pokemon_stats(pokemon_name)`**: Retorna as estatísticas de cada Pokémon.

---

### 5. **API**
- **Fonte**: [PokeAPI](https://pokeapi.co/).
- **Endpoints** utilizados:
  - `/pokemon?limit={limit}`: Retorna lista de Pokémon.
  - `/pokemon/{name}`: Retorna detalhes de um Pokémon específico, incluindo tipos e estatísticas.

---

### 6. **Tratativas**
- **Falha na API**: Tratamento de erros de conexão com mensagens ao usuário.
- **Missing Values**: Tratamento de valores ausentes com preenchimento padrão.
- **Filtragem**: Aplicação de filtros, como Pokémon com `hp > 50`.

---

### 7. **Exportação**
- Dados exportados para um banco SQLite (`pokemon_data.db`), com as seguintes tabelas:
  - `pokemon_list`
  - `pokemon_types`
  - `pokemon_stats`

---

### 8. **Versionamento**
- Foi gerado o arquivo `requirements.txt` com todas as dependências do projeto.

---

### 9. **Execução do Código**
- Pode ser executado diretamente em um ambiente Python com as dependências instaladas.

---

## **Documentação**

### 1. **Organização**
- O projeto está documentado em um formato lógico, com as seções descritas claramente.

---

### 2. **Descrição das Etapas**
- **Extração**: Dados obtidos diretamente da API PokeAPI.
- **Transformação**: 
  - Os tipos de Pokémon foram separados em colunas (`type_1` e `type_2`).
  - Estatísticas transformadas em colunas individuais (`hp`, `attack`, `defense`).
- **Carregamento**: 
  - Dados integrados e exportados para um banco SQLite.

---

### 3. **Exemplos**
Exemplo de saída de dados:

**Tabela `pokemon_list`**
| pokemon_id | pokemon_name |
|------------|--------------|
| 1          | bulbasaur    |
| 2          | ivysaur      |
| 3          | venusaur     |

**Tabela `pokemon_types`**
| pokemon_name | type_1  | type_2   |
|--------------|---------|----------|
| bulbasaur    | grass   | poison   |
| ivysaur      | grass   | poison   |
| venusaur     | grass   | poison   |

**Tabela `pokemon_stats`**
| pokemon_name | hp  | attack | defense |
|--------------|-----|--------|---------|
| bulbasaur    | 45  | 49     | 49      |
| ivysaur      | 60  | 62     | 63      |
| venusaur     | 80  | 82     | 83      |

---

## **Saída (DB)**

### 1. **Organização**
- Os dados foram organizados em um banco SQLite contendo três tabelas integráveis.

---

### 2. **Consistência**
- Dados foram normalizados e validados.
- Tipos foram separados corretamente.
- Estatísticas foram filtradas e apresentadas no formato adequado.
