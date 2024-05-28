A criação de um ambiente de Integração Contínua / Entrega Contínua (CI/CD) envolve várias etapas e pode variar dependendo das ferramentas específicas que você está usando. No entanto, aqui está um exemplo geral de como você pode configurar um ambiente CI/CD usando o GitHub Actions:

1. **Crie um repositório no GitHub**

O primeiro passo é ter um repositório no GitHub onde seu código está armazenado.

2. **Crie um arquivo de fluxo de trabalho do GitHub Actions**

No seu repositório, crie um novo arquivo no diretório `.github/workflows/`, por exemplo, `.github/workflows/ci-cd.yml`. Este arquivo definirá seu fluxo de trabalho CI/CD.

3. **Defina seu fluxo de trabalho CI/CD**

No arquivo `ci-cd.yml`, você definirá as etapas do seu fluxo de trabalho CI/CD. Aqui está um exemplo simples de um fluxo de trabalho que instala dependências, executa testes e, em seguida, implanta para um ambiente quando o código é mesclado na branch principal:

```yaml
name: CI/CD Workflow

on:
  push:
    branches:
      - main

jobs:
  build-and-test:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2

    - name: Set up Node.js
      uses: actions/setup-node@v2
      with:
        node-version: 14

    - name: Install dependencies
      run: npm ci

    - name: Run tests
      run: npm test

  deploy:
    needs: build-and-test
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2

    - name: Deploy to environment
      run: echo "Deploying to environment..."
      # Add your deployment commands here
```

Este é um exemplo muito básico. Seu fluxo de trabalho real provavelmente será mais complexo e pode incluir etapas adicionais, como construção de artefatos, análise estática de código, implantação em diferentes ambientes (por exemplo, staging e produção), etc.

4. **Faça commit e push do seu arquivo de fluxo de trabalho**

Depois de criar seu arquivo de fluxo de trabalho, faça commit e push para o seu repositório. O GitHub Actions começará a executar seu fluxo de trabalho sempre que o evento especificado ocorrer (neste caso, quando o código é mesclado na branch principal).

Lembre-se de que este é apenas um exemplo e que a configuração do ambiente CI/CD pode variar muito dependendo das suas necessidades específicas e das ferramentas que você está usando.