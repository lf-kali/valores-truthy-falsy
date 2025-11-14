# 🚀 Cheatsheet: Truthy/Falsy e Operadores em TypeScript

## ❌ Valores Falsy (Os que resultam em `false`)

-   `false`
-   `0`, `-0`, `0n` (BigInt zero)
-   `""` (String vazia)
-   `null`
-   `undefined`
-   `NaN`

------------------------------------------------------------------------

## ✨ Operadores Úteis em TypeScript

### 1. Operador OR Lógico (`||`)

Retorna o **primeiro valor Truthy** que encontrar.\
Se todos forem Falsy, retorna o último.

    const a = 0 || 5;   // a é 5 (0 é Falsy)
    const b = 1 || 5;   // b é 1 (1 é Truthy)

------------------------------------------------------------------------

### 2. Operador Coalescing Nulo (`??`)

Retorna o valor da direita **apenas se** o da esquerda for `null` ou
`undefined`.\
Útil para preservar valores Falsy válidos como `0` ou `""`.

    const a = 0 ?? 5;      // a é 0 (0 não é null/undefined)
    const b = null ?? 5;   // b é 5

------------------------------------------------------------------------

### 3. Duplo NOT (`!!`)

Força a conversão para booleano explícito (`true` ou `false`).

    const a = !!"olá";   // a é true
    const b = !!0;       // b é false

------------------------------------------------------------------------

### 💡 Nota

Use `if (valor)` com cautela.\
Ele funciona muito bem para verificar `null`/`undefined`, mas também
filtrará valores como `0` e `""`.

Se quiser preservar `0` ou `""`, prefira `??`.
