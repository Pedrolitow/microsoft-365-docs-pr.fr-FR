---
title: Utiliser l’outil d’exportation eDiscovery d’Office 365 dans Microsoft Edge
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Vous devez activer la prise en charge de ClickOnce pour utiliser Microsoft Edge pour exporter les résultats de recherche de la recherche de contenu et eDiscovery dans le centre de sécurité et de conformité.
ms.openlocfilehash: db70b4cdbc57f519db3b6b962eb8aa43585ba335
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42078563"
---
# <a name="use-the-office-365-ediscovery-export-tool-in-microsoft-edge"></a>Utiliser l’outil d’exportation eDiscovery d’Office 365 dans Microsoft Edge

Suite à des modifications récentes apportées à Microsoft Edge, la prise en charge de ClickOnce n’est plus activée par défaut. Pour continuer à utiliser l’outil d’exportation de découverte électronique Microsoft Office 365 pour télécharger des résultats de recherche de contenu ou de découverte électronique, vous devez utiliser [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) ou activer la prise en charge ClickOnce dans Microsoft Edge.

## <a name="how-to-enable-clickonce-support-in-microsoft-edge"></a>Activation de la prise en charge de ClickOnce dans Microsoft Edge

1. Dans Microsoft Edge, accédez à **edge://flags/#edge-cliquez-une seule fois**.

2. Si la valeur existante est définie sur **default** ou **Disabled** dans la liste déroulante, remplacez-la par **Enabled**.
    
   ![](../media/ClickOnceimage1.png)

3. Faites défiler jusqu’au bas de la fenêtre du navigateur et cliquez sur **redémarrer** pour redémarrer le serveur Edge.

   ![](../media/ClickOnceimage2.png)

**Remarque :** Les organisations peuvent utiliser la stratégie de groupe pour désactiver la prise en charge ClickOnce. Pour vérifier s’il existe une stratégie d’organisation pour la prise en charge de ClickOnce, accédez à **Edge://Policy**. La capture d’écran suivante montre que ClickOnce est activé dans l’ensemble de l’organisation. Si cette valeur de stratégie est définie sur **false**, vous devrez contacter un administrateur de votre organisation.

![](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-office-365-ediscovery-export-tool"></a>Installer et exécuter l’outil d’exportation eDiscovery d’Office 365

1. Cliquez sur **Télécharger les résultats** sur la page de menu volant d’une recherche d’exportation dans le contenu ou de découverte électronique.

   ![Cliquez sur Télécharger les résultats sur la page de menu volant pour télécharger les résultats de la recherche.](../media/ClickOnceExport1.png)

2. Vous serez invité à confirmer le lancement de l’outil, puis cliquez sur **ouvrir**.

   ![Cliquez sur Ouvrir pour lancer l’outil d’exportation de découverte électronique.](../media/ClickOnceimage4.png)

   Si l’outil d’exportation de découverte électronique Microsoft Office 365 n’est pas installé, vous serez invité à indiquer un avertissement de sécurité. 

   ![Cliquez sur installer pour installer l’outil d’exportation de découverte électronique.](../media/ClickOnceimage5.png)

3. Cliquez sur **Installer**. Une fois l’installation terminée, l’outil d’exportation se lance automatiquement.

Pour plus d’informations, voir les rubriques suivantes :

- [Exporter les résultats de la recherche de contenu](export-search-results.md)

- [Activation des indicateurs d’expérimentation dans Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
