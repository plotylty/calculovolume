### README
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=paulossjunior_calculovolume&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=paulossjunior_calculovolume)
# Cálculo do Volume de um Cilindro

Este projeto implementa uma função para calcular o volume de um cilindro com base no raio e na altura fornecidos, além de testes automatizados para garantir a qualidade do código. A biblioteca `pytest` é utilizada para os testes, com suporte a relatórios de cobertura de código por meio do plugin `pytest-cov`.

---

## Funcionalidades

- **Cálculo do Volume**: Implementa a fórmula \( V = \pi \cdot r^2 \cdot h \) para calcular o volume de um cilindro.
- **Validação de Dados**: Gera um erro se o raio ou a altura forem negativos ou zero.
- **Testes Automatizados**: Testa a função com vários cenários, incluindo entradas válidas e inválidas.
- **Cobertura de Código**: Mede a cobertura dos testes usando `pytest-cov`.

---

## Estrutura do Projeto

```
.
├── volume_cilindro.py       # Código principal
├── test_volume_cilindro.py  # Testes com pytest
└── README.md                # Documentação
```

---

## Requisitos

- Python 3.7 ou superior
- Dependências do projeto:
  - `pytest`
  - `pytest-cov`

Instale as dependências executando:

```bash
pip install pytest pytest-cov
```
ou 

```bash
pip install -r requirements.txt
```
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

2. **Executando os Testes:**

   Para rodar os testes automatizados, execute o comando:

   ```bash
   pytest test_volume_cilindro.py
   ```

3. **Gerando Relatório de Cobertura:**

   Para medir a cobertura dos testes, utilize o comando:

   ```bash
   pytest --cov=volume_cilindro test_volume_cilindro.py
   ```

   Exemplo de saída esperada:
   ```
   ---------- coverage: platform darwin, python 3.x.x ----------
   Name                    Stmts   Miss  Cover
   -------------------------------------------
   volume_cilindro.py          6      0   100%
   ```

---

## Estrutura do Código

### Módulo `volume_cilindro.py`

Contém a função principal:

```python
def calcular_volume_cilindro(raio, altura):
    """
    Calcula o volume de um cilindro.
    Fórmula: V = π * r² * h
    """
    if raio <= 0 or altura <= 0:
        raise ValueError("O raio e a altura devem ser maiores que zero.")
    return math.pi * (raio ** 2) * altura
```

### Testes

Os testes garantem o correto funcionamento do código e cobrem cenários como:

- Valores válidos para raio e altura.
- Valores negativos ou zero para raio ou altura.

Exemplo de teste:

```python
def test_volume_cilindro_valores_validos():
    raio = 3
    altura = 5
    esperado = math.pi * (raio ** 2) * altura
    resultado = calcular_volume_cilindro(raio, altura)
    assert pytest.approx(resultado, rel=1e-5) == esperado
```

---
