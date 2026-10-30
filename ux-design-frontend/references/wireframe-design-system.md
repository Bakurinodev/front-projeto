# Wireframe, Design System e Style Guide

## Sumário
1. Wireframe
2. Design System, Pattern Library e Style Guide
3. Como aplicar em projetos para cliente

---

## 1. Wireframe

**O que é:** diagrama visual que esboça a estrutura de um site ou app: quais elementos existem, como se relacionam e onde ficam. Também chamado de protótipo de baixa fidelidade. Vem **antes** de cores, fontes e imagens.

**Por que importa:** o que o desenvolvedor imagina muitas vezes não é o que o cliente quer. Desenhar e validar antes de detalhar evita o cenário em que, na entrega, o cliente diz que não gostou e o retrabalho começa do zero. O cliente também fica mais tranquilo quando participa das etapas de criação.

**O que colocar:**
- Liste todos os elementos que a página precisa: cabeçalho, menu, campos de formulário, botões de CTA, rodapé.
- Dê destaque visual proporcional à importância, usando diferença de tamanho (não precisa ser o tamanho final) e espaçamento para criar hierarquia.
- Em web, pense em como os elementos se reorganizam em telas menores, inclusive o que some no mobile.
- Anote elementos com funcionalidade, comportamento de interação ou requisito técnico.

**Quatro tipos, do mais simples ao mais completo:**

| Tipo | Descrição |
|---|---|
| Básico (baixa fidelidade) | esquema simples, geralmente preto e branco ou cinza |
| Anotado | o básico mais notas curtas explicando o motivo e o propósito de cada item, agrupadas por área de conteúdo/funcionalidade |
| Fluxo de usuário | visualizações estáticas de um wireframe interativo, ou apresentação de slides mostrando o caminho do usuário |
| Interativo de alta definição | permite experimentar toques, cliques e deslizes; feito em ferramenta como Figma |

Escolha o menor tipo que valida a dúvida do momento. Se a dúvida é "onde fica o quê", o básico basta.

## 2. Design System, Pattern Library e Style Guide

São três coisas relacionadas que costumam ser confundidas:

| Termo | O que é | Escopo |
|---|---|---|
| **Style Guide** (guia de estilo) | documento com diretrizes de identidade visual: logos, fontes, cores, grids, ícones, tipografia, botões e seus estados | só a parte visual |
| **Pattern Library** (biblioteca de padrões) | conjunto de componentes reutilizáveis que funcionam como vocabulário: formulários, botões, blocos de texto, CTAs | só os componentes de interface |
| **Design System** | sistema de padronização com elementos, regras e princípios; abrange style guide + pattern library e evolui com o produto | tudo, mais as regras de uso |

**Por que usar um design system:** consistência, padronização e identidade da marca; replicar telas rapidamente com componentes prontos; a equipe gasta menos tempo ajustando aparência e mais tempo nos problemas complexos do produto.

**Como funciona:** é o guia de referência para criar novas interfaces. Precisa ser consultado antes de construir e atualizado quando as diretrizes mudam, para manter todas as equipes alinhadas.

**O que um style guide deve conter (exemplo de tipografia do ebook):**
- famílias tipográficas (por exemplo, uma para títulos e outra para texto), com pesos usados;
- tabela de hierarquia de texto com nome, peso, tamanho e altura de linha, indo de Display até Heading 6 (no exemplo, títulos com line-height de 1,3 × o tamanho da fonte);
- o mesmo raciocínio para cores, espaçamentos, ícones, botões e estados.

Um style guide serve principalmente a quem chega num projeto: dá o necessário para trabalhar de acordo com o padrão, com menos ajustes no fim.

## 3. Como aplicar em projetos para cliente

1. **Antes de codar:** wireframe de baixa fidelidade, aprovado pelo cliente. Anote o que não é óbvio.
2. **Ao definir identidade:** paleta e tipografia primeiro (veja `cores.md`), depois o resto.
3. **Ao codar:** transforme o style guide em tokens CSS e em poucos componentes base (botão, campo, card, modal). Telas novas nascem desses componentes.
4. **Ao entregar:** inclua uma página ou documento curto de style guide. Para projetos pequenos, uma página com cores, tipografia, botões e espaçamentos já cumpre o papel e custa pouco.
5. **Ao evoluir:** quando uma decisão visual mudar, mude no token/componente, não tela por tela.
