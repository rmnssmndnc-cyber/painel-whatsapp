# Painel WhatsApp

Aplicativo para Windows com contatos, mensagens livres, imagens e PDFs.

## Versão publicada

[Baixar versão 2.2.3](pacotes/Painel_WhatsApp_2_2_3.zip)

Ao abrir esta versão no Windows, o painel tenta criar automaticamente o atalho **Painel WhatsApp** na Área de Trabalho do usuário. Também há um botão **Criar atalho na Área de Trabalho** para recriá-lo. O atalho usa pythonw.exe para abrir direto o painel, sem digitar comandos. Os resultados dos envios continuam na janela de console. Mantenha a pasta do projeto no mesmo lugar.

A criação usa recursos do Windows e não requer administrador nem alteração de políticas de execução. Se o Windows bloquear a criação, o painel continua disponível e informa a falha. Um atalho de outro programa com o mesmo nome não será sobrescrito.

Mantém as duas tentativas de abertura da versão 2.2.2, somente antes de qualquer envio. Mensagens enviadas manualmente não são reconhecidas automaticamente pelo histórico: confira antes de retomar a campanha.

O ZIP inclui código-fonte e instruções. Requer Python e Playwright já instalados no projeto.

## Atualizar pelo painel

A partir da versão 2.2.0, abra **Atualizações** e configure a fonte:

```
https://raw.githubusercontent.com/rmnssmndnc-cyber/painel-whatsapp/main/atualizacoes.json
```

Clique em **Verificar e atualizar**. Novas versões precisam ser desenvolvidas, testadas e publicadas; o programa não cria atualizações sozinho.

Contatos, campanhas, anexos, sessão e histórico ficam no computador. Não envie a pasta dados para este repositório.

Validação: 40 testes locais sem envio real e instalação 2.2.2 → 2.2.3 em cópia temporária com histórico preservado. A criação e abertura do atalho precisam ser validadas no Windows do usuário.
