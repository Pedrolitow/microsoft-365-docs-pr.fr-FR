---
title: Gouvernance de l’accès Microsoft 365 groupes, Teams et SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: En savoir plus sur la gouvernance de l’accès Microsoft 365 groupes, Teams et SharePoint.
ms.openlocfilehash: 3e0485813a264fe9042e0de9596ba07e50ef72a3
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204300"
---
# <a name="governing-access-in-microsoft-365-groups-teams-and-sharepoint"></a>Gouvernance de l’accès Microsoft 365 groupes, Teams et SharePoint

De nombreux contrôles vous permettent de contrôler la façon dont les utilisateurs accèdent aux ressources dans les groupes, les équipes et les SharePoint. Examinez ces options et réfléchissez à la façon dont elles s’miquent aux besoins de votre entreprise, à la sensibilité de vos données et à l’étendue des personnes avec qui vos utilisateurs doivent collaborer.

Le tableau suivant fournit une référence rapide pour les contrôles d’accès disponibles dans Microsoft 365. Des informations supplémentaires sont fournies dans les sections suivantes.

|Catégorie|Description|Référence|
|:-------|:----------|:--------|
|Appartenance|||
||Découverte d’équipes privées|[Gérer la découverte d’équipes privées dans Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)|
||Appartenance à un groupe dynamique basée sur des règles|[Créer ou mettre à jour un groupe dynamique dans Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)|
||Contrôler qui peut partager des fichiers, des dossiers et des sites.|[Configurer et gérer les demandes d’accès](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)|
|Accès conditionnel|||
||Multi-Factor Authentication|[Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/concept-mfa-howitworks)|
||Contrôler l’accès aux appareils en fonction de la sensibilité au groupe, à l’équipe ou au site.|[Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Limiter l’accès au site pour les appareils non utilisés.|[Contrôler SharePoint’accès à partir d’appareils non utilisés](/sharepoint/control-access-from-unmanaged-devices)|
||Contrôler l’accès au site en fonction de l’emplacement|[Contrôler l’accès aux données SharePoint et OneDrive en fonction de l’emplacement réseau](/sharepoint/control-access-based-on-network-location)|
|Accès invité|||
||Autoriser ou bloquer SharePoint partage à partir de domaines spécifiés.|[Restreindre le partage de contenu SharePoint et OneDrive par domaine](/sharepoint/restricted-domains-sharing)|
||Autoriser ou bloquer l’appartenance à une équipe ou à un groupe à partir de domaines spécifiés.|[Autoriser ou bloquer des invitations à des utilisateurs B2B à partir d’organisations spécifiques](/azure/active-directory/b2b/allow-deny-list)|
||Empêcher le partage anonyme.|[Désactiver les liens Tout le monde](./share-limit-accidental-exposure.md#turn-off-anyone-links)|
||Contrôler les autorisations pour les liens d’accès anonyme.|[Définir des autorisations de lien pour les liens Tout le monde](./best-practices-anonymous-sharing.md#set-link-permissions)|
||Contrôler l’expiration des liens de partage anonyme.|[Définir une date d’expiration pour les liens Tout le monde](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)|
||Contrôler le type de lien de partage affiché aux utilisateurs par défaut.|[Modifier le type de lien par défaut d’un site](/sharepoint/change-default-sharing-link)|
||Limiter le partage externe à des personnes spécifiques.|[Limiter le partage externe aux groupes de sécurité spécifiés](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)|
||Contrôler l’accès invité à un groupe, une équipe ou un site en fonction de la sensibilité des informations.|[Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Désactiver les options de partage.|[Limiter le partage dans Microsoft 365](./microsoft-365-limit-sharing.md)|
|Gestion des utilisateurs|||
||Passer régulièrement en revue l’appartenance aux équipes et aux groupes.|[Que sont les révisions d’accès Azure AD ?](/azure/active-directory/governance/access-reviews-overview)|
||Automatisez la gestion des accès aux groupes et aux équipes.|[Qu’est-ce que la gestion des droits Azure AD ?](/azure/active-directory/governance/entitlement-management-overview)|
||Autoriser ou empêcher les utilisateurs de créer des canaux privés dans Teams.|[Gérer le cycle de vie des canaux privés dans Microsoft Teams](/MicrosoftTeams/private-channels-life-cycle-management)|

## <a name="membership"></a>Appartenance

L’appartenance aux équipes et aux groupes est contrôlée par les propriétaires. Les membres peuvent inviter d’autres personnes, mais les invitations sont envoyées aux propriétaires pour approbation. Bien que les équipes et groupes publics soient découvrables par tous les membres de l’organisation, vous pouvez contrôler si les équipes et groupes privés sont découvrables :

- [Gérer la découverte d’équipes privées dans Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)

Vous pouvez gérer l’appartenance d’un groupe ou d’une équipe dynamiquement en fonction de certains critères, tels que le service. Dans ce cas, les membres et les propriétaires ne peuvent pas inviter des personnes à l’équipe. Les groupes dynamiques utilisent les métadonnées que vous Azure Active Directory pour contrôler qui est membre du groupe. Assurez-vous que les métadonnées que vous utilisez sont complètes et à jour, car des métadonnées incorrectes peuvent entraîner l’ajout d’utilisateurs en dehors des groupes ou d’utilisateurs incorrects.

- [Créer ou mettre à jour un groupe dynamique dans Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

SharePoint sites permettent d’ajouter des propriétaires, des membres et des visiteurs en dehors de l’appartenance à un groupe ou à une équipe. En fonction de vos besoins, vous pouvez limiter les personnes qui peuvent inviter des personnes sur le site. En outre, en fonction de la sensibilité des informations dans un site donné, vous pouvez restreindre les personnes qui peuvent partager des fichiers et des dossiers. Ces restrictions sont configurées par l’équipe, le groupe ou le propriétaire du site :

- [Configurer et gérer les demandes d’accès](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)


## <a name="conditional-access"></a>Accès conditionnel

Avec Microsoft 365, vous pouvez exiger une authentification multifacteur pour les personnes à l’intérieur et à l’extérieur de votre organisation. Il existe de nombreuses options dans les circonstances où les utilisateurs sont invités à retentifier un second facteur d’authentification. Nous vous recommandons vivement de déployer l’authentification multifacteur pour votre organisation :

- [Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/concept-mfa-howitworks)

Si vous avez des informations sensibles dans certains de vos groupes et équipes, vous pouvez appliquer des stratégies de gestion des appareils en fonction de l’étiquette de confidentialité d’un groupe ou d’une équipe. Vous pouvez bloquer entièrement l’accès à partir d’appareils nonmanagés ou autoriser un accès limité au web uniquement :

- [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)

Dans SharePoint, vous pouvez restreindre l’accès aux sites à partir d’emplacements réseau spécifiés.

- [Contrôler l’accès aux données SharePoint et OneDrive en fonction de l’emplacement réseau](/sharepoint/control-access-based-on-network-location)


Ressources supplémentaires :

- [Planifier un déploiement d’accès conditionnel](/azure/active-directory/conditional-access/plan-conditional-access)

- [Microsoft Intune vue d’ensemble](/mem/intune/fundamentals/what-is-intune)

- [Contrôler SharePoint’accès à partir d’appareils non utilisés](/sharepoint/control-access-from-unmanaged-devices)


## <a name="guest-access"></a>Accès invité

Vous pouvez restreindre les invités en fonction du domaine de leur adresse de messagerie. SharePoint offre des paramètres de restriction de domaine propres à l’organisation et au site. Les groupes et Teams utiliser les listes d’autoriser et de refuser de domaine dans Azure AD. Veillez à configurer les deux paramètres pour éviter le partage indésirable et garantir une expérience utilisateur cohérente :

- [Restreindre le partage de contenu SharePoint et OneDrive par domaine](/sharepoint/restricted-domains-sharing)

- [Autoriser ou bloquer des invitations à des utilisateurs B2B à partir d’organisations spécifiques](/azure/active-directory/b2b/allow-deny-list)

Microsoft 365 permet le partage anonyme de fichiers et de dossiers à l’aide de liens de partage *Tout le* monde. *Tous les* liens peuvent être transmis et toute personne ayant le lien peut accéder à l’élément partagé. En fonction de la sensibilité de vos  données, envisagez de régir la façon dont les liens Tout le monde sont utilisés, y compris de les éteindre entièrement, de restreindre les autorisations de lien en lecture seule ou de définir un délai d’expiration pour eux :

- [Désactiver les liens Tout le monde](./share-limit-accidental-exposure.md#turn-off-anyone-links)

- [Définir des autorisations de lien pour les liens Tout le monde](./best-practices-anonymous-sharing.md#set-link-permissions)

- [Définir une date d’expiration pour les liens Tout le monde](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)

Lors du partage de fichiers ou de dossiers, les utilisateurs peuvent choisir parmi plusieurs types de liens. Pour réduire le risque de partage inapproprié accidentel, vous pouvez modifier le type de lien par défaut présenté aux utilisateurs lorsqu’ils partagent. Par exemple, la modification de la valeur par  défaut des liens *Tout* le monde (qui autorisent l’accès anonyme) vers les liens des personnes de votre organisation peut réduire le risque de partage externe indésirable d’informations sensibles :

- [Modifier le type de lien par défaut d’un site](/sharepoint/change-default-sharing-link)

Si votre organisation dispose de données sensibles que vous devez partager avec des invités, mais que vous êtes préoccupé par le partage inapproprié, vous pouvez limiter le partage externe de fichiers et de dossiers aux membres des groupes de sécurité spécifiés. De cette façon, vous pouvez restreindre le partage en externe à un groupe spécifique de personnes ou demander à vos utilisateurs de prendre des formations sur le partage externe approprié avant de les ajouter au groupe de sécurité :

- [Limiter le partage externe aux groupes de sécurité spécifiés](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)

Les groupes et Teams ont des paramètres au niveau de l’organisation qui autorisent ou refusent l’accès invité. Bien que vous pouvez restreindre l’accès invité à des équipes ou des groupes spécifiques à l’aide de [Microsoft PowerShell,](per-group-guest-access.md)nous vous recommandons de le faire au moyen d’une étiquette de niveau de sensibilité. Avec les étiquettes de sensibilité, vous pouvez automatiquement autoriser ou refuser l’accès invité en fonction de l’étiquette appliquée :

- [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)

Dans un environnement où vous invitez fréquemment des invités à des groupes et des équipes, envisagez de mettre en place des révisions d’accès invité régulièrement programmées. Les propriétaires peuvent être invités à passer en revue les invités de leurs groupes et équipes, et à approuver ou refuser l’accès.

- [Configurer les révisions d’accès invité](/microsoft-365/solutions/create-secure-guest-sharing-environment#set-up-guest-access-reviews)

Microsoft 365 offre de nombreuses méthodes de partage d’informations. Si vous avez des informations sensibles et que vous souhaitez limiter la façon dont elles sont partagées, examinez les options de limitation du partage :

- [Limiter le partage dans Microsoft 365](./microsoft-365-limit-sharing.md)

Ressources supplémentaires :

- [Configurer la collaboration sécurisée avec Microsoft 365](./setup-secure-collaboration-with-teams.md)

- [Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](./best-practices-anonymous-sharing.md)

- [Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation](./share-limit-accidental-exposure.md)

- [Créer un environnement de partage sécurisé avec des invités](./create-secure-guest-sharing-environment.md)

- [Activer la collaboration externe B2B, puis gérer les utilisateurs pouvant avoir des invités](/azure/active-directory/b2b/delegate-invitations)

## <a name="user-management"></a>Gestion des utilisateurs

À mesure que les groupes et les équipes évoluent dans votre organisation, il est bon de passer régulièrement en revue l’appartenance aux équipes et aux groupes. Cela peut être particulièrement utile pour les équipes et les groupes dont l’appartenance change, celles qui contiennent des informations sensibles ou celles qui incluent des invités. Envisagez de définir des révisions d’accès pour ces équipes et groupes :

- [Que sont les révisions d’accès Azure AD ?](/azure/active-directory/governance/access-reviews-overview)

De nombreuses organisations ont des partenariats commerciaux avec d’autres organisations ou fournisseurs clés avec lesquels elles collaborent en profondeur. La gestion des utilisateurs et l’accès aux ressources peuvent être difficiles à gérer dans ces scénarios. Envisagez d’automatiser certaines tâches de gestion des utilisateurs et même de les faire passer à votre organisation partenaire :

- [Qu’est-ce que la gestion des droits Azure AD ?](/azure/active-directory/governance/entitlement-management-overview)

Les canaux privés Teams autoriser les conversations étendues et le partage de fichiers entre un sous-ensemble de membres de l’équipe. En fonction de vos besoins spécifiques, vous pouvez autoriser ou bloquer cette fonctionnalité.

- [Canaux privés dans Microsoft Teams](/MicrosoftTeams/private-channels)

- [Gérer le cycle de vie des canaux privés dans Microsoft Teams](/MicrosoftTeams/private-channels-life-cycle-management)

Ressources supplémentaires :

- [Azure Active Directory Gouvernance des identités](/azure/active-directory/governance)

## <a name="related-topics"></a>Rubriques connexes

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Sécurité et de la conformité dans Microsoft Teams](/microsoftteams/security-compliance-overview)

[Gérer les paramètres de partage dans SharePoint](/sharepoint/turn-external-sharing-on-or-off)

[Créer et gérer un réseau externe dans Yammer](/yammer/work-with-external-users/create-and-manage-an-external-network)

[Configurer Teams avec trois niveaux de protection](./configure-teams-three-tiers-protection.md)