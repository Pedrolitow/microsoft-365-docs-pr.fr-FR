---
title: Configurer la collaboration sécurisée avec Microsoft 365
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
recommendations: false
description: Découvrez comment configurer la collaboration de contenu sécurisée dans Teams protéger vos données en fonction de leur sensibilité.
ms.openlocfilehash: 227f63284f6fb2bdae52fe32d1c011698d3f44fd
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53657050"
---
# <a name="set-up-secure-collaboration-with-microsoft-365-and-microsoft-teams"></a>Configurer une collaboration sécurisée avec Microsoft 365 et Microsoft Teams

La possibilité de partager facilement des informations avec les bonnes personnes tout en empêchant le partage de partage est essentielle au succès d’une organisation. Cela inclut la possibilité de partager des données sensibles en toute sécurité avec uniquement ceux qui doivent y avoir accès. Selon le projet, cela peut inclure le partage de données sensibles avec des personnes extérieures à votre organisation.

Cette solution de collaboration comprend deux composants pour vous aider :

- Déployer Microsoft Teams avec le niveau de protection le plus élevé pour chaque projet
- Configurer le partage externe avec les paramètres de sécurité appropriés pour chaque projet

![Déployer Teams avec une protection appropriée et configurer le partage externe avec les paramètres de sécurité appropriés](..\media\solutions-architecture-center\secure-collaboration-overview.png)

Si les outils de collaboration de contenu souples et faciles à utiliser ne sont pas disponibles, les utilisateurs collaborent souvent par e-mail de documents. Il s’agit d’une méthode de collaboration fastidieuse et sujette aux erreurs, qui peut augmenter le risque de partage inapproprié d’informations. Si les personnes trouvent le partage d’informations trop difficile, elles peuvent revenir à l’utilisation de produits grand public qui ne sont pas régis par le secteur de l’information. Cela peut présenter un risque encore plus élevé.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxMmL?autoplay=false]

Avec Microsoft 365, vous pouvez déployer des Teams avec une variété de configurations qui vous aident :

- Protéger votre propriété intellectuelle
- Faciliter la collaboration
- Créer un équilibre entre sécurité et convivialité qui augmente la satisfaction des utilisateurs et réduit le risque de shadow IT

La plupart des organisations ont une variété d’informations, avec différents degrés de sensibilité et divers degrés d’impact sur l’entreprise si les informations sont partagées de manière inappropriée. Selon la sensibilité d’une information donnée, vous pouvez autoriser le partage avec :

- Tout le monde (non authentifié)
- Personnes au sein de l’organisation
- Personnes spécifiques au sein de l’organisation
- Des personnes spécifiques à l’intérieur et à l’extérieur de l’organisation

Les informations telles que les brochures marketing sont destinées à un partage à l’extérieur de l’organisation. Les informations telles que les menus de menu de menu ne sont pas destinées au partage externe, mais n’auraient aucun impact sur l’entreprise si elles étaient partagées en externe. Ces types d’informations ont peu ou pas besoin d’une protection.

Ces mêmes brochures marketing, en cours de développement, peuvent uniquement être partagées au sein de l’organisation. Dans ce cas, les paramètres de partage par défaut Teams sont peut-être suffisants.

Les informations sur un nouveau produit en cours de développement peuvent être considérées comme sensibles, même au sein de l’organisation. Un degré de protection plus élevé peut être approprié dans ce cas. Vous pouvez restreindre l’accès à ces informations aux membres d’une équipe spécifique, par exemple. Selon le projet, vous devrez peut-être collaborer avec des personnes extérieures à votre organisation, telles qu’un fournisseur ou une organisation partenaire.

Les informations qui sont essentielles au succès de votre organisation ou qui ont des exigences strictes en matière de sécurité ou de conformité peuvent nécessiter des niveaux de protection encore plus élevés.

![Échelle de risque de faible (publication de la brochure) à élevée (données métiers sensibles)](../media/solutions-architecture-center/SecureCollaboration-SensitivityAndBusinessImpactofSharing-fromVisio.png)

Pour tous les scénarios mentionnés ci-dessus, vous pouvez utiliser des équipes dans Microsoft Teams pour stocker, partager et collaborer sur les informations.

Pour configurer la collaboration sécurisée, vous devez utiliser ces fonctionnalités Microsoft 365 de sécurité.

