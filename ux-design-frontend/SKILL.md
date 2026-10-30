---
name: ux-design-frontend
description: Fundamentos de UX/UI para desenvolvedores frontend, destilados do ebook "UX Design para desenvolvedores frontend" (Iuri Silva). Use sempre que o usuário pedir para criar, revisar, melhorar ou criticar uma interface (site, landing page, app, formulário, dashboard, componente, tela), escolher paleta de cores, definir espaçamento ou hierarquia visual, desenhar botão/CTA, montar wireframe, design system ou style guide, ou avaliar usabilidade com as heurísticas de Nielsen. Use também ao gerar HTML/CSS/React/Tailwind de telas, para que o código já saia com bons fundamentos visuais, mesmo que a pessoa não diga "UX" ou "design". Gatilhos típicos - "melhora essa tela", "essa interface tá feia/confusa", "review de UI", "qual paleta usar", "grid de 8px", "botão de CTA", "wireframe", "design system", "style guide", "usabilidade", "heurísticas de Nielsen".
---

# UX Design para desenvolvedores frontend

Este skill transforma os conceitos do ebook em regras aplicáveis ao código. Ele serve para dois trabalhos: **construir** telas com bons fundamentos e **revisar** telas existentes. Descubra qual dos dois o pedido é e siga a seção correspondente.

Os arquivos em `references/` têm o detalhe de cada tema. Leia só o que o pedido exige (tabela no fim deste arquivo).

## Modo construir (gerando UI)

Antes de entregar o código, passe a tela por este checklist. A ordem importa: hierarquia e espaçamento resolvem a maior parte do que parece "feio" em interfaces feitas por devs.

1. **Hierarquia.** O elemento mais importante da tela é óbvio em 2 segundos? Títulos maiores e mais pesados, texto corrido mais leve/claro. Tamanho, peso e cor trabalham juntos; mudar só um costuma não bastar.
2. **Proximidade.** Itens relacionados ficam colados; grupos diferentes ficam separados. Regra prática do ebook: a distância entre grupos é o dobro da distância dentro de um grupo.
3. **Espaçamento.** Espaço em branco é parte do design, não desperdício. Use a escala de múltiplos de 8 (snippet abaixo) em vez de valores soltos como 13px ou 22px.
4. **Alinhamento.** Uma borda esquerda comum para título, subtítulo e corpo. Dois alinhamentos quase iguais parecem erro.
5. **Repetição.** Mesmo raio de borda, mesmas sombras, mesmo padrão de botão e card em toda a interface. Componentes iguais para funções iguais.
6. **Contraste.** Texto sobre imagem precisa de overlay/gradiente; texto claro sobre fundo claro é falha. Veja os números de contraste na seção "Complementos".
7. **Cores.** Defina a paleta no início e use poucas. Evite cores primárias puras e saturadas no máximo (`#00ff00`, `#ff0000`); tons ligeiramente mais suaves parecem profissionais. Detalhes em `references/cores.md`.
8. **CTA.** Uma ação primária por contexto, com frase curta ("Inscreva-se"), cor de destaque da paleta, posição óbvia e bastante padding interno.
9. **Estados e feedback.** Carregando, vazio, erro, sucesso, hover, foco, desabilitado. Interface sem esses estados passa a impressão de quebrada. Veja a heurística 1 e a 9 em `references/heuristicas-nielsen.md`.
10. **Formulários.** Só peça o que é necessário agora; o resto vai para depois do login. Erro aparece perto do campo, em linguagem simples, dizendo como corrigir.

Ao entregar, acrescente no fim 3 a 5 linhas com as decisões de UX que você tomou e por quê (por exemplo, "botão primário em azul da paleta, 48px de altura, 32px de distância do campo anterior"). Isso ensina o usuário e permite que ele discorde com base em algo concreto. Não faça palestra sobre os princípios.

### Tokens base (escala de 8)

Ponto de partida para CSS. Ajuste à marca do projeto.

```css
:root {
  /* espaçamento: múltiplos de 8, com 4 como meio-passo para ajustes finos */
  --space-1: 4px;
  --space-2: 8px;   /* dentro de um grupo (label -> campo) */
  --space-3: 16px;  /* entre itens do mesmo bloco */
  --space-4: 24px;  /* entre blocos relacionados */
  --space-5: 32px;  /* antes da ação principal / entre grupos */
  --space-6: 48px;
  --space-7: 64px;  /* entre seções */

  /* tipografia: hierarquia por tamanho + peso */
  --font-display: 700 40px/1.3 var(--font-sans);
  --font-h1: 700 32px/1.3 var(--font-sans);
  --font-h2: 700 24px/1.3 var(--font-sans);
  --font-body: 400 16px/1.5 var(--font-sans);

  /* o design define as cores logo no começo; nomeie por função, não por cor */
  --color-primary: ;
  --color-text: ;
  --color-text-muted: ;
  --color-surface: ;
  --color-danger: ;
}
```

