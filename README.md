# 🚀 Deploy de Aplicação Web em Nuvem com AWS Elastic Beanstalk

Este repositório contém a documentação prática do laboratório de implantação de uma aplicação web (Node.js) utilizando o **AWS Elastic Beanstalk**, configurando o gerenciamento de permissões via **AWS IAM** e analisando a infraestrutura provisionada automaticamente.

---

## 🎯 Objetivo do Laboratório

O objetivo principal deste projeto foi entender como a **AWS Elastic Beanstalk** atua como uma Plataforma como Serviço (PaaS), abstraindo a complexidade do gerenciamento direto de infraestrutura e permitindo a implantação ágil e centralizada de aplicações em nuvem.

### Tecnologias e Serviços Utilizados:

* **AWS Elastic Beanstalk** (Deploy e Orquestração PaaS)
* **AWS IAM** (Identity and Access Management — Roles e Instance Profiles)
* **Amazon EC2** (Servidores virtuais/Web Server)
* **Node.js** (Ambiente de execução da aplicação)
* **Auto Scaling & Elastic Load Balancing (ELB)** (Alta disponibilidade e gerenciamento de carga)
* **Amazon CloudWatch** (Monitoramento e logs)

---

## 🏗️ Arquitetura do Elastic Beanstalk

A imagem abaixo ilustra a estrutura de infraestrutura gerenciada de forma abstrata pela AWS ao implantar a aplicação:

![Arquitetura do Elastic Beanstalk](/imagens/Captura%20de%20Tela%20(2194).png)

---

## 🛠️ Passo a Passo da Implementação

### 1. Configuração de Acesso e Permissões (AWS IAM)

Para que a instância EC2 criada pelo Elastic Beanstalk possa se comunicar com os demais serviços da AWS de forma segura, foi criada a **Role IAM** `role-beanstalk-ec2-priscillacorrea`:

![Role IAM Criada](/imagens/Captura%20de%20Tela%20(2211).png)

Em seguida, foram associadas as **políticas gerenciadas** necessárias para garantir permissões de execução Web, comunicação de worker, Docker e monitoramento de saúde:

* `AWSElasticBeanstalkWebTier`
* `AWSElasticBeanstalkWorkerTier`
* `AWSElasticBeanstalkMulticontainerDocker`
* `AWSElasticBeanstalkEnhancedHealth`

![Políticas de Permissões Anexadas à Role](/imagens/Captura%20de%20Tela%20(2212).png)

---

### 2. Criação do Ambiente no AWS Elastic Beanstalk

* Acessou-se o console do **AWS Elastic Beanstalk** para criar a aplicação `MeuApps-PriscillaCorrea` e o ambiente `MeuApps-PriscillaCorrea-desenvolvimento`.
* Selecionou-se a plataforma **Node.js 24** rodando sobre **Amazon Linux 2023**.
* Foi vinculado o **Instance Profile (Role IAM)** configurado no passo anterior.
* O deploy foi finalizado com sucesso e o ambiente ficou com status **Health: Ok**.

![Painel do Elastic Beanstalk - Ambientes e Status](/imagens/Captura%20de%20Tela%20(2213).png)

---

### 3. Validação e Monitoramento

* **Validação:** A aplicação foi acessada e testada com sucesso através do *Domain / Endpoint* público gerado automaticamente pelo Elastic Beanstalk (`MeuApps-PriscillaCorrea-desenvolvimento.eba-t7yaiwsp.us-west-1.elasticbeanstalk.com`).
* **Monitoramento:** Foram exploradas as opções do painel como **Events**, **Health & monitoring** e **Logs** para auditoria do ambiente.

---

## 🧠 Aprendizados e Competências Adquiridas

Como estudante em transição de carreira para a área de Tecnologia / Cloud Computing, este laboratório me permitiu consolidar:

1. **Princípio de Menor Privilégio (IAM):** Entendimento prático de como vincular perfis de instância (*Instance Profiles*) a recursos para garantir segurança sem expor credenciais fixas.
2. **Conceito de PaaS (Platform as a Service):** Compreensão de como o Elastic Beanstalk automatiza o provisionamento de servidores, balanceamento de carga e *auto scaling*, permitindo focar na entrega da aplicação.
3. **Observabilidade em Nuvem:** Uso das ferramentas de logs e métricas nativas para acompanhamento da saúde da aplicação.

---

## 📌 Próximos Passos

* Realizar o upload de um código-fonte próprio (pacote zip) substituindo a aplicação de exemplo.
* Configurar variáveis de ambiente diretamente pelo console do Elastic Beanstalk.

---
*Projeto desenvolvido para fins de estudo e composição de portfólio de infraestrutura em nuvem.*