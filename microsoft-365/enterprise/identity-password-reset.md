---
title: 'Étape 5 : Simplifier l’accès pour les utilisateurs'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et configurez la réinitialisation du mot de passe libre-service (SSPR) pour Azure AD.
ms.openlocfilehash: 98118a5891ea8224843faa638b52a421d96e8a0b
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32287054"
---
# <a name="step-5-simplify-access-for-users"></a>Étape 5 : Simplifier l’accès pour les utilisateurs

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)


<a name="identity-pw-writeback"></a>
## <a name="simplify-password-updates"></a>Simplifiez les mises à jour du mot de passe

*Cette étape est facultative pour les environnements hybrides et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans cette section, vous devez autoriser les utilisateurs à réinitialiser leur mot de passe via Azure Active Directory (Azure AD), qui est ensuite répliqué sur votre Active Directory Domain Services (AD DS)local. Ce processus est appelé écriture différée de mot de passe. Avec l’écriture différée de mot de passe, les utilisateurs n’ont pas besoin de mettre à jour leur mot de passe via la version locale Active Directory Domain Services (AD DS) où sont stockés les comptes d’utilisateurs et leurs attributs. C’est utile pour les utilisateurs itinérants ou distants qui ne possèdent pas de connexion d’accès à distance au réseau local.

L’écriture différée de mot de passe est requise pour exploiter entièrement les fonctionnalités de la protection des identités, comme obliger les utilisateurs à modifier leur mot de passe en local lorsqu’un risque élevé de compromission de compte a été détecté.

Pour obtenir plus d’informations et les instructions de configuration, consultez l’article [Azure AD SSPR avec l’écriture différée de mot de passe](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>Procédez à la mise à niveau vers la dernière version d’Azure AD Connect pour vous assurer la meilleure expérience possible et les nouvelles fonctionnalités dès leur diffusion. Pour obtenir plus d’informations, consultez l’article [Installation personnalisée d’Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : Écriture différée de mot de passe](password-writeback-m365-ent-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-pw-writeback) pour cette étape.

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

Dans cette section, vous devrez configurer Azure Active Directory Seamless Single Sign-On (Azure AD Seamless SSO) pour autoriser vos utilisateurs à se connecter aux services qui utilisent des comptes d’utilisateurs Azure AD sans taper leur mot de passe, ni dans de nombreux cas, leur nom d’utilisateur. Cela donne à vos utilisateurs un accès facile aux applications basées sur le cloud, telles qu’Office 365, sans nécessiter des composants supplémentaires en local, tels que des serveurs de fédération d’identité.

Vous allez configurer l’authentification unique transparente d’Azure AD avec l’outil Azure AD Connect.

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

Lorsqu’un utilisateur tente de se connecter à partir d’un appareil, il voit une page ressemblant à l’exemple de page de connexion à Office 365 suivant *avant personnalisation*.

![Exemple de page de connexion à Office 365 avant personnalisation](./media/identity-customize-office-365-sign-in/id-step01-sign-in-before.png)

Et voici ce que le même utilisateur de Contoso Corporation verrait *après personnalisation*.

![Exemple de page de connexion à Office 365 après personnalisation](./media/identity-customize-office-365-sign-in/id-step01-sign-in-after.png)

Pour plus d’informations, reportez-vous à la rubrique [Ajouter l’identité de votre entreprise à la page de connexion d’Office 365](https://docs.microsoft.com/office365/admin/setup/customize-sign-in-page).

Pour des instructions de configuration, reportez-vous à la rubrique relative à l’[ajout de l’identité de votre entreprise à vos pages de connexion et de panneau d’accès](http://aka.ms/aadpaddbranding).

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-custom-sign-in) pour cette étape.


## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step6.png)| [Utiliser des groupes pour faciliter la gestion](identity-self-service-group-management.md) |


