---
title: Forum aux questions sur le déploiement centralisé
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Examinez les réponses aux questions fréquentes sur le déploiement centralisé à partir du Centre d’administration Microsoft 365.
ms.openlocfilehash: 0da9ec9595fd433abe1e2e2ae3f2e3a0c6b3b9b5
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53228003"
---
# <a name="centralized-deployment-faq"></a>Forum aux questions sur le déploiement centralisé

Le déploiement centralisé est la façon recommandée pour un administrateur Office 365 de déployer des modules de Office (Word, Excel, PowerPoint et Outlook) pour les utilisateurs et les groupes au sein d’une organisation, à condition que l’organisation réponde à toutes les exigences d’utilisation du déploiement centralisé, comme indiqué dans cet article.   
  
## <a name="how-do-i-know-if-my-organization-is-set-up-for-centralized-deployment"></a>Comment savoir si mon organisation est définie pour un déploiement centralisé ?  

Le déploiement centralisé des add-ins nécessite que les utilisateurs utilisent Applications Microsoft 365 pour les grandes entreprises (et soient connectés à Office à l’aide de leurs informations d’identification de connexion organisationnelle) et qu’ils Exchange Online boîtes aux lettres. Votre annuaire d’abonnement doit être dans un répertoire ou fédéré dans Azure Active Directory.  
 
Le déploiement centralisé est uniquement pris en charge pour les boîtes aux lettres en ligne. Il ne prend pas en charge le déploiement vers des boîtes aux lettres Exchange sur site.

