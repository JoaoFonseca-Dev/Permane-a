# Relatório de Adequação à LGPD — Site "Permaneça"

**Data da auditoria:** 29/10/2026
**O que foi auditado:** o arquivo `index.html` publicado (versão enxuta, 527.939 bytes), que traz HTML, CSS e JavaScript embutidos. A pasta original do projeto (código-fonte, `package.json`, histórico do git) **não estava mais disponível** neste ambiente. Por isso, o que depende dela aparece como "Não verificável".
**Tipo de trabalho:** somente leitura. Nada no site foi alterado. Este arquivo é a única coisa criada.

---

## 1. Resumo em 5 linhas

1. É um site simples, de uma página só, sem banco de dados e sem servidor próprio. Isso reduz muito o risco de vazamento.
2. Ele coleta nome, e-mail e WhatsApp pelo formulário de cadastro. Esses dados vão para uma conversa de WhatsApp com a autora.
3. Não encontrei chaves, senhas, rastreadores, pixels de anúncio nem cookies de publicidade.
4. O que falta é papel e transparência: não há política de privacidade, não há identificação de quem cuida dos dados e não há canal para o titular pedir seus direitos.
5. Há ainda um erro de informação: o formulário de depoimento diz que o texto foi "publicado na página", mas ele só fica no navegador de quem escreveu.

## 2. Nota geral

🟡 **Atenção.** A estrutura técnica é segura e enxuta, mas o site coleta dados pessoais (e pode atrair dados sensíveis, como saúde e fé) sem nenhum aviso de privacidade, e isso é uma falha clara da lei (Art. 9º).

## 3. Os 3 problemas mais urgentes

1. **Possível token do GitHub ainda ativo (item 1).** Um token de acesso ao repositório foi colado numa conversa anterior. Se ele não foi revogado, qualquer pessoa que o tenha poderia trocar o site por outro (por exemplo, uma página falsa de compra). *Não verificável por mim:* só você consegue ver isso no GitHub.
2. **Site sem política de privacidade e sem canal para o titular (itens 2 e 3).** Quem digita nome, e-mail e WhatsApp não sabe quem vai usar os dados, para quê, nem como pedir exclusão. Se nada mudar, a autora fica exposta a reclamação de qualquer pessoa na ANPD, e o site perde a confiança de quem lê.
3. **Dados de fé e saúde sem cuidado específico (item 5).** O site fala de câncer, Deus e igreja. Uma pessoa que se cadastra para "receber reflexões e encontros" revela, de forma indireta, sua religião. A lei trata esse tipo de dado como "sensível" e pede mais cuidado.

## 4. Tabela ranqueada de todos os itens

Escala: Gravidade e Probabilidade de 1 a 5. A ordem segue Gravidade × Probabilidade (G×P). Em empate, vem antes o item de menor esforço e menor risco.

