---
title: Examiner les alertes dans Microsoft 365 Defender
description: Examinez les alertes visibles sur les appareils, les utilisateurs et les boîtes aux lettres.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: a9d8d2fe7fe26b90719502fffebaa96526a26d24207b49136e52373fc058d94b
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53799348"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>Examiner les alertes dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les alertes sont la base de tous les incidents et indiquent l’occurrence d’événements malveillants ou suspects dans votre environnement. Les alertes font généralement partie d’une attaque plus large et fournissent des indices sur un incident.

Dans Microsoft 365 Defender, les alertes associées sont regroupées pour former des [incidents.](incidents-overview.md) Les incidents fournissent toujours le contexte plus large d’une attaque, mais l’analyse des alertes peut être utile lorsque des analyses plus approfondies sont nécessaires. 

La **file d’attente Alertes** affiche l’ensemble actuel des alertes. Vous arrivez à la file d’attente des alertes à partir **d’incidents & alertes** > alertes sur le lancement rapide du portail Microsoft 365 Defender ([security.microsoft.com](https://security.microsoft.com)).

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="Exemple de file d’attente des alertes":::

Les alertes provenant de différentes solutions de sécurité Microsoft telles que Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365 et Microsoft 365 Defender apparaissent ici.

Par défaut, la file d’attente des alertes du portail Microsoft 365 Defender affiche les alertes nouvelles et en cours depuis les 30 derniers jours. L’alerte la plus récente se trouve en haut de la liste, ce qui vous permet de la voir en premier. 

Dans la file d’attente des alertes par défaut, vous pouvez sélectionner **Filtres** pour voir un volet **Filtres,** à partir duquel vous pouvez spécifier un sous-ensemble des alertes. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="Exemple de volet filtres pour la file d’attente d’alertes":::

Vous pouvez filtrer les alertes en fonction de ces critères :

- Severity
- État
- Catégorie
- Source de détection
- Balises
- Stratégie
- Ressources impactées

## <a name="analyze-an-alert"></a>Analyser une alerte

Pour voir la page principale de l’alerte, sélectionnez le nom de l’alerte. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="Exemple de page de détails d’une alerte dans le portail Microsoft 365 Defender web":::

Vous pouvez également sélectionner l’action Ouvrir la **page d’alerte** principale dans le volet Gérer **les** alertes.

Une page d’alerte se compose des sections suivantes : 

- Article d’alerte, qui est la chaîne d’événements et d’alertes liés à cette alerte dans l’ordre chronologique
- Détails récapitulatifs

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="Exemple de page de détails d’une alerte dans le portail Microsoft 365 Defender web":::

Dans une page d’alerte, vous pouvez sélectionner les ellipses (**...**) à côté de n’importe quelle entité pour voir les actions disponibles, telles que l’ouverture de la page d’alerte ou la liaison de l’alerte à un autre incident.

### <a name="alert-sources"></a>Sources d’alerte
Microsoft 365 Defender alertes peuvent être issues de solutions telles que Microsoft Defender pour Endpoint, Microsoft Defender pour Office 365 et Microsoft Cloud App Security. Vous remarquerez peut-être des alertes avec des caractères prédépendants dans l’alerte. Le tableau suivant fournit des conseils pour vous aider à comprendre le mappage des sources d’alerte en fonction du caractère prédépendant de l’alerte.

> [!NOTE]
> - Les GUID prédépendants sont spécifiques uniquement aux expériences unifiées telles que la file d’attente des alertes unifiées, la page des alertes unifiées, l’examen unifié et l’incident unifié.<br>
> - Le caractère précédé ne modifie pas le GUID de l’alerte. La seule modification du GUID est le composant prédépendant.<br>


Source de l’alerte | Caractère en prédépendant 
:---|:---
Microsoft Defender pour Office 365 | `fa{GUID}` <br> Exemple : `fa123a456b-c789-1d2e-12f1g33h445h6i` 
Microsoft Defender pour point de terminaison | `da` ou `ed` pour les alertes de détection personnalisées <br> 
Microsoft Defender pour l’identité | `aa{GUID}` <br> Exemple : `aa123a456b-c789-1d2e-12f1g33h445h6i` 
Microsoft Cloud App Security |`ca{GUID}` <br> Exemple : `ca123a456b-c789-1d2e-12f1g33h445h6i` 

### <a name="analyze-affected-assets"></a>Analyser les ressources affectées

La section **Actions entreprises** contient une liste des biens concernés, tels que les boîtes aux lettres, les appareils et les utilisateurs affectés par cette alerte. 

Vous pouvez également sélectionner Afficher dans  le centre  **de l’action** pour afficher l’onglet Historique du centre de Microsoft 365 Defender de travail. 

### <a name="trace-an-alerts-role-in-the-alert-story"></a>Suivre le rôle d’une alerte dans l’article d’alerte

L’article d’alerte affiche toutes les ressources ou entités associées à l’alerte dans une arborescence de processus. L’alerte dans le titre est celle qui est sélectionnée lorsque vous vous pointez pour la première fois sur la page de votre alerte sélectionnée. Les ressources de l’article d’alerte sont ex expandables et peuvent être cliquées. Ils fournissent des informations supplémentaires et accélèrent votre réponse en vous permettant d’agir directement dans le contexte de la page d’alerte. 

> [!NOTE]
> La section de l’article sur l’alerte peut contenir plusieurs alertes, avec des alertes supplémentaires liées à la même arborescence d’exécution apparaissant avant ou après l’alerte que vous avez sélectionnée.

### <a name="view-more-alert-information-on-the-details-page"></a>Afficher plus d’informations sur les alertes sur la page de détails

La page de détails affiche les détails de l’alerte sélectionnée, ainsi que les détails et les actions qui y sont associés. Si vous sélectionnez l’une des ressources ou entités affectées dans l’article d’alerte, la page de détails change pour fournir des informations contextuelles et des actions pour l’objet sélectionné.

Une fois que vous avez sélectionné une entité d’intérêt, la page de détails change pour afficher les informations sur le type d’entité sélectionné, les informations historiques lorsqu’elle est disponible et les options d’action sur cette entité directement à partir de la page d’alerte.

## <a name="manage-alerts"></a>Gérer des alertes

Pour gérer une alerte, sélectionnez l’alerte dans la file d’attente des alertes sur sa ligne pour voir un volet Gérer **les** alertes. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="Exemple du volet récapitulatif d’une alerte":::

Le **volet Gérer les** alertes vous permet de spécifier :

- État de l’alerte (Nouveau, Résolu, En cours).
- Classification de l’alerte (non définie, alerte True, Fausse alerte).
- Pour la classification en tant qu’alerte réelle, le type de menace pour l’alerte dans le **champ Détermination.**
- Commentaire de l’alerte.

> [!NOTE]
> Une façon de gérer les alertes via l’utilisation de balises. La fonctionnalité de marquage de Microsoft Defender pour Office 365 est déployée de manière incrémentielle et est actuellement en prévisualisation. <br>
> Actuellement, les noms de balise modifiés sont appliqués uniquement aux alertes créées *après la* mise à jour. Les alertes qui ont été générées avant la modification ne reflètent pas le nom de balise mis à jour. 

À partir de ce volet, vous pouvez également effectuer les actions supplémentaires ci-après : 

- Ouvrir la page principale d’alerte
- Consulter un expert en menaces Microsoft
- Afficher l’envoi
- Lien vers un autre incident
- Voir l’alerte dans une chronologie
- Créer une règle de suppression

Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-actions.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-actions.png" alt-text="Exemple d’actions sur une alerte dans le portail Microsoft 365 Defender web":::

La liste des actions supplémentaires dépend du type d’alerte.

## <a name="resolve-an-alert"></a>Résoudre une alerte

Une fois que vous avez terminé l’analyse d’une  alerte et qu’elle peut être  résolue, allez dans le volet Gérer l’alerte et marquez l’état de l’alerte comme Résolu et classez-la en tant qu’alerte **False** ou Alerte **True.** Pour les alertes vraies, spécifiez le type de menace de l’alerte dans le **champ Détermination.**

La classification des alertes et la spécification de leur détermination permettent d’Microsoft 365 Defender pour fournir plus d’alertes vraies et moins de fausses alertes.

## <a name="next-steps"></a>Prochaines étapes

Si nécessaire pour les incidents in-process, poursuivez votre [enquête.](investigate-incidents.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Gérer des incidents](manage-incidents.md)
- [Examiner des incidents](investigate-incidents.md)
