---
title: Paramètres interactions entre les groupes Microsoft 365 et les SharePoint
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
recommendations: false
description: En savoir plus sur les interactions de paramètres entre Microsoft 365 groupes et SharePoint
ms.openlocfilehash: 6f24f18a91e897467a85a31945efe34c78b51db74dd2ffc0aa65322fd936a9ae
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53853046"
---
# <a name="settings-interactions-between-microsoft-365-groups-and-sharepoint"></a>Paramètres interactions entre les groupes Microsoft 365 et les SharePoint

Certains paramètres de Microsoft 365 groupes et de SharePoint dans Microsoft 365, en particulier liés au partage et à la création de sites d’équipe et de groupe, se chevauchent. Cet article fournit des descriptions de ces interactions et les meilleures pratiques pour l’utilisation de ces paramètres.

![Diagramme de Venn des fonctionnalités SharePoint, Yammer et des groupes](../media/groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-microsoft-365-groups"></a>Les effets des paramètres SharePoint sur les Microsoft 365 de groupe

|SharePoint paramètre|Description|Impact sur les Microsoft 365 groupes|Recommandation|
|:-----------------|:----------|:-----------------------------|:-------------|
|Partage externe pour l’organisation et le site|Détermine si les sites, fichiers et dossiers peuvent être partagés avec des personnes extérieures à l’organisation.|Si SharePoint et les paramètres de groupes ne correspondent pas, l’accès au site peut être bloqué pour les invités du groupe, ou l’accès externe peut être disponible dans le site, mais pas dans le groupe.|Lorsque vous modifiez les paramètres de partage, vérifiez les paramètres de groupes et les SharePoint de site pour les sites d’équipe connectés à un groupe.<br><br>Voir [Collaborer avec des invités dans un site.](./collaborate-in-site.md)|
|Domaine autoriser/bloquer|Autorise ou empêche le partage de contenu avec des domaines spécifiés.|Les groupes ne reconnaissent pas SharePoint listes d’accès ou de blocage. Les utilisateurs provenant de domaines non SharePoint peuvent accéder aux SharePoint via un groupe.|Gérez les listes d’accès/de blocage de domaine pour Azure AD et SharePoint ensemble. Créez un processus de gouvernance à l’échelle de l’organisation pour autoriser et bloquer les domaines.<br><br>Voir SharePoint de domaine et les [paramètres](/sharepoint/restricted-domains-sharing) de [domaine Azure AD](/azure/active-directory/b2b/allow-deny-list)|
|Autoriser les utilisateurs dans les groupes de sécurité spécifiques à partager avec l’extérieur|Spécifie les groupes de sécurité qui peuvent partager des sites, des dossiers et des fichiers en externe.|Ce paramètre n’affecte pas les propriétaires de groupes qui partagent des groupes en externe. Les invités de groupe ont accès au site SharePoint associé.||
|SharePoint de partage de site|Détermine qui peut partager le site directement en dehors de l’appartenance au groupe. Ceci est configuré par le propriétaire du groupe ou du site.|Ce paramètre n’affecte pas directement le groupe, mais il peut permettre aux utilisateurs d’être ajoutés à un site et de ne pas avoir accès à d’autres ressources de groupe|Envisagez d’utiliser ce paramètre pour limiter le partage du site directement et gérer l’accès au site via le groupe.|
|Permet aux utilisateurs de créer des sites à partir SharePoint page de démarrage et de OneDrive|Spécifie si les utilisateurs peuvent créer de nouveaux sites SharePoint sites.|Si ce paramètre est désactivé, les utilisateurs peuvent toujours créer des sites d’équipe connectés à un groupe en créant un groupe.||

## <a name="the-effects-of-microsoft-365-groups-setting-on-sharepoint"></a>Les effets de la définition Microsoft 365 groupes sur les SharePoint

|Microsoft 365 groupes|Description|Effet sur les SharePoint|Recommandation|
|:---------------------------|:----------|:-------------------|:-------------|
|Conventions d’attribution de nom|Spécifie les préfixes et suffixes de nom de groupe, ainsi que les mots bloqués pour la création de groupe|Les stratégies sont appliquées pour les utilisateurs créant des sites d’équipe connectés à un groupe, mais pas pour les sites de communication ou les sites avec d’autres modèles.|Créez des instructions d’attribution de noms distinctes pour les sites de communication si nécessaire.|
|Accès invité de groupe|Spécifie si des personnes extérieures à l’organisation peuvent être ajoutées à des groupes.|Si SharePoint et les paramètres de groupes ne correspondent pas, l’accès au site peut être bloqué pour les invités du groupe, ou l’accès externe peut être disponible dans le site, mais pas dans le groupe.|Lorsque vous modifiez les paramètres de partage, vérifiez les paramètres de groupes et les SharePoint de site pour les sites d’équipe connectés à un groupe.<br><br>Voir [Collaborer avec des invités dans un site](./collaborate-in-site.md)|
|Création de groupe par groupe de sécurité|Les groupes peuvent uniquement être créés par les membres d’un groupe de sécurité spécifique.|Les utilisateurs qui ne sont pas membres du groupe de sécurité ne pourront pas créer de site d’équipe connecté à un groupe.|Assurez-vous que votre processus de demande de groupe inclut des instructions pour demander un site.|
|Stratégie d’expiration de groupe|Spécifie une période après laquelle les groupes qui ne sont pas activement utilisés seront automatiquement supprimés.|Lorsque le groupe est supprimé, le site SharePoint est également supprimé. Le contenu protégé par les stratégies de rétention est conservé.|Utilisez des stratégies d’expiration pour éviter les problèmes de groupes et de sites inutilisés.|

## <a name="related-topics"></a>Sujets connexes

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Collaborer avec des personnes extérieures à votre organisation](./collaborate-with-people-outside-your-organization.md)

[Gérer la création de sites dans SharePoint](/sharepoint/manage-site-creation)