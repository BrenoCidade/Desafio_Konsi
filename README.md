# DesafioKonsi 🚀

## Introdução 🌟

É uma solução para a gestão eficiente de leads, oferecendo dois fluxos principais para simplificar e automatizar processos.

## Fluxos

### 🔄 Fluxo 1: Inserção e Atualização de Leads

- Integre-se com sistemas de coleta para inserir ou atualizar leads automaticamente.
- Formatação inteligente dos dados para garantir padronização e consistência.
- Validação automática de dados essenciais como nome, telefone, e-mail e cpf.

### 🌐 Fluxo 2: Consulta via Webhook

- API que permite consultar leads em tempo real via webhook.
- Valida a existência do lead com base no número de telefone.
- Retorna dados detalhados do lead, como nome, e-mail e status.
- Integração pronta para sistemas de marketing e vendas.

## Funcionalidades

### 🖋️ Inserção Automática de Leads

- Automatize a inserção de leads recebidos de diferentes fontes (formulários, APIs, etc.).
- Validação em tempo real para garantir a qualidade dos dados.
- Elimine duplicações com regras personalizadas de tratamento.

### ♻️ Atualização de Leads Existentes

- Atualize informações de leads já cadastrados com base em novos dados.
- Sincronização eficiente para manter o banco de dados sempre atualizado.
- Histórico de alterações para rastrear modificações.

### 🔗 Webhook de Consulta

- Consulta de leads via endpoint dedicado.
- Respostas rápidas com dados completos.
- Suporte a múltiplos formatos de requisição (JSON, XML).
- Logs detalhados de consultas para auditoria.

### 📞 Validação por Telefone

- Verifique a existência do lead com base no número de telefone.
- Retorne informações do lead.
- Integração para sistemas que dependem de informações precisas e atualizadas.

### 📋 Formatação Padronizada

- Padronize nomes, e-mails, telefones e cpfs automaticamente.
- Garantia de que os dados estão no formato correto para utilização.

## Benefícios 🎉

- **Automatização**: Reduza o trabalho manual na inserção e atualização de leads. 🤖
- **Confiabilidade**: Garanta a integridade e consistência dos dados. ✅
- **Velocidade**: Obtenha respostas rápidas via webhook em suas consultas. ⚡
- **Flexibilidade**: Integre-se com múltiplos sistemas e formatos de dados. 🔗
- **Eficiência**: Melhore o processo de captura, gestão e validação de leads. 📊

---

## 📘 Como Usar

Antes de iniciar, certifique-se de que você já tem instalado:

- n8n
- nodejs
- mongodb

## 🔄 Fluxo 1: Inserção e Atualização de Leads

### Passo 1: Preparando a Planilha e Salvando Como CSV com Vírgulas

1. **Preparar a Planilha**: Read/Write Files from Disk
2.   - Abra a Planilha no Excel ou Google Sheets:
3.   - Se estiver usando o Excel ou Google Sheets, abra a planilha que contém os dados dos leads que você deseja importar.
     - Verifique se os dados estão organizados corretamente com as colunas que você precisa, como: nome, telefone, released_value, cpf e data de nascimento.
  **Verifique a Estrutura das Colunas:**
     - Certifique-se de que a planilha contenha as colunas essenciais, como
       
       | name         | phone         | released_value | cpf            | birthdate          |
       |--------------|---------------|----------------|----------------|--------------------|
       | João Silva   | 11987654321   | 5000           | 123.456.789-00 | 1985/06/15         |
       | Maria Souza  | 11876543210   | 3000           | 987.654.321-00 | 1990/10/22         |
       | Carlos Lima  | 11987654322   | 2000           | 111.222.333-44 | 1987/01/30         |
   
      - **name**: Nome completo do lead.
      - **phone**: Número de telefone do lead (com DDD, sem espaços ou caracteres especiais).
      - **released_value**: Valor liberado para o lead, como limite de crédito ou valor de promoção.
      - **cpf**: Número de CPF do lead, no formato `XXX.XXX.XXX-XX`.
      - **birthdate**: A data de nascimento do lead, no formato `YYYY/MM/DD`.
  **Salvar a Planilha Como CSV com Vírgulas**
    No Excel:
      - Após ter a planilha pronta, vá até o menu Arquivo.
      - Selecione Salvar Como e escolha o formato CSV (Comma delimited) (*.csv).
      - Escolha o local onde deseja salvar o arquivo e clique em Salvar.
      - O Excel pode alertá-lo que algumas funcionalidades (como formatação) podem ser perdidas ao salvar no formato CSV. Isso é normal, pois o CSV salva apenas os dados.
    No Google Sheets:
      - Após a planilha estar pronta, clique em Arquivo no menu superior.
      - Selecione Fazer download e depois Valores separados por vírgula (.csv).
      - O arquivo CSV será baixado para o seu computador.
          
### Passo 2: Importar Workflows no n8n

1. **Acesse o n8n**: Faça login na sua instância do n8n.
2. **Adicionar Novo Workflow**:
   - Clique em "Add Workflow".
3. **Importar Workflow**:
   - Clique nos três pontinhos no canto superior direito.
   - Selecione "Import from File".
4. **Importar o Fluxo 1**:
   - Importe o arquivo de workflow fluxo_1.json.
5. **Importar o Fluxo 2**:
   - Repita os passos acima e importe o fluxo_2.json.

### Passo 4: Editar o Workflow Fluxo 1 no n8n

1. **Acesse o Workflow Fluxo 1**: No n8n, abra o workflow Fluxo 1 que você importou.
2. **Editar Nó File_csv_base**:
   - Preencha os seguintes campos com suas informações:
     - **Configure o caminho para o arquivo CSV que será utilizado como entrada. Certifique-se de que o n8n tem permissão para acessar o arquivo.**

## 🔄 Fluxo 2: Consulta de Leads via Webhook e Validação pelo Telefone

1. ### Passo 1: Configurar o Webhook no n8n
2. **Criar um novo Workflow no n8n**:
   - No painel do n8n, clique em "Add Workflow" para criar um novo fluxo.
  **Adicionar o nó Webhook**:
   - Arraste e solte o nó **Webhook** na área de trabalho do seu fluxo.
   - Configure o Webhook para o método **POST**.
   - No campo **Path**, defina o caminho do Webhook. Exemplo: `/consulta-lead`.
   - O n8n fornecerá uma URL que ficará assim: `https://seu-n8n.com/webhook/consulta-lead`.
  **Salvar o Workflow**:
   - Salve o fluxo após configurar o Webhook.
  ### Passo 2: Testar o Webhook com o Postman
  **Abra o Postman ou alguma ferramenta similar**:
   - Caso não tenha o Postman, baixe e instale-o [aqui](https://www.postman.com/downloads/).
  **Configuração da Requisição no Postman**:
   - No Postman, crie uma nova requisição **POST**.
   - No campo **URL**, insira a URL do Webhook gerado no n8n, por exemplo:  
     `https://seu-n8n.com/webhook/consulta-lead`.
  **Adicionar o Corpo da Requisição (Body)**:
   - No Postman, selecione a opção **Body**.
   - Escolha o formato **raw** e o tipo de dados **JSON**.
   - Adicione o seguinte conteúdo no corpo da requisição:

     ```json
     {
       "phone": "11987654321"
     }
     ```
  **Enviar a Requisição**:
   - Clique em **Send** no Postman para enviar a requisição.
   - O n8n irá processar a requisição e retornar uma resposta, que pode ser visualizada na aba **Response** do Postman.


---

Agora que os workflows foram importados, configurados e editados, sua automação está pronta para funcionar!
