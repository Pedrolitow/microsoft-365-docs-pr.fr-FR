---
title: Configurer la collaboration sécurisée avec Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: Découvrez comment configurer teams pour protéger vos données en fonction de leur sensibilité.
ms.openlocfilehash: 77493398b11109a51c4e60599561fd8cd4f6c3ac
ms.sourcegitcommit: 101084f9c81616342d78493232d8f13f5ffa4ddf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "44002671"
---
# <a name="set-up-secure-collaboration-with-microsoft-365"></a>Configurer la collaboration sécurisée avec Microsoft 365

La possibilité de partager facilement des informations avec les personnes appropriées tout en empêchant le surPartage est essentielle au succès d’une organisation. Cela inclut la possibilité de partager des données sensibles en toute sécurité avec uniquement les personnes qui doivent y accéder. En fonction du projet, il peut s’agir de partager des données sensibles avec des personnes extérieures à votre organisation.

Ce guide de solution comprend deux composants qui vous aident à :
- Déployer Microsoft teams avec le niveau de protection approprié pour chaque projet
- Configurer le partage externe avec les paramètres de sécurité appropriés pour chaque projet

![Déployer teams avec une protection appropriée et configurer le partage externe avec les paramètres de sécurité appropriés](..\media\solutions-architecture-center\secure-collaboration-overview.png)

Si les outils de collaboration polyvalents et faciles à utiliser ne sont pas disponibles, les utilisateurs collaborent souvent en utilisant des documents de messagerie. Il s’agit d’une méthode de collaboration laborieuse et sujette aux erreurs, qui peut augmenter le risque d’un partage d’informations inapproprié. Si les utilisateurs trouvent des informations de partage trop difficiles, ils peuvent revenir à l’utilisation de produits grand public qui ne sont pas régis par ce dernier. Cela peut poser un risque encore plus élevé.

Avec Microsoft 365, vous pouvez déployer teams avec une variété de configurations qui vous aident à :

- Protéger votre propriété intellectuelle
- Faciliter la collaboration
- Créer un équilibre entre sécurité et convivialité qui augmente la satisfaction des utilisateurs et réduit le risque d’ombre

La plupart des organisations ont un grand nombre d’informations, avec différents degrés de sensibilité et différents degrés d’impact sur l’activité si les informations sont partagées de manière inappropriée. En fonction de la sensibilité d’une information donnée, vous pouvez autoriser le partage avec :

- Tout le monde (non authentifié)
- Personnes au sein de l’Organisation
- Personnes spécifiques au sein de l’Organisation
- Personnes spécifiques à l’intérieur et à l’extérieur de l’Organisation

Les informations telles que les brochures marketing sont destinées à être partagées à l’extérieur de l’organisation. Les informations telles que les menus de la cafétéria ne sont pas destinées au partage externe, mais n’ont pas d’impact commercial si elles étaient partagées en externe. Ces types d’informations nécessitent peu ou pas de protection.

Les mêmes brochures marketing, qu’en cours de développement, ne peuvent être partagées que dans l’organisation. Dans ce cas, les paramètres de partage par défaut dans teams peuvent être suffisants.

Les informations sur un nouveau produit qui est en cours de développement peuvent être considérées comme sensibles, même au sein de l’organisation. Un niveau de protection plus élevé peut être approprié dans ce cas. Vous pouvez restreindre l’accès à ces informations aux membres d’une équipe spécifique, par exemple. En fonction du projet, il se peut que vous deviez collaborer avec des personnes extérieures à votre organisation, telles qu’un fournisseur ou une organisation partenaire.

Des informations essentielles au succès de votre organisation ou ayant des exigences de sécurité ou de conformité rigoureuses peuvent nécessiter des niveaux de protection encore plus élevés.

![Mise à l’ampleur des risques de faible (brochure publiée) à élevée (données professionnelles sensibles)](../media/solutions-architecture-center/SecureCollaboration-SensitivityAndBusinessImpactofSharing-fromVisio.png)

Pour tous les scénarios mentionnés ci-dessus, vous pouvez utiliser teams dans Microsoft teams pour stocker, partager et collaborer sur les informations. 

## <a name="using-teams-for-all-kinds-of-data"></a>Utilisation de teams pour tous les types de données

Pour gérer l’accès aux informations avec différentes sensibilités, nous avons développé [trois niveaux différents de protection pour teams](configure-teams-three-tiers-protection.md). Vous pouvez personnaliser l’un de ces niveaux pour mieux répondre aux besoins ou à votre entreprise. 

![Image miniature représentant le poster architecture logique Teams](../media/solutions-architecture-center/Teams-tiers-of-protection-1.png)


