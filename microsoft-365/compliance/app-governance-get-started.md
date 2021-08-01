---
title: Démarrer avec la gouvernance des applications
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
localization_priority: Priority
search.appverid:
- MOE150
- MET150
description: Démarrage avec des fonctionnalités de gouvernance des applications pour régir vos applications.
ms.openlocfilehash: c4cdc83d41a888fbf395d2c13e442bbaaf7da54e
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53621678"
---
# <a name="get-started-with-app-governance-in-preview"></a>Démarrage avec la gouvernance des applications (en préversion)

Pour commencer à utiliser le module complémentaire de gouvernance des applications de Microsoft Cloud App Security :

1. Vérifiez que votre compte dispose du [niveau de licence approprié](#licensing-for-app-governance). La gouvernance des applications est une fonctionnalité complémentaire de Microsoft Cloud App Security (MCAS), et MCAS doit donc être présent dans votre compte en tant que produit autonome ou dans le cadre des différents packs de licences énumérés ci-dessous.
1. Vous devez avoir l’un des [rôles d’administrateur](#administrator-roles) répertoriés ci-dessous pour accéder aux pages de gouvernance des applications dans le portail.
1. L’inscription de client de votre organisation doit se trouver dans l’une des [zones prises en charge d’Amérique du Nord, d’Europe ou d’Afrique](app-governance-countries.md).

## <a name="add-app-governance-to-your-microsoft-365-account"></a>Ajouter la gouvernance des applications à votre compte Microsoft 365

Pour les nouveaux clients Microsoft 365 :

1. En haut de cette page, cliquez sur le bouton  **Compte gratuit** .
1. Sous  **Essayez Microsoft 365 pour les entreprises** cliquez sur  **Essai gratuit d’un mois**.
1. Effectuez les étapes de l’inscription.

Pour les clients Microsoft 365 existants :

1. Dans votre Centre d’administration Microsoft 365, accédez à  **Facturation** > **Acheter des services** et cliquez sur **Modules complémentaires**. Utilisez la barre de recherche pour localiser **gouvernance des applications**.
1. Dans la carte de gouvernance des applications, cliquez sur  **Détails**.
1. Cliquez sur **Activer Démarrer l'essai gratuit**.

## <a name="add-integration-with-mcas"></a>Ajouter une intégration à MCAS 

Conditions préalables :

- Office 365 est connecté dans Sécurité des applications cloud
- Les applications office 365 Azure AD sont activées

Pour activer la synchronisation de la gouvernance des applications avec Sécurité des applications cloud, procédez comme suit :

1. Accédez à votre portail Microsoft Cloud App Security : [https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com)
1. Cliquez sur l’icône d’engrenage (coin supérieur droit), puis sélectionnez **Paramètres**.
1. Sous **Protection contre les menaces**, sélectionnez **Gouvernance des applications**.
1. Cliquez sur **Activer l’intégration de la gouvernance des applications**, puis sélectionnez **Enregistrer**.

Ensuite, passez en revue les stratégies nouvellement activées dans MCAS. L’affichage des nouvelles stratégies peut prendre quelques minutes une fois l’intégration activée.

- Réputation de l’application OAuth Microsoft 365
- Détection de l'hameçonnage de OAuth Microsoft 365
- Gouvernance des applications OAuth Microsoft 365
- Examiner le widget Gouvernance des applications dans le tableau de bord MCAS
- Examinez les alertes de gouvernance d'applications nouvellement générées dans les alertes MCAS.
- Examinez les stratégies OAuth MCAS M365 dans la liste des stratégies de gouvernance des applications.
- Examinez les alertes OAuth MCAS M365 nouvellement générées dans les alertes de gouvernance des applications

## <a name="licensing-for-app-governance"></a>Licences pour la gouvernance des applications

Avant de vous lancer dans la gouvernance des applications, vous devez confirmer votre centre d'administration [Microsoft 365 – les abonnements](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/subscriptions) et les éventuels modules complémentaires. Pour accéder à la gouvernance des applications et l’utiliser, votre organisation doit disposer de l’un des abonnements ou modules complémentaires suivants :

- Microsoft Cloud App Security
- Microsoft 365 E5
- Microsoft 365 E5 Conformité
- Développeur Microsoft 365 E5 (sans Windows et Audioconférence)
- Microsoft 365 E5, Protection des informations et gouvernance
- Microsoft 365 E5 Sécurité
- Microsoft 365 E5 avec minutes d’appels
- Microsoft 365 E5 sans Audioconférence
- Conformité Microsoft 365 A5 pour les enseignants
- Conformité Microsoft 365 A5 pour les étudiants
- Microsoft 365 A5 pour les enseignants
- Microsoft 365 A5 pour les étudiants
- Microsoft 365 A5 - Information Protection et gouvernance pour les enseignants
- Microsoft 365 A5 - Information Protection et gouvernance pour les étudiants
- Sécurité Microsoft 365 A5 pour les enseignants
- Sécurité Microsoft 365 A5 pour les étudiants
- Avantages de l’utilisation de Microsoft 365 A5 pour les étudiants
- Microsoft 365 A5 avec minutes d’appels pour les enseignants
- Microsoft 365 A5 avec minutes d’appels pour les étudiants
- Microsoft 365 A5 sans Audioconférence pour les enseignants
- Microsoft 365 A5 sans Audioconférence pour les étudiants
- Avantages de l’utilisation de Microsoft 365 A5 pour les étudiants sans Audioconférence

## <a name="administrator-roles"></a>Rôles d'administrateur

> [!NOTE]
> Seul un rôle d’administrateur global peut activer l'essai gratuit de la gouvernance de l'application.

L'un des rôles d'administrateur suivants est requis pour voir les pages de gouvernance des applications ou gérer les stratégies et les paramètres :

- Administrateur de l'application
- Administrateur de l'application cloud
- Administrateur de la société
- Administrateur de conformité
- Administrateur de conformité des données
- Lecteur de conformité (en lecture seule)
- Lecteur général
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur sécurité (en lecture seule)

> [!NOTE]
> Seul un administrateur global peut activer l'essai gratuit de la gouvernance de l'application.

Voici les fonctionnalités de chaque rôle.

| Rôle | Lire le tableau de bord | Lire toutes les applications |Lire les stratégies | Créer, mettre à jour ou supprimer des stratégies | Lire les alertes | Mettre à jour des alertes | Lire les paramètres | Définir les paramètres de mise à jour | Lire la correction | Mettre à jour la correction |
|:-------|:-----|:-------|:-------|:-------|:-------|:-------|:-------|:-------|:-------|:-------|
| Administrateur de l'application | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) |
| Administrateur de l'application cloud | ![Coche](..\media\checkmark.png) | | | | | | | | | |
| Administrateur de la société | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) |
| Administrateur de conformité | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) |  | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | |
| Administrateur de conformité des données | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) |  | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | |
| Lecteur de conformité | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) |  | ![Coche](..\media\checkmark.png) |  | ![Coche](..\media\checkmark.png) |  | | |
| Lecteur général  | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) |  | ![Coche](..\media\checkmark.png) |  | ![Coche](..\media\checkmark.png) |  | | |
| Administrateur de sécurité | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) |  | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | |
| Opérateur de sécurité | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | |
| Lecteur de sécurité  | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) | ![Coche](..\media\checkmark.png) |  | ![Coche](..\media\checkmark.png) |  | ![Coche](..\media\checkmark.png) |  | ![Coche](..\media\checkmark.png) | |
|||||||||| | |

