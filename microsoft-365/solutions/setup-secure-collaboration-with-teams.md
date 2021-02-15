---
title: Configurer la collaboration sécurisée avec Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
- m365solution-securecollab
- m365solution-overview
ms.custom:
- M365solutions
- seo-marvel-jun2020
f1.keywords: NOCSH
description: Découvrez comment configurer la collaboration de contenu sécurisée dans Teams pour protéger vos données en fonction de leur sensibilité.
ms.openlocfilehash: f65657125fef8b8cf7e4e229d70d8fe211153392
ms.sourcegitcommit: a0cddd1f888edb940717e434cda2dbe62e5e9475
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49613583"
---
# <a name="set-up-secure-collaboration-with-microsoft-365"></a>Configurer la collaboration sécurisée avec Microsoft 365

La possibilité de partager facilement des informations avec les bonnes personnes tout en empêchant le partage de partage est essentielle au succès d’une organisation. Cela inclut la possibilité de partager des données sensibles en toute sécurité avec uniquement ceux qui doivent y avoir accès. Selon le projet, cela peut inclure le partage de données sensibles avec des personnes extérieures à votre organisation.

Cette solution de collaboration comprend deux composants pour vous aider :
- Déployer Microsoft Teams avec le niveau de protection le plus élevé pour chaque projet
- Configurer le partage externe avec les paramètres de sécurité appropriés pour chaque projet

![Déployer Teams avec une protection appropriée et configurer le partage externe avec les paramètres de sécurité appropriés](..\media\solutions-architecture-center\secure-collaboration-overview.png)

Si les outils de collaboration de contenu souples et faciles à utiliser ne sont pas disponibles, les utilisateurs collaborent souvent par e-mail de documents. Il s’agit d’une méthode de collaboration fastidieuse et sujette aux erreurs, qui peut augmenter le risque de partage inapproprié d’informations. Si les personnes trouvent le partage d’informations trop difficile, elles peuvent revenir à l’utilisation de produits grand public qui ne sont pas régis par le secteur de l’information. Cela peut présenter un risque encore plus élevé.

Avec Microsoft 365, vous pouvez déployer Teams avec une variété de configurations qui vous aident :

- Protéger votre propriété intellectuelle
- Faciliter la collaboration
- Créer un équilibre entre sécurité et convivialité qui augmente la satisfaction des utilisateurs et réduit le risque de shadow IT

La plupart des organisations ont une variété d’informations, avec différents degrés de sensibilité et divers degrés d’impact sur l’entreprise si les informations sont partagées de manière inappropriée. Selon la sensibilité d’une information donnée, vous pouvez autoriser le partage avec :

- Tout le monde (non authentifié)
- Personnes au sein de l’organisation
- Personnes spécifiques au sein de l’organisation
- Des personnes spécifiques à l’intérieur et à l’extérieur de l’organisation

Les informations telles que les brochures marketing sont destinées à un partage à l’extérieur de l’organisation. Les informations telles que les menus de la salle de menus ne sont pas destinées au partage externe, mais n’auraient aucun impact sur l’entreprise si elles étaient partagées en externe. Ces types d’informations n’ont besoin que de peu ou pas de protection.

Ces mêmes brochures marketing, en cours de développement, peuvent uniquement être partagées au sein de l’organisation. Dans ce cas, les paramètres de partage par défaut dans Teams peuvent être suffisants.

Les informations sur un nouveau produit en cours de développement peuvent être considérées comme sensibles, même au sein de l’organisation. Un degré de protection plus élevé peut être approprié dans ce cas. Vous pouvez restreindre l’accès à ces informations aux membres d’une équipe spécifique, par exemple. Selon le projet, vous devrez peut-être collaborer avec des personnes extérieures à votre organisation, telles qu’un fournisseur ou une organisation partenaire.

Les informations qui sont essentielles au succès de votre organisation ou qui ont des exigences strictes en matière de sécurité ou de conformité peuvent nécessiter des niveaux de protection encore plus élevés.

![Échelle de risque de faible (publication de la brochure) à élevée (données métiers sensibles)](../media/solutions-architecture-center/SecureCollaboration-SensitivityAndBusinessImpactofSharing-fromVisio.png)

Pour tous les scénarios mentionnés ci-dessus, vous pouvez utiliser les équipes de Microsoft Teams pour stocker, partager et collaborer sur les informations. 

Pour configurer la collaboration sécurisée, vous utilisez ces fonctionnalités et fonctionnalités Microsoft 365.

| Produit ou composant | Fonctionnalité | Licence |
|:-------|:-----|:-------|
| Microsoft Defender pour Office 365 | Pièces jointes sécurisées pour SPO, OneDrive et Teams ; Documents sécurisés ; Liens sécurisés pour Teams    | Microsoft 365 E1, E3 et E5 |
| SharePoint    | Stratégies de partage de sites et de fichiers, autorisations de partage de site, liens de partage, demandes d’accès, paramètres de partage d’invités de site | Microsoft 365 E1, E3 et E5 |
| Microsoft Teams   | Accès invité, équipes privées, canaux privés | Microsoft 365 E1, E3 et E5 |
| Conformité Microsoft 365  | Étiquettes de confidentialité    | Microsoft 365 E3 et E5 |

### <a name="using-teams-for-all-kinds-of-data"></a>Utilisation de Teams pour tous les types de données

