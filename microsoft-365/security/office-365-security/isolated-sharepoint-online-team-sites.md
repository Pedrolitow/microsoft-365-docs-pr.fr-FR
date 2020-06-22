---
title: Sites d’équipe SharePoint Online isolés
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: Découvrez les sites d’équipe SharePoint Online isolés, y compris les utilisations, les exigences et les fonctionnalités compatibles.
ms.openlocfilehash: 0646ffc37256702844b550fd1beb841944b2d509
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44819532"
---
# <a name="isolated-sharepoint-online-team-sites"></a>Sites d’équipe SharePoint Online isolés

 **Résumé :** Découvrez les utilisations pour les sites d'équipe SharePoint Online isolés.
  
SharePoint Online team sites are an easy way to quickly create a space for collaboration of notes, documents, articles, a calendar, and other resources in Microsoft Office 365. SharePoint Online team sites are based on a Microsoft 365 group and have a simplified administration model to allow open collaboration with a private set of group members or the entire organization. A default SharePoint Online team site allows members of the Microsoft 365 group to invite other users and control permissions settings.
  
However, in some cases, you want to create a SharePoint Online team site for collaboration where the permissions of that site are more tightly controlled through group membership and SharePoint Online permission levels, which are only managed by SharePoint administrators. We call this an isolated site, which is isolated to the set of users that are either collaborating, viewing its contents, or administering the site. You might need an isolated site for the following:
  
- travailler sur un projet secret au sein de votre organisation ;
    
- stocker des éléments de propriété intellectuelle précieux ou très sensibles pour votre organisation ;
    
- conserver les ressources destinées à une procédure judiciaire engagée par votre organisation ou à laquelle elle est soumise ;
    
- Pour partager un abonnement Microsoft 365 avec d’autres organisations dont certaines activités se recoupent, mais qui, pour la plupart, existent en tant qu’entités distinctes.
    
Voici les exigences d’un site isolé :
  
- Seuls les administrateurs SharePoint Online peuvent gérer le site, en particulier l’accès au site par les membres du groupe et la configuration des autorisations personnalisées.
    
- Les membres du site ne peuvent pas inviter d’autres membres à accéder au site d’équipe.
    
- Users who are not members of the isolated site cannot request access to the site. They will receive an access denied web page when they attempt to access any URL associated with the site.
    
The tradeoff of requiring centralized access control and custom permissions by SharePoint Online administrators is that the site remains isolated over time. For example, current members cannot, either intentionally or accidentally, invite or configure custom permissions for other users within the Microsoft 365 subscription who should not be members of the site.
  
Un site isolé peut être utilisé avec d’autres fonctionnalités, telles que :
  
- la gestion des droits relatifs à l’information pour garantir que les ressources du site restent chiffrées même si elles sont téléchargées localement et chargées sur un autre site accessible à toute l’entreprise ;
    
- la protection contre la perte de données pour empêcher les utilisateurs d’envoyer par e-mail les ressources du site, comme des fichiers.
    
## <a name="next-steps"></a>Étapes suivantes

Pour tester un site d'équipe SharePoint Online isolé faisant partie d'un abonnement à la version d'évaluation, consultez la rubrique [Site d'équipe SharePoint Online isolé dans votre environnement de développement/test d'Office 365](isolated-sharepoint-online-team-site-dev-test-environment.md).
  
Lorsque vous souhaitez déployer un site d'équipe SharePoint Online isolé en production, lisez la procédure détaillée dans la rubrique [Conception d'un site d'équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md).
  
## <a name="related-topics"></a>Voir aussi

[Conception d'un site d'équipe SharePoint Online isolé](design-an-isolated-sharepoint-online-team-site.md)
  
[Gestion d’un site d’équipe SharePoint Online isolé](manage-an-isolated-sharepoint-online-team-site.md)

[Déploiement d’un site d’équipe SharePoint Online isolé](deploy-an-isolated-sharepoint-online-team-site.md)


