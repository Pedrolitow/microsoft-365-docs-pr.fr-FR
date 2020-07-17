---
title: Déployer des compléments dans le centre d’administration
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
ms.openlocfilehash: 4e9a3a4b7182bfd452c63abd03836623dc77260c
ms.sourcegitcommit: f7566dd6010744c72684efdc37f4471672330b61
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "45138243"
---
# <a name="deploy-add-ins-in-the-admin-center"></a>Déployer des compléments dans le centre d’administration

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

[] Les compléments Office vous aident à personnaliser vos documents et à accéder plus simplement aux informations sur le web (voir [Commencer à utiliser votre complément Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). En tant qu’administrateur, vous pouvez déployer des compléments Office pour les utilisateurs de votre organisation à l’aide de la fonctionnalité de déploiement centralisé dans le centre d’administration 365 de Microsoft. Le déploiement centralisé est la méthode recommandée et la plus riche en fonctionnalités permettant à la plupart des administrateurs de déployer des compléments pour les utilisateurs et les groupes au sein d’une organisation. 

Pour plus d’informations sur la façon de déterminer si votre organisation peut prendre en charge le déploiement centralisé, reportez-vous à la rubrique [déterminer si un déploiement centralisé de compléments fonctionne pour votre organisation](centralized-deployment-of-add-ins.md).

Pour en savoir plus sur la gestion des compléments après le déploiement, consultez [la rubrique gestion des compléments dans le centre d’administration](manage-addins-in-the-admin-center.md) .
  
> [!NOTE]
>  Pour Word, Excel et PowerPoint utilisent un [catalogue d’applications SharePoint](https://dev.office.com/docs/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) pour déployer des compléments pour les utilisateurs dans un environnement local sans connexion à Microsoft 365 et/ou prise en charge des compléments SharePoint requis. Pour Outlook, utilisez le panneau de configuration Exchange pour déployer dans un environnement local sans connexion à Microsoft 365.
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Approche recommandée pour le déploiement de compléments Office

Pour déployer des compléments à l’aide d’une approche progressive, nous vous recommandons d’effectuer les opérations suivantes :
  
1. Déployez le complément vers un petit groupe de parties intéressées et de membres du service informatique. Si le déploiement réussit, passez à l’étape 2.
    
2. Déployez le complément à d’autres personnes au sein de l’entreprise. Une fois encore, évaluez les résultats et, si elle réussit, poursuivez le déploiement complet.
    
3. Effectuer un déploiement complet pour tous les utilisateurs.
    
En fonction de la taille de l’audience cible, vous pouvez ajouter ou supprimer des étapes de déploiement.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Déploiement d’un complément Office à l’aide du centre d’administration

Avant de commencer, consultez [la rubrique déterminer si un déploiement centralisé de compléments fonctionne pour votre organisation](centralized-deployment-of-add-ins.md).
  
1. Dans le centre d’administration, accédez à **Settings** la \> page **compléments** de paramètres.
    
2. Sélectionnez **déployer un complément** en haut de la page, puis cliquez sur **suivant**.
    
3. Sélectionnez une option et suivez les instructions.
  
4. Si vous avez sélectionné l’option d’ajout d’un complément à partir de l’Office Store, effectuez votre sélection de complément. </br>

    Vous pouvez afficher les compléments disponibles par catégories : **suggestions pour vous**, **évaluation**ou **nom**. Seuls les compléments gratuits sont disponibles dans l’Office Store. Les compléments payants ne sont pas pris en charge pour le moment. Une fois que vous avez sélectionné un complément, acceptez les conditions requises pour continuer. <br/> 

    > [!NOTE] 
    > Avec l’option Office Store, les mises à jour et les améliorations sont apportées automatiquement aux utilisateurs.

5. Sur la page suivante, sélectionnez **Tout le monde**, **Utilisateurs/groupes spécifiques**ou **Moi uniquement** pour spécifier les personnes vers lesquelles le complément est déployé. Utilisez la zone de recherche pour rechercher des utilisateurs ou des groupes spécifiques. <br/>

    > [!NOTE] 
    > Pour en savoir plus sur les autres États qui s’appliquent à un complément, consultez la rubrique [États des compléments](https://docs.microsoft.com/microsoft-365/admin/manage/manage-addins-in-the-admin-center.md).
  
6. Sélectionnez **Déployer**.
  
7. Une coche verte apparaît lorsque le complément est déployé. Suivez les instructions sur la page pour tester le complément.

    > [!NOTE]
    > Il se peut que les utilisateurs doivent relancer Office pour afficher l’icône du complément sur le ruban de l’application. Les compléments Outlook peuvent prendre jusqu’à 24 heures pour apparaître sur les rubans des applications.
    
8. Lorsque vous avez terminé, sélectionnez **suivant**. Si vous avez déjà déployé, vous pouvez sélectionner Modifier les utilisateurs **qui ont accès au complément** pour le déployer sur un plus grand nombre d’utilisateurs.

    Si vous avez déployé le complément auprès d’autres membres de votre organisation, suivez les instructions pour annoncer le déploiement du complément. <br/>
  
    Il est recommandé d’informer les utilisateurs et les groupes que le complément déployé est disponible. Envisagez d’envoyer un courrier électronique qui décrit quand et comment utiliser le complément. Inclure ou créer un lien vers du contenu d’aide ou des FAQ susceptibles d’aider les utilisateurs s’ils ont des problèmes avec le complément.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Points à considérer lors de l'affectation d'un complément à des utilisateurs et groupes

Les administrateurs peuvent affecter un complément à tout le monde ou à des utilisateurs et groupes spécifiques. Chaque option a des conséquences spécifiques :
  
- **Tout le monde** Cette option affecte le complément à tous les utilisateurs de l’organisation. Utilisez-la avec parcimonie et uniquement pour les compléments qui sont réellement universels pour l'ensemble de votre organisation. 
    
- **Les utilisateurs** Si vous affectez un complément à un utilisateur individuel, puis que vous déployez le complément sur un nouvel utilisateur, vous devez d’abord ajouter le nouvel utilisateur.
    
- **Groupes** Si vous affectez un complément à un groupe, le complément est automatiquement affecté aux utilisateurs qui sont ajoutés au groupe. Lorsqu’un utilisateur est supprimé d’un groupe, il perd l’accès au complément. Dans les deux cas, aucune action supplémentaire n’est requise de l’administrateur. 

- **Moi-même** Si vous affectez un complément à vous-même, le complément est affecté uniquement à votre compte, ce qui est idéal pour tester le complément.
    
L’option appropriée pour votre organisation dépend de votre configuration. Toutefois, nous vous recommandons d’utiliser des groupes. En tant qu’administrateur, vous pouvez trouver plus facile de gérer les compléments à l’aide de groupes et de contrôler l’appartenance à ces groupes plutôt que d’affecter des utilisateurs individuels à chaque fois. Dans certains cas, vous souhaiterez peut-être limiter l’accès à un petit ensemble d’utilisateurs en effectuant des affectations à des utilisateurs spécifiques en affectant manuellement les utilisateurs.
  
## <a name="more-about-office-add-ins-security"></a>En savoir plus sur la sécurité des compléments Office

Les compléments Office combinent un fichier manifeste XML qui inclut certaines métadonnées sur le complément, mais surtout qui pointe vers une application web contenant tout le code et la logique. Les fonctionnalités des compléments peuvent varier. Par exemple, les compléments peuvent :
  
- afficher des données.
    
- lire le document d'un utilisateur pour fournir des services contextuels.
    
- lire et écrire des données vers le document d'un utilisateur et à partir de celui-ci pour fournir une valeur à cet utilisateur.
    
Pour plus d'informations sur les types et fonctionnalités des compléments Office, voir [Vue d'ensemble de la plateforme des compléments Office](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins), notamment la section « Anatomie d'un complément Office ».
  
Pour interagir avec le document de l'utilisateur, le complément doit déclarer les autorisations dont il a besoin dans le fichier manifeste. Un modèle d'autorisations d'accès d'une API JavaScript à cinq niveaux fournit la base de la confidentialité et de la sécurité pour les utilisateurs des compléments du volet Office. La plupart des compléments de l'Office Store sont au niveau ReadWriteDocument. Presque tous les compléments prennent en charge le niveau ReadDocument au minimum. Pour plus d'informations sur les niveaux d'autorisation, voir [Demande d'autorisations pour l'utilisation d'API dans les compléments de contenu et du volet Office](https://docs.microsoft.com/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins).
  
Lors de la mise à jour d'un manifeste, les modifications standard sont apportées à l'icône et au texte d'un complément. Les commandes de complément changent parfois, contrairement aux autorisations du complément. L'application web dans laquelle le code et la logique du complément sont exécutés peut changer à tout moment, ce qui est la nature même des applications web.
  
Les mises à jour des compléments se produisent comme suit :
  
- **Complément métier :** dans ce cas, lorsqu'un administrateur a chargé explicitement un manifeste, le complément nécessite que l'administrateur charge un nouveau fichier manifeste pour prendre en charge la modification des métadonnées. Le complément est mis à jour au démarrage suivant des applications Office concernées. L'application web peut changer à tout moment. 

    > [!NOTE]
    > L’administrateur n’a pas besoin de supprimer un complément LOB pour effectuer une mise à jour.   Dans la section compléments, l’administrateur peut simplement cliquer sur le complément LOB et cliquer sur le **bouton mettre à jour** dans le coin inférieur droit. La mise à jour ne fonctionnera que si la version du nouveau complément est supérieure à celle du complément existant.   
    
- **Complément de l'Office Store :** lorsqu'un administrateur a sélectionné un complément à partir de l'Office Store, si un complément est mis à jour dans l'Office Store, le complément sera mis à jour plus tard dans le déploiement centralisé. Le complément est mis à jour au démarrage suivant des applications Office concernées. L'application web peut changer à tout moment. 
  
## <a name="learn-more"></a>En savoir plus

[Gérer des compléments dans le centre d’administration](manage-addins-in-the-admin-center.md)

[Création de compléments Office](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins-fundamentals).

[Mineurs et acquisition de compléments à partir du magasin](minors-and-acquiring-addins-from-the-store.md)
  
[Utiliser les cmdlets PowerShell de déploiement centralisé pour gérer les compléments](https://docs.microsoft.com/office365/enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins)
  
[Résolution des problèmes : l’utilisateur ne voit pas les compléments](https://docs.microsoft.com/office365/troubleshoot/access-management/user-not-seeing-add-ins)
