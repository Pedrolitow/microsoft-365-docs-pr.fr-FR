---
title: Configurer des Advanced eDiscovery dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-scenario
search.appverid:
- MOE150
- MET150
description: Cet article explique comment configurer des Advanced eDiscovery vous permet de commencer à créer et gérer des cas. Il décrit également les abonnements et les licences Microsoft requis. Après quelques étapes rapides, l’outil Advanced eDiscovery est prêt à être utilisé.
ms.openlocfilehash: eb37c11f8773189a8090178bf65c909b09fa941f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60153005"
---
# <a name="set-up-microsoft-365-advanced-ediscovery"></a>Configurer Microsoft 365 Advanced eDiscovery

Advanced eDiscovery dans Microsoft 365 fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter des données qui répondent aux enquêtes internes et externes de votre organisation. Rien n’est nécessaire pour déployer des Advanced eDiscovery, mais un administrateur informatique et un responsable eDiscovery doivent effectuer certaines tâches préalables avant que votre organisation puisse commencer à créer et utiliser des cas Advanced eDiscovery pour gérer vos enquêtes.

Cet article décrit les étapes suivantes nécessaires à la Advanced eDiscovery.

![Étapes de la Advanced eDiscovery.](../media/set-up-advanced-ediscovery.png)

Cela inclut la garantie de la licence appropriée requise pour accéder aux Advanced eDiscovery et ajouter des dépositaires aux cas, et l’attribution d’autorisations à votre équipe juridique et d’enquête afin qu’elle puisse accéder aux cas et les gérer.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Étape 1 : Vérifier et attribuer les licences appropriées

La gestion des Advanced eDiscovery nécessite l’abonnement d’organisation approprié et la licence par utilisateur. Pour obtenir la liste des conditions de licence requises pour Advanced eDiscovery, voir [Abonnements et licences.](overview-ediscovery-20.md#subscriptions-and-licensing)

## <a name="step-2-assign-ediscovery-permissions"></a>Étape 2 : Attribuer des autorisations eDiscovery

Pour accéder Advanced eDiscovery ou ajouté en tant que membre d’un Advanced eDiscovery, un utilisateur doit se voir attribuer les autorisations appropriées. Plus précisément, un utilisateur doit être ajouté en tant que membre du groupe de rôles Gestionnaire eDiscovery dans le Centre de conformité Microsoft 365. Les membres de ce groupe de rôles peuvent créer et gérer Advanced eDiscovery cas. Ils peuvent ajouter et supprimer des membres, placer des dépositaires et des emplacements de contenu en conservation, gérer les notifications de conservation légale, créer et modifier des recherches associées à un cas, ajouter des résultats de recherche à un groupe de révision, analyser des données dans un groupe de révision et exporter et télécharger à partir d’un cas Advanced eDiscovery.

Pour ajouter des utilisateurs au groupe de rôles Gestionnaire eDiscovery, complétez les étapes suivantes :

1. Go to <https://compliance.microsoft.com/permissions> and sign in using the credentials for an admin account in your Microsoft 365 organization.

2. Dans la page **Autorisations,** sélectionnez le groupe de rôles **Gestionnaire eDiscovery.**

3. Dans la page volante du Gestionnaire  eDiscovery, cliquez sur Modifier à côté de la section Gestionnaire **eDiscovery.**

4. Dans la page Choisir le gestionnaire **eDiscovery** dans l’Assistant Modifier le groupe de rôles, cliquez sur Choisir le Gestionnaire **eDiscovery.**

5. Cliquez **sur** Ajouter, puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Cliquez **sur** Ajouter pour ajouter les utilisateurs sélectionnés, puis cliquez sur **Terminé.**

7. Cliquez **sur Enregistrer** pour ajouter les utilisateurs au groupe de rôles, puis cliquez sur **Fermer** pour terminer l’étape.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Plus d’informations sur le groupe de rôles Gestionnaire eDiscovery

Il existe deux sous-groupes dans le groupe de rôles Gestionnaire eDiscovery. Ces sous-groupes ont différents rôles.

- **Gestionnaire eDiscovery**: peut afficher et gérer les Advanced eDiscovery cas qu’ils créent ou dont ils sont membres. Si un autre gestionnaire eDiscovery crée un cas mais n’ajoute pas un deuxième gestionnaire eDiscovery en tant que membre de ce cas, le deuxième gestionnaire eDiscovery ne sera pas en mesure d’afficher ou d’ouvrir le cas sur la page Advanced eDiscovery dans le centre de conformité. En règle générale, la plupart des membres de votre organisation peuvent être ajoutés au sous-groupe gestionnaire eDiscovery.

- **Administrateur eDiscovery**: peut effectuer toutes les tâches de gestion de cas qu’un gestionnaire eDiscovery peut effectuer. De plus, un administrateur de découverte électronique peut :

  - Afficher tous les cas répertoriés sur la page Advanced eDiscovery.
  
  - Gérer tous les cas au sein l’organisation après s’être ajouté en tant que membre du cas.

  - Accéder et exporter des données de cas pour tout cas au sein de l’organisation.

  En raison de l’étendue de l’accès, une organisation ne doit avoir que quelques administrateurs membres du sous-groupe administrateurs eDiscovery.

Pour plus d’informations sur les autorisations eDiscovery et une description de chaque rôle attribué au groupe de rôles Gestionnaire eDiscovery, voir Attribuer des [autorisations eDiscovery.](assign-ediscovery-permissions.md)

## <a name="step-3-configure-global-settings-for-advanced-ediscovery"></a>Étape 3 : Configurer les paramètres globaux pour Advanced eDiscovery

La dernière étape à effectuer avant que les membres de votre organisation commencent à créer et à utiliser des cas consiste à configurer des paramètres globaux qui s’appliquent à tous les cas de votre organisation. Pour l’instant, le seul paramètre global est la détection des privilèges *client-avocat* (d’autres paramètres globaux seront disponibles à l’avenir). Ce paramètre permet au modèle de privilège client-avocat de s’exécuter lorsque vous analysez des données dans un jeu à réviser. Le modèle utilise l’apprentissage automatique pour déterminer la probabilité qu’un document contienne du contenu de nature juridique. Il compare également les participants des documents à une liste d’avocats (que vous soumettez lors de la configuration du modèle) pour déterminer si un document a au moins un participant qui est avocat.

Pour plus d’informations sur la configuration et l’utilisation du modèle de détection des privilèges [client-avocat,](attorney-privilege-detection.md)voir Configurer la détection des privilèges client-avocat dans Advanced eDiscovery .

> [!NOTE]
> Il s’agit d’une étape facultative que vous pouvez effectuer à tout moment. Le fait de ne pas implémenter le modèle de détection des privilèges client-avocat ne vous empêche pas de créer et d’utiliser Advanced eDiscovery cas.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez Advanced eDiscovery, vous êtes prêt à [créer un cas.](create-and-manage-advanced-ediscoveryv2-case.md)