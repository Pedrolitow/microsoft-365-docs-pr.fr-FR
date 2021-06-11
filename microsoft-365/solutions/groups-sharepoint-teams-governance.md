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
recommendations: false
description: En savoir plus sur les interactions de paramètres entre Microsoft 365 groupes, Teams et SharePoint
ms.openlocfilehash: 14a21cd34fe38b47d93d0cbcec5e9cb2a3bc49c7
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52539082"
---
# <a name="settings-interactions-between-microsoft-365-groups-teams-and-sharepoint"></a>Paramètres des interactions entre les groupes Microsoft 365, Teams et SharePoint

Certains paramètres de Microsoft 365 Groupes, Microsoft Teams et SharePoint en Microsoft 365, notamment liés au partage et à la création de sites de groupe/équipe et SharePoint, se chevauchent. Cet article fournit des descriptions de ces interactions et les meilleures pratiques pour l’utilisation de ces paramètres.

![Diagramme de Venn des fonctionnalités SharePoint, Teams et des groupes](../media/teams-groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-groups-and-teams"></a>Les effets des paramètres SharePoint sur les groupes et les équipes

|SharePoint paramètre|Description|Impact sur les Microsoft 365 et les Teams|Recommandation|
|:-----------------|:----------|:---------------------------------------|:-------------|
|Partage externe pour l’organisation et le site|Détermine si les sites, fichiers et dossiers peuvent être partagés avec des personnes extérieures à l’organisation.|Si SharePoint, les groupes et les paramètres de Teams ne correspondent pas, les invités de l’équipe peuvent ne pas pouvoir accéder au site ou un accès externe inattendu peut se produire.|Lorsque vous modifiez les paramètres de partage, vérifiez les paramètres de groupes, les paramètres Teams et les paramètres SharePoint de site pour les sites d’équipe connectés à un groupe.<br><br> Voir [Collaborer avec des invités dans une équipe](./collaborate-as-team.md)|
|Domaine autoriser/bloquer|Autorise ou empêche le partage de contenu avec des domaines spécifiés.|Les groupes et Teams ne reconnaissent pas SharePoint listes d’SharePoint ou de blocage. Les utilisateurs de domaines non autorisé dans SharePoint peuvent accéder à des sites SharePoint ou du contenu via une équipe.|Gérez les listes d’accès/de blocage de domaine pour Azure AD et SharePoint ensemble. Créez un processus de gouvernance à l’échelle de l’organisation pour autoriser et bloquer les domaines.<br><br>Voir SharePoint de domaine et les [paramètres](/sharepoint/restricted-domains-sharing) de [domaine Azure AD](/azure/active-directory/b2b/allow-deny-list)|
|Autoriser les utilisateurs dans les groupes de sécurité spécifiques à partager avec l’extérieur|Spécifie les groupes de sécurité qui peuvent partager SharePoint sites, dossiers et fichiers en externe.|Ce paramètre n’empêche pas les propriétaires d’équipe de partager des équipes en externe. Les invités d’équipe ont accès au site SharePoint associé.||
|SharePoint de partage de site|Détermine qui peut partager le site directement en dehors de l’appartenance à l’équipe. Cette configuration est configurée par l’équipe ou le propriétaire du site.|Ce paramètre n’affecte pas directement l’équipe, mais il peut permettre aux utilisateurs d’être ajoutés à un site et de ne pas avoir accès à l’équipe elle-même ou à d’Teams ressources|Envisagez d’utiliser ce paramètre pour limiter le partage du site directement et gérer l’accès au site par le biais de l’équipe.|
|Permet aux utilisateurs de créer des sites à partir SharePoint page de démarrage et de OneDrive|Spécifie si les utilisateurs peuvent créer des sites SharePoint sites.|Si ce paramètre est désactivé, les utilisateurs peuvent toujours créer des sites d’équipe connectés à un groupe en créant une équipe.||

## <a name="the-effects-of-groups-settings-on-teams"></a>Les effets des paramètres de groupes sur les équipes

|Microsoft 365 groupes|Description|Effet sur les Teams|Recommandation|
|:---------------------------|:----------|:--------------|:-------------|
|Conventions d’attribution de nom|Spécifie les préfixes et suffixes de nom de groupe, ainsi que les mots bloqués pour la création de groupe|Les stratégies sont appliquées pour les utilisateurs qui créent des équipes.||
|Accès invité de groupe|Spécifie si des personnes extérieures à l’organisation peuvent être ajoutées à des groupes.|Si les groupes ou les Teams de partage d’invités sont éteints, l’équipe ne peut pas être partagée avec des invités.|Lorsque vous modifiez les paramètres de partage d’invités, vérifiez les paramètres des Teams, des groupes et du site SharePoint associé à l’équipe.<br><br> Voir [Collaborer avec des invités dans une équipe](./collaborate-as-team.md)|
|Création de groupe par groupe de sécurité|Les groupes peuvent uniquement être créés par les membres d’un groupe de sécurité spécifique.|Les utilisateurs qui ne sont pas membres du groupe de sécurité ne pourront pas créer d’équipe.|Assurez-vous que le processus de demande d’un groupe inclut des instructions pour demander une équipe ou un site SharePoint site.|
|Stratégie d’expiration de groupe|Spécifie une période après laquelle les groupes qui ne sont pas activement utilisés seront automatiquement supprimés.|Lorsque le groupe est supprimé, l’équipe et SharePoint site sont également supprimés. Le contenu protégé par les stratégies de rétention est conservé.|Utilisez des stratégies d’expiration pour éviter les problèmes d’équipes, de groupes et de sites inutilisés.|

## <a name="related-topics"></a>Voir aussi

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Collaborer avec des personnes extérieures à votre organisation](./collaborate-with-people-outside-your-organization.md)

[Gérer la création de sites dans SharePoint](/sharepoint/manage-site-creation)