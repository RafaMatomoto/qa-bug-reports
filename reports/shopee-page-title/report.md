# Estudo de Caso 001: Shopee Brasil

**Categoria:** Investigação de interface web / HTML  
**Data:** 27/11/2026  
**Status:** Reportado à empresa

## 1. Descrição do problema

Ao acessar a página "Minhas Compras" na versão web da Shopee Brasil, foi identificado que o título exibido na aba do navegador era:

`opl_accessibility_page_title`

O texto aparenta ser uma chave interna de tradução que não foi substituída pelo conteúdo esperado.

## 2. Ambiente de investigação

- Plataforma: Shopee Brasil
- Ambiente: Navegador Google Chrome
- Ferramenta: Chrome DevTools
- Recursos utilizados: Elements e Console

## 3. Investigação técnica

Durante a inspeção do documento HTML, foram encontrados dois elementos `<title>` dentro do elemento `<head>`:

**Primeiro elemento:**

```html
<title>opl_accessibility_page_title</title>
```

**Segundo elemento:**

```html
<title>Shopee Brasil | Na Shopee Compensa Mais | Frete Grátis e Cupons</title>
```

Ambos os elementos estavam conectados ao documento (`isConnected: true`).

Ao executar:

```javascript
document.title
```

O navegador retornou:

```text
opl_accessibility_page_title
```

Também foi utilizada a seguinte verificação:

```javascript
document.head.innerHTML.includes('opl_accessibility_page_title')
```

**Resultado:** `true`.

## 4. Resultado observado

Ao consultar a propriedade `document.title`, foi retornado o texto `opl_accessibility_page_title`.

A inspeção do `<head>` mostrou dois elementos `<title>` conectados ao documento. O primeiro continha a chave `opl_accessibility_page_title`, enquanto o segundo continha o título institucional da Shopee Brasil.

Assim, foi constatada uma divergência entre os dois elementos e o título retornado por `document.title`.

## 5. Resultado esperado

A página deveria apresentar um título legível e apropriado, sem expor chaves internas de tradução.

## 6. Análise técnica

A presença de dois elementos `<title>` no mesmo documento indica uma inconsistência na estrutura HTML observada.

O texto `opl_accessibility_page_title` apresenta características de uma chave interna de tradução ou internacionalização (i18n), mas essa interpretação não foi confirmada.

Uma possível hipótese é uma falha na geração ou atualização dos metadados da página.

A origem técnica do comportamento não foi identificada durante esta investigação.

## 7. Comunicação

O problema foi documentado e encaminhado ao atendimento da Shopee para análise da equipe técnica responsável.

## 8. Conclusão

A investigação demonstrou como ferramentas de desenvolvimento do navegador podem ser utilizadas para identificar inconsistências em aplicações web, inspecionar elementos HTML e documentar possíveis falhas técnicas.

## 9. Evidências

### Evidência 1: título exibido na aba do navegador

![Título incorreto na aba](evidence/screenshot-01-browser-tab.png.png)

### Evidência 2: inspeção do título no DevTools

![Inspeção do título no DevTools](evidence/screenshot-01-browser-title.png.png)

### Evidência 3: investigação dos elementos HTML

![JSON com os dois elementos title](evidence/screenshot-02-devtools-investigation.png.png)

---

*Estudo independente, realizado para fins educacionais e de desenvolvimento de habilidades em QA.*
