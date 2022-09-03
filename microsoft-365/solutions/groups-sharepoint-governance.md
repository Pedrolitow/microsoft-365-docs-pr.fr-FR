---
title: Interactions de paramètres entre Groupes Microsoft 365 et SharePoint
ms.reviewer: mmclean
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: En savoir plus sur les interactions de paramètres entre Groupes Microsoft 365 et SharePoint
ms.openlocfilehash: 8b17a868c31273a1e2ec4c5c8b8fbda8a59ef273
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67579598"
---
# <a name="settings-interactions-between-microsoft-365-groups-and-sharepoint"></a>Interactions de paramètres entre Groupes Microsoft 365 et SharePoint

Certains paramètres pour Groupes Microsoft 365 et SharePoint dans Microsoft 365, en particulier liés au partage et à la création de sites de groupe et d’équipe, se chevauchent. Cet article fournit des descriptions de ces interactions et des meilleures pratiques pour l’utilisation de ces paramètres.

![Diagramme venn des fonctionnalités SharePoint, Yammer et des groupes.](../media/groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-microsoft-365-groups"></a>Effets des paramètres SharePoint sur les groupes Microsoft 365

|Paramètre SharePoint|Description|Effet sur les groupes Microsoft 365|Recommandation|
|:-----------------|:----------|:-----------------------------|:-------------|
|Partage externe pour l’organisation et le site|Détermine si les sites, fichiers et dossiers peuvent être partagés avec des personnes extérieures à l’organisation.|Si les paramètres SharePoint et les groupes ne correspondent pas, les invités du groupe peuvent être bloqués d’accéder au site, ou l’accès externe peut être disponible dans le site, mais pas dans le groupe.|Lors de la modification des paramètres de partage, vérifiez les paramètres des groupes et des sites SharePoint pour les sites d’équipe connectés à un groupe.<br><br>Voir [Collaborer avec des invités dans un site](./collaborate-in-site.md).|
|Autorisation/bloc de domaine|Autorise ou empêche le partage de contenu avec des domaines spécifiés.|Les groupes ne reconnaissent pas les listes d’autorisation ou les listes de blocage SharePoint. Les utilisateurs de domaines non autorisés dans SharePoint peuvent accéder à SharePoint via un groupe.|Gérez ensemble les listes d’autorisations de domaine ou les listes de blocage pour Azure AD et SharePoint. Créez un processus de gouvernance à l’échelle de l’organisation pour autoriser et bloquer des domaines.<br><br>Voir [les paramètres de domaine SharePoint et les](/sharepoint/restricted-domains-sharing) [paramètres de domaine Azure AD](/azure/active-directory/b2b/allow-deny-list)|
|Autoriser les utilisateurs de groupes de sécurité spécifiques à partager en externe|Spécifie les groupes de sécurité qui peuvent partager des sites, des dossiers et des fichiers en externe.|Ce paramètre n’affecte pas les propriétaires de groupes qui partagent des groupes en externe. Les invités de groupe ont accès au site SharePoint associé.||
|Paramètres de partage de site SharePoint|Détermine qui peut partager le site directement en dehors de l’appartenance au groupe. Ceci est configuré par le propriétaire du groupe ou du site.|Ce paramètre n’affecte pas directement le groupe, mais il peut permettre aux utilisateurs d’être ajoutés à un site et de ne pas avoir accès à d’autres ressources de groupe.|Envisagez d’utiliser ce paramètre pour limiter le partage du site directement et gérer l’accès au site via le groupe.|
|Permettre aux utilisateurs de créer des sites à partir de la page de démarrage SharePoint et de OneDrive|Spécifie si les utilisateurs peuvent créer des sites SharePoint.|Si ce paramètre est désactivé, les utilisateurs peuvent toujours créer des sites d’équipe connectés à un groupe en créant un groupe.||

## <a name="the-effects-of-microsoft-365-groups-setting-on-sharepoint"></a>Effets de la définition des groupes Microsoft 365 sur SharePoint

|Paramètre des groupes Microsoft 365|Description|Effet sur SharePoint|Recommandation|
|:---------------------------|:----------|:-------------------|:-------------|
|Conventions d’attribution de nom|Spécifie les préfixes et suffixes de nom de groupe et les mots bloqués pour la création de groupe|Les stratégies sont appliquées pour les utilisateurs qui créent des sites d’équipe connectés à un groupe, mais pas pour les sites de communication ou les sites avec d’autres modèles.|Si nécessaire, créez des instructions de nommage distinctes pour les sites de communication.|
|Accès invité de groupe|Spécifie si des personnes extérieures à l’organisation peuvent être ajoutées à des groupes.|Si les paramètres SharePoint et les groupes ne correspondent pas, les invités du groupe peuvent être bloqués d’accéder au site, ou l’accès externe peut être disponible dans le site, mais pas dans le groupe.|Lors de la modification des paramètres de partage, vérifiez les paramètres des groupes et des sites SharePoint pour les sites d’équipe connectés à un groupe.<br><br>Voir [Collaborer avec des invités dans un site](./collaborate-in-site.md)|
|Création de groupes par groupe de sécurité|Les groupes ne peuvent être créés que par des membres d’un groupe de sécurité spécifique.|Les utilisateurs qui ne sont pas membres du groupe de sécurité ne pourront pas créer de site d’équipe connecté à un groupe.|Assurez-vous que votre processus de demande d’un groupe inclut des instructions pour demander un site.|
|Stratégie d’expiration de groupe|Spécifie une période après laquelle les groupes qui ne sont pas utilisés activement seront automatiquement supprimés.|Lorsque le groupe est supprimé, le site SharePoint associé est également supprimé. Le contenu protégé par des stratégies de rétention est conservé.|Utilisez des stratégies d’expiration pour éviter la prolifération de groupes et de sites inutilisés.|

## <a name="related-topics"></a>Voir aussi

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Collaborer avec des personnes extérieures à votre organisation](./collaborate-with-people-outside-your-organization.md)

[Gérer la création de sites dans SharePoint](/sharepoint/manage-site-creation)