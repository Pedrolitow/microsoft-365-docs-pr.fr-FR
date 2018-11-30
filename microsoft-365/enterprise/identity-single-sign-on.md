---
title: 'Étape 10 : Simplifier la connexion de l’utilisateur'
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
description: Comprenez et configurez l’authentification unique transparente d’Azure AD.
ms.openlocfilehash: 9d18cb559d3a4a9ee401e0f94fb53bc6360d88c8
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867382"
---
# <a name="step-10-simplify-user-sign-in"></a>Étape 10 : Simplifier la connexion de l’utilisateur

*Cette étape est facultative pour les environnements hybrides et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

Dans cette étape, vous devrez configurer l’authentification unique transparente d’Azure Active Directory pour autoriser vos utilisateurs à se connecter aux services qui utilisent des comptes d’utilisateur Azure AD sans devoir taper ni leurs mots de passe, ni leurs noms d’utilisateur (dans de nombreux cas). Cela permet à vos utilisateurs d’accéder plus facilement aux applications informatiques comme Office 365, sans avoir besoin de composants locaux supplémentaires, tels que des serveurs de fédération des identités.

Vous allez configurer l’authentification unique transparente d’Azure AD avec l’outil Azure AD Connect.

Reportez-vous aux [instructions pour configurer l’authentification unique transparente d’Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start).

|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test : authentification unique transparente Azure AD](single-sign-on-m365-ent-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consultez les [critères de sortie](identity-exit-criteria.md#crit-identity-sso) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step11.png)| [Personnaliser la page de connexion à Office 365](identity-customize-office-365-sign-in.md) |

