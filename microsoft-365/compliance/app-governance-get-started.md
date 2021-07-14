---
title: Démarrer avec la gouvernance des applications
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: JoeDavies-MSFT
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
ms.openlocfilehash: 0fc00819947d3d472de9199b0381c6f33de0acd6
ms.sourcegitcommit: 41c7f7bd5c808ee5ceca0f6efe13d4e67da0262b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2021
ms.locfileid: "53420165"
---
# <a name="get-started-with-app-governance-in-preview"></a>Démarrage avec la gouvernance des applications (en préversion)

Pour commencer à utiliser la fonctionnalité de gouvernance des applications pour Microsoft Cloud App Security :

1. Vérifiez que votre compte dispose du niveau de licence approprié. La gouvernance des applications est une fonctionnalité complémentaire pour Microsoft Cloud App Security (MCAS). Par conséquent, MCAS doit être présent dans votre compte en tant que produit autonome ou dans le cadre des différents packages de licences répertoriés ci-dessous.
1. Vous devez avoir l’un des rôles d’administrateur répertoriés ci-dessous pour accéder aux pages de gouvernance des applications dans le portail.

## <a name="licensing-for-app-governance"></a>Licences pour la gouvernance des applications

Avant de commencer à utiliser la gouvernance des applications, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) et tous les modules complémentaires. Pour accéder à la gouvernance des applications et l’utiliser, votre organisation doit disposer de l’un des abonnements ou modules complémentaires suivants :

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

L’un des rôles d’administrateur suivants est nécessaire pour afficher les pages de gouvernance des applications ou gérer les stratégies et les paramètres :

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

## <a name="add-app-governance-to-your-microsoft-365-account"></a>Ajouter la gouvernance des applications à votre compte Microsoft 365

Pour les clients Microsoft 365 existants :

1. Dans votre [Centre d’administration Microsoft 365](https://admin.microsoft.com), accédez à **Facturation - Acheter des services** et cliquez sur **modules complémentaires**.
1. Dans la carte de gouvernance des applications, cliquez sur **Détails**.
1. Cliquez sur **Démarrer l’essai gratuit**.
1. Renseignez les informations demandées pour ajouter la gouvernance des applications à votre client sélectionné. Si vous êtes un nouveau client, vous devez d’abord fournir des informations pour établir un compte et créer un client pour votre période d’essai. Une fois cette opération effectuée, vous pouvez ajouter la gouvernance des applications à la version d’évaluation.

Pour les nouveaux clients Microsoft 365 :

1. En haut de cette page, cliquez sur le bouton **Compte gratuit** .
1. Sous **Essayez Microsoft 365 pour les entreprises** cliquez sur **Essai gratuit d’un mois**.

Pour les deux :

1. Dans le portail d’inscription, indiquez votre adresse e-mail à utiliser pour la version d’évaluation. Si vous êtes un client existant, utilisez l’e-mail associé à votre compte. Cliquez sur **Suivant**.
1. Une fois que vous êtes connecté, cliquez sur **Essayez maintenant** pour obtenir l’essai gratuit.
1. Cliquez sur **Continuer** pour fermer la page et commencer la configuration de la version d’évaluation. Pour les nouveaux clients de gouvernance des applications, la mise à disposition de votre instance de gouvernance des applications peut prendre jusqu’à deux heures. Pour les clients existants, il n’y aura aucune interruption des services existants.
  > [!NOTE]
Si vous n’avez pas encore de compte, vous serez invité à configurer un nouveau compte avant de poursuivre l’essai.

1. Entrez un nom de domaine disponible pour votre client AAD, puis cliquez sur **Vérifier la disponibilité**. Vous recevrez automatiquement un rôle d’administrateur (si vous n’avez pas de rôle existant pour la gouvernance des applications) et pourrez toujours modifier le nom de domaine et/ou acheter d’autres clients ultérieurement via le Centre d’administration Microsoft 365.
1. Entrez le nom d’utilisateur et le mot de passe que vous souhaitez utiliser pour vous connecter à votre compte. Cliquez sur **S’inscrire**.
1. Cliquez sur **Démarrage** pour accéder au portail de gouvernance des applications ou **Gérer votre abonnement** pour accéder au Centre d’administration Microsoft 365.