| # | Prioridade | Problema (em linguagem simples) | Onde está | Por que é um problema | Ganho ao corrigir | Risco ao implementar | Esforço | Como corrigir (resumo) | Base legal |
|---|---|---|---|---|---|---|---|---|---|
| 1 | **P0** (G4×P2=8) | Token de acesso ao GitHub foi compartilhado numa conversa e pode estar ativo | Conta GitHub `JoaoFonseca-Dev` (fora do código) | Quem tiver o token pode alterar o site | Elimina o risco de o site ser sequestrado | Nenhum para o site | Baixo (minutos) | Revogar o token no GitHub e ativar verificação em duas etapas | Arts. 46 e 49 |
| 2 | **P1** (G3×P5=15) | Não existe política de privacidade | Rodapé e formulários (`index.html`, linhas ~493–510) | A lei exige informar finalidade, quem controla, com quem compartilha e quais os direitos | Cumpre a lei e passa confiança | Baixo | Baixo | Criar página "Política de Privacidade" em português simples, com data, e linkar no rodapé e perto dos formulários | Art. 9º, Art. 6º VI |
| 3 | **P1** (G3×P5=15) | Não há canal nem processo para o titular pedir acesso, correção ou exclusão | Todo o site (nenhum e-mail ou contato de privacidade) | Sem canal, não dá para atender o prazo de 15 dias | Atende direitos básicos e reduz reclamações | Baixo | Baixo | Publicar um e-mail ou WhatsApp de privacidade e definir quem responde e como apaga | Arts. 18, 19 e 41 §2 |
| 4 | **P1** (G3×P4=12) | O cadastro "para receber novidades" não explica o uso, não pede aceite claro e não deixa registro | Formulário `#signupForm` (linhas ~451–458) | O envio de novidades é marketing, que normalmente precisa de consentimento claro | Evita mensagens indesejadas e dá prova de aceite | Baixo | Baixo | Adicionar texto curto de finalidade e caixa **não pré-marcada** de aceite; explicar como sair da lista | Arts. 7º I e 8º |
| 5 | **P1** (G4×P3=12) | Conteúdo de fé e saúde pode gerar dado sensível sem cuidado | Textos do site; depoimentos; cadastro | Dado de religião e saúde exige base do Art. 11 e mais cautela | Reduz o risco de maior gravidade | Baixo | Baixo | Dizer na política que o cadastro pode revelar fé; pedir consentimento específico; orientar a não escrever dados de saúde nos depoimentos | Art. 5º II e Art. 11 |
| 6 | **P1** (G2×P5=10) | O formulário de depoimento diz "já está publicado nesta página", mas só salva no navegador de quem escreveu | `#depoimentoForm`; JS grava em `localStorage`, chave `permaneca_depoimentos` | Informação errada ao usuário e dado guardado no aparelho sem aviso | Honestidade com o usuário | Médio (muda o funcionamento) | Médio | Opção A: trocar o texto para "depoimento enviado à autora para aprovação" e mandar por WhatsApp. Opção B: criar armazenamento real com moderação | Art. 6º VI e Art. 9º |
| 7 | **P2** (G2×P5=10) | As fontes do Google são carregadas dos servidores do Google | `<link>` nas linhas 21–23 | O endereço IP do visitante vai ao Google (EUA) assim que a página abre, sem aviso | Menos terceiros e site mais rápido | Baixo | Baixo | Hospedar as fontes dentro do próprio site | Arts. 33 a 36 e 9º |
| 8 | **P2** (G3×P3=9) | Os 4 depoimentos reais (Sabrina, Sara, Beatriz, Dani) podem estar sem autorização por escrito | Seção `#depoimentos` | Nome e relato são dados pessoais | Prova de autorização | Baixo | Baixo | Guardar a mensagem em que cada pessoa autorizou o uso | Arts. 7º I e 8º |
| 9 | **P2** (G3×P3=9) | Terceiros que recebem dados não estão listados nem avaliados (WhatsApp/Meta, Netlify, GitHub, Google Fonts) | Todo o site | Há envio de dados ao exterior; precisa estar informado e coberto por contrato | Transparência | Baixo | Médio | Listar os terceiros na política e conferir os termos de cada um | Arts. 33–36 e 39 |
| 10 | **P2** (G3×P3=9) | Não há regra de quanto tempo guardar a lista de contatos | Conversas no WhatsApp da autora | Dado deve ser apagado quando acaba a finalidade | Evita acúmulo | Baixo | Baixo | Definir prazo (ex.: apagar quem pedir; revisar a lista a cada 12 meses) e escrever na política | Arts. 15 e 16 |
| 11 | **P2** (G4×P2=8) | Não há plano para vazamento (celular do WhatsApp, conta GitHub e Netlify sem proteção reforçada confirmada) | Fora do código | O prazo de aviso à ANPD é curto (3 dias úteis, dobro para pequeno porte que comprove) | Resposta rápida se algo ocorrer | Baixo | Baixo | Ativar duas etapas no WhatsApp, GitHub e Netlify; criar um registro simples de incidentes (guardar 5 anos) | Art. 48 e Res. CD/ANPD 15/2024 |
| 12 | **P2** (G2×P3=6) | Não há registro simples do que se faz com os dados | Fora do código | Boa prática exigida, em versão simplificada, até de pequenos | Organização | Baixo | Baixo | Usar o mapa de dados (seção 8 deste relatório) como registro inicial | Art. 37 |
| 13 | **P3** (G2×P2=4) | Sem cabeçalhos de segurança (CSP, referrer) | Configuração do Netlify | Reduz exposição a ataques de página | Defesa extra | Médio (CSP mal feita quebra o site) | Baixo | Criar `_headers` com `Referrer-Policy` e `X-Content-Type-Options`; testar antes | Art. 46 |
| 14 | **P3** (G2×P1=2) | Sem aviso sobre menores | Política | O site não é voltado a crianças, mas qualquer um pode digitar | Clareza | Baixo | Baixo | Incluir frase: "Este site é voltado a adultos" | Art. 14 e ECA Digital |
| 15 | **P3** (G1×P2=2) | `localStorage` não está citado | Política | Boa prática avisar | Transparência | Baixo | Baixo | Citar na política (some se o item 6 for resolvido) | Art. 9º |

