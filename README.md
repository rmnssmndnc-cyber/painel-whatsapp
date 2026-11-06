# Painel WhatsApp

Aplicativo local para Windows com contatos, mensagens livres, imagens e PDFs.

## Versão publicada

[Baixar versão 2.4.7](pacotes/Painel_WhatsApp_2_4_7.zip)

2.4.7: extrai nomes apenas do título do participante, preserva nomes longos e usa o índice da linha na deduplicação para tolerar mudanças de posição. Não exclui nomes de uma letra nem une homônimos. 72 testes locais passaram; instalação 2.4.6 para 2.4.7 preservou os dados na cópia de teste. Consulta de telefones nos dados individuais ainda não implementada. Validação desta versão no WhatsApp real pendente.

2.4.6: reconhece role=dialog com aria-label Pesquisar membros. Abra Ver tudo antes de selecionar a lista e mantenha a pesquisa vazia. Percorre a rolagem interna e ignora separadores por letras. Validado com o HTML recebido (geometria simulada) e lista virtualizada; teste real no Windows ainda pendente. HTML privado não incluído. Telefones ausentes na lista continuam em branco.

2.4.5: procura o ancestral rolável dentro do painel de membros, inclusive acima de pane-side. Ignora caixas sem intervalo de rolagem. Detecta rolagem travada e informa resultado parcial quando termina antes da contagem declarada. Teste DOM simula 240 membros virtualizados e verifica que todos são percorridos. Telefones não exibidos na lista continuam sem preenchimento; consulta automática aos perfis não foi implementada. Validação no WhatsApp real ainda pendente.

2.4.4: reconhece o contêiner com aria-label Lista de membros dentro de pane-side, sem confundi-lo com conversas. Erros de seleção permanecem na mensagem final após o prazo. O HTML fornecido pelo operador reproduziu a rejeição na 2.4.3 e a seleção/leitura de suas 10 linhas na 2.4.4, com geometria simulada em jsdom. Esse arquivo privado não está no pacote. A rolagem completa no WhatsApp real ainda precisa ser confirmada.

2.4.3: reconhece linhas de participantes dentro de #main quando Dados do grupo e a contagem de membros estão presentes no mesmo painel. Rejeita mensagens, conversas e dados de contato. Testes DOM com jsdom usam a estrutura de listitem/cell-frame-title fornecida pelo operador; geometria simulada. Não houve leitura real do grupo. Telefones ausentes na lista continuam em branco.

2.4.2: o modo de seleção deixa os cliques de navegação passarem. Só intercepta uma linha reconhecida após validar o contêiner. A faixa de instrução fica na parte inferior para não cobrir o cabeçalho. Teste de eventos JavaScript reproduz navegação e seleção, sem acesso ao WhatsApp real.

A versão 2.4.1 repete a substituição de JSON quando há bloqueios temporários no Windows, preservando o arquivo anterior. Também evita regravar estados idênticos da leitura de grupos. Bloqueios persistentes continuam sendo informados ao operador.

## Exportar grupo — experimental

Na aba Contatos, clique em **Exportar grupo**. Informe o nome do grupo e, opcionalmente, o total de participantes. Clique em **1. Abrir WhatsApp**, abra o grupo e a lista completa de participantes. Volte ao painel e clique em **2. Selecionar lista**. No navegador, clique em uma linha de participante. O programa marca a lista e tenta percorrê-la sem abrir conversas privadas ou enviar mensagens.

Revise a prévia e use **3. Salvar planilha**. O arquivo XLSX tem Nome, Telefone e Observação, além dos dados da coleta. Telefones repetidos são agrupados. Telefones que não aparecem ou não têm DDI reconhecível ficam em branco; nomes são os exibidos no WhatsApp, não identidades verificadas. Homônimos sem telefone precisam de conferência.

Alcançar o fim da lista visível não prova que todos os participantes foram exibidos. Compare a prévia com o total do grupo. Mudanças na interface podem impedir a seleção ou a leitura. A versão é experimental e ainda precisa de teste na interface real do WhatsApp do usuário. Os resultados ficam em dados/exportacoes_grupos e não são enviados à IA ou adicionados à campanha.

A criação de planilhas ocorre localmente, usando somente a biblioteca padrão do Python. A função compartilha o bloqueio de execução com os envios, para não disputar a sessão.

A sequência de segunda mensagem após resposta continua em desenvolvimento e não faz parte desta versão.

## Assistente ChatGPT — experimental

Abra **Assistente IA → Preparar conexão** uma vez. Isso instala PyJWT 2.10.1 e dependências de criptografia no Python do painel. Depois clique em **Continuar com ChatGPT** e autorize no navegador oficial. O login usa Authorization Code com PKCE, state, nonce e validação da assinatura do ID token. O aplicativo usa o fluxo oficial de registro dinâmico para aplicações locais; disponibilidade depende da conta e da autorização. Não usa chave de API e não há fallback para cobrança por API.

Escolha um modelo retornado pela sua conta:

- **Escrever mensagem** envia somente o pedido digitado à OpenAI. O resultado só vai ao campo da campanha quando você clica em **Usar texto na mensagem**. Não envia a campanha.
- **Analisar falhas da campanha** envia apenas contagens de eventos e categorias fixas de falha. Não inclui nomes, telefones, mensagens, anexos, caminhos locais ou credenciais. Use **Ver dados do diagnóstico** para conferir.

A IA não executa ferramentas, não modifica código ou histórico, não corrige números e não reenvia mensagens. A análise é sugestiva; contagens históricas não equivalem ao estado atual dos destinatários. Não há aprendizado permanente automático.

Uso sujeito aos limites do plano ChatGPT. O painel não compra créditos. Revise as permissões do aplicativo em https://chatgpt.com/settings/usage e desative uso de créditos se quiser limitar à assinatura.

Tokens ficam somente na memória da janela Assistente IA. Ao fechar a janela, desconectar ou expirar a autorização, é necessário entrar novamente. O painel mantém apenas o ID do host e o mapeamento de registros/identidades para reutilizar o cadastro. Não solicita offline_access nem guarda refresh tokens. Desconectar encerra a sessão local; revogue o acesso do aplicativo nas configurações do ChatGPT quando desejar.

Documentação oficial usada: [registro e login](https://developers.openai.com/siwc/token-sharing-open-source/sign-in), [modelos e inferência](https://developers.openai.com/siwc/token-sharing-open-source/models-and-inference).

## Atalho

Removida a criação automática por PowerShell após bloqueio observado pelo AVG. O atalho manual existente continua funcionando. **Ajuda com atalho** copia o destino e explica como criar o atalho pelo Windows. Mantenha a pasta do projeto no mesmo lugar.

## Atualizar pelo painel

Abra **Atualizações → Verificar e atualizar**, usando a fonte:

```
https://raw.githubusercontent.com/rmnssmndnc-cyber/painel-whatsapp/main/atualizacoes.json
```

Contatos, campanhas, anexos, sessão e histórico ficam no computador. Não envie a pasta dados para este repositório. O ZIP inclui o código-fonte. Python e Playwright devem estar instalados no projeto.

Validação: 69 testes locais (incluindo bloqueios temporários, persistentes, outros erros de disco e preservação do erro original), incluindo deduplicação, DDI, telefones ausentes, leitura em páginas simuladas, interrupção, planilha sem fórmulas executáveis, autenticação da IA e preservação do histórico. Instalação 2.4.5 → 2.4.6 verificada em cópia temporária e sintaxe JavaScript conferida. O download do navegador de teste falhou neste ambiente; não houve teste visual ou leitura real de grupo. Nenhuma mensagem foi enviada.
