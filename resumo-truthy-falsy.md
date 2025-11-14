# 💡 Resumo: Valores Truthy e Falsy com TypeScript

Estes conceitos explicam como valores **não-booleanos** (como números, strings ou objetos) são avaliados em contextos booleanos (onde se espera `true` ou `false`), como em instruções `if`, `while`, ou operadores lógicos (`&&`, `||`).

Em TypeScript, os valores **Falsy** (aqueles que avaliam para `false`) e **Truthy** (aqueles que avaliam para `true`) são os mesmos do JavaScript.

O grande benefício no TS é o **Type Narrowing** (Estreitamento de Tipo), onde a verificação `if (valor)` ajuda o compilador a entender o tipo da variável dentro do bloco condicional, tornando o código mais seguro.

---

## Valores Falsy (Considerados `false`)

São os **seis** valores específicos que, quando convertidos para Booleano, resultam em `false`. Qualquer outra coisa é Truthy!

* `false` (o valor booleano)
* `0` (o número zero) e `-0` (zero negativo) e `0n` (BigInt zero)
* `""` (string vazia)
* `null` (ausência intencional de valor)
* `undefined` (variável declarada, mas sem valor atribuído)
* `NaN` (Not-a-Number, resultado de operações matemáticas inválidas)

---

### Exemplo de Type Narrowing (Estreitamento de Tipo)

O desenvolvedor fictício **Gabriel** usa uma verificação Truthy para garantir que uma variável não seja `null` ou `undefined`:

```typescript
function saudarUsuario(nome: string | null) {
  if (nome) {
    // Dentro deste bloco, o TypeScript garante que 'nome' não é null ou "" (string vazia).
    // O tipo de 'nome' é "estreitado" para apenas 'string'.
    console.log(`Olá, ${nome.toUpperCase()}!`); // 'toUpperCase' é seguro aqui.
  } else {
    // Neste bloco, 'nome' é Falsy (null ou "").
    console.log("Nome não fornecido.");
  }
}

// Chamadas:
saudarUsuario("Alice"); // Truthy -> Olá, ALICE!
saudarUsuario(null);    // Falsy -> Nome não fornecido.
saudarUsuario("");      // Falsy -> Nome não fornecido.