## 5. Detalhe de cada item

### Item 1 — Token do GitHub (P0) · *Não verificável*
- **Evidência:** em conversa anterior, um token pessoal do GitHub (começa com `ghp_****`) foi colado no chat. Não aparece no `index.html` nem no README (conferi). Não sei se foi revogado.
- **Passo a passo (você faz):** GitHub → Settings → Developer settings → Personal access tokens → apagar o token. Ativar verificação em duas etapas em Settings → Password and authentication.
- **Como testar:** o token antigo some da lista.
- **Cuidados:** nenhum impacto no site, pois o Netlify usa a própria conexão.

### Item 2 — Política de privacidade · *Confirmado*
- **Evidência:** o rodapé (linhas ~493–510) tem só direitos autorais, Instagram e um aviso de que o livro não substitui acompanhamento médico. Não há link de privacidade em nenhum lugar.
- **Passo a passo:** escrever página com: quem é a controladora (nome da Tatiana Fonseca, ou CNPJ se tiver), quais dados coleta (nome, e-mail, WhatsApp, texto de depoimento), para quê, com quem compartilha (WhatsApp/Meta, hospedagem), por quanto tempo guarda, direitos e canal. Colocar data e versão. Linkar no rodapé e junto de cada formulário.
- **Como testar:** o link abre de qualquer tela e a política bate com o mapa de dados (seção 8).
- **Cuidados:** não copiar política pronta de outro site; ela precisa descrever o que este site realmente faz. Revisar com advogado.

### Item 3 — Canal e processo para direitos · *Confirmado (canal ausente)*
- **Evidência:** nenhum e-mail, formulário ou telefone de privacidade no site. O único contato é o WhatsApp comercial e o Instagram.
- **Passo a passo:** escolher um canal (e-mail dedicado ou WhatsApp) e escrevê-lo na política. Definir o roteiro: confirmar quem pede, responder em até 15 dias (30 dias pode valer para agente de pequeno porte, **a confirmar** em fonte oficial) e apagar o contato das conversas e das listas.
- **Observação:** a exigência de nomear um encarregado (DPO) é flexibilizada para agentes de pequeno porte pela Res. CD/ANPD 2/2022, **mas o canal de contato continua obrigatório**. Se a Tatiana atende como pessoa física ou MEI, não é preciso nomear, mas é preciso ter o canal. *Não verificável:* o enquadramento dela como pequeno porte.
- **Como testar:** peça a alguém para enviar um pedido de teste e veja se a resposta sai no prazo.

### Item 4 — Cadastro sem consentimento claro · *Confirmado*
- **Evidência:** o formulário tem nome (obrigatório), e-mail (opcional) e WhatsApp (obrigatório). O texto acima do formulário fala em "receber reflexões, novidades, encontros e conteúdos". Abaixo há só a frase "Ao enviar, você abrirá uma conversa no WhatsApp com seus dados preenchidos". Não há caixa de aceite. O JavaScript só monta a mensagem e abre `wa.me`; nada é guardado no site.
- **Ponto bom:** como a própria pessoa envia a mensagem, ela decide o que enviar. Isso reduz risco.
- **Ponto fraco:** a lista de novidades é marketing e o aceite não fica registrado. A mensagem enviada ("Quero continuar permanecendo") pode servir de prova, desde que a autora a guarde.
- **Passo a passo:** adicionar caixa desmarcada: "Aceito receber novidades da autora por WhatsApp/e-mail e li a Política de Privacidade". Bloquear o envio sem marcar. Incluir na mensagem do WhatsApp a frase "Aceito receber novidades". Explicar como sair ("responda SAIR").
- **Cuidados:** testar no celular, porque o WhatsApp abre numa nova aba.

### Item 5 — Dados sensíveis (fé e saúde) · *Provável*
- **Evidência:** o texto do site cita "câncer" (5 vezes), "Deus" (27), "igreja" e "fé". O cadastro e os depoimentos são campos abertos.
- **Por que importa:** a lei trata religião e saúde como dados sensíveis (Art. 5º II). Quem entra numa lista de reflexão espiritual pode estar revelando a própria fé; quem escreve um depoimento pode contar sua doença.
- **Passo a passo:** na política, avisar isso com clareza; no depoimento, incluir uma frase: "Evite informar dados de saúde de terceiros"; guardar o aceite específico.
- **Cuidados:** não exigir nenhum dado extra só por causa disso.