Ces niveaux de *ligne de base*, *sensibles*et *hautement sensibles* , augmentent graduellement les protections qui empêchent le surPartage et les fuites d’informations potentielles, comme illustré dans le tableau suivant.

||**Niveau de référence**|**Niveau sensible**|**Niveau hautement sensible**|
|:--|:-----------|:------------|:-------------------|
|Équipe publique ou privée|Les deux|Private|Private|
|Partage non authentifié|Blocked|Blocked|Blocked|
|Partage de fichiers|Autorisé|Autorisé|Seuls les propriétaires d’équipe peuvent partager.|
|Membres de l’équipe|Tout le monde peut rejoindre des équipes publiques.<br>Approbation du propriétaire de l’équipe requise pour rejoindre des équipes privées.|Approbation du propriétaire de l’équipe requise pour rejoindre le groupe.|Approbation du propriétaire de l’équipe requise pour rejoindre le groupe.|
|Chiffrement de documents|||Disponible avec l’étiquette de confidentialité|
|Partage d’invités|Autorisé|Peut être autorisé ou bloqué|Peut être autorisé ou bloqué|
|Appareils non gérés|Aucune restriction|Accès Web uniquement|Blocked|

La configuration de ces couches implique les opérations suivantes :

- Configuration des paramètres dans teams pour l’accès invité et les canaux privés
- Configuration des paramètres du site SharePoint associé d’une équipe pour le partage interne et invité, les demandes d’accès et les liens de partage
- Pour les niveaux *sensibles* et *hautement sensibles* , configuration des étiquettes de confidentialité pour classer les équipes et contrôler le partage d’invités et l’accès à partir d’appareils non gérés
- Pour le niveau *hautement sensible* , configuration d’une étiquette de sensibilité pour chiffrer les documents auxquels elle s’applique

Commencez par le niveau de ligne de base, puis ajoutez des équipes qui utilisent les niveaux *sensibles* et *hautement sensibles* selon vos besoins afin de protéger les informations de votre organisation. Consultez les ressources suivantes pour commencer :

- [Configurer teams avec la protection de base](configure-teams-baseline-protection.md)
- [Configurer teams avec protection des données sensibles](configure-teams-sensitive-protection.md)
- [Configurer teams avec la protection des données hautement sensibles](configure-teams-highly-sensitive-protection.md)

Si vous disposez d’un projet hautement sensible qui nécessite une protection supplémentaire contre le partage même au sein de votre organisation, vous pouvez configurer une équipe qui utilise sa propre étiquette de confidentialité pour chiffrer les fichiers afin que seuls les membres de l’équipe puissent les lire. Pour plus d’informations, consultez [la rubrique Configure a Team with Security isolation](secure-teams-security-isolation.md) .

## <a name="sharing-with-people-outside-your-organization"></a>Partage avec des personnes extérieures à votre organisation

Il se peut que vous deviez [partager des informations de confidentialité avec des personnes extérieures à votre organisation](collaborate-with-people-outside-your-organization.md). Cela peut aller du partage d’un seul document avec une seule personne à la collaboration sur un projet principal avec une grande organisation partenaire ou des traducteurs indépendants dans le monde entier. Dans Microsoft 365, cette plage de partage externe peut être réalisée facilement et grâce aux protections appropriées pour protéger vos informations sensibles.

Ces ressources vous aideront à configurer votre environnement pour collaborer avec des personnes extérieures à votre organisation :

- [Collaborer sur des documents](collaborate-on-documents.md) pour partager des fichiers individuels de dossiers.
- [Collaborez dans un site](collaborate-in-site.md) pour collaborer avec des invités sur un site SharePoint.
- [Collaborez en tant qu’équipe](collaborate-as-team.md) pour collaborer avec des invités dans une équipe.

En fonction de la sensibilité des informations partagées, vous pouvez ajouter des protections pour empêcher le surPartage. Ces ressources vous aideront à configurer les protections dont vous avez besoin pour votre organisation :

- [Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)
- [Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation](share-limit-accidental-exposure.md)
- [Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)

Si vous disposez d’un projet important avec une organisation partenaire, vous pouvez utiliser Azure habilitations Management pour gérer les invités de cette organisation dans une équipe que vous configurez pour le projet. Pour plus d’informations, voir [créer un extranet B2B avec des invités gérés](b2b-extranet.md) .

## <a name="see-also"></a>Voir aussi

[Documentation de sécurité Office 365](https://docs.microsoft.com/microsoft-365/security)

[Documentation sur la conformité dans Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance)

[Bienvenue dans Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
