# Painel WhatsApp

Aplicativo local para Windows com contatos, mensagens livres, imagens e PDFs.

## Versão publicada

[Baixar versão 2.4.3](pacotes/Painel_WhatsApp_2_4_3.zip)

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

Validação: 62 testes locais (incluindo bloqueios temporários, persistentes, outros erros de disco e preservação do erro original), incluindo deduplicação, DDI, telefones ausentes, leitura em páginas simuladas, interrupção, planilha sem fórmulas executáveis, autenticação da IA e preservação do histórico. Instalação 2.4.2 → 2.4.3 verificada em cópia temporária e sintaxe JavaScript conferida. O download do navegador de teste falhou neste ambiente; não houve teste visual ou leitura real de grupo. Nenhuma mensagem foi enviada.
