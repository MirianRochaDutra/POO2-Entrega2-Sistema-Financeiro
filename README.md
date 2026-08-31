# Módulo 3 — Strategy

No Módulo 3 foram criadas estratégias para rendimento, juros e correção monetária.

## Estratégias de rendimento, juros e correção monetária

Foi escolhida a utilização de interfaces separadas para rendimento, juros e correção monetária.

A decisão foi tomada porque, apesar de os três problemas utilizarem o padrão Strategy, eles representam conceitos diferentes dentro do sistema financeiro.

O rendimento representa o crescimento de um valor aplicado.

Os juros representam um cálculo baseado em capital, taxa e tempo.

A correção monetária representa a atualização de um valor por um índice de correção, como IPCA ou INPC.

Por isso, foi utilizada uma interface própria para cada conceito:

- `EstrategiaRendimento`
- `EstrategiaJuros`
- `EstrategiaCorrecaoMonetaria`

Essa decisão é semelhante ao que aconteceu no tutorial com `EstrategiaDesconto` e `EstrategiaFrete`. Mesmo que os dois utilizem Strategy, eles representam conceitos diferentes.

## Onde a estratégia é guardada

A estratégia é passada como parâmetro no momento do cálculo.

Essa decisão segue a ideia apresentada no Capítulo 9.

A estratégia representa a forma de realizar determinado cálculo naquele momento. Assim, não é necessário guardar uma estratégia como atributo permanente de uma entidade.

Por exemplo:

```python
estrategia = RendimentoPoupanca(10)
resultado = estrategia.calcular(1000.0)