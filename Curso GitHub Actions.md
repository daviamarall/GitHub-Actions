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

Claro! Vou continuar com os detalhes dos módulos seguintes.

---

## Módulo 2: Criando e Executando Workflows

### Aula 2.1: Primeiro Workflow

**Criando um Arquivo de Workflow YAML**
1. No repositório GitHub, vá para a aba "Actions".
2. Clique em "Set up a workflow yourself" ou escolha um template.
3. Crie um arquivo chamado `main.yml` na pasta `.github/workflows`.

**Estrutura Básica de um Workflow**
```yaml
name: CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Run a one-line script
      run: echo Hello, world!
    - name: Run a multi-line script
      run: |
        echo Add other actions to build,
        echo test, and deploy your project.
```

### Aula 2.2: Utilizando Actions

**O que são Actions**
Actions são elementos reutilizáveis de um workflow que executam uma tarefa específica, como verificar o código, executar testes ou implantar um aplicativo. Elas podem ser públicas ou personalizadas.

**Actions Públicas vs. Actions Personalizadas**
- **Públicas**: Criadas pela comunidade e disponíveis no GitHub Marketplace.
- **Personalizadas**: Criadas por você para tarefas específicas do seu projeto.

**Exemplo de Uso de Actions Públicas**
```yaml
steps:
  - uses: actions/checkout@v2
  - name: Set up Node.js
    uses: actions/setup-node@v2
    with:
      node-version: '14'
```

### Aula 2.3: Variáveis e Secrets

**Definindo e Utilizando Variáveis**
Variáveis podem ser definidas diretamente no arquivo YAML e usadas nos steps.
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    env:
      NODE_ENV: production
    steps:
    - name: Print NODE_ENV
      run: echo ${{ env.NODE_ENV }}
```

**Armazenando e Acessando Secrets**
Secrets são informações sensíveis (como tokens e senhas) que são armazenadas de forma segura no GitHub.
1. No repositório, vá para "Settings" > "Secrets and variables" > "Actions".
2. Adicione um novo secret.
3. Utilize o secret no workflow.
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v2
    - name: Use secret
      run: echo ${{ secrets.MY_SECRET }}
```

## Módulo 3: Integrações e Notificações

### Aula 3.1: Integrando com Outros Serviços

**Integração com Slack**
1. Configure um webhook no Slack.
2. Adicione o webhook URL como um secret no GitHub.
3. Utilize a Action para enviar notificações.
```yaml
jobs:
  notify:
    runs-on: ubuntu-latest
    steps:
    - name: Send Slack notification
      uses: 8398a7/action-slack@v3
      with:
        status: ${{ job.status }}
        fields: repo,message,commit,author
      env:
        SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK }}
```

**Integração com AWS**
1. Configure as credenciais no AWS e adicione-as como secrets no GitHub.
2. Utilize Actions específicas para AWS.
```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Configure AWS credentials
      uses: aws-actions/configure-aws-credentials@v1
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: us-east-1
    - name: Deploy to S3
      run: aws s3 sync ./dist s3://my-bucket
```

### Aula 3.2: Enviando Notificações

**Configurando Notificações por Email**
GitHub Actions não suporta diretamente notificações por email, mas você pode utilizar um serviço externo como SendGrid.
1. Configure SendGrid e obtenha uma API Key.
2. Adicione a API Key como um secret no GitHub.
3. Utilize uma Action para enviar email.
```yaml
jobs:
  notify:
    runs-on: ubuntu-latest
    steps:
    - name: Send email notification
      uses: dawidd6/action-send-mail@v3
      with:
        server_address: smtp.sendgrid.net
        server_port: 587
        username: apikey
        password: ${{ secrets.SENDGRID_API_KEY }}
        subject: GitHub Actions Notification
        body: Build ${{ job.status }}
        to: user@example.com
        from: actions@example.com
```

**Notificações via Slack e Outras Plataformas**
Siga o mesmo processo descrito na Aula 3.1 para integrar e enviar notificações para diferentes plataformas usando webhooks e Actions específicas.

