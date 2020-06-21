---
title: Gérer le déploiement des compléments dans le centre d’administration
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
ms.openlocfilehash: 25a4cd4147f6388cdbd8982eb10624e7b7e8f6cb
ms.sourcegitcommit: 659adf65d88ee44f643c471e6202396f1ffb6576
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44780120"
---
# <a name="manage-deployment-of-add-ins-in-the-microsoft-365-admin-center"></a>Gérer le déploiement de compléments dans le Centre d’administration Microsoft 365

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

[] Les compléments Office vous aident à personnaliser vos documents et à accéder plus simplement aux informations sur le web (voir [Commencer à utiliser votre complément Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). En tant qu’administrateur, vous pouvez déployer des compléments Office pour les utilisateurs de votre organisation. Vous pouvez effectuer cette opération à l’aide de la fonctionnalité déploiement centralisé dans le centre d’administration 365 de Microsoft.
  
Le déploiement centralisé est la méthode recommandée et la plus riche en fonctionnalités permettant à la plupart des administrateurs de déployer des compléments pour les utilisateurs et les groupes au sein d’une organisation. Pour plus d’informations sur la façon de déterminer si votre organisation peut prendre en charge le déploiement centralisé, reportez-vous à la rubrique [déterminer si un déploiement centralisé de compléments fonctionne pour votre organisation](centralized-deployment-of-add-ins.md).
  
Une déploiement centralisé offre les avantages suivants :
  
- Un administrateur général peut attribuer un complément directement à un utilisateur, à plusieurs utilisateurs via un groupe ou à tout le monde dans le client.
    
- When the relevant Office application starts, the add-in automatically downloads for the user. If the add-in supports add-in commands, the add-in automatically appears in the Ribbon within the Office application.
    
- Les compléments ne s’affichent plus pour les utilisateurs si l’administrateur désactive ou supprime le complément, ou si l’utilisateur est supprimé d’Azure Active Directory ou d’un groupe auquel le complément est affecté.
    
> [!NOTE]
>  Pour Word, Excel et PowerPoint utilisent un [catalogue d’applications SharePoint](https://dev.office.com/docs/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) pour déployer des compléments pour les utilisateurs dans un environnement local sans connexion à Microsoft 365 et/ou prise en charge des compléments SharePoint requis. > pour Outlook utilisez le panneau de configuration Exchange pour déployer dans un environnement local sans connexion à Microsoft 365. > 
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Approche recommandée pour le déploiement de compléments Office

Consider rolling out add-ins in a phased approach to help ensure your add-in deployment goes smoothly. We recommend the following plan:
  
1. Roll-out the add-in to a small set of business stakeholders and members of the IT department. Evaluate if the deployment was successful, and if so, move on to step 2.
    
2. Roll-out to a larger set of individuals within the business who will be using the add-in. Again, evaluate results and, if all went well, go to the next step of a full deployment.
    
3. Effectuez un déploiement complet vers un groupe cible d'utilisateurs.
    
Selon la taille du groupe cible, vous pouvez ajouter ou supprimer des étapes de déploiement.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Déploiement d’un complément Office à l’aide du centre d’administration

Avant de commencer, consultez [la rubrique déterminer si un déploiement centralisé de compléments fonctionne pour votre organisation](centralized-deployment-of-add-ins.md).

  
1. Dans le centre d’administration, accédez à **Settings** la \> page **compléments** de paramètres.
    
2. Sélectionnez **Déployer un complément** en haut de la page. Sur la page Vue d’ensemble, sélectionnez **Suivant**.
    
3. Sélectionnez une option et suivez les instructions.
  
4. Si vous avez sélectionné l’option d’ajout d’un complément à partir de l’Office Store, vous pouvez maintenant effectuer votre sélection de complément. Notez que vous pouvez afficher les compléments disponibles via l'une des catégories **Suggestions**, **Évaluation** ou **Nom**. Seuls les compléments gratuits peuvent être ajoutés à partir de l'Office Store. Les compléments payants ne sont pas pris en charge pour le moment. Une fois que vous avez sélectionné votre complément, vous devez accepter les termes et conditions supplémentaires pour pouvoir continuer. <br/><br/> Remarque : avec l’option Office Store, les mises à jour et les améliorations apportées au complément seront automatiquement mises à la disposition des utilisateurs sans votre intervention.

5. Sur la page suivante, sélectionnez **tout le monde**, **utilisateurs/groupes spécifiques** ou **seulement moi** pour spécifier les personnes vers lesquelles le complément est déployé. Utilisez la zone de recherche pour trouver les utilisateurs ou groupes vers lesquels vous voulez déployer le complément. <br/>Remarque : Découvrez les autres États qui s’appliquent à un complément. Consultez la section [États des compléments](#add-in-states) plus loin dans cette rubrique.
  
6. Sélectionnez **Déployer**.
  
7. Une coche verte apparaît lorsque le complément a été déployé. Vous pouvez suivre les instructions sur la page pour vérifier que le complément a bien été déployé.

> [!NOTE]
> Les utilisateurs devront peut-être relancer Office pour voir l’icône de complément apparaissent sur le ruban de l’application. Les compléments Outlook peuvent prendre jusqu’à 24 heures pour apparaître sur les rubans des utilisateurs.
    
8. Lorsque vous avez terminé, sélectionnez **suivant**. Si vous avez déjà déployé, vous pouvez sélectionner Modifier les utilisateurs **qui ont accès au complément** afin de le déployer sur un plus grand nombre d’utilisateurs.



Si vous avez déployé le complément vers des membres de votre organisation autre que vous-même, suivez les instructions affichées afin d’annoncer efficacement le déploiement du complément. <br/>Votre complément apparaît à présent avec d’autres applications dans Microsoft 365.
  
Il est recommandé d'informer les utilisateurs et les groupes vers lesquels vous déployez le complément afin qu'ils sachent que celui-ci est disponible. Songez à leur envoyer un courrier décrivant quand et comment utiliser le complément, et expliquant comment celui-ci peut les aider à mieux accomplir leur travail. Inclure ou créer un lien vers du contenu d’aide pertinent ou des questions fréquentes susceptibles d’aider les utilisateurs à rencontrer des problèmes avec le complément.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Points à considérer lors de l'affectation d'un complément à des utilisateurs et groupes

Admins can assign an add-in to everyone or to specific users and groups. Each option has implications:
  
- **Everyone**: As the name implies, this option assigns the add-in to every user in the tenant. Use this option sparingly and only for add-ins that are truly universal to your organization. 
    
- **Users**: If you assign an add-in to an individual user, then to deploy the add-in to a new user, you will need to first add that user. The same goes for removing users. 
    
- **Groups**: If you assign an add-in to a group, users who are added to the group will automatically be assigned the add-in. And, when a user is removed from a group, the user loses access to the add-in. In either case, no additional action is required from you as the admin. 

- **Je me contente**: Si vous affectez un complément à vous-même, le complément est affecté uniquement à votre compte. Cette solution est idéale si vous souhaitez tester le complément en premier.
    
L’option la plus adaptée à votre organisation dépend de votre configuration. Toutefois, nous vous recommandons d'effectuer les affectations via des groupes. En tant qu'administrateur, vous trouverez probablement plus facile de gérer les compléments à l'aide de groupes, et de contrôler l'appartenance aux groupes au lieu de devoir modifier à chaque fois les utilisateurs auxquels le complément est affecté. En revanche, dans certains cas, il peut être préférable de restreindre l'accès à un très petit groupe d'utilisateurs et donc d'affecter le complément à des utilisateurs spécifiques. Par conséquent, vous devez alors gérer manuellement les utilisateurs auxquels le complément est affecté.
  
### <a name="add-in-states"></a>États de complément

Un complément peut avoir l’état **activé** ou **désactivé** .
  
|**État**|**Comment l'état se produit**|**Impact**|
|:-----|:-----|:-----|
|**Active**  <br/> |Un administrateur a chargé le complément et l’a affecté à des utilisateurs ou à des groupes.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté voient celui-ci dans les clients concernés.  <br/> |
|**Désactivé**  <br/> |Un administrateur a désactivé le complément.  <br/> |Les utilisateurs et les groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> Si l'état du complément est modifié en Actif, les utilisateurs et groupes ont de nouveau accès à celui-ci.  <br/> |
|**Deleted**  <br/> |Un administrateur a supprimé le complément.  <br/> |Les utilisateurs et groupes auxquels le complément est affecté ne peuvent plus accéder à celui-ci.  <br/> |
   
Envisagez de supprimer un complément s’il n’est plus utilisé. Désactiver un complément peut être judicieux si celui-ci est utilisé uniquement à des moments spécifiques au cours d'une année.
  
### <a name="security-of-office-add-ins"></a>Sécurité des compléments Office

Office add-ins combine an XML manifest file that contains some metadata about the add-in, but most importantly points to a web application which contains all the code and logic. Add-ins can range in their capabilities. For example, add-ins can:
  
- afficher des données.
    
- lire le document d'un utilisateur pour fournir des services contextuels.
    
- lire et écrire des données vers le document d'un utilisateur et à partir de celui-ci pour fournir une valeur à cet utilisateur.
    
Pour plus d'informations sur les types et fonctionnalités des compléments Office, voir [Vue d'ensemble de la plateforme des compléments Office](https://go.microsoft.com/fwlink/p/?linkid=846362), notamment la section « Anatomie d'un complément Office ».
  
To interact with the user's document, the add-in needs to declare what permission it needs in the manifest. A five-level JavaScript API access-permissions model provides the basis for privacy and security for users of task pane add-ins. The majority of the add-ins in the Office Store are level ReadWriteDocument with almost all add-ins supporting at least the ReadDocument level. For more information about the permission levels, see [Requesting permissions for API use in content and task pane add-ins](https://go.microsoft.com/fwlink/p/?linkid=848863).
  
When updating a manifest, the typical changes are to an add-in's icon and text. Occasionally, add-in commands change. However, the permissions of the add-in do not change. The web application where all the code and logic for the add-in runs can change at any time, which is the nature of web applications.
  
Les mises à jour des compléments se produisent comme suit :
  
- **Line-of-business add-in:** In this case, where an admin explicitly uploaded a manifest, the add-in requires that the admin upload a new manifest file to support metadata changes. The next time the relevant Office applications start, the add-in will update. The web application can change at any time. 

    > [!NOTE]
    > L’administrateur n’a pas besoin de supprimer un complément LOB pour effectuer une mise à jour.   Dans la section compléments, l’administrateur peut simplement cliquer sur le complément LOB et cliquer sur le **bouton mettre à jour** dans le coin inférieur droit. La mise à jour ne fonctionnera que si la version du nouveau complément est supérieure à celle du complément existant.   
    
- **Office Store add-in:** When an admin selected an add-in from the Office Store, if an add-in updates in the Office Store, the add-in will update later in Centralized Deployment. The next time the relevant Office applications start, the add-in will update. The web application can change at any time. 

### <a name="edit-add-in-access"></a>Modifier l’accès au complément

Post-déploiement, les administrateurs peuvent également modifier l’accès des utilisateurs aux compléments.

1. Dans le centre d’administration, accédez à la page **paramètres**de  >  **& des compléments** .

2. Sélectionnez le complément déployé.

3. Cliquez sur **modifier** sous la rubrique **qui a accès**.
4. Enregistrez les modifications.
    
### <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>Empêcher les téléchargements de compléments en désactivant l’Office Store sur tous les clients (sauf Outlook)

> [!NOTE]
> L’installation d’un complément Outlook est gérée par un [autre processus](https://technet.microsoft.com/library/jj943754%28v=exchg.150%29.aspx).

En tant qu’organisation, vous souhaiterez peut-être empêcher le téléchargement de nouveaux compléments Office à partir de l’Office Store. Il peut être utilisé conjointement avec un déploiement centralisé afin de s’assurer que seuls les compléments approuvés par l’organisation sont déployés pour les utilisateurs au sein de votre organisation.
  
Pour désactiver l’acquisition de compléments :
  
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
  
Pour empêcher un utilisateur de se connecter à l’aide d’un compte Microsoft, vous pouvez limiter l’ouverture de session pour utiliser uniquement le compte d’organisation. Pour plus d’informations, consultez la [rubrique](https://technet.microsoft.com/library/jj683102%28v=office.16%29.aspx).
 
  
## <a name="minors-and-acquiring-add-ins-from-the-store"></a>Mineurs et acquisition de compléments à partir du magasin

Le règlement général sur la protection des données (RGPD) est un règlement de l’Union européenne qui devient effectif le 25 mai 2018. Il donne aux utilisateurs des droits et la protection de leurs données. L’un des aspects du RGPD est que les mineurs ne peuvent pas avoir leurs données personnelles envoyées aux parties que leur parent ou tuteur n’a pas approuvées. L’âge spécifique défini comme un mineur dépend de la région où se trouve la personne.
  
Les régions dont la réglementation statutaire est relative au consentement parental incluent les États-Unis, la Corée du Sud, le Royaume-Uni et l’Union européenne. Pour ces régions, un mineur est bloqué (via Azure Active Directory) pour obtenir les nouveaux compléments Office à partir du Store et exécuter des compléments qui ont été précédemment acquis. Pour les pays sans réglementation réglementaire, il n’y aura pas de restrictions de téléchargement.
  
Un utilisateur est considéré comme mineur en fonction des données spécifiées dans Azure Active Directory. L’administrateur client est responsable de la déclaration du groupe d’âge légal et de l’autorisation parentale pour cet utilisateur.
  
Si le parent/tuteur est accepté par un utilisateur secondaire à l’aide d’un complément spécifique, l’administrateur client peut utiliser un déploiement centralisé pour déployer ce complément sur tous les mineurs qui ont le consentement.
  
Pour être conforme à RGPD pour les mineurs, vous devez vous assurer que l’une des versions suivantes d’Office est déployée dans votre établissement scolaire ou votre organisation.
  
 **Pour Word, Excel, PowerPoint et Project**: 
  
|||
|:-----|:-----|
|**Plateforme** <br/> |**Numéro de build** <br/> |
|Applications Microsoft 365 pour les entreprises (canal actuel)  <br/> |9001,2138   <br/> |
|Applications Microsoft 365 pour Enterprise (canal d’entreprise semi-annuel)  <br/> |8431,2159  <br/> |
|Office 2016 pour Windows  <br/> |16.0.4672.1000  <br/> |
|Office 2013 pour Windows  <br/> |15.0.5023.1000  <br/> |
|Office 2016 pour Mac  <br/> |16.11.18020200  <br/> |
|Office pour le web  <br/> |N/A  <br/> |
   
 **Pour Outlook**: 
  
|||
|:-----|:-----|
|**Plateforme** <br/> |**Numéro de build** <br/> |
|Outlook 2016 pour Windows (MSI)  <br/> |Générer non TBD  <br/> |
|Outlook 2016 pour Windows (C2R)  <br/> |16.0.9323.1000  <br/> |
|Office 2016 pour Mac  <br/> |16.0.9318.1000  <br/> |
|Outlook Mobile pour iOS  <br/> |2.75.0  <br/> |
|Outlook Mobile pour Android  <br/> |2.2.145  <br/> |
|Outlook.com  <br/> |N/A  <br/> |
   
 **Configuration requise pour Office 2013**
  
Word, Excel et PowerPoint 2013 pour Windows prend en charge les mêmes vérifications mineures si la bibliothèque d’authentification Active Directory (ADAL) est activée. Il existe deux options pour la conformité, comme expliqué ci-dessous.
  
- **Activez Adal**. Cet article explique comment activer ADAL pour Office 2013 : utilisation de l' [authentification moderne Microsoft 365 avec les clients Office](https://docs.microsoft.com/office365/enterprise/modern-auth-for-office-2013-and-2016).<br/>Vous devez également définir les clés de Registre pour activer ADAL, comme expliqué dans la rubrique [activation de l’authentification moderne pour Office 2013 sur les appareils Windows](../security-and-compliance/enable-modern-authentication.md).<br/>En outre, vous devez installer les mises à jour d’avril suivantes pour Office 2013 :
    
  - [Description de la mise à jour de sécurité pour Office 2013:10 avril 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)
    
  - [2018 avril, mise à jour pour Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)
    
- **N’activez pas Adal**. Si vous ne parvenez pas à activer ADAL dans Office 2013, nous vous recommandons d’utiliser la stratégie de groupe pour désactiver le magasin pour les clients Office. Vous trouverez [ici](https://technet.microsoft.com/library/cc178992.aspx)des informations sur la façon de désactiver les paramètres de l’application pour Office.
    
## <a name="end-user-experience-with-add-ins"></a>Expérience des utilisateurs finaux avec les compléments

Now that you've deployed the add-in, your end users can start using it in their Office applications (see [Start using your Office Add-in](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). The add-in will appear on all platforms that the add-in supports.
  
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

## <a name="delete-the-add-in"></a>Supprimer le complément

Vous pouvez également supprimer un complément qui a été déployé.

1. Dans le centre d’administration, accédez à la page **paramètres**de  >  **& des compléments** .

2. Sélectionnez le complément déployé.

3. Cliquez sur **supprimer le complément**. Supprimez le bouton du complément dans le coin inférieur droit.
4. Validez vos sélections, puis sélectionnez **Supprimer le complément**.
  
## <a name="learn-more"></a>En savoir plus

Pour en savoir plus sur la création et la génération de compléments, voir [Compléments Office](https://go.microsoft.com/fwlink/p/?linkid=846362).
  
[Utilisez les cmdlets PowerShell de déploiement centralisé pour gérer les compléments](https://docs.microsoft.com/office365/enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins).
  
[Résolution des problèmes : l’utilisateur ne voit pas les compléments](https://docs.microsoft.com/office365/troubleshoot/access-management/user-not-seeing-add-ins)