### Item 6 — Depoimento "publicado" que não publica · *Confirmado*
- **Evidência:** o JavaScript cria o cartão na página e guarda nome e texto em `localStorage` (chave `permaneca_depoimentos`), só no aparelho do visitante. Outra pessoa nunca verá o texto. Mesmo assim a tela diz "Seu depoimento já está publicado nesta página".
- **Por que importa:** é uma informação falsa ao usuário e um dado guardado sem aviso no aparelho dele.
- **Passo a passo:** o caminho mais simples e seguro é mudar o texto e o botão para "Enviar depoimento pela autora" e abrir o WhatsApp com o texto (como já é feito no cadastro). A autora decide o que publica e pede autorização. Se quiser publicação automática de verdade, é preciso um serviço externo com moderação (novo terceiro, novos riscos).
- **Como testar:** abrir o site em outro navegador e confirmar que o depoimento novo **não** aparece (comportamento atual) e, depois da correção, que o texto promete só o que acontece.
- **Cuidados:** mexe no comportamento do site; testar em Safari e Chrome.

### Item 7 — Google Fonts · *Confirmado*
- **Evidência:** linhas 21–23 carregam `fonts.googleapis.com` e `fonts.gstatic.com`.
- **Passo a passo:** baixar as fontes Cormorant Garamond e Montserrat, incluir no repositório e trocar o `<link>` por `@font-face` local.
- **Como testar:** na aba Rede do navegador, nenhuma chamada ao Google.
- **Cuidados:** conferir se as fontes ficaram iguais em celular e computador.

### Item 8 — Autorização dos depoentes · *Não verificável*
- **O que preciso de você:** prints das mensagens em que Sabrina, Sara, Beatriz e Dani autorizaram o uso do relato e do nome.

### Item 9 — Terceiros e transferência internacional · *Confirmado (lista); contratos Não verificáveis*
- **Evidência:** Google Fonts (Google), WhatsApp (Meta) via `wa.me`, Netlify, GitHub, Instagram (link). O JSON-LD usa só dados da autora. Nenhum provedor de IA, analytics, e-mail, pagamento ou chat de suporte.
- **Passo a passo:** listar os terceiros na política com a finalidade e o país; conferir os termos de dados (DPA) de Netlify e GitHub.
- **Cuidados:** a Res. CD/ANPD 19/2024 trata de cláusulas-padrão de transferência internacional. Para um site pequeno, o foco é informar e usar fornecedores com termos públicos.

### Item 10 — Retenção · *Não verificável*
- **O que preciso de você:** onde a lista de contatos fica guardada (só no WhatsApp? planilha? caderno?) e se há backup.

### Item 11 — Incidentes · *Não verificável*
- **Passo a passo:** ativar duas etapas no WhatsApp e no GitHub/Netlify; escrever um mini plano (quem avisar, em que ordem, registro com data e descrição, guardado por 5 anos).

### Item 12 — Registro das atividades · *Confirmado (ausente)*
- Usar a seção 8 deste relatório como ponto de partida.

### Item 13 — Cabeçalhos de segurança · *Não verificável em produção*
- Não fiz requisições ao site publicado (regra da tarefa). Pelo código, não há `meta referrer` nem política de segurança de conteúdo. Os links externos usam `rel="noopener"`, o que é bom.

### Item 14 — Menores · *Provável (baixo risco)*
- O conteúdo é para adultos e não é um serviço que atraia crianças de forma específica. Não há conta, perfil nem publicidade. O ECA Digital (Lei 15.211/2025) tem como alvo serviços direcionados a menores ou de "acesso provável" por eles; este site, pela natureza, tende a ficar fora. **A confirmar** com advogado.

### Item 15 — `localStorage` · *Confirmado*
- Só é usado para os depoimentos. Não há cookies, pixels, analytics nem Google Analytics. Por isso **não precisa de banner de cookies hoje**. Se algum dia adicionar analytics ou pixel, será preciso banner com opção de recusar.

## 6. O que já está bom