### Aula 3.3: Usando Webhooks

**O que são Webhooks**
Webhooks são chamados HTTP que ocorrem em resposta a um evento em um serviço. No contexto de GitHub Actions, webhooks podem ser usados para iniciar workflows em resposta a eventos externos.

**Configurando Webhooks no GitHub Actions**
1. Vá para "Settings" > "Webhooks" no repositório GitHub.
2. Adicione um novo webhook com a URL do serviço externo.
3. Configure o serviço externo para enviar dados para a URL do webhook.
4. No workflow, configure o trigger para responder a eventos do webhook.
```yaml
on:
  workflow_dispatch:
  repository_dispatch:
    types: [custom_event]

jobs:
  handle_webhook:
    runs-on: ubuntu-latest
    steps:
    - name: Process webhook payload
      run: echo "Webhook event received: ${{ github.event }}"
```

## Módulo 4: CI/CD com GitHub Actions

### Aula 4.1: Integração Contínua (CI)

**Configurando Testes Automatizados**
1. Defina os testes no repositório (por exemplo, usando Jest para Node.js).
2. Configure o workflow para executar os testes em cada push.
```yaml
jobs:
  test:
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

**Utilizando Linters e Formatadores**
1. Configure o linter e formatador no projeto (por exemplo, ESLint e Prettier para JavaScript).
2. Adicione steps no workflow para executar o linter e formatador.
```yaml
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Set up Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '14'
    - name: Install dependencies
      run: npm install
    - name: Run linter
      run: npm run lint
    - name: Run formatter
      run: npm run format
```

### Aula 4.2: Entrega Contínua (CD)

**Configurando Deploy Automatizado**
1. Defina o processo de deploy (por exemplo, deploy para Heroku, Netlify, AWS).
2. Adicione steps no workflow para realizar o deploy.
```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Deploy to Heroku
      uses: akhileshns/heroku-deploy@v3.6.8
      with:
        heroku_api_key: ${{ secrets.HEROKU_API_KEY }}
        heroku_app_name: "my-app"
        heroku_email: "user@example.com"
```

**Deploy para Diferentes Ambientes (Produção, Staging)**
1. Configure diferentes ambientes no serviço de deploy (por exemplo, diferentes apps no Heroku).
2. Adicione lógica no workflow para deploy condicional.
```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Deploy to Production
      if: github.ref == 'refs/heads/main'
      uses: akhileshns/heroku-deploy@v3.6.8
      with:
        heroku_api_key: ${{ secrets.HEROKU_API_KEY }}
        heroku_app_name: "my-production-app"
        heroku_email: "user@example.com"
    - name: Deploy to Staging
      if: github.ref == 'refs/heads/develop'
      uses: akhileshns/heroku-deploy@v3.6.8
      with:
        heroku_api_key: ${{ secrets.HEROKU_API_KEY }}
        heroku_app_name: "my-staging-app"
        heroku_email: "user@example.com"
```

### Aula 4.3: Deploys Complexos

**Deploys com Rollback**
1. Configure steps para manter um histórico de releases.
2. Adicione lógica no workflow para reverter para uma release anterior em caso de falha.
```yaml
jobs

:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Deploy to Production
      run: |
        # Deploy logic here
    - name: Rollback if deploy fails
      if: failure()
      run: |
        # Rollback logic here
```

**Estratégias de Deploy (Canary, Blue-Green)**
1. Configure diferentes ambientes de deploy para canary ou blue-green.
2. Adicione steps no workflow para realizar deploy gradual ou alternado.
```yaml
jobs:
  canary_deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Deploy Canary
      run: |
        # Canary deploy logic here

  blue_green_deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Deploy to Blue
      run: |
        # Deploy to Blue environment
    - name: Switch Traffic to Blue
      run: |
        # Switch traffic to Blue environment
```

## Módulo 5: Otimização e Melhores Práticas

### Aula 5.1: Reutilizando Workflows

**Usando Templates de Workflows**
1. Crie um arquivo de template de workflow em um repositório separado.
2. Inclua o template em outros repositórios.
```yaml
jobs:
  build:
    uses: organization/repository/.github/workflows/template.yml@main
