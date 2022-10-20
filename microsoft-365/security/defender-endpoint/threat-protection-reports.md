---
title: Rapport sur la protection contre les menaces dans Microsoft Defender pour point de terminaison
description: Suivre les détections d’alertes, les catégories et la gravité à l’aide du rapport de protection contre les menaces
keywords: détection d’alerte, source, alerte par catégorie, gravité de l’alerte, classification des alertes, détermination
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 1f848ac8f0c2e58c91018825b5559f2259169b3b
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68637439"
---
# <a name="threat-protection-report-in-microsoft-defender-for-endpoint"></a>Rapport sur la protection contre les menaces dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Le rapport de protection contre les menaces fournit des informations générales sur les alertes générées dans votre organisation. Le rapport inclut des informations de tendance montrant les sources de détection, les catégories, les gravités, les états, les classifications et les déterminations des alertes dans le temps.

Le tableau de bord est structuré en deux sections :

:::image type="content" source="images/threat-protection-reports.png" alt-text="Rapport sur la protection contre les menaces" lightbox="images/threat-protection-reports.png":::

Section|Description
---|---
1|Tendances des alertes
2|Résumé des alertes

## <a name="alert-trends"></a>Tendances des alertes
Par défaut, les tendances d’alerte affichent les informations d’alerte de la période de 30 jours se terminant par la dernière journée complète. Pour obtenir une meilleure perspective des tendances qui se produisent dans votre organisation, vous pouvez affiner la période de rapport en ajustant la période indiquée. Pour ajuster la période, sélectionnez un intervalle de temps dans les options de liste déroulante :

- 30 jours
- 3 mois
- 6 mois
- Personnalisé

> [!NOTE]
> Ces filtres sont appliqués uniquement à la section Tendances des alertes. Elle n’affecte pas la section récapitulative des alertes.

## <a name="alert-summary"></a>Résumé des alertes

Bien que les tendances d’alerte affichent des informations d’alerte de tendance, le résumé des alertes affiche les informations d’alerte limitées au jour actuel.

 Le résumé des alertes vous permet d’explorer une file d’attente d’alerte particulière avec le filtre correspondant qui lui est appliqué. Par exemple, le fait de cliquer sur la barre EDR dans la carte Sources de détection vous permet d’accéder à la file d’attente des alertes avec des résultats affichant uniquement les alertes générées à partir des détections EDR.

> [!NOTE]
> Les données reflétées dans la section récapitulative sont limitées à 180 jours avant la date actuelle. Par exemple, si la date du jour est le 5 novembre 2019, les données de la section récapitulative reflètent les nombres entre le 5 mai 2019 et le 5 novembre 2019.
>
> Le filtre appliqué à la section Tendances n’est pas appliqué à la section récapitulative.

## <a name="alert-attributes"></a>Attributs d’alerte

Le rapport est constitué de cartes qui affichent les attributs d’alerte suivants :

- **Sources de détection** : affiche des informations sur les capteurs et les technologies de détection qui fournissent les données utilisées par Microsoft Defender pour point de terminaison pour déclencher des alertes.
- **Catégories de menaces** : affiche les types d’activité de menace ou d’attaque qui ont déclenché des alertes, indiquant les zones de focus possibles pour vos opérations de sécurité.
- **Gravité** : affiche le niveau de gravité des alertes, indiquant l’impact potentiel collectif des menaces sur votre organisation et le niveau de réponse nécessaire pour y remédier.
- **État** : affiche l’état de résolution des alertes, indiquant l’efficacité de vos réponses d’alerte manuelles et de la correction automatisée (si activée).
- **Classification & détermination** : montre comment vous avez classé les alertes lors de la résolution, que vous les ayez classifiées comme des menaces réelles (alertes réelles) ou comme des détections incorrectes (fausses alertes). Ces cartes montrent également la détermination des alertes résolues, fournissant des insights supplémentaires tels que les types de menaces réelles trouvées ou les activités légitimes qui ont été détectées incorrectement.

## <a name="filter-data"></a>Filtrer les données

Utilisez les filtres fournis pour inclure ou exclure des alertes avec certains attributs.

> [!NOTE]
> Ces filtres s’appliquent à **toutes les** cartes du rapport.

Par exemple, pour afficher des données sur les alertes de gravité élevée uniquement :

1. Sous **Incidents & alertes** \> **Filtres d’alertes** \> **> Gravité**, sélectionnez **Élevé**.
2. Vérifiez que toutes les autres options sous **Gravité** sont désélectionnées.
3. Sélectionnez **Appliquer**.

## <a name="related-topic"></a>Rubrique connexe

- [Rapport d’intégrité et de conformité des appareils](device-health-reports.md)
