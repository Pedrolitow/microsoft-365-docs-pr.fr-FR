---
title: 'Étape 7 : Configurer la gouvernance des identités'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/06/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre et configurer la gouvernance des identités pour votre client Azure AD.
ms.openlocfilehash: 1c0eab574e5436dd0c88a0b46d1916281bcf0577
ms.sourcegitcommit: 63e35b846d964dde5919a08c2fe432e749e8eff6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "37047357"
---
# <a name="step-7-configure-identity-governance"></a>Étape 7 : Configurer la gouvernance des identités

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

La gouvernance des identités s’intéresse à la protection, la surveillance et l’audit de l’accès aux ressources critiques, tout en assurant la productivité des employés. Par exemple, avec la gouvernance des identités, vous pouvez vous assurer que les utilisateurs appropriés disposent de l’accès approprié aux ressources adéquates et déterminer si cet accès change au fil du temps.

Pour plus d' informations sur la gouvernance des identités pour Azure Active Directory (Azure AD), consultez [cet article](https://docs.microsoft.com/azure/active-directory/governance/identity-governance-overview).

<a name="identity-access-reviews"></a>
## <a name="set-up-azure-ad-access-reviews"></a>Configurer les révisions d’accès Azure AD

*Cette étape est facultative et s’applique uniquement à la version E5 de Microsoft 365 Entreprise*

Dans cette étape, vous allez configurer les révisions d’accès Azure AD qui vous permettent de passer en revue l’accès d’un utilisateur afin de garantir l’accès permanent aux seules personnes appropriées. Par exemple :

- Lorsqu’un nouvel employé rejoint votre organisation, vous devez vous assurer qu’il dispose d’un accès approprié pour être productif.
- Au fur et à mesure que cet employé passe d’une équipe, d’un emplacement ou d’un service à un autre, vous devez vous assurer que son accès aux équipes, emplacements ou services précédents est supprimé si nécessaire.
- Lorsque cet employé ou un invité quitte votre organisation, vous devez vous assurer qu’il a été supprimé.

Ceci est particulièrement important si votre organisation fait l’objet d’audits de sécurité pour déterminer si les comptes d’utilisateurs ont un niveau d’accès trop important, ce qui peut entraîner des amendes en cas de violation des réglementations régionales ou industrielles.

Consultez [cet article](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overview) pour plus d’informations sur les révisions d’accès Azure AD.

Pour configurer différents types de révisions d’accès, voir les articles suivants :

- [Groupes et applications](https://docs.microsoft.com/azure/active-directory/governance/create-access-review)
- [Rôles Azure AD](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Rôles de ressources Azure](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-access-reviews) pour cette étape.

## <a name="next-step"></a>Étape suivante

[ Identifier les critères de sortie de l’infrastructure](identity-exit-criteria.md)

