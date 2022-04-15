---
title: Attribuer des rôles et des autorisations dans Microsoft Defender pour les PME
description: Découvrez comment attribuer des rôles et des autorisations dans Microsoft Defender pour les PME
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: e4a3be91ff46626654f0c0f7b027557958429b33
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862673"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>Attribuer des rôles et des autorisations dans Microsoft Defender pour les PME

> [!NOTE]
> Microsoft Defender pour les PME est désormais inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md). 

Pour effectuer des tâches dans le portail Microsoft 365 Defender, telles que la configuration de Microsoft Defender pour les PME, l’affichage de rapports ou l’exécution d’actions de réponse sur les menaces détectées, des autorisations appropriées doivent être attribuées à votre équipe de sécurité. Les autorisations sont accordées par le biais de rôles attribués dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ou dans [Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>Procédure

1. [En savoir plus sur les rôles dans Defender pour Entreprises](#roles-in-defender-for-business).

2. [Affichez ou modifiez les attributions de rôles pour votre équipe de sécurité](#view-or-edit-role-assignments).

3. [Passez à vos étapes suivantes](#next-steps).

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="roles-in-defender-for-business"></a>Rôles dans Defender entreprise

Le tableau suivant décrit les trois rôles qui peuvent être attribués dans Defender entreprise. [En savoir plus sur les rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

| Niveau d’autorisation | Description |
|:---|:---|
| **Administrateurs généraux** (également appelés administrateurs généraux) <br/><br/> *Il est recommandé de limiter le nombre d’administrateurs généraux.* | Les administrateurs généraux peuvent effectuer toutes sortes de tâches. La personne qui a inscrit votre entreprise pour Microsoft 365 ou pour Microsoft Defender pour les PME est un administrateur général par défaut. <br/><br/> Les administrateurs généraux sont en mesure d’accéder aux paramètres/de les modifier sur tous les portails Microsoft 365, par exemple : <br/>- Le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) |
| **Administrateurs de sécurité** (également appelés administrateurs de sécurité) | Les administrateurs de sécurité peuvent effectuer les tâches suivantes : <br/>- Afficher et gérer les stratégies de sécurité <br/>- Afficher et gérer les menaces et alertes de sécurité (ces activités incluent la prise d’actions de réponse sur les points de terminaison) <br/>- Afficher les informations et les rapports de sécurité |
| **Lecteur de sécurité** | Les lecteurs de sécurité peuvent effectuer les tâches suivantes : <br/>- Afficher les stratégies de sécurité <br/>- Afficher les menaces et alertes de sécurité <br/>- Afficher les informations et les rapports de sécurité  |


## <a name="view-or-edit-role-assignments"></a>Afficher ou modifier des attributions de rôles

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans le volet de navigation, choisissez **Autorisations & rôles**, puis sous **Azure AD**, sélectionnez **Rôles**.

3. Sélectionnez l’un des rôles suivants pour ouvrir son volet latéral :

   - Administrateur général
   - Administrateur de sécurité
   - Lecteur Sécurité

   > [!IMPORTANT]
   > Microsoft recommande d’accorder aux utilisateurs l’accès uniquement à ce dont ils ont besoin pour effectuer leurs tâches. Nous appelons ce concept *le privilège minimum* pour les autorisations. Pour plus d’informations, consultez [les meilleures pratiques pour l’accès le moins privilégié pour les applications](/azure/active-directory/develop/secure-least-privileged-access). 

4. Dans le volet latéral, sélectionnez les **membres Gérer dans Azure AD** lien. Cette action vous permet d’Azure Active Directory (Azure AD) où vous pouvez afficher et gérer vos attributions de rôles.

5. Sélectionnez un utilisateur pour ouvrir son profil, puis choisissez **Rôles attribués**.

   - Pour ajouter un rôle, choisissez **+ Ajouter des affectations**.
   - Pour supprimer un rôle, choisissez **X Supprimer les affectations**. 

## <a name="need-to-add-users"></a>Vous avez besoin d’ajouter des utilisateurs ?

Si vous n’avez pas encore ajouté d’utilisateurs à votre abonnement, consultez [Ajouter des utilisateurs et attribuez des licences en même temps](mdb-add-users.md).

## <a name="next-steps"></a>Prochaines étapes

Passez à :

- [Étape 3 : Configurer des notifications par e-mail](mdb-email-notifications.md)
- [Étape 4 : Intégrer des appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md)