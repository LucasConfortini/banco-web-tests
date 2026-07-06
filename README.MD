# Banco Web Tests

Este projeto tem como objetivo demonstrar a automação de testes web com Cypress e JavaScript, organizando a estrutura em testes de interface e comandos personalizados reutilizáveis.

## Objetivo do projeto

O projeto foi criado para mostrar como automatizar cenários de negócio em uma aplicação web utilizando Cypress, com foco em:

- validação de fluxos de login;
- validação de transferências bancárias;
- uso de Custom Commands para reduzir duplicação de código;
- geração de relatórios de execução em HTML.

## Componentes do projeto

A estrutura principal do projeto é composta por:

- [package.json](package.json): contém as dependências e scripts de execução do projeto.
- [cypress.config.js](cypress.config.js): configuração do Cypress, URL base e plugin de relatórios.
- [cypress/e2e](cypress/e2e): arquivos de testes automatizados.
- [cypress/support](cypress/support): implementação de comandos personalizados e configuração global do Cypress.
- [cypress/fixtures](cypress/fixtures): dados de teste, como credenciais utilizadas nos cenários.
- [cypress/reports](cypress/reports): relatórios gerados após a execução dos testes.

## Pré-requisitos

Antes de executar os testes, certifique-se de que os seguintes itens estão disponíveis:

- Node.js instalado;
- npm instalado;
- a API do projeto (banco-api) em execução;
- a aplicação web (banco-web) em execução.

A URL base configurada para os testes é:

- http://localhost:4000

## Instalação

No diretório raiz do projeto, execute:

```bash
npm install
```

Isso instalará as dependências listadas no [package.json](package.json), incluindo o Cypress e o plugin de relatórios.

## Execução dos testes

### Executar os testes no modo headless

```bash
npm test
```

### Executar os testes com interface gráfica

```bash
npm run cy:open
```

### Executar os testes em modo headed

```bash
npm run cy:headed
```

## Relatórios

Os relatórios HTML são gerados automaticamente após a execução dos testes utilizando o plugin Cypress Mochawesome Reporter.

Os arquivos ficam salvos em:

- [cypress/reports/html](cypress/reports/html)

## Testes implementados

Os cenários automatizados estão localizados em [cypress/e2e](cypress/e2e):

### Login

- Login com credenciais válidas;
- Login com credenciais inválidas, validando a mensagem de erro exibida.

### Transferência

- Transferência com dados válidos;
- Tentativa de transferência acima de R$ 5.000,00 sem token, validando a mensagem de erro.

## Custom Commands

Os comandos personalizados foram organizados em arquivos separados para melhorar a reutilização e manutenção do código.

### Comandos comuns

- `verificarMensagemNoToast(mensagem)`: valida a mensagem exibida no toast.
- `selecionarOpcaoCombobox(labelDoCampo, opcao)`: seleciona uma opção em um combobox por label.

### Comandos de login

- `fazerLoginComCredenciaisValidas()`: realiza login com as credenciais válidas armazenadas no fixture.
- `fazerLoginComCredenciaisInvalidas()`: realiza login com credenciais inválidas para validar o fluxo de erro.

### Comandos de transferência

- `realizarTransferencia(contaOrigem, contaDestino, valor)`: executa o preenchimento do formulário de transferência com os dados informados.

## Fixtures

Os dados de teste estão armazenados em [cypress/fixtures/credenciais.json](cypress/fixtures/credenciais.json), permitindo centralizar credenciais e facilitar futuras alterações.

## Observações

- Os testes dependem da aplicação web e da API estarem disponíveis no ambiente local.
- O projeto é um exemplo prático de automação com Cypress, com foco em organização, reutilização e legibilidade do código.
