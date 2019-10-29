---
title: 'Étape 2 : Sécuriser vos mots de passe'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/20/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Vous devez rendre vos mots de passe forts et gérables au sein de votre organisation.
ms.openlocfilehash: 375f4a678e85dccb544ffaf56f648e98609841d9
ms.sourcegitcommit: 2aeafb631aaabc53eea0a8029711eb891e48d249
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "37746510"
---
# <a name="step-2-secure-your-passwords"></a>Étape 2 : Sécuriser vos mots de passe

![Phase 2 - Identité](./media/deploy-foundation-infrastructure/identity_icon-small.png)

<a name="identity-password-prot"></a>
## <a name="prevent-bad-passwords"></a>Éviter les mots de passe incorrects

*Cette étape facultative s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Tous vos utilisateurs doivent utiliser le [guide des mots de passe Microsoft](https://www.microsoft.com/research/publication/password-guidance/) pour créer leurs mots de passe de compte d'utilisateur.

Pour empêcher les utilisateurs de créer un mot de passe facile à déterminer, optez pour la protection par mot de passe Azure AD qui utilise une liste globale de mots de passe interdits et une liste personnalisée facultative de mots de passe interdits que vous spécifiez. Par exemple, vous pouvez spécifier des termes propres à votre organisation, tels que :

- Noms de marques
- Noms de produits
- Emplacements (par exemple, le siège social de l’entreprise)
- Termes internes spécifiques à l’entreprise
- Abréviations dotées d’une signification spécifique à l’entreprise.

Vous pouvez interdire les mots de passe incorrects [dans le cloud](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad) et localement pour [Active Directory Domain Services (AD DS)](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad-on-premises).

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-password-prot) de cette section.

<a name="identity-pw-reset"></a>
## <a name="simplify-password-resets"></a>Simplifiez les réinitialisations du mot de passe

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans cette section, vous autoriserez la réinitialisation de mot de passe en libre-service (SSPR) d’Azure AD pour permettre aux utilisateurs de réinitialiser ou de déverrouiller leurs mots de passe ou leurs comptes. Le système inclut des rapports détaillés de suivi d’accès au système, ainsi que des notifications pour vous prévenir de toute utilisation malveillante ou de tout abus. Vous devez activer l’écriture différée de mot de passe avant de pouvoir déployer la réinitialisation de mot de passe.

Reportez-vous aux [Instructions pour activer la réinitialisation de mot de passe](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-deployment).

|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : Réinitialisation de mot de passe](password-reset-m365-ent-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-pw-reset) pour cette étape.


<a name="identity-sso"></a>
## <a name="simplify-user-sign-in"></a>Simplifiez la connexion utilisateur

*Cette étape est facultative pour les environnements hybrides et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans cette section, vous devrez configurer Azure Active Directory Seamless Single Sign-On (Azure AD Seamless SSO), qui fonctionne avec la Synchronisation de hachage de mot de passe (PHS) et l'Authentification directe (PTA), pour autoriser vos utilisateurs à se connecter aux services qui utilisent des comptes d’utilisateurs Azure AD sans avoir à taper leur mot de passe, et dans de nombreux cas, leur nom d’utilisateur. Cela donne à vos utilisateurs un accès facile aux applications basées sur le cloud, telles qu’Office 365, sans nécessiter des composants supplémentaires en local, tels que des serveurs de fédération d’identité.

Vous configurez l’authentification unique transparente Azure AD avec l’outil Azure AD Connect.

Reportez-vous aux [instructions pour configurer l’authentification unique transparente d’Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start).

|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test : authentification unique transparente Azure AD](single-sign-on-m365-ent-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-sso) pour cette étape.


<a name="identity-custom-sign-in"></a>
## <a name="customize-the-office-365-sign-in-page"></a>Personnaliser la page de connexion à Office 365

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans cette section, vous allez permettre aux utilisateurs de reconnaître la page de connexion de votre organisation en ajoutant le nom de votre entreprise, votre logo et d’autres éléments reconnaissables. 

Microsoft 365 Entreprise vous permet de personnaliser l’aspect des pages de connexion et du panneau d’accès pour y inclure votre logo d’entreprise, des modèles de couleurs et des informations personnalisées sur l’utilisateur. 

Pour plus d’informations, reportez-vous à la rubrique [Ajouter l’identité de votre entreprise à la page de connexion d’Office 365](https://docs.microsoft.com/office365/admin/setup/customize-sign-in-page).

Pour des instructions de configuration, reportez-vous à la rubrique relative à l’[ajout de l’identité de votre entreprise à vos pages de connexion et de panneau d’accès](https://aka.ms/aadpaddbranding).

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-custom-sign-in) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![Étape 3](./media/stepnumbers/Step3.png)| [Sécuriser et gérer les connexions de vos utilisateurs](identity-secure-user-sign-ins.md) |
