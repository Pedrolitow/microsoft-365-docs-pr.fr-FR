---
title: Examiner les alertes dans Microsoft 365 Defender
description: Examiner les alertes visibles sur les appareils, les utilisateurs et les boîtes aux lettres.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: ce75fff753acfa9d5e183154e09805b04d7523da
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321432"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>Examiner les alertes dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les alertes sont la base de tous les incidents et indiquent l’occurrence d’événements malveillants ou suspects dans votre environnement. Les alertes font généralement partie d’une attaque plus large et fournissent des indices sur un incident.

Dans Microsoft 365 Defender, les alertes associées sont regroupées pour former des [incidents](incidents-overview.md). Les incidents fournissent toujours le contexte plus large d’une attaque, mais l’analyse des alertes peut être utile lorsque des analyses plus approfondies sont nécessaires. 

La **file d’attente Alertes** affiche l’ensemble actuel des alertes. Vous arrivez à la file d’attente des **alertes à partir d’incidents & alertes > alertes** sur le lancement rapide du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender web</a>.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="Exemple de file d’attente d’alertes dans le Microsoft 365 Defender web":::

Des alertes provenant de différentes solutions de sécurité Microsoft telles que Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365 et Microsoft 365 Defender apparaissent ici.

Par défaut, la file d’attente des alertes du portail Microsoft 365 Defender affiche les alertes nouvelles et en cours depuis les 30 derniers jours. L’alerte la plus récente se trouve en haut de la liste pour que vous la voyez en premier. 

Dans la file d’attente des alertes par défaut, vous pouvez  sélectionner **Filtrer** pour voir un volet Filtre, à partir duquel vous pouvez spécifier un sous-ensemble des alertes. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="Exemple de volet de filtres pour la file d’attente d’alertes dans Microsoft 365 Defender portail":::

Vous pouvez filtrer les alertes en fonction de ces critères :

- Severity
- Statut
- Sources de service
- Entités (les biens touchés)
- État d’examen automatisé

## <a name="required-roles-for-defender-for-office-365-alerts"></a>Rôles requis pour Defender pour les alertes Office 365 de sécurité

Vous devez avoir l’un des rôles suivants pour accéder à Microsoft Defender pour Office 365 alertes :

- Pour les Azure Active Directory (Azure AD) globaux :

   - Administrateur général

   - Administrateur de sécurité

   - Opérateur de sécurité

   - Lecteur général

   - Lecteur de sécurité

- Office 365 groupes de rôles de conformité & sécurité et conformité

   - Administrateur de conformité

   - Gestion de l’organisation 

- Un [rôle personnalisé](custom-roles.md)

## <a name="analyze-an-alert"></a>Analyser une alerte

Pour voir la page principale de l’alerte, sélectionnez le nom de l’alerte. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="Exemple de page de détails d’une alerte dans le portail Microsoft 365 Defender web":::

Une page d’alerte se compose des sections suivantes : 

- Article d’alerte, qui est la chaîne d’événements et d’alertes liés à cette alerte dans l’ordre chronologique
- Détails récapitulatifs

Dans une page d’alerte, vous pouvez sélectionner les ellipses (**...**) en regard de n’importe quelle entité pour voir les actions disponibles, telles que la liaison de l’alerte à un autre incident. La liste des actions disponibles dépend du type d’alerte.

### <a name="alert-sources"></a>Sources d’alerte

Microsoft 365 Defender alertes peuvent être issues de solutions telles que Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour les applications cloud et le module de gouvernance des applications pour Microsoft Defender pour les applications cloud. Vous remarquerez peut-être des alertes avec des caractères prédépendants dans l’alerte. Le tableau suivant fournit des conseils pour vous aider à comprendre le mappage des sources d’alerte en fonction du caractère prédépendant de l’alerte.

