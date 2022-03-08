---
title: Transférer manuellement des données entre deux comptes
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ms.assetid: 7dc5d983-84b2-4802-bef0-602ae1780a42
description: Découvrez comment transférer manuellement des données entre deux comptes Microsoft 365 lorsque vous avez modifié le nom de l’offre ou de la société, ou combiné plusieurs abonnements en un seul.
ms.openlocfilehash: 7d6cb9e055fd27e8f9b0a26e7ff4bfffa97421ae
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316714"
---
# <a name="transfer-data-manually-between-two-accounts"></a>Transférer manuellement des données entre deux comptes

Préparez-vous à mettre en place vos comptabilité et bloquer un segment de temps sur votre calendrier : le transfert de données entre deux comptes Microsoft 365 est un processus manuel, compliqué et chronophage. Il ne s’agit pas d’un processus automatisé ou pris en charge. Nous allons vous aider à démarrer.
  
> [!CAUTION]
> Il y aura un temps d’in Microsoft 365 pendant le processus pendant lequel le courrier électronique, les Skype Entreprise et un site web public hébergé sur Microsoft 365 ne fonctionneront pas. Les utilisateurs obtiennent de nouveaux noms d’utilisateur et mots de passe, et ils doivent réinitialiser Outlook.

**Ne transférez les données manuellement à l’aide des instructions de cette rubrique que si l’une des procédures suivantes s’applique :**
  
- Vous devez modifier un plan dans une autre famille de services.

- Le nom de votre société a changé et vous avez décidé de créer un abonnement et de migrer vos données, car vous souhaitez utiliser différents noms de domaine initiaux.

- Vous devez combiner plusieurs abonnements en un nouvel abonnement.

> [!IMPORTANT]
> Si vous devez modifier votre [plan](../../commerce/subscriptions/switch-to-a-different-plan.md) d’abonnement et que vous pouvez utiliser l’Assistant Changer de plan, ou si vous devez transférer vers un nouveau plan d’abonnement dans la même famille d’abonnements même lorsque l’Assistant Changer de plan ne fonctionne pas, vous n’avez pas besoin de transférer manuellement vos données et il n’y a pas de temps d’arrêt.

