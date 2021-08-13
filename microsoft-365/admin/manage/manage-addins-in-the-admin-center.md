---
title: Gérer des compléments dans le centre d’administration
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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Découvrez comment utiliser des add-ins centralisés pour déployer des modules pour les utilisateurs et les groupes de votre organisation.
ms.openlocfilehash: a6eb234f9911b13616483456ef67866b99b4dee39fca90c2b16b272de2a85d62
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53825374"
---
# <a name="manage-add-ins-in-the-admin-center"></a>Gérer des compléments dans le centre d’administration

Office vous aident à personnaliser vos documents et à simplifier la façon dont vous accédez aux informations sur le web (voir Démarrer à l’aide de [votre Office).](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862) 

Une fois qu’un administrateur a déployé des modules pour les utilisateurs d’une organisation, il peut désactiver ou activer les modules, modifier, supprimer et gérer l’accès aux modules.

Pour plus d’informations sur l’installation des modules complémentaires à partir du Centre d’administration, voir Déployer des [modules complémentaires dans le Centre d’administration.](./manage-deployment-of-add-ins.md)
  
## <a name="add-in-states"></a>États de complément

Un add-in peut être à **l’état On** ou **Off.**
  
| État | Comment l’état se produit | Impact |
|:-----|:-----|:-----|
|**Actif**  <br/> |L’administrateur a chargé le module et l’a affecté à des utilisateurs ou des groupes.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté voient celui-ci dans les clients concernés.  <br/> |
|**Désactivé**  <br/> |Un administrateur a désactivé le complément.  <br/> |Les utilisateurs et les groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> Si l'état du complément est modifié en Actif, les utilisateurs et groupes ont de nouveau accès à celui-ci.  <br/> |
|**Deleted**  <br/> |Un administrateur a supprimé le complément.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> |
   
Envisagez de supprimer un add-in si personne ne l’utilise plus. Par exemple, la turning off an add-in might make sense if an add-in is used only during specific times of the year.

## <a name="delete-an-add-in"></a>Suppression d’un complément

Vous pouvez également supprimer un module qui a été déployé.

1. Dans le Centre d’administration, allez à la page **Paramètres**  >  **services & les modules.**

    > [!NOTE]
    > Vous pouvez également déployer des applications intégrées dans le Centre d’administration. [](test-and-deploy-microsoft-365-apps.md) Les applications intégrées sont visibles par les administrateurs Exchange général et les administrateurs. Si vous ne voyez pas les étapes ci-dessus, consultez la section Déploiement centralisé en Paramètres  >  **applications intégrées.** En haut de la page **Applications intégrées,** choisissez **Les applications.**

2. Sélectionnez le add-in déployé.

3. Cliquez sur **Supprimer le add-in.** Supprimez le bouton de la fonction de la fonction dans le coin inférieur droit.

4. Validez vos sélections, puis sélectionnez **Supprimer le complément**.

## <a name="edit-add-in-access"></a>Modification de l’accès d’un complément

Après le déploiement, les administrateurs peuvent également gérer l’accès des utilisateurs aux add-ins.

1. Dans le Centre d’administration, allez à la page **Paramètres**  >  **services & les modules.**

    > [!NOTE]
    > Vous pouvez également déployer des applications intégrées dans le Centre d’administration. [](test-and-deploy-microsoft-365-apps.md) Les applications intégrées sont visibles par les administrateurs Exchange général et les administrateurs. Si vous ne voyez pas les étapes ci-dessus, consultez la section Déploiement centralisé en Paramètres  >  **applications intégrées.** En haut de la page **Applications intégrées,** choisissez **Les applications.**


2. Sélectionnez le add-in déployé.

3. Cliquez sur **Modifier sous** **Qui’accès.**

4. Enregistrez les modifications.

## <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>Empêcher les téléchargements de Office sur tous les clients (sauf Outlook)

> [!NOTE]
> Outlook’installation du module est gérée par [un processus différent.](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins)

En tant qu’organisation, vous pouvez empêcher le téléchargement de nouveaux Office à partir du Office Store. Cela peut être utilisé conjointement avec le déploiement centralisé pour vous assurer que seuls les compléments approuvés par l’organisation sont déployés pour les utilisateurs au sein de votre organisation.
  
**Pour désactiver l’acquisition d’un add-in**
  
