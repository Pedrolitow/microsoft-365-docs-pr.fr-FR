---
title: 'Étape 14 : permettre aux utilisateurs de créer et de gérer leurs propres groupes'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/01/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre et configurer la gestion des groupes en libre-service Azure AD.
ms.openlocfilehash: d46e82fd72b8eef896a223229a2cc3d25ae56c76
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867168"
---
# <a name="step-14-allow-users-to-create-and-manage-their-own-groups"></a>Étape 14 : permettre aux utilisateurs de créer et de gérer leurs propres groupes

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

Dans cette étape, vous allez identifier des groupes Azure Active Directory (AD) qui peuvent être gérés par des propriétaires de groupe et non par les administrateurs informatiques. Appelée *gestion des groupes en libre-service*, cette fonctionnalité permet aux propriétaires de groupe non désignés comme administrateurs de créer et de gérer des groupes de sécurité. 

Les utilisateurs peuvent demander à appartenir à un groupe de sécurité. Cette demande est envoyée au propriétaire du groupe, et non à l’administrateur informatique. Ainsi, le contrôle quotidien de l’appartenance au groupe peut être délégué aux propriétaires d’équipes, de projets ou d’entreprises qui comprennent l’usage du groupe pour l’entreprise et peuvent gérer ses membres.

>[!Note]
>La gestion des groupes en libre-service est disponible uniquement pour la sécurité Azure AD et les groupes Office 365. Cette fonction n’est pas disponible pour les groupes à extension messagerie, les listes de distribution ou les groupes ayant été synchronisés à partir de votre instance Windows Server Active Directory (AD) locale.
>

Pour obtenir plus d’informations, consultez les [instructions pour configurer un groupe Azure AD pour la gestion en libre-service](https://docs.microsoft.com/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-self-service-groups) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step15.png)| [Configurer l’appartenance à un groupe dynamique](identity-automatic-group-membership.md) |
