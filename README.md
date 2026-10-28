# Painel WhatsApp

Aplicativo para Windows com contatos, mensagens livres, imagens e PDFs.

## Versão publicada

[Baixar versão 2.2.2](pacotes/Painel_WhatsApp_2_2_2.zip)

A abertura de conversa agora permite duas tentativas, com até 120 segundos de espera pela interface em cada uma. Uma página vazia remove a conversa anterior antes da navegação. A repetição acontece somente antes do envio; não repete mensagens com resultado incerto. Avisos de número inválido são procurados em diálogos e alertas. O diagnóstico estrutural fica em dados/diagnostico_conversa.json, sem mensagens nem telefones.

Isso trata falhas de carregamento; não garante resolver todo contato que falhou. Mensagens enviadas manualmente não são reconhecidas automaticamente pelo histórico: confira antes de retomar a campanha.

O ZIP inclui código-fonte e instruções. Requer Python e Playwright já instalados no projeto.

## Atualizar pelo painel

A partir da versão 2.2.0, abra **Atualizações** e configure a fonte:

```
https://raw.githubusercontent.com/rmnssmndnc-cyber/painel-whatsapp/main/atualizacoes.json
```

Clique em **Verificar e atualizar**. Novas versões precisam ser desenvolvidas, testadas e publicadas; o programa não cria atualizações sozinho.

Contatos, campanhas, anexos, sessão e histórico ficam no computador. Não envie a pasta dados para este repositório.

Validação: 38 testes locais sem envio real e instalação 2.2.1 → 2.2.2 em cópia temporária com histórico preservado. O comportamento real de abertura precisa ser validado no Windows do usuário.
