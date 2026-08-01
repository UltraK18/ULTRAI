# ULTRAI

Um aplicativo de desktop para Windows voltado a trabalho com IA que não para. Quatro modos em uma única janela — conversar, construir em uma pasta de projeto real, projetar em uma tela (canvas), gerar imagens e vídeos — além de agendamento, execuções multiagente e o celular como uma segunda tela.

[English](./README.md) | [中文(简体)](./README.zh.md) | [中文(繁體)](./README.zht.md) | [한국어](./README.ko.md) | [Deutsch](./README.de.md) | [Español](./README.es.md) | [Français](./README.fr.md) | [Dansk](./README.da.md) | [日本語](./README.ja.md) | [Polski](./README.pl.md) | [Русский](./README.ru.md) | [العربية](./README.ar.md) | [Norsk](./README.no.md) | [Português (Brasil)](./README.br.md) | [ไทย](./README.th.md) | [Bosanski](./README.bs.md) | [Türkçe](./README.tr.md)

[![Latest Release](https://img.shields.io/github/v/release/UltraK18/ULTRAI?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/UltraK18/ULTRAI/total?style=flat-square)](https://github.com/UltraK18/ULTRAI/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20x64-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Freeware-green?style=flat-square)

> Este repositório é apenas para **distribuição de releases**. O código-fonte não é publicado aqui.

---

## Download

Windows 10 / 11 (x64). Requer o runtime do WebView2, que já vem presente na maioria das instalações do Windows.

**[Baixe a versão mais recente](https://github.com/UltraK18/ULTRAI/releases/latest)** — obtenha o `ULTRAI_x.y.z_x64_en-US.msi` e execute-o.

Depois disso, o aplicativo cuida de si mesmo: verifica novas versões ao iniciar e periodicamente, avisa quando uma está disponível e a instala no lugar.

## Quatro modos, uma janela

Cada modo é uma tela construída para um propósito específico, com suas próprias ferramentas e seus próprios agentes — mas é um único aplicativo, um único conjunto de configurações, um único lugar onde seu histórico vive.

| Modo | A tela | O que você faz lá |
| :--- | :--- | :--- |
| **Chat** | Conversa | Qualquer provedor e modelo, nível de esforço de raciocínio por mensagem, pesquisa aprofundada com citações, arquivos e imagens de entrada |
| **Code** | Uma pasta de projeto real | Árvore de arquivos, diffs em um painel de revisão, um terminal ao lado do chat, confirmações de permissão antes que qualquer coisa toque o disco |
| **Design** | Tela viva (canvas) + agente designer | As telas são renderizadas ao lado do chat conforme são construídas; o trabalho finalizado é repassado ao Code como arquivos reais |
| **Studio** | Tela livre (canvas) + chat | Gere imagens e vídeos, posicione-os e reorganize-os, solte seus próprios arquivos e continue iterando sobre o que já está lá |

Trocar de modo não reinicia nada — cada modo mantém suas próprias conversas, e a barra lateral mostra as que pertencem ao lugar onde você está.

## A interface é o ponto principal

A maioria das ferramentas nesse espaço é um terminal ou uma página web dentro de um wrapper. O ULTRAI é um aplicativo de desktop que foi projetado, não montado.

- **Vidro que é realmente vidro** — as superfícies flutuantes rodam um pequeno motor de renderização, não um filtro de desfoque. Ele calcula um mapa de normais para a borda (bezel) e desenha reflexos especulares a partir dele, além de deslocar o que está atrás da superfície para que as bordas refratem. Controles como o toggle e o slider vão além e resolvem a refração de Snell com um índice de refração e uma espessura, de modo que o indicador (thumb) curva a trilha sob ele. Um desfoque em CSS não consegue fazer isso, e a diferença aparece em cada borda.
- **Cantos squircle** — os painéis usam uma superelipse, não um arco circular, de modo que a curva entra na borda reta sem o ponto achatado que se obtém com `border-radius`.
- **Dois temas, ambos deliberados** — os modos claro e escuro são construídos sobre uma única paleta de tom concreto com uma leve tonalidade fria, ajustada para que nada seja ofuscante em nenhum dos extremos. Cada superfície é um token, então o aplicativo inteiro se move junto, em vez de derivar tela por tela.
- **Contenção proposital** — nenhum emoji em qualquer lugar do produto, nenhum ponto de exclamação, nenhum tom de torcida. Cada painel carrega uma única superfície; a separação vem de luz de contorno e sombra, não de caixas desenhadas dentro de caixas.
- **Janela sem costuras** — uma barra de título de 32px na métrica do Windows 11 que compartilha o plano de fundo do aplicativo, de modo que o chrome não se lê como uma faixa separada acima do conteúdo.
- **O mobile é um layout diferente, não um menor** — bottom sheets, controles de largura total e uma área de toque dimensionada para o dedo, decididos pelo dispositivo, não pela largura da janela.

## Geração, com modelos reais

O Studio não é um único endpoint de imagem. Ele escolhe a partir de um catálogo a cada tarefa e informa qual modelo usou e por quê.

- **Vídeo** — Veo 3.1 e Veo 3.0 (além de suas variantes fast), Sora 2 e Sora 2 Pro, Grok Imagine Video, Gemini Omni Flash
- **Imagem** — GPT Image 2 e 1.5, Gemini 3 Pro Image, Gemini 3.1 Flash Image (e Flash Lite), Grok Imagine Image
- **Vídeo na entrada, vídeo na saída** — forneça um clipe existente como entrada, não apenas um prompt
- **Ele verifica o próprio trabalho** — extrai quadros do que gerou, analisa-os e decide se deve tentar novamente
- **Duração, proporção e qualidade são suas escolhas** — pediu 30 segundos, 30 segundos é o que é construído, na forma que você pediu

Quais modelos você consegue alcançar depende das contas de provedor que você conecta (Vertex AI, OpenAI, xAI).

## Modo ULTRA — muitos agentes, uma única tarefa

Para trabalhos grandes demais para um único contexto. O ULTRA divide a tarefa em subtarefas, executa-as entre agentes fase por fase, e faz com que os resultados sejam **verificados de forma independente antes de serem mesclados** — um crítico e verificações adversariais, não o mesmo agente se autoavaliando. Você acompanha a execução e pode intervir a qualquer momento. Modelo e nível de esforço de raciocínio são definidos por função, de modo que um worker barato e um verificador caro podem ser propositalmente provedores diferentes.

## Ele cumpre seus compromissos

Diga "todo dia útil às 9" ou "daqui a duas horas" e isso se torna uma tarefa real, não uma anotação. Quando ela dispara, a tarefa chega como uma mensagem naquela conversa e a IA começa a trabalhar nela.

- Um calendário e uma lista mostram tudo o que está registrado; a próxima execução fica na parte inferior da barra lateral
- Estava fechado quando algo venceu? O aplicativo descobre o que perdeu e junta tudo em uma única execução de recuperação
- `/loop` repete uma tarefa pelo número de rodadas que você definir

## Metas que a IA não pode declarar concluídas

Defina uma meta para uma conversa e uma avaliação independente controla a conclusão. O agente que executa o trabalho não tem o poder de decidir que terminou.

## Pesquisa que se aprofunda, e perguntas antes do trabalho

**Deep research** planeja os ângulos, depois pesquisa e lê em paralelo entre sub-agentes e cita o que encontrou. A busca do dia a dia também é incomumente rigorosa: o modelo é instruído a pesquisar em vez de supor, a usar a data de hoje em vez de um ano herdado do treinamento, e a verificar afirmações no tempo presente antes de responder. As descobertas são apresentadas de forma equilibrada, com fontes citadas no próprio texto.

**Deep interview** — quando um pedido está subespecificado, transforma a conversa em uma entrevista estruturada e define exatamente o que você quer antes que qualquer trabalho comece.

## Trabalho que roda enquanto você faz outra coisa

Tarefas longas não mantêm a janela refém.

- **Execuções em segundo plano** — entregue uma tarefa e ela roda isolada, como um fork da conversa ou como um sub-agente, e pode pedir mais permissão no meio da execução se esbarrar em algum obstáculo.
- **Um monitor ao vivo** — uma barra na parte inferior mostra tudo o que está em andamento de uma vez: suas próprias tarefas em segundo plano, as iniciadas em outro lugar, chamadas de sub-agente em execução, execuções do ULTRA, e qualquer comando de shell que esteja rodando há um tempo. Clique para acompanhar qualquer uma delas.
- **Bifurque (fork) uma conversa** — ramifique a partir de qualquer ponto para tentar algo sem perder o original, e pule entre ramificações a partir do índice de mensagens.

## Transferência entre modos

O trabalho não fica preso no modo em que começou. O Design entrega telas finalizadas ao Code como arquivos reais em disco. As sessões do Code trocam perguntas e resultados entre si. O Studio coloca o que um agente produziu diretamente na tela. Cada transferência move arquivos reais ou mensagens reais, não um bloco de texto copiado.

## Um espaço de trabalho que a IA pode usar sem tocar nos seus arquivos

O modo Chat tem seu próprio espaço de rascunho em disco. A IA pode escrever, ler, executar e revisar coisas ali livremente — rascunhos, scripts, arquivos intermediários — sem pedir sua permissão a cada passo e sem acessar suas pastas. Você nunca precisa pensar em onde isso fica; você simplesmente recebe o resultado, e seus próprios diretórios permanecem intocados a menos que você os aponte.

## Sessões que conversam entre si

No modo Code, uma sessão pode repassar uma pergunta ou um resultado para outra — a que está trabalhando no backend pode perguntar à que conhece o frontend. As mensagens chegam como uma mensagem real na outra conversa. Você abre o canal; nada se conecta sozinho.

## Seu celular é uma segunda tela

Ative o servidor e abra o ULTRAI a partir do navegador do celular na mesma rede. O layout mobile é construído para toque — bottom sheets e controles de largura total — e não é um desktop encolhido. Conversas, modelos e configurações são compartilhados, então você continua exatamente de onde parou.

## Faça do seu jeito

Tudo abaixo é um arquivo simples no seu disco, que você pode ler, editar e versionar.

- **Agentes** — `~/.ultrai/agents/*.md`. O frontmatter decide tudo: em quais modos o agente aparece, quais ferramentas pode usar, quais seções do prompt recebe, quais recursos (pesquisa, metas, entrevista) tem permissão de usar. Edite pelas Configurações, e os agentes nativos podem ser restaurados ao original a qualquer momento.
- **Skills** — `~/.ultrai/skills/*/SKILL.md`. Instruções reutilizáveis que o modelo pode incorporar, ou que você pode invocar como um comando de barra. Ative ou desative cada uma individualmente.
- **Módulos de prompt** — o system prompt é montado a partir de um catálogo, e o frontmatter de cada agente escolhe quais seções recebe. Não declare nada e o prompt do agente fica byte a byte idêntico ao padrão; opte por incluir módulos para mudar como ele pensa. Cada modo vem com seu próprio prompt, construído para aquele tipo de trabalho, em vez de um único prompt forçado a servir para tudo.
- **Servidores MCP** — declarados em `ultrai.jsonc`. Locais ou remotos, com autenticação onde necessário, ativáveis individualmente por servidor.
- **Memória** — mantida em três categorias (sobre você, tópicos, áreas), com resumos injetados e detalhes buscados sob demanda, além de uma limpeza periódica que mescla duplicatas e contradições. Disponível apenas no modo Chat, e você pode ver e excluir cada entrada pelas Configurações.
- **Provedores** — Anthropic, OpenAI, Google, Google Vertex, xAI, OpenRouter e endpoints personalizados, com suas próprias chaves.

## Seus dados ficam no seu PC

Conversas e configurações são armazenadas **apenas na sua máquina**. Não existe um servidor ULTRAI — suas conversas vão apenas para o provedor de IA que você mesmo conectou, usando sua própria chave.

Nada é coletado, e não há telemetria.

## Início rápido

1. **Conecte um provedor** — adicione sua chave de API em Configurações → Provedores.
2. **Escolha um modelo** — modelo e nível de esforço de raciocínio ficam à direita da barra de entrada.
3. **Escolha um modo** — as abas na parte superior da barra lateral.
4. **Comece a trabalhar** — abra uma pasta no modo Code; nos outros modos, basta começar a conversar.
5. **Delegue algo** — diga "resuma meu dia todas as noites" e o aplicativo cuidará disso sozinho.

## Stack técnica

Um aplicativo nativo para Windows construído sobre o Tauri 2. A interface é feita em SolidJS; o backend roda como um único binário empacotado junto com o aplicativo.

## Feedback

Bugs e pedidos de recursos vão para [Issues](https://github.com/UltraK18/ULTRAI/issues).

## Licença

O ULTRAI é freeware. Gratuito para uso pessoal e comercial. O código-fonte não está disponível publicamente.

O ULTRAI começou como um fork do [opencode](https://github.com/sst/opencode) e foi reconstruído bem além dele, mas ainda inclui código do opencode, que é licenciado sob MIT — Copyright (c) 2025 opencode. A licença MIT está citada na íntegra nos avisos incluídos com o aplicativo.
