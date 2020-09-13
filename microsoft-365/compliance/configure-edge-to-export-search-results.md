---
title: Utiliser l’outil d’exportation de découverte électronique dans Microsoft Edge
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
description: Vous devez activer la prise en charge de ClickOnce pour utiliser la dernière version de Microsoft Edge pour télécharger les résultats de recherche à partir de la recherche de contenu et eDiscovery dans le centre de sécurité et de conformité.
ms.openlocfilehash: 60f42d2884c56aaff40bc0a6a979e99698a3cd2e
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47546818"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Utiliser l’outil d’exportation de découverte électronique dans Microsoft Edge

En raison de modifications récentes apportées à la version la plus récente de Microsoft Edge, la prise en charge de ClickOnce n’est plus activée par défaut. Pour continuer à utiliser l’outil d’exportation de découverte électronique pour télécharger des résultats de recherche de contenu ou de recherche de découverte électronique, vous devez utiliser [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) ou activer la prise en charge ClickOnce dans la dernière version de Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Activer la prise en charge ClickOnce dans Microsoft Edge

1. Dans Microsoft Edge, accédez à **edge://flags/#edge-cliquez-une seule fois**.

2. Si la valeur existante est définie sur **default** ou **Disabled** dans la liste déroulante, remplacez-la par **Enabled**.

   ![Sélectionner activé à partir de la liste déroulante](../media/ClickOnceimage1.png)

3. Faites défiler jusqu’au bas de la fenêtre du navigateur et cliquez sur **redémarrer** pour redémarrer le serveur Edge.

   ![Cliquez sur redémarrer](../media/ClickOnceimage2.png)

**Remarque :** Les organisations peuvent utiliser la stratégie de groupe pour désactiver la prise en charge ClickOnce. Pour vérifier s’il existe une stratégie d’organisation pour la prise en charge de ClickOnce, accédez à **Edge://Policy**. La capture d’écran suivante montre que ClickOnce est activé dans l’ensemble de l’organisation. Si cette valeur de stratégie est définie sur **false**, vous devrez contacter un administrateur de votre organisation.

![Liste des stratégies organisationnelles Edge](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>Installer et exécuter l’outil d’exportation eDiscovery

1. Cliquez sur **Télécharger les résultats** sur la page de menu volant d’une recherche d’exportation dans le contenu ou de découverte électronique.

   ![Cliquez sur Télécharger les résultats sur la page de menu volant pour télécharger les résultats de la recherche.](../media/ClickOnceExport1.png)

2. Vous serez invité à confirmer le lancement de l’outil, puis cliquez sur **ouvrir**.

   ![Cliquez sur Ouvrir pour lancer l’outil d’exportation de découverte électronique.](../media/ClickOnceimage4.png)

   Si l’outil d’exportation de découverte électronique n’est pas installé, un message d’avertissement de sécurité s’affiche. 

   ![Cliquez sur installer pour installer l’outil d’exportation de découverte électronique.](../media/ClickOnceimage5.png)

3. Cliquez sur **Installer**. Une fois l’installation terminée, l’outil d’exportation se lance automatiquement.

Pour plus d’informations, voir les rubriques suivantes :

- [Exporter les résultats de la recherche de contenu](export-search-results.md)

- [Activation des indicateurs d’expérimentation dans Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
