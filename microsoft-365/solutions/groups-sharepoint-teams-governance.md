---
title: Paramètres des interactions entre les groupes Microsoft 365, Teams et SharePoint
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
description: En savoir plus sur les interactions de paramètres entre les groupes Microsoft 365, Teams et SharePoint
ms.openlocfilehash: 23ef7a316417109ae51c221f1a25524dea3abeca
ms.sourcegitcommit: a0cddd1f888edb940717e434cda2dbe62e5e9475
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49613665"
---
# <a name="settings-interactions-between-microsoft-365-groups-teams-and-sharepoint"></a>Paramètres des interactions entre les groupes Microsoft 365, Teams et SharePoint

Certains paramètres pour les groupes Microsoft 365, Microsoft Teams et SharePoint dans Microsoft 365, notamment liés au partage et à la création de groupes/équipes et de sites SharePoint, se chevauchent. Cet article fournit des descriptions de ces interactions et les meilleures pratiques pour l’utilisation de ces paramètres.

![Diagramme de Venn des fonctionnalités SharePoint, Teams et groupes](../media/teams-groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-groups-and-teams"></a>Les effets des paramètres SharePoint sur les groupes et les équipes

|Paramètre SharePoint|Description|Impact sur les groupes Microsoft 365 et Teams|Recommandation|
|:-----------------|:----------|:---------------------------------------|:-------------|
|Partage externe pour l’organisation et le site|Détermine si les sites, fichiers et dossiers peuvent être partagés avec des personnes extérieures à l’organisation.|Si SharePoint, les groupes et les paramètres Teams ne correspondent pas, les invités de l’équipe peuvent être bloqués pour accéder au site ou un accès externe inattendu peut se produire.|Lorsque vous modifiez les paramètres de partage, vérifiez les paramètres des groupes, des paramètres Teams et des paramètres de site SharePoint pour les sites d’équipe connectés à un groupe.<br><br> Voir [Collaborer avec des invités dans une équipe](https://docs.microsoft.com/microsoft-365/solutions/collaborate-as-team)|
|Domaine autoriser/bloquer|Autorise ou empêche le partage de contenu avec des domaines spécifiés.|Les groupes et Teams ne reconnaissent pas les listes d’autoriser ou de bloquer SharePoint. Les utilisateurs de domaines non autorisé dans SharePoint peuvent accéder aux sites ou au contenu SharePoint par le biais d’une équipe.|Gérez ensemble les listes d’accès/de blocage de domaine pour Azure AD et SharePoint. Créez un processus de gouvernance à l’échelle de l’organisation pour autoriser et bloquer les domaines.<br><br>Voir [paramètres de domaine SharePoint](https://docs.microsoft.com/sharepoint/restricted-domains-sharing) et paramètres de [domaine Azure AD](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)|
|Autoriser les utilisateurs dans les groupes de sécurité spécifiques à partager avec l’extérieur|Spécifie les groupes de sécurité qui peuvent partager des sites, des dossiers et des fichiers SharePoint en externe.|Ce paramètre n’empêche pas les propriétaires d’équipe de partager des équipes en externe. Les invités d’équipe ont accès au site SharePoint associé.||
|Paramètres de partage de site SharePoint|Détermine qui peut partager le site directement en dehors de l’appartenance à l’équipe. Cette configuration est configurée par l’équipe ou le propriétaire du site.|Ce paramètre n’affecte pas directement l’équipe, mais il peut permettre aux utilisateurs d’être ajoutés à un site et de ne pas avoir accès à l’équipe elle-même ou à d’autres ressources Teams|Envisagez d’utiliser ce paramètre pour limiter le partage du site directement et gérer l’accès au site par le biais de l’équipe.|
|Laisser les utilisateurs créer des sites à partir de la page d’accueil de SharePoint et de OneDrive|Spécifie si les utilisateurs peuvent créer de nouveaux sites SharePoint.|Si ce paramètre est désactivé, les utilisateurs peuvent toujours créer des sites d’équipe connectés à un groupe en créant une équipe.||

## <a name="the-effects-of-groups-settings-on-teams"></a>Les effets des paramètres de groupes sur les équipes

|Paramètre des groupes Microsoft 365|Description|Impact sur Teams|Recommandation|
|:---------------------------|:----------|:--------------|:-------------|
|Conventions d’attribution de nom|Spécifie les préfixes et suffixes de nom de groupe, ainsi que les mots bloqués pour la création de groupe|Les stratégies sont appliquées pour les utilisateurs qui créent des équipes.||
|Accès invité de groupe|Spécifie si des personnes extérieures à l’organisation peuvent être ajoutées à des groupes.|Si les groupes ou les paramètres de partage d’invités Teams sont hors de l’équipe, l’équipe ne peut pas être partagée avec des invités.|Lorsque vous modifiez les paramètres de partage d’invités, vérifiez les paramètres pour Teams, les groupes et le site SharePoint associé à l’équipe.<br><br> Voir [Collaborer avec des invités dans une équipe](https://docs.microsoft.com/microsoft-365/solutions/collaborate-as-team)|
|Création de groupe par groupe de sécurité|Les groupes peuvent uniquement être créés par les membres d’un groupe de sécurité spécifique.|Les utilisateurs qui ne sont pas membres du groupe de sécurité ne pourront pas créer d’équipe.|Assurez-vous que votre processus de demande de groupe inclut des instructions pour demander une équipe ou un site SharePoint.|
|Stratégie d’expiration de groupe|Spécifie une période après laquelle les groupes qui ne sont pas activement utilisés seront automatiquement supprimés.|Lorsque le groupe est supprimé, l’équipe et le site SharePoint associé sont également supprimés. Le contenu protégé par les stratégies de rétention est conservé.|Utilisez des stratégies d’expiration pour éviter les problèmes d’équipes, de groupes et de sites inutilisés.|

## <a name="related-topics"></a>Rubriques connexes

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Collaborer avec des personnes extérieures à votre organisation](https://docs.microsoft.com/microsoft-365/solutions/collaborate-with-people-outside-your-organization)

[Gérer la création de sites dans SharePoint](https://docs.microsoft.com/sharepoint/manage-site-creation)
