# Layout, padrões de leitura e CTA

## Grid de 8 pontos

**Regra:** tamanhos, margens, paddings e distâncias entre elementos são múltiplos de 8 (8, 16, 24, 32, 40, 48...). Isso dá consistência, facilita o ajuste entre dispositivos (muitas resoluções comuns são divisíveis por 8) e elimina a deliberação sobre "quantos pixels?" a cada elemento.

**Dois níveis de distância.** Entre elementos do mesmo conteúdo use uma distância base; para separar conteúdos diferentes use o dobro. Exemplo do ebook (tela de login), de cima para baixo:

| Relação | Distância |
|---|---|
| título "Bem-vindo!" até o primeiro campo | 24px |
| label/borda interna do campo | 8px |
| campo e-mail até campo senha | 16px |
| último campo até o botão "Entrar na conta" | 32px |

O padrão por trás: quanto mais "separado" conceitualmente, maior o espaço. Quando o espaço dentro do grupo é menor que o espaço entre grupos, a proximidade comunica a estrutura sem precisar de linhas ou caixas.

**No código:** tokens `--space-*` do SKILL.md. Alturas de controles também seguem a escala (botão 40 ou 48px, input 40 ou 48px). Em Tailwind, prefira `p-2/4/6/8`, `gap-2/4/6/8`, `h-10/12`.

## Padrões de leitura (cultura ocidental, esquerda para direita)

Estes padrões indicam onde ficam os "pontos nobres" da página, isto é, onde colocar a informação mais importante. Antes de adotar um, entenda como os seus usuários realmente leem a página.

### Padrão F (páginas com muito texto: artigos, blogs, resultados de busca)
O leitor percorre o topo, desce pela lateral esquerda procurando palavras-chave e só lê linhas inteiras quando algo interessa, formando um "F".
**Faça:** títulos e subtítulos alinhados à esquerda, primeiras palavras de cada parágrafo carregando a ideia, listas, negrito/cor/itálico com moderação nos pontos cruciais (se tudo destaca, nada destaca).

### Padrão Z (páginas esparsas: landing pages, anúncios, home)
O olhar vai do canto superior esquerdo ao direito, desce na diagonal até o canto inferior esquerdo e atravessa para o inferior direito.
**Faça:** logo no ponto 1, navegação/CTA secundário no ponto 2, imagem ou proposta de valor na diagonal, CTA principal no ponto 4. Nota: o Z é convenção de composição, não achado de pesquisa tão sólido quanto o F; trate como sugestão (veja "Complementos" no SKILL.md).

Em ambos, uma boa hierarquia visual reduz o esforço cognitivo e leva o usuário a concluir a tarefa.

## CTA (Call to Action)

Um CTA é qualquer elemento que convida o usuário a agir: botão, frase, imagem, link. A ação pode ser clicar, comprar, assinar newsletter, preencher formulário.

Quatro regras do ebook, mais o que fazer no código:

1. **Frase curta.** O usuário precisa entender o que acontece ao clicar. "Inscreva-se" vence "Inscreva-se para receber novidades". Verbo no imperativo + resultado ("Criar conta", "Copiar frase", "Baixar guia").
2. **Cor viva.** O CTA tem que ser mais atrativo que os botões comuns. Escolha uma cor chamativa **da sua paleta**; um CTA em versão clara/desbotada, como no contraexemplo do ebook, some. Botões secundários usam estilo contornado ou neutro.
3. **Localização óbvia.** Num lugar que o usuário encontre sem procurar, de preferência visível sem rolar. Em páginas longas, repita o CTA ao fim das seções importantes.
4. **Espaçamento interno generoso.** Mais padding dá presença. Um bom ponto de partida é altura 48px e padding lateral 24 a 32px; contraexemplo do ebook: botão apertado e pequeno colado no texto.

Complementos práticos (convenção de mercado, não do ebook): uma ação primária por contexto; alvo de toque de pelo menos 44px no mobile; estado de foco visível; estado de carregando ao clicar.

### Exemplo de botão primário

```css
.btn-primary {
  background: var(--color-primary);
  color: var(--color-on-primary);   /* contraste >= 4.5:1 com o fundo */
  min-height: 48px;
  padding: 0 var(--space-4);
  border: 0;
  border-radius: 8px;
  font: 600 16px/1 var(--font-sans);
  cursor: pointer;
}
.btn-primary:focus-visible { outline: 3px solid var(--color-focus); outline-offset: 2px; }
.btn-primary[disabled] { opacity: .5; cursor: not-allowed; }
```