Vous pouvez utiliser le contrôle [de compatibilité du](centralized-deployment-of-add-ins.md#centralized-deployment-compatibility-checker)déploiement centralisé pour déterminer si votre abonnement est   éligible. 
  
## <a name="how-do-you-target-add-in-user-assignments-with-centralized-deployment"></a>Comment cibler les affectations d’utilisateurs de add-in avec le déploiement centralisé ?  

Le déploiement centralisé prend en charge les affectations à des utilisateurs individuels, des groupes et à tous les utilisateurs du client. Le déploiement centralisé peut être utilisé pour les utilisateurs de groupes de niveau supérieur ou de groupes sans groupes parents, mais pas pour les utilisateurs de groupes imbrmbrés ou de groupes qui ont des groupes parents. Le déploiement centralisé fait également partie de la plupart des groupes Azure Active Directory, notamment les groupes Office 365, les listes de distribution et les groupes de sécurité.  

Il est préférable d’utiliser des affectations de groupes plutôt que des affectations individuelles d’utilisateurs pour faciliter la gestion.
 
Pour plus d’informations, voir [Affectations d’utilisateurs et de groupes.](./centralized-deployment-of-add-ins.md#user-and-group-assignments)  
   
## <a name="how-long-does-it-take-for-add-ins-to-show-up-for-all-users"></a>Combien de temps faut-il pour que les modules s’afficheront pour tous les utilisateurs ?  

L’exposition d’un add-in pour tous les utilisateurs peut prendre jusqu’à 24 heures. Les mises à jour de modules, les modifications apportées à l’aide de l’activer ou de la désactiver, ou les suppressions de ces derniers peuvent prendre autant de temps. 
  
## <a name="as-an-administrator-how-do-i-manage-the-user-access-to-add-ins-for-my-organization"></a>En tant qu’administrateur, comment puis-je gérer l’accès des utilisateurs aux add-ins pour mon organisation ?

Pour faciliter le déploiement des modules pour les utilisateurs, les groupes ou l’ensemble de votre organisation, nous recommandons aux administrateurs d’utiliser le déploiement centralisé.

Pour plus d’informations sur la gestion de l’accès des utilisateurs, voir :
 - [Empêcher les téléchargements de Office sur tous les clients (sauf Outlook)](./manage-addins-in-the-admin-center.md#prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook)
 - [Désignation des administrateurs et utilisateurs qui peuvent installer et gérer des compléments pour Outlook](/Exchange/specify-who-can-install-and-manage-add-ins-2013-help)

## <a name="will-centralized-deployment-provide-admins-the-flexibility-to-choose-the-deployment-method-for-outlook-add-ins"></a>Le déploiement centralisé offre-t-il aux administrateurs la possibilité de choisir la méthode de déploiement pour Outlook des modules ?  

Oui. Le déploiement centralisé offre aux administrateurs la possibilité de choisir l’une des trois méthodes de déploiement pour les Outlook lors du déploiement de ces derniers :

**Fixe (valeur par défaut)**   Le add-in est déployé automatiquement pour les utilisateurs affectés et ils ne peuvent pas le supprimer.  
 
**Disponible** Les utilisateurs peuvent installer le Outlook en choisissant Home **> Get More add-ins > admin-managed**.
 
**Facultatif** Le add-in est déployé automatiquement pour les utilisateurs affectés, mais ils peuvent choisir de le supprimer.  
    
## <a name="can-admins-update-line-of-business-lob-add-ins"></a>Les administrateurs peuvent-ils mettre à jour des add-ins métier ?  

Oui. Les administrateurs peuvent télécharger un nouveau fichier manifeste pour prendre en charge les modifications apportées aux métadonnées pour les add-ins LOB déployés par l’administrateur. Le add-in est mis à jour lors du prochain démarrage Office applications. L'application web peut changer à tout moment.  
 
Pour plus d’informations, voir le [add-in métier.](./manage-addins-in-the-admin-center.md)  

## <a name="can-admins-turn-off-add-ins"></a>Les administrateurs peuvent-ils désactiver les modules ?  

Oui. Les administrateurs peuvent activer ou désactiver les modules qu’ils déploient pour tous les utilisateurs à partir du Centre d’administration Microsoft.

Pour plus d’informations, voir [États des modules complémentaires.](./manage-addins-in-the-admin-center.md#add-in-states)  

##  <a name="can-admins-delete-or-remove-add-ins"></a>Les administrateurs peuvent-ils supprimer ou supprimer des modules ?

Oui. Les administrateurs peuvent supprimer des modules qu’ils ont déployés pour tous les utilisateurs à partir du Centre d’administration Microsoft.

Pour plus d’informations, [voir Supprimer un module complémentaire.](./manage-addins-in-the-admin-center.md#delete-an-add-in) 
  
## <a name="can-admins-deploy-paid-add-ins-from-the-office-store-using-centralized-deployment"></a>Les administrateurs peuvent-ils déployer des add-ins payants à partir du Office Store à l’aide d’un déploiement centralisé ? 

Non. Pour l’instant, vous ne pouvez pas déployer de Office payants à partir du Office Store à l’aide du déploiement centralisé.  
 
Nous vous suggérons d’atteindre le développeur de logiciels indépendants pour que le add-in payant demande un fichier manifeste ou une URL. L’administrateur client peut ensuite déployer le add-in en tant que add-in cœur de rôle à l’aide du déploiement centralisé.
    
## <a name="which-admin-role-do-i-need-to-manage-add-ins-for-my-organization"></a>Quel rôle d’administrateur ai-je besoin pour gérer les modules pour mon organisation ?  

L’administrateur général est le rôle recommandé avec un accès complet au cycle de vie de gestion des applications. Si vous êtes la personne qui a acheté votre abonnement Microsoft 365 Entreprise, vous êtes l’administrateur global. 
 
Votre abonnement est livré avec un ensemble de rôles d’administrateur que vous pouvez attribuer à d’autres utilisateurs de votre organisation. Chaque rôle d’administrateur est map pour les fonctions d’entreprise courantes et donne aux membres de votre organisation des autorisations pour effectuer des tâches spécifiques dans le Centre d’administration Microsoft 365.  
 
Pour plus d’informations, voir [Attribuer des rôles d’administrateur.](../add-users/assign-admin-roles.md) 
