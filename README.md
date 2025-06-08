# Atividade Final — ETL + Classificação (MongoDB & Elasticsearch)

## ☑️ Visão geral

Este projeto realiza as seguintes etapas:

1. Faz ETL do arquivo **`df_file.csv`**.
2. Insere os documentos brutos em **MongoDB** (`lab_ml.tweets_raw`) e **Elasticsearch** (`tweets_raw`).
3. Treina, do zero, um modelo **TF-IDF + RandomForest**.
4. Rotula uma amostra e grava em **`tweets_predicted`** (MongoDB + Elasticsearch).
5. Exibe métricas de avaliação para validação do modelo.

---

## 🚀 Passo a passo Docker

1. **Subir MongoDB** (dentro da pasta `mongodb/`):

   ```bash
   cd mongodb/
   sudo docker-compose up -d
   ```

   - Inicia o container de MongoDB na porta **27017**.

2. **Subir Elasticsearch + Kibana** (dentro da pasta `elastic-logstash/`):

   ```bash
   cd ../elastic-logstash/
   sudo docker-compose up -d
   ```

   - Inicia o container de Elasticsearch na porta **9200** e Kibana na porta **5601**.

3. **Subir Jupyter Notebook** (dentro da pasta `Jupyter-notebook/`):

   ```bash
   cd ../Jupyter-notebook/
   sudo docker-compose up -d --build
   ```

   - Inicia o container do Jupyter Notebook na porta **8888**.

4. **Acessar Jupyter**:

   - Abra no navegador: [http://localhost:8888](http://localhost:8888).
   - Interface web do Jupyter Notebook estará disponível.

5. **Copiar o CSV**:

   - Copie **`df_file.csv`** para a pasta `Jupyter-notebook/notebooks/`.
   - O arquivo ficará disponível ao lado dos notebooks dentro do container.

6. **Executar ETL**:

   - No Jupyter, abra **`01_Upload.ipynb`** e clique em **Run All**.
   - Espera-se a mensagem: `✅ Inseridos N documentos em MongoDB e Elasticsearch`.

7. **Conferir índice no Kibana**:

   - Abra no navegador: [http://localhost:5601](http://localhost:5601) → **Discover** → crie um _index pattern_ **`tweets_raw*`**.
   - Você deverá ver todos os documentos brutos inseridos em Elasticsearch.

8. **Treinar e rotular**:

   - No Jupyter, abra **`02_Train_Predict.ipynb`** e clique em **Run All**.
   - Será exibida a acurácia no teste e mensagem: `✅ Amostra rotulada e salva`.


## 🔧 Configurações adicionais

- **Portas a liberar (VM / VirtualBox / WSL):**

  - MongoDB: 27017
  - Elasticsearch: 9200
  - Kibana: 5601
  - Jupyter: 8888

- **Credenciais MongoDB usadas nos notebooks:**

  ```text
  usuário: admin
  senha: 123456
  banco: lab_ml
  ```
