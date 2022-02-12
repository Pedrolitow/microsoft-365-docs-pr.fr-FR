---
title: Résoudre les problèmes d’installation de Microsoft Defender pour endpoint sur Mac
description: Résolution des problèmes d’installation dans Microsoft Defender pour point de terminaison sur Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, install
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5f56e28d472cb3fdf8dd089effcd4beac6e42374
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62766655"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Résoudre les problèmes d’installation de Microsoft Defender pour endpoint sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="installation-failed"></a>Échec de l’installation

Pour l’installation manuelle, la page Résumé de l’Assistant d’installation indique : « Une erreur s’est produite lors de l’installation. Le programme d’installation a rencontré une erreur qui a provoqué l’échec de l’installation. Contactez l’éditeur de logiciels pour obtenir de l’aide. » Pour les déploiements mdm, il s’affiche également sous la forme d’un échec d’installation générique.

Bien que nous n’affichions pas une erreur exacte à l’utilisateur final, nous tenez un fichier journal avec la progression de l’installation dans `/Library/Logs/Microsoft/mdatp/install.log`. Chaque session d’installation s’y connecte. Vous pouvez utiliser la sortie `sed` de la dernière session d’installation uniquement :

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

Dans cet exemple, la raison réelle est précédée du préfixe `[ERROR]`.
L’installation a échoué car une mise à niveau vers une version antérieure entre ces versions n’est pas prise en charge.

## <a name="mdatp-install-log-missing-or-not-updated"></a>Journal d’installation MDATP manquant ou non mis à jour

Dans de rares cas, l’installation ne laisse aucune trace dans le fichier /Library/Logs/Microsoft/mdatp/install.log de MDATP.
Tout d’abord, vérifiez qu’une installation s’est produite. Ensuite, analysez les erreurs possibles en interrogeant les journaux macOS. Il est utile de le faire dans les déploiements mdm, lorsqu’il n’existe pas d’interface utilisateur client. Nous vous recommandons d’utiliser une fenêtre de temps étroite pour exécuter une requête et filtrer selon le nom du processus de journalisation, car il y aura une quantité considérable d’informations.

```bash
grep '^2020-03-11 13:08' /var/log/install.log
```
```Output
log show --start '2020-03-11 13:00:00' --end '2020-03-11 13:08:50' --info --debug --source --predicate 'processImagePath CONTAINS[C] "install"' --style syslog
```
