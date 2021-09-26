---
title: Commentaires et informations NPS du produit Microsoft pour votre organisation
f1.keywords:
- NOCSH
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Utilisez les scores de vos utilisateurs finaux (NPS) pour voir ce qu’ils pensent des produits et services Microsoft.
ms.openlocfilehash: 967de32339c23cf277871102dfecc8c00a55d8e6
ms.sourcegitcommit: aebcdbef52e42f37492a7f780b8b9b2bc0998d5c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59777073"
---
# <a name="microsoft-product-nps-feedback-and-insights-for-your-organization"></a>Commentaires et informations NPS du produit Microsoft pour votre organisation

En tant qu’administrateur d Microsoft 365 organisation, vous pouvez désormais voir les informations et les données générées par les utilisateurs de votre organisation.

Les enquêtes NPS collectent les commentaires des utilisateurs et mesurent la tendance que les utilisateurs entent à recommander des produits et des services à leurs amis et collègues. Ces données peuvent être utilisées au niveau de l’organisation pour déterminer les stratégies d’adoption et de déploiement.

Nous utilisons les enquêtes NPS et les commentaires de vos utilisateurs finaux pour vous fournir des informations sur les produits et services Microsoft. Ces informations peuvent vous aider à déterminer les produits et services que les utilisateurs finaux de votre organisation utilisent, ainsi qu’à identifier les problèmes et à les résoudre rapidement. Avec ces informations, vous pouvez :

<!--See location of users who have submitted feedback-->
- Voir le système d’exploitation ou la plateforme qu’ils utilisent
- Filtrer sur le produit, la plateforme et la recherche à l’aide de mots clés
- Voir les commentaires de l’utilisateur final sur les principaux produits et problèmes
- Exporter les commentaires et les informations d’enquête vers un fichier CSV pour une investigation plus approfondie

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être [](../add-users/about-admin-roles.md) administrateur pour afficher et lire les rapports d’enquête. Les enquêtes de commentaires de votre organisation doivent être allumées pour afficher et lire les rapports d’enquête. Pour en savoir [plus, consultez La](manage-feedback-ms-org.md) gestion des commentaires Microsoft pour votre organisation.

## <a name="survey-insights"></a>Informations sur les enquêtes

1. Dans le Centre d’administration, allez à **l’aperçu** de l’enquête NPS de commentaires sur  >    >  **le produit d’état.**
2. À partir de la page Informations sur les **enquêtes NPS,** accédez à la page pour voir les informations d’enquête relatives à NPS pour votre organisation.

:::image type="content" source="../../media/prosight-product-feedback.png" alt-text="Screenshot: Microsoft 365 Nps survey insights":::

### <a name="chart-information"></a>Informations sur le graphique

**Le nombre** total de commentaires indique le nombre total de réponses de commentaires NPS envoyées par les utilisateurs finaux, inclut les commentaires NPS avec des commentaires et sans commentaires.

**Les commentaires indiquent** le nombre total de réponses de commentaires NPS envoyées par l’utilisateur final qui incluent des commentaires.

**Le volume par application** indique le nombre total de réponses aux commentaires NPS par application.

**Le volume de commentaires par mois** indique le nombre total de réponses de commentaires NPS par mois.

:::image type="content" source="../../media/prosight-charts-area.png" alt-text="Screenshot: Microsoft 365 survey insights":::

### <a name="top-topic-filters"></a>Filtres des principales rubriques

Les rubriques sont des modèles d’apprentissage automatique qui permettent d’analyser les commentaires, les expressions et les commentaires de l’enquête NPS, ce qui permet d’accéder aux thèmes les plus courants à un niveau supérieur. Les filtres des rubriques les plus populaires affichent les 5 premières rubriques avec le plus grand volume de commentaires verbatim.

:::image type="content" source="../../media/prosight-top-topic-filters-2.png" alt-text="Screenshot: Top topic filters on NPS survey data":::

