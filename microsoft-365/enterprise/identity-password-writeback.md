---
title: 'Étape 9 : simplifier les mises à jour des mots de passe'
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
description: Comprendre et configurer l’écriture différée de mot de passe pour les environnements hybrides.
ms.openlocfilehash: 55da101ca729de804ae76dafbe35a46969af9d8d
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867021"
---
# <a name="step-9-simplify-password-updates"></a>Étape 9 : simplifier les mises à jour des mots de passe

*Cette étape est facultative pour les environnements hybrides et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

À cette étape, vous allez autoriser les utilisateurs à réinitialiser leur mot de passe via Azure Active Directory (AD). Ils seront ensuite copiés sur votre instance Windows Server Active Directory (AD) locale. Ce processus est appelé écriture différée de mot de passe. Avec l’écriture différée de mot de passe, les utilisateurs n’ont pas besoin de mettre à jour leur mot de passe localement via Windows Server AD où les comptes d’utilisateurs et leurs attributs sont stockés. Cette étape est utile aux utilisateurs itinérants ou distants qui ne disposent pas d’une connexion d’accès à distance au réseau local.

L’écriture différée de mot de passe est requise pour exploiter entièrement les fonctionnalités de la protection des identités, comme obliger les utilisateurs à modifier leur mot de passe en local lorsqu’un risque élevé de compromission de compte a été détecté.

Pour obtenir plus d’informations et les instructions de configuration, consultez l’article [Azure AD SSPR avec l’écriture différée de mot de passe](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>Procédez à la mise à niveau vers la dernière version d’Azure AD Connect pour vous assurer la meilleure expérience possible et les nouvelles fonctionnalités dès leur diffusion. Pour obtenir plus d’informations, consultez l’article [Installation personnalisée d’Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-pw-writeback) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step10.png)| [Simplifier la connexion de l’utilisateur](identity-single-sign-on.md) |

