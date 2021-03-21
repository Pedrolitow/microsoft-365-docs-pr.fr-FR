---
title: Interactions des paramètres entre les groupes Microsoft 365 et SharePoint
ms.reviewer: mmclean
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
description: En savoir plus sur les interactions de paramètres entre les groupes Microsoft 365 et SharePoint
ms.openlocfilehash: e1aeaca792fb551de503bd4c68256ccf14f45022
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50921035"
---
# <a name="settings-interactions-between-microsoft-365-groups-and-sharepoint"></a>Interactions des paramètres entre les groupes Microsoft 365 et SharePoint

Certains paramètres pour les groupes Microsoft 365 et SharePoint dans Microsoft 365, notamment liés au partage et à la création de sites d’équipe et de groupe, se chevauchent. Cet article fournit des descriptions de ces interactions et les meilleures pratiques pour l’utilisation de ces paramètres.

![Diagramme de Venn des fonctionnalités sharePoint, Yammer et de groupes](../media/groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-microsoft-365-groups"></a>Les effets des paramètres SharePoint sur les groupes Microsoft 365

|Paramètre SharePoint|Description|Impact sur les groupes Microsoft 365|Recommandation|
|:-----------------|:----------|:-----------------------------|:-------------|
|Partage externe pour l’organisation et le site|Détermine si les sites, fichiers et dossiers peuvent être partagés avec des personnes extérieures à l’organisation.|Si les paramètres de SharePoint et de groupes ne correspondent pas, il se peut que les invités du groupe ne soient pas en droit d’accéder au site, ou que l’accès externe soit disponible dans le site, mais pas dans le groupe.|Lorsque vous modifiez les paramètres de partage, vérifiez les paramètres de groupes et les paramètres de site SharePoint pour les sites d’équipe connectés à un groupe.<br><br>Voir [Collaborer avec des invités dans un site.](./collaborate-in-site.md)|
|Domaine autoriser/bloquer|Autorise ou empêche le partage de contenu avec des domaines spécifiés.|Les groupes ne reconnaissent pas les listes d’actions SharePoint autoriser ou bloquer. Les utilisateurs de domaines non autorisé dans SharePoint peuvent accéder à SharePoint via un groupe.|Gérez ensemble les listes d’accès/de blocage de domaine pour Azure AD et SharePoint. Créez un processus de gouvernance à l’échelle de l’organisation pour autoriser et bloquer les domaines.<br><br>Voir [paramètres de domaine SharePoint](/sharepoint/restricted-domains-sharing) et paramètres de [domaine Azure AD](/azure/active-directory/b2b/allow-deny-list)|
|Autoriser les utilisateurs dans les groupes de sécurité spécifiques à partager avec l’extérieur|Spécifie les groupes de sécurité qui peuvent partager des sites, des dossiers et des fichiers en externe.|Ce paramètre n’affecte pas les propriétaires de groupe qui partagent des groupes en externe. Les invités de groupe ont accès au site SharePoint associé.||
|Paramètres de partage de site SharePoint|Détermine qui peut partager le site directement en dehors de l’appartenance au groupe. Ceci est configuré par le propriétaire du groupe ou du site.|Ce paramètre n’affecte pas directement le groupe, mais il peut permettre aux utilisateurs d’être ajoutés à un site et de ne pas avoir accès à d’autres ressources de groupe|Envisagez d’utiliser ce paramètre pour limiter le partage du site directement et gérer l’accès au site via le groupe.|
|Laisser les utilisateurs créer des sites à partir de la page d’accueil de SharePoint et de OneDrive|Spécifie si les utilisateurs peuvent créer de nouveaux sites SharePoint.|Si ce paramètre est désactivé, les utilisateurs peuvent toujours créer des sites d’équipe connectés à un groupe en créant un groupe.||

## <a name="the-effects-of-microsoft-365-groups-setting-on-sharepoint"></a>Les effets du paramètre de groupes Microsoft 365 sur SharePoint

|Paramètre des groupes Microsoft 365|Description|Effet sur SharePoint|Recommandation|
|:---------------------------|:----------|:-------------------|:-------------|
|Conventions d’attribution de nom|Spécifie les préfixes et suffixes de nom de groupe, ainsi que les mots bloqués pour la création de groupe|Les stratégies sont appliquées pour les utilisateurs créant des sites d’équipe connectés à un groupe, mais pas pour les sites de communication ou les sites avec d’autres modèles.|Créez des instructions d’attribution de noms distinctes pour les sites de communication si nécessaire.|
|Accès invité de groupe|Spécifie si des personnes extérieures à l’organisation peuvent être ajoutées à des groupes.|Si les paramètres de SharePoint et de groupes ne correspondent pas, il se peut que les invités du groupe ne soient pas en droit d’accéder au site, ou que l’accès externe soit disponible dans le site, mais pas dans le groupe.|Lorsque vous modifiez les paramètres de partage, vérifiez les paramètres de groupes et les paramètres de site SharePoint pour les sites d’équipe connectés à un groupe.<br><br>Voir [Collaborer avec des invités dans un site](./collaborate-in-site.md)|
|Création de groupe par groupe de sécurité|Les groupes peuvent uniquement être créés par les membres d’un groupe de sécurité spécifique.|Les utilisateurs qui ne sont pas membres du groupe de sécurité ne pourront pas créer de site d’équipe connecté à un groupe.|Assurez-vous que votre processus de demande de groupe inclut des instructions pour demander un site.|
|Stratégie d’expiration de groupe|Spécifie une période après laquelle les groupes qui ne sont pas activement utilisés seront automatiquement supprimés.|Lorsque le groupe est supprimé, le site SharePoint associé est également supprimé. Le contenu protégé par les stratégies de rétention est conservé.|Utilisez des stratégies d’expiration pour éviter les problèmes de groupes et de sites inutilisés.|

## <a name="related-topics"></a>Rubriques connexes

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Collaborer avec des personnes extérieures à votre organisation](./collaborate-with-people-outside-your-organization.md)

[Gérer la création de sites dans SharePoint](/sharepoint/manage-site-creation)