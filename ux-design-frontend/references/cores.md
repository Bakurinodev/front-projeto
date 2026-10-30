# Cores em interfaces

## Por que a paleta vem primeiro
A paleta carrega a personalidade da marca e influencia se a pessoa confia no produto ou segue adiante. Por isso o ebook insiste: **escolha as cores logo no início do projeto**, para que as decisões seguintes (botões, estados, ilustrações) sejam coerentes com a identidade. Uma paleta bem definida também ajuda na legibilidade, destaca CTAs e estimula interação sem parecer agressiva.

## Processo de escolha
1. Descreva a marca em 3 a 5 adjetivos (confiável, jovem, premium, acolhedora...).
2. Escolha **uma cor primária** que combine com esses adjetivos (veja as associações abaixo como ponto de partida).
3. Acrescente neutros (texto, bordas, fundos) e **cores de estado**: sucesso, erro, alerta, informação.
4. Defina a cor do CTA dentro da paleta, com destaque em relação aos botões comuns.
5. Teste contraste de todos os pares texto/fundo (meta AA: 4,5:1 para texto normal, 3:1 para texto grande e ícones/bordas).
6. Registre tudo como tokens (`--color-primary`, `--color-danger`...) e use só eles no CSS.

## Saturação e pureza
O ebook compara botões em tons equilibrados com botões em verde, vermelho, amarelo e azul puros e saturados, e os últimos parecem amadores. Prefira tons levemente dessaturados. Em botão amarelo, use texto escuro (texto branco sobre amarelo falha no contraste, e o próprio ebook mostra isso como exemplo ruim).

## Associações por cor (ponto de partida, não regra)
Estas associações vêm do ebook e variam por cultura e contexto. Use para iniciar a conversa com o cliente e para evitar escolhas que contradizem a mensagem da marca.

| Cor | Associada a | Cuidado | Exemplo citado no ebook |
|---|---|---|---|
| Verde | natureza, dinheiro, saúde, calma, renovação | serve bem para sucesso/confirmar | John Deere |
| Vermelho | paixão, energia, fome, urgência, perigo | em excesso gera raiva/medo; dose controlada | McDonald's |
| Laranja | entusiasmo, criatividade, amizade, aventura | intensa, porém menos agressiva que o vermelho | Nickelodeon |
| Amarelo | otimismo, felicidade, sol, esperança | também lembra alerta e perigo; texto escuro por cima | Renault |
| Rosa | delicadeza, leveza, brincadeira, romantismo | forte associação com público infantil/feminino | Barbie |
| Azul | confiança, estabilidade, segurança, tecnologia | muito comum em tecnologia, pode passar despercebida | Dell, HP, Skype |
| Roxo | criatividade, sabedoria, realeza, mistério | também lembra luto e arrogância | Twitch, Vivo |
| Marrom | conforto, terra, rústico, simplicidade | | Cacau Show |
| Branco | paz, limpeza, simplicidade, precisão | | Adidas |
| Preto | sofisticação, luxo, poder, elegância | também medo e tristeza | Chanel, Gucci |
| Cinza | equilíbrio, neutralidade | ideal para cabeçalhos, gráficos e fundos que não devem roubar atenção; em excesso lembra monotonia | Apple |

## Convenções de estado (úteis em UI, independentes da marca)
- Sucesso: verde. Erro/destrutivo: vermelho. Alerta: amarelo/âmbar. Informação: azul.
- Esses significados são tão convencionais que mudar quebra a heurística 2 (correspondência com o mundo real). Mantenha, mas nunca use só a cor: junte ícone e texto.
