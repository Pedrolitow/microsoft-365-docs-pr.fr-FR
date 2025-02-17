---
title: Score d’adoption Microsoft - Confidentialité
f1.keywords:
- NOCSH
ms.author: camillepack
author: camillepack
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
monikerRange: o365-worldwide
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: Comment la confidentialité est protégée avec le score d’adoption.
ms.openlocfilehash: 74ca30762ecaccc03ff76c7c928f3f96f566a05c
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726858"
---
# <a name="privacy-controls-for-adoption-score"></a>Contrôles de confidentialité pour le score d’adoption

Le score d’adoption fournit des insights sur le parcours de transformation numérique de votre organisation grâce à son utilisation de Microsoft 365 et aux expériences technologiques qui le prennent en charge.  Le score de votre organisation reflète les mesures des personnes et de l’expérience technologique et peut être comparé à des points de référence d’organisations similaires à la vôtre. Pour plus d’informations, consultez la [vue d’ensemble du score d’adoption](adoption-score.md).

Votre confidentialité est importante pour Microsoft. Pour savoir comment nous protégeons votre confidentialité, consultez la [déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement). Le score d’adoption vous donne, en tant qu’administrateur informatique de votre organisation, l’accès aux paramètres de confidentialité pour vous assurer que toutes les informations de score d’adoption que vous affichez sont exploitables, sans compromettre la confiance que votre organisation accorde à Microsoft.

Dans la zone expériences des personnes, les métriques sont disponibles uniquement au niveau de l’organisation. Cette zone examine la façon dont les utilisateurs utilisent Microsoft 365 en examinant les catégories de collaboration de contenu, mobilité, réunions, travail d’équipe et communication. Nous vous proposons plusieurs niveaux de contrôle pour vous aider à répondre à vos besoins en matière de politique de confidentialité interne.
Les contrôles vous donnent les éléments suivants :

- Rôles d’administrateur flexibles pour contrôler qui peut voir les informations dans le score d’adoption
- La possibilité de supprimer des utilisateurs et des groupes des calculs d’expérience de personnes
- La possibilité de refuser le domaine d’expérience des personnes

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-adoption-score"></a>Rôles d’administrateur flexibles pour contrôler qui peut voir les informations dans le score d’adoption

Pour afficher l’intégralité du score d’adoption, vous devez avoir l’un des rôles d’administrateur suivants :

- Administrateur général
- Administrateurs Exchange
- Administrateur SharePoint
- Administrateur Skype Entreprise
- Administrateur Teams
- Lecteur général
- Lecteur de rapports
- Lecteur Rapports de synthèse de l’utilisation
- Gestionnaire de réussite de l’expérience utilisateur

L’administrateur général peut attribuer le rôle Lecteur de rapports, Lecteur de rapports récapitulatives d’utilisation ou Gestionnaire de réussite de l’expérience utilisateur à toute personne responsable de la gestion et de l’adoption des modifications, mais pas nécessairement un administrateur informatique.

Les utilisateurs disposant du rôle Lecteur de rapports peuvent afficher les données de rapport d’utilisation et le tableau de bord des rapports dans Centre d'administration Microsoft 365 et le pack de contexte d’adoption dans Power BI. Les utilisateurs disposant du rôle Lecteur des rapports de résumé d’utilisation peuvent uniquement voir les agrégats au niveau du locataire et les agrégats au niveau du groupe dans Microsoft 365 Usage Analytics and Adoption Score. Le rôle Gestionnaire de réussite de l’expérience utilisateur inclut les autorisations du rôle Lecteur des rapports de synthèse d’utilisation et peut accéder à d’autres informations relatives à l’adoption, telles que le Centre de messages, les commentaires sur les produits et l’intégrité du service. Pour en savoir plus sur les différents rôles, consultez [Rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference) .

## <a name="capability-to-choose-specific-users-or-certain-groups"></a>Possibilité de choisir des utilisateurs spécifiques ou certains groupes

Vous pouvez choisir les utilisateurs et les groupes dont les données seront utilisées pour déterminer les expériences des personnes de votre organisation. L’omission de certains groupes affecte les calculs d’insights. Vous devez être administrateur général pour exclure votre organisation des rapports d’expérience de personnes. L’application de la modification peut prendre jusqu’à 24 heures.

Pour omettre certains groupes :

1. Dans le Centre d’administration, accédez à **Paramètres** > **de l’organisation** > **Score d’adoption**.
2. Sélectionnez **Exclure des utilisateurs spécifiques via un groupe**.  
3. Choisissez un ou plusieurs groupes AAD Administration Center à omettre.
4. Sélectionnez **Enregistrer les modifications**.

:::image type="content" source="../../media/adoption-score-exclude-users.png" alt-text="Capture d’écran : option permettant d’exclure des utilisateurs spécifiques via un groupe lors du calcul des insights.":::

## <a name="capability-to-opt-out-of-people-experiences"></a>Possibilité de refuser les expériences des personnes

Vous pouvez également désactiver la zone d’expérience des personnes du score d’adoption. Si vous vous désengagez, personne de votre organisation ne sera en mesure d’afficher ces métriques, et votre organisation sera supprimée de tous les calculs qui impliquent la communication, les réunions, le travail d’équipe, la collaboration de contenu et la mobilité. Vous devez être administrateur général pour exclure votre organisation des rapports d’expérience de personnes. L’application de la modification peut prendre jusqu’à 24 heures. Vous pouvez annuler votre modification avant la fin de la journée en heure UTC pour conserver les données historiques.

Pour refuser :

1. Dans le Centre d’administration, accédez à **Paramètres**  >  **de l’organisation** > **Score d’adoption**.
2. Sélectionnez **Ne pas calculer pour les utilisateurs**. 
3. Dans l’écran de confirmation **Voulez-vous supprimer des données des expériences contacts ?** , sélectionnez **Supprimer les données**.
4. Sélectionnez  **Enregistrer**.

:::image type="content" source="../../media/adoption-score-calculate-insights.png" alt-text="Capture d’écran : option des paramètres de l’organisation pour désactiver les insights sur les expériences de personnes":::