> [!NOTE]
> - Les GUID prédépendants sont spécifiques uniquement aux expériences unifiées telles que la file d’attente des alertes unifiées, la page des alertes unifiées, l’examen unifié et l’incident unifié.
> - Le caractère précédé ne modifie pas le GUID de l’alerte. La seule modification du GUID est le composant prédépendant.

| Source de l’alerte | Caractère en prédépendant |
| :---|:--- |
| Microsoft Defender pour Office 365 | `fa{GUID}` <br> Exemple : `fa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender pour point de terminaison | `da` ou pour `ed` les alertes de détection personnalisées <br> |
| Microsoft Defender pour l’identité | `aa{GUID}` <br> Exemple : `aa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender for Cloud Apps |`ca{GUID}` <br> Exemple : `ca123a456b-c789-1d2e-12f1g33h445h6i` |

### <a name="analyze-affected-assets"></a>Analyser les ressources affectées

La section **Actions entreprises** contient une liste des biens concernés, tels que les boîtes aux lettres, les appareils et les utilisateurs affectés par cette alerte. 

Vous pouvez également sélectionner **Afficher dans le centre de actions** pour  afficher l’onglet  Historique du centre de actions dans le portail Microsoft 365 Defender web. 

### <a name="trace-an-alerts-role-in-the-alert-story"></a>Suivre le rôle d’une alerte dans l’article d’alerte

L’article d’alerte affiche toutes les ressources ou entités associées à l’alerte dans une arborescence de processus. L’alerte dans le titre est celle qui est sélectionnée lorsque vous vous pointez pour la première fois sur la page de votre alerte sélectionnée. Les ressources de l’article d’alerte sont ex expandables et peuvent être cliquées. Ils fournissent des informations supplémentaires et accélèrent votre réponse en vous permettant d’agir directement dans le contexte de la page d’alerte. 

> [!NOTE]
> La section de l’article sur l’alerte peut contenir plusieurs alertes, avec des alertes supplémentaires liées à la même arborescence d’exécution apparaissant avant ou après l’alerte que vous avez sélectionnée.

### <a name="view-more-alert-information-on-the-details-page"></a>Afficher plus d’informations sur les alertes sur la page de détails

La page de détails affiche les détails de l’alerte sélectionnée, ainsi que les détails et les actions qui y sont associés. Si vous sélectionnez l’une des ressources ou entités affectées dans l’article d’alerte, la page de détails change pour fournir des informations contextuelles et des actions pour l’objet sélectionné.

Une fois que vous avez sélectionné une entité d’intérêt, la page de détails change pour afficher les informations sur le type d’entité sélectionné, les informations historiques lorsqu’elle est disponible et les options d’action sur cette entité directement à partir de la page d’alerte.

## <a name="manage-alerts"></a>Gérer des alertes

Pour gérer une alerte, sélectionnez **Gérer l’alerte** dans la section Détails du résumé de la page d’alerte. Pour une seule alerte, voici un exemple du volet Gérer **les** alertes.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="Exemple du volet Gérer les alertes dans le portail Microsoft 365 Defender web":::

Le **volet Gérer les** alertes vous permet d’afficher ou de spécifier :

- État de l’alerte (Nouveau, Résolu, En cours).
- Compte d’utilisateur qui a reçu l’alerte.
- Classification de l’alerte :

   - **Non définie** (valeur par défaut).

   - **Vrai positif avec** un type de menace. Utilisez cette classification pour les alertes qui indiquent avec précision une menace réelle. Spécifier le type de menace permet à votre équipe de sécurité de voir les modèles de menace et d’agir pour défendre votre organisation contre celles-ci.

   - **Activité d’information attendue avec** un type d’activité. Utilisez les options de cette catégorie pour classer les alertes pour les tests de sécurité, l’activité de l’équipe rouge et le comportement inhabituel attendu des applications et des utilisateurs de confiance.

   - **Faux positif pour** les types d’alertes qui ont été créés même en l’absence d’activité malveillante. La classification des alertes comme faux positifs Microsoft 365 Defender améliorer sa qualité de détection.