> [!NOTE]
> Nous publions une rubrique intelligente uniquement après qu’elle a rencontré une barre de qualité minimale définie en partenariat avec des experts techniques. Les mesures de précision et de rappel sont utilisées pour déterminer la même valeur.

**La précision détaillée est** la manière dont il est probable qu’un verbatim classé dans cette rubrique soit correct.

**Verbatim Recall** est la manière dont un verbatim lié à cette rubrique est classé dans cette rubrique.

Les rubriques actuellement disponibles sont les suivantes :

**La navigation** inclut les commentaires des clients sur la navigation et l’utilisation de l’application.

- Précision détaillée - 93 %
- Rappel verbatim - 98 %

**La collaboration** fait référence à la facilité de collaboration des utilisateurs à l’aide des applications Microsoft.

- Verbatim Precision - 92 %
- Verbatim Recall-91%

**La valeur** fait référence aux perceptions des clients concernant des sujets tels que les préférences de tarification et de paiement.

- Verbatim Precision- 86%
- Verbatim Recall- 100%

**La fiabilité** inclut les commentaires des clients sur le comportement de l’application et du système, ce qui entraîne un arrêt inattendu.

- Précision détaillée - 97 %
- Rappel verbatim - 94 %

**Les** performances font référence aux commentaires des clients qui traitent des problèmes liés à la vitesse perçue des opérations qu’un utilisateur connaît lors de l’utilisation d’un produit Microsoft. Cette rubrique ne couvre pas les domaines des incidents ou des problèmes de fiabilité plus larges.

- Verbatim Precision - 92 %
- Rappel verbatim - 98 %

**Les commentaires des utilisateurs** sur l’éducation incluent des commentaires des clients sur la documentation d’aide, des didacticiels, des guides et d’autres contenus d’apprentissage en ligne ou dans le produit.

- Verbatim Precision- 83%
- Rappel verbatim - 87 %

**La complexité** fait référence aux commentaires des clients quant à la complexité ou à l’utilisation des applications.

- Verbatim Precision - 92 %
- Rappel verbatim - 89 %

**Les Compliment** font référence aux commentaires des clients qui ont un sentiment positif et qui ne correspondent à aucun autre sujet.

- Précision détaillée - 93 %
- Rappel verbatim - 98 %

### <a name="export-to-csv-and-search"></a>Exporter vers le CSV et la recherche

Vous pouvez exporter des données brutes pour une analyse plus approfondie à l’aide de la fonctionnalité Exporter vers CSV.

> [!NOTE]
> Les données brutes incluent tous les types de commentaires, y compris les commentaires non NPS.

### <a name="filters"></a>Filtres

Vous pouvez filtrer par **canaux,** **produits,** **plateformes** et **types de commentaires.**

**Les canaux** sont un moyen pour les organisations de sélectionner la fréquence à quelle fréquence elles obtiennent des mises à jour de fonctionnalités pour Office. Pour plus d’informations, [découvrez la vue d’ensemble des canaux de mise à jour Microsoft 365 Apps.](/deployoffice/overview-update-channels) Ce filtre vous permet de filtrer jusqu’aux commentaires envoyés par un utilisateur sur un canal spécifique

Les commentaires peuvent être envoyés sur différentes **plateformes telles** qu’Android, iOS, Mac et Windows. Ce filtre vous permet de filtrer les commentaires en fonction de la plateforme sur qui il a été envoyé.

La majorité des Microsoft 365 **produits pour** les entreprises se trouvent sous ce filtre. Utilisez ce filtre pour sélectionner les produits pour qui des commentaires ont été soumis.

Utilisez **les types de commentaires** (uniquement sur les types de commentaires NPS) pour filtrer les commentaires que nous collectons.

:::image type="content" source="../../media/prosight-filters.png" alt-text="Screenshot: Microsoft 365 NPS survey insights filters":::
