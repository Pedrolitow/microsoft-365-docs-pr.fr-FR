---
title: Forum aux questions sur le déploiement centralisé
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
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
description: Passez en revue les réponses aux questions fréquemment posées sur le déploiement centralisé à partir du centre d’administration Microsoft 365.
ms.openlocfilehash: 0d0f2163982042f7b8f868a36f5cc115a17295a2
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44399823"
---
# <a name="centralized-deployment-faq"></a>Forum aux questions sur le déploiement centralisé

Le déploiement centralisé est la méthode recommandée pour un administrateur Office 365 pour déployer des compléments Office (Word, Excel, PowerPoint et Outlook) pour les utilisateurs et les groupes au sein d’une organisation, à condition que l’organisation remplisse toutes les conditions d’utilisation du déploiement centralisé comme décrit dans cet article.   
  
## <a name="how-do-i-know-if-my-organization-is-set-up-for-centralized-deployment"></a>Comment savoir si mon organisation est configurée pour un déploiement centralisé ?  

Le déploiement centralisé des compléments nécessite que les utilisateurs utilisent les applications Microsoft 365 pour Enterprise (et sont connectés à Office à l’aide de leurs informations d’identification de connexion de l’organisation) et disposent de boîtes aux lettres Exchange Online. Le répertoire de votre abonnement doit être dans Azure Active Directory ou être fédéré.  
 
Le déploiement centralisé est uniquement pris en charge pour les boîtes aux lettres en ligne. Il ne prend pas en charge le déploiement vers des boîtes aux lettres Exchange locales.
 
