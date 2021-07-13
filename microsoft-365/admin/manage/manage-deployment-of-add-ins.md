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
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Découvrez comment déployer des add-ins pour des utilisateurs et des groupes de votre organisation à l’aide du déploiement centralisé dans le Centre d’administration.
ms.openlocfilehash: 88613e593f3c8375073865ebe9b7e417c6b3f06f
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53392850"
---
# <a name="deploy-add-ins-in-the-admin-center"></a>Déployer des compléments dans le centre d’administration

[] Les compléments Office vous aident à personnaliser vos documents et à accéder plus simplement aux informations sur le web (voir [Commencer à utiliser votre complément Office](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). En tant qu’administrateur, vous pouvez déployer des Office pour les utilisateurs de votre organisation à l’aide de la fonctionnalité Déploiement centralisé dans le Centre d’administration Microsoft 365. Le déploiement centralisé est le moyen recommandé et le plus riche en fonctionnalités pour la plupart des administrateurs de déployer des modules pour les utilisateurs et les groupes au sein d’une organisation.

Pour plus d’informations sur la façon de déterminer si votre organisation peut prendre en charge le déploiement centralisé, voir [Determine if Centralized Deployment of add-ins works for your organization](centralized-deployment-of-add-ins.md).

Pour en savoir plus sur la gestion des add-ins après le déploiement, voir Gérer les [add-ins dans le Centre d’administration](manage-addins-in-the-admin-center.md)
  
> [!NOTE]
>  Pour Word, Excel et PowerPoint utilisent un catalogue d’applications [SharePoint](/office/dev/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) pour déployer des applications pour les utilisateurs dans un environnement local sans connexion à Microsoft 365 et/ou prise en charge des SharePoint. Par Outlook utiliser Exchange panneau de Microsoft 365.
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Approche recommandée pour le déploiement de compléments Office

Pour déployer des add-ins à l’aide d’une approche par phases, nous vous recommandons les étapes suivantes :
  
1. Déployez le complément vers un petit groupe de parties intéressées et de membres du service informatique. Si le déploiement réussit, passer à l’étape 2.
    
2. Déployer le add-in à d’autres personnes au sein de l’entreprise. Là encore, évaluez les résultats et, en cas de réussite, poursuivez le déploiement complet.
    
3. Effectuer un déploiement complet pour tous les utilisateurs.
    
Selon la taille de l’audience cible, vous pouvez ajouter ou supprimer des étapes de déploiement.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Déploiement d’un complément Office à l’aide du centre d’administration

Avant de commencer, voir Déterminer si le déploiement centralisé de vos modules de déploiement [fonctionne pour votre organisation.](centralized-deployment-of-add-ins.md)
  
1. Dans le Centre d’administration, Paramètres la page  \> **Des modules.** Si vous ne voyez pas la page de l’application, **rendez-vous** sur la page **Paramètres** applications \>  \> **intégrées.**

2. Sélectionnez **Déployer le add-in** en haut de la page, puis sélectionnez **Suivant**.

    > [!NOTE]
    > Le Centre d’administration est mis à jour vers l’expérience de déploiement avec les applications intégrées. Les applications intégrées sont visibles uniquement par les administrateurs globaux, tandis que pour d’autres, l’ancienne expérience existe toujours. Si vous ne voyez pas les étapes ci-dessus, consultez la section Déploiement centralisé en Paramètres  >  **applications intégrées.** En haut de la page **Applications intégrées,** choisissez **Les applications.**

3. Sélectionnez une option et suivez les instructions.
  
4. Si vous avez sélectionné l’option d’ajout d’un Office Store, faites votre sélection. </br>

    Vous pouvez afficher les add-ins disponibles par catégories : Suggéré pour **vous,** **Évaluation** ou **Nom**. Seuls les add-ins gratuits sont disponibles dans Office Store. Les compléments payants ne sont pas pris en charge pour le moment. Une fois que vous avez sélectionné un module, acceptez les conditions générales pour continuer. <br/> 

    > [!NOTE]
    > Avec l’option Office Store, les mises à jour et les améliorations sont automatiquement déployées pour les utilisateurs.

5. Sur la page suivante, sélectionnez **Tout le monde**, **Utilisateurs/groupes spécifiques** ou **Moi uniquement** pour spécifier les personnes vers lesquelles le complément est déployé. Utilisez la zone de recherche pour rechercher des utilisateurs ou des groupes spécifiques. <br/>

    > [!NOTE]
    > Pour en savoir plus sur les autres états qui s’appliquent à un add-in, voir [États de l’application.](./manage-addins-in-the-admin-center.md)
  
6. Sélectionnez **Déployer**.
  
7. Une coche verte s’affiche lorsque le module est déployé. Suivez les instructions de la page pour tester le add-in.

    > [!NOTE]
    > Les utilisateurs devront peut-être redémarrer Office pour afficher l’icône de la application sur le ruban de l’application. Outlook des applications peuvent prendre jusqu’à 24 heures pour apparaître sur les rubans de l’application.

8. Lorsque vous avez terminé, sélectionnez **Suivant**. Si vous avez déployé votre déploiement uniquement sur vous-même, vous pouvez sélectionner Modifier qui a accès au **add-in** pour le déployer pour d’autres utilisateurs.

    Si vous avez déployé le add-in vers d’autres membres de votre organisation, suivez les instructions pour annoncer le déploiement du module. <br/>
  
    Il est bon d’informer les utilisateurs et les groupes que le add-in déployé est disponible. Envisagez d’envoyer un e-mail qui décrit quand et comment utiliser le add-in. Inclure ou lier du contenu d’aide ou des FAQ qui peuvent aider les utilisateurs s’ils ont des problèmes avec le add-in.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Points à considérer lors de l'affectation d'un complément à des utilisateurs et groupes

Les administrateurs globaux et Exchange administrateurs peuvent affecter un module à tout le monde ou à des utilisateurs et groupes spécifiques. Chaque option a des conséquences spécifiques :
  
- **Tout le monde** Cette option affecte le add-in à tous les utilisateurs de l’organisation. Utilisez-la avec parcimonie et uniquement pour les compléments qui sont réellement universels pour l'ensemble de votre organisation.

- **Utilisateurs** Si vous affectez un add-in à un utilisateur individuel, puis déployez le module sur un nouvel utilisateur, vous devez d’abord ajouter le nouvel utilisateur.

- **Groupes** Si vous affectez un add-in à un groupe, le module est automatiquement attribué aux utilisateurs ajoutés au groupe. Lorsqu’un utilisateur est supprimé d’un groupe, il perd l’accès au module. Dans les deux cas, aucune action supplémentaire n’est requise de la part de l’administrateur.

- **Moi uniquement** Si vous affectez un add-in à vous-même, il est affecté uniquement à votre compte, ce qui est idéal pour tester le module.

L’option la plus efficace pour votre organisation dépend de votre configuration. Toutefois, nous vous recommandons d’effectuer des affectations à l’aide de groupes. En tant qu’administrateur, il peut être plus facile de gérer les modules en utilisant des groupes et en contrôlant l’appartenance à ces groupes plutôt que d’affecter des utilisateurs individuels à chaque fois. Dans certains cas, vous pouvez restreindre l’accès à un petit groupe d’utilisateurs en attribuant des affectations à des utilisateurs spécifiques en attribuant manuellement des utilisateurs.
  
## <a name="more-about-office-add-ins-security"></a>En savoir plus Office sécurité des add-ins

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
    > L’administrateur n’a pas besoin de supprimer un add-in LOB pour faire une mise à jour.   Dans la section Des add-ins, l’administrateur peut simplement  cliquer sur le add-in LOB et choisir le bouton Mettre à jour dans le coin inférieur droit. La mise à jour ne fonctionne que si la version du nouveau module est supérieure à celle du nouveau.

- **Complément de l'Office Store :** lorsqu'un administrateur a sélectionné un complément à partir de l'Office Store, si un complément est mis à jour dans l'Office Store, le complément sera mis à jour plus tard dans le déploiement centralisé. Le complément est mis à jour au démarrage suivant des applications Office concernées. L'application web peut changer à tout moment.
  
## <a name="related-content"></a>Contenu associé

[Gérer les add-ins dans le Centre d’administration](manage-addins-in-the-admin-center.md) (article)\
[Créer votre premier add-in de](/office/dev/add-ins/quickstarts/word-quickstart?tabs=yeomangenerator) volet de tâches Word (article\
[Mineurs et acquisition](minors-and-acquiring-addins-from-the-store.md) de modules dans le Store (article)\ Utilisez les [cmdlets PowerShell](../../enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md) de déploiement centralisé pour gérer les modules (article)\  
[Résolution des problèmes : l’utilisateur ne voit pas les modules (article)](/office365/troubleshoot/access-management/user-not-seeing-add-ins)