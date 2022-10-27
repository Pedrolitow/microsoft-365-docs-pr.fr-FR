---
title: Gérer des compléments dans le centre d’administration
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
- Adm_NonTOC
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Découvrez comment utiliser des compléments centralisés pour déployer des compléments sur des utilisateurs et des groupes de votre organisation.
ms.openlocfilehash: f6e26af9bdc6379b89474c36173fa263fc1ab5aa
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68731258"
---
# <a name="manage-add-ins-in-the-microsoft-365-admin-center"></a>Gérer les compléments dans le Centre d'administration Microsoft 365

Les compléments Office vous aident à personnaliser vos documents et à simplifier la façon dont vous accédez aux informations sur le web. Voir [Commencer à utiliser votre complément Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 

Une fois qu’un administrateur général ou Exchange a déployé des compléments pour les utilisateurs d’une organisation, il peut désactiver ou activer les compléments, modifier, supprimer et gérer l’accès aux compléments.

Pour plus d’informations sur l’installation de compléments à partir du centre d’administration, consultez [Déployer des compléments dans le centre d’administration](./manage-deployment-of-add-ins.md).
  
## <a name="add-in-states"></a>États de complément

Un complément peut être à l’état **Activé** ou **Désactivé** .
  
| État | Comment l’état se produit | Impact |
|:-----|:-----|:-----|
|**Actif**  <br/> |Administration chargé le complément et l’a affecté à des utilisateurs ou des groupes.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté voient celui-ci dans les clients concernés.  <br/> |
|**Désactivé**  <br/> |Un administrateur a désactivé le complément.  <br/> |Les utilisateurs et les groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> Si l'état du complément est modifié en Actif, les utilisateurs et groupes ont de nouveau accès à celui-ci.  <br/> |
|**Deleted**  <br/> |Un administrateur a supprimé le complément.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> |
   
Envisagez de supprimer un complément si personne ne l’utilise plus. Par exemple, la désactivation d’un complément peut avoir un sens si un complément est utilisé uniquement à des moments spécifiques de l’année.

## <a name="delete-an-add-in"></a>Suppression d’un complément

Vous pouvez également supprimer un module qui a été déployé.

1. Dans le Centre d’administration, accédez à la page **Paramètres** > **Applications intégrées** .

2. Sélectionnez le complément déployé, puis **l’onglet Configuration.**

3. Dans le volet **Configuration** , accédez à **Paramètres** > **avancés Compléments**.

4. Sélectionnez de nouveau le module dans la liste.

5. Choisir **Supprimer les compléments** Supprimez le bouton du complément dans le coin inférieur droit.

6. Validez vos sélections, puis choisissez **Supprimer.**

## <a name="edit-add-in-access"></a>Modification de l’accès d’un complément

Après le déploiement, les administrateurs peuvent également gérer l'accès des utilisateurs aux modules complémentaires.

1. Dans le Centre d’administration, accédez à la page **Paramètres** > **Applications intégrées** .

2. Sélectionnez l'add-in déployé.

3. Cliquez sur **Modifier sous** **Qui a accès.**

4. Enregistrez les modifications.

## <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>Empêcher les téléchargements de compléments en désactivant l’Office Store sur tous les clients (à l’exception d’Outlook)

> [!NOTE]
> L’installation du complément Outlook est gérée par un [autre processus](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins).

En tant qu’organisation, vous souhaiterez peut-être empêcher le téléchargement de nouveaux compléments Office à partir de l’Office Store. Cela peut être utilisé conjointement avec le déploiement centralisé pour garantir que seuls les compléments approuvés par l’organisation sont déployés sur les utilisateurs au sein de votre organisation.
  
**Pour désactiver l’acquisition de compléments**
  
1. Dans le Centre d’administration, accédez à la page **Paramètres** \> [Paramètres De l’organisation](https://go.microsoft.com/fwlink/p/?linkid=2053743) .

2. Sélectionnez **Applications et services appartenant aux utilisateurs**.
    
3. Désactivez l’option pour permettre aux utilisateurs d’accéder à Office Store.

    Cela empêche tous les utilisateurs d’acquérir les modules suivants dans le Store.
      
    - Les compléments pour Word, Excel et PowerPoint 2016 à partir de :
        
      - Windows
      - Mac
      - Bureau
        
        
    - Acquisitions à partir **d’AppSource**
        
    - Compléments dans Microsoft 365
        
    Un utilisateur qui tente d’accéder au Magasin voit le message suivant : **Désolé, Microsoft 365 a été configuré pour empêcher l’acquisition individuelle de compléments Office Store.**
  
La prise en charge de la désactivation de l’Office Store est disponible dans les versions suivantes :
  
- Windows : 16.0.9001 - Actuellement disponible.
    
- Mac : 16.10.18011401 - Actuellement disponible.
    
- iOS : 2.9.18010804 - Actuellement disponible.
    
- Le web - Actuellement disponible.
    
Cela n’empêche pas un administrateur d’utiliser le déploiement centralisé pour affecter un complément à partir de l’Office Store.

> [!NOTE] 
> Les compléments tels que Visio Data Visualizer, Bing Cartes et Personnes Graph s’affichent toujours dans le ruban, même si un administrateur a désactivé le Windows Store. Pour supprimer ces liens, les administrateurs doivent désactiver le Store via stratégie de groupe Object (GPO).
  
Pour empêcher un utilisateur de se connecter avec un compte Microsoft, vous pouvez restreindre l’ouverture de session pour utiliser uniquement le compte d’organisation. Pour plus d’informations, voir [Identité, authentification et autorisation dans Office 2016](/DeployOffice/security/identity-authentication-and-authorization-in-office).  

> [!NOTE] 
> Empêcher les utilisateurs d’accéder à l’Office Store les empêche également de charger une version test des [compléments Office à des fins de test à partir d’un partage réseau](/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins).

## <a name="more-about-the-end-user-experience-with-add-ins"></a>En savoir plus sur l’expérience de l’utilisateur final avec les compléments

Une fois que vous avez déployé un complément, vos utilisateurs finaux peuvent commencer à l’utiliser dans leurs applications Office. Le complément apparaît sur toutes les plateformes prises en charge par le complément. Voir [Commencer à utiliser votre complément Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 
  
If the add-in supports add-in commands, the commands appear on the Office ribbon. In the following example, the command **Search Citation** appears for the **Citations** add-in. 

![Ruban Office avec citations de recherche.](../../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
Si le complément déployé ne prend pas en charge les commandes de complément ou si vous souhaitez afficher tous les compléments déployés, vous pouvez les afficher via **Mes compléments**. 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a>Dans Word 2016, Excel 2016 ou PowerPoint 2016

1. Sélectionnez **Insérer \> mes compléments**. 
    
2. Sélectionnez l'onglet **Géré par l'administrateur** dans la fenêtre Compléments Office. 
    
3. Double-cliquez sur le complément que vous avez déployé précédemment (dans cet exemple, **Citations**).

    ![Administration onglet Géré de la page Compléments Office.](../../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)
  
### <a name="in-outlook"></a>Dans Outlook

1. Dans le ruban **Accueil** , sélectionnez **Obtenir des compléments**.

    ![Bouton Stocker dans Outlook.](../../media/getaddinsicon.png)
  
2. Sélectionnez **Géré par l’administrateur** dans le volet de navigation gauche. 

## <a name="related-content"></a>Contenu associé

[Mineurs et acquisition de compléments à partir du Microsoft Store](./minors-and-acquiring-addins-from-the-store.md)

