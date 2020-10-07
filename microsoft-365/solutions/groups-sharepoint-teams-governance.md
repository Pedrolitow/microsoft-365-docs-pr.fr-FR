---
title: Interactions des paramètres entre les groupes Microsoft 365, teams et SharePoint
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
description: En savoir plus sur les interactions de paramètres entre les groupes Microsoft 365, teams et SharePoint
ms.openlocfilehash: 3a6d4e057f88410a8808ea133bf7e579d0041228
ms.sourcegitcommit: 9841058fcc95f7c2fed6af92bc3c3686944829b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "48377544"
---
# <a name="settings-interactions-between-microsoft-365-groups-teams-and-sharepoint"></a>Interactions des paramètres entre les groupes Microsoft 365, teams et SharePoint

Certains paramètres pour les groupes Microsoft 365, Microsoft teams et SharePoint dans Microsoft 365, en particulier ceux liés au partage et à la création de groupe/d’équipe et de site SharePoint, se chevauchent. Cet article décrit ces interactions et les meilleures pratiques relatives à l’utilisation de ces paramètres.

![Diagramme de Venn des fonctionnalités SharePoint, teams et Groups](../media/teams-groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-groups-and-teams"></a>Effets des paramètres SharePoint sur les groupes et les équipes

|Paramètre SharePoint|Description|Effet sur les groupes et les équipes Microsoft 365|Recommandation|
|:-----------------|:----------|:---------------------------------------|:-------------|
|Partage externe pour l’organisation et le site|Détermine si des sites, des fichiers et des dossiers peuvent être partagés avec des personnes extérieures à l’organisation.|Si les paramètres SharePoint, groupes et Teams ne correspondent pas, les invités de l’équipe peuvent ne pas pouvoir accéder au site ou un accès externe inattendu peut se produire.|Lorsque vous modifiez les paramètres de partage, vérifiez les paramètres de groupe, les paramètres de teams et les paramètres de site SharePoint pour les sites d’équipe connectés à un groupe.<br><br> Voir [collaborer avec des invités dans une équipe](https://docs.microsoft.com/microsoft-365/solutions/collaborate-as-team)|
|Bloc autorisé de domaine|Autorise ou empêche le partage de contenu avec des domaines spécifiés.|Les groupes et les équipes ne reconnaissent pas les listes verte ou rouge de SharePoint. Les utilisateurs de domaines non autorisés dans SharePoint peuvent accéder aux sites SharePoint ou au contenu par le biais d’une équipe.|Gérer ensemble les listes d’adresses de domaine autorisées/bloquées pour Azure AD et SharePoint. Créez un processus de gouvernance à l’échelle de l’Organisation pour autoriser et bloquer les domaines.<br><br>Voir paramètres de [domaine SharePoint](https://docs.microsoft.com/sharepoint/restricted-domains-sharing) et [paramètres de domaine Azure ad](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)|
|Autoriser les utilisateurs dans les groupes de sécurité spécifiques à partager avec l’extérieur|Spécifie les groupes de sécurité qui peuvent partager des sites, des dossiers et des fichiers SharePoint de manière externe.|Ce paramètre n’empêche pas les propriétaires d’équipe de partager des équipes de manière externe. Les invités d’équipe ont accès au site SharePoint associé.||
|Paramètres de partage de sites SharePoint|Détermine les personnes qui peuvent partager le site directement en dehors des membres de l’équipe. Cette configuration est configurée par le propriétaire de l’équipe ou du site.|Ce paramètre n’affecte pas directement l’équipe, mais il peut autoriser les utilisateurs à être ajoutés à un site sans avoir accès à l’équipe elle-même ou à d’autres ressources Teams.|Envisagez d’utiliser ce paramètre pour limiter le partage du site directement et gérer l’accès au site par le biais de l’équipe.|
|Autoriser les utilisateurs à créer des sites à partir de la page de démarrage SharePoint et de OneDrive|Indique si les utilisateurs peuvent créer de nouveaux sites SharePoint.|Si ce paramètre est désactivé, les utilisateurs peuvent toujours créer des sites d’équipe connectés à un groupe en créant une équipe.||

## <a name="the-effects-of-groups-settings-on-teams"></a>Effets des paramètres de groupe sur teams

|Paramètre de groupes Microsoft 365|Description|Effet sur teams|Recommandation|
|:---------------------------|:----------|:--------------|:-------------|
|Conventions d’attribution de nom|Spécifie les préfixes de nom de groupe et les suffixes, et les mots bloqués pour la création de groupe|Les stratégies sont appliquées pour les utilisateurs qui créent des équipes.||
|Accès invité de groupe|Indique si les utilisateurs externes à l’organisation peuvent être ajoutés à des groupes.|Si les paramètres de partage des invités des groupes ou des équipes sont désactivés, l’équipe ne peut pas être partagée avec des invités.|Lorsque vous modifiez les paramètres de partage des invités, vérifiez les paramètres des équipes, des groupes et du site SharePoint associé à l’équipe.<br><br> Voir [collaborer avec des invités dans une équipe](https://docs.microsoft.com/microsoft-365/solutions/collaborate-as-team)|
|Création de groupe par groupe de sécurité|Les groupes ne peuvent être créés que par les membres d’un groupe de sécurité spécifique.|Les utilisateurs qui ne sont pas membres du groupe de sécurité ne seront pas en mesure de créer une équipe.|Assurez-vous que votre processus de demande d’un groupe inclut des instructions pour la demande d’une équipe ou d’un site SharePoint.|
|Stratégie d’expiration de groupe|Spécifie une période de temps au terme de laquelle les groupes qui ne sont pas utilisés activement sont automatiquement supprimés.|Lorsque le groupe est supprimé, l’équipe et le site SharePoint associé sont également supprimés. Le contenu protégé par les stratégies de rétention est conservé.|Utilisez des stratégies d’expiration pour éviter la prolifération des équipes, des groupes et des sites inutilisés.|

## <a name="related-topics"></a>Voir aussi

[Collaboration avec des personnes extérieures à votre organisation](https://docs.microsoft.com/microsoft-365/solutions/collaborate-with-people-outside-your-organization)

[Gérer la création de sites dans SharePoint](https://docs.microsoft.com/sharepoint/manage-site-creation)
