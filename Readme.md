# 🐾 PetLov - Automação de Testes E2E com Cypress

![Cypress](https://img.shields.io/badge/-cypress-%23E5E5E5?style=for-the-badge&logo=cypress&logoColor=058a5e)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)
![Status](https://img.shields.io/badge/status-active-success.svg?style=for-the-badge)

> **Projeto de QA Automation:** Estratégia de testes ponta a ponta (E2E) para garantir a qualidade da plataforma de doações PetLov.

---

## 📋 Sobre o Projeto

Este repositório contém a suíte de testes automatizados desenvolvida para a aplicação **PetLov**, uma plataforma que conecta pessoas interessadas em ajudar ONGs de proteção animal.

O objetivo deste projeto vai além de testar telas: ele demonstra a implementação de uma **arquitetura de testes escalável, manutenível e integrada a um pipeline de Integração Contínua (CI)**.

### 🎯 Cenários Cobertos

A automação foca nos fluxos críticos de conversão do usuário:

* **🏠 Landing Page:** Validação de elementos visuais, títulos e redirecionamentos (Sanity Check).
* **📝 Cadastro de Ponto de Doação:**
    * **Caminho Feliz:** Preenchimento completo do formulário com integração de CEP.
    * **Integração com API Externa:** Mock da API `ViaCEP` para garantir determinismo e velocidade nos testes.
    * **Tratamento de Exceções:** Validação de campos obrigatórios, formatos inválidos e mensagens de erro amigáveis.

---

## 🛠️ Destaques Técnicos 

Aqui estão as principais estratégias de engenharia de software aplicadas neste projeto:

1.  **Design Pattern & Abstração:**
    * Uso de **Custom Commands** (`/support/commands.js`) para encapsular lógicas repetitivas (ex: `fillDonationForm`), tornando os testes mais limpos e legíveis.
    
2.  **Gestão de Massa de Dados (Fixtures):**
    * Separação completa entre lógica de teste e dados utilizando arquivos `.json` na pasta `fixtures`. Isso facilita a manutenção e permite testes com diferentes sets de dados sem alterar o código.

3.  **Network Stubbing (Mocking de API):**
    * Utilização do `cy.intercept` para controlar a requisição à API externa de CEP (`viacep.com.br`).
    * *Por que isso é importante?* Isso remove a dependência de serviços de terceiros, evita "flaky tests" (testes intermitentes) caso a API caia e torna a execução muito mais rápida.

4.  **CI/CD Pipeline (GitHub Actions):**
    * Configuração de workflow automatizado (`cypress.yml`) que executa os testes a cada push ou disparo manual.
    * **Estratégia de Matriz:** Execução paralela em múltiplos navegadores (**Chrome e Firefox**) para garantir compatibilidade cross-browser.
    * Integração com **Cypress Cloud** para gravação de vídeos e relatórios de execução.

---

## 🚀 Como Rodar o Projeto

Siga os passos abaixo para executar a suíte de testes em sua máquina.

### Pré-requisitos
* **Node.js** (v18 ou superior)
* **NPM** (Gerenciador de pacotes)

### 1. Instalação
Clone o repositório e instale as dependências:

```bash
git clone [https://github.com/seu-usuario/petlov-cypress.git](https://github.com/seu-usuario/petlov-cypress.git)
cd petlov-cypress
npm install
