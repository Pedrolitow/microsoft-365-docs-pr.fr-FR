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
description: Vous devez activer ClickOnce prise en charge pour utiliser la version la plus récente de Microsoft Edge pour télécharger les résultats de la recherche à partir de recherche de contenu et eDiscovery dans le Centre de sécurité et de conformité.
ms.openlocfilehash: 13556b08a0eaec5ed11bdaf09014a3988cd56829
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092434"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Utiliser l’outil d’exportation eDiscovery dans Microsoft Edge

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Suite aux modifications récentes apportées à la dernière version de Microsoft Edge, ClickOnce prise en charge n’est plus activée par défaut. Pour continuer à utiliser l’outil d’exportation eDiscovery pour télécharger les résultats de recherche de contenu ou eDiscovery, vous devez utiliser [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) ou activer ClickOnce prise en charge dans la dernière version de Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Activer ClickOnce prise en charge dans Microsoft Edge

1. Dans Microsoft Edge, accédez à **edge://flags/#edge-click-once**.

2. Si la valeur existante est définie sur **Valeur par défaut** ou **Désactivée** dans la liste déroulante, **remplacez-la par Activé**.

   ![Sélectionnez Activé dans la liste déroulante.](../media/ClickOnceimage1.png)

3. Faites défiler vers le bas de la fenêtre du navigateur, puis cliquez sur **Redémarrer** pour redémarrer Edge.

   ![Cliquez sur Redémarrer.](../media/ClickOnceimage2.png)

**Note:** Les organisations peuvent utiliser stratégie de groupe pour désactiver ClickOnce prise en charge. Pour vérifier s’il existe une stratégie organisationnelle pour le support ClickOnce, accédez à **edge://policy**. La capture d’écran suivante montre que ClickOnce est activé dans toute l’organisation. Si cette valeur de stratégie est définie sur **false**, vous devez contacter un administrateur de votre organisation.

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
