---
title: 'Étape 4 : configurer l’authentification d’utilisateur sécurisée'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et configurez l’authentification multifacteur pour les comptes d’utilisateur.
ms.openlocfilehash: 73e884802329765fd6a89cfb7d0e04116c17968c
ms.sourcegitcommit: 66bb5af851947078872a4d31d3246e69f7dd42bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34072084"
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

Vous allez activer l’authentification multifacteur et configurer la méthode d’authentification secondaire sur une base de compte par utilisateur. Informez bien les utilisateurs que l’authentification multifacteur est en cours d’activation pour qu’ils comprennent les exigences telles que l’utilisation obligatoire d’un smartphone pour la connexion et puissent se connecter correctement.

Pour plus d’informations, voir [Planifier l’authentification multifacteur](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted).

>[!Note]
>Dans certaines applications, comme Microsoft Office 2010 ou antérieures et Apple Mail, vous ne pouvez pas utiliser l’authentification multifacteur. Pour utiliser ces applications, vous devez utiliser des « mots de passe d’application » à la place de votre mot de passe habituel. Le mot de passe d’application permet à l’application de contourner l’authentification multifacteur et de continuer à fonctionner. Pour en savoir plus sur les mots de passe d’application, reportez-vous à [Créer un mot de passe d’application pour Office 365](https://support.office.com/article/Create-an-app-password-for-Office-365-3e7c860f-bda4-4441-a618-b53953ee1183).
>

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : authentification multifacteur](multi-factor-authentication-microsoft-365-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-mfa) pour cette section.



<a name="identity-ident-prot"></a>
## <a name="protect-against-credential-compromise"></a>Protégez-vous contre la compromission des informations d’identification

*Cette étape est facultative et s’applique uniquement à la version E5 de Microsoft 365 Entreprise*

Cette section explique comment configurer des stratégies de protection contre la compromission d’informations d’identification consistant pour un attaquant à déterminer le nom de compte et le mot de passe d’un utilisateur afin d’accéder aux services et données cloud d’une organisation. Azure AD Identity Protection fournit un certain nombre de moyens pour empêcher un attaquant de se déplacer latéralement dans vos comptes et groupes, puis vers vos données les plus précieuses.

Azure AD Identity Protection vous permet de :

|||
|:---------|:---------|
|déterminer et résoudre les vulnérabilités potentielles dans les identités de votre organisation ;|Azure AD utilise l’apprentissage automatique pour détecter les anomalies et les activités douteuses, telles que les connexions et les activités post-connexion. À l’aide de ces données, Identity Protection génère des rapports et les alertes qui vous aident à évaluer les problèmes et à prendre des mesures.|
|Détecter des actions douteuses qui sont liées aux identités de votre organisation et y répondre automatiquement|Vous pouvez configurer des stratégies de risque qui répondent automatiquement aux problèmes détectés lorsqu’un niveau de risque spécifié a été atteint. Ces stratégies, en plus des autres contrôles d’accès conditionnel fournis par Azure Active Directory et Enterprise Mobility + Security (EMS) peuvent automatiquement bloquer l’accès ou prendre des actions correctives, comme réinitialiser les mots de passe et demander l’authentification multifacteur pour les connexions suivantes.|
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

