# Data Lake Project

Este repositório contém um projeto de Data Lake que utiliza Airflow para orquestração de ingestão de dados do Postgres para o Snowflake, e dbt para transformação e criação de views. A infraestrutura foi implementada em uma máquina virtual Ubuntu hospedada no AWS EC2. O projeto foi criado ao longo do curso Bootcamp Engenharia de Dados na Udemy e seguiu as orientações do instrutor.


## Tecnologias Utilizadas
- **Postgres:** Banco de dados de origem.
- **Airflow:** Orquestração de workflows.
- **Snowflake:** Data Lake para armazenamento de dados.
- **dbt:** Transformação de dados e criação de views.
- **AWS EC2:** Hospedagem da máquina virtual Ubuntu para execução do Docker e Airflow.

## Estrutura do Repositório
- `airflow/`: Contém a DAG do Airflow que consome o Postgres e envia para o Snowflake.
- `dbt/`: Contém os modelos e configurações do dbt.
- `sql/`: Scripts SQL para criação de tabelas e transformações.
- `docs/`: Documentação adicional e diagramas.

## Configuração e Execução

### Pré-requisitos
- Conta no AWS e configuração de uma instância EC2 rodando Ubuntu.
- Docker e Docker Compose instalados na instância EC2.
- Conta no Snowflake.
- Banco de dados Postgres.

### Passo a Passo

1. **Configuração da Instância EC2:**
    - Crie uma instância EC2 no AWS com o sistema operacional Ubuntu.
    - Instale o Docker e o Docker Compose na instância.

2. **Configuração do Airflow:**
    - Navegue até a pasta `airflow/`.
    - Atualize o arquivo `docker-compose.yml` com suas credenciais do Postgres e Snowflake.
    - Execute o comando: `docker-compose up -d`.

3. **Configuração do dbt:**
    - Navegue até a pasta `dbt/`.
    - Atualize o arquivo `dbt_project.yml` com suas credenciais do Snowflake.
    - Execute os comandos:
      ```sh
      dbt deps
      dbt seed
      dbt run
      dbt test
      ```

4. **Execução do Pipeline:**
    - Acesse a interface do Airflow em `http://<SEU_IP_PUBLICO_DO_EC2>:8080`.
    - Ative e inicie o DAG `ingestion_dag`.

    É importante que dentro do EC2, configure a porta 8080 para que consiga acessar o pipeline.

## Documentação
- Consulte a pasta `docs/` para detalhes adicionais e diagramas do projeto.

## Resultados
- Centralização de dados no Snowflake.
- Criação de views otimizadas com dbt.
- Automação e escalabilidade do pipeline de dados com Airflow.

## Licença
Este projeto está licenciado sob a MIT License.
