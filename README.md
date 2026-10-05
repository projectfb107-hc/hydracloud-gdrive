# Hydra GDrive

**O [Hydra Launcher](https://github.com/hydralauncher/hydra) com os saves dos seus jogos guardados no seu próprio Google Drive.**

É o Hydra normal, com uma opção a mais: em vez do Hydra Cloud, o salvamento na nuvem usa uma pasta no **seu** Drive. Você joga, fecha o jogo, e o save sobe sozinho. Em outro PC, ele desce antes de o jogo abrir.

Gratuito, sem fins lucrativos, sem vínculo com o Hydra Launcher nem com o Google. [English summary below](#english).

**[⬇ Baixar a versão mais recente](https://github.com/projectfb107-hc/hydracloud-gdrive/releases/latest)**

---

## O que você precisa

| | |
| --- | --- |
| Sistema | Linux de 64 bits com pacotes **RPM**: Fedora, Nobara e parecidos |
| Conta Hydra | Sim, a gratuita serve. Não precisa de assinatura |
| Conta Google | Sim, a sua. Os saves vão para o seu Drive |

Ainda não há pacote para Windows, Ubuntu/Debian, Arch ou Steam Deck. A versão para Windows está no [roadmap](#roadmap).

## Instalar

1. Baixe o arquivo `hydralauncher-X.Y.Z.x86_64.rpm` da [página de releases](https://github.com/projectfb107-hc/hydracloud-gdrive/releases/latest).
2. Abra um terminal na pasta do download e instale:

   ```bash
   sudo dnf install ./hydralauncher-*.x86_64.rpm
   ```

   Já tem o Hydra oficial instalado na mesma versão? Use `reinstall` no lugar de `install`. Seus jogos, configurações e saves continuam onde estão.

O pacote não é assinado, então instale pelo terminal: alguns atualizadores gráficos recusam pacotes sem assinatura.

## Conectar o Google Drive

1. Abra o Hydra e entre na sua conta Hydra.
2. Vá em **Ajustes → Integrações → Google Drive → Conectar**. Use a janela normal do Hydra: o card do Drive não aparece no modo Big Picture.
3. O navegador abre o login do Google. Entre com a conta em que quer guardar os saves e autorize. Se aparecer um aviso de app não verificado, clique em **Avançado** e continue.
4. De volta ao Hydra, o card mostra a sua conta e **"Salvando no Google Drive"**.

Pronto. Para cada jogo, o Hydra sincroniza ao abrir a página do jogo, antes de iniciar e ao fechar. Para ver ou forçar: página do jogo → **Gerenciar → Hydra Cloud → Sincronizar agora**.

O jogo precisa ter o executável configurado no Hydra. Sem isso, a tela mostra "Executável necessário".

## Desligue a atualização automática do Hydra

Em **Ajustes**, desmarque **"Baixar atualizações automaticamente"**.

Com essa opção ligada, o Hydra baixa a versão **oficial** por cima desta, e a opção do Google Drive some até você instalar de novo o pacote daqui. Seus saves não são afetados.

## Atualizar

Quando sair uma versão nova do Hydra, um pacote novo aparece na [página de releases](https://github.com/projectfb107-hc/hydracloud-gdrive/releases), normalmente no dia seguinte. Baixe e instale do mesmo jeito:

```bash
sudo dnf install ./hydralauncher-*.x86_64.rpm
```

Feche o Hydra antes e abra de novo depois.

## Como funciona

- O app pede só a permissão `drive.file` do Google. Com ela, ele enxerga **apenas os arquivos que ele mesmo criou**, numa pasta chamada **Hydra Cloud Saves**. O resto do seu Drive fica invisível para ele.
- Cada versão de save vira um arquivo de índice, e cada arquivo de save é guardado uma vez só. O que não mudou não é enviado de novo.
- Ficam guardadas as **5 versões mais recentes** de cada jogo.
- O login do Google fica guardado, criptografado, no seu computador. Nada passa por servidor de terceiros: os saves vão do seu PC direto para o Google.
- Todo o resto do salvamento na nuvem é o do próprio Hydra: achar onde cada jogo salva, comparar versões, tratar conflito.

## Perguntas comuns

**Apareceu "Conflito". E agora?**
O Hydra encontrou diferença entre o save do PC e o da nuvem e não quis escolher por você. Abra **Gerenciar → Hydra Cloud**, compare as datas e escolha **Manter saves locais** ou **Usar saves da nuvem**.

**Troquei de conta Google, ou apaguei a pasta no Drive. Perco os saves do PC?**
Não. Quando a nuvem está vazia, esta versão sempre **envia** o que está no PC. Ela nunca apaga saves locais por encontrar a nuvem vazia.

**Apaguei os saves da nuvem num PC. O outro PC apaga os dele?**
Não. Pelo mesmo motivo, o outro PC envia os saves dele de volta. Para apagar de vez, apague nos dois.

**Uso em dois PCs. Preciso fazer algo?**
Instale e conecte a mesma conta Google nos dois. Feche o jogo num antes de abrir no outro, para o save ter tempo de subir.

**Quero voltar para o Hydra Cloud oficial.**
Em **Ajustes → Integrações → Google Drive**, desmarque "Usar o Google Drive para os saves na nuvem" ou clique em **Desconectar**.

**Como apago tudo?**
Clique em **Desconectar** no Hydra e apague a pasta **Hydra Cloud Saves** do seu Drive. Você também pode revogar o acesso em [myaccount.google.com/permissions](https://myaccount.google.com/permissions).

**Os backups antigos do Hydra Cloud (V1) aparecem?**
Não. Eles existem só nos servidores do Hydra e ficam ocultos enquanto o modo Google Drive está ligado.

## Limites conhecidos

- **Só RPM**, por enquanto.
- **Sem atualização automática.** É preciso baixar o pacote novo a cada versão.
- **Até 100 contas Google** podem conectar enquanto o app não passar pela verificação do Google.
- Arquivos de save antigos, que nenhuma versão guardada usa mais, continuam ocupando espaço no Drive. Saves são pequenos, então isso demora a pesar.
- O card do Google Drive só existe na janela normal, não no Big Picture. A sincronização funciona nos dois.

## Roadmap

Planejado, sem data definida:

- **Versão para Windows.** Um instalador `.exe` com o mesmo recurso do Google Drive.
- Pacotes para outras distribuições Linux (`.deb` e AppImage).
- O card do Google Drive também no modo Big Picture.
- Limpeza dos arquivos de save que não são mais usados, para liberar espaço no Drive.
- Verificação do app pelo Google, para tirar o limite de 100 contas.

Quer que algum item ande primeiro? Diga numa [issue](https://github.com/projectfb107-hc/hydracloud-gdrive/issues).

## Voltar ao Hydra oficial

Instale o pacote oficial do [Hydra Launcher](https://github.com/hydralauncher/hydra/releases) por cima. Seus jogos e saves locais continuam.

## Privacidade e termos

[Política de Privacidade](https://projectfb107-hc.github.io/hydracloud-gdrive/privacy.html) · [Termos de Serviço](https://projectfb107-hc.github.io/hydracloud-gdrive/terms.html)

Faça suas próprias cópias dos saves importantes. Este projeto é oferecido como está, sem garantia.

## Problemas e sugestões

Abra uma [issue](https://github.com/projectfb107-hc/hydracloud-gdrive/issues). Diga a versão, o jogo e o que apareceu na tela.

## Créditos e licença

Baseado no [Hydra Launcher](https://github.com/hydralauncher/hydra), de Los Broxas, sob licença MIT. Este projeto não é afiliado ao Hydra Launcher nem ao Google.

---

## English

**Hydra Launcher with your game saves kept in your own Google Drive.** A free, non-commercial build of [Hydra Launcher](https://github.com/hydralauncher/hydra) (MIT). Not affiliated with Hydra Launcher or Google.

**Requirements:** 64-bit Linux with RPM packages (Fedora, Nobara and similar), a Hydra account (free is fine) and your own Google account.

**Install**

```bash
sudo dnf install ./hydralauncher-*.x86_64.rpm
```

Use `reinstall` if the official Hydra of the same version is already installed. The package is unsigned, so install it from a terminal.

**Connect:** Settings → Integrations → Google Drive → Connect, in the regular window (not Big Picture). Sign in with the Google account that should hold your saves. Hydra then syncs each game when you open its page, before launch and after you close it.

**Turn off "Download updates automatically"** in Settings. Otherwise Hydra installs the official build over this one and the Google Drive option disappears until you reinstall. Your saves are not affected.

**Update:** download the new RPM from [Releases](https://github.com/projectfb107-hc/hydracloud-gdrive/releases) and install it the same way. There is no automatic update.

**How it works:** the app asks only for Google's `drive.file` scope, so it can see just the files it created, in a folder named **Hydra Cloud Saves**. Saves go straight from your computer to Google. The 5 most recent versions of each game are kept. An empty cloud never deletes local saves: this build uploads instead.

**Limits:** RPM only; no automatic update; up to 100 Google accounts until the app is verified by Google; the Drive card is not shown in Big Picture.

**Roadmap** (planned, no dates): a **Windows version**, `.deb` and AppImage packages, the Drive card in Big Picture, cleanup of unused save files, and Google verification to lift the 100-account limit.

[Privacy Policy](https://projectfb107-hc.github.io/hydracloud-gdrive/privacy.html) · [Terms of Service](https://projectfb107-hc.github.io/hydracloud-gdrive/terms.html) · [Issues](https://github.com/projectfb107-hc/hydracloud-gdrive/issues)
