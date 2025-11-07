# Alura Carreira Especialista IA [Nível 1]

### Proprosta do Nível
> Chegou a hora de transformar ideias em automações reais. Neste passo, você vai aprender a usar ferramentas como Make, N8N para criar fluxos inteligentes que automatizam desde tarefas simples até integrações com redes sociais. Esse domínio é essencial para especialistas de IA que querem atuar em áreas como marketing, atendimento ou operações.
>
> Além disso, você vai explorar os fundamentos do RAG (Retrieval-Augmented Generation), técnica essencial para criar chatbots e assistentes capazes de buscar informações em bases de dados e responder com contexto. Com esse conjunto de habilidades, você já estará apto(a) a atuar como desenvolvedor(a) júnior de soluções baseadas em IA.

---

## n8n

Este tópico é dedicado para documentar os projetos em aula referente a n8n.
Os arquivos ficarão na pasta `projects/n8n`.

<details>
<summary><strong>Case 1: Cotação Monetária para Google Sheets</strong></summary>

**Objetivo:** Consumir uma API de cotação monetária e armazenar os dados em um banco de dados (Google Sheets).

* **API Utilizada:** [AwesomeAPI](https://economia.awesomeapi.com.br/)
* **Destino:** Google Sheets

#### Estrutura do Workflow

`Trigger Click Manual` -> `Requisição HTTPS` -> `Tratamento/Seleção dos Dados` -> `Registro no Google Sheets`

#### Workflow Visual

![Workflow N8N Case 1](https://github.com/user-attachments/assets/251b3699-f8a6-42f3-8749-cafa24aec0ce)

#### Aprendizados

* A utilizar o nó do Google Sheets no N8N para adicionar dados a uma planilha.
* A configurar o fluxo de autenticação do N8N com o Google Drive via OAuth 2.
* A criar e nomear uma planilha no Google Sheets para integrar dados do workflow.
* A mapear dados do workflow para colunas específicas em uma planilha.
* A configurar um gatilho no N8N que inicia um fluxo ao receber e-mails no Gmail.
* A integrar o N8N com uma API usando o nó HTTP Request para manipulação de dados.
* A extrair e processar informações de e-mails recebidos com o N8N.
* A utilizar um nó de configuração para filtrar e renomear dados extraídos.

</details>

<details>
<summary><strong>Case 2: Agente IA para Resumo de E-mail via SMS</strong></summary>

**Objetivo:** Receber um e-mail, criar um resumo usando IA (Gemini) e enviar este resumo via SMS.

#### Estrutura do Workflow

`Trigger Automatico (E-mail Recebido)` -> `Tratamento/Seleção dos Dados` -> `Resumo com IA (Gemini)` -> `Envio do Resumo (SMS)`

#### Workflow Visual
<img width="915" height="303" alt="flow_case_2" src="https://github.com/user-attachments/assets/e2ac6fae-d3da-4915-8374-fbe7b298dcca" />

#### Aprendizados

* Automatizar um fluxo a partir de um gatilho de e-mail (Email Trigger).
* Integrar um modelo de IA (Google Gemini) em um fluxo N8N.
* Autenticar serviços externos (Google AI Studio, 7IO SMS) usando chaves de API.
* Criar *prompts* eficazes para instruir a IA a realizar uma tarefa (como resumir um texto).
* Processar a saída de texto gerada pela IA para uso em etapas seguintes.
* Configurar e utilizar um nó de serviço de SMS para enviar mensagens formatadas.

</details>
<details>
<summary><strong>Case 3: Triagem Inteligente de E-mails com IA (Classificação e Resposta)</strong></summary>

**Objetivo:** Automatizar o atendimento ao cliente por e-mail, usando IA para classificar a complexidade (Simples/Complexo) e direcionar a ação correta.

#### Estrutura do Workflow

`Trigger (E-mail Recebido)` -> `IA Classificador ` -> `Nó "If" (Lógica Condicional)`

* **Se SIMPLES:** -> `IA Gerador de Resposta Automática` -> `Enviar E-mail (Resposta ao Cliente)`
* **Se COMPLEXO:** -> `IA Gerador de Sugestão (para Agente)` -> `Enviar E-mail (Sugestão para Equipe Interna)`

#### Workflow Visual

<img width="1581" height="786" alt="image" src="https://github.com/user-attachments/assets/9125e3a5-c59c-47ac-8655-0c074d832572" />

#### Exemplos de Execução

**1. Teste de Caso SIMPLES (Resposta Automática)**

> **E-mail Recebido do Usuário:**
> "Quais são os horários de atendimento da flexdata ?"
>
> **Resposta Automática (Gerada pela IA):**
> "Prezado cliente,
>
> A FlexData atende dos segundas à sextas-feiras, das 8h às 18h. Estamos à disposição para ajudá-lo durante este horário.
>
> Atenciosamente,
> Equipe FlexData"

**2. Teste de Caso COMPLEXO (Sugestão para Atendente)**

> **E-mail Recebido do Usuário:**
> "Preciso desenvolver um produto de dados do zero, preciso fazer uma democratização de varias teabelas de logs do meu site e após isso fezer um dashboard para extrair insights desses dados, como vocês poderiam me ajudar a desenvolver essa ideia ?"
>
> **Sugestão Gerada pela IA (Enviada ao Atendente):**
>
> **Contexto:**
> * O cliente precisa desenvolver um produto de dados do zero.
> * Ele precisa democratizar várias tabelas de logs do seu site.
> * Após isso, ele precisa criar um dashboard para extrair insights desses dados.
>
> **Proposta de solução para o atendente:**
> * Gostaria de entender melhor suas necessidades. Poderia nos detalhar sobre as seguintes informações:
>   * Quais são as principais tabelas de logs que você gostaria de democratizar?
>   * Quais são os principais insights que você gostaria de extrair do seu dashboard?
>   * Existem requisitos específicos para o desenvolvimento do seu produto de dados?
> * Em seguida, podemos discutir as opções de tecnologia e soluções mais adequadas para atender às suas necessidades.

---

#### Aprendizados

* Utilizar um modelo de IA  como um **classificador de texto** (ex: "SIMPLES" vs. "COMPLEXO").
* Implementar **lógica condicional** (branching) usando o nó "If" para criar fluxos de trabalho diferentes.
* Criar **prompts de IA distintos** para tarefas diferentes (um para classificar, outro para gerar resposta, outro para sugerir).
* Automatizar o envio de e-mails contextuais, baseados na saída da IA.
* Estruturar um fluxo de **triagem (triage) automatizado**, otimizando o tempo do atendimento humano.

</details>
