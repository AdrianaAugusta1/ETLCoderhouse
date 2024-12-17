Documentação do Projeto - ETL PokeAPI
Autora: Adriana Augusta Beltrão  
Data: 10/09/2024  

1. Introdução
Este projeto tem como objetivo realizar um processo ETL (Extração, Transformação e Carregamento) utilizando a PokeAPI como fonte de dados. O projeto visa extrair informações sobre Pokémon, transformá-las em tabelas organizadas e exportá-las para um banco de dados SQLite.  

Objetivos: 
- Extrair dados da PokeAPI sobre lista de Pokémon, tipos e estatísticas.  
- Realizar transformações necessárias nos dados (separação de tipos, normalização e filtragem).  
- Carregar os dados em um banco SQLite.  

Base de Dados: 
A fonte de dados utilizada é a **PokeAPI**, uma API pública que disponibiliza informações sobre Pokémon em JSON.  

## 2. Bibliotecas
As bibliotecas utilizadas no projeto são:  
- requests: Realiza as requisições na API.  
- pandas: Manipulação e tratamento dos dados extraídos.  
- sqlite3: Criação e manipulação do banco de dados SQLite.  
- notifypy: Gera alertas visuais ao usuário.  

## 3. Organização do Código
O projeto está dividido em três etapas principais, seguindo o conceito ETL:  
1. Extração: Coleta de dados da API.  
2. Transformação: Manipulação dos dados (normalização, separação e filtragem).  
3. Carregamento: Exportação dos dados transformados para o banco SQLite.  

## 4. Funções

### **fetch_data(url)  
- Entrada: `url` (string) - URL do endpoint da API.  
- Saída: Retorna os dados JSON extraídos da API ou `None` em caso de erro.  
- Objetivo: Função genérica para buscar dados em uma URL da API.  

### get_pokemon_list(limit=10) 
- Entrada: `limit` (inteiro) - Número máximo de Pokémon a serem listados.  
- Saída: Lista de dicionários contendo `id` e `name` de cada Pokémon.  
- Objetivo: Buscar os nomes e IDs dos Pokémon da API.  

### get_pokemon_types(pokemon_name) 
- Entrada: `pokemon_name` (string) - Nome do Pokémon.  
- Saída: Dicionário com o nome do Pokémon e seus respectivos tipos.  
- Objetivo: Retornar os tipos de um Pokémon específico.  

### get_pokemon_stats(pokemon_name) 
- Entrada: `pokemon_name` (string) - Nome do Pokémon.  
- Saída: Dicionário com o nome do Pokémon e suas estatísticas básicas (HP, ataque, defesa).  
- Objetivo: Retornar as estatísticas de um Pokémon específico.  

### alerta(mensagem)  
- Entrada: `mensagem` (string) - Mensagem a ser exibida ao usuário.  
- Saída: Nenhuma.  
- Objetivo: Exibir alertas ao usuário utilizando a biblioteca `notifypy`.  

## 5. API 
Fonte: [PokeAPI](https://pokeapi.co/)  

Endpoints utilizados: 
1. `/pokemon?limit={limit}` - Retorna uma lista de Pokémon.  
2. `/pokemon/{name}` - Retorna detalhes de um Pokémon específico, como tipos e estatísticas.  

## 6. Tratativas  
- Falha de Conexão com a API: Quando ocorre erro na requisição, o usuário é informado através de alertas visuais.  
- Valores Ausentes (Missing Values): Preenchimento padrão é aplicado em casos de dados faltantes.  

## 7. Exportação
Os dados tratados foram exportados para um banco de dados SQLite denominado `pokemon_data.db`. As seguintes tabelas foram criadas:  
1. **pokemon_list**: Contém IDs e nomes dos Pokémon.  
2. **pokemon_types**: Contém os tipos de cada Pokémon.  
3. **pokemon_stats**: Contém as estatísticas básicas (HP, ataque e defesa) de cada Pokémon.  

---

## 8. Versionamento 
Foi gerado o arquivo `requirements.txt` com todas as dependências necessárias para execução do projeto.  

---

## 9. Execução do Código 
1. Garanta que as bibliotecas necessárias estejam instaladas com o comando:  
   ```bash
   pip install -r requirements.txt
   ```  
2. Execute o código em um ambiente Python compatível, como Jupyter Notebook ou IDE.  
3. A saída será gerada em arquivos `.db` e exibida no terminal.  

## 10. Exemplos de Saída

### **Tabela pokemon_list**  
| pokemon_id | pokemon_name |  
|------------|--------------|  
| 1          | bulbasaur    |  
| 2          | ivysaur      |  
| 3          | venusaur     |  

### Tabela pokemon_types
| pokemon_name | type_1 | type_2 |  
|--------------|--------|--------|  
| bulbasaur    | grass  | poison |  
| ivysaur      | grass  | poison |  
| venusaur     | grass  | poison |  

### Tabela pokemon_stats 
| pokemon_name | hp | attack | defense |  
|--------------|----|--------|---------|  
| bulbasaur    | 45 | 49     | 49      |  
| ivysaur      | 60 | 62     | 63      |  
| venusaur     | 80 | 82     | 83      |  

## 11. Saída no Banco de Dados 
Os dados foram organizados no banco SQLite de forma normalizada, com tabelas integráveis e consistentes.  
