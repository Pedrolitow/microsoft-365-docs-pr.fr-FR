---
title: Gouvernance de l’accès dans les groupes Microsoft 365, Teams et SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment régir l’accès dans les groupes Microsoft 365, Teams et SharePoint.
ms.openlocfilehash: 7d0f49f394bb6c5408c7de98d9fe63f306b334b2
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67985737"
---
# <a name="governing-access-in-microsoft-365-groups-teams-and-sharepoint"></a>Gouvernance de l’accès dans les groupes Microsoft 365, Teams et SharePoint

Il existe de nombreux contrôles qui vous permettent de régir la façon dont les personnes accèdent aux ressources dans les groupes, les équipes et SharePoint. Passez en revue ces options et réfléchissez à la façon dont elles correspondent à vos besoins métier, à la sensibilité de vos données et à l’étendue des personnes avec lesquelles vos utilisateurs doivent collaborer.

Le tableau suivant fournit une référence rapide pour les contrôles d’accès disponibles dans Microsoft 365. Des informations supplémentaires sont fournies dans les sections suivantes.

|Catégorie|Description|Référence|
|:-------|:----------|:--------|
|Appartenance|||
||Découverte d’équipes privées|[Gérer la découverte d’équipes privées dans Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)|
||Appartenance à un groupe dynamique basée sur des règles|[Créer ou mettre à jour un groupe dynamique dans Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)|
||Contrôler qui peut partager des fichiers, des dossiers et des sites.|[Configurer et gérer les demandes d’accès](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)|
|Accès conditionnel|||
||Authentification multifacteur|[Authentification multifacteur Azure AD](/azure/active-directory/authentication/concept-mfa-howitworks)|
||Contrôler l’accès aux appareils en fonction du groupe, de l’équipe ou du site.|[Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Limitez l’accès au site pour les appareils non gérés.|[Contrôler l’accès SharePoint à partir d’appareils non gérés](/sharepoint/control-access-from-unmanaged-devices)|
||Contrôler l’accès au site en fonction de l’emplacement|[Contrôler l’accès aux données SharePoint et OneDrive en fonction de l’emplacement réseau](/sharepoint/control-access-based-on-network-location)|
|Accès invité|||
||Autorisez ou bloquez le partage SharePoint à partir de domaines spécifiés.|[Restreindre le partage de contenu SharePoint et OneDrive par domaine](/sharepoint/restricted-domains-sharing)|
||Autorisez ou bloquez l’appartenance à une équipe ou à un groupe à partir de domaines spécifiés.|[Autoriser ou bloquer des invitations à des utilisateurs B2B à partir d’organisations spécifiques](/azure/active-directory/b2b/allow-deny-list)|
||Empêcher le partage anonyme.|[Désactiver les liens Tout le monde](./share-limit-accidental-exposure.md#turn-off-anyone-links)|
||Contrôlez les autorisations pour les liens d’accès anonyme.|[Définir des autorisations de lien pour les liens Tout le monde](./best-practices-anonymous-sharing.md#set-link-permissions)|
||Contrôler l’expiration des liens de partage anonyme.|[Définir une date d’expiration pour les liens Tout le monde](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)|
||Contrôlez le type de lien de partage indiqué aux utilisateurs par défaut.|[Modifier le type de lien par défaut d’un site](/sharepoint/change-default-sharing-link)|
||Limitez le partage externe à des personnes spécifiques.|[Limiter le partage externe aux groupes de sécurité spécifiés](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)|
||Contrôler l’accès invité à un groupe, une équipe ou un site en fonction de la sensibilité des informations.|[Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Désactivez les options de partage.|[Limiter le partage dans Microsoft 365](./microsoft-365-limit-sharing.md)|
|Gestion des utilisateurs|||
||Passez régulièrement en revue l’appartenance à l’équipe et au groupe.|[Que sont les révisions d’accès Azure AD ?](/azure/active-directory/governance/access-reviews-overview)|
||Automatiser la gestion des accès aux groupes et aux équipes.|[Qu’est-ce que la gestion des droits d’utilisation Azure AD ?](/azure/active-directory/governance/entitlement-management-overview)|

## <a name="membership"></a>Appartenance

L’appartenance des équipes et des groupes est contrôlée par les propriétaires. Les membres peuvent inviter d’autres personnes, mais les invitations sont envoyées aux propriétaires pour approbation. Bien que les équipes et les groupes publics soient détectables par n’importe qui dans l’organisation, vous pouvez contrôler si les équipes et les groupes privés sont détectables :

- [Gérer la découverte d’équipes privées dans Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)

Vous pouvez gérer dynamiquement l’appartenance à un groupe ou une équipe en fonction de certains critères, tels que le service. Dans ce cas, les membres et les propriétaires ne peuvent pas inviter de personnes à l’équipe. Les groupes dynamiques utilisent les métadonnées que vous définissez dans Azure Active Directory pour contrôler qui est membre du groupe. Assurez-vous que les métadonnées que vous utilisez sont complètes et à jour, car des métadonnées incorrectes peuvent entraîner l’interruption des groupes ou l’ajout d’utilisateurs incorrects.

- [Créer ou mettre à jour un groupe dynamique dans Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

Les sites SharePoint offrent la possibilité d’ajouter des propriétaires, des membres et des visiteurs en dehors de l’appartenance au groupe ou à l’équipe. En fonction de vos besoins, vous souhaiterez peut-être limiter les personnes pouvant inviter des personnes à accéder au site. En outre, en fonction de la sensibilité des informations dans un site donné, vous souhaiterez peut-être limiter les personnes pouvant partager des fichiers et des dossiers. Ces restrictions sont configurées par l’équipe, le groupe ou le propriétaire du site :

- [Configurer et gérer les demandes d’accès](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)


## <a name="conditional-access"></a>Accès conditionnel

Avec Microsoft 365, vous pouvez exiger une authentification multifacteur pour les personnes internes et externes à votre organisation. Il existe de nombreuses options pour les circonstances dans lesquelles les personnes sont invités à entrer un deuxième facteur d’authentification. Nous vous recommandons vivement de déployer l’authentification multifacteur pour votre organisation :

- [Authentification multifacteur Azure AD](/azure/active-directory/authentication/concept-mfa-howitworks)

Si vous disposez d’informations sensibles dans certains de vos groupes et équipes, vous pouvez appliquer des stratégies de gestion des appareils en fonction de l’étiquette de confidentialité d’un groupe ou d’une équipe. Vous pouvez bloquer entièrement l’accès à partir d’appareils non gérés, ou autoriser un accès web limité uniquement :

- [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)

Dans SharePoint, vous pouvez restreindre l’accès aux sites à partir d’emplacements réseau spécifiés.

- [Contrôler l’accès aux données SharePoint et OneDrive en fonction de l’emplacement réseau](/sharepoint/control-access-based-on-network-location)


Ressources supplémentaires :

- [Planifier un déploiement d’accès conditionnel](/azure/active-directory/conditional-access/plan-conditional-access)

- [Vue d’ensemble de Microsoft Intune](/mem/intune/fundamentals/what-is-intune)

- [Contrôler l’accès SharePoint à partir d’appareils non gérés](/sharepoint/control-access-from-unmanaged-devices)


## <a name="guest-access"></a>Accès invité

Vous pouvez restreindre les invités en fonction du domaine de leur adresse e-mail. SharePoint offre des paramètres de restriction de domaine propres à l’organisation et au site. Les groupes et Teams utilisent les listes d’autorisation ou les listes de blocage de domaine dans Azure AD. Veillez à configurer les deux paramètres pour éviter le partage indésirable et garantir une expérience utilisateur cohérente :

- [Restreindre le partage de contenu SharePoint et OneDrive par domaine](/sharepoint/restricted-domains-sharing)

- [Autoriser ou bloquer des invitations à des utilisateurs B2B à partir d’organisations spécifiques](/azure/active-directory/b2b/allow-deny-list)

Microsoft 365 permet le partage anonyme de fichiers et de dossiers à l’aide de liens de partage *tout le monde* . *Tous les* liens peuvent être transférés et toute personne disposant du lien peut accéder à l’élément partagé. En fonction de la sensibilité de vos données, envisagez de régir la façon dont les liens *Anyone* sont utilisés, notamment en les désactivant entièrement, en limitant les autorisations de liaison en lecture seule ou en définissant un délai d’expiration pour eux :

- [Désactiver les liens Tout le monde](./share-limit-accidental-exposure.md#turn-off-anyone-links)

- [Définir des autorisations de lien pour les liens Tout le monde](./best-practices-anonymous-sharing.md#set-link-permissions)

- [Définir une date d’expiration pour les liens Tout le monde](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)

Lors du partage de fichiers ou de dossiers, les utilisateurs ont plusieurs types de liens parmi lesquels choisir. Pour réduire le risque de partage inapproprié accidentel, vous pouvez modifier le type de lien par défaut présenté aux utilisateurs lorsqu’ils partagent. Par exemple, la modification de la valeur par défaut des liens *Tout le monde* ( qui autorisent l’accès anonyme ) à *Personnes dans les liens de votre organisation* peut réduire le risque de partage externe indésirable d’informations sensibles :

- [Modifier le type de lien par défaut d’un site](/sharepoint/change-default-sharing-link)

Si votre organisation a des données sensibles que vous devez partager avec des invités, mais que vous êtes préoccupé par un partage inapproprié, vous pouvez limiter le partage externe de fichiers et de dossiers aux membres des groupes de sécurité spécifiés. De cette façon, vous pouvez restreindre le partage externe à un groupe spécifique de personnes, ou demander à vos utilisateurs de suivre une formation sur le partage externe approprié avant de les ajouter au groupe de sécurité :

- [Limiter le partage externe aux groupes de sécurité spécifiés](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)

Les groupes et Teams ont des paramètres au niveau de l’organisation qui autorisent ou refusent l’accès invité. Bien que vous puissiez [restreindre l’accès invité à des équipes ou des groupes spécifiques à l’aide de Microsoft PowerShell](per-group-guest-access.md), nous vous recommandons de le faire au moyen d’une étiquette de confidentialité. Avec les étiquettes de confidentialité, vous pouvez autoriser ou refuser automatiquement l’accès invité en fonction de l’étiquette appliquée :

- [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)

Dans un environnement où vous invitez fréquemment des invités à des groupes et des équipes, envisagez de configurer des révisions d’accès invité régulièrement planifiées. Les propriétaires peuvent être invités à consulter les invités de leurs groupes et équipes et à approuver ou refuser l’accès.

- [Configurer les révisions d’accès invité](/microsoft-365/solutions/create-secure-guest-sharing-environment#set-up-guest-access-reviews)

Microsoft 365 offre de nombreuses méthodes différentes de partage d’informations. Si vous disposez d’informations sensibles et que vous souhaitez restreindre la façon dont elles sont partagées, passez en revue les options permettant de limiter le partage :

- [Limiter le partage dans Microsoft 365](./microsoft-365-limit-sharing.md)

Ressources supplémentaires :

- [Configurer la collaboration sécurisée avec Microsoft 365](./setup-secure-collaboration-with-teams.md)

- [Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](./best-practices-anonymous-sharing.md)

- [Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation](./share-limit-accidental-exposure.md)

- [Créer un environnement de partage sécurisé avec des invités](./create-secure-guest-sharing-environment.md)

- [Activer la collaboration externe B2B, puis gérer les utilisateurs pouvant avoir des invités](/azure/active-directory/b2b/delegate-invitations)

## <a name="user-management"></a>Gestion des utilisateurs

À mesure que les groupes et les équipes évoluent au sein de votre organisation, une bonne pratique consiste à examiner régulièrement l’appartenance des équipes et des groupes. Cela peut être particulièrement utile pour les équipes et les groupes dont l’appartenance change, celles qui contiennent des informations sensibles ou celles qui incluent des invités. Envisagez de configurer des révisions d’accès pour ces équipes et groupes :

- [Que sont les révisions d’accès Azure AD ?](/azure/active-directory/governance/access-reviews-overview)

De nombreuses organisations ont des partenariats commerciaux avec d’autres organisations ou fournisseurs clés avec lesquels elles collaborent en profondeur. La gestion des utilisateurs et l’accès aux ressources peuvent être difficiles à gérer dans ces scénarios. Envisagez d’automatiser certaines tâches de gestion des utilisateurs et même de les transférer à votre organisation partenaire :

- [Qu’est-ce que la gestion des droits d’utilisation Azure AD ?](/azure/active-directory/governance/entitlement-management-overview)

Les canaux privés dans Teams permettent des conversations étendues et le partage de fichiers entre un sous-ensemble de membres de l’équipe. En fonction de vos besoins métier spécifiques, vous souhaiterez peut-être autoriser ou bloquer cette fonctionnalité.

- [Canaux privés dans Microsoft Teams](/MicrosoftTeams/private-channels)

Les canaux partagés vous permettent d’inviter des personnes extérieures à l’équipe ou à l’extérieur de l’organisation. En fonction des besoins de votre entreprise et des stratégies de partage externes, vous pouvez autoriser ou bloquer cette fonctionnalité.

- [Canaux partagés](/MicrosoftTeams/shared-channels)

Ressources supplémentaires :

- [Gouvernance des identités Azure Active Directory](/azure/active-directory/governance)

## <a name="related-topics"></a>Voir aussi

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Sécurité et conformité dans Microsoft Teams](/microsoftteams/security-compliance-overview)

[Gérer les paramètres de partage dans SharePoint](/sharepoint/turn-external-sharing-on-or-off)

[Créer et gérer un réseau externe dans Yammer](/yammer/work-with-external-users/create-and-manage-an-external-network)

[Configurer Teams avec trois niveaux de protection](./configure-teams-three-tiers-protection.md)