- Não há banco de dados, login, senha ou servidor próprio. Isso elimina quase todos os riscos de vazamento em massa.
- Nenhuma chave, token ou senha no código publicado (conferi o arquivo).
- Nenhum rastreador, pixel de anúncio, analytics ou cookie.
- Cadastro mínimo: e-mail é opcional.
- A pessoa envia a própria mensagem no WhatsApp, então decide o que compartilhar.
- Os textos dos depoimentos são inseridos como texto puro (`textContent`), o que evita injeção de código.
- Links externos com `rel="noopener"`.
- Não há decisão automática nem uso de IA com dados de usuários (Art. 20 não se aplica).
- O site tem um aviso claro de que o livro não substitui acompanhamento médico ou terapêutico.

## 7. O que não deu para verificar

- **Pasta do projeto, histórico do git e dependências** (`npm audit`): a pasta não estava neste ambiente. O bundle publicado não mostra bibliotecas externas.
- **Se o token do GitHub foi revogado** e se há verificação em duas etapas nas contas GitHub, Netlify e WhatsApp.
- **Cabeçalhos reais do site em produção** (não consultei o ambiente).
- **Quem é a controladora** (pessoa física, MEI ou empresa) e se se enquadra como agente de pequeno porte.
- **Onde a lista de contatos fica guardada** e por quanto tempo.
- **Autorizações dos depoentes.**
- **Termos de dados de Netlify, GitHub e Meta.**
- **Nota:** o domínio `permaneca-site.netlify.app` é gratuito do Netlify; um domínio próprio ajudaria na confiança, mas não é exigência da LGPD.

## 8. Mapa de dados

| Dado | Onde é coletado | Onde fica guardado | Para que é usado | Com quem é compartilhado | Por quanto tempo | Sensível? |
|---|---|---|---|---|---|---|
| Nome | `#sName` (cadastro) | Mensagem no WhatsApp da autora; nada no site | Contato e envio de novidades | WhatsApp/Meta | Sem prazo definido | Não (mas pode indicar fé pelo contexto) |
| E-mail (opcional) | `#sEmail` | Mensagem no WhatsApp | Contato | WhatsApp/Meta | Sem prazo definido | Não |
| Telefone/WhatsApp | `#sWhats` | Mensagem no WhatsApp | Contato | WhatsApp/Meta | Sem prazo definido | Não |
| Nome e texto do depoimento | `#dName`, `#dText` | `localStorage` do navegador do visitante, chave `permaneca_depoimentos` | Mostrar o cartão na própria tela do visitante | Ninguém | Até o visitante limpar o navegador | **Pode ser** (fé, saúde) |
| Endereço IP e dados técnicos | Ao abrir a página | Logs do Netlify e do Google Fonts | Entregar o site e as fontes | Netlify, Google (EUA) | Definido pelos terceiros | Não |
| Nome e telefone da autora | Rodapé, links `wa.me` | Página pública | Venda e contato | Público | Enquanto o site existir | Não |
| Nome e relato de 4 depoentes | Seção de depoimentos | HTML publicado | Confiança na compra | Público | Enquanto o site existir | **Pode ser** (fé, saúde) |

## 9. Anexo — O que a lei exige hoje

Consulta feita em **29/10/2026**. Os sites oficiais `planalto.gov.br` e `gov.br/anpd` **não estavam acessíveis neste ambiente**; por isso, os pontos abaixo foram conferidos em fontes secundárias (escritórios e imprensa especializada) e estão marcados como **"a confirmar em fonte oficial"**.

