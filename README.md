# 🧠 Desafio AWS — Análise de Sentimentos com Inteligência Artificial

Este projeto faz parte do **Desafio de Projeto da DIO (Digital Innovation One)** e tem como objetivo demonstrar a **integração entre serviços da AWS** para criar um fluxo automatizado de **Análise de Sentimentos** utilizando o **Amazon Comprehend**, com apoio de **Lambda**, **S3** e **EC2**.  

A arquitetura foi desenvolvida para representar um **cenário realista e seguro**, no qual um arquivo enviado ao S3 aciona uma função Lambda que processa o conteúdo, utiliza o Amazon Comprehend para interpretar os sentimentos e armazena os resultados no S3 — com suporte de uma instância EC2 para análises complementares e visualização dos dados.

---

## 🏗️ Arquitetura da Solução
<img width="780" height="406" alt="diagramaAWS" src="https://github.com/user-attachments/assets/ec7f8322-f082-4cb4-97f5-99adc01d145a" />



### 🔁 Fluxo de Funcionamento

1. 👤 O **usuário** envia um arquivo de texto (comentário, avaliação, etc.) a partir do computador.
2. ☁️ O arquivo é armazenado no **Amazon S3** no **bucket de entrada (input-bucket)**.  
3. ⚡ Um evento de **upload no S3** aciona automaticamente uma **função AWS Lambda**.  
4. 🧩 A **Lambda** lê o conteúdo e envia o texto para o **Amazon Comprehend** para análise de sentimentos (*Positivo*, *Negativo*, *Neutro* ou *Misto*).  
5. 💻 Uma **instância EC2** pode ser acionada para realizar análises adicionais, como:  
   - Geração de relatórios.  
   - Visualização de dados.  
   - Integração com APIs ou dashboards.  
6. 📦 Os resultados são gravados novamente no **S3** no **bucket de saída (output-bucket)**.  
7. 📊 O usuário pode visualizar ou baixar o resultado final.

```
📁 aws-sentiment-analysis
├── 📄 README.md → Documentação do projeto
├── 📁 lambda-function → Código da função Lambda (Python/Node.js)
│   ├── index.js / main.py
│   ├── requirements.txt / package.json
├── 📁 ec2 → Scripts e configurações para EC2
│   ├── setup.sh
│   └── dashboard.py
├── 📁 samples → Arquivos de exemplo para upload
│   ├── review1.txt
│   └── review2.txt
├── 📁 results → Saída processada (output-bucket)
├── 📁 diagrams → Diagramas da arquitetura
│   └── diagramaAWS.png
└── 📄 .gitignore

```

## 🚀 Como Reproduzir o Projeto

### 1️⃣ Criar buckets no S3
- `input-bucket-sentimentos`
- `output-bucket-resultados`

### 2️⃣ Criar e configurar a função Lambda
- Linguagem: Python ou Node.js  
- Permissões: acesso ao S3 e Comprehend  
- Evento de gatilho: **S3 → PUT (upload)**  

### 3️⃣ Configurar EC2
- Instância: Amazon Linux ou Ubuntu  
- Função: processar relatórios, logs ou dashboards  
- Permissões IAM: leitura dos buckets e escrita de resultados  

### 4️⃣ Testar o fluxo
- Envie um arquivo `.txt` com frases ou comentários.  
- Verifique o resultado processado no bucket de saída.  

---

## 💬 Resultados Esperados

Após o upload de um arquivo no **S3**, a **Lambda** é acionada automaticamente, envia o conteúdo para o **Comprehend**, e o resultado da análise é salvo no **bucket de saída**.  
A **instância EC2** pode ser utilizada para visualizar estatísticas ou consolidar relatórios com base nesses resultados.

---

## 🧠 Aprendizados

- Entendimento de **event-driven architecture** (arquitetura orientada a eventos).  
- Integração prática entre **Lambda**, **S3**, **Comprehend** e **EC2**.  
- Aplicação de boas práticas em **segurança e escalabilidade na AWS**.  
- Automação completa de um pipeline de **Análise de Sentimentos com IA**.

---

## 👨‍💻 Autor

**Matheus Sampaio**  
💻 Desenvolvedor | ☁️ Entusiasta em Cloud e Back-End  
🔗 [LinkedIn]([https://www.linkedin.com/](https://www.linkedin.com/in/matheus-sampaio-dev/)) 

---

> “Dito por si: como posso adicionar um EC2 nesse diagrama?”  
> — Aqui está o resultado final dessa integração, com um fluxo mais completo e realista, unindo computação serverless, IA e automação em nuvem.

---
## ✅ Boas Práticas Implementadas

- **Arquitetura híbrida (Serverless + EC2)** → Combina agilidade com flexibilidade de processamento.  
- **Disparo automático por eventos do S3** → Fluxo 100% automatizado.  
- **Segurança com AWS IAM** → Papéis e polític
