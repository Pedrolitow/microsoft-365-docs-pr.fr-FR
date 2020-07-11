---
title: Gérer les compléments dans le centre d’administration
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
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Découvrez comment déployer des compléments pour les utilisateurs et les groupes de votre organisation à l’aide du déploiement centralisé dans le centre d’administration.
ms.openlocfilehash: caaea8404c099f56704d21684323a4b20e61f52d
ms.sourcegitcommit: 222fc3f8841de82b1b558f47db8a79aa5054d0ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2020
ms.locfileid: "45103098"
---
# <a name="manage-add-ins-in-the-admin-center"></a>Gérer les compléments dans le centre d’administration

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

Les compléments Office vous permettent de personnaliser vos documents et de rationaliser le mode d’accès aux informations sur le Web (voir [commencer à utiliser votre complément Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). 

Une fois qu’un administrateur déploie des compléments pour les utilisateurs d’une organisation, l’administrateur peut désactiver ou activer les compléments, modifier, supprimer et gérer l’accès aux compléments.

Pour plus d’informations sur l’installation des compléments à partir du centre d’administration, consultez [la rubrique deploy Add-ins in the Admin Center](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins).
  
## <a name="add-in-states"></a>États de complément

Un complément peut avoir l’état **activé** ou **désactivé** .
  
|**État**|**Comment l'état se produit**|**Impact**|
|:-----|:-----|:-----|
|**Active**  <br/> |Un administrateur a chargé le complément et l’a affecté à des utilisateurs ou à des groupes.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté voient celui-ci dans les clients concernés.  <br/> |
|**Désactivé**  <br/> |Un administrateur a désactivé le complément.  <br/> |Les utilisateurs et les groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> Si l'état du complément est modifié en Actif, les utilisateurs et groupes ont de nouveau accès à celui-ci.  <br/> |
|**Deleted**  <br/> |Un administrateur a supprimé le complément.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> |
   
Envisagez de supprimer un complément s’il n’est plus utilisé. Par exemple, la désactivation d’un complément peut être utile si un complément est utilisé uniquement à des moments spécifiques de l’année.

## <a name="delete-an-add-in"></a>Suppression d’un complément

Vous pouvez également supprimer un complément qui a été déployé.

1. Dans le centre d’administration, accédez à la page **paramètres**de  >  **& des compléments** .

2. Sélectionnez le complément déployé.

3. Cliquez sur **supprimer le complément**. Supprimez le bouton du complément dans le coin inférieur droit.

4. Validez vos sélections, puis sélectionnez **Supprimer le complément**.

## <a name="edit-add-in-access"></a>Modification de l’accès d’un complément

Post-déploiement, les administrateurs peuvent également gérer l’accès des utilisateurs aux compléments.

1. Dans le centre d’administration, accédez à la page **paramètres**de  >  **& des compléments** .

2. Sélectionnez le complément déployé.

3. Cliquez sur **modifier** sous la rubrique **qui a accès**.

4. Enregistrez les modifications.

## <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>Empêcher les téléchargements de compléments en désactivant l’Office Store sur tous les clients (sauf Outlook)

> [!NOTE]
> L’installation d’un complément Outlook est gérée par un [autre processus](https://technet.microsoft.com/library/jj943754%28v=exchg.150%29.aspx).

En tant qu’organisation, vous souhaiterez peut-être empêcher le téléchargement de nouveaux compléments Office à partir de l’Office Store. Il peut être utilisé conjointement avec un déploiement centralisé afin de s’assurer que seuls les compléments approuvés par l’organisation sont déployés pour les utilisateurs au sein de votre organisation.
  
**Pour désactiver l’acquisition du complément**
  
1. Dans le centre d’administration, cliquez sur la page **Paramètres** \> [Services &amp; Compléments](https://go.microsoft.com/fwlink/p/?linkid=2053743).
    
3. Sélectionnez **Applications et services appartenant aux utilisateurs**.
    
4. Désactivez l’option pour permettre aux utilisateurs d’accéder à Office Store.

Cela empêchera tous les utilisateurs d’acquérir les compléments suivants à partir de la Banque.
  
- Compléments pour Word, Excel et PowerPoint 2016 à partir de :
    
  - Windows
    
  - Mac
    
  - Office
    
    
- Acquisitions à partir de **AppSource**
    
- Compléments dans Microsoft 365
    
Un utilisateur qui tente d’accéder au magasin verra apparaître le message suivant : « **Désolé, Microsoft 365 a été configuré pour empêcher l’acquisition individuelle de compléments de l’Office Store.**
  
La prise en charge de la désactivation de l’Office Store est disponible dans les versions suivantes :
  
- Windows : 16.0.9001 actuellement disponible.
    
- Mac : 16.10.18011401-actuellement disponible.
    
- iOS : 2.9.18010804-actuellement disponible.
    
- Le Web est actuellement disponible.
    
Cela n’empêche pas un administrateur d’utiliser un déploiement centralisé pour affecter un complément à partir de l’Office Store.
  
Pour empêcher un utilisateur de se connecter à l’aide d’un compte Microsoft, vous pouvez limiter l’ouverture de session pour utiliser uniquement le compte d’organisation. Pour plus d’informations, voir [identité, authentification et autorisation dans Office 2016](https://technet.microsoft.com/library/jj683102%28v=office.16%29.aspx).  

## <a name="more-about-the-end-user-experience-with-add-ins"></a>En savoir plus sur l’expérience de l’utilisateur final avec les compléments

Une fois que vous avez déployé un complément, vos utilisateurs finaux peuvent commencer à l’utiliser dans leurs applications Office (voir [commencer à utiliser votre complément Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). Le complément apparaît sur toutes les plateformes prises en charge par le complément.
  
If the add-in supports add-in commands, the commands appear on the Office ribbon. In the following example, the command **Search Citation** appears for the **Citations** add-in. 

![Ruban Office avec des citations de recherche](../../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
Si le complément déployé ne prend pas en charge les commandes de complément ou si vous souhaitez afficher tous les compléments déployés, vous pouvez les consulter via **mes compléments**. 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a>Dans Word 2016, Excel 2016 ou PowerPoint 2016

1. Sélectionnez **insérer \> mes compléments**. 
    
2. Sélectionnez l'onglet **Géré par l'administrateur** dans la fenêtre Compléments Office. 
    
3. Double-cliquez sur le complément que vous avez déployé précédemment (dans cet exemple, **Citations** ). <br/>![Onglet géré par l’administrateur de la page compléments Office](../../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)
  
### <a name="in-outlook"></a>Dans Outlook

1. Sur le ruban **Accueil** , sélectionnez **obtenir des compléments**.<br/>![Bouton Store dans Outlook](../../media/getaddinsicon.png)
  
2. Sélectionnez **Géré par l’administrateur** dans le volet de navigation gauche. 

## <a name="learn-more"></a>En savoir plus

[Déployer des compléments dans le centre d’administration](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins)

Pour en savoir plus sur la création et la génération de compléments, voir [Compléments Office](https://go.microsoft.com/fwlink/p/?linkid=846362).
  
[Utilisez les cmdlets PowerShell de déploiement centralisé pour gérer les compléments](https://docs.microsoft.com/office365/enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins).
  
[Résolution des problèmes : l’utilisateur ne voit pas les compléments](https://docs.microsoft.com/office365/troubleshoot/access-management/user-not-seeing-add-ins)

[Mineurs et acquisition de compléments à partir du Microsoft Store](https://docs.microsoft.com/microsoft-365/admin/manage/minors-and-acquiring-addins-from-the-store)