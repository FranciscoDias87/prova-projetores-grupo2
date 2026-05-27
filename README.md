# Projeto Grupo 2

Arthur | Edson | Edelvan | Francisco Gabriel | Richelmer

---

## 📋 Avaliação do Código HTML

### 📊 Resumo Geral
**Nota: 6/10** - O código apresenta uma boa estrutura semântica, mas contém erros significativos em validação de dados e inconsistências na estrutura de elementos.

**Nota: 6 + Ponto_Extra 5 = 10**
Ponto extra do Multirão
---

## ✅ Pontos Positivos

### 1. **Uso Correto de Tags Semânticas (8/10)**
- ✓ `<header>` utilizado corretamente para o cabeçalho
- ✓ `<main>` envolvendo o conteúdo principal
- ✓ `<section>` para agrupar a tabela de projetores
- ✓ `<footer>` para o rodapé
- ⚠️ `<aside>` usado para o formulário - semanticamente adequado, porém poderia ser melhor contextualizado

### 2. **Boas Práticas Gerais**
- ✓ Declaração DOCTYPE correta
- ✓ Encoding UTF-8 especificado
- ✓ Meta viewport configurada para responsividade
- ✓ Código bem indentado e legível
- ✓ Ausência de "div soup" desnecessária

---

## ❌ Erros Encontrados

### 1. **Problemas na Tabela (CRÍTICO - 3/10)**

**Linha 25-29:** Primeira linha com apenas 3 `<td>` quando deve ter 4
```html
<tr>
    <td>Projetor 1</td>
    <td>08:00</td>
    <td>Maria</td>
    <!-- ❌ FALTA 1 TD - esperado 4 colunas -->
</tr>
```

**Linha 33-38:** Segunda linha com dados em ordem incorreta
```html
<tr>
    <td>2º Ano B</td>      <!-- ❌ ORDEM ERRADA -->
    <td>Projetor 2</td>
    <td>João</td>
    <td>09:00</td>
</tr>
```

**Problemas:**
- Primeira linha tem apenas 3 `<td>` quando deve ter 4 (conforme cabeçalho)
- Segunda linha tem dados em ordem incorreta (não segue: Projetor → Horário → Professor → Turma)
- Falta validação de integridade dos dados

**Correção:**
```html
<tr>
    <td>Projetor 1</td>
    <td>08:00</td>
    <td>Maria</td>
    <td>1º Ano A</td>     <!-- ✓ CORRETO: 4 colunas -->
</tr>

<tr>
    <td>Projetor 2</td>
    <td>09:00</td>
    <td>João</td>
    <td>2º Ano B</td>     <!-- ✓ CORRETO: ordem mantida -->
</tr>
```

---

### 2. **Problemas no Formulário (CRÍTICO - 4/10)**

**Linhas 48-73:** IDs e labels vazios
```html
<!-- ❌ ERRO: IDs vazios -->
<label for="">Nome do Professor</label>
<input type="text" id="">

<label for="">Data</label>
<input type="date" id="">

<label for="">Horário</label>
<input type="time" id="">

<!-- ... mais campos com mesmos problemas -->
```

**Problemas:**
- Atributo `for=""` vazio - não há associação entre `<label>` e `<input>`
- Atributo `id=""` vazio - impossível identificar campos no JavaScript
- Atributo `name=""` **COMPLETAMENTE AUSENTE** - formulário não funcionaria ao enviar dados
- Falta de `type="email"` para o campo de contato
- Falta validação `required` nos campos obrigatórios

**Correção:**
```html
<form>
    <label for="professor">Nome do Professor</label>
    <input type="text" id="professor" name="professor" required>
    
    <br><br>
    
    <label for="data">Data</label>
    <input type="date" id="data" name="data" required>
    
    <br><br>
    
    <label for="horario">Horário</label>
    <input type="time" id="horario" name="horario" required>
    
    <br><br>
    
    <label for="projetor">Projetor</label>
    <select id="projetor" name="projetor" required>
        <option value="">-- Selecione um projetor --</option>
        <option value="proj1">Projetor 1</option>
        <option value="proj2">Projetor 2</option>
        <option value="tv">TV</option>
    </select>
    
    <br><br>
    
    <label for="contato">Contato</label>
    <input type="email" id="contato" name="contato" required>
    
    <br><br>
    
    <button type="submit">Reservar</button>
</form>
```

