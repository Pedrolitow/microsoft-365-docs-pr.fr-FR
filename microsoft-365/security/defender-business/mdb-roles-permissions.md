---
title: Attribuer des rôles et des autorisations dans Microsoft Defender entreprise
description: Découvrez comment attribuer des rôles et des autorisations dans Microsoft Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/10/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 4e87b8b2bbf926e231e5d610e212f7b73005d1ce
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449124"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>Attribuer des rôles et des autorisations dans Microsoft Defender entreprise

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement [Microsoft 365 Business Premium clients,](../../business-premium/index.md) à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Pour effectuer des tâches dans le portail Microsoft 365 Defender, telles que la configuration de Microsoft Defender pour les entreprises, l’affichage de rapports ou l’exécution d’actions de réponse sur les menaces détectées, des autorisations appropriées doivent être attribuées à votre équipe de sécurité. Les autorisations sont accordées par le biais de rôles attribués dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ou [dans Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>Procédure

1. [Découvrez les rôles dans Defender for Business](#roles-in-defender-for-business).

2. [Afficher ou modifier les attributions de rôles pour votre équipe de sécurité](#view-or-edit-role-assignments).

3. [Procédez comme vous le faire pour les étapes suivantes](#next-steps).

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>


## <a name="roles-in-defender-for-business"></a>Rôles dans Defender for Business

Le tableau suivant décrit les trois rôles qui peuvent être attribués dans Defender for Business. [En savoir plus sur les rôles d’administrateur](../../admin/add-users/about-admin-roles.md). <br/><br/>

| Niveau d’autorisation | Description |
|:---|:---|
| **Administrateurs globaux** (également appelés administrateurs globaux) <br/><br/> *En tant que meilleure pratique, limitez le nombre d’administrateurs globaux.* | Les administrateurs globaux peuvent effectuer toutes sortes de tâches. La personne qui a inscrit votre organisation à Microsoft 365 ou Microsoft Defender entreprise est un administrateur général par défaut. <br/><br/> Les administrateurs globaux peuvent accéder/modifier les paramètres sur tous les portails Microsoft 365, tels que : <br/>- Le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portail ([https://security.microsoft.com](https://security.microsoft.com)) |
| **Administrateurs de sécurité** (également appelés administrateurs de sécurité) | Les administrateurs de sécurité peuvent effectuer les tâches suivantes : <br/>- Afficher et gérer les stratégies de sécurité <br/>- Afficher et gérer les alertes et les menaces de sécurité (ces activités incluent la prise d’actions de réponse sur les points de terminaison) <br/>- Afficher les informations de sécurité et les rapports |
| **Lecteur de sécurité** | Les lecteurs de sécurité peuvent effectuer les tâches suivantes : <br/>- Afficher les stratégies de sécurité <br/>- Afficher les menaces et alertes de sécurité <br/>- Afficher les informations de sécurité et les rapports  |


## <a name="view-or-edit-role-assignments"></a>Afficher ou modifier des attributions de rôles

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Dans le volet de navigation, sélectionnez **Autorisations & rôles**, puis sous **Azure AD,** sélectionnez **Rôles**.

3. Sélectionnez l’un des rôles suivants pour ouvrir son volet latéral :

   - Administrateur général
   - Administrateur de sécurité
   - Lecteur Sécurité

   > [!IMPORTANT]
   > Microsoft recommande d’accorder aux personnes l’accès uniquement à ce dont elles ont besoin pour effectuer leurs tâches. Nous appelons ce concept *le privilège minimum* pour les autorisations. Pour en savoir plus, [consultez Les meilleures pratiques en matière d’accès moins privilégié pour les applications](/azure/active-directory/develop/secure-least-privileged-access). 

4. Dans le volet latéral, sélectionnez les membres **Gérer Azure AD** lien. Cette action vous permet d’Azure Active Directory (Azure AD) où vous pouvez afficher et gérer vos attributions de rôles.

5. Sélectionnez un utilisateur pour ouvrir son profil, puis choisissez **Rôles attribués**.

   - Pour ajouter un rôle, choisissez **+ Ajouter des affectations**.
   - Pour supprimer un rôle, choisissez **X Supprimer les affectations**. 

## <a name="next-steps"></a>Prochaines étapes

Procédez comme il se doit pour :

- [Étape 3 : Configurer les notifications par courrier électronique](mdb-email-notifications.md)

- [Étape 4 : Intégrer des appareils à Microsoft Defender pour Entreprises](mdb-onboard-devices.md)