1. Dans le centre d’administration, cliquez sur la page **Paramètres** \> [Services &amp; Compléments](https://go.microsoft.com/fwlink/p/?linkid=2053743).

    > [!NOTE]
    > Vous pouvez également déployer des applications intégrées dans le Centre d’administration. [](test-and-deploy-microsoft-365-apps.md) Les applications intégrées sont visibles par les administrateurs Exchange général et les administrateurs. Si vous ne voyez pas les étapes ci-dessus, consultez la section Déploiement centralisé en Paramètres  >  **applications intégrées.** En haut de la page **Applications intégrées,** choisissez **Les applications.**

    
3. Sélectionnez **Applications et services appartenant aux utilisateurs**.
    
4. Désactivez l’option pour permettre aux utilisateurs d’accéder à Office Store.

    Cela empêche tous les utilisateurs d’acquérir les modules suivants dans le Store.
      
    - Les add-ins pour Word, Excel et PowerPoint 2016 à partir de :
        
      - Windows
      - Mac
      - Office
        
        
    - Acquisitions à partir **d’AppSource**
        
    - Les Microsoft 365
        
    Un utilisateur qui tente d’accéder au Store voit le message suivant : **Désolé, Microsoft 365** a été configuré pour empêcher l’acquisition individuelle de Office store.
  
La prise en charge de la Office Store est disponible dans les versions suivantes :
  
- Windows : 16.0.9001 - Actuellement disponible.
    
- Mac : 16.10.18011401 - Actuellement disponible.
    
- iOS : 2.9.18010804 - Actuellement disponible.
    
- Le site web - Actuellement disponible.
    
Cela n’empêche pas un administrateur d’utiliser le déploiement centralisé pour affecter un Office Store.

> [!NOTE] 
> Les add-ins tels que Visio Data Visualizer, Bing Cartes et People Graph s’afficheront toujours dans le ruban, même si un administrateur a désactivé le Store. Pour supprimer ces liens, les administrateurs doivent désactiver le Store via l’objet de stratégie de groupe (GPO).
  
Pour empêcher un utilisateur de se signer avec un compte Microsoft, vous pouvez restreindre l’accès pour utiliser uniquement le compte d’organisation. Pour plus d’informations, voir [Identité, authentification et autorisation dans Office 2016.](/DeployOffice/security/identity-authentication-and-authorization-in-office)  

> [!NOTE] 
> Le fait d’empêcher les utilisateurs d’accéder à l’Office Store les empêchera également de recharger une version test des Office pour les tester à partir [d’un partage réseau.](/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins)

## <a name="more-about-the-end-user-experience-with-add-ins"></a>En savoir plus sur l’expérience de l’utilisateur final avec les add-ins

Une fois que vous avez déployé un application, vos utilisateurs finaux peuvent commencer à l’utiliser dans leurs applications Office (voir Démarrer à l’aide de [votre Office).](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862) Le add-in apparaît sur toutes les plateformes qu’il prend en charge.
  
Si le complément prend en charge les commandes de complément, celles-ci apparaissent sur le ruban Office. Dans l'exemple suivant, la commande **Search Citation** (Rechercher une citation) apparaît pour le complément **Citations**. 

![Office ruban avec citations de recherche](../../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
Si le add-in déployé ne prend pas en charge les commandes de ce dernier ou si vous souhaitez afficher tous les modules, vous pouvez les afficher via Mes **modules.** 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a>Dans Word 2016, Excel 2016 ou PowerPoint 2016

1. Sélectionnez **\> Insérer mes modules.** 
    
2. Sélectionnez l'onglet **Géré par l'administrateur** dans la fenêtre Compléments Office. 
    
3. Double-cliquez sur le module que vous avez déployé précédemment (dans cet exemple, **Citations).**

    ![Onglet Géré par l’administrateur de la page Office de recherche](../../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)
  
### <a name="in-outlook"></a>Dans Outlook

1. Dans le **ruban Accueil,** **sélectionnez Obtenir des modules.**

    ![Bouton Store dans Outlook](../../media/getaddinsicon.png)
  
2. Sélectionnez **Géré par l’administrateur** dans le volet de navigation gauche. 

## <a name="related-content"></a>Contenu connexe

[Déployer des add-ins dans le Centre d’administration](./manage-deployment-of-add-ins.md) (article)\
En savoir plus sur la création et la [création de Office de développement](/office/dev/add-ins/overview/office-add-ins) (article)\
[Utiliser les cmdlets PowerShell](../../enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md) de déploiement centralisé pour gérer les add-ins (article)\
[Résolution des problèmes : l’utilisateur ne voit pas les modules](/office365/troubleshoot/access-management/user-not-seeing-add-ins) (article)\
[Mineurs et acquisition de Microsoft Store](./minors-and-acquiring-addins-from-the-store.md) (article)
