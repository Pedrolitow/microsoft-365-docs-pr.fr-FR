---
title: Déployer des compléments dans le centre d’administration
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
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Apprenez à déployer des modules d’accès aux utilisateurs et aux groupes de votre organisation en utilisant le déploiement centralisé dans le centre d’administration.
ms.openlocfilehash: 2d3b90a75f38a2c1146c0b0e5470c80b0af2c63f
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572272"
---
# <a name="deploy-add-ins-in-the-admin-center"></a>Déployer des compléments dans le centre d’administration

[] Les compléments Office vous aident à personnaliser vos documents et à accéder plus simplement aux informations sur le web (voir [Commencer à utiliser votre complément Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). En tant qu’administrateur, vous pouvez déployer Office add-ins pour les utilisateurs de votre organisation en utilisant la fonction de déploiement centralisé dans le Microsoft 365 d’administration. Le déploiement centralisé est le moyen recommandé et le plus riche en fonctionnalités pour la plupart des administrateurs de déployer des modules d’accès aux utilisateurs et aux groupes au sein d’une organisation.

Pour plus d’informations sur la façon de déterminer si votre organisation peut prendre en charge le déploiement centralisé, [voir Déterminer si le déploiement centralisé d’add-ins fonctionne pour votre organisation](centralized-deployment-of-add-ins.md).

Pour en savoir plus sur la gestion des modules d’ajout après le déploiement, [consultez gérer les modules clés dans le centre d’administration](manage-addins-in-the-admin-center.md)
  
> [!NOTE]
>  Pour Word, Excel et PowerPoint utilisent [un catalogue d’applications SharePoint](https://dev.office.com/docs/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) pour déployer des modules d’ajout aux utilisateurs dans un environnement sur place sans connexion à Microsoft 365 et/ou prise en charge des modules de SharePoint requis. Pour Outlook utiliser Exchange panneau de contrôle pour déployer dans un environnement sur place sans connexion à Microsoft 365.
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Approche recommandée pour le déploiement de compléments Office

Pour déployer les modules d’ajout en utilisant une approche progressive, nous recommandons ce qui suit :
  
1. Déployez le complément vers un petit groupe de parties intéressées et de membres du service informatique. Si le déploiement est réussi, passez à l’étape 2.
    
2. Déployer l’add-in à plus de personnes au sein de l’entreprise. Encore une fois, évaluez les résultats et, en cas de succès, continuez avec le déploiement complet.
    
3. Effectuez un déploiement complet pour tous les utilisateurs.
    
Selon la taille de l’audience cible, vous pouvez ajouter ou supprimer des étapes de déploiement.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Déploiement d’un complément Office à l’aide du centre d’administration

Avant de commencer, voir [Déterminer si le déploiement centralisé d’add-ins fonctionne pour votre organisation](centralized-deployment-of-add-ins.md).
  
1. Dans le centre d’administration, **rendez-vous sur Paramètres** page \> **Add-ins.** Si vous ne voyez pas la page **Add-in, rendez-vous** sur la page  \> **Paramètres’applications** \> **intégrées Add-ins.**

2. Sélectionnez **Déployer Add-in** en haut de la page, puis sélectionnez **Suivant**.

    > [!NOTE]
    > Le centre d’administration est mis à jour pour l’expérience de déploiement avec les applications intégrées. Les applications intégrées ne sont visibles que par les administrateurs global, tandis que pour d’autres, l’ancienne expérience existe toujours. Si vous ne voyez pas les étapes ci-dessus, allez à la section Déploiement centralisé en allant **à Paramètres**  >  **applications intégrées**. En haut de la page **Applications intégrées,** choisissez **Add-ins**.

3. Sélectionnez une option et suivez les instructions.
  
4. Si vous avez choisi l’option d’ajouter un add-in du Office Store, faites votre sélection add-in. </br>

    Vous pouvez afficher les add-ins disponibles par catégories : **Suggéré pour vous,** **Notation,** ou **Nom**. Seuls les add-ins gratuits sont disponibles sur le Office Store. Les compléments payants ne sont pas pris en charge pour le moment. Après avoir sélectionné un module d’ajout, acceptez les modalités de procéder. <br/> 

    > [!NOTE]
    > Avec l’option Office Store, les mises à jour et les améliorations sont automatiquement déployées aux utilisateurs.

5. Sur la page suivante, sélectionnez **Tout le monde**, **Utilisateurs/groupes spécifiques** ou **Moi uniquement** pour spécifier les personnes vers lesquelles le complément est déployé. Utilisez la boîte de recherche pour trouver des utilisateurs ou des groupes spécifiques. <br/>

    > [!NOTE]
    > Pour en savoir plus sur les autres états qui s’appliquent à un module de modules ajoutés, [consultez les états add-in](./manage-addins-in-the-admin-center.md).
  
6. Sélectionnez **Déployer**.
  
7. Une tique verte apparaît lorsque l’add-in est déployé. Suivez les instructions de la page pour tester l’add-in.

    > [!NOTE]
    > Les utilisateurs peuvent avoir besoin de relancer Office pour afficher l’icône add-in sur le ruban de l’application. Outlook add-ins peuvent prendre jusqu’à 24 heures pour apparaître sur les rubans d’application.

8. Une fois terminé, sélectionnez **Suivant**. Si vous vous êtes déployé sur vous-même, vous pouvez sélectionner **Change qui a accès à l’add-in pour** le déployer à un plus grand nombre d’utilisateurs.

    Si vous avez déployé l’add-in à d’autres membres de votre organisation, suivez les instructions pour annoncer le déploiement de l’add-in. <br/>
  
    Il est de bonnes pratiques d’informer les utilisateurs et les groupes que l’add-in déployé est disponible. Envisagez d’envoyer un e-mail qui décrit quand et comment utiliser l’add-in. Incluez ou reliez-vous au contenu d’aide ou aux FAQ qui pourraient aider les utilisateurs s’ils ont des problèmes avec l’add-in.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Points à considérer lors de l'affectation d'un complément à des utilisateurs et groupes

Les administrateurs et les Exchange administrateurs peuvent attribuer un module de soutien à tout le monde ou à des utilisateurs et groupes spécifiques. Chaque option a des conséquences spécifiques :
  
- **Tout le monde** Cette option attribue l’add-in à chaque utilisateur de l’organisation. Utilisez-la avec parcimonie et uniquement pour les compléments qui sont réellement universels pour l'ensemble de votre organisation.

- **Les utilisateurs** Si vous assignez un module de module à un utilisateur individuel, puis que vous déployez l’add-in à un nouvel utilisateur, vous devez d’abord ajouter le nouvel utilisateur.

- **Les groupes** Si vous attribuez un module de module à un groupe, les utilisateurs qui sont ajoutés au groupe se voient automatiquement attribuer l’add-in. Lorsqu’un utilisateur est supprimé d’un groupe, l’utilisateur perd l’accès à l’add-in. Dans les deux cas, aucune action supplémentaire n’est requise de la part de l’administrateur.

- **Juste moi** Si vous attribuez un module de complément à vous-même, l’add-in n’est attribué qu’à votre compte, ce qui est idéal pour tester l’add-in.

La bonne option pour votre organisation dépend de votre configuration. Toutefois, nous vous recommandons de faire des tâches en utilisant des groupes. En tant qu’administrateur, il peut être plus facile de gérer les modules d’ajout en utilisant des groupes et en contrôlant l’adhésion de ces groupes plutôt que d’affecter des utilisateurs individuels à chaque fois. Dans certaines situations, vous pouvez restreindre l’accès à un petit ensemble d’utilisateurs en effectuant des affectations à des utilisateurs spécifiques en affectant les utilisateurs manuellement.
  
## <a name="more-about-office-add-ins-security"></a>En savoir plus Office la sécurité des add-ins

Les compléments Office combinent un fichier manifeste XML qui inclut certaines métadonnées sur le complément, mais surtout qui pointe vers une application web contenant tout le code et la logique. Les fonctionnalités des compléments peuvent varier. Par exemple, les compléments peuvent :
  
- afficher des données.

- lire le document d'un utilisateur pour fournir des services contextuels.

- lire et écrire des données vers le document d'un utilisateur et à partir de celui-ci pour fournir une valeur à cet utilisateur.

Pour plus d'informations sur les types et fonctionnalités des compléments Office, voir [Vue d'ensemble de la plateforme des compléments Office](/office/dev/add-ins/overview/office-add-ins), notamment la section « Anatomie d'un complément Office ».
  
Pour interagir avec le document de l'utilisateur, le complément doit déclarer les autorisations dont il a besoin dans le fichier manifeste. Un modèle d'autorisations d'accès d'une API JavaScript à cinq niveaux fournit la base de la confidentialité et de la sécurité pour les utilisateurs des compléments du volet Office. La plupart des compléments de l'Office Store sont au niveau ReadWriteDocument. Presque tous les compléments prennent en charge le niveau ReadDocument au minimum. Pour plus d'informations sur les niveaux d'autorisation, voir [Demande d'autorisations pour l'utilisation d'API dans les compléments de contenu et du volet Office](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins).
  
