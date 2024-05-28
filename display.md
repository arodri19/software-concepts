A propriedade CSS `display` especifica o tipo de caixa de renderização usada por um elemento. Aqui estão alguns exemplos de como você pode usá-lo em HTML:

1. **display: block;**

Os elementos `block` começam em uma nova linha e ocupam todo o espaço disponível horizontalmente. Exemplos de elementos `block` incluem `<div>`, `<p>` e `<h1>` a `<h6>`.

```html
<div style="display: block; background-color: lightblue;">Eu sou um elemento block</div>
```

2. **display: inline;**

Os elementos `inline` não começam em uma nova linha e ocupam apenas o espaço necessário. Exemplos de elementos `inline` incluem `<span>`, `<a>`, e `<img>`.

```html
<span style="display: inline; background-color: lightgreen;">Eu sou um elemento inline</span>
```

3. **display: none;**

`display: none;` é usado para ocultar um elemento.

```html
<div style="display: none;">Eu sou um elemento oculto</div>
```

4. **display: flex;**

`display: flex;` define um elemento como um contêiner flexível e permite que você use propriedades flex para alinhar e distribuir espaço entre itens em um contêiner.

```html
<div style="display: flex; justify-content: space-between;">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>
```

5. **display: grid;**

`display: grid;` define um elemento como um contêiner de grade e permite que você use propriedades de grade para criar um layout de grade complexo.

```html
<div style="display: grid; grid-template-columns: auto auto auto; gap: 10px;">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>
```

Lembre-se de que esses são apenas alguns exemplos do uso da propriedade `display`. Existem muitos outros valores que você pode usar, dependendo das suas necessidades.