Pour plus d’informations sur chaque rôle, consultez [Autorisations de rôle Administrateur](/azure/active-directory/roles/permissions-reference).

## <a name="canceling-your-trial"></a>Annulation de votre version d'évaluation

Si vous n'avez pas participé à la préversion privée et que vous souhaitez annuler votre version d'évaluation de la gouvernance des applications, vous pouvez communiquer avec votre contact CXE ou suivre les étapes suivantes :

1. Dans le Centre d’administration Microsoft 365, accédez à **Facturation** > **Vos produits**.
1. Accédez à la version d’évaluation de la gouvernance des applications, cliquez sur les trois points, puis sélectionnez **Annuler l’abonnement**.
1. Dans le volet volant qui en résulte, indiquez la raison de l’annulation, les commentaires supplémentaires, puis sélectionnez **Annuler l’abonnement**.
1. Sélectionnez **Annuler l’abonnement** dans l’écran contextuel qui en résulte. Votre version d'évaluation est annulée, vous perdez l'accès à la gouvernance des applications et vos données de gouvernance des applications sont supprimées (données de journal utilisées pour créer les aperçus et les détections de gouvernance des applications, aucun courriel ou autre fichier n'est affecté).

## <a name="known-issues-for-the-public-preview"></a>Problèmes connus dans la préversion publique

L’équipe de gouvernance des applications a identifié les problèmes connus suivants pour la préversion : 

- Synchronisation bidirectionnelle entre Microsoft Defender et les alertes de gouvernance des applications : actuellement, les alertes résolues dans Defender doivent également être résolues manuellement dans la gouvernance des applications.
- Les informations sur les comptes prioritaires dans les onglets Utilisateurs d’application et Utilisation ne fonctionnent pas comme prévu pour certains utilisateurs.
