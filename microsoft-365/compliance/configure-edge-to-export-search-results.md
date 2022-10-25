---
title: Utiliser l’outil d’exportation eDiscovery dans Microsoft Edge
description: Vous devez activer la prise en charge de ClickOnce pour utiliser la dernière version de Microsoft Edge pour télécharger les résultats de recherche à partir de Recherche de contenu et eDiscovery dans le portail de sécurité et de conformité.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection:
- tier1
- purview-compliance
- ediscovery
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 31e8937ba83bc1612f2396040b16563fd3dbea9e
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688645"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Utiliser l’outil d’exportation eDiscovery dans Microsoft Edge

En raison des modifications récentes apportées à la version la plus récente de Microsoft Edge, la prise en charge de ClickOnce n’est plus activée par défaut. Pour continuer à utiliser l’outil d’exportation eDiscovery afin de télécharger les résultats de recherche de contenu ou eDiscovery, vous devez utiliser [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) ou activer la prise en charge de ClickOnce dans la version la plus récente de Microsoft Edge.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Activer la prise en charge de ClickOnce dans Microsoft Edge

1. Dans Microsoft Edge, accédez à **edge://flags/#edge-click-once**.

2. Si la valeur existante est définie sur **Par défaut** ou **Désactivé** dans la liste déroulante, remplacez-la par **Activé**.

   ![Sélectionnez Activé dans la liste déroulante.](../media/ClickOnceimage1.png)

3. Faites défiler vers le bas de la fenêtre du navigateur et sélectionnez **Redémarrer** pour redémarrer Microsoft Edge.

   ![Cliquez sur Redémarrer.](../media/ClickOnceimage2.png)

**Note:** Les organisations peuvent utiliser stratégie de groupe pour désactiver la prise en charge de ClickOnce. Pour vérifier s’il existe une stratégie organisationnelle pour la prise en charge de ClickOnce, accédez à **edge://policy**. La capture d’écran suivante montre que ClickOnce est activé dans l’ensemble de l’organisation. Si cette valeur de stratégie est définie sur **false**, vous devez contacter un administrateur de votre organisation.

![Liste des stratégies organisationnelles Edge.](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>Installer et exécuter l’outil d’exportation eDiscovery

1. Sélectionnez **Télécharger les résultats** dans la page volante d’une exportation dans recherche de contenu ou dans un cas eDiscovery.

   ![Cliquez sur Télécharger les résultats dans la page volante pour télécharger les résultats de la recherche.](../media/ClickOnceExport1.png)

2. Vous serez invité à fournir une confirmation de lancement de l’outil, puis sélectionnez **Ouvrir**.

   ![Cliquez sur Ouvrir pour lancer l’outil d’exportation eDiscovery.](../media/ClickOnceimage4.png)

   Si l’outil d’exportation eDiscovery n’est pas installé, un avertissement de sécurité s’affiche. 

   ![Cliquez sur Installer pour installer l’outil d’exportation eDiscovery.](../media/ClickOnceimage5.png)

3. Sélectionnez **Installer**. Une fois installé, l’outil d’exportation se lance automatiquement.

Si vous souhaitez en savoir plus, consultez les articles suivants :

- [Exporter les résultats de la recherche de contenu](export-search-results.md)

- [Comment activer les indicateurs d’expérience dans Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
