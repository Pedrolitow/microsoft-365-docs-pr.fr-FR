---
title: 'Étape 4 : configurer l’authentification d’utilisateur sécurisée'
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
description: Comprenez et configurez l’authentification multifacteur pour les comptes d’utilisateur.
ms.openlocfilehash: 2a4a0926a08ae8279523219a2d7a2386ea0c6742
ms.sourcegitcommit: 91ff1d4339f0f043c2b43997d87d84677c79e279
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "36981845"
---
# <a name="step-4-configure-secure-user-authentication"></a>Étape 4 : configurer l’authentification d’utilisateur sécurisée

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

<a name="identity-mfa"></a>
## <a name="set-up-multi-factor-authentication"></a>Configurer l’authentification multifacteur

*Cette étape facultative s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Lors de cette étape, vous allez configurer l’authentification multifacteur (MFA) pour ajouter une deuxième couche de sécurité aux connexions et transactions de l’utilisateur. L’authentification multifacteur nécessite une méthode de vérification supplémentaire une fois que les utilisateurs ont entré correctement leur mot de passe. Sans l’authentification multifacteur, le mot de passe est la seule méthode de vérification. Le problème avec les mots de passe est qu’un grand nombre d’entre eux peuvent facilement être devinés par une personne malveillante ou partagés involontairement avec des parties non approuvées.

Avec l’authentification multifacteur, la deuxième couche de sécurité peut être :

- un appareil personnel et approuvé qui n’est pas facilement usurpé ou dupliqué (un smartphone, par exemple) ;
- un attribut biométrique (une empreinte numérique, par exemple).

Vous allez activer l’authentification multifacteur et configurer la méthode d’authentification secondaire avec les [stratégies d’accès conditionnel](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted#enable-multi-factor-authentication-with-conditional-access), qui vous permettent d’utiliser les groupes Azure Active Directory (Azure AD) pour déployer l’authentification multifacteur vers des ensembles d’utilisateurs spécifiés, tels que des utilisateurs pilotes, régions géographiques ou services. Informez bien vos utilisateurs que l’authentification multifacteur est en cours d’activation pour qu’ils comprennent les exigences telles que l’utilisation obligatoire d’un smartphone pour la connexion et puissent se connecter correctement. 

Pour plus d’informations, voir [Planifier l’authentification multifacteur](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted).

>[!Note]
>Dans certaines applications, comme Microsoft Office 2010 ou antérieures et Apple Mail, vous ne pouvez pas utiliser l’authentification multifacteur. Pour utiliser ces applications, vous devez utiliser des « mots de passe d’application » à la place de votre mot de passe habituel. Le mot de passe d’application permet à l’application de contourner l’authentification multifacteur et de continuer à fonctionner. Pour en savoir plus sur les mots de passe d’application, reportez-vous à [Créer un mot de passe d’application pour Office 365](https://support.office.com/article/Create-an-app-password-for-Office-365-3e7c860f-bda4-4441-a618-b53953ee1183).
>

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : authentification multifacteur](multi-factor-authentication-microsoft-365-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-mfa) pour cette étape.

<a name="identity-password-prot"></a>
## <a name="prevent-bad-passwords"></a>Éviter les mots de passe incorrects

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Pour empêcher les utilisateurs de créer un mot de passe facile à déterminer, optez pour la protection par mot de passe Azure AD qui utilise une liste globale de mots de passe interdits et une liste personnalisée facultative de mots de passe que vous spécifiez. Par exemple, vous pouvez spécifier des termes propres à votre organisation, tels que «

- Noms de marques
- Noms de produits
- Emplacements (par exemple, le siège social de l’entreprise)
- Termes internes spécifiques à l’entreprise
- Abréviations dotées d’une signification spécifique à l’entreprise.

Vous pouvez interdire les mots de passe incorrects [dans le cloud](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad) et localement pour [Active Directory Domain Services (AD DS)](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad-on-premises).

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-password-prot) pour cette étape.

