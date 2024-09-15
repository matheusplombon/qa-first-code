# QA First Code

Bem-vindo ao **QA First Code**! Este repositório contém o código e os recursos do meu primeiro projeto de Quality Assurance (QA). O objetivo deste projeto é proporcionar uma introdução prática ao mundo dos testes de software e garantir a qualidade do código.

## Sobre o Projeto

Neste repositório, você encontrará:

- **Scripts de Teste**: Exemplos de testes automatizados que demonstram práticas básicas de QA.
- **Configurações de Teste**: Arquivos de configuração e ferramentas usadas para executar os testes.
- **Documentação**: Orientações sobre como configurar e executar os testes.

## Estrutura do Repositório

- **`tests/`**: Contém scripts de teste, incluindo `registration.spec.js` e `login.spec.js`, que são usados para verificar a funcionalidade das páginas de cadastro e login.
- **`config/`**: Inclui arquivos de configuração para os testes, como `test_config.json`.

## Testes

### Testes de Registro

O arquivo `registration.spec.js` contém dois testes para a página de cadastro:

1. **Cadastro de Novo Usuário**: Verifica se é possível preencher corretamente os campos do formulário e cadastrar um novo usuário.

    ```javascript
    describe('Página de cadastro', () => {
      it('Deve preencher os campos do formulário corretamente para cadastrar um novo usuário', () => {
        cy.visit('https://adopet-frontend-cypress.vercel.app/');
        cy.get('[data-test="register-button"]').click();
        cy.get('[data-test="input-name"]').type('Ana de Jesus');
        cy.get('[data-test="input-email"]').type('ana@email.com');
        cy.get('[data-test="input-password"]').type('Senha123');
        cy.get('[data-test="input-confirm-password"]').type('Senha123');
        cy.get('[data-test="submit-button"]').click();
      })
    })
    ```

2. **Cadastro Incorreto**: Verifica se mensagens de erro são exibidas quando os campos obrigatórios não são preenchidos corretamente.

    ```javascript
    describe('Página de cadastro', () => {
      it('Preencher os campos do formulário incorretamente e exibir mensagens ao usuário', () => {
          cy.visit('https://adopet-frontend-iota.vercel.app/');
          cy.get('[data-test="register-button"]').click();
          cy.get('[data-test="submit-button"]').click();
          cy.contains('É necessário informar um endereço de email').should('be.visible');
          cy.contains('Crie uma senha').should('be.visible');
          cy.contains('Repita a senha criada acima').should('be.visible');  
      })
    })
    ```

### Testes de Login

O arquivo `login.spec.js` contém um teste para a página de login:

1. **Login de Usuário**: Verifica se é possível preencher corretamente os campos de login e autenticar o usuário na página.

    ```javascript
    describe('Página de login', () => {
      beforeEach(() => {
        cy.visit('https://adopet-frontend-cypress.vercel.app/');
        cy.get('[data-test="login-button"]').click();
      })
          it('Deve preencher os campos do login corretamente e autenticar o usuário na página', () => {
            cy.get('[data-test="input-loginEmail"]').type('ana@email.com');
            cy.get('[data-test="input-loginPassword"]').type('Senha123');
            cy.get('[data-test="submit-button"]').click();
          })
    })
    ```

## Requisitos

Para executar os testes, você precisará dos seguintes requisitos:

- [Node.js](https://nodejs.org/)
- [Cypress](https://www.cypress.io/)


