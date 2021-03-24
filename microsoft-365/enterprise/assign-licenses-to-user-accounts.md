---
title: Attribuer des licences Microsoft 365 à des comptes d’utilisateur
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Décrit comment attribuer des licences Microsoft 365 à des comptes d’utilisateur, individuellement ou en fonction de l’appartenance à un groupe.
ms.openlocfilehash: 2fe1e2f959fae8b0bc82a7dcd4f65f33b21c368a
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51051531"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>Attribuer des licences Microsoft 365 à des comptes d’utilisateur

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Pour le modèle d’identité cloud uniquement, vous pouvez attribuer des licences Microsoft 365 aux comptes d’utilisateur lors de leur création, en fonction de la façon dont vous les créez.

Pour le modèle d’identité hybride, lorsque les comptes d’utilisateur des services de domaine Active Directory (AD DS) sont synchronisés pour la première fois, ils ne se voit pas attribuer automatiquement un emplacement ou une licence Microsoft 365. **Vous devez configurer chaque compte d’utilisateur avec un emplacement d’utilisateur avant ou avec l’attribution d’une licence.**

Dans les deux cas, vous devez attribuer une licence à des comptes d’utilisateurs afin que vos utilisateurs peuvent accéder aux services Microsoft 365, tels que le courrier électronique et Microsoft Teams.

Vous pouvez attribuer des licences aux comptes d’utilisateurs individuellement ou automatiquement par le biais de l’appartenance à un groupe.

Pour attribuer des licences Microsoft 365 à des comptes d’utilisateur individuels, vous pouvez utiliser :

- [Le Centre d’administration Microsoft 365](../admin/manage/assign-licenses-to-users.md)
- [PowerShell](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)
- Centre d’administration Azure AD

## <a name="group-based-licensing"></a>Gestion des licences en fonction des groupes

Vous pouvez configurer des groupes de sécurité dans Azure AD pour attribuer automatiquement des licences d’un ensemble d’abonnements à tous les membres du groupe. C’est ce que l’on appelle la *gestion des licences basée sur les groupes*. Si un compte d’utilisateur est ajouté au groupe ou supprimé de ce dernier, les licences des abonnements du groupe sont automatiquement attribuées au compte d’utilisateur ou supprimées du compte.

Vérifiez que vous disposez de suffisamment de licences pour tous les membres du groupe. Si vous n’avez plus de licences, aucune licence ne sera attribuée aux nouveaux utilisateurs tant que d’autres licences ne seront pas disponibles.

>[!Note]
>Vous ne devez pas configurer la gestion des licences par groupes pour des groupes qui contiennent des comptes B2B Azure.
>

Pour plus d’informations, voir la gestion des licences basée [sur les groupes dans Azure AD.](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)

## <a name="next-steps"></a>Étapes suivantes

Avec l’ensemble approprié de comptes d’utilisateurs qui ont reçu des licences, vous êtes maintenant prêt à :

- [Implémenter la sécurité](../security/defender-365-security/security-roadmap.md)
- [Déployer des logiciels clients, tels que Microsoft 365 Apps](/DeployOffice/deployment-guide-microsoft-365-apps)
- [Configurer la gestion des appareils](device-management-roadmap-microsoft-365.md)
- [Configurer les services et les applications](configure-services-and-applications.md)