Pour gérer l’accès aux informations avec des sensibilités différentes, nous avons développé trois [niveaux différents de protection pour Teams.](configure-teams-three-tiers-protection.md) Vous pouvez personnaliser l’un de ces niveaux pour mieux répondre aux besoins ou à votre entreprise. 

![Image miniature représentant le poster architecture logique Teams](../media/solutions-architecture-center/Teams-tiers-of-protection-1.png)


Ces *niveaux*( base *de* référence, sensible et hautement *sensible)* augmentent progressivement les protections qui permettent d’éviter le partage et la fuite potentielle d’informations, comme indiqué dans le tableau suivant.

|-|**Niveau de référence**|**Niveau sensible**|**Niveau hautement sensible**|
|:--|:-----------|:------------|:-------------------|
|Équipe publique ou privée|Les deux|Privé|Privé|
|Partage non authentifié|Blocked|Blocked|Blocked|
|Partage de fichiers|Autorisé|Autorisé|Seuls les propriétaires d’équipe peuvent partager.|
|Appartenance à une équipe|Tout le monde peut rejoindre des équipes publiques.<br>Approbation du propriétaire de l’équipe requise pour rejoindre des équipes privées.|Approbation du propriétaire de l’équipe requise pour rejoindre l’équipe.|Approbation du propriétaire de l’équipe requise pour rejoindre l’équipe.|
|Chiffrement de documents|||Disponible avec l’étiquette de niveau de sensibilité|
|Partage d’invités|Autorisé|Peut être autorisé ou bloqué|Peut être autorisé ou bloqué|
|Appareils non gérés|Aucune restriction|Accès web uniquement|Blocked|

La configuration de ces niveaux implique les éléments ci-après :

- Configuration des paramètres dans Teams pour l’accès invité et les canaux privés
- Configuration des paramètres dans le site SharePoint associé d’une équipe pour le partage interne et invité, les demandes d’accès et les liens de partage
- Pour les *niveaux sensibles* et hautement *sensibles,* configurez les étiquettes de sensibilité pour classer les équipes et contrôlez le partage d’invités et l’accès à partir d’appareils nonmanagés
- Pour le *niveau hautement sensible,* configuration d’une étiquette de niveau de sensibilité pour chiffrer les documents auquel elle est appliquée

Commencez par le niveau de référence,  puis ajoutez des équipes qui utilisent les niveaux sensibles et *hautement sensibles* selon vos besoins pour protéger les informations de votre organisation. Consultez ces ressources pour commencer :

- [Configurer les équipes avec la protection de référence](configure-teams-baseline-protection.md)
- [Configurer les équipes avec la protection des données sensibles](configure-teams-sensitive-protection.md)
- [Configurer des équipes avec la protection des données hautement sensibles](configure-teams-highly-sensitive-protection.md)

Si vous avez un projet hautement sensible qui nécessite une protection supplémentaire contre le partage même au sein de votre organisation, vous pouvez configurer une équipe qui utilise sa propre étiquette de sensibilité pour chiffrer les fichiers afin que seuls les membres de l’équipe peuvent les lire. Pour plus [d’informations, voir](secure-teams-security-isolation.md) Configurer une équipe avec isolation de la sécurité.

### <a name="sharing-with-people-outside-your-organization"></a>Partage avec des personnes extérieures à votre organisation

Vous devrez peut-être partager des informations de sensibilité avec [des personnes extérieures à votre organisation.](collaborate-with-people-outside-your-organization.md) Cela peut aller du partage d’un document unique avec une seule personne à la collaboration sur un projet majeur avec une grande organisation partenaire ou des rédacteurs du monde entier. Dans Microsoft 365, cette plage de partage externe peut être effectuée facilement et avec les protections appropriées pour protéger vos informations sensibles.

Ces ressources vous aideront à commencer à définir votre environnement pour collaborer avec des personnes extérieures à votre organisation :

- [Collaborez sur des documents](collaborate-on-documents.md) pour partager des fichiers individuels de dossiers.
- [Collaborez dans un site pour](collaborate-in-site.md) collaborer avec des invités dans un site SharePoint.
- [Collaborez en équipe pour](collaborate-as-team.md) collaborer avec des invités d’une équipe.

En fonction du niveau de sensibilité des informations partagées, vous pouvez ajouter des dispositifs de protection pour empêcher le partage. Ces ressources vous aideront à configurer les protections dont vous avez besoin pour votre organisation :

- [Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)
- [Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation](share-limit-accidental-exposure.md)
- [Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)

Si vous avez un projet majeur avec une organisation partenaire, vous pouvez utiliser Azure Entitlement Management pour gérer les invités de cette organisation dans une équipe que vous avez définie pour le projet. Pour plus d’informations, voir Créer un [extranet B2B](b2b-extranet.md) avec des invités gérés.

## <a name="deploy-the-secure-collaboration-solution"></a>Déployer la solution de collaboration sécurisée

Lorsque vous êtes prêt à déployer cette solution, poursuivez les étapes suivantes :
1. Configurez les [trois différents niveaux de protection pour Teams.](configure-teams-three-tiers-protection.md)
2. Configurez les paramètres pour [le partage d’informations sensibles avec des personnes extérieures à votre organisation.](collaborate-with-people-outside-your-organization.md)

## <a name="see-also"></a>Voir aussi

[Documentation de sécurité Office 365](https://docs.microsoft.com/microsoft-365/security)

[Documentation sur la conformité dans Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance)

[Bienvenue dans Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
