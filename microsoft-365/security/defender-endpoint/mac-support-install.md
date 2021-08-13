---
title: Résoudre les problèmes d’installation de Microsoft Defender pour Endpoint sur Mac
description: Résolution des problèmes d’installation dans Microsoft Defender pour point de terminaison sur Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, install
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a0de3e0d910e2e410df0f057a389451db98ff017569faf854152088729b5f165
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53833548"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes d’installation de Microsoft Defender pour endpoint sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="installation-failed"></a>Échec de l’installation

Pour l’installation manuelle, la page Résumé de l’Assistant d’installation indique : « Une erreur s’est produite lors de l’installation. Le programme d’installation a rencontré une erreur qui a provoqué l’échec de l’installation. Contactez le fabricant du logiciel pour obtenir de l’aide. » Pour les déploiements mdm, il s’affiche également comme un échec d’installation générique.

Bien que nous n’affichions pas une erreur exacte à l’utilisateur final, nous tenez un fichier journal avec la progression de l’installation dans `/Library/Logs/Microsoft/mdatp/install.log` . Chaque session d’installation s’y connecte. Vous pouvez utiliser la `sed` sortie de la dernière session d’installation uniquement :

```bash
sed -n 'H; /^preinstall com.microsoft.wdav begin/h; ${g;p;}' /Library/Logs/Microsoft/mdatp/install.log
```
```Output
preinstall com.microsoft.wdav begin [2020-03-11 13:08:49 -0700] 804
INSTALLER_SECURE_TEMP=/Library/InstallerSandboxes/.PKInstallSandboxManager/CB509765-70FC-4679-866D-8A14AD3F13CC.activeSandbox/89FA879B-971B-42BF-B4EA-7F5BB7CB5695
correlation id=CB509765-70FC-4679-866D-8A14AD3F13CC
[ERROR] Downgrade from 100.88.54 to 100.87.80 is not permitted
preinstall com.microsoft.wdav end [2020-03-11 13:08:49 -0700] 804 => 1
```

Dans cet exemple, la raison réelle est précédée du `[ERROR]` préfixe .
L’installation a échoué car une mise à niveau vers une version antérieure entre ces versions n’est pas prise en charge.

## <a name="mdatp-install-log-missing-or-not-updated"></a>Journal d’installation MDATP manquant ou non mis à jour

Dans de rares cas, l’installation ne laisse aucune trace dans le fichier /Library/Logs/Microsoft/mdatp/install.log de MDATP.
Vous pouvez vérifier qu’une installation s’est produite et analyser les erreurs possibles en interrogeant les journaux macOS (cela est utile dans le déploiement mdm, en l’absence d’interface utilisateur client). Nous vous recommandons d’utiliser une fenêtre de temps étroite pour exécuter une requête et de filtrer par nom de processus de journalisation, car il y aura une quantité considérable d’informations.

```bash
grep '^2020-03-11 13:08' /var/log/install.log
```
```Output
log show --start '2020-03-11 13:00:00' --end '2020-03-11 13:08:50' --info --debug --source --predicate 'processImagePath CONTAINS[C] "install"' --style syslog
```