```

**Compartilhando Workflows entre Repositórios**
1. Crie um repositório de workflows compartilhados.
2. Utilize o repositório compartilhado nos workflows dos seus projetos.
```yaml
jobs:
  build:
    uses: organization/shared-workflows/.github/workflows/build.yml@main
```

### Aula 5.2: Performance e Escalabilidade

**Otimizando Tempo de Execução**
1. Utilize caching para dependências e artefatos.
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Cache dependencies
      uses: actions/cache@v2
      with:
        path: ~/.npm
        key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
        restore-keys: |
          ${{ runner.os }}-node-
    - uses: actions/checkout@v2
    - name: Install dependencies
      run: npm install
```

**Utilizando Caching**
1. Configure caching no workflow para salvar dependências entre execuções.
```yaml
steps:
  - name: Cache npm modules
    uses: actions/cache@v2
    with:
      path: ~/.npm
      key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
      restore-keys: ${{ runner.os }}-node-
  - name: Install dependencies
    run: npm install
```

### Aula 5.3: Segurança e Conformidade

**Práticas Recomendadas de Segurança**
1. Utilize secrets para armazenar informações sensíveis.
2. Configure permissões mínimas necessárias para workflows.
3. Verifique a origem de Actions usadas (use Actions verificadas).

**Conformidade com Normas e Regulamentos**
1. Configure workflows para verificar conformidade com normas como GDPR, HIPAA, etc.
2. Adicione steps no workflow para realizar auditorias automáticas de segurança.
```yaml
jobs:
  security_audit:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run security audit
      run: npm audit
```

## Módulo 6: Casos de Uso Avançados

### Aula 6.1: Criando Actions Personalizadas

**Estrutura de uma Action Personalizada**
1. Crie um repositório para a Action.
2. Configure o `action.yml` com metadados da Action.
```yaml
name: 'My Custom Action'
description: 'A custom action for demonstration'
inputs:
  myInput:
    description: 'An input for the action'
    required: true
    default: 'default value'
runs:
  using: 'node12'
  main: 'index.js'
```

**Publicando Actions no GitHub Marketplace**
1. Complete o `action.yml` com detalhes e exemplos.
2. Adicione um README detalhado.
3. Marque uma release no GitHub e publique a Action.

### Aula 6.2: Automatizando Tarefas Comuns

**Automatizando Releases e Versionamento**
1. Configure um workflow para criar releases automáticas.
```yaml
name: Create Release

on:
  push:
    tags:
      - 'v*'

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Create GitHub Release
      uses: actions/create-release@v1
      with:
        tag_name: ${{ github.ref }}
        release_name: Release ${{ github.ref }}
        body: |
          Release notes here
        draft: false
        prerelease: false
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

**Gerenciamento de Dependências**
1. Configure workflows para atualizar dependências automaticamente.
```yaml
name: Dependency Update

on:
  schedule:
    - cron: '0 0 * * 1' # Runs every Monday at midnight

jobs:
  update-dependencies:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Update dependencies
      run: npm update
    - name: Commit updated dependencies
      run: |
        git config --global user.name 'github-actions'
        git config --global user.email 'github-actions@github.com'
        git add .
        git commit -m 'Update dependencies'
    - name: Push changes
      uses: ad-m/github-push-action@v0.6.0
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
```

### Aula 6.3: Monitoramento e Logging

**Configurando Monitoramento de Workflows**
1. Utilize ferramentas de monitoramento como Grafana e Prometheus.
2. Configure GitHub Actions para enviar métricas para essas ferramentas.

**Analisando Logs de Execução**
1. Acesse os logs de execução na aba "Actions" do repositório.
2. Utilize ferramentas de análise de logs para insights mais profundos.
```yaml
jobs:
  monitor:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v2
    - name: Send metrics to monitoring tool
      run: |
        curl -X POST -H "Content-Type: application/json" -d '{"status": "${{ job.status }}"}' https://monitoring.example.com/api
```


