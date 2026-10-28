# Painel WhatsApp

Aplicativo local para Windows com contatos, mensagens livres, imagens e PDFs.

## Versão publicada

[Baixar versão 2.3.0](pacotes/Painel_WhatsApp_2_3_0.zip)

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

Validação: 45 testes locais, incluindo fluxo OAuth com servidor local e tokens de teste assinados, rejeição de callbacks inválidos, ausência de credenciais no disco, resposta incompleta e anonimização do diagnóstico. Instalação 2.2.3 → 2.3.0 testada em cópia com histórico preservado. Nenhuma mensagem real foi enviada. Login real com OpenAI, elegibilidade da conta e funcionamento da interface no Windows ainda dependem de validação pelo usuário.
