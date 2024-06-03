# GitHub Actions

## Módulo 1: Introdução ao GitHub Actions
### Aula 1.1: O que é GitHub Actions?
- Definição e história do GitHub Actions.
- Principais funcionalidades e benefícios.

### Aula 1.2: Conceitos Básicos
- Workflows, Jobs e Steps.
- Arquivo de configuração YAML.

### Aula 1.3: Configuração Inicial
- Habilitando GitHub Actions em um repositório.
- Visão geral da interface de GitHub Actions.

## Módulo 2: Criando e Executando Workflows
### Aula 2.1: Primeiro Workflow
- Criando um arquivo de workflow YAML.
- Estrutura básica de um workflow.

### Aula 2.2: Utilizando Actions
- O que são Actions.
- Actions públicas vs. Actions personalizadas.

### Aula 2.3: Variáveis e Secrets
- Definindo e utilizando variáveis.
- Armazenando e acessando secrets.

## Módulo 3: Integrações e Notificações
### Aula 3.1: Integrando com Outros Serviços
- Integração com Slack.
- Integração com AWS.

### Aula 3.2: Enviando Notificações
- Configurando notificações por email.
- Notificações via Slack e outras plataformas.

### Aula 3.3: Usando Webhooks
- O que são webhooks.
- Configurando webhooks no GitHub Actions.

## Módulo 4: CI/CD com GitHub Actions
### Aula 4.1: Integração Contínua (CI)
- Configurando testes automatizados.
- Utilizando linters e formatadores.

### Aula 4.2: Entrega Contínua (CD)
- Configurando deploy automatizado.
- Deploy para diferentes ambientes (produção, staging).

### Aula 4.3: Deploys Complexos
- Deploys com rollback.
- Estratégias de deploy (canary, blue-green).

## Módulo 5: Otimização e Melhores Práticas
### Aula 5.1: Reutilizando Workflows
- Usando templates de workflows.
- Compartilhando workflows entre repositórios.

### Aula 5.2: Performance e Escalabilidade
- Otimizando tempo de execução.
- Utilizando caching.

### Aula 5.3: Segurança e Conformidade
- Práticas recomendadas de segurança.
- Conformidade com normas e regulamentos.

## Módulo 6: Casos de Uso Avançados
### Aula 6.1: Criando Actions Personalizadas
- Estrutura de uma Action personalizada.
- Publicando Actions no GitHub Marketplace.

### Aula 6.2: Automatizando Tarefas Comuns
- Automatizando releases e versionamento.
- Gerenciamento de dependências.

### Aula 6.3: Monitoramento e Logging
- Configurando monitoramento de workflows.
- Analisando logs de execução.

## Recursos Adicionais
- Links úteis e documentação.
- Comunidade e suporte.

---

### Estrutura do Repositório no GitHub:

```plaintext
github-actions-curso/
├── modulo1/
│   ├── aula1.1.md
│   ├── aula1.2.md
│   ├── aula1.3.md
├── modulo2/
│   ├── aula2.1.md
│   ├── aula2.2.md
│   ├── aula2.3.md
├── modulo3/
│   ├── aula3.1.md
│   ├── aula3.2.md
│   ├── aula3.3.md
├── modulo4/
│   ├── aula4.1.md
│   ├── aula4.2.md
│   ├── aula4.3.md
├── modulo5/
│   ├── aula5.1.md
│   ├── aula5.2.md
│   ├── aula5.3.md
├── modulo6/
│   ├── aula6.1.md
│   ├── aula6.2.md
│   ├── aula6.3.md
└── recursos-adicionais.md
```
---

## Módulo 1: Introdução ao GitHub Actions

### Aula 1.1: O que é GitHub Actions?

**Definição e História do GitHub Actions**
GitHub Actions é uma plataforma de integração contínua e entrega contínua (CI/CD) que permite automatizar o fluxo de trabalho de desenvolvimento de software diretamente no GitHub. Lançado em 2018, o GitHub Actions oferece uma maneira poderosa e flexível de criar, testar e implantar código automaticamente.

**Principais Funcionalidades e Benefícios**
- **Automação de Workflows**: Permite a criação de workflows personalizados para diversas tarefas.
- **CI/CD Integrado**: Facilita a configuração de pipelines de integração e entrega contínua.
- **Flexibilidade e Escalabilidade**: Suporta uma ampla variedade de linguagens e plataformas.
- **Comunidade e Marketplace**: Acesso a uma vasta biblioteca de Actions criadas pela comunidade.

### Aula 1.2: Conceitos Básicos

**Workflows, Jobs e Steps**
- **Workflows**: Conjunto de jobs definidos em um arquivo YAML que são executados em resposta a eventos.
- **Jobs**: Conjunto de steps que são executados em um runner.
- **Steps**: Tarefas individuais executadas em um job.

**Arquivo de Configuração YAML**
O arquivo de configuração do GitHub Actions é escrito em YAML e define os workflows. Um exemplo básico de arquivo YAML:

```yaml
name: CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Set up Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '14'
    - name: Install dependencies
      run: npm install
    - name: Run tests
      run: npm test
```

### Aula 1.3: Configuração Inicial

**Habilitando GitHub Actions em um Repositório**
1. Acesse o repositório no GitHub.
2. Clique na aba "Actions".
3. Selecione um template de workflow ou crie um novo workflow.

**Visão Geral da Interface de GitHub Actions**
- **Aba "Actions"**: Exibe todos os workflows configurados no repositório.
- **Log de Execução**: Mostra os detalhes da execução dos workflows, incluindo status, logs e erros.

---

Continuarei preenchendo os demais módulos. Se você tiver alguma prioridade ou ajuste específico, por favor, me avise!