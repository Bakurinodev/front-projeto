# As 10 heurísticas de Nielsen, aplicadas ao frontend

Uma heurística é uma regra geral para reduzir a carga cognitiva do usuário. Servem em dois momentos: durante o desenvolvimento (como base para um layout funcional) e depois de entregar uma funcionalidade (como lista de verificação para achar problemas).

Para cada item: a ideia, o teste rápido e o que fazer no código.

## Sumário
1. Visibilidade do status do sistema
2. Correspondência entre o sistema e o mundo real
3. Controle e liberdade do usuário
4. Consistência e padronização
5. Prevenção de erros
6. Reconhecimento em vez de memorização
7. Eficiência e flexibilidade de uso
8. Estética e design minimalista
9. Ajudar a reconhecer, diagnosticar e recuperar de erros
10. Ajuda e documentação

---

## 1. Visibilidade do status do sistema
**Ideia:** o sistema sempre mostra o que está acontecendo e qual o próximo passo. Exemplo do ebook: o player de playlist do YouTube mostra o que já carregou, em que ponto o vídeo está, quanto falta e qual item da fila está tocando.
**Teste:** depois de qualquer clique, o usuário sabe em menos de 1 segundo se algo aconteceu?
**No código:** estados de carregamento (spinner, skeleton, barra de progresso), botão que muda para "Salvando..." e fica desabilitado, toast de confirmação, item ativo destacado na navegação, indicador de etapa em fluxos longos (passo 2 de 4). Para leitores de tela, anuncie mudanças com `aria-live`.

## 2. Correspondência entre o sistema e o mundo real
**Ideia:** a interface fala a língua do usuário: palavras, ícones e conceitos que ele já conhece. Exemplo do ebook: um menu com o ícone do Instagram em vez de três linhas seria estranho.
**Teste:** um termo da tela só faz sentido para quem conhece o sistema por dentro?
**No código:** rótulos no vocabulário do usuário ("Meus pedidos", não "Listagem de ordens"), ícones convencionais (lupa = buscar, lixeira = excluir), ícone ambíguo sempre acompanhado de texto.

## 3. Controle e liberdade do usuário
**Ideia:** quem erra precisa de saída de emergência clara, sem passar por processo longo. (O ebook descreve de forma mais ampla; esta é a definição original de Nielsen. Exemplo do ebook: no Twitter dá para excluir um post, mas não editar, o que protege quem republicou.)
**Teste:** se o usuário clicar errado, consegue voltar sem custo?
**No código:** desfazer/refazer, botão "Cancelar" em todo fluxo, fechar modal com Esc e clique fora, "Voltar" que preserva o que já foi digitado, exclusão com opção de restaurar (lixeira ou toast com "Desfazer").

## 4. Consistência e padronização
**Ideia:** o mesmo elemento significa a mesma coisa em todo lugar, e segue convenções da plataforma. Exemplo do ebook: os ícones dos apps do Google compartilham as mesmas cores, então a marca é reconhecida de imediato.
**Teste:** duas telas com a mesma função usam o mesmo componente, texto e posição?
**No código:** biblioteca de componentes única, tokens de cor/espaço/raio, um só estilo de botão primário, logo no canto superior esquerdo levando à home, links com aparência de link.

## 5. Prevenção de erros
**Ideia:** melhor que boa mensagem de erro é uma interface em que o erro não acontece. Quando a ação é irreversível, peça confirmação antes.
**Teste:** onde, nesta tela, uma pessoa distraída causaria dano?
**No código:** `type="email"`, `inputmode="numeric"`, máscaras e `pattern` para evitar formato errado, validação enquanto digita (sem gritar antes da hora), botão destrutivo separado e com confirmação que repete o nome do que será apagado, valores padrão sensatos, desabilitar opções inválidas. Exemplo do ebook: a busca do Google sugere termos enquanto o usuário digita e oferece a grafia correta.

## 6. Reconhecimento em vez de memorização
**Ideia:** tudo que o usuário precisa deve estar visível ou fácil de achar; ele não deve ter que lembrar de uma tela para a outra. Exemplo do ebook: usuários procuram a barra de busca do navegador no topo, e um navegador que a colocasse embaixo quebraria o hábito.
**Teste:** o usuário precisa lembrar de informação de uma tela anterior para completar esta?
**No código:** `autocomplete` correto nos campos, itens recentes e favoritos, labels sempre visíveis (placeholder não substitui label, porque some ao digitar), menus em posições esperadas, preservar filtros ao navegar.

## 7. Eficiência e flexibilidade de uso
**Ideia:** novatos precisam de caminho guiado e detalhado; experientes precisam de atalhos. A interface deve atender os dois. Exemplo do ebook: no VS Code o iniciante usa cliques e, com o tempo, migra para comandos.
**Teste:** uma tarefa repetida tem versão rápida?
**No código:** atalhos de teclado documentados, paleta de comandos, ações em lote, preenchimento automático, personalização do que aparece, contagem de cliques até o objetivo (veja `usabilidade.md`).

## 8. Estética e design minimalista
**Ideia:** cada informação extra compete com a importante e aumenta o tempo de decisão e a chance de abandono. Exemplo do ebook: um login que pedisse CEP, RG e e-mail secundário.
**Teste:** se eu remover este elemento, alguém sentiria falta na tarefa principal?
**No código:** peça só o essencial no cadastro e o resto depois (perfil pós-login), divulgue detalhes progressivamente (accordion, "ver mais"), um destaque por seção, texto direto.

## 9. Ajudar a reconhecer, diagnosticar e recuperar de erros
**Ideia:** quando algo falha, a mensagem diz o que houve e como resolver, em linguagem simples, perto de onde o erro ocorreu. Não culpa nem intimida o usuário e não mostra código técnico.
**Teste:** a mensagem passaria no teste "minha avó entenderia o que fazer"?
**No código:** erro inline junto do campo, com borda + ícone + texto (não só cor); mensagem que ensina ("Informe sua senha" é melhor que um erro genérico; "A senha precisa ter 8 caracteres ou mais" é melhor ainda); resumo de erros no topo em formulários longos com links para os campos; foco movido para o primeiro campo inválido; nunca exibir stack trace ou `Error 500` cru.

## 10. Ajuda e documentação
**Ideia:** se as 9 anteriores forem bem aplicadas, o usuário raramente precisará de ajuda; mesmo assim, a central de ajuda deve ser fácil de achar. Exemplo do ebook: o menu "Help" do VS Code com atalhos, documentação e tutoriais.
**Teste:** em 10 segundos o usuário acha onde pedir ajuda?
**No código:** link de ajuda no cabeçalho ou rodapé fixo, tooltips curtos em campos complexos, busca na documentação, exemplos em contexto ("ex.: 12345-678" abaixo do campo de CEP).
