---
title: Gérer la Microsoft 365 d’identité
ms.author: kvice
author: kelleyvice-msft
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
description: Découvrez comment utiliser les fonctionnalités Microsoft 365 gouvernance des identités.
ms.openlocfilehash: 9b353a83b79c2b66ca224914a7d33a4854919d4e
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58356671"
---
# <a name="manage-microsoft-365-identity-governance"></a>Gérer la Microsoft 365 d’identité

La gouvernance des identités s’intéresse à la protection, la surveillance et l’audit de l’accès aux ressources critiques, tout en assurant la productivité des employés. Par exemple, avec la gouvernance des identités, vous pouvez vous assurer que les utilisateurs appropriés disposent de l’accès approprié aux ressources adéquates et déterminer si cet accès change au fil du temps.

Pour plus d’informations, consultez cette vue d’ensemble de la gouvernance des [identités pour Azure Active Directory (Azure AD).](/azure/active-directory/governance/identity-governance-overview)

## <a name="set-up-azure-ad-access-reviews"></a>Configurer les révisions d’accès Azure AD

Les révisions d’accès Azure AD vous permettent de passer en revue l’accès d’un utilisateur pour vous assurer que seules les bonnes personnes ont un accès continu. Par exemple :

- Lorsqu’un nouvel employé rejoint votre organisation, vous devez vous assurer qu’il dispose d’un accès approprié pour être productif.
- Au fur et à mesure que cet employé passe d’une équipe, d’un emplacement ou d’un service à un autre, vous devez vous assurer que son accès aux équipes, emplacements ou services précédents est supprimé si nécessaire.
- Lorsque cet employé ou un invité quitte votre organisation, vous devez vous assurer qu’il a été supprimé.

Ceci est particulièrement important si votre organisation fait l’objet d’audits de sécurité pour déterminer si les comptes d’utilisateurs ont un niveau d’accès trop important, ce qui peut entraîner des amendes en cas de violation des réglementations régionales ou industrielles.

Pour plus d’informations, voir la [vue d’ensemble des révisions d’accès.](/azure/active-directory/governance/access-reviews-overview)

Pour configurer différents types de révisions d’accès, consultez les articles suivants :

- [Groupes et applications](/azure/active-directory/governance/create-access-review)
- [Rôles Azure AD](/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Rôles de ressources Azure](/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

## <a name="set-up-azure-ad-entitlement-management"></a>Configurer la gestion des droits Azure AD

La gestion des droits Azure AD Wiht vous permet de gérer le cycle de vie des identités et des accès à grande échelle en automatisant les flux de travail de demande d’accès, les affectations d’accès, les avis et l’expiration.

Vos employés ont besoin d’accéder à différents groupes, applications et sites pour effectuer leur travail. La gestion de cet accès peut être difficile car les exigences changent, de nouvelles applications sont ajoutées ou les utilisateurs ont besoin de droits d’accès supplémentaires. Lorsque vous collaborez avec d’autres organisations, vous ne savez peut-être pas qui dans l’autre organisation a besoin d’accéder aux ressources de votre organisation, et les utilisateurs externes ne connaissent pas les applications, les groupes ou les sites que votre organisation utilise.

La gestion des droits Azure AD peut vous aider à gérer plus efficacement l’accès aux groupes, applications et sites SharePoint pour les utilisateurs internes et externes.
 
Pour plus d’informations, voir la [vue d’ensemble de la gestion des droits Azure AD.](/azure/active-directory/governance/entitlement-management-overview)