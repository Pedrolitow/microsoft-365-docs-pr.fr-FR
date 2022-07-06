---
title: Utiliser l’outil d’exportation eDiscovery dans Microsoft Edge
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Vous devez activer le support ClickOnce pour utiliser la version la plus récente de Microsoft Edge pour télécharger les résultats de la recherche à partir de Recherche de contenu et eDiscovery dans le Centre de sécurité et de conformité.
ms.openlocfilehash: f93ab1da1b76d435cc1ce684aa459b4c131dfff8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630386"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Utiliser l’outil d’exportation eDiscovery dans Microsoft Edge

Suite aux modifications récentes apportées à la dernière version de Microsoft Edge, la prise en charge de ClickOnce n’est plus activée par défaut. Pour continuer à utiliser l’outil d’exportation eDiscovery pour télécharger les résultats de recherche de contenu ou eDiscovery, vous devez utiliser [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) ou activer la prise en charge clickOnce dans la version la plus récente de Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Activer la prise en charge de ClickOnce dans Microsoft Edge

1. Dans Microsoft Edge, accédez à **edge://flags/#edge-click-once**.

2. Si la valeur existante est définie sur **Valeur par défaut** ou **Désactivée** dans la liste déroulante, **remplacez-la par Activé**.

   ![Sélectionnez Activé dans la liste déroulante.](../media/ClickOnceimage1.png)

3. Faites défiler vers le bas de la fenêtre du navigateur, puis cliquez sur **Redémarrer** pour redémarrer Edge.

   ![Cliquez sur Redémarrer.](../media/ClickOnceimage2.png)

**Note:** Les organisations peuvent utiliser stratégie de groupe pour désactiver la prise en charge de ClickOnce. Pour vérifier s’il existe une stratégie organisationnelle pour la prise en charge de ClickOnce, accédez à **edge://policy**. La capture d’écran suivante montre que ClickOnce est activé dans l’ensemble de l’organisation. Si cette valeur de stratégie est définie sur **false**, vous devez contacter un administrateur de votre organisation.

![Liste des stratégies d’organisation Edge.](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>Installer et exécuter l’outil d’exportation eDiscovery

1. Cliquez sur **Télécharger les résultats** dans la page de menu volant d’une exportation dans recherche de contenu ou dans un cas eDiscovery.

   ![Cliquez sur Télécharger les résultats dans la page de menu volant pour télécharger les résultats de la recherche.](../media/ClickOnceExport1.png)

2. Vous serez invité à confirmer le lancement de l’outil, Cliquez sur **Ouvrir**.

   ![Cliquez sur Ouvrir pour lancer l’outil d’exportation eDiscovery.](../media/ClickOnceimage4.png)

   Si l’outil d’exportation eDiscovery n’est pas installé, un avertissement de sécurité s’affiche. 

   ![Cliquez sur Installer pour installer l’outil d’exportation eDiscovery.](../media/ClickOnceimage5.png)

3. Cliquez sur **Installer**. Une fois installé, l’outil d’exportation se lance automatiquement.

Pour plus d’informations, voir les rubriques suivantes :

- [Exporter les résultats de la recherche de contenu](export-search-results.md)

- [Comment activer des indicateurs d’expérience dans Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
