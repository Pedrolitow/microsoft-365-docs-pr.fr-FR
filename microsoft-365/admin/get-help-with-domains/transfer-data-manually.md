---
title: Transférer des données manuellement entre deux comptes
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ms.assetid: 7dc5d983-84b2-4802-bef0-602ae1780a42
description: Découvrez comment transférer des données manuellement entre deux comptes Microsoft 365 lorsque vous avez modifié le plan ou le nom de la société, ou combiné plusieurs abonnements en un seul.
ms.openlocfilehash: 1297e2d55692262be55b166dacc56cb89cc6c8a0
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47948723"
---
# <a name="transfer-data-manually-between-two-accounts"></a>Transférer des données manuellement entre deux comptes

Préparez-vous à cumuler vos manches et à bloquer un intervalle de temps sur votre calendrier : le transfert de données entre deux comptes Microsoft 365 est un processus manuel, complexe et long. Il ne s’agit pas d’un processus automatisé ou pris en charge. Nous allons commencer.
  
> [!CAUTION]
> Le processus dans lequel le courrier électronique, Skype entreprise et un site Web public hébergé sur Microsoft 365 ne fonctionnera pas. Les utilisateurs obtiennent les nouveaux noms d’utilisateur et mots de passe, et ils doivent réinitialiser Outlook.

**Transférez les données manuellement à l’aide des instructions de cette rubrique si l’une des conditions suivantes s’applique :**
  
- Vous devez passer à un plan dans une autre famille de services.

- Le nom de votre société a changé et vous avez décidé de créer un nouvel abonnement et de migrer vos données, car vous voulez utiliser des noms de domaine initiaux différents.

- Vous devez combiner plusieurs abonnements en un seul.

> [!IMPORTANT]
> Si vous avez besoin de [modifier votre plan d’abonnement](../../commerce/subscriptions/switch-to-a-different-plan.md) et que vous pouvez utiliser l’Assistant changer de plan, ou si vous devez effectuer un transfert vers un nouveau plan d’abonnement dans la même famille d’abonnements, même si l’Assistant changer de plan ne fonctionne pas, vous n’avez pas besoin de transférer manuellement vos données et il n’y a pas de temps d’indisponibilité.

