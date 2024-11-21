[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=paulossjunior_calculovolume&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=paulossjunior_calculovolume)


Este projeto implementa uma função para calcular o volume de um cilindro com base no raio e na altura fornecidos, além de testes automatizados para garantir a qualidade do código. O GitHub Actions é utilizado para CI/CD, executando os testes automatizados e enviando os resultados para o SonarCloud.

---

## Funcionalidades

- **Cálculo do Volume**: Implementa a fórmula \( V = \pi \cdot r^2 \cdot h \) para calcular o volume de um cilindro.
- **Validação de Dados**: Gera um erro se o raio ou a altura forem negativos ou zero.
- **Testes Automatizados**: Testa a função com vários cenários, incluindo entradas válidas e inválidas.
- **Cobertura de Código**: Mede a cobertura dos testes com `pytest-cov`.
- **Integração com CI/CD**: 
  - Execução automatizada dos testes com GitHub Actions.
  - Envio de análise de código e cobertura de testes para o SonarCloud.

---

## Estrutura do Projeto

```
.
├── volume_cilindro.py       # Código principal
├── test_volume_cilindro.py  # Testes com pytest
├── .github/
│   └── workflows/
│       └── python-tests-sonar.yml  # Workflow para GitHub Actions
└── README.md                # Documentação
```

---

## Requisitos

- Python 3.7 ou superior
- Dependências do projeto:
  - `pytest`
  - `pytest-cov`
- GitHub Actions configurado no repositório.
- Conta e projeto configurados no [SonarCloud](https://sonarcloud.io/).

---

## Como Usar

1. **Cálculo do Volume:**

   Importe e utilize a função `calcular_volume_cilindro`:

   ```python
   from volume_cilindro import calcular_volume_cilindro

   raio = 3
   altura = 5
   volume = calcular_volume_cilindro(raio, altura)
   print(f"O volume do cilindro é: {volume:.2f}")
   ```

2. **Executando os Testes Localmente:**

   Para rodar os testes automatizados, execute o comando:

   ```bash
   pytest --cov=volume_cilindro
   ```

3. **Gerando Relatório de Cobertura Localmente:**

   Para gerar o relatório de cobertura no formato XML, use:

   ```bash
   pytest --cov=volume_cilindro --cov-report=xml
   ```

---

## Integração com GitHub Actions

Este repositório utiliza o GitHub Actions para executar testes automatizados e integrar com o SonarCloud. O workflow está definido em `.github/workflows/python-tests-sonar.yml`.

### Pipeline

1. **Testes Automatizados:**
   - Roda os testes usando `pytest`.
   - Gera um relatório de cobertura no formato XML.
   - Armazena o relatório como artefato no GitHub Actions.

2. **SonarCloud:**
   - Envia os resultados da análise de código e cobertura para o SonarCloud.
   - Exibe os relatórios detalhados de qualidade do código na interface do SonarCloud.

### Como Configurar:

1. Configure um projeto no SonarCloud ([Iniciar](https://sonarcloud.io/)).
2. Gere um **token de autenticação** no SonarCloud.
3. Adicione o token ao GitHub Secrets do repositório:
   - Vá em **Settings > Secrets and variables > Actions > New repository secret**.
   - Crie um segredo chamado `SONAR_TOKEN` com o valor do token gerado.
4. Atualize o arquivo `.github/workflows/python-tests-sonar.yml` com:
   - O nome da sua organização: `-Dsonar.organization=seu_organizacao`.
   - O nome do projeto no SonarCloud: `-Dsonar.projectKey=seu_projeto`.

---

## Resultado Esperado

### GitHub Actions
- Ao realizar um `push` na branch principal ou abrir um pull request:
  - Os testes são executados.
  - O relatório de cobertura é enviado ao SonarCloud.

### SonarCloud
- Exibe as seguintes métricas:
  - **Cobertura de Código:** Percentual de código coberto por testes.
  - **Qualidade do Código:** Relatórios de problemas detectados, duplicações, etc.
  - **Manutenibilidade:** Métricas para melhorias no código.

---


