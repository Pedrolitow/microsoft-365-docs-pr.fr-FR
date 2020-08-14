---
title: Interactions de paramètres entre les groupes Microsoft 365 et SharePoint
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
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: En savoir plus sur les interactions de paramètres entre les groupes Microsoft 365 et SharePoint
ms.openlocfilehash: 0c9fdd69db82985039bae03768aa0c19f514c99f
ms.sourcegitcommit: 66f1f430b3dcae5f46cb362a32d6fb7da4cff5c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "46662620"
---
# <a name="settings-interactions-between-microsoft-365-groups-and-sharepoint"></a>Interactions de paramètres entre les groupes Microsoft 365 et SharePoint

Certains paramètres pour les groupes Microsoft 365 et SharePoint dans Microsoft 365, en particulier ceux liés à la création de sites de partage et de groupe et de site d’équipe, se chevauchent les uns avec les autres. Cet article décrit ces interactions et les meilleures pratiques relatives à l’utilisation de ces paramètres.

![Diagramme de Venn des fonctionnalités SharePoint, Yammer et groupes](../media/groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-microsoft-365-groups"></a>Effets des paramètres SharePoint sur les groupes Microsoft 365

|Paramètre SharePoint|Description|Effet sur les groupes Microsoft 365|Recommandation|
|:-----------------|:----------|:-----------------------------|:-------------|
|Partage externe pour l’organisation et le site|Détermine si des sites, des fichiers et des dossiers peuvent être partagés avec des personnes extérieures à l’organisation.|Si les paramètres SharePoint et les groupes ne correspondent pas, les invités du groupe peuvent être bloqués ou l’accès externe peut être disponible sur le site, mais pas dans le groupe.|Lors de la modification des paramètres de partage, vérifiez les paramètres de groupe et les paramètres de site SharePoint pour les sites d’équipe connectés à un groupe.<br><br>Consultez [la rubrique collaborer avec des invités dans un site](https://docs.microsoft.com/microsoft-365/solutions/collaborate-in-site).|
|Bloc autorisé de domaine|Autorise ou empêche le partage de contenu avec des domaines spécifiés.|Les groupes ne reconnaissent pas les listes verte ou rouge de SharePoint. Les utilisateurs de domaines non autorisés dans SharePoint peuvent accéder à SharePoint par le biais d’un groupe.|Gérer ensemble les listes d’adresses de domaine autorisées/bloquées pour Azure AD et SharePoint. Créez un processus de gouvernance à l’échelle de l’Organisation pour autoriser et bloquer les domaines.<br><br>Voir paramètres de [domaine SharePoint](https://docs.microsoft.com/sharepoint/restricted-domains-sharing) et [paramètres de domaine Azure ad](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)|
|Autoriser les utilisateurs dans les groupes de sécurité spécifiques à partager avec l’extérieur|Spécifie les groupes de sécurité qui peuvent partager des sites, des dossiers et des fichiers de manière externe.|Ce paramètre n’affecte pas les groupes de partage de groupe à l’extérieur. Les invités du groupe ont accès au site SharePoint associé.||
|Paramètres de partage de sites SharePoint|Détermine les personnes qui peuvent partager le site directement en dehors de l’appartenance au groupe. Cette configuration est configurée par le propriétaire du groupe ou du site.|Ce paramètre n’affecte pas directement le groupe, mais il peut autoriser les utilisateurs à être ajoutés à un site sans avoir accès à d’autres ressources de groupe.|Envisagez d’utiliser ce paramètre pour limiter le partage du site directement et gérer l’accès au site via le groupe.|
|Autoriser les utilisateurs à créer des sites à partir de la page de démarrage SharePoint et de OneDrive|Indique si les utilisateurs peuvent créer de nouveaux sites SharePoint.|Si ce paramètre est désactivé, les utilisateurs peuvent toujours créer des sites d’équipe connectés à un groupe en créant un groupe.||

## <a name="the-effects-of-microsoft-365-groups-setting-on-sharepoint"></a>Effets du paramètre groupes Microsoft 365 sur SharePoint

|Paramètre de groupes Microsoft 365|Description|Effet sur SharePoint|Recommandation|
|:---------------------------|:----------|:-------------------|:-------------|
|Stratégies d’attribution de noms|Spécifie les préfixes de nom de groupe et les suffixes, et les mots bloqués pour la création de groupe|Les stratégies sont appliquées pour les utilisateurs qui créent des sites d’équipe connectés à un groupe, mais pas des sites de communication ou des sites avec d’autres modèles.|Créez des instructions de dénomination distinctes pour les sites de communication, le cas échéant.|
|Accès invité de groupe|Indique si les utilisateurs externes à l’organisation peuvent être ajoutés à des groupes.|Si les paramètres SharePoint et les groupes ne correspondent pas, les invités du groupe peuvent être bloqués ou l’accès externe peut être disponible sur le site, mais pas dans le groupe.|Lors de la modification des paramètres de partage, vérifiez les paramètres de groupe et les paramètres de site SharePoint pour les sites d’équipe connectés à un groupe.<br><br>Voir [collaborer avec des invités dans un site](https://docs.microsoft.com/microsoft-365/solutions/collaborate-in-site)|
|Création de groupe par groupe de sécurité|Les groupes ne peuvent être créés que par les membres d’un groupe de sécurité spécifique.|Les utilisateurs qui ne sont pas membres du groupe de sécurité ne seront pas en mesure de créer un site d’équipe connecté à un groupe.|Assurez-vous que votre processus de demande d’un groupe inclut des instructions pour la demande d’un site.|
|Stratégie d’expiration de groupe|Spécifie une période de temps au terme de laquelle les groupes qui ne sont pas utilisés activement sont automatiquement supprimés.|Lorsque le groupe est supprimé, le site SharePoint associé est également supprimé. Le contenu protégé par les stratégies de rétention est conservé.|Utilisez des stratégies d’expiration pour éviter la prolifération des groupes et des sites inutilisés.|

## <a name="related-topics"></a>Voir aussi

[Collaboration avec des personnes extérieures à votre organisation](https://docs.microsoft.com/microsoft-365/solutions/collaborate-with-people-outside-your-organization)

[Gérer la création de sites dans SharePoint](https://docs.microsoft.com/sharepoint/manage-site-creation)