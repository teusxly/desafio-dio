# 🧠 Desafio AWS — Análise de Sentimentos com Inteligência Artificial

Este projeto faz parte do **Desafio de Projeto da DIO (Digital Innovation One)** e tem como objetivo demonstrar a **integração entre serviços da AWS** para criar um fluxo automatizado de **Análise de Sentimentos** utilizando o **Amazon Comprehend**, com apoio de **Lambda**, **S3** e **EC2**.  

A arquitetura foi desenvolvida para representar um **cenário realista e seguro**, no qual um arquivo enviado ao S3 aciona uma função Lambda que processa o conteúdo, utiliza o Amazon Comprehend para interpretar os sentimentos e armazena os resultados no S3 — com suporte de uma instância EC2 para análises complementares e visualização dos dados.

---

## 🏗️ Arquitetura da Solução

![Diagrama da Arquitetura](./diagrams/diagramaAWS.png)

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

---

## ✅ Boas Práticas Implementadas

- **Arquitetura híbrida (Serverless + EC2)** → Combina agilidade com flexibilidade de processamento.  
- **Disparo automático por eventos do S3** → Fluxo 100% automatizado.  
- **Segurança com AWS IAM** → Papéis e polític