- Commentaire de l’alerte.

> [!NOTE]
> Une façon de gérer les alertes par le biais de l’utilisation de balises. La fonctionnalité de marquage de Microsoft Defender pour Office 365 est déployée de manière incrémentielle et est actuellement en prévisualisation. <br>
> Actuellement, les noms de balise modifiés sont appliqués uniquement aux alertes créées *après la* mise à jour. Les alertes qui ont été générées avant la modification ne reflètent pas le nom de balise mis à jour. 

Pour gérer un *ensemble d’alertes similaire à* une alerte spécifique, sélectionnez Afficher les **alertes similaires** dans la zone **INSIGHT** de la section détails récapitulatifs de la page d’alerte.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" alt-text="Gérer une alerte dans le portail Microsoft 365 Defender web":::

Dans le **volet Gérer les alertes** , vous pouvez ensuite classer toutes les alertes associées en même temps. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" alt-text="Gestion des alertes associées dans le portail Microsoft 365 Defender web":::

Si des alertes similaires ont déjà été classifiées dans le passé, vous pouvez gagner du temps en utilisant Microsoft 365 Defender recommandations pour découvrir comment les autres alertes ont été résolues. Dans la section Détails du résumé, **sélectionnez Recommandations**.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" alt-text="Exemple de sélection de recommandations pour une alerte":::

**L’onglet Recommandations** fournit des actions et des conseils pour l’examen, la correction et la prévention. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" alt-text="Exemple de recommandations d’alerte":::

## <a name="resolve-an-alert"></a>Résoudre une alerte

Une fois que vous avez terminé l’analyse d’une alerte et qu’elle peut être  résolue, allez dans le volet Gérer l’alerte ou des alertes similaires, marquez l’état comme résolu, puis classez-le comme vrai **positif** avec un type de menace, une activité d’information **,** une activité attendue avec un type d’activité ou un **faux positif**.

La classification des alertes permet Microsoft 365 Defender améliorer sa qualité de détection.

## <a name="use-power-automate-to-triage-alerts"></a>Utiliser Power Automate pour trier les alertes

Les équipes d’opérations de sécurité modernes (SecOps) ont besoin d’automatisation pour fonctionner efficacement. Pour se concentrer sur le recherche et l’investigation des menaces réelles, les équipes SecOps utilisent Power Automate pour trier la liste des alertes et éliminer ceux qui ne sont pas des menaces.  

### <a name="criteria-for-resolving-alerts"></a>Critères de résolution des alertes

- Le message d’in-office de l’utilisateur est allumé

- L’utilisateur n’est pas marqué comme étant à risque élevé

Si les deux sont vraies, SecOps marque l’alerte comme un voyage légitime et la résout. Une notification est publiée dans Microsoft Teams une fois l’alerte résolue.

### <a name="connect-power-automate-to-microsoft-defender-for-cloud-apps"></a>Connecter Power Automate à Microsoft Defender pour les applications cloud

Pour créer l’automatisation, vous aurez besoin d’un jeton d’API avant de pouvoir Power Automate à Microsoft Defender pour les applications cloud.

1. Cliquez **Paramètres**, sélectionnez **Extensions de sécurité**, puis cliquez sur Ajouter un jeton **dans** **l’onglet Jetons d’API**.

2. Fournissez un nom pour votre jeton, puis cliquez sur **Générer**. Enregistrez le jeton, car vous en aurez besoin ultérieurement.

### <a name="create-an-automated-flow"></a>Créer un flux automatisé

Pour obtenir un processus détaillé pas à pas, regardez la vidéo [ici](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn).

Cette vidéo décrit également comment connecter l’automatisation de l’alimentation à Defender pour les applications cloud.

## <a name="next-steps"></a>Étapes suivantes

Si nécessaire pour les incidents in-process, poursuivez votre [enquête](investigate-incidents.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Gérer des incidents](manage-incidents.md)
- [Examiner des incidents](investigate-incidents.md)
