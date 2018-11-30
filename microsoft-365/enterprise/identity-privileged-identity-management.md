---
title: 'Étape 3 : Configurer des administrateurs généraux à la demande'
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
description: Comprenez et configurez Azure AD Privileged Identity Management.
ms.openlocfilehash: 659beff3c31d17afa03d3ecf754c581f3ca2e230
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867030"
---
# <a name="step-3-set-up-on-demand-global-administrators"></a>Étape 3 : Configurer des administrateurs généraux à la demande

*Cette étape est facultative et s’applique uniquement à la version E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

Dans cette étape, vous configurerez Azure AD Privileged Identity Management (PIM) afin de réduire la durée pendant laquelle vos comptes d’administrateur général sont vulnérables aux attaques d’utilisateurs malveillants. PIM fournit l’affectation du rôle Administrateur général à la demande, juste-à-temps, en cas de besoin.  

Au lieu que vos comptes d’administrateur général soient un administrateur permanent, ils deviennent des administrateurs éligibles. Le rôle Administrateur général est inactif tant que personne n’en a besoin. Vous effectuerez ensuite un processus d’activation pour ajouter le rôle Administrateur général au compte d’administrateur général pour une durée spécifique. À l’expiration du délai, PIM supprime le rôle Administrateur général du compte d’administrateur général.

PIM est disponible avec Azure Active Directory Premium P2, qui est inclus avec Microsoft 365 Entreprise E5. Vous pouvez également acheter des licences Azure Active Directory Premium P2 individuelles pour vos comptes d’administrateur général.

Pour activer Azure PIM pour votre client Azure AD et vos comptes d’administrateur général, consultez les [étapes de configuration de PIM](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).

Reportez-vous à la rubrique [Sécurisation de l’accès privilégié pour les déploiements hybrides et cloud dans Azure AD](https://docs.microsoft.com/azure/active-directory/admin-roles-best-practices) pour développer une feuille de route détaillée qui sécurise l’accès privilégié contre les cyber-attaquants.

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-pim) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step4.png)| [Simplifier la réinitialisation de mot de passe](identity-password-reset.md) |

