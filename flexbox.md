Flexbox é uma ferramenta poderosa para alinhar e distribuir espaço entre itens em um contêiner. Aqui estão alguns exemplos práticos de como usar o Flexbox com HTML e CSS:

1. **Exemplo básico de Flexbox**

```html
<div class="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
</div>

<style>
.container {
  display: flex;
}

.item {
  flex: 1;
  border: 1px solid black;
  padding: 10px;
  margin: 5px;
}
</style>
```

2. **Alinhamento horizontal e vertical**

```html
<div class="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
</div>

<style>
.container {
  display: flex;
  justify-content: center; /* alinhamento horizontal */
  align-items: center; /* alinhamento vertical */
  height: 200px; /* altura definida para demonstrar o alinhamento vertical */
}

.item {
  border: 1px solid black;
  padding: 10px;
  margin: 5px;
}
</style>
```

3. **Flexbox com direção de coluna**

```html
<div class="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
</div>

<style>
.container {
  display: flex;
  flex-direction: column; /* muda a direção para coluna */
}

.item {
  border: 1px solid black;
  padding: 10px;
  margin: 5px;
}
</style>
```

Esses são apenas alguns exemplos de como usar o Flexbox. O Flexbox tem muitas outras propriedades e valores que você pode usar para criar layouts complexos.