<a name="identity-ident-prot"></a>
## <a name="protect-against-credential-compromise"></a>Protégez-vous contre la compromission des informations d’identification

*Cette étape est facultative et s’applique uniquement à la version E5 de Microsoft 365 Entreprise*

Cette section explique comment configurer des stratégies de protection contre la compromission d’informations d’identification consistant pour un attaquant à déterminer le nom de compte et le mot de passe d’un utilisateur afin d’accéder aux services et données cloud d’une organisation. Azure AD Identity Protection fournit un certain nombre de moyens pour empêcher un attaquant de se déplacer latéralement dans vos comptes et groupes, puis vers vos données les plus précieuses.

Azure AD Identity Protection vous permet de :

|||
|:---------|:---------|
|déterminer et résoudre les vulnérabilités potentielles dans les identités de votre organisation ;|Azure AD utilise le Machine Learning pour détecter les anomalies et les activités suspectes, telles que les connexions et les activités post-connexion. Grâce à ces données, Azure AD Identity Protection génère des rapports et des alertes qui vous permettent d’évaluer les problèmes et de prendre des mesures.|
|Détecter des actions douteuses qui sont liées aux identités de votre organisation et y répondre automatiquement|Vous pouvez configurer des stratégies qui répondent automatiquement aux problèmes détectés lorsqu’un niveau de risque spécifié est atteint. Outre les autres contrôles d’accès conditionnel fournis par Azure AD et Microsoft Intune, ces stratégies peuvent automatiquement bloquer l’accès ou prendre des mesures correctives, qui incluent des réinitialisations de mot de passe et impliquent une authentification multifacteur pour les connexions suivantes.|
|Examiner les incidents suspects et les résoudre avec des actions d’administration|Vous pouvez examiner des événements à risque en utilisant les informations sur l’incident de sécurité. Des flux de travail de base sont disponibles pour effectuer le suivi des enquêtes et lancer des actions de correction, telles que des réinitialisations du mot de passe.|

[Plus d’informations sur Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection).

Reportez-vous à la rubrique des [étapes pour activer Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection-enable).

Les résultats de cette étape sont que vous avez activé Azure AD Identity Protection et que vous l’utilisez pour :

- résoudre les vulnérabilités d’identités potentielles ;
- détecter les tentatives de compromission d’informations d’identification possibles ;
- examiner et résoudre des incidents d’identités suspects en cours.

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test : Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-ident-prot) pour cette section.

## <a name="monitor-tenant-and-sign-in-activity"></a>Surveillez l’activité de connexion et du client

*Cette étape facultative s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans cette étape, vous allez passer en revue les journaux d’audit et l’activité de connexion à l’aide des rapports Azure AD. Deux types de rapports sont disponibles.

Le **rapport d’activité des journaux d’audit** enregistre l’historique de toutes les tâches effectuées dans votre client Azure AD. Ce rapport répond aux questions telles que :

- Qui a ajouté une personne à un groupe d’administration ?
- Quels sont les utilisateurs qui se connectent à une application spécifique ?
- Combien de réinitialisations de mot de passe sont prévues ?

Le **rapport d’activité des connexions** enregistre l’auteur des tâches indiquées par le rapport des journaux d’audit. Ce rapport répond aux questions telles que :

- Pour un utilisateur spécifique à l’étude, quel est son modèle de connexion ?
- Quel est mon volume de connexions par jour, semaine ou mois ?
- Combien de ces tentatives de connexion n’ont pas abouti, et pour quels comptes ?

Pour plus d’informations sur les rapports et la façon d’y accéder, reportez-vous à la rubrique [Création de rapports Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-azure-portal).

Après cette étape, vous connaîtrez ces rapports et saurez comment les utiliser pour obtenir des informations sur les activités et événements Azure AD à des fins de planification et de sécurité.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step5.png)| [Simplifier l’accès pour les utilisateurs](identity-password-reset.md) |

