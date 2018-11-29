---
title: 'Étape 1 : Planifier les utilisateurs et les groupes'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/13/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Planifiez l’ensemble des utilisateurs et des groupes qui travailleront pour votre organisation.
ms.openlocfilehash: 8062cc2b681f0ae45a8114a6d827f5d1ece2fe3e
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866831"
---
# <a name="step-1-plan-for-users-and-groups"></a>Étape 1 : Planifier les utilisateurs et les groupes

*Cette étape est requise et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

À cette étape, vous allez créer votre infrastructure d’identités qui combine des utilisateurs, des groupes et l’appartenance à un groupe avec des fonctionnalités de sécurité dans la configuration correcte. Vous pouvez ainsi :

- contrôler qui a accès aux ressources dans votre environnement ;
- sécuriser l’accès avec des contrôles qui garantissent de fortes assurances concernant l’identité (les utilisateurs sont ce qu’ils déclarent être) et l’accès à partir d’appareils approuvés ;
- configurer des ressources dans votre environnement avec des autorisations appropriées pour réduire le risque potentiel de fuite des données. 
- surveiller votre environnement afin de contrôler les comportements d’utilisateur anormaux et agir automatiquement.

## <a name="plan-your-primary-identity-provider"></a>Planifier votre fournisseur d’identité principal

Pour créer votre infrastructure d’identités, vous désignerez un fournisseur d’identité principal. Ce service stocke les comptes d’utilisateur et leurs attributs, groupes et appartenances, et prend en charge leur administration continue.

Lorsque votre organisation adopte Microsoft 365 Entreprise, votre fournisseur d’identité principal peut être :

- **Windows Server Active Directory (AD)**, un fournisseur d’identité intranet hébergé sur des ordinateurs exécutant Windows Server. Cela est généralement utilisé par les organisations qui ont un fournisseur d’identité local existant.
- **Azure Active Directory (Azure AD**), une identité basée sur le cloud en tant que Service (IDaaS) qui fournit un large éventail de fonctionnalités pour la gestion et la protection de votre environnement. Cela est généralement utilisé par les organisations qui n’ont aucune infrastructure locale existante.

Si votre organisation a un fournisseur d’identité local existant, vous devez synchroniser vos groupes et comptes d’utilisateur de Windows Server AD avec Azure AD pour fournir un accès plus transparent aux services basés sur le cloud de Microsoft 365 Entreprise. Vous pouvez également utiliser Azure AD pour créer et gérer des groupes qui existent uniquement dans le cloud Microsoft.

Une fois que vous avez vos utilisateurs et groupes dans Azure AD, vous pouvez :

- gérer tous les comptes Azure AD pour toutes vos applications cloud ; 
- utiliser le même ensemble de contrôles pour protéger l’accès aux applications au sein de votre environnement ;
- collaborer avec des partenaires externes ;
- surveiller un comportement de compte anormal (comme des tentatives de connexion suspectes) et agir automatiquement.

Lisez les instructions des deux sections suivantes pour planifier et implémenter vos groupes et comptes d’utilisateur.

## <a name="categorize-your-users"></a>Classer vos utilisateurs
Les utilisateurs dans les organisations peuvent être classés de plusieurs façons. Par exemple, certains utilisateurs sont des employés qui ont un statut permanent. Certains sont des fournisseurs, des entrepreneurs ou des partenaires qui ont un statut temporaire. Certains sont des utilisateurs externes qui n’ont aucun compte d’utilisateur mais doivent avoir accès à des ressources et services spécifiques pour prendre en charge l’interaction et la collaboration. Par exemple :

- Les comptes client représentent les utilisateurs au sein de votre organisation auxquels vous octroyez une licence pour les services cloud
- Les comptes B2B représentent les utilisateurs externes à votre organisation que vous invitez à participer à la collaboration

Répertoriez les types d’utilisateurs de votre organisation. Quels sont les regroupements ? Par exemple, vous pouvez regrouper des utilisateurs par fonction de haut niveau ou par objectif pour votre organisation.

Par ailleurs, certains services cloud peuvent être partagés avec des utilisateurs externes à votre organisation sans comptes d’utilisateur. Vous devrez identifier ces groupes d’utilisateurs également.

## <a name="plan-for-windows-server-ad-and-azure-ad-groups"></a>Planifier pour des groupes Windows Server AD et Azure AD

Vous pouvez utiliser des groupes dans Azure AD à plusieurs fins qui simplifient la gestion de votre environnement cloud. Par exemple, pour les groupes Azure AD, vous pouvez :

- utiliser la gestion des licences par groupes pour attribuer des licences pour Office 365 et Enterprise Mobility + Security (EMS) à vos comptes d’utilisateur automatiquement dès qu’ils sont ajoutés dans Azure AD ou synchronisés à partir de Windows Server AD ; 
- ajouter des comptes d’utilisateur à des groupes spécifiques dynamiquement basés sur des attributs de compte d’utilisateur, comme l’attribut service ;  
- configurer automatiquement des utilisateurs pour des applications SaaS et protéger l’accès à ces applications avec l’authentification multifacteur et d’autres règles d’accès conditionnel ;
- configurer les autorisations et niveaux d’accès pour les sites d’équipe SharePoint Online. Les groupes Azure AD peuvent également être utilisés avec des stratégies Azure Information Protection limitées pour protéger des fichiers avec le chiffrement et les autorisations. 

## <a name="results"></a>Résultats

Lorsque vous terminez cette étape, vous avez :

- une liste de comptes d’utilisateur dans Azure AD qui correspondent aux employés au sein de votre organisation et les fournisseurs, entrepreneurs et partenaires qui travaillent pour ou avec votre organisation ;
- un ensemble de groupes et leur appartenance dans Azure AD qui représentent des ensembles logiques de comptes d’utilisateur et d’autres groupes pour l’attribution de paramètres de sécurité pour les services de cloud computing Microsoft et l’attribution automatique de licences.

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-user-groups) pour cette étape.


## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step2.png)| [Protéger des comptes Administrateur général](identity-designate-protect-admin-accounts.md) |