|**Tâches**|**Étapes**|
|:-----|:-----|
|Achetez le plan vers qui vous souhaitez passer.  <br/> |Lorsque vous vous inscrivez, vous spécifiez le nom de la société à utiliser dans les noms de domaine initiaux :  *votre*  société .  *onmicrosoft.com, votre*  société -public.sharepoint.com et votre  *entreprise .sharepoint.com*  . Vous devez utiliser un nom de  *votre*  entreprise différent de celui des abonnements existants.  <br/> > [!NOTE]> il faut généralement plusieurs mois après l’annulation d’un abonnement pour libérer les noms de domaine initiaux qui utilisent  votre entreprise à partir de nos systèmes. Même si vous prévoyez d’enregistrer toutes vos données à partir de votre ancien abonnement Microsoft 365 et d’annuler cet abonnement, l’ancienne valeur de votre entreprise n’est pas immédiatement disponible pour une utilisation dans un nouvel abonnement.           |
|Supprimez votre domaine personnalisé de votre ancien Microsoft 365 abonnement.  <br/> | Suivez [les](remove-a-domain.md) étapes requises avant de supprimer un domaine pour supprimer le nom de domaine des adresses de messagerie des utilisateurs et supprimer les enregistrements DNS pour le courrier électronique et Lync pour le domaine personnalisé. Si vous hébergez votre site web public Microsoft 365, vous devez également supprimer l’enregistrement CNAME qui pointe vers celui-ci.  <br/> > [!IMPORTANT]> Après avoir supprimé l’enregistrement MX qui approvisionnement le courrier électronique vers ce domaine personnalisé, le courrier électronique cesse de fonctionner tant que vous n’avez pas ajouté le domaine à votre nouveau compte, que vous avez installé le nouvel enregistrement MX et que vous avez installé vos utilisateurs. Lorsque vous supprimez les enregistrements DNS pour Lync, Lync cesse de fonctionner. Une fois que vous avez supprimé l’enregistrement CNAME qui pointe vers votre site web public, il ne sera pas disponible.           [Supprimez le domaine](remove-a-domain.md) .  <br/> |
|Configurer votre domaine personnalisé pour votre nouvel abonnement et configurer vos utilisateurs.  <br/> | Configurer votre nouvel abonnement, y compris la création des enregistrements DNS requis pour votre domaine personnalisé.  <br/>  Créez vos utilisateurs, avec des adresses de messagerie sur votre domaine personnalisé.  <br/> |
|Transférer des données de votre ancien abonnement vers votre nouvel abonnement.  <br/> | Connectez-vous aux deux comptes dans des fenêtres de navigateur distinctes :  <br/>  Cliquez avec le bouton droit sur l’icône de votre navigateur et ouvrez deux fenêtres de navigateur privées. Vous pouvez utiliser des informations d’identification différentes dans les deux fenêtres pour vous inscrire sur les deux comptes.  <br/> [Transférer les paramètres d’administration entre les abonnements](#email) <br/> [Transférer la structure et les données du site d’équipe](#transfer-team-site-structure-and-data) <br/> [Transfert d’un site web public entre les abonnements](#transfer-a-public-website-between-subscriptions) <br/> [Transférer les paramètres d’administration entre les abonnements](#email) <br/> |
|Annulez l’abonnement pour l’offre avec qui vous avez terminé en appelant le Support Microsoft Microsoft 365.  <br/> | Vérifiez que votre nouvel abonnement fonctionne et que toutes les données ont été transférées.  <br/>  [Contactez le support technique pour](../../business-video/get-help-support.md) annuler votre ancien abonnement.  <br/> |

## <a name="transfer-administrative-settings-between-subscriptions"></a>Transférer les paramètres d’administration entre les abonnements

Go to the following pages on each account, and set up the new account based on the old account’s settings.
  
Si vous transférez des données de Microsoft 365 vers Microsoft 365 moyenne entreprise ou Microsoft 365 Entreprise, les pages d’administration sont structurées différemment. Regardez [une vidéo : présentation Microsoft 365 Entreprise](../index.yml), puis allez aux endroits suivants pour examiner les paramètres d’administration.
  
Pour Microsoft 365 Entreprise et Microsoft 365 moyenne entreprise :
  
|**Location**|**Objectif**|
|:-----|:-----|
|**Administrateur** \>  \> Microsoft 365 **service** <br/> |Sélectionnez chaque onglet pour les paramètres de messagerie, de sites, de Lync, de logiciels utilisateur, de mots de passe, de communauté, de gestion des droits et de mobilité.  <br/> |
|**Administrateur** \> **Exchange** <br/> | Exchange Online paramètres  <br/> |
|**Administrateur** \> **SharePoint** <br/> | SharePoint Online  <br/> |
|**Administrateur** \> **Skype Entreprise** <br/> |Paramètres de Skype Entreprise supplémentaires  <br/> |

Pour Microsoft 365 petite entreprise
  
|**Location**|**Objectif**|
|:-----|:-----|
|**Administrateur** \> **Gérer les paramètres à l’échelle de l’organisation** <br/> |Paramètres d’administration  <br/> |

## <a name="transfer-a-public-website-between-subscriptions"></a>Transfert d’un site web public entre les abonnements

Si vous avez un site web public hébergé sur Microsoft 365, vous devez l’enregistrer et le créer à nouveau dans votre nouvel abonnement.
  
> [!NOTE]
> Si votre site web public est hébergé par un fournisseur d’hébergement DNS, aucune modification n’est requise. Il ne sera pas affecté par votre transition.
  
Pour enregistrer une bibliothèque de documents ou un contenu de liste à partir d’un environnement SharePoint Online vers des partages de fichiers ou sur un ordinateur local, voir Migration manuelle du contenu [SharePoint Online](/sharepoint/troubleshoot/migration-tool/content-manual-migration).
  
> [!NOTE]
> L’application de migration de site public ne peut pas transférer de données vers un autre abonnement.
  
## <a name="transfer-team-site-structure-and-data"></a>Transférer la structure et les données du site d’équipe

Il existe plusieurs façons d’enregistrer ou de transférer des données de site d’équipe :
  
- Vous pouvez enregistrer l’ancien site en tant que modèle et importer le modèle dans le nouveau site.

- Pour transférer des documents, recréez d’abord manuellement votre hiérarchie sur le nouveau site. Ensuite, vous pouvez ouvrir SharePoint sites d’équipe en même temps, ouvrir les deux bibliothèques de documents avec Windows Explorer, puis copier et coller les documents. Voir [la vidéo : copier ou déplacer des fichiers de bibliothèque à l’aide de l’outil Ouvrir avec l’Explorateur](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e).

- Pour transférer des données de liste, enregistrez un modèle [de liste et](https://support.microsoft.com/office/c3884ad1-bc49-44b8-b3d6-3bc6a01eb393) utilisez le modèle enregistré pour re-créer la liste sur le nouveau site.

- Pour enregistrer une bibliothèque de documents ou un contenu de liste à partir d’un environnement SharePoint Online (OneDrive Entreprise ou sites d’équipe) vers des partages de fichiers ou sur un ordinateur local, voir Informations sur la migration manuelle du contenu [SharePoint Online](/sharepoint/troubleshoot/migration-tool/content-manual-migration).

## <a name="transfer-users-data-between-subscriptions"></a>Transférer les données des utilisateurs entre les abonnements

### <a name="email"></a>E-mail :

Demandez aux utilisateurs [de déplacer leurs messages électroniques, contacts, tâches et informations](https://support.microsoft.com/office/0996ece3-57c6-49bc-977b-0d1892e2aacc) de calendrier après avoir installé votre nouvel abonnement. Ils peuvent obtenir leur ancien courrier électronique à l’aide de leur nom d’utilisateur initial, par exemple sue@contoso.onmicrosoft.com.
  
### <a name="onedrive-for-business-data"></a>OneDrive Entreprise données :

Demandez aux utilisateurs de copier/[synchroniser OneDrive Entreprise contenu](https://support.microsoft.com/office/59b1de2b-519e-4d3a-8f45-51647cf291cd) sur leur ordinateur, puis de le rajouter à leur nouvel abonnement.

### <a name="onenote"></a>OneNote 

Demandez aux utilisateurs [de sauvegarder OneNote](https://support.microsoft.com/office/back-up-notes-f58b34b0-611d-435e-87fa-7942a1767af4?ui=en-us&rs=en-us&ad=us) et de restaurer les [notes d’une sauvegarde](https://support.microsoft.com/en-us/office/restore-notes-from-a-backup-5daf9cb0-6769-4998-a5de-f044fdd0d831?ui=en-us&rs=en-us&ad=us) vers leurs nouveaux abonnements.
