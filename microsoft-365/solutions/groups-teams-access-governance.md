---
title: Administration des accès dans les groupes Microsoft 365, teams et SharePoint
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
description: Découvrez comment régir l’accès dans les groupes Microsoft 365, teams et SharePoint.
ms.openlocfilehash: ec4e62f4d77b9aadbdc7457631ac1c4b498221c3
ms.sourcegitcommit: 9841058fcc95f7c2fed6af92bc3c3686944829b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "48377568"
---
# <a name="governing-access-in-microsoft-365-groups-teams-and-sharepoint"></a>Administration des accès dans les groupes Microsoft 365, teams et SharePoint

De nombreux contrôles vous permettent de contrôler la manière dont les utilisateurs accèdent aux ressources dans des groupes, des équipes et de SharePoint. Passez en revue ces options et réfléchissez à la façon dont elles correspondent à vos besoins professionnels, à la sensibilité de vos données et à l’étendue des personnes avec lesquelles vos utilisateurs doivent collaborer.

Le tableau suivant fournit un guide de référence rapide pour les contrôles d’accès disponibles dans Microsoft 365. Pour plus d’informations, reportez-vous aux sections suivantes.

|Catégorie|Description|Référence|
|:-------|:----------|:--------|
|Appartenance|||
||Découverte de teams privées|[Gestion de la découverte de teams privées dans Microsoft teams](https://docs.microsoft.com/microsoftteams/manage-discovery-of-private-teams)|
||Appartenance à un groupe dynamique basée sur des règles|[Créer ou mettre à jour un groupe dynamique dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-create-rule)|
||Contrôlez les personnes qui peuvent partager des fichiers, des dossiers et des sites.|[Configurer et gérer les demandes d’accès](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)|
|Accès conditionnel|||
||Authentification multifacteur|[Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)|
||Contrôler l’accès aux périphériques en fonction de la sensibilité du groupe, de l’équipe ou du site.|[Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)|
||Limitez l’accès au site pour les appareils non gérés.|[Contrôler l’accès à SharePoint à partir d’appareils non gérés](https://docs.microsoft.com/sharepoint/control-access-from-unmanaged-devices)|
||Contrôler l’accès au site en fonction de l’emplacement|[Contrôler l’accès aux données SharePoint et OneDrive en fonction de l’emplacement réseau](https://docs.microsoft.com/sharepoint/control-access-based-on-network-location)|
|Accès invité|||
||Autoriser ou bloquer le partage SharePoint à partir de domaines spécifiés.|[Restreindre le partage de contenu SharePoint et OneDrive par domaine](https://docs.microsoft.com/sharepoint/restricted-domains-sharing)|
||Autoriser ou bloquer l’appartenance d’une équipe ou d’un groupe à des domaines spécifiés.|[Autoriser ou bloquer des invitations à des utilisateurs B2B d’organisations spécifiques](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)|
||Empêcher le partage anonyme.|[Désactiver les liens Tout le monde](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure#turn-off-anyone-links)|
||Contrôler les autorisations pour les liens d’accès anonyme.|[Définir les autorisations de liens pour tous les liens](https://docs.microsoft.com/microsoft-365/solutions/best-practices-anonymous-sharing#set-link-permissions)|
||Contrôler l’expiration des liens de partage anonyme.|[Définir une date d’expiration pour les liens Tout le monde](https://docs.microsoft.com/microsoft-365/solutions/best-practices-anonymous-sharing#set-an-expiration-date-for-anyone-links)|
||Contrôler le type de lien de partage affiché par défaut aux utilisateurs.|[Modifier le type de lien par défaut d’un site](https://docs.microsoft.com/sharepoint/change-default-sharing-link)|
||Limitez le partage externe à des personnes spécifiques.|[Limiter le partage externe aux groupes de sécurité spécifiés](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)|
||Contrôler l’accès invité à un groupe, une équipe ou un site en fonction de la sensibilité aux informations.|[Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)|
||Désactivez les options de partage.|[Limiter le partage dans Microsoft 365](https://docs.microsoft.com/microsoft-365/solutions/microsoft-365-limit-sharing)|
|Gestion des utilisateurs|||
||Examinez les membres de l’équipe et du groupe régulièrement.|[Qu’est-ce que les révisions Azure AD Access ?](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overview)|
||Automatiser la gestion des accès aux groupes et aux équipes.|[Qu’est-ce que la gestion des droits Azure AD ?](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview)|
||Autoriser ou empêcher des personnes de créer des canaux privés dans Teams.|[Gérer le cycle de vie des canaux privés dans Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/private-channels-life-cycle-management)|

## <a name="membership"></a>Appartenance

L’appartenance aux équipes et aux groupes est contrôlée par les propriétaires. Les membres peuvent inviter d’autres personnes, mais les invitations sont envoyées aux propriétaires pour approbation. Bien que les groupes et les équipes publiques soient détectables par tous les utilisateurs de l’organisation, vous pouvez contrôler si des équipes et des groupes privés sont détectables :

- [Gestion de la découverte de teams privées dans Microsoft teams](https://docs.microsoft.com/microsoftteams/manage-discovery-of-private-teams)

Vous pouvez gérer l’appartenance d’un groupe ou d’une équipe de manière dynamique en fonction de certains critères, tels que le service. Dans ce cas, les membres et les propriétaires ne peuvent pas inviter des personnes à l’équipe.

- [Créer ou mettre à jour un groupe dynamique dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-create-rule)

Les sites SharePoint offrent la possibilité d’ajouter des propriétaires, des membres et des visiteurs indépendamment de l’appartenance à un groupe ou d’une équipe. En fonction de vos besoins, vous pouvez décider qui peut inviter des personnes sur le site. En outre, en fonction de la sensibilité des informations d’un site donné, vous pouvez limiter les personnes qui peuvent partager des fichiers et des dossiers. Ces restrictions sont configurées par le propriétaire de l’équipe, du groupe ou du site :

- [Configurer et gérer les demandes d’accès](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)


## <a name="conditional-access"></a>Accès conditionnel

Avec Microsoft 365, vous pouvez exiger l’authentification multifacteur pour les deux personnes à l’intérieur et à l’extérieur de votre organisation. Il existe de nombreuses options pour les circonstances dans lesquelles les utilisateurs sont invités à spécifier un deuxième facteur d’authentification. Nous vous recommandons vivement de déployer l’authentification multifacteur pour votre organisation :

- [Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

Si vous avez des informations sensibles dans certains de vos groupes et équipes, vous pouvez appliquer des stratégies de gestion des appareils en fonction de l’étiquette de confidentialité d’une équipe ou d’un groupe. Vous pouvez bloquer l’accès à partir d’appareils non gérés ou accorder un accès limité au Web uniquement :

- [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)

Dans SharePoint, vous pouvez restreindre l’accès aux sites à partir des emplacements réseau spécifiés.

- [Contrôler l’accès aux données SharePoint et OneDrive en fonction de l’emplacement réseau](https://docs.microsoft.com/sharepoint/control-access-based-on-network-location)


Ressources supplémentaires :

- [Planifier un déploiement d’accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/plan-conditional-access)

- [Vue d’ensemble de Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune)

- [Contrôler l’accès à SharePoint à partir d’appareils non gérés](https://docs.microsoft.com/sharepoint/control-access-from-unmanaged-devices)


## <a name="guest-access"></a>Accès invité

Vous pouvez restreindre les invités en fonction du domaine de leur adresse de messagerie. SharePoint propose des paramètres de restriction de domaine spécifiques à l’échelle de l’organisation et de votre site. Les groupes et les équipes utilisent les listes d’autorisation et de refus de domaine dans Azure AD. Veillez à configurer les deux paramètres pour éviter un partage indésirable et garantir une expérience utilisateur cohérente :

- [Restreindre le partage de contenu SharePoint et OneDrive par domaine](https://docs.microsoft.com/sharepoint/restricted-domains-sharing)

- [Autoriser ou bloquer des invitations à des utilisateurs B2B d’organisations spécifiques](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)

Microsoft 365 autorise le partage anonyme de fichiers et de dossiers *à l’aide* de liens de partage. Les liens *tout le monde* peuvent être transférés et quiconque disposant du lien peut accéder à l’élément partagé. En fonction de la sensibilité de vos données, vous devez prendre en compte le mode d’utilisation des liens *tout le monde* , notamment leur désactivation complète, la restriction des autorisations de liaison en lecture seule ou la définition d’un délai d’expiration pour eux :

- [Désactiver les liens Tout le monde](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure#turn-off-anyone-links)

- [Définir les autorisations de liens pour tous les liens](https://docs.microsoft.com/microsoft-365/solutions/best-practices-anonymous-sharing#set-link-permissions)

- [Définir une date d’expiration pour les liens Tout le monde](https://docs.microsoft.com/microsoft-365/solutions/best-practices-anonymous-sharing#set-an-expiration-date-for-anyone-links)

Lors du partage de fichiers ou de dossiers, les utilisateurs ont le choix entre plusieurs types de liens. Pour réduire le risque de partage accidentel inapproprié, vous pouvez modifier le type de lien par défaut présenté aux utilisateurs lorsqu’ils sont partagés. Par exemple, la modification de la valeur par défaut à partir de liens *tout utilisateur* , qui autorise l’accès anonyme à des *personnes dans votre organisation* , permet de réduire le risque de partage externe indésirable d’informations sensibles :

- [Modifier le type de lien par défaut d’un site](https://docs.microsoft.com/sharepoint/change-default-sharing-link)

Si votre organisation a des données sensibles que vous devez partager avec des invités, mais que vous êtes préoccupé par le partage inapproprié, vous pouvez limiter le partage externe des fichiers et des dossiers aux membres des groupes de sécurité spécifiés. De cette manière, vous pouvez limiter le partage externe à un groupe spécifique de personnes ou demander à vos utilisateurs de suivre une formation sur le partage externe approprié avant de les ajouter au groupe de sécurité :

- [Limiter le partage externe aux groupes de sécurité spécifiés](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)

Les groupes et les équipes ont un paramètre au niveau de l’organisation qui autorise ou refuse l’accès invité. Bien que vous puissiez [restreindre l’accès invité à des équipes ou à des groupes spécifiques à l’aide de Microsoft PowerShell](per-group-guest-access.md), nous vous recommandons d’effectuer cette opération par le biais d’une étiquette de sensibilité. Avec les étiquettes de sensibilité, vous pouvez autoriser ou refuser automatiquement l’accès invité en fonction de l’étiquette appliquée :

- [Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)

Microsoft 365 propose de nombreuses méthodes de partage d’informations. Si vous avez des informations sensibles et que vous souhaitez limiter la manière dont elles sont partagées, passez en revue les options permettant de limiter le partage :

- [Limiter le partage dans Microsoft 365](https://docs.microsoft.com/microsoft-365/solutions/microsoft-365-limit-sharing)

Ressources supplémentaires :

- [Configurer la collaboration sécurisée avec Microsoft 365](https://docs.microsoft.com/microsoft-365/solutions/setup-secure-collaboration-with-teams)

- [Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](https://docs.microsoft.com/microsoft-365/solutions/best-practices-anonymous-sharing)

- [Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure)

- [Créer un environnement de partage sécurisé avec des invités](https://docs.microsoft.com/microsoft-365/solutions/create-secure-guest-sharing-environment)

- [Activer la collaboration externe B2B et gérer les personnes autorisées à inviter des invités](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

## <a name="user-management"></a>Gestion des utilisateurs

À mesure que les groupes et les équipes évoluent dans votre organisation, il est recommandé d’examiner régulièrement l’appartenance aux équipes et aux groupes. Cela peut s’avérer particulièrement utile pour les équipes et les groupes qui changent d’appartenance, ceux qui contiennent des informations sensibles ou ceux qui incluent des invités. Envisagez de configurer les révisions d’accès pour ces équipes et ces groupes :

- [Qu’est-ce que les révisions Azure AD Access ?](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overview)

De nombreuses organisations ont des partenariats commerciaux avec d’autres organisations ou fournisseurs clés avec lesquels ils collaborent en profondeur. La gestion des utilisateurs et l’accès aux ressources peuvent être difficiles à gérer dans ces scénarios. Envisagez d’automatiser certaines tâches de gestion des utilisateurs et même de les passer à votre organisation partenaire :

- [Qu’est-ce que la gestion des droits Azure AD ?](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview)

Les canaux privés dans teams autorisent les conversations et le partage de fichiers délimités entre un sous-ensemble de membres d’équipe. En fonction de vos besoins spécifiques, vous pouvez autoriser ou bloquer cette fonctionnalité.

- [Canaux privés dans Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/private-channels)

- [Gérer le cycle de vie des canaux privés dans Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/private-channels-life-cycle-management)

Ressources supplémentaires :

- [Gouvernance d’identité Azure Active Directory](https://docs.microsoft.com/azure/active-directory/governance)

## <a name="related-topics"></a>Voir aussi

[Sécurité et de la conformité dans Microsoft Teams](https://docs.microsoft.com/microsoftteams/security-compliance-overview)

[Gérer les paramètres de partage dans SharePoint](https://docs.microsoft.com/sharepoint/turn-external-sharing-on-or-off)

[Créer et gérer un réseau externe dans Yammer](https://docs.microsoft.com/yammer/work-with-external-users/create-and-manage-an-external-network)

[Configurer Teams avec trois niveaux de protection](https://docs.microsoft.com/microsoft-365/solutions/configure-teams-three-tiers-protection)