|Produit ou composant|Fonctionnalité|Licence|
|---|---|---|
|Microsoft Defender pour Office 365|Coffre Pièces jointes pour SPO, OneDrive et Teams ; Coffre Documents ; Coffre Liens pour Teams|Microsoft 365 E1, E3 et E5|
|SharePoint|Stratégies de partage de sites et de fichiers, autorisations de partage de site, liens de partage, demandes d’accès, paramètres de partage d’invités de site|Microsoft 365 E1, E3 et E5|
|Microsoft Teams|Accès invité, équipes privées, canaux privés|Microsoft 365 E1, E3 et E5|
|Conformité Microsoft 365|Étiquettes de confidentialité|Microsoft 365 E3 et E5|

## <a name="collaboration-governance"></a>Gouvernance de la collaboration

Microsoft 365 offre de nombreuses options pour la gouvernance de votre solution de collaboration. Nous vous recommandons d’utiliser ce contenu de déploiement en plus du contenu de gouvernance de [collaboration](collaboration-governance-overview.md) pour créer la meilleure solution de collaboration pour votre organisation.

### <a name="using-teams-for-all-kinds-of-data"></a>Utilisation Teams pour tous les types de données

Pour gérer l’accès aux informations selon des sensibilités différentes, nous avons développé trois [niveaux de protection](configure-teams-three-tiers-protection.md)pour Teams . Vous pouvez personnaliser l’un de ces niveaux pour mieux répondre aux besoins ou à votre entreprise.

![Graphique de trois niveaux de protection pour Teams](../media/solutions-architecture-center/Teams-tiers-of-protection-1.png)

Ces *niveaux*( base *de* référence, sensible et hautement *sensible)* augmentent progressivement les protections qui permettent d’éviter le partage et la fuite potentielle d’informations, comme indiqué dans le tableau suivant.

|-|Niveau de référence|Niveau sensible|Niveau hautement sensible|
|---|---|---|---|
|Équipe publique ou privée|Les deux|Private|Private|
|Partage non authentifié|Blocked|Blocked|Blocked|
|Partage de fichiers|Autorisé|Autorisé|Seuls les propriétaires d’équipe peuvent partager.|
|Appartenance à une équipe|Tout le monde peut rejoindre des équipes publiques.<br>Approbation du propriétaire de l’équipe requise pour rejoindre des équipes privées.|Approbation du propriétaire de l’équipe requise pour rejoindre l’équipe.|Approbation du propriétaire de l’équipe requise pour rejoindre l’équipe.|
|Chiffrement de documents|||Disponible avec l’étiquette de niveau de sensibilité|
|Partage d’invités|Autorisé|Peut être autorisé ou bloqué|Peut être autorisé ou bloqué|
|Appareils non gérés|Aucune restriction|Accès web uniquement|Blocked|

La configuration de ces niveaux implique les éléments ci-après :

- Configuration des paramètres dans Teams pour l’accès invité et les canaux privés
- Configuration des paramètres dans le site d’SharePoint d’une équipe pour le partage interne et invité, les demandes d’accès et les liens de partage
- Pour les *niveaux sensibles* et hautement *sensibles,* la configuration des étiquettes de sensibilité pour classer les équipes et contrôler le partage d’invités et l’accès à partir d’appareils non utilisés
- Pour le *niveau hautement sensible,* configuration d’une étiquette de sensibilité pour chiffrer les documents à laquelle elle est appliquée

Commencez par le niveau de référence,  puis ajoutez des équipes qui utilisent les niveaux sensibles et *hautement sensibles* selon vos besoins pour protéger les informations de votre organisation. Consultez ces ressources pour commencer :

- [Configurer les équipes avec la protection de référence](configure-teams-baseline-protection.md)
- [Configurer les équipes avec la protection des données sensibles](configure-teams-sensitive-protection.md)
- [Configurer des équipes avec la protection des données hautement sensibles](configure-teams-highly-sensitive-protection.md)

Si vous avez un projet hautement sensible qui nécessite une protection supplémentaire contre le partage même au sein de votre organisation, vous pouvez configurer une équipe qui utilise sa propre étiquette de sensibilité pour chiffrer les fichiers afin que seuls les membres de l’équipe peuvent les lire. Pour plus [d’informations, voir](secure-teams-security-isolation.md) Configurer une équipe avec isolation de la sécurité.

### <a name="sharing-with-people-outside-your-organization"></a>Partage avec des personnes extérieures à votre organisation

Vous devrez peut-être partager des informations de sensibilité avec [des personnes extérieures à votre organisation.](collaborate-with-people-outside-your-organization.md) Cela peut aller du partage d’un document unique avec une seule personne à la collaboration sur un projet majeur avec une grande organisation partenaire ou des rédacteurs du monde entier. En Microsoft 365, cette plage de partage externe peut être effectuée facilement et avec les protections appropriées pour protéger vos informations sensibles.

Ces ressources vous aideront à commencer à définir votre environnement pour collaborer avec des personnes extérieures à votre organisation :

- [Collaborez sur des documents](collaborate-on-documents.md) pour partager des fichiers individuels de dossiers.
- [Collaborez dans un site pour](collaborate-in-site.md) collaborer avec des invités dans un site SharePoint site.
- [Collaborez en équipe pour](collaborate-as-team.md) collaborer avec des invités d’une équipe.

En fonction de la sensibilité des informations partagées, vous pouvez ajouter des dispositifs de protection pour empêcher le partage. Ces ressources vous aideront à configurer les protections dont vous avez besoin pour votre organisation :

- [Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)
- [Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation](share-limit-accidental-exposure.md)
- [Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)

Si vous avez un projet majeur avec une organisation partenaire, vous pouvez utiliser Azure Entitlement Management pour gérer les invités de cette organisation dans une équipe que vous avez définie pour le projet. Pour plus d’informations, voir Créer un [extranet B2B](b2b-extranet.md) avec des invités gérés.

## <a name="training-for-administrators"></a>Formation pour les administrateurs

Ces modules de formation de Microsoft Learn peuvent vous aider à découvrir les fonctionnalités de collaboration, de gouvernance et d’identité dans Teams et SharePoint.

### <a name="teams"></a>Teams

|Formation :|Gérer la collaboration en équipe avec Microsoft Teams|
|---|---|
|![Teams de formation sur la collaboration](../media/manage-team-collaboration-with-microsoft-teams.svg)|Gérer la collaboration en équipe avec Microsoft Teams vous présente les fonctionnalités et possibilités de Microsoft Teams, le Hub central pour la collaboration en équipe dans Microsoft 365. Vous découvrirez comment utiliser Teams pour simplifier le travail en équipe et la communication au sein de votre organisation, à la fois en local et hors site, sur un large éventail d’appareils (des bureaux aux tablettes et téléphones), tout en tirant parti des fonctionnalités enrichies des applications Office 365. Vous pourrez ainsi comprendre comment Teams fournit un environnement complet et flexible pour la collaboration entre les applications et les appareils. Cette rubrique d’apprentissage peut vous aider à vous préparer à la certification Certification Microsoft 365 : Administrateur Teams associé.<p>2 h 17 min - Learning chemin d’accès - 5 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/m365-teams-collab-prepare-deployment/introduction/)

### <a name="sharepoint"></a>SharePoint

|Formation :|Collaborer avec SharePoint dans Microsoft 365|
|---|---|
|![SharePoint de formation](../media/collaborate-with-sharepoint-in-microsoft-365.svg)|Gérer le contenu partagé avec Microsoft SharePoint vous présente les fonctionnalités de SharePoint, ainsi que son fonctionnement avec Microsoft 365. Vous découvrirez les différents types de sites SharePoint, notamment les sites hub, ainsi que la protection des informations, la création de rapports et la surveillance. En outre, vous apprendrez à utiliser le partage de fichiers et de dossiers SharePoint pour optimiser la collaboration, à partager des fichiers en externe et à gérer des sites SharePoint dans le Centre d’administration SharePoint. Cette rubrique d’apprentissage peut vous aider à vous préparer à la certification Certification Microsoft 365 : Administrateur de travail d’équipe associé.<p>1 h 14 min - Learning chemin d’accès - 4 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/m365-teams-sharepoint-plan-sharepoint/introduction/)

### <a name="information-protection"></a>Protection des informations

|Formation :|Protéger les informations d’entreprise avec Microsoft 365|
|---|---|
|![Teams de formation sur la protection des informations](../media/protect-enterprise-information-microsoft-365.svg)|Plus que jamais, la protection et la sécurisation des informations de votre organisation constituent un défi. Le chemin d’apprentissage pour protéger les informations d’entreprise avec Microsoft 365 explique comment protéger vos informations sensibles contre tout partage excessif accidentel ou utilisation incorrecte, comment découvrir et classifier des données, comment les protéger à l’aide d’étiquettes de confidentialité et comment surveiller et analyser vos informations sensibles pour les protéger contre la perte. Ce parcours d’apprentissage peut vous aider à vous préparer à la certification Microsoft 365 certification : associé administrateur de sécurité et Microsoft 365 certifié : Enterprise certifications expertes en administration.<p>1 h - chemin d Learning - 5 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/m365-security-info-overview/introduction/)

### <a name="identity-and-access"></a>Identité et accès

|Formation :|Protégez les identités et l’accès avec Azure Active Directory|
|---|---|
|![Icône De formation identité et accès](../media/protect-identity-and-access-with-microsoft-365.svg)|Le parcours d’apprentissage Identité et accès aborde les dernières technologies de gestion des identités et accès, ainsi que les outils de renforcement de l’authentification, et donne des conseils sur la protection des identités au sein de votre organisation. Les technologies de gestion des identités et accès de Microsoft vous permettent de sécuriser l’identité de votre organisation (locale ou dans le cloud) et permettent à vos utilisateurs de travailler en toute sécurité où qu’ils se trouvent. Cette rubrique d’apprentissage peut vous aider à vous préparer aux certifications Certification Microsoft 365 : Administrateur de sécurité associé et Certification Microsoft 365 : Administration entreprise expert.<p>2 h 52 min - Learning chemin d’accès - 6 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/m365-identity-overview/introduction/)

## <a name="training-for-end-users"></a>Formation pour les utilisateurs finaux

Ces modules de formation peuvent aider vos utilisateurs à utiliser Teams, des groupes et des SharePoint pour la collaboration Microsoft 365.

|Teams|SharePoint|
|---|---|
|![Configurer et personnaliser l’icône de formation de votre équipe](../media/set-up-customize-team-training.png)<br>**[Configurer et personnaliser votre équipe](https://support.microsoft.com/office/702a2977-e662-4038-bef5-bdf8ee47b17b)**|![SharePoint de formation de partage et de synchronisation](../media/sharepoint-share-sync-training.png)<br>**[Partager et synchroniser](https://support.microsoft.com/office/98cb2ff2-c27e-42ea-b055-c2d895f8a5de)**|
|![Teams l’icône de formation télécharger et rechercher des fichiers](../media/smc-teams-upload-find-files-training.png)<br>**[Télécharger et rechercher des fichiers](https://support.microsoft.com/office/57b669db-678e-424e-b0a0-15d19215cb12)**||
|![Icône Collaborer dans les équipes et les canaux](../media/teams-collaborate-channels-training.png)<br>**[Collaborer dans des équipes et des canaux](https://support.microsoft.com/office/c3d63c10-77d5-4204-a566-53ddcf723b46)**||

## <a name="illustrations"></a>Illustrations

Ces illustrations vous aideront à comprendre comment les groupes et les équipes interagissent avec d’autres services dans Microsoft 365 et les fonctionnalités de gouvernance et de conformité disponibles pour vous aider à gérer ces services dans votre organisation.

### <a name="groups-in-microsoft-365-for-it-architects"></a>Groupes dans Microsoft 365 pour les architectes informatique

Quels sont les besoins des architectes informatique concernant les groupes dans Microsoft 365

|**Item**|**Description**|
|---|---|
|[![Image miniature pour les groupes infographie](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) <br> Mise à jour de juin 2019|Ces illustrations décrivent les différents types de groupes, la manière dont ceux-ci sont créés et gérés et quelques recommandations en matière de gouvernance.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams et services de productivité connexes dans Microsoft 365 pour les architectes informatique

L’architecture logique de services de productivité dans Microsoft 365, fonctionnant avec Microsoft Teams.

|**Item**|**Description**|
|---|---|
|[![Image miniature représentant le poster architecture logique Teams](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>Mise à jour d’avril 2019|Microsoft fournit une suite de services de productivité qui fonctionnent ensemble pour fournir une expérience de collaboration avec la gouvernance des données, la sécurité et la conformité. <p>Cette série d’illustrations fournit une visibilité de l’architecture logique de services de productivité pour les architectes d’entreprise, fonctionnant avec Microsoft Teams.|

## <a name="deploy-the-secure-collaboration-solution"></a>Déployer la solution de collaboration sécurisée

Lorsque vous êtes prêt à déployer cette solution, poursuivez les étapes suivantes :

1. Configurez les [trois différents niveaux de protection pour Teams](configure-teams-three-tiers-protection.md).
2. Configurez les paramètres pour [le partage d’informations sensibles avec des personnes extérieures à votre organisation.](collaborate-with-people-outside-your-organization.md)

## <a name="see-also"></a>Voir aussi

[Documentation de sécurité Office 365](../security/index.yml)

[Documentation sur la conformité dans Microsoft 365](../compliance/index.yml)

[Bienvenue dans Microsoft Teams](/MicrosoftTeams/Teams-overview)
