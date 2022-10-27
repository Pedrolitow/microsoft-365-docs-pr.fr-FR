---
title: Transférer des données manuellement entre deux comptes
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ms.assetid: 7dc5d983-84b2-4802-bef0-602ae1780a42
description: Découvrez comment transférer manuellement des données entre deux comptes Microsoft 365 lorsque vous avez modifié le nom du plan ou de l’entreprise, ou combiné plusieurs abonnements en un seul.
ms.openlocfilehash: feb2cafee627a44dafc7ee8621c1b2910ddd7470
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68718147"
---
# <a name="transfer-data-manually-between-two-accounts"></a>Transférer des données manuellement entre deux comptes

Préparez-vous à retrousser vos manches et à bloquer une partie du temps sur votre calendrier : le transfert de données entre deux comptes Microsoft 365 est un processus manuel, complexe et fastidieux. Il ne s’agit pas d’un processus automatisé ou pris en charge. Nous allons vous aider à commencer.
  
> [!CAUTION]
> Il y aura des temps d’arrêt pendant le processus où les e-mails, les Skype Entreprise et un site web public hébergé sur Microsoft 365 ne fonctionneront pas. Les utilisateurs recevront de nouveaux noms d’utilisateur et mots de passe, et ils devront réinitialiser Outlook.

**Transférez des données manuellement à l’aide des instructions de cette rubrique uniquement si l’une des conditions suivantes s’applique :**
  
- Vous devez passer à un plan dans une autre famille de services.

- Le nom de votre entreprise a changé et vous avez décidé de créer un abonnement et de migrer vos données, car vous souhaitez utiliser différents noms de domaine initiaux.

- Vous devez combiner plusieurs abonnements en un seul.

> [!IMPORTANT]
> Si vous avez besoin de [modifier votre plan d’abonnement](../../commerce/subscriptions/switch-to-a-different-plan.md) et que vous pouvez utiliser l’Assistant Changer de plan, ou si vous devez transférer vers un nouveau plan d’abonnement dans la même famille d’abonnements, même lorsque l’Assistant Changer de plan ne fonctionne pas, vous n’avez pas besoin de transférer manuellement vos données et il n’y a pas de temps d’arrêt.

