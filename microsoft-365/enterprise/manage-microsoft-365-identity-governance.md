---
title: Gérer Microsoft 365 Identity Governance
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Découvrez comment utiliser les fonctionnalités de gouvernance d’identités Microsoft 365.
ms.openlocfilehash: d5bcafb5b452e693bf3ff706c436a9986eeeae76
ms.sourcegitcommit: 04c4252457d9b976d31f53e0ba404e8f5b80d527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "48328515"
---
# <a name="manage-microsoft-365-identity-governance"></a>Gérer Microsoft 365 Identity Governance

La gouvernance des identités s’intéresse à la protection, la surveillance et l’audit de l’accès aux ressources critiques, tout en assurant la productivité des employés. Par exemple, avec la gouvernance des identités, vous pouvez vous assurer que les utilisateurs appropriés disposent de l’accès approprié aux ressources adéquates et déterminer si cet accès change au fil du temps.

Pour plus d’informations, consultez cette [vue d’ensemble de la gouvernance des identités pour Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/governance/identity-governance-overview).

## <a name="set-up-azure-ad-access-reviews"></a>Configurer les révisions d’accès Azure AD

Les révisions Azure AD Access vous permettent de vérifier l’accès d’un utilisateur afin de s’assurer que seules les personnes appropriées disposent d’un accès continu. Par exemple :

- Lorsqu’un nouvel employé rejoint votre organisation, vous devez vous assurer qu’il dispose d’un accès approprié pour être productif.
- Au fur et à mesure que cet employé passe d’une équipe, d’un emplacement ou d’un service à un autre, vous devez vous assurer que son accès aux équipes, emplacements ou services précédents est supprimé si nécessaire.
- Lorsque cet employé ou un invité quitte votre organisation, vous devez vous assurer qu’il a été supprimé.

Ceci est particulièrement important si votre organisation fait l’objet d’audits de sécurité pour déterminer si les comptes d’utilisateurs ont un niveau d’accès trop important, ce qui peut entraîner des amendes en cas de violation des réglementations régionales ou industrielles.

Pour plus d’informations, consultez la rubrique [vue d’ensemble des révisions Access](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overview).

Azure AD Privileged Identity Management (PIM) offre des contrôles supplémentaires conçus pour sécuriser les droits d’accès aux ressources dans Azure AD, Azure et d’autres services de cloud computing Microsoft. Azure AD PIM fournit un ensemble complet de contrôles de gouvernance pour vous aider à sécuriser les ressources de votre entreprise telles que le répertoire, Office 365 et les rôles de ressources Azure. Comme avec d’autres formes d’accès, les organisations peuvent utiliser les révisions d’accès pour configurer une recertification récurrente des accès pour tous les utilisateurs bénéficiant de rôles d’administrateur. Azure AD PIM est disponible uniquement avec la version E5 de Microsoft 365 Entreprise.

Pour configurer différents types de révisions d’accès, consultez les articles suivants :

- [Groupes et applications](https://docs.microsoft.com/azure/active-directory/governance/create-access-review)
- [Rôles Azure AD](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Rôles de ressources Azure](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

## <a name="set-up-azure-ad-entitlement-management"></a>Configurer la gestion des droits Azure AD

Wiht Azure AD admises, vous pouvez gérer le cycle de vie des identités et des accès à l’horizontale en automatisant les flux de travail de demande d’accès, les attributions d’accès, les révisions et l’expiration.

Vos employés ont besoin d’accéder à différents groupes, applications et sites pour effectuer leur travail. La gestion de cet accès peut être complexe, car les exigences changent, que de nouvelles applications sont ajoutées ou que les utilisateurs ont besoin de droits d’accès supplémentaires. Lorsque vous collaborez avec d’autres organisations, vous pouvez ne pas savoir qui a besoin d’accéder aux ressources de votre organisation dans l’autre organisation, et les utilisateurs externes ne sauront pas quelles applications, quels groupes ou quels sites votre organisation utilise.

La gestion des droits Azure AD peut vous aider à gérer plus efficacement l’accès aux groupes, aux applications et aux sites SharePoint pour les utilisateurs internes et externes.
 
Pour plus d’informations, reportez-vous à la rubrique [vue d’ensemble de la gestion des droits Azure ad](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview).
