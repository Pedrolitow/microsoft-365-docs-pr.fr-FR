---
title: Configurer eDiscovery (Premium) dans Microsoft Purview
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
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
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Cet article explique comment configurer eDiscovery (Premium) pour que vous puissiez commencer à créer et gérer des cas. Il décrit également les abonnements et licences Microsoft requis. Une fois que vous avez effectué quelques étapes rapides, l’outil eDiscovery (Premium) est prêt à être utilisé.
ms.openlocfilehash: 70b3d4cd5587b4996bd2999be8fdcae62feb1b85
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67821074"
---
# <a name="set-up-microsoft-purview-ediscovery-premium"></a>Configurer Microsoft Purview eDiscovery (Premium)

Microsoft Purview eDiscovery (Premium) fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter des données qui répondent aux investigations internes et externes de votre organisation. Rien n’est nécessaire pour déployer eDiscovery (Premium), mais il existe certaines tâches prérequises qu’un administrateur informatique et un responsable eDiscovery doivent effectuer avant que votre organisation puisse commencer à créer et utiliser des cas eDiscovery (Premium) pour gérer vos investigations.

Cet article décrit les étapes suivantes nécessaires à la configuration d’eDiscovery (Premium).

![Étapes de configuration d’eDiscovery (Premium).](../media/set-up-advanced-ediscovery.png)

Cela inclut la garantie des licences appropriées requises pour accéder à eDiscovery (Premium) et ajouter des consignats aux cas, et l’attribution d’autorisations à votre équipe juridique et d’enquête afin qu’elle puisse accéder aux cas et les gérer.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Étape 1 : Vérifier et attribuer les licences appropriées

La gestion des licences pour eDiscovery (Premium) nécessite l’abonnement à l’organisation et les licences par utilisateur appropriés. Pour obtenir la liste des exigences de licence pour eDiscovery (Premium), consultez [Abonnements et licences](overview-ediscovery-20.md#subscriptions-and-licensing).

## <a name="step-2-assign-ediscovery-permissions"></a>Étape 2 : Attribuer des autorisations eDiscovery

Pour accéder à eDiscovery (Premium) ou être ajouté en tant que membre d’un cas eDiscovery (Premium), un utilisateur doit disposer des autorisations appropriées. Plus précisément, un utilisateur doit être ajouté en tant que membre du groupe de rôles eDiscovery Manager dans le portail de conformité Microsoft Purview. Les membres de ce groupe de rôles peuvent créer et gérer des cas eDiscovery (Premium). Ils peuvent ajouter et supprimer des membres, placer les consignats et les emplacements de contenu en attente, gérer les notifications de conservation légale, créer et modifier des recherches associées dans un cas, ajouter des résultats de recherche à un jeu de révision, analyser des données dans un jeu de révision, et exporter et télécharger à partir d’un cas eDiscovery (Premium).

Effectuez les étapes suivantes pour ajouter des utilisateurs au groupe de rôles gestionnaire eDiscovery :

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">portail de conformité</a>et connectez-vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans la page Autorisations, sélectionnez le groupe de **rôles** **gestionnaire eDiscovery** .

3. Dans la page de menu volant eDiscovery Manager, cliquez sur **Modifier** en regard de la section **gestionnaire eDiscovery** .

4. Dans la page **Choisir le gestionnaire eDiscovery** dans l’Assistant Modifier un groupe de rôles, cliquez sur **Choisir le gestionnaire eDiscovery**.

5. Cliquez sur **Ajouter** , puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Cliquez sur **Ajouter** pour ajouter les utilisateurs sélectionnés, puis cliquez sur **Terminé**.

7. Cliquez sur **Enregistrer** pour ajouter les utilisateurs au groupe de rôles, puis sur **Fermer** pour terminer l’étape.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Plus d’informations sur le groupe de rôles eDiscovery Manager

Il existe deux sous-groupes dans le groupe de rôles gestionnaire eDiscovery. Ces sous-groupes ont différents rôles.

- **Gestionnaire eDiscovery** : peut afficher et gérer les cas eDiscovery (Premium) qu’ils créent ou dont ils sont membres. Si un autre gestionnaire eDiscovery crée un cas mais n’ajoute pas de deuxième gestionnaire eDiscovery en tant que membre de ce cas, le deuxième gestionnaire eDiscovery ne peut pas afficher ou ouvrir le cas sur la page eDiscovery (Premium) dans le Centre de conformité. En général, la plupart des membres de votre organisation peuvent être ajoutés au sous-groupe eDiscovery Manager.

- **Administrateur eDiscovery** : peut effectuer toutes les tâches de gestion de cas qu’un gestionnaire eDiscovery peut effectuer. De plus, un administrateur de découverte électronique peut :

  - Afficher tous les cas répertoriés sur la page de la découverte électronique.
  
  - Gérer tous les cas au sein l’organisation après s’être ajouté en tant que membre du cas.

  - Accéder et exporter des données de cas pour tout cas au sein de l’organisation.

  En raison de l’étendue de l’accès, une organisation ne doit avoir que quelques administrateurs membres du sous-groupe administrateurs eDiscovery.

Pour plus d’informations sur les autorisations eDiscovery et une description de chaque rôle affecté au groupe de rôles eDiscovery Manager, consultez [Affecter des autorisations eDiscovery](assign-ediscovery-permissions.md).

## <a name="step-3-configure-global-settings-for-ediscovery-premium"></a>Étape 3 : Configurer les paramètres globaux pour eDiscovery (Premium)

La dernière étape à effectuer avant que les membres de votre organisation commencent à créer et à utiliser des cas consiste à configurer des paramètres globaux qui s’appliquent à tous les cas de votre organisation. À l'heure actuelle, le seul paramètre global est la *détection du privilège avocat-client* (des paramètres plus globaux seront disponibles à l'avenir). Ce paramètre permet au modèle de privilège avocat-client de s’exécuter lorsque vous analysez des données dans un ensemble de révisions. Le modèle utilise le Machine Learning pour déterminer la probabilité qu’un document contienne du contenu de nature juridique. Il compare également les participants aux documents avec une liste d’avocats (que vous soumettez lors de la configuration du modèle) pour déterminer si un document a au moins un participant qui est un avocat.

Pour plus d’informations sur la configuration et l’utilisation du modèle de détection des privilèges [avocat-client, consultez Configurer la détection des privilèges avocat-client dans eDiscovery (Premium).](attorney-privilege-detection.md)

> [!NOTE]
> Il s’agit d’une étape facultative que vous pouvez effectuer à tout moment. Le fait de ne pas implémenter le modèle de détection des privilèges avocat-client ne vous empêche pas de créer et d’utiliser des cas eDiscovery (Premium).

## <a name="next-steps"></a>Prochaines étapes

Après avoir configuré eDiscovery (Premium), vous êtes prêt à [créer un cas](create-and-manage-advanced-ediscoveryv2-case.md).