---
title: 'Étape 8 : surveiller l’état de la synchronisation'
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
description: Comprenez et configurez Azure AD Connect Health.
ms.openlocfilehash: 21cfd88617bccab3f0a2bdb51c0d320cd4568a56
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867261"
---
# <a name="step-8-monitor-synchronization-health"></a>Étape 8 : surveiller l’état de la synchronisation

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

Dans cette étape, vous allez installer un agent Azure AD Connect Health sur chacun de vos serveurs d’identité locaux pour surveiller votre infrastructure d’identités et les services de synchronisation fournis par Azure AD Connect. Les informations de surveillance sont mises à disposition dans un portail Azure AD Connect Health où vous pouvez afficher des alertes, l’analyseur de performances, l’analyse de l’utilisation et d’autres informations.

![Composants d’Azure AD Connect Health](./media/identity-azure-ad-connect-health/identity-azure-ad-connect-health.png)

La décision de conception clé concernant l’utilisation d’Azure AD Connect Health est basée sur la manière dont vous utilisez Azure AD Connect :

- Si vous utilisez de nouveau l’option d’**authentification gérée**, commencez avec la rubrique relative à l’[utilisation d’Azure AD Connect Health avec la synchronisation](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) pour comprendre et configurer Azure AD Connect Health.
- Si vous synchronisez uniquement les noms des comptes et des groupes à l’aide de l’**authentification fédérée** avec Active Directory Federation Services (AD FS), commencez avec la rubrique [Utilisation d’Azure AD Connect Health avec AD FS](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) pour comprendre et configurer Azure AD Connect Health.

Lorsque vous terminez cette étape, vous avez :

- l’agent Azure AD Connect Health installé sur vos serveurs de fournisseur d’identité local ;
- le portail Azure AD Connect Health qui affiche l’état actuel de vos activités d’infrastructure et de synchronisation locales avec le client Azure AD pour vos abonnements Office 365 et EMS.

Comme point de vérification intermédiaire, vous pouvez consultez les [critères de sortie](identity-exit-criteria.md#crit-identity-sync-health) pour cette étape.


## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step9.png)| [Simplifiez les mises à jour du mot de passe](identity-password-writeback.md) |

