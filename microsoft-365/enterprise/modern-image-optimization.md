---
title: Optimiser les images dans les pages de sites modernes SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: sstewart
search.appverid:
- MET150
description: Découvrez comment utiliser les outils inclus dans SharePoint Online pour optimiser les images dans les pages de site modernes de SharePoint Online.
ms.openlocfilehash: 62a4b728d4b06b148fa24a3a3163fd980b027ce9
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67702113"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>Optimiser les images dans les pages de sites modernes SharePoint Online

Cet article vous aidera à comprendre comment optimiser les images dans les pages de sites modernes SharePoint Online.

Pour plus d’informations sur l’optimisation des images dans les sites de publication classiques, consultez [Optimisation des images pour SharePoint Online](image-optimization-for-sharepoint-online.md).

>[!NOTE]
>Pour plus d’informations sur les performances dans les portails modernes SharePoint Online, consultez [Performances offertes par l’expérience moderne de SharePoint](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>Utiliser l’outil Diagnostic de page pour SharePoint pour analyser l’optimisation des images

L’outil Diagnostic de page pour SharePoint est une extension de navigateur pour le nouveau Microsoft Edge (https://www.microsoft.com/edge) et les navigateurs Chrome que vous pouvez utiliser pour analyser les pages de sites de publication SharePoint classiques et les portails modernes. L’outil fournit un rapport pour chaque page analysée montrant comment la page se comporte par rapport à un ensemble défini de critères de performance. Pour installer et découvrir l’outil Diagnostic de page pour SharePoint, consultez [Utiliser l’outil Diagnostic de page pour SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>L’outil Diagnostic de page fonctionne uniquement pour SharePoint Online et ne peut pas être utilisé sur une page système SharePoint.

Lorsque vous analysez une page de site moderne SharePoint avec l’outil Diagnostic de page pour SharePoint, vous pouvez voir des informations sur les images de grande taille dans le volet Tests de diagnostic.

Les résultats possibles sont les suivants :

- **Attention requise** (rouge) : la page contient **une ou plusieurs** images dont la taille est supérieure à 300 Ko
- **Aucune action requise** (vert) : la page ne contient pas d’images dont la taille est supérieure à 300 Ko

Si le résultat **Images de grande taille détectées** apparaît dans la section des résultats **Attention requise**, vous pouvez cliquer sur le résultat pour afficher les détails supplémentaires.

![Résultats de l’outil Diagnostics de page.](../media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>Résoudre les problèmes liés aux images de grande taille

Si une page contient des images dont la taille est supérieure à 300 Ko, sélectionnez le résultat **Images de grande taille détectées** pour voir les images trop volumineuses. Dans les pages modernes SharePoint Online, les rendus d’images sont automatiquement fournis et dimensionnés en fonction de la taille de la fenêtre du navigateur et de la résolution du moniteur client. Vous devez toujours optimiser les images pour une utilisation sur le Web avant de les télécharger sur SharePoint Online. Les images de très grand taille sont automatiquement réduites en taille et en résolution, ce qui peut entraîner des caractéristiques de rendu inattendues.

Avant d’apporter des révisions de page pour résoudre les problèmes de performances, notez le temps de chargement des pages dans les résultats de l’analyse. Exécutez à nouveau l’outil après votre révision pour déterminer si le nouveau résultat est inclus dans la norme de référence et vérifier le nouveau temps de chargement des pages pour voir s’il y a eu une amélioration.

![Résultats du temps de chargement de la page.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Le temps de chargement des pages peut varier en fonction de nombreux facteurs tels que la charge réseau, l’heure de la journée et d’autres conditions transitoires. Vous devez tester le temps de chargement des pages plusieurs fois avant et après avoir apporté des modifications pour vous aider à faire la moyenne des résultats.

## <a name="related-topics"></a>Voir aussi

[Optimisation des performances SharePoint Online](tune-sharepoint-online-performance.md)

[Optimisation des performances Office 365](tune-microsoft-365-performance.md)

[Performances offertes par l’expérience moderne de SharePoint](/sharepoint/modern-experience-performance)

[Réseaux de distribution de contenu](content-delivery-networks.md)

[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md)