---
title: Configurer Advanced eDiscovery dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-ediscovery
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Cet article explique comment configurer Advanced eDiscovery pour commencer à créer et gérer des cas. Il décrit également les abonnements et les licences Microsoft requis. Après quelques étapes rapides, l’outil Advanced eDiscovery est prêt à être utilisé.
ms.openlocfilehash: 29a220f36a55a04d1c1a24add03b2e013a5c60ba
ms.sourcegitcommit: 3d48e198e706f22ac903b346cadda06b2368dd1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2021
ms.locfileid: "50727409"
---
# <a name="set-up-microsoft-365-advanced-ediscovery"></a>Configurer Microsoft 365 Advanced eDiscovery

Advanced eDiscovery dans Microsoft 365 fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter des données qui répondent aux enquêtes internes et externes de votre organisation. [](overview-ediscovery-20.md#advanced-ediscovery-workflow) Rien n’est nécessaire pour déployer Advanced eDiscovery, mais un administrateur informatique et un responsable eDiscovery doivent effectuer certaines tâches préalables avant que votre organisation puisse commencer à créer et utiliser des cas Advanced eDiscovery pour gérer vos enquêtes.

Cet article décrit les étapes nécessaires pour configurer Advanced eDiscovery. Cela inclut la garantie de la licence appropriée requise pour accéder à Advanced eDiscovery et ajouter des dépositaires aux cas, et l’attribution d’autorisations à votre équipe juridique et d’examen afin qu’elle puisse accéder aux cas et les gérer.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Étape 1 : Vérifier et attribuer les licences appropriées

La gestion des licences pour Advanced eDiscovery nécessite l’abonnement d’organisation et la licence par utilisateur appropriés.

- **Abonnement à l’organisation :** Pour accéder à Advanced eDiscovery dans le Centre de conformité Microsoft 365 ou le Centre de sécurité & conformité, votre organisation doit avoir l’une des fonctionnalités suivantes :

  - Abonnement Microsoft 365 E5 ou Office 365 E5
  
  - Abonnement Microsoft 365 E3 avec le module complémentaire E5 conformité

  - Abonnement Microsoft 365 E3 avec E5 eDiscovery et module d’audit

  Si vous n’avez pas de plan Microsoft 365 E5 et que vous souhaitez essayer Advanced eDiscovery, vous pouvez ajouter [Microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou vous inscrire à une version d’essai de Microsoft 365 E5. [](https://www.microsoft.com/microsoft-365/enterprise)

- **Licences par utilisateur :** Pour ajouter un utilisateur en tant que dépositaire dans un cas de découverte électronique anticipée, l’une des licences suivantes doit lui être attribuée, en fonction de l’abonnement de votre organisation :

  - Microsoft 365 : une licence Microsoft 365 E5, une licence de module de conformité E5 ou une licence de modules de découverte électronique et d’audit E5 doivent être attribuées aux utilisateurs.

  - Office 365 : une licence Office 365 E5 doit être attribuée aux utilisateurs.

   Pour plus d’informations sur l’attribution de licences, voir [Attribuer des licences aux utilisateurs.](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)

> [!NOTE]
> Les utilisateurs ont uniquement besoin d’une licence E5 (ou de la licence de module supplémentaire appropriée) pour être ajoutés en tant que dépositaires à un cas Advanced eDiscovery. Les administrateurs informatiques, les gestionnaires eDiscovery, les avocats, les techniciens juridiques ou les enquêteurs qui utilisent Advanced eDiscovery pour gérer les cas et examiner les données de cas n’ont pas besoin d’une licence E5 ou de modules add-on.

## <a name="step-2-assign-ediscovery-permissions"></a>Étape 2 : Attribuer des autorisations eDiscovery

Pour accéder à Advanced eDiscovery ou être ajouté en tant que membre d’un cas Advanced eDiscovery, un utilisateur doit avoir les autorisations appropriées. Plus précisément, un utilisateur doit être ajouté en tant que membre du groupe de rôles Gestionnaire eDiscovery dans le Centre de sécurité & conformité. Les membres de ce groupe de rôles peuvent créer et gérer des cas Advanced eDiscovery. Ils peuvent ajouter et supprimer des membres, placer des dépositaires et des emplacements de contenu en conservation, gérer les notifications de conservation légale, créer et modifier des recherches associées à un cas, ajouter des résultats de recherche à un groupe de révision, analyser des données dans un jeu à réviser et exporter et télécharger à partir d’un cas Advanced eDiscovery.

Pour ajouter des utilisateurs au groupe de rôles Gestionnaire eDiscovery, complétez les étapes suivantes :

1. Go to [https://protection.office.com/permissions](https://protection.office.com/permissions) and sign in using the credentials for an admin account in your Microsoft 365 organization.

2. Dans la page **Autorisations,** sélectionnez le groupe de rôles **Gestionnaire eDiscovery.**

3. Dans la page volante du Gestionnaire  eDiscovery, cliquez sur Modifier à côté de la section Gestionnaire **eDiscovery.**

4. Dans la page Choisir le gestionnaire **eDiscovery** dans l’Assistant Modifier le groupe de rôles, cliquez sur Choisir le Gestionnaire **eDiscovery.**

5. Cliquez **sur** Ajouter, puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Cliquez **sur** Ajouter pour ajouter les utilisateurs sélectionnés, puis cliquez sur **Terminé.**

7. Cliquez **sur Enregistrer** pour ajouter les utilisateurs au groupe de rôles, puis cliquez sur **Fermer** pour terminer l’étape.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Plus d’informations sur le groupe de rôles Gestionnaire eDiscovery

Il existe deux sous-groupes dans le groupe de rôles Gestionnaire eDiscovery. Ces sous-groupes ont différents rôles.

- **Gestionnaire eDiscovery :** Peut afficher et gérer les cas Advanced eDiscovery qu’ils créent ou dont ils sont membres. Si un autre gestionnaire eDiscovery crée un cas mais n’ajoute pas un deuxième gestionnaire eDiscovery en tant que membre de ce cas, le deuxième gestionnaire eDiscovery ne sera pas en mesure d’afficher ou d’ouvrir le cas sur la page Advanced eDiscovery dans le centre de conformité. En règle générale, la plupart des membres de votre organisation peuvent être ajoutés au sous-groupe gestionnaire eDiscovery.

- **Administrateur eDiscovery :** Peut effectuer toutes les tâches de gestion des cas qu’un gestionnaire eDiscovery peut effectuer. De plus, un administrateur de découverte électronique peut :

  - Afficher tous les cas répertoriés sur la page Advanced eDiscovery.
  
  - Gérer tous les cas au sein l’organisation après s’être ajouté en tant que membre du cas.

  - Accéder et exporter des données de cas pour tout cas au sein de l’organisation.

  En raison de l’étendue de l’accès, une organisation ne doit avoir que quelques administrateurs membres du sous-groupe administrateurs eDiscovery.

Pour plus d’informations sur les autorisations eDiscovery et une description de chaque rôle affecté au groupe de rôles Gestionnaire eDiscovery, voir Attribuer des [autorisations eDiscovery.](assign-ediscovery-permissions.md)

## <a name="step-3-configure-global-settings-for-advanced-ediscovery"></a>Étape 3 : Configurer les paramètres globaux pour Advanced eDiscovery

La dernière étape à effectuer avant que les membres de votre organisation commencent à créer et à utiliser des cas consiste à configurer des paramètres globaux qui s’appliquent à tous les cas de votre organisation. Pour l’instant, le seul paramètre global est la détection des privilèges *client-avocat* (d’autres paramètres globaux seront disponibles à l’avenir). Ce paramètre permet au modèle de privilège client-avocat de s’exécuter lorsque vous analysez des données dans un jeu à réviser. Le modèle utilise l’apprentissage automatique pour déterminer la probabilité qu’un document contienne du contenu de nature juridique. Il compare également les participants des documents à une liste d’avocats (que vous soumettez lors de la configuration du modèle) pour déterminer si un document a au moins un participant qui est avocat.

Pour plus d’informations sur la configuration et l’utilisation du modèle de détection des privilèges client-avocat, voir Configurer la détection des privilèges [client-avocat dans Advanced eDiscovery](attorney-privilege-detection.md).

> [!NOTE]
> Il s’agit d’une étape facultative que vous pouvez effectuer à tout moment. Le fait de ne pas implémenter le modèle de détection des privilèges client-avocat ne vous empêche pas de créer et d’utiliser des cas Advanced eDiscovery.

## <a name="next-steps"></a>Étapes suivantes

Après avoir installé Advanced eDiscovery, vous êtes prêt à [créer un cas.](create-and-manage-advanced-ediscoveryv2-case.md)
