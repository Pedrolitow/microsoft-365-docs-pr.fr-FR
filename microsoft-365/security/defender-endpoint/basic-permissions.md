---
title: Utiliser des autorisations de base pour accéder à Centre de sécurité Microsoft Defender
description: Découvrez comment utiliser les autorisations de base pour accéder au portail Microsoft Defender pour point de terminaison.
keywords: attribuer des rôles d’utilisateur, attribuer un accès en lecture et en écriture, attribuer un accès en lecture seule, utilisateur, rôles d’utilisateur, rôles
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.service: microsoft-365-security
ms.subservice: mde
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
search.appverid: met150
ms.openlocfilehash: a90250b69315c954688849337a985f2a99afa724
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68641730"
---
# <a name="use-basic-permissions-to-access-the-portal"></a>Utiliser des autorisations de base pour accéder au portail

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- Azure Active Directory
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-basicaccess-abovefoldlink)

Reportez-vous aux instructions ci-dessous pour utiliser la gestion des autorisations de base.

Vous pouvez utiliser l’une des solutions suivantes :

- Azure PowerShell
- Portail Azure

Pour un contrôle granulaire sur les autorisations, [basculez vers le contrôle d’accès en fonction du rôle](rbac.md).

## <a name="assign-user-access-using-azure-powershell"></a>Attribuer un accès utilisateur à l’aide de Azure PowerShell

Vous pouvez affecter des utilisateurs avec l’un des niveaux d’autorisation suivants :

- Accès complet (lecture et écriture)
- Accès en lecture seule

### <a name="before-you-begin"></a>Avant de commencer

- Installez Azure PowerShell. Pour plus d’informations, voir [Comment installer et configurer Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).

  > [!NOTE]
  > Vous devez exécuter les applets de commande PowerShell dans une ligne de commande avec élévation de privilèges.

- Connectez-vous à votre annuaire Azure Active Directory. Pour plus d’informations, consultez [Connect-MsolService](/powershell/module/msonline/connect-msolservice).

  - **Accès complet** : les utilisateurs disposant d’un accès complet peuvent se connecter, afficher toutes les informations système et résoudre les alertes, envoyer des fichiers pour une analyse approfondie et télécharger le package d’intégration. L’attribution de droits d’accès complets nécessite l’ajout des utilisateurs aux rôles intégrés AAD « Administrateur de sécurité » ou « Administrateur général ».
  - **Accès en lecture seule** : les utilisateurs disposant d’un accès en lecture seule peuvent se connecter, afficher toutes les alertes et les informations associées.

    Ils ne seront pas en mesure de modifier les états d’alerte, d’envoyer des fichiers pour une analyse approfondie ou d’effectuer des opérations de modification d’état.

    L’attribution de droits d’accès en lecture seule nécessite d’ajouter les utilisateurs au rôle intégré Azure AD « Lecteur de sécurité ».

Procédez comme suit pour attribuer des rôles de sécurité :

- Pour l’accès en **lecture et en écriture** , affectez des utilisateurs au rôle d’administrateur de sécurité à l’aide de la commande suivante :

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress "secadmin@Contoso.onmicrosoft.com"
  ```

- Pour un accès **en lecture seule** , affectez aux utilisateurs le rôle lecteur sécurité à l’aide de la commande suivante :

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Reader" -RoleMemberEmailAddress "reader@Contoso.onmicrosoft.com"
  ```

Pour plus d’informations, consultez [Ajouter ou supprimer des membres de groupe à l’aide d’Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal).

## <a name="assign-user-access-using-the-azure-portal"></a>Attribuer l’accès utilisateur à l’aide de la Portail Azure

Pour plus d’informations, consultez [Attribuer des rôles d’administrateur et de non-administrateur aux utilisateurs avec Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

## <a name="related-topic"></a>Rubrique connexe

- [Gérer l’accès au portail à l’aide de RBAC](rbac.md)