|**Tâches**|**Étapes**|
|:-----|:-----|
|Achetez le plan vers lequel vous souhaitez passer.  <br/> |Lorsque vous vous inscrivez, vous spécifiez le nom de la société à utiliser dans les noms de domaine initiaux :  *votre société*  .onmicrosoft.com,  *votre société*  -public.sharepoint.com et  *votre société*  .sharepoint.com. Vous devez utiliser un nom de  *société*  différent de celui que vous avez utilisé pour tous les abonnements existants.  <br/> > [!NOTE]> Il faut généralement un minimum de plusieurs mois après l’annulation d’un abonnement pour libérer les noms de domaine initiaux qui utilisent  *votre entreprise*  à partir de nos systèmes. Même si vous envisagez d’enregistrer toutes vos données de votre ancien abonnement Microsoft 365 et d’annuler cet abonnement,  *l’ancienne valeur de votre entreprise*  n’est pas immédiatement disponible pour une utilisation dans un nouvel abonnement.           |
|Supprimez votre domaine personnalisé de votre ancien abonnement Microsoft 365.  <br/> | Suivez les [étapes requises avant de supprimer un domaine](remove-a-domain.md) pour supprimer le nom de domaine des adresses e-mail des utilisateurs et supprimer les enregistrements DNS pour la messagerie et Lync pour le domaine personnalisé. Si vous hébergez votre site web public sur Microsoft 365, vous devez également supprimer l’enregistrement CNAME qui pointe vers celui-ci.  <br/> > [!IMPORTANT]> Une fois que vous avez supprimé l’enregistrement MX qui achemine le courrier électronique vers ce domaine personnalisé, l’e-mail cesse de fonctionner jusqu’à ce que vous ayez ajouté le domaine à votre nouveau compte, configuré le nouvel enregistrement MX et configuré vos utilisateurs. Lorsque vous supprimez les enregistrements DNS pour Lync, Lync cesse de fonctionner. Une fois que vous avez supprimé l’enregistrement CNAME qui pointe vers votre site web public, il ne sera plus disponible.           [Supprimez le domaine](remove-a-domain.md) .  <br/> |
|Configurez votre domaine personnalisé pour votre nouvel abonnement et configurez vos utilisateurs.  <br/> | Configurez votre nouvel abonnement, y compris la création des enregistrements DNS requis pour votre domaine personnalisé.  <br/>  Créez vos utilisateurs, avec des adresses e-mail sur votre domaine personnalisé.  <br/> |
|Transférez des données de votre ancien abonnement vers votre nouvel abonnement.  <br/> | Connectez-vous aux deux comptes dans des fenêtres de navigateur distinctes :  <br/>  Cliquez avec le bouton droit sur l’icône de votre navigateur et ouvrez deux fenêtres de navigateur privées. Vous pouvez utiliser différentes informations d’identification dans les deux fenêtres pour vous connecter aux deux comptes.  <br/> [Transférer des paramètres d’administration entre des abonnements](#email) <br/> [Transférer la structure et les données du site d’équipe](#transfer-team-site-structure-and-data) <br/> [Transférer un site web public entre des abonnements](#transfer-a-public-website-between-subscriptions) <br/> [Transférer des paramètres d’administration entre des abonnements](#email) <br/> |
|Annulez l’abonnement pour le plan que vous avez terminé en appelant Support Microsoft pour Microsoft 365.  <br/> | Vérifiez que votre nouvel abonnement fonctionne et que toutes les données ont été transférées.  <br/>  [Contactez le support technique](../../business-video/get-help-support.md) pour annuler votre ancien abonnement.  <br/> |

## <a name="transfer-administrative-settings-between-subscriptions"></a>Transférer des paramètres d’administration entre des abonnements

Accédez aux pages suivantes sur chaque compte et configurez le nouveau compte en fonction des paramètres de l’ancien compte.
  
Si vous transférez des données de Microsoft 365 vers Microsoft 365 Midsize Business ou Microsoft 365 Entreprise, les pages d’administration sont structurées différemment. Regardez une [vidéo : Présentation de Microsoft 365 Entreprise](../index.yml) et accédez aux emplacements suivants pour examiner les paramètres d’administration.
  
Pour Microsoft 365 Entreprise et Microsoft 365 Midsize Business :
  
|**Emplacement**|**Objectif**|
|:-----|:-----|
| \> Administration **paramètres du service** **Microsoft 365** \> <br/> |Sélectionnez chaque onglet pour les paramètres du courrier, des sites, de Lync, des logiciels utilisateur, des mots de passe, de la communauté, de la gestion des droits et des appareils mobiles.  <br/> |
| \> Administration **Exchange** <br/> | Exchange Online paramètres  <br/> |
| \> Administration **SharePoint** <br/> | Paramètres SharePoint Online  <br/> |
| \> **Skype Entreprise Administration** <br/> |Paramètres de Skype Entreprise supplémentaires  <br/> |

Pour Microsoft 365 Small Business
  
|**Emplacement**|**Objectif**|
|:-----|:-----|
| \> Administration **Gérer les paramètres à l’échelle de l’organisation** <br/> |Paramètres d’administration  <br/> |

## <a name="transfer-a-public-website-between-subscriptions"></a>Transférer un site web public entre des abonnements

Si vous avez un site web public hébergé sur Microsoft 365, vous devez l’enregistrer et le recréer dans votre nouvel abonnement.
  
> [!NOTE]
> Si votre site web public est hébergé auprès d’un fournisseur d’hébergement DNS, aucune modification n’est requise. Il ne sera pas affecté par votre transition.
  
Pour enregistrer une bibliothèque de documents ou lister le contenu d’un environnement SharePoint Online sur des partages de fichiers ou sur un ordinateur local, voir [Migration manuelle du contenu SharePoint Online](/sharepoint/troubleshoot/migration-tool/content-manual-migration).
  
> [!NOTE]
> L’application de migration de site public ne peut pas transférer de données vers un autre abonnement.
  
## <a name="transfer-team-site-structure-and-data"></a>Transférer la structure et les données du site d’équipe

Il existe plusieurs façons d’enregistrer ou de transférer des données de site d’équipe :
  
- Vous pouvez enregistrer l’ancien site en tant que modèle et importer le modèle dans le nouveau site.

- Pour transférer des documents, commencez par recréer manuellement votre hiérarchie sur le nouveau site. Vous pouvez ensuite ouvrir les deux sites d’équipe SharePoint en même temps, ouvrir les deux bibliothèques de documents avec l’Explorateur Windows et copier et coller les documents. Consultez [Vidéo : Copier ou déplacer des fichiers de bibliothèque à l’aide de l’outil Ouvrir avec l’Explorateur](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e).

- Pour transférer des données de liste, enregistrez un [modèle de liste](https://support.microsoft.com/office/c3884ad1-bc49-44b8-b3d6-3bc6a01eb393) et utilisez le modèle enregistré pour recréer la liste sur le nouveau site.

- Pour enregistrer une bibliothèque de documents ou lister le contenu d’un environnement SharePoint Online (OneDrive Entreprise ou sites d’équipe) sur des partages de fichiers ou sur un ordinateur local, voir [Informations sur la migration manuelle de contenu SharePoint Online](/sharepoint/troubleshoot/migration-tool/content-manual-migration).

## <a name="transfer-users-data-between-subscriptions"></a>Transférer les données des utilisateurs entre des abonnements

### <a name="email"></a>E-mail :

Demandez aux utilisateurs de [déplacer leurs e-mails, contacts, tâches et informations de calendrier](https://support.microsoft.com/office/0996ece3-57c6-49bc-977b-0d1892e2aacc) après avoir configuré votre nouvel abonnement. Ils peuvent accéder à leur ancien e-mail en utilisant leur nom d’utilisateur initial, tel que sue@contoso.onmicrosoft.com.
  
### <a name="onedrive-for-business-data"></a>OneDrive Entreprise données :

Demandez aux utilisateurs de copier/synchroniser [OneDrive Entreprise contenu sur leur ordinateur](https://support.microsoft.com/office/59b1de2b-519e-4d3a-8f45-51647cf291cd), puis de le rajouter à leur nouvel abonnement.

### <a name="onenote"></a>OneNote 

Demandez aux utilisateurs de [sauvegarder OneNote](https://support.microsoft.com/office/back-up-notes-f58b34b0-611d-435e-87fa-7942a1767af4?ui=en-us&rs=en-us&ad=us) et [de restaurer des notes à partir d’une sauvegarde](https://support.microsoft.com/en-us/office/restore-notes-from-a-backup-5daf9cb0-6769-4998-a5de-f044fdd0d831?ui=en-us&rs=en-us&ad=us) vers leurs nouveaux abonnements.