---

### 3. **Falta de Atributos Importantes (2/10)**

| Atributo | Problema | Impacto |
|----------|----------|--------|
| `name=""` | Não existe em nenhum `<input>` | Formulário não envia dados |
| `type="submit"` | Falta no `<button>` | Comportamento impreciso |
| `required` | Ausente em campos obrigatórios | Sem validação do lado cliente |
| `type="email"` | Campo "Contato" como `text` | Sem validação de email |
| `<option value="">` | Falta em `<select>` | Sem opção padrão |

---

## 📋 Tabela Comparativa

| Critério | Status | Nota |
|----------|--------|------|
| **Tags Semânticas** | ✓ Bem utilizado | 8/10 |
| **Estrutura de Tabela** | ❌ Erros estruturais | 3/10 |
| **Estrutura de Formulário** | ❌ Erros críticos | 4/10 |
| **Limpeza do Código** | ✓ Bem indentado | 9/10 |

---

## 🎯 Recomendações Finais

1. **URGENTE:** Corrigir a associação `label-input` com `id` e `for` funcionando
2. **URGENTE:** Adicionar atributo `name` em todos os campos do formulário
3. **IMPORTANTE:** Corrigir quantidade e ordem de `<td>` na tabela
4. **IMPORTANTE:** Usar `type="email"` para campo de contato
5. **BOAS PRÁTICAS:** Adicionar atributo `required` em campos obrigatórios
6. **BOAS PRÁTICAS:** Adicionar `type="submit"` no botão e `action` no formulário

---

## 🎨 Avaliação do Código CSS

### 📊 Resumo Geral
**Nota: 4.5/10** - O código apresenta uma estrutura básica funcional, mas com várias oportunidades de melhoria em termos de organização, responsividade e uso de boas práticas modernas. Há um erro crítico na media query que compromete a responsividade.

