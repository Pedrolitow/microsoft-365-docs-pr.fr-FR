---
title: Utiliser des autorisations de base pour accéder Centre de sécurité Microsoft Defender
description: Découvrez comment utiliser les autorisations de base pour accéder au portail Microsoft Defender for Endpoint.
keywords: attribuer des rôles d’utilisateur, attribuer un accès en lecture et en écriture, attribuer un accès en lecture seule, utilisateur, rôles d’utilisateur, rôles
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 05e9eadb9047fd4a2c8a4d01ecefc3ec2f73f9db
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60207988"
---
# <a name="use-basic-permissions-to-access-the-portal"></a>Utiliser des autorisations de base pour accéder au portail

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- Azure Active Directory
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-basicaccess-abovefoldlink)

Reportez-vous aux instructions ci-dessous pour utiliser la gestion des autorisations de base.

Vous pouvez utiliser l’une des solutions suivantes :

- Azure PowerShell
- Portail Azure

Pour un contrôle granulaire des autorisations, [basculez vers le contrôle d’accès basé sur les rôles.](rbac.md)

## <a name="assign-user-access-using-azure-powershell"></a>Attribuer un accès utilisateur à l’aide Azure PowerShell

Vous pouvez affecter des utilisateurs avec l’un des niveaux d’autorisation suivants :

- Accès total (lecture et écriture)
- Accès en lecture seule

### <a name="before-you-begin"></a>Avant de commencer

- Installez Azure PowerShell. Pour plus d’informations, voir [comment installer et configurer Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).

  > [!NOTE]
  > Vous devez exécuter les cmdlets PowerShell dans une ligne de commande avec élévation de élévation de niveaux.

- Connecter à votre Azure Active Directory. Pour plus d’informations, [voir Connecter-MsolService](/powershell/module/msonline/connect-msolservice).

  - **Accès total**: les utilisateurs ayant un accès total peuvent se connecter, afficher toutes les informations système et résoudre les alertes, soumettre des fichiers pour une analyse approfondie et télécharger le package d’intégration. L’attribution de droits d’accès total nécessite l’ajout des utilisateurs aux rôles intégrés AAD « Administrateur de la sécurité » ou « Administrateur général ».
  - **Accès en lecture seule**: les utilisateurs ayant un accès en lecture seule peuvent se connecter, afficher toutes les alertes et les informations connexes.

    Ils ne pourront pas modifier les états d’alerte, soumettre des fichiers pour analyse approfondie ou effectuer des opérations de changement d’état.

    L’attribution de droits d’accès en lecture seule nécessite l’ajout des utilisateurs au rôle intégré Azure AD « Lecteur de sécurité ».

Pour attribuer des rôles de sécurité, utilisez les étapes suivantes :

- Pour **accéder en lecture et en** écriture, attribuez aux utilisateurs le rôle d’administrateur de sécurité à l’aide de la commande suivante :

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress "secadmin@Contoso.onmicrosoft.com"
  ```

- Pour **un accès en lecture seule,** attribuez aux utilisateurs le rôle de lecteur de sécurité à l’aide de la commande suivante :

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Reader" -RoleMemberEmailAddress "reader@Contoso.onmicrosoft.com"
  ```

Pour plus d’informations, voir Ajouter ou supprimer des membres du groupe à [l’aide Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal).

## <a name="assign-user-access-using-the-azure-portal"></a>Attribuer un accès utilisateur à l’aide du portail Azure

Pour plus d’informations, voir [Attribuer des rôles d’administrateur et de non-administrateur](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal)aux utilisateurs Azure Active Directory .

## <a name="related-topic"></a>Rubrique connexe

- [Gérer l’accès au portail à l’aide de RBAC](rbac.md)
