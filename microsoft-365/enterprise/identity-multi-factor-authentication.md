---
title: 'Étape 5 : Configurer l’authentification multifacteur'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et configurez l’authentification multifacteur pour les comptes d’utilisateur.
ms.openlocfilehash: a54eb047c94430a2b3f61d06500c929e400e3d82
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867323"
---
# <a name="step-5-set-up-multi-factor-authentication"></a>Étape 5 : Configurer l’authentification multifacteur

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

Lors de cette étape, vous allez configurer l’authentification multifacteur (MFA) pour ajouter une deuxième couche de sécurité aux connexions et transactions de l’utilisateur. L’authentification multifacteur nécessite une méthode de vérification supplémentaire une fois que les utilisateurs ont entré correctement leur mot de passe. Sans l’authentification multifacteur, le mot de passe est la seule méthode de vérification. Le problème avec les mots de passe est qu’un grand nombre d’entre eux peuvent facilement être devinés par une personne malveillante ou partagés involontairement avec des parties non approuvées.

Avec l’authentification multifacteur, la deuxième couche de sécurité peut être :

- un appareil personnel et approuvé qui n’est pas facilement usurpé ou dupliqué (un smartphone, par exemple) ;
- un attribut biométrique (une empreinte numérique, par exemple).

Vous allez activer l’authentification multifacteur et configurer la méthode d’authentification secondaire sur une base de compte par utilisateur. Informez bien les utilisateurs que l’authentification multifacteur est en cours d’activation pour qu’ils comprennent les exigences telles que l’utilisation obligatoire d’un smartphone pour la connexion et puissent se connecter correctement.

Pour plus d’informations, reportez-vous à [Planifier l’authentification multifacteur pour les déploiements Office 365](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba).

Pour configurer l’authentification multifacteur, reportez-vous à [Configurer l’authentification multifacteur pour les utilisateurs d’Office 365](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).

Vous pouvez exiger une authentification multifacteur avec des stratégies d’accès conditionnel. Par exemple, vous pouvez configurer une stratégie qui exigeait l’authentification multifacteur lorsque l’authentification est déterminée comme étant à risque élevé ou moyen. Pour plus d’informations, reportez-vous à [Stratégies communes pour les identités et l’accès aux appareils](identity-access-policies.md#require-mfa-based-on-sign-in-risk).

>[!Note]
>Dans certaines applications, comme Microsoft Office 2010 ou antérieures et Apple Mail, vous ne pouvez pas utiliser l’authentification multifacteur. Pour utiliser ces applications, vous devez utiliser des « mots de passe d’application » à la place de votre mot de passe habituel. Le mot de passe d’application permet à l’application de contourner l’authentification multifacteur et de continuer à fonctionner. Pour en savoir plus sur les mots de passe d’application, reportez-vous à [Créer un mot de passe d’application pour Office 365](https://support.office.com/article/Create-an-app-password-for-Office-365-3e7c860f-bda4-4441-a618-b53953ee1183).
>

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : authentification multifacteur](multi-factor-authentication-microsoft-365-test-environment.md) |
|||

Comme point de vérification temporaire, vous pouvez voir les [critères de sortie](identity-exit-criteria.md#crit-identity-mfa) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step6.png)| [Se protéger contre la compromission de confidentialité](identity-azure-ad-identity-protection.md) |