**Arquivo:** [style.css](https://github.com/FranciscoDias87/prova-projetores-grupo2/blob/master/style.css)

---

## ✅ Pontos Positivos

### 1. **Estrutura Lógica e Semântica (7/10)**
- ✓ Organização sequencial clara: elementos globais → componentes → media queries
- ✓ Uso de seletores semânticos (`header`, `main`, `section`, `footer`)
- ✓ Código bem indentado e legível
- ✓ Sem uso excessivo de classes desnecessárias

### 2. **Uso Básico de Flexbox (6/10)**
- ✓ Implementação correta de `display: flex` no `main`
- ✓ Propriedade `justify-content: space-between` aplicada apropriadamente
- ⚠️ Faltam outras propriedades úteis como `gap`, `align-items`, `flex-wrap`

### 3. **Componentes Visuais (7/10)**
- ✓ Botões com cor distinctive (laranja) e efeito hover
- ✓ Tabela com bom contraste (cabeçalho preto, células brancas)
- ✓ Header e footer com identidade visual clara

---

## ❌ Erros Encontrados

### 1. **ERRO CRÍTICO: Media Query com Lógica Invertida (1/10)**

**Linhas 66-78:** A media query está implementada incorretamente
```css
@media(max-width:768px){
  main{
    flex-direction: row;  /* ❌ ERRO: já é o padrão (row) */
  }
  section{
    width: 500px;        /* ❌ Continua grande em mobile */
  }
  aside{
    width: 500px;        /* ❌ Idem - vai gerar overflow */
  }
  table{
    display: inline;     /* ❌ Sem efeito real */
  }
}
```

**Problemas:**
- `flex-direction: row` é o **padrão** do navegador - está desnecessário
- Deveria ser `flex-direction: column` para empilhar elementos em mobile
- Larguras continuam 500px em telas pequenas (máximo 768px) - **causará overflow**
- Sem ajustes adequados para devices reais (smartphones com 375px-480px)
- `display: inline` na tabela não faz sentido - deveria ser `display: block`

**Correção:**
```css
/* Mobile-First Approach */
@media(max-width:768px){
  main{
    flex-direction: column;  /* ✓ Empilha verticalmente */
  }
  
  section{
    width: 100%;            /* ✓ Ocupa toda a largura */
    padding: 15px;          /* ✓ Reduz padding em mobile */
  }
  
  aside{
    width: 100%;            /* ✓ Ocupa toda a largura */
    margin-left: 0;         /* ✓ Remove margem lateral */
    margin-top: 20px;       /* ✓ Adiciona espaço superior */
  }
  
  table{
    font-size: 0.9rem;      /* ✓ Reduz tamanho da fonte */
  }
  
  th, td{
    padding: 10px;          /* ✓ Reduz padding */
  }
}

/* Adicionar breakpoints adicionais */
@media(max-width:480px){
  header { height: 100px; }
  h1 { padding-top: 20px; font-size: 1.5rem; }
  section, aside { padding: 10px; }
}
```

---

### 2. **Falta de Variáveis CSS (2/10)**

**Problema:** Cores e valores são repetidos sem centralização

```css
/* ❌ Cores repetidas */
header { background: #0044aa; }      /* Linha 4 */
footer { background-color: #0044aa; } /* Linha 76 */

/* ❌ Branco repetido */
header { color: #fff; }               /* Linha 6 */
footer { color: white; }              /* Linha 77 */

/* ❌ Padding repetido */
section { padding: 20px; }            /* Linha 13 */
aside { padding: 20px; }              /* Linha 18 */
```

**Impacto:** Manutenção difícil - alterar uma cor requer mudanças em múltiplos lugares

**Solução com CSS Custom Properties:**
```css
:root {
  /* Cores */
  --color-primary: #0044aa;
  --color-text-light: #fff;
  --color-text-dark: #000;
  --color-bg-light: #eee;
  --color-bg-mid: #ccc;
  --color-accent: orange;
  
  /* Espaçamentos */
  --spacing-sm: 10px;
  --spacing-base: 15px;
  --spacing-lg: 20px;
  
  /* Border Radius */
  --radius-input: 10px;
  --radius-button: 20px;
  
  /* Tipografia */
  --font-family: sans-serif;
}

body {
  background-color: white;
  font-family: var(--font-family);
}

header {
  background: var(--color-primary);
  color: var(--color-text-light);
}

/* ... etc */
```

---

### 3. **Falta de Separação por Seções e Comentários (3/10)**

**Problema:** Sem comentários organizando o código

**Melhorado:**
```css
/* ========================================
   1. RESET E ESTILOS GLOBAIS
   ======================================== */
body {
  background-color: white;
  font-family: var(--font-family);
}

/* ========================================
   2. HEADER E NAVEGAÇÃO
   ======================================== */
header {
  background: var(--color-primary);
  /* ... */
}

h1 {
  padding-top: 40px;
  font-size: 2rem;
  font-weight: bold;
}

/* ========================================
   3. LAYOUT PRINCIPAL (FLEXBOX)
   ======================================== */
main {
  display: flex;
  justify-content: space-between;
  gap: var(--spacing-lg);
}

/* ========================================
   4. COMPONENTES: TABELA
   ======================================== */
table { /* ... */ }
th { /* ... */ }
td { /* ... */ }

/* ========================================
   5. COMPONENTES: FORMULÁRIO
   ======================================== */
input { /* ... */ }
select { /* ... */ }
button { /* ... */ }

/* ========================================
   6. FOOTER
   ======================================== */
footer { /* ... */ }

/* ========================================
   7. RESPONSIVIDADE (MEDIA QUERIES)
   ======================================== */
@media(max-width:768px) { /* ... */ }
```

---

### 4. **Hierarquia Visual Incompleta (6/10)**

**Problemas:**
- ❌ `h1` sem `font-size` explícito - não há clara hierarquia visual
- ❌ `input` e `button` sem `font-size` diferenciado
- ❌ Sem `font-weight` explícito para destaques
- ⚠️ Sem suficiente contraste entre `section` (#eee) e `aside` (#ccc)

**Melhorias:**
```css
h1 {
  padding-top: 40px;
  font-size: 2.5rem;      /* ✓ Deixa claro que é título principal */
  font-weight: bold;
  color: var(--color-text-light);
}

h2, h3 {
  font-size: 1.5rem;      /* ✓ Subtítulos */
  font-weight: bold;
}

button {
  background-color: var(--color-accent);
  padding: 15px 25px;     /* ✓ Mais padding horizontal */
  border-radius: var(--radius-button);
  border: 0;
  cursor: pointer;
  font-weight: bold;      /* ✓ Destaca como ação */
  font-size: 1.1rem;      /* ✓ Aumenta visibilidade */
  transition: opacity 0.3s;
}

button:hover {
  opacity: 0.7;           /* ✓ Melhora visual do efeito */
  transform: scale(1.05); /* ✓ Adiciona feedback interativo */
}
```

---

### 5. **Faltam Propriedades de Responsividade (3/10)**

**Problemas:**
- ❌ Sem `max-width` em containers (conteúdo pode ficar muito largo em 4K)
- ❌ Sem `gap` no flexbox (espaçamento manual com margin)
- ❌ Sem `flex-wrap` para contemplar reflow
- ❌ Sem ajustes de `font-size` responsivos

**Melhorias:**
```css
main {
  display: flex;
  justify-content: space-between;
  gap: var(--spacing-lg);    /* ✓ Espaçamento automático */
  flex-wrap: wrap;           /* ✓ Permite reflow */
  max-width: 1400px;         /* ✓ Limita em telas muito grandes */
  margin: 0 auto;            /* ✓ Centraliza */
}

section {
  flex: 1;                   /* ✓ Grow/shrink responsivo */
  min-width: 300px;          /* ✓ Não fica muito pequeno */
}

aside {
  flex: 0 0 500px;           /* ✓ Tamanho fixo com flexibilidade */
}
```

---

## 📊 Tabela Resumida de Avaliação

| Critério | Avaliação | Detalhes | Nota |
|----------|-----------|----------|------|
| **Flexbox/Grid** | ⚠️ Parcial | Flexbox básico correto, mas sem propriedades avançadas | 6/10 |
| **Media Queries** | ❌ Crítico | Lógica invertida, breakpoints insuficientes, sem ajustes reais | 2/10 |
| **Organização CSS** | ❌ Deficiente | Sem variáveis, sem comentários, sem separação por seções | 3/10 |
| **Hierarquia Visual** | ⚠️ Parcial | Presente mas incompleta, faltam font-sizes e pesos | 6/10 |
| **Responsividade Geral** | ❌ Inadequada | Media query com erro crítico que causa overflow em mobile | 2/10 |
| **GERAL** | **4.5/10** | **Melhorias urgentes necessárias** | - |

---

## 🔧 Recomendações Prioritárias

### 🔴 **CRÍTICO (Resolver Primeiro)**
1. **Corrigir media query:** `flex-direction: column` e `width: 100%` para mobile
2. **Adicionar CSS Custom Properties** para cores, espaçamentos e tipografia
3. **Adicionar mais breakpoints:** 320px, 480px, 768px, 1024px

### 🟠 **IMPORTANTE**
4. Definir `font-size` e `font-weight` explícitos para criar hierarquia visual
5. Adicionar comentários organizando o CSS em seções
6. Usar `gap` ao invés de `margin` no flexbox
7. Adicionar `max-width` e `margin: auto` ao `main`

### 🟡 **BOAS PRÁTICAS**
8. Implementar transições suaves com `transition`
9. Adicionar efeitos visuais mais sofisticados em `:hover` e `:focus`
10. Considerar usar CSS Grid para layouts mais complexos

---

## 📝 Sugestão de Código CSS Refatorado

```css
/* ========================================
   CSS CUSTOM PROPERTIES (VARIÁVEIS)
   ======================================== */
:root {
  --color-primary: #0044aa;
  --color-text-light: #fff;
  --color-text-dark: #000;
  --color-bg-light: #eee;
  --color-bg-mid: #ccc;
  --color-accent: orange;
  
  --spacing-xs: 5px;
  --spacing-sm: 10px;
  --spacing-base: 15px;
  --spacing-lg: 20px;
  --spacing-xl: 30px;
  
  --radius-input: 10px;
  --radius-button: 20px;
  
  --font-family: sans-serif;
  --font-size-base: 1rem;
  --font-size-h1: 2.5rem;
  --font-size-h2: 1.5rem;
}

/* ========================================
   RESET E ESTILOS GLOBAIS
   ======================================== */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: white;
  font-family: var(--font-family);
  font-size: var(--font-size-base);
  color: var(--color-text-dark);
}

/* ========================================
   HEADER
   ======================================== */
header {
  background: var(--color-primary);
  height: 120px;
  color: var(--color-text-light);
  text-align: center;
  padding: var(--spacing-lg) 0;
}

h1 {
  font-size: var(--font-size-h1);
  font-weight: bold;
  padding-top: var(--spacing-lg);
}

/* ========================================
   LAYOUT PRINCIPAL
   ======================================== */
main {
  display: flex;
  justify-content: space-between;
  gap: var(--spacing-lg);
  max-width: 1400px;
  margin: var(--spacing-lg) auto;
  padding: 0 var(--spacing-lg);
  flex-wrap: wrap;
}

section {
  background-color: var(--color-bg-light);
  flex: 1;
  min-width: 300px;
  padding: var(--spacing-lg);
  border-radius: var(--radius-input);
}

aside {
  background-color: var(--color-bg-mid);
  flex: 0 0 500px;
  padding: var(--spacing-lg);
  border-radius: var(--radius-input);
}

/* ========================================
   TABELA
   ======================================== */
table {
  width: 100%;
  border-collapse: collapse;
}

th {
  background-color: var(--color-text-dark);
  color: var(--color-text-light);
  padding: var(--spacing-base);
  text-align: left;
  font-weight: bold;
}

td {
  background-color: white;
  padding: var(--spacing-base);
  border-bottom: 1px solid var(--color-bg-light);
}

/* ========================================
   FORMULÁRIO
   ======================================== */
input {
  padding: 12px;
  border-radius: var(--radius-input);
  border: 2px solid var(--color-text-dark);
  font-size: var(--font-size-base);
  margin: var(--spacing-sm) 0;
}

input:focus {
  outline: none;
  border-color: var(--color-primary);
  box-shadow: 0 0 5px rgba(0, 68, 170, 0.5);
}

select {
  padding: 12px;
  border-radius: var(--radius-input);
  font-size: var(--font-size-base);
  border: 2px solid var(--color-text-dark);
  margin: var(--spacing-sm) 0;
}

button {
  background-color: var(--color-accent);
  padding: var(--spacing-base) var(--spacing-lg);
  border-radius: var(--radius-button);
  border: 0;
  cursor: pointer;
  font-weight: bold;
  font-size: 1.1rem;
  color: var(--color-text-dark);
  transition: all 0.3s ease;
}

button:hover {
  opacity: 0.8;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

button:active {
  transform: translateY(0);
}

/* ========================================
   FOOTER
   ======================================== */
footer {
  background-color: var(--color-primary);
  color: var(--color-text-light);
  padding: var(--spacing-lg);
  text-align: center;
  margin-top: var(--spacing-xl);
}

/* ========================================
   RESPONSIVIDADE
   ======================================== */

/* Tablets */
@media(max-width: 1024px) {
  main {
    flex-direction: column;
  }
  
  aside {
    flex: 0 0 auto;
    width: 100%;
  }
}

/* Dispositivos menores */
@media(max-width: 768px) {
  main {
    flex-direction: column;
    padding: 0 var(--spacing-sm);
  }
  
  section {
    width: 100%;
    padding: var(--spacing-base);
  }
  
  aside {
    width: 100%;
    margin-left: 0;
    margin-top: var(--spacing-lg);
  }
  
  header {
    height: 100px;
  }
  
  h1 {
    font-size: 1.8rem;
    padding-top: var(--spacing-base);
  }
  
  table {
    font-size: 0.9rem;
  }
  
  th, td {
    padding: var(--spacing-sm);
  }
}

/* Smartphones */
@media(max-width: 480px) {
  header {
    height: 80px;
  }
  
  h1 {
    font-size: 1.5rem;
    padding-top: var(--spacing-sm);
  }
  
  main {
    gap: var(--spacing-base);
  }
  
  section, aside {
    padding: var(--spacing-sm);
  }
  
  input, select {
    width: 100%;
  }
  
  button {
    width: 100%;
    padding: var(--spacing-base);
    font-size: 1rem;
  }
  
  table {
    font-size: 0.8rem;
  }
}
```

---

## ✨ Conclusão

O projeto tem uma **boa base visual**, mas precisa de ajustes importantes em responsividade e organização. A aplicação das recomendações acima transformaria o CSS em **código profissional e mantível**. O erro na media query é especialmente crítico pois quebra a usabilidade em dispositivos móveis.
