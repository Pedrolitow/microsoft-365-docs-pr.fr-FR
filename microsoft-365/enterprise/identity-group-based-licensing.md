---
title: 'Étape 12 : Configurer la gestion des licences automatique'
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
description: Comprenez et configurez la gestion des licences par groupes pour des groupes Azure AD.
ms.openlocfilehash: 82e4192f2ef9ba3d1d5ed7bd99a8cf603d7d4cc9
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866821"
---
# <a name="step-12-set-up-automatic-licensing"></a>Étape 12 : Configurer la gestion des licences automatique

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

Dans cette étape, vous allez configurer des groupes de sécurité dans Azure AD pour attribuer automatiquement des licences d’un jeu d’abonnements à tous les membres du groupe. Il s’agit de la *gestion des licences par groupes*. Si un compte d’utilisateur est ajouté ou supprimé du groupe, les licences pour les abonnements du groupe sont automatiquement attribuées ou supprimées du compte d’utilisateur.

Pour Microsoft 365 Entreprise, vous allez configurer des groupes de sécurité Azure AD pour affecter ces deux licences :

- Office 365 Entreprise E3 ou E5
- Enterprise Mobility + Security (EMS) E3 ou E5

Utilisez les groupes identifiés à l’Étape 2 pour rechercher les groupes qui contiennent une liste de comptes où tous les utilisateurs de ce groupe doivent avoir des licences Office 365 et EMS. Vérifiez que vous avez suffisamment de licences pour tous les membres du groupe. Si vous n’avez plus de licences, aucune licence ne sera attribuée aux nouveaux utilisateurs tant que d’autres licences ne sont pas disponibles.

>[!Note]
>Vous ne devez pas configurer la *gestion des licences par groupes* pour des groupes qui contiennent des comptes B2B Azure.
>

Consultez des informations supplémentaires dans la rubrique [Principes de base des licences basées sur les groupes dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal).

Consultez les [étapes pour configurer la gestion des licences par groupes pour un groupe de sécurité Azure](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-group-assignment-azure-portal).

Les résultats de cette étape sont les suivants :

- Vous avez identifié les groupes de sécurité qui sont adaptés à la gestion des licences par groupes.
- Vous avez configuré ces groupes pour la gestion des licences par groupes.

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : Automatiser les licences et l’appartenance au groupe](automate-licenses-group-membership-microsoft-365-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-group-license) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step13.png)| [Surveillez l’activité de connexion et du client](identity-azure-ad-access-usage-reporting.md) |

