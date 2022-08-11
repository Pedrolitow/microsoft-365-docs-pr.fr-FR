---
title: Attribuer des rôles et des autorisations dans Microsoft Defender pour entreprises
description: Attribuez des rôles à votre équipe de cybersécurité. Découvrez ces rôles et autorisations dans Defender entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.date: 08/09/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365solution-mdb-setup
ms.openlocfilehash: b8e884c207479a7d2781e1ea4e31b9ee91bd25db
ms.sourcegitcommit: 6bff75867764335685f972943170c7db46e33a6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2022
ms.locfileid: "67300889"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>Attribuer des rôles et des autorisations dans Microsoft Defender pour entreprises

Pour effectuer des tâches dans le portail Microsoft 365 Defender, telles que la configuration de Defender entreprise, l’affichage de rapports ou l’exécution d’actions de réponse sur les menaces détectées, des autorisations appropriées doivent être attribuées à votre équipe de sécurité. Les autorisations sont accordées par le biais de rôles qui sont affectés dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ou dans [Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>Procédure

1. [En savoir plus sur les rôles dans Defender pour entreprises](#roles-in-defender-for-business).
2. [Afficher ou modifier les attributions de rôles pour votre équipe de sécurité](#view-or-edit-role-assignments).
3. [Passez à vos étapes suivantes](#next-steps).


## <a name="roles-in-defender-for-business"></a>Rôles dans Defender entreprise

Le tableau suivant décrit les trois rôles qui peuvent être attribués dans Defender entreprise. [En savoir plus sur les rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

| Niveau d’autorisation | Description |
|:---|:---|
| **Administrateurs généraux** (également appelés administrateurs généraux) <p> *Il est recommandé de limiter le nombre d’administrateurs généraux.* | Les administrateurs généraux peuvent effectuer toutes sortes de tâches. La personne qui a inscrit votre entreprise pour Microsoft 365 ou Defender Entreprise est un administrateur général par défaut. <p> Les administrateurs généraux peuvent modifier les paramètres de tous les portails Microsoft 365, par exemple : <ul><li>Le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))</li><li>portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))</li></ul> |
| **Administrateurs de sécurité** (également appelés administrateurs de sécurité) | Les administrateurs de sécurité peuvent effectuer les tâches suivantes : <ul><li>Afficher et gérer les stratégies de sécurité</li><li>Afficher et gérer les menaces et alertes de sécurité (ces activités incluent la prise d’actions de réponse sur les points de terminaison)</li><li>Afficher les informations et les rapports de sécurité</li></ul> |
| **Lecteur de sécurité** | Les lecteurs de sécurité peuvent effectuer les tâches suivantes :<ul><li>Afficher les stratégies de sécurité</li><li>Afficher les menaces et les alertes de sécurité</li><li>Afficher les informations et les rapports de sécurité</li></ul>  |


## <a name="view-or-edit-role-assignments"></a>Afficher ou modifier des attributions de rôles

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Autorisations & rôles**, puis sous **Azure AD**, sélectionnez **Rôles**.

3. Sélectionnez l’un des rôles suivants pour ouvrir son volet latéral :

   - Administrateur général
   - Administrateur de sécurité
   - Lecteur Sécurité

   > [!IMPORTANT]
   > Microsoft vous recommande d’accorder aux utilisateurs l’accès uniquement à ce dont ils ont besoin pour effectuer leurs tâches. Nous appelons ce concept *le privilège minimum* pour les autorisations. Pour plus d’informations, consultez [les meilleures pratiques pour l’accès le moins privilégié pour les applications](/azure/active-directory/develop/secure-least-privileged-access). 

4. Dans le volet latéral, sélectionnez le lien **Gérer les membres dans Azure AD** . Cette action vous permet d’accéder à Azure Active Directory (Azure AD), où vous pouvez afficher et gérer vos attributions de rôles.

5. Sélectionnez un utilisateur pour ouvrir son profil, puis choisissez **Rôles attribués**.

   - Pour ajouter un rôle, choisissez **+ Ajouter des affectations**.
   - Pour supprimer un rôle, choisissez **X Supprimer les affectations**. 

## <a name="need-to-add-users"></a>Vous avez besoin d’ajouter des utilisateurs ?

Si vous n’avez pas encore ajouté d’utilisateurs à votre abonnement, consultez [Ajouter des utilisateurs et attribuez des licences en même temps](mdb-add-users.md).

## <a name="next-steps"></a>Prochaines étapes

Atteindre:

- [Étape 3 : Configurer des notifications par e-mail](mdb-email-notifications.md)
- [Étape 4 : Intégrer des appareils à Defender entreprise](mdb-onboard-devices.md)