Em Tailwind, a escala padrão já é em passos de 4px (`p-2` = 8px, `p-4` = 16px, `p-8` = 32px); use classes múltiplas de 2 (`2, 4, 6, 8, 12, 16`) para ficar dentro do grid de 8.

## Modo revisão (avaliando UI existente)

Quando o usuário mostrar uma tela (print, código ou descrição) e pedir opinião, use este formato. Seja específico: "o botão está pequeno" é pouco; "o botão tem 28px de altura e 8px de padding lateral, o que o deixa menor que o texto ao redor, sugiro 48px de altura e 24px de padding" é revisão.

```
## Veredito
1-2 frases: o que mais pesa na experiência hoje.

## Problemas (do mais grave ao menos grave)
### 1. [título curto do problema]
- **O que vi:** [fato observável]
- **Por que importa:** [princípio ou heurística nº X e o efeito no usuário]
- **Correção:** [mudança concreta, com CSS/JSX quando fizer sentido]

## O que já está bom
Curto, só o que é específico e verdadeiro.
```

Priorize por impacto na tarefa do usuário: primeiro o que impede ou confunde a ação principal (CTA invisível, erro sem explicação, falta de feedback), depois hierarquia e espaçamento, por último polimento (alinhamentos finos, consistência de raio). Se o material enviado não permite julgar algo (por exemplo, não dá para ver estados de hover num print), diga isso em vez de supor.

Se faltar contexto que muda a recomendação (quem é o público, qual é a ação principal da tela), faça uma pergunta objetiva e continue com o que dá para avaliar sem ela.

## Complementos ao ebook

O ebook não cobre acessibilidade e tem alguns pontos fracos. Estes ajustes valem sobre o texto original:

- **Contraste numérico.** O ebook fala de contraste só de forma qualitativa. Como meta mínima (WCAG 2.x, nível AA): razão 4,5:1 para texto normal e 3:1 para texto grande (a partir de ~24px, ou ~19px em negrito) e para bordas/ícones de componentes. Teste com o inspetor de contraste do DevTools. Sobre texto em cima de foto, meça o pior trecho da imagem, não o médio.
- **Cor nunca é o único sinal.** Erro em vermelho precisa de texto e/ou ícone também; o ebook mostra o texto "Este campo não pode ficar vazio" junto da borda vermelha, que é o padrão correto.
- **Heurística 3 (controle e liberdade).** O ebook descreve como "liberdade de fazer o que quiser". Nielsen define de forma mais estreita: o usuário precisa de uma saída de emergência clara quando faz algo por engano, ou seja, desfazer, refazer, cancelar, voltar, fechar modal com Esc. Use essa definição ao revisar.
- **Psicologia das cores é tendência, não regra.** As associações (verde = natureza, azul = confiança) variam por cultura e setor, e a lista do ebook mistura sentimentos positivos e negativos para a mesma cor. Use como ponto de partida para conversar com o cliente, nunca como justificativa única de uma escolha.
- **Padrão Z.** O padrão F tem origem em estudos de rastreamento ocular; o Z é uma convenção de composição bem mais frouxa. Use o Z como sugestão para páginas esparsas (landing, anúncio), não como fato sobre o comportamento do usuário. Sobre o F, trate-o como o que acontece quando o texto não tem estrutura: o remédio é títulos, parágrafos curtos e destaques moderados.
- **Posição do CTA.** O ebook diz para preferir a parte superior; o diagrama do padrão Z põe o CTA no canto inferior direito. Resolva assim: um CTA visível sem rolar a página e, em páginas longas, repetido no fim das seções importantes.

## Quando ler cada referência

| Situação | Arquivo |
|---|---|
| Revisar fluxos, formulários, mensagens de erro, feedback, navegação | `references/heuristicas-nielsen.md` |
| Escolher ou criticar paleta, definir cor de CTA, cores de estado | `references/cores.md` |
| Definir espaçamento, grid, estrutura de leitura da página, desenhar botões de ação | `references/layout-e-cta.md` |
| Wireframe, design system, style guide, entrega a cliente | `references/wireframe-design-system.md` |
| Medir ou argumentar sobre usabilidade, testes com usuários | `references/usabilidade.md` |

Para pedidos grandes (por exemplo, "faça a landing page inteira"), leia `layout-e-cta.md` e `cores.md` antes de escrever código.

## Fonte

Conteúdo destilado e reorganizado a partir do ebook "UX Design para desenvolvedores frontend", de Iuri Silva, com os complementos marcados acima. É material de uso pessoal; não o redistribua como se fosse conteúdo original.