**Pontos conferidos (fonte secundária):**
- **Lei nº 15.352/2026:** sancionada em 25/02/2026, transforma a ANPD em **Agência Nacional de Proteção de Dados**, agência reguladora vinculada ao Ministério da Justiça. A MP nº 1.317/2025 foi convertida nela. Fonte: [Teletime](https://teletime.com.br/26/02/2026/lei-que-torna-anpd-agencia-e-fixa-vigencia-do-eca-digital-e-sancionada/). *A confirmar em fonte oficial.*
- **ECA Digital (Lei nº 15.211/2025):** vigente desde **17/03/2026**; aplica-se a serviços digitais voltados a crianças e adolescentes ou de "acesso provável" por eles; proíbe só a autodeclaração de idade; multa de até 10% do faturamento no Brasil. Sanções administrativas previstas a partir de nov/2026. Fonte: [Mayer Brown](https://www.mayerbrown.com/pt/insights/publications/2026/04/enforcement-of-brazils-eca-digital-introduces-new-obligations-for-companies). *A confirmar em fonte oficial.*
- **Res. CD/ANPD nº 15/2024 (incidentes):** comunicação à ANPD e aos titulares em **3 dias úteis** do conhecimento; complementação em 20 dias úteis; registro de todos os incidentes por, no mínimo, **5 anos**; prazo em dobro para agente de pequeno porte que comprove. Fonte: [Cescon Barrieu](https://cesconbarrieu.com.br/anpd-aprova-o-regulamento-de-comunicacao-de-incidente-de-seguranca/). *A confirmar em fonte oficial.*
- **Res. CD/ANPD nº 2/2022 (pequeno porte):** dispensa a nomeação formal de encarregado (mas exige canal de contato), simplifica registro de operações e dobra prazos. **Não flexibiliza** princípios, base legal, direitos do titular, segurança, nem as regras para crianças. Não vale para tratamento de alto risco (por exemplo, em larga escala com dados sensíveis). Fonte: [Confidata](https://confidata.com.br/blog/lgpd-pequenas-empresas-resolucao-pequeno-porte). *A confirmar em fonte oficial.*
- **Res. CD/ANPD nº 19/2024 (transferência internacional, cláusulas-padrão):** prazo para adequar contratos terminou em 23/08/2025. Fonte: [Mattos Filho](https://www.mattosfilho.com.br/unico/clausulas-padrao-anpd/). *A confirmar em fonte oficial.*
- **Res. CD/ANPD nº 18/2024 (encarregado):** não consegui confirmar o conteúdo detalhado. **A confirmar.**
- **Multa (Art. 52 e Res. CD/ANPD nº 4/2023):** multa simples de até 2% do faturamento no Brasil no último exercício, limitada a R$ 50 milhões por infração, além de advertência, publicização, bloqueio, eliminação e suspensão. Veio do texto da lei que conheço, **não conferido em fonte oficial nesta sessão. A confirmar.**
- **Artigos da LGPD citados** (5º, 6º, 7º, 8º, 9º, 11, 14, 15, 16, 18, 19, 20, 33–36, 37–39, 41, 46–49, 52): vêm do conhecimento do auditor sobre o texto da Lei nº 13.709/2018. **Não consegui abrir o Planalto**; conferir em https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm.
- **Novidades dos últimos 12 meses:** a imprensa especializada cita revisão do regulamento de fiscalização e do processo regulatório da ANPD em 2026. Não li o texto dos documentos. **A confirmar.**

## 10. Aviso

Este relatório é uma avaliação técnica e não substitui orientação jurídica. Textos como política de privacidade e termos devem passar por revisão de um profissional de direito.

---

## 11. Atualização de 29/10/2026 — correções feitas

Autorizadas pela pessoa responsável ("tudo que tem de erro"). Teste automático: sem erros, sem pedidos externos, sem rolagem lateral, formulários só abrem o WhatsApp depois do aceite.

| Item | Situação |
|---|---|
| 1 Token do GitHub | **Pendente com você**: revogar no GitHub e ativar duas etapas |
| 2 Política de privacidade | Feito (seção `#privacidade`, link no rodapé e nos formulários) |
| 3 Canal de privacidade | Feito (botão de WhatsApp na política). Sem e-mail dedicado |
| 4 Aceite no cadastro | Feito (caixa não pré-marcada, obrigatória, vai na mensagem) |
| 5 Dados sensíveis | Feito (aviso na política e no depoimento) |
| 6 Depoimento "publicado" | Feito (agora é enviado à autora pelo WhatsApp; `localStorage` deixou de ser usado e a chave antiga é apagada) |
| 7 Google Fonts | Feito (fontes dentro do arquivo) |
| 8 Autorização dos depoentes | **Pendente com você**: guardar as mensagens de autorização |
| 9 Terceiros | Feito na política |
| 10 Retenção | Texto na política (12 meses sem conversa = revisão e exclusão); **confirme se você aceita esse prazo** |
| 11 Plano de incidentes | **Pendente com você**: duas etapas no WhatsApp, GitHub e Netlify; registro simples |
| 12 Registro de atividades | Use a seção 8 |
| 13 Cabeçalhos | Arquivo `_headers` criado (precisa subir ao repositório); `meta referrer` já incluído |
| 14 Menores | Feito na política |
| 15 `localStorage` | Resolvido junto com o item 6 |
