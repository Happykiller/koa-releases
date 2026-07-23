# KoA â€” Kingdom of Agents

Poste de supervision des sessions **Claude Code** sous WSL2 : plusieurs agents ouverts en
parallÃ¨le, leur Ã©tat d'un coup d'Å“il, et la possibilitÃ© de rÃ©pondre sans quitter la fenÃªtre.

Ce dÃ©pÃ´t ne contient **que les binaires**. Les sources sont privÃ©es.

## Installer

ðŸ‘‰ **[TÃ©lÃ©charger la derniÃ¨re version](../../releases/latest)**

Deux fichiers y sont joints :

| Fichier | Pour qui |
|---|---|
| `KoA-<version>-win-x64.msi` | **le plus simple** â€” double-clic, aucun droit d'administrateur, raccourci au menu DÃ©marrer, dÃ©sinstallation propre |
| `KoA-<version>-win-x64.zip` | qui prÃ©fÃ¨re ne rien installer, ou dont l'entreprise bloque les `.msi` |

**Windows affichera Â« Windows a protÃ©gÃ© votre ordinateur Â»** : le paquet n'est pas signÃ©.
*Informations complÃ©mentaires* â†’ *ExÃ©cuter quand mÃªme*.

### Si vous prenez le `.zip`

**Extrayez-le avant de lancer KoA** â€” clic droit sur l'archive â†’ *Extraire tout*.

Double-cliquer `Koa.App.exe` depuis l'aperÃ§u du zip fait apparaÃ®tre un message rÃ©clamant
l'installation du **.NET Desktop Runtime**. Ce message est trompeur : le runtime est bien dans
l'archive, mais Windows n'aura extrait qu'un fichier sur 599. **Ne l'installez pas**, cela ne
dÃ©bloquerait rien.

## PrÃ©requis

Deux choses qu'aucun paquet ne peut embarquer :

- **WSL2**, avec au moins une distribution et **Claude Code** installÃ© dedans ;
- le **runtime WebView2** â€” dÃ©jÃ  prÃ©sent sur un Windows Ã  jour.

Windows 10 version 2004 ou plus rÃ©cent, 64 bits.

## Au premier lancement

KoA dÃ©pose son hook dans `~/.koa/` et fusionne les entrÃ©es nÃ©cessaires dans le
`~/.claude/settings.json` de la distribution, aprÃ¨s sauvegarde en `settings.json.koa-backup`.
Sans ce hook, les sessions s'ouvrent mais leur Ã©tat n'est pas suivi.

Vos donnÃ©es â€” catalogue, sessions, journaux â€” vivent dans `%LOCALAPPDATA%\Koa`. **La
dÃ©sinstallation ne les touche pas.**

## Remonter un dÃ©faut

Indiquez la version affichÃ©e en haut Ã  gauche de la fenÃªtre, et joignez le journal du jour :

```
%LOCALAPPDATA%\Koa\logs\koa-AAAAMMJJ.log
```

Pour un journal dÃ©taillÃ©, lancez KoA avec `KOA_LOG_LEVEL=Verbose`.
