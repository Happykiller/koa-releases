# KoA — Kingdom of Agents

Poste de supervision des sessions **Claude Code** sous WSL2 : plusieurs agents ouverts en
parallèle, leur état d'un coup d'œil, et la possibilité de répondre sans quitter la fenêtre.

Ce dépôt ne contient **que les binaires**. Les sources sont privées.

## Installer

👉 **[Télécharger la dernière version](../../releases/latest)**

Deux fichiers y sont joints :

| Fichier | Pour qui |
|---|---|
| `KoA-<version>-win-x64.msi` | **le plus simple** — double-clic, aucun droit d'administrateur, raccourci au menu Démarrer, désinstallation propre |
| `KoA-<version>-win-x64.zip` | qui préfère ne rien installer, ou dont l'entreprise bloque les `.msi` |

**Windows affichera « Windows a protégé votre ordinateur »** : le paquet n'est pas signé — ce
n'est pas une menace détectée, c'est l'absence de signature.

Plutôt que de cliquer *Exécuter quand même* sans rien vérifier, deux gestes dans PowerShell, une
fois pour toutes : `Get-FileHash` pour comparer l'empreinte à celle publiée dans la release, puis
`Unblock-File` pour retirer le marquage « téléchargé depuis Internet ». L'avertissement ne revient
plus pour ce fichier. Les deux commandes exactes et l'empreinte de la version sont **en bas de la
page de la release**.

### Si vous prenez le `.zip`

**Extrayez-le avant de lancer KoA** — clic droit sur l'archive → *Extraire tout*.

Double-cliquer `Koa.App.exe` depuis l'aperçu du zip fait apparaître un message réclamant
l'installation du **.NET Desktop Runtime**. Ce message est trompeur : le runtime est bien dans
l'archive, mais Windows n'aura extrait qu'un fichier sur 599. **Ne l'installez pas**, cela ne
débloquerait rien.

## Prérequis

Deux choses qu'aucun paquet ne peut embarquer :

- **WSL2**, avec au moins une distribution et **Claude Code** installé dedans ;
- le **runtime WebView2** — déjà présent sur un Windows à jour.

Windows 10 version 2004 ou plus récent, 64 bits.

## Au premier lancement

KoA dépose son hook dans `~/.koa/` et fusionne les entrées nécessaires dans le
`~/.claude/settings.json` de la distribution, après sauvegarde en `settings.json.koa-backup`.
Sans ce hook, les sessions s'ouvrent mais leur état n'est pas suivi.

Vos données — catalogue, sessions, journaux — vivent dans `%LOCALAPPDATA%\Koa`. **La
désinstallation ne les touche pas.**

## Remonter un défaut

Indiquez la version affichée en haut à gauche de la fenêtre, et joignez le journal du jour :

```
%LOCALAPPDATA%\Koa\logs\koa-AAAAMMJJ.log
```

Pour un journal détaillé, lancez KoA avec `KOA_LOG_LEVEL=Verbose`.
