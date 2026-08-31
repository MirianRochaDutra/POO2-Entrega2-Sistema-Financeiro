# Sistema de Controle Financeiro Pessoal

Projeto desenvolvido em Python utilizando Programação Orientada a Objetos.

O sistema possui as classes:

- Conta
- Categoria
- Lancamento
- Fechamento
- Conciliacao
- Extrato

Também possui testes automatizados utilizando pytest.

## Fechamento

O `Fechamento` recebe uma lista de lançamentos e cria uma cópia dessa lista.

A decisão foi utilizar cópia porque o fechamento representa um registro consolidado de um período. Depois que o fechamento é criado, alterações na lista original não devem modificar o fechamento.

Além disso, a propriedade `lancamentos` também retorna uma cópia da lista. Dessa forma, código externo não consegue alterar diretamente a coleção interna do objeto.

## Conciliacao

A `Conciliacao` foi criada como uma classe própria.

A decisão foi separar essa responsabilidade porque conciliação representa uma operação específica: verificar se o total de débitos é igual ao total de créditos.

Manter essa responsabilidade em uma classe própria evita colocar responsabilidades demais dentro de `Fechamento`.

Quando os valores não conferem, o método `conciliar()` lança um `ValueError` com uma mensagem informando os valores encontrados.

## Período sem lançamentos

Um `Fechamento` pode ser criado sem lançamentos.

Nesse caso:

- quantidade de lançamentos = 0
- total de débitos = 0
- total de créditos = 0
- saldo = 0

Essa decisão permite representar um período em que não houve movimentação financeira.

## Conciliação sem lançamentos

Uma conciliação sem débitos e sem créditos é considerada conciliada, pois os dois lados possuem valor zero.

Portanto:

```text
débitos = 0
créditos = 0