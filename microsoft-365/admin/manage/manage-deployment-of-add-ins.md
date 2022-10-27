---
title: Déployer des compléments dans le centre d’administration
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
- Tier3
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Découvrez comment déployer des compléments sur des utilisateurs et des groupes de votre organisation à l’aide du déploiement centralisé dans le centre d’administration.
ms.openlocfilehash: ad44b5c415507dfbd9944f460da963e39b582b36
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68733854"
---
# <a name="deploy-add-ins-in-the-microsoft-365-admin-center"></a>Déployer des compléments dans le Centre d'administration Microsoft 365

Les compléments Office vous aident à personnaliser vos documents et à simplifier la façon dont vous accédez aux informations sur le web (voir [Commencer à utiliser votre complément Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). En tant qu’administrateur, vous pouvez déployer des compléments Office pour les utilisateurs de votre organisation à l’aide de la fonctionnalité Déploiement centralisé dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>. Le déploiement centralisé est le moyen recommandé et le plus riche en fonctionnalités pour la plupart des administrateurs de déployer des compléments sur des utilisateurs et des groupes au sein d’une organisation.

Pour plus d’informations sur la façon de déterminer si votre organisation peut prendre en charge le déploiement centralisé, consultez [Déterminer si le déploiement centralisé de compléments fonctionne pour votre organisation](centralized-deployment-of-add-ins.md).

Pour en savoir plus sur la gestion des compléments après le déploiement, consultez [Gérer les compléments dans le Centre d’administration](manage-addins-in-the-admin-center.md)
  
> [!NOTE]
>  Pour Word, Excel et PowerPoint utilisent un catalogue d’applications [SharePoint](/office/dev/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) pour déployer des compléments pour les utilisateurs dans un environnement local sans connexion à Microsoft 365 et/ou prise en charge des compléments SharePoint requis. Pour Outlook, utilisez le panneau de configuration Exchange pour effectuer un déploiement dans un environnement local sans connexion à Microsoft 365.
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Approche recommandée pour le déploiement des compléments Office

Pour déployer des compléments à l’aide d’une approche par phases, nous vous recommandons ce qui suit :
  
1. Déployez le complément vers un petit groupe de parties intéressées et de membres du service informatique. Si le déploiement réussit, passez à l’étape 2.
    
2. Déployez le complément à d’autres personnes au sein de l’entreprise. Là encore, évaluez les résultats et, en cas de réussite, poursuivez le déploiement complet.
    
3. Effectuez un déploiement complet pour tous les utilisateurs.
    
Selon la taille de l’audience cible, vous pouvez ajouter ou supprimer des étapes de déploiement.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Déployer un complément Office à l’aide du Centre d’administration

Avant de commencer, consultez [Déterminer si le déploiement centralisé des compléments fonctionne pour votre organisation](centralized-deployment-of-add-ins.md).
  
1. Dans le Centre d’administration, accédez à la page **Paramètres** \> Applications **intégrées** \> **Compléments** .

2. Sélectionnez **Déployer le add-in** en haut de la page, puis sélectionnez **Suivant**.

    > [!NOTE]
    > Vous pouvez également déployer des applications intégrées dans le[ Centre d’administration. ](test-and-deploy-microsoft-365-apps.md) Les applications intégrées sont visibles par les administrateurs Exchange général et les administrateurs. Si vous ne voyez pas les étapes ci-dessus, accédez à la section Déploiement centralisé en accédant à **Paramètres Applications** > **intégrées**. En haut de la page **Applications intégrées** , choisissez **Compléments**.

3. Sélectionnez une option et suivez les instructions.
  
4. Si vous avez sélectionné l’option pour ajouter un complément à partir de l’Office Store, effectuez votre sélection de complément. </br>

    Vous pouvez afficher les compléments disponibles par catégories : **Suggéré pour vous**, **Évaluation** ou **Nom**. Seuls les compléments gratuits sont disponibles à partir de l’Office Store. Les compléments payants ne sont pas pris en charge pour le moment. Après avoir sélectionné un complément, acceptez les conditions générales pour continuer. <br/> 

    > [!NOTE]
    > Avec l’option Office Store, les mises à jour et les améliorations sont automatiquement déployées sur les utilisateurs.

5. Sur la page suivante, sélectionnez **Tout le monde**, **Utilisateurs/groupes spécifiques** ou **Moi uniquement** pour spécifier les personnes vers lesquelles le complément est déployé. Utilisez la zone de recherche pour rechercher des utilisateurs ou des groupes spécifiques. <br/>

    > [!NOTE]
    > Pour en savoir plus sur les autres états qui s’appliquent à un complément, consultez [États du complément](./manage-addins-in-the-admin-center.md).
  
6. Sélectionnez **Déployer**.
  
7. Une graduation verte s’affiche lorsque le complément est déployé. Suivez les instructions sur la page pour tester le complément.

    > [!NOTE]
    > Les utilisateurs devront peut-être relancer Office pour afficher l’icône du complément dans le ruban de l’application. Outlook des applications peuvent prendre jusqu’à 24 heures pour apparaître sur les rubans de l’application.

8. Quand vous avez terminé, sélectionner **Suivant**. Si vous avez déployé sur vous-même, vous pouvez sélectionner **Modifier qui a accès au complément** pour le déployer sur d’autres utilisateurs.

    Si vous avez déployé le complément sur d’autres membres de votre organisation, suivez les instructions pour annoncer le déploiement du complément. <br/>
  
    Il est recommandé d’informer les utilisateurs et les groupes que le complément déployé est disponible. Envisagez d’envoyer un e-mail qui décrit quand et comment utiliser le complément. Incluez ou créez un lien vers du contenu d’aide ou des FAQ qui peuvent aider les utilisateurs s’ils rencontrent des problèmes avec le complément.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Points à considérer lors de l'affectation d'un complément à des utilisateurs et groupes

Les administrateurs généraux et les administrateurs Exchange peuvent attribuer un complément à tout le monde ou à des utilisateurs et groupes spécifiques. Chaque option a des conséquences spécifiques :
  
- **Chacun** Cette option affecte le complément à chaque utilisateur de l’organisation. Utilisez-la avec parcimonie et uniquement pour les compléments qui sont réellement universels pour l'ensemble de votre organisation.

- **Utilisateurs** Si vous attribuez un complément à un utilisateur individuel, puis déployez le complément sur un nouvel utilisateur, vous devez d’abord ajouter le nouvel utilisateur.

- **Groupes** Si vous attribuez un complément à un groupe, les utilisateurs qui sont ajoutés au groupe se voient automatiquement attribuer le complément. Lorsqu’un utilisateur est supprimé d’un groupe, il perd l’accès au complément. Dans les deux cas, aucune action supplémentaire n’est requise de la part de l’administrateur.

- **Juste moi** Si vous attribuez un complément à vous-même, le complément est affecté uniquement à votre compte, ce qui est idéal pour tester le complément.

L’option appropriée pour votre organisation dépend de votre configuration. Toutefois, nous vous recommandons d’effectuer des affectations à l’aide de groupes. En tant qu’administrateur, il peut être plus facile de gérer les compléments en utilisant des groupes et en contrôlant l’appartenance à ces groupes plutôt que d’affecter des utilisateurs individuels à chaque fois. Dans certains cas, vous pouvez restreindre l’accès à un petit ensemble d’utilisateurs en effectuant des affectations à des utilisateurs spécifiques en attribuant manuellement des utilisateurs.
  
## <a name="more-about-office-add-ins-security"></a>En savoir plus sur la sécurité des compléments Office

Les compléments Office combinent un fichier manifeste XML qui contient des métadonnées sur le complément, mais qui pointe surtout vers une application web qui contient tout le code et la logique. Les fonctionnalités des compléments peuvent varier. Par exemple, les compléments peuvent :
  
- afficher des données.

- lire le document d'un utilisateur pour fournir des services contextuels.

- lire et écrire des données vers le document d'un utilisateur et à partir de celui-ci pour fournir une valeur à cet utilisateur.

Pour plus d’informations sur les types et les fonctionnalités des compléments Office, voir [Vue d’ensemble de la plateforme des compléments Office](/office/dev/add-ins/overview/office-add-ins), en particulier la section « Anatomie d’un complément Office ».
  
To interact with the user's document, the add-in needs to declare what permission it needs in the manifest. A five-level JavaScript API access-permissions model provides the basis for privacy and security for users of task pane add-ins. The majority of the add-ins in the Office Store are level ReadWriteDocument with almost all add-ins supporting at least the ReadDocument level. For more information about the permission levels, see [Requesting permissions for API use in content and task pane add-ins](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins).
  
When updating a manifest, the typical changes are to an add-in's icon and text. Occasionally, add-in commands change. However, the permissions of the add-in do not change. The web application where all the code and logic for the add-in runs can change at any time, which is the nature of web applications.
  
Les mises à jour des compléments se produisent comme suit :
  
- **Line-of-business add-in:** In this case, where an admin explicitly uploaded a manifest, the add-in requires that the admin upload a new manifest file to support metadata changes. The next time the relevant Office applications start, the add-in will update. The web application can change at any time.

    > [!NOTE]
    > Administration n’a pas besoin de supprimer un complément métier pour effectuer une mise à jour.   Dans la section Compléments, Administration pouvez simplement cliquer sur le complément métier et choisir le **bouton Mettre à jour** dans le coin inférieur droit. La mise à jour fonctionne uniquement si la version du nouveau complément est supérieure à celle du complément existant.

- **Office Store add-in:** When an admin selected an add-in from the Office Store, if an add-in updates in the Office Store, the add-in will update later in Centralized Deployment. The next time the relevant Office applications start, the add-in will update. The web application can change at any time.
  
## <a name="related-content"></a>Contenu associé

[Gérer les compléments dans le Centre d’administration](manage-addins-in-the-admin-center.md) (article)\
[Créer votre premier complément du volet Office Word](/office/dev/add-ins/quickstarts/word-quickstart?tabs=yeomangenerator) (article\
[Mineurs et acquisition de compléments à partir du magasin](minors-and-acquiring-addins-from-the-store.md) (article)\
[Utiliser les applets de commande PowerShell de déploiement centralisé pour gérer les compléments](../../enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md) (article)\
[Résolution des problèmes : l’utilisateur ne voit pas les compléments](/office365/troubleshoot/access-management/user-not-seeing-add-ins) (article)