|**Tâches**|**Étapes**|
|:-----|:-----|
|Achetez le plan vers lequel vous souhaitez vous déplacer.  <br/> |Lorsque vous vous inscrivez, vous spécifiez le nom de la société à utiliser dans les noms de domaine initiaux :  *yourcompany*  . onmicrosoft.com,  *yourcompany*  -public.sharepoint.com et  *yourcompany*  . SharePoint.com. Vous devez utiliser un nom  *yourcompany*  différent de celui que vous avez utilisé pour les abonnements existants.  <br/> > [!NOTE]> il faut généralement un minimum de plusieurs mois après l’annulation d’un abonnement pour libérer les noms de domaine initiaux qui utilisent  *yourcompany*  de nos systèmes. Même si vous envisagez d’enregistrer toutes vos données à partir de votre ancien abonnement Microsoft 365 et d’annuler cet abonnement, l’ancienne valeur  *yourcompany*  n’est pas immédiatement disponible pour une utilisation dans un nouvel abonnement.           |
|Supprimez votre domaine personnalisé de votre ancien abonnement Microsoft 365.  <br/> | Suivez les [étapes requises avant de supprimer un domaine](remove-a-domain.md) afin de supprimer le nom de domaine des adresses de messagerie des utilisateurs et de supprimer les enregistrements DNS pour le courrier électronique et Lync pour le domaine personnalisé. Si vous hébergez votre site Web public sur Microsoft 365, vous devez également supprimer l’enregistrement CNAMe qui pointe vers celui-ci.  <br/> > [!IMPORTANT]> après avoir supprimé l’enregistrement MX qui achemine le courrier vers ce domaine personnalisé, le courrier électronique cessera de fonctionner jusqu’à ce que vous ayez ajouté le domaine à votre nouveau compte, configurez le nouvel enregistrement MX et configurez vos utilisateurs. Lorsque vous supprimez les enregistrements DNS pour Lync, Lync cessera de fonctionner. Et après avoir supprimé l’enregistrement CNAMe qui pointe vers votre site Web public, il ne sera pas disponible.           [Supprimez le domaine](remove-a-domain.md) .  <br/> |
|Configurez votre domaine personnalisé pour votre nouvel abonnement et configurez vos utilisateurs.  <br/> | Configurez votre nouvel abonnement, y compris la création des enregistrements DNS requis pour votre domaine personnalisé.  <br/>  Créez vos utilisateurs, avec des adresses de messagerie sur votre domaine personnalisé.  <br/> |
|Transférer des données de votre ancien abonnement à votre nouvel abonnement.  <br/> | Connectez-vous aux deux comptes dans des fenêtres de navigateur distinctes :  <br/>  Cliquez avec le bouton droit sur l’icône de votre navigateur et ouvrez deux fenêtres de navigateur privé. Vous pouvez utiliser des informations d’identification différentes dans les deux fenêtres pour vous connecter aux deux comptes.  <br/> [Transférer les paramètres d’administration entre les abonnements](#email) <br/> [Transférer la structure et les données d’un site d’équipe](#transfer-team-site-structure-and-data) <br/> [Transférer un site Web public entre les abonnements](#transfer-a-public-website-between-subscriptions) <br/> [Transférer les paramètres d’administration entre les abonnements](#email) <br/> |
|Annulez l’abonnement pour le plan que vous avez obtenu en appelant le support Microsoft pour Microsoft 365.  <br/> | Vérifiez que votre nouvel abonnement fonctionne et que toutes les données ont été transférées.  <br/>  [Contactez le support](../contact-support-for-business-products.md) technique pour annuler votre ancien abonnement.  <br/> |

## <a name="transfer-administrative-settings-between-subscriptions"></a>Transférer les paramètres d’administration entre les abonnements

Accédez aux pages suivantes sur chaque compte, puis configurez le nouveau compte en fonction des paramètres de l’ancien compte.
  
Si vous transférez des données de Microsoft 365 vers Microsoft 365 Midmarket ou Microsoft 365 Enterprise, les pages d’administration sont structurées différemment. Regardez une [vidéo : présentation de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/admin/)et accédez aux paramètres d’administration suivants.
  
Pour Microsoft 365 entreprise et Microsoft 365 moyenne entreprise :
  
|**Location**|**Objectif**|
|:-----|:-----|
|**Administrateur** \> **Microsoft 365** \> **Paramètres de service** <br/> |Sélectionnez chaque onglet pour les paramètres de messagerie, sites, Lync, logiciel utilisateur, mots de passe, communauté, gestion des droits et mobile.  <br/> |
|**Administrateur** \> **Exchange** <br/> | Paramètres Exchange Online  <br/> |
|**Administrateur** \> **SharePoint** <br/> | Paramètres SharePoint Online  <br/> |
|**Administrateur** \> **Skype entreprise** <br/> |Paramètres supplémentaires de Skype entreprise  <br/> |

Pour Microsoft 365 petite entreprise
  
|**Location**|**Objectif**|
|:-----|:-----|
|**Administrateur** \> **Gérer les paramètres à l’échelle de l’organisation** <br/> |Paramètres d’administration  <br/> |

## <a name="transfer-a-public-website-between-subscriptions"></a>Transférer un site Web public entre les abonnements

Si vous disposez d’un site Web public hébergé sur Microsoft 365, vous devez l’enregistrer et le recréer sur votre nouvel abonnement.
  
> [!NOTE]
> Si votre site Web public est hébergé auprès d’un fournisseur d’hébergement DNS, aucune modification n’est requise. Elle n’est pas affectée par votre transition.
  
Pour enregistrer une bibliothèque de documents ou un contenu de liste à partir d’un environnement SharePoint Online vers des partages de fichiers ou vers un ordinateur local, voir [migration manuelle de contenu SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=402910).
  
> [!NOTE]
> L’application de migration de site public ne peut pas transférer de données vers un autre abonnement.
  
## <a name="transfer-team-site-structure-and-data"></a>Transférer la structure et les données d’un site d’équipe

Il existe plusieurs façons d’enregistrer ou de transférer des données de site d’équipe :
  
- Vous pouvez enregistrer l’ancien site en tant que modèle et importer le modèle dans le nouveau site.

- Pour transférer des documents, commencez par recréer manuellement votre hiérarchie sur le nouveau site. Vous pouvez ensuite ouvrir les deux sites d’équipe SharePoint simultanément, ouvrir les deux bibliothèques de documents à l’aide de l’Explorateur Windows et copier-coller les documents. Consultez la [vidéo : copier ou déplacer des fichiers de bibliothèque à l’aide de la fonction ouvrir avec l’Explorateur](https://support.microsoft.com/office/c7c20284-bc94-47f4-9728-d28e9daf0790).

- Pour transférer des données de liste, enregistrez un [modèle de liste](https://support.microsoft.com/office/c3884ad1-bc49-44b8-b3d6-3bc6a01eb393)et utilisez le modèle enregistré pour recréer la liste sur le nouveau site.

- Pour enregistrer une bibliothèque de documents ou un contenu de liste à partir d’un environnement SharePoint Online (OneDrive entreprise ou sites d’équipe) vers des partages de fichiers ou vers un ordinateur local, voir [informations sur la migration manuelle du contenu SharePoint Online](https://support.microsoft.com/kb/2783484).

## <a name="transfer-users-data-between-subscriptions"></a>Transférer les données des utilisateurs entre les abonnements

### <a name="email"></a>Messagerie:

Demandez aux utilisateurs de [déplacer leurs courriers électroniques, contacts, tâches et informations de calendrier](https://support.microsoft.com/office/0996ece3-57c6-49bc-977b-0d1892e2aacc) après avoir configuré votre nouvel abonnement. Ils peuvent accéder à leur ancien courrier électronique à l’aide de leur nom d’utilisateur initial, par exemple sue@contoso.onmicrosoft.com.
  
### <a name="onedrive-for-business-data"></a>Données OneDrive entreprise :

Demandez aux utilisateurs de copier/synchroniser le [contenu OneDrive entreprise sur leur ordinateur](https://support.microsoft.com/office/59b1de2b-519e-4d3a-8f45-51647cf291cd), puis rajoutez-le à leur nouvel abonnement.

### <a name="onenote"></a>OneNote 

Demandez aux utilisateurs de [sauvegarder OneNote](https://support.microsoft.com/office/back-up-notes-f58b34b0-611d-435e-87fa-7942a1767af4?ui=en-us&rs=en-us&ad=us) et de [restaurer des notes à partir d’une sauvegarde](https://support.microsoft.com/en-us/office/restore-notes-from-a-backup-5daf9cb0-6769-4998-a5de-f044fdd0d831?ui=en-us&rs=en-us&ad=us) vers leurs nouveaux abonnements.