Vous pouvez utiliser le [Vérificateur de compatibilité du déploiement centralisé Office 365](https://docs.microsoft.com/microsoft-365/admin/manage/centralized-deployment-of-add-ins?view=o365-worldwide#office-365-centralized-deployment-compatibility-checker)   pour déterminer si votre abonnement est éligible. 
  
## <a name="how-do-you-target-add-in-user-assignments-with-centralized-deployment"></a>Comment ciblez-vous les affectations d’utilisateurs de compléments avec un déploiement centralisé ?  

Le déploiement centralisé prend en charge les affectations à des utilisateurs individuels, des groupes et tout le monde dans le client. Le déploiement centralisé peut être utilisé pour les utilisateurs dans les groupes de niveau supérieur ou les groupes sans groupes parents, mais pas pour les utilisateurs dans les groupes ou groupes imbriqués ayant des groupes parents. Le déploiement centralisé fait également partie de la plupart des groupes Azure Active Directory, y compris les groupes Office 365, les listes de distribution et les groupes de sécurité.  

Il est préférable d’utiliser des affectations de groupes au lieu de l’affectation individuelle des utilisateurs pour faciliter la gestion.
 
Pour plus d’informations, consultez la rubrique [attributions d’utilisateurs et de groupes](https://docs.microsoft.com/microsoft-365/admin/manage/centralized-deployment-of-add-ins?view=o365-worldwide#user-and-group-assignments).  
   
## <a name="how-long-does-it-take-for-add-ins-to-show-up-for-all-users"></a>Combien de temps faut-il pour que les compléments s’affichent pour tous les utilisateurs ?  

Un complément peut prendre jusqu’à 24 heures pour s’afficher pour tous les utilisateurs. La mise à jour des compléments peut prendre le même temps, passer de l’activation ou de la désactivation, ou des suppressions de compléments. 
  
## <a name="as-an-administrator-how-do-i-manage-the-user-access-to-add-ins-for-my-organization"></a>En tant qu’administrateur, comment puis-je gérer l’accès des utilisateurs aux compléments pour mon organisation ?

Pour faciliter le déploiement des compléments pour les utilisateurs, les groupes ou l’ensemble de votre organisation, nous recommandons aux administrateurs d’utiliser un déploiement centralisé.

Pour plus d’informations sur la gestion de l’accès utilisateur, voir </br>[Empêcher les téléchargements de compléments en désactivant l’Office Store sur tous les clients (sauf Outlook)](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins?view=o365-worldwide#prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook) et </br>[Spécifiez les administrateurs et les utilisateurs qui peuvent installer et gérer les compléments pour Outlook](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins?redirectedfrom=MSDN).

## <a name="will-centralized-deployment-provide-admins-the-flexibility-to-choose-the-deployment-method-for-outlook-add-ins"></a>Le déploiement centralisé offrira-t-il la souplesse nécessaire pour choisir la méthode de déploiement des compléments Outlook ?  

Oui. Le déploiement centralisé offre aux administrateurs la souplesse nécessaire pour choisir l’une des trois méthodes de déploiement pour les compléments Outlook lors du déploiement de compléments :

**Fixed (valeur par défaut)**   Le complément est déployé automatiquement sur les utilisateurs affectés, et ils ne peuvent pas le supprimer.  
 
**Disponible** Les utilisateurs peuvent installer le complément dans Outlook en choisissant Accueil > obtenir d’autres compléments > gérés par l’administrateur.   
 
**Facultatif** Le complément est déployé automatiquement sur les utilisateurs attribués, mais ils peuvent choisir de le supprimer.  
    
## <a name="can-admins-update-line-of-business-lob-add-ins"></a>Les administrateurs peuvent-ils mettre à jour des compléments métier (LOB) ?  

Oui. Les administrateurs peuvent télécharger un nouveau fichier manifeste afin de prendre en charge les modifications de métadonnées pour les compléments métier déployés par l’administrateur. Le complément est mis à jour lors du prochain démarrage des applications Office. L'application web peut changer à tout moment.  
 
Pour plus d’informations, reportez-vous à la rubrique [line-of-Business Add-in](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins?view=o365-worldwide#security-of-office-add-ins).  

## <a name="can-admins-turn-off-add-ins"></a>Les administrateurs peuvent-ils désactiver les compléments ?  

Oui. Les administrateurs peuvent activer ou désactiver les compléments qu’ils déploient pour tous les utilisateurs à partir du centre d’administration Microsoft.

Pour plus d’informations, consultez la rubrique [États des compléments](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins?view=o365-worldwide#add-in-states).  

##  <a name="can-admins-delete-or-remove-add-ins"></a>Les administrateurs peuvent-ils supprimer ou supprimer des compléments ?

Oui. Les administrateurs peuvent supprimer des compléments qu’ils ont déployés pour tous les utilisateurs à partir du centre d’administration Microsoft.

Pour plus d’informations, consultez [la rubrique delete the Add-in](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins?view=o365-worldwide#delete-the-add-in). 
  
## <a name="can-admins-deploy-paid-add-ins-from-the-office-store-using-centralized-deployment"></a>Les administrateurs peuvent-ils déployer des compléments payants à partir de l’Office Store à l’aide d’un déploiement centralisé ? 

Non. Vous ne pouvez pas déployer des compléments payants à partir de l’Office Store à l’aide du déploiement centralisé pour le moment.  
 
Nous vous suggérons de contacter le développeur ISV pour le complément payant afin de demander un fichier manifeste ou une URL. L’administrateur client peut ensuite déployer le complément en tant que complément métier à l’aide du déploiement centralisé.
    
## <a name="which-admin-role-do-i-need-to-manage-add-ins-for-my-organization"></a>Quel rôle d’administrateur dois-je utiliser pour gérer les compléments pour mon organisation ?  

Vous devez disposer du rôle d’administrateur global pour gérer les compléments. Si vous êtes la personne qui a acheté votre abonnement Microsoft 365 pour les entreprises, vous êtes l’administrateur général. 
 
Votre abonnement est fourni avec un ensemble de rôles d’administrateur que vous pouvez attribuer à d’autres utilisateurs au sein de votre organisation. Chaque rôle d’administrateur est mappé à des fonctions professionnelles courantes et donne aux membres de votre organisation des autorisations pour effectuer des tâches spécifiques dans le centre d’administration 365 de Microsoft.  
 
Pour plus d’informations, consultez la rubrique [assigner des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles?view=o365-worldwide).  