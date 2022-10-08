---
title: Paramètres des interactions entre les groupes Microsoft 365, Teams et SharePoint
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
description: En savoir plus sur les interactions de paramètres entre Groupes Microsoft 365, Teams et SharePoint
ms.openlocfilehash: 6d66b7e84d922108e83e8fa3e045272c82fd8f51
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67986331"
---
# <a name="settings-interactions-between-microsoft-365-groups-teams-and-sharepoint"></a>Paramètres des interactions entre les groupes Microsoft 365, Teams et SharePoint

Certains paramètres pour Groupes Microsoft 365, Microsoft Teams et SharePoint dans Microsoft 365, en particulier liés au partage et à la création de groupes/d’équipes et de sites SharePoint, se chevauchent. Cet article fournit des descriptions de ces interactions et des meilleures pratiques pour l’utilisation de ces paramètres.

![Diagramme venn des fonctionnalités SharePoint, Teams et des groupes.](../media/teams-groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-groups-and-teams"></a>Effets des paramètres SharePoint sur les groupes et les équipes

|Paramètre SharePoint|Description|Effet sur les groupes Microsoft 365 et Teams|Recommandation|
|:-----------------|:----------|:---------------------------------------|:-------------|
|Partage externe pour l’organisation et le site|Détermine si les sites, fichiers et dossiers peuvent être partagés avec des personnes extérieures à l’organisation.|Si les paramètres SharePoint, groupes et Teams ne correspondent pas, les invités de l’équipe peuvent être bloqués pour accéder au site, ou un accès externe inattendu peut se produire.|Lors de la modification des paramètres de partage, vérifiez les paramètres des groupes, des paramètres Teams et des paramètres de site SharePoint pour les sites d’équipe connectés à un groupe.<br><br> Voir [Collaborer avec des invités dans une équipe](./collaborate-as-team.md)|
|Autorisation/bloc de domaine|Autorise ou empêche le partage de contenu avec des domaines spécifiés.|Les groupes et Teams ne reconnaissent pas les listes d’autorisation ou les listes de blocage SharePoint. Les utilisateurs de domaines non autorisés dans SharePoint peuvent accéder à des sites ou du contenu SharePoint par le biais d’une équipe.|Gérez ensemble les listes d’autorisations de domaine ou les listes de blocage pour Azure AD et SharePoint. Créez un processus de gouvernance à l’échelle de l’organisation pour autoriser et bloquer des domaines.<br><br>Voir [les paramètres de domaine SharePoint et les](/sharepoint/restricted-domains-sharing) [paramètres de domaine Azure AD](/azure/active-directory/b2b/allow-deny-list)|
|Autoriser les utilisateurs de groupes de sécurité spécifiques à partager en externe|Spécifie les groupes de sécurité qui peuvent partager des sites, des dossiers et des fichiers SharePoint en externe.|Ce paramètre n’empêche pas les propriétaires d’équipe de partager des équipes en externe. Les invités d’équipe ont accès au site SharePoint associé.||
|Paramètres de partage de site SharePoint|Détermine qui peut partager le site directement en dehors de l’appartenance à l’équipe. Ceci est configuré par l’équipe ou le propriétaire du site.|Ce paramètre n’affecte pas directement l’équipe, mais il peut permettre aux utilisateurs d’être ajoutés à un site et de ne pas avoir accès à l’équipe elle-même ou à d’autres ressources Teams.|Envisagez d’utiliser ce paramètre pour limiter le partage du site directement et gérer l’accès au site via l’équipe.|
|Permettre aux utilisateurs de créer des sites à partir de la page de démarrage SharePoint et de OneDrive|Spécifie si les utilisateurs peuvent créer des sites SharePoint.|Si ce paramètre est désactivé, les utilisateurs peuvent toujours créer des sites d’équipe connectés à un groupe en créant une équipe.||

## <a name="the-effects-of-groups-settings-on-teams"></a>Effets des paramètres de groupes sur les équipes

|Paramètre des groupes Microsoft 365|Description|Effet sur Teams|Recommandation|
|:---------------------------|:----------|:--------------|:-------------|
|Conventions d’attribution de nom|Spécifie les préfixes et suffixes de nom de groupe et les mots bloqués pour la création de groupe|Les stratégies sont appliquées pour les utilisateurs qui créent des équipes.||
|Accès invité de groupe|Spécifie si des personnes extérieures à l’organisation peuvent être ajoutées à des groupes.|Si les paramètres de partage d’invités ou de groupes sont désactivés, l’équipe ne peut pas être partagée avec les invités.|Lorsque vous modifiez les paramètres de partage d’invités, vérifiez les paramètres pour Teams, les groupes et le site SharePoint associé à l’équipe.<br><br> Voir [Collaborer avec des invités dans une équipe](./collaborate-as-team.md)|
|Création de groupes par groupe de sécurité|Les groupes ne peuvent être créés que par des membres d’un groupe de sécurité spécifique.|Les utilisateurs qui ne sont pas membres du groupe de sécurité ne pourront pas créer d’équipe.|Assurez-vous que votre processus de demande d’un groupe inclut des instructions pour demander une équipe ou un site SharePoint.|
|Stratégie d’expiration de groupe|Spécifie une période après laquelle les groupes qui ne sont pas utilisés activement seront automatiquement supprimés.|Lorsque le groupe est supprimé, l’équipe et le site SharePoint associé sont également supprimés. Le contenu protégé par des stratégies de rétention est conservé.|Utilisez des stratégies d’expiration pour éviter la prolifération d’équipes, de groupes et de sites inutilisés.|

## <a name="related-topics"></a>Voir aussi

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Collaborer avec des personnes extérieures à votre organisation](./collaborate-with-people-outside-your-organization.md)

[Gérer la création de sites dans SharePoint](/sharepoint/manage-site-creation)