Lors de la mise à jour d'un manifeste, les modifications standard sont apportées à l'icône et au texte d'un complément. Les commandes de complément changent parfois, contrairement aux autorisations du complément. L'application web dans laquelle le code et la logique du complément sont exécutés peut changer à tout moment, ce qui est la nature même des applications web.
  
Les mises à jour des compléments se produisent comme suit :
  
- **Complément métier :** dans ce cas, lorsqu'un administrateur a chargé explicitement un manifeste, le complément nécessite que l'administrateur charge un nouveau fichier manifeste pour prendre en charge la modification des métadonnées. Le complément est mis à jour au démarrage suivant des applications Office concernées. L'application web peut changer à tout moment.

    > [!NOTE]
    > Admin n’a pas besoin de supprimer un lob add-in pour faire une mise à jour.   Dans la section Add-ins, Admin peut simplement cliquer sur l’add-in LOB et choisir le bouton **mise à jour** dans le coin inférieur droit. Mise à jour ne fonctionnera que si la version du nouvel add-in est supérieure à celle de l’add-in existant.

- **Complément de l'Office Store :** lorsqu'un administrateur a sélectionné un complément à partir de l'Office Store, si un complément est mis à jour dans l'Office Store, le complément sera mis à jour plus tard dans le déploiement centralisé. Le complément est mis à jour au démarrage suivant des applications Office concernées. L'application web peut changer à tout moment.
  
## <a name="related-content"></a>Contenu connexe

[Gérer les add-ins dans le centre d’administration](manage-addins-in-the-admin-center.md) (article)

[Créez votre premier module de tâches Word (article)](/office/dev/add-ins/quickstarts/word-quickstart?tabs=yeomangenerator)

[Mineurs et acquisition d’add-ins dans le magasin](minors-and-acquiring-addins-from-the-store.md) (article)
  
[Utilisez des cmdlets PowerShell de déploiement centralisés pour gérer les modules ajoutés](../../enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md) (article)
  
[Dépannage : Utilisateur ne voyant pas d’add-ins](/office365/troubleshoot/access-management/user-not-seeing-add-ins) (article)