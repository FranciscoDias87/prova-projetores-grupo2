# Projeto Grupo 2

Arthur | Edson | Edelvan | Francisco Gabriel | Richelmer

---

## 📋 Avaliação do Código HTML

### 📊 Resumo Geral
**Nota: 6/10** - O código apresenta uma boa estrutura semântica, mas contém erros significativos em validação de dados e inconsistências na estrutura de elementos.

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
