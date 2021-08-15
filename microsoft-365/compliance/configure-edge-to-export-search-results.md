---
title: Utiliser l’outil d’exportation eDiscovery dans Microsoft Edge
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Vous devez activer la prise en charge ClickOnce pour utiliser la dernière version de Microsoft Edge pour télécharger les résultats de recherche à partir de la recherche de contenu et de la découverte électronique dans le centre de sécurité et conformité.
ms.openlocfilehash: ec241d36bc24d72e4c0ea3e30e622e42eb9546bfb4b548220e98a0d9ea1c0334
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53830909"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Utiliser l’outil d’exportation eDiscovery dans Microsoft Edge

Suite aux modifications récentes apportées à la dernière version de Microsoft Edge, ClickOnce prise en charge des ClickOnce n’est plus activée par défaut. Pour continuer à utiliser l’outil d’exportation eDiscovery pour télécharger les résultats de recherche de contenu ou eDiscovery, vous devez utiliser [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) ou activer la prise en charge de ClickOnce dans la dernière version de Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Activer ClickOnce prise en charge des Microsoft Edge

1. In Microsoft Edge, go to **edge://flags/#edge-click-once**.

2. Si la valeur existante est définie sur **Default** ou **Disabled** dans la liste liste, changez-la **en Activé.**

   ![Select Enabled from dropdown list](../media/ClickOnceimage1.png)

3. Faites défiler vers le bas jusqu’au bas de la fenêtre du navigateur, puis cliquez sur **Redémarrer** pour redémarrer Edge.

   ![Cliquez sur Redémarrer](../media/ClickOnceimage2.png)

**Remarque :** Les organisations peuvent utiliser la stratégie de groupe pour désactiver ClickOnce prise en charge. Pour vérifier s’il existe une stratégie d’organisation ClickOnce prise en charge, edge://policy **.** La capture d’écran suivante montre que ClickOnce est activé dans toute l’organisation. Si cette valeur de stratégie est définie sur **False,** vous devez contacter un administrateur de votre organisation.

![Liste des stratégies d’organisation Edge](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>Installer et exécuter l’outil d’exportation eDiscovery

1. Cliquez **sur Télécharger les résultats** sur la page volante d’une exportation dans la recherche de contenu ou un cas eDiscovery.

   ![Cliquez sur Télécharger les résultats sur la page volante pour télécharger les résultats de la recherche](../media/ClickOnceExport1.png)

2. Vous serez invité à confirmer le lancement de l’outil, cliquez sur **Ouvrir.**

   ![Cliquez sur Ouvrir pour lancer l’outil d’exportation eDiscovery](../media/ClickOnceimage4.png)

   Si l’outil d’exportation eDiscovery n’est pas installé, un avertissement de sécurité vous est demandé. 

   ![Cliquez sur Installer pour installer l’outil d’exportation eDiscovery](../media/ClickOnceimage5.png)

3. Cliquez sur **Installer**. Une fois installé, l’outil d’exportation se lance automatiquement.

Pour plus d’informations, voir les rubriques suivantes :

- [Exporter les résultats de la recherche de contenu](export-search-results.md)

- [Comment activer des indicateurs d’expérience dans Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
