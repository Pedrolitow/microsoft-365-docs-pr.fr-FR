---
title: Attribuer des licences Microsoft 365 à des comptes d’utilisateurs
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- scotvorg
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Décrit comment attribuer des licences Microsoft 365 à des comptes d’utilisateur, individuellement ou en fonction de l’appartenance au groupe.
ms.openlocfilehash: f9b508e4299e84752238a5f2f0290a4ad223c17f
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68194882"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>Attribuer des licences Microsoft 365 à des comptes d’utilisateurs

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Pour le modèle d’identité cloud uniquement, vous pouvez attribuer des licences Microsoft 365 à des comptes d’utilisateur au fur et à mesure de leur création, selon la façon dont vous les créez.

Pour le modèle d’identité hybride, lorsque les comptes d’utilisateur services de domaine Active Directory (AD DS) sont synchronisés pour la première fois, ils ne reçoivent pas automatiquement un emplacement ou une licence Microsoft 365. **Vous devez configurer chaque compte d’utilisateur avec un emplacement utilisateur avant ou avec l’attribution d’une licence.**

Dans les deux cas, vous devez attribuer une licence à des comptes d’utilisateur afin que vos utilisateurs puissent accéder aux services Microsoft 365, tels que la messagerie électronique et Microsoft Teams.

Vous pouvez attribuer des licences à des comptes d’utilisateur individuellement ou automatiquement par le biais de l’appartenance à un groupe.

Pour affecter des licences Microsoft 365 à des comptes d’utilisateur individuels, vous pouvez utiliser :

- [Le Centre d'administration Microsoft 365](../admin/manage/assign-licenses-to-users.md)
- [PowerShell](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)
- Centre d’administration Azure AD

## <a name="group-based-licensing"></a>Gestion des licences en fonction des groupes

Vous pouvez configurer des groupes de sécurité dans Azure AD pour attribuer automatiquement des licences à partir d’un ensemble d’abonnements à tous les membres du groupe. C’est ce que l’on appelle la *gestion des licences basée sur les groupes*. Si un compte d’utilisateur est ajouté au groupe ou supprimé de ce dernier, les licences des abonnements du groupe sont automatiquement attribuées au compte d’utilisateur ou supprimées du compte.

Vérifiez que vous disposez de suffisamment de licences pour tous les membres du groupe. Si vous n’avez plus de licences, aucune licence ne sera attribuée aux nouveaux utilisateurs tant que d’autres licences ne seront pas disponibles.

>[!Note]
>Vous ne devez pas configurer la gestion des licences par groupes pour des groupes qui contiennent des comptes B2B Azure.
>

Pour plus d’informations, consultez [licences basées sur des groupes dans Azure AD](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Prochaines étapes

Avec l’ensemble approprié de comptes d’utilisateur auxquels des licences ont été attribuées, vous êtes maintenant prêt à :

- [Implémenter la sécurité](/microsoft-365/security/office-365-security/overview)
- [Déployer des logiciels clients, tels que Microsoft 365 Apps](/DeployOffice/deployment-guide-microsoft-365-apps)
- [Configurer la gestion des appareils](device-management-roadmap-microsoft-365.md)
- [Configurer des services et des applications](configure-services-and-applications.md)
