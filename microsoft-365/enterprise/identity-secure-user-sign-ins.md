---
title: 'Étape 3 : Sécuriser et gérer les connexions de vos utilisateurs'
f1.keywords:
- NOCSH
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
description: Vous pouvez sécuriser plus efficacement les connexions des utilisateurs aux appareils Windows et à Microsoft 365.
ms.openlocfilehash: c541f5b74fe3ea6e94b002212f21ec8645e8e87e
ms.sourcegitcommit: 6c8edbc54b193e964cf93aec48c51cb79231f1d9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "42544013"
---
# <a name="step-3-secure-and-manage-your-user-sign-ins"></a>Étape 3 : Sécuriser et gérer les connexions de vos utilisateurs

![Phase 2 - Identité](../media/deploy-foundation-infrastructure/identity_icon-small.png)


<a name="identity-windows-hello"></a>
## <a name="use-windows-hello-for-business"></a>Utiliser Windows Hello Entreprise

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365*

Windows Hello Entreprise dans Windows 10 Entreprise remplace les mots de passe par une authentification à deux facteurs forte lors de la connexion à un appareil Windows. Les deux facteurs sont un nouveau type d’informations d’identification d’utilisateur qui est lié à un appareil et à un code biométrique ou PIN.

Pour plus d’informations, consultez [Vue d’ensemble de Windows Hello Entreprise](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-overview).


<a name="identity-mfa"></a>
## <a name="set-up-azure-multi-factor-authentication"></a>Configurer Authentication multifacteur Azure

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365*

Dans cette étape, vous allez configurer Authentication multifacteur Azure (MFA) pour ajouter une seconde couche de sécurité aux connexions et transactions des utilisateurs. Authentication multifacteur Azure requiert une méthode de vérification supplémentaire une fois que les utilisateurs ont correctement entré leur mot de passe. Sans Authentication multifacteur Azure, le mot de passe reste la seule méthode de vérification. Le problème avec les mots de passe est que bon nombre d'entre eux se devinent facilement par un pirate ou sont partagés inconsciemment avec des parties non approuvées.

Avec l’authentification multifacteur, la deuxième couche de sécurité peut être :

- un appareil personnel et approuvé qui n’est pas facilement usurpé ou dupliqué (un smartphone, par exemple) ;
- un attribut biométrique (une empreinte numérique, par exemple).

Vous allez activer l’authentification multifacteur et configurer la méthode d’authentification secondaire avec les [stratégies d’accès conditionnel](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted#enable-multi-factor-authentication-with-conditional-access), qui vous permettent d’utiliser les groupes Azure Active Directory (Azure AD) pour déployer l’authentification multifacteur vers des ensembles d’utilisateurs spécifiés, tels que des utilisateurs pilotes, régions géographiques ou services. Informez bien vos utilisateurs que l’authentification multifacteur est en cours d’activation pour qu’ils comprennent les exigences telles que l’utilisation obligatoire d’un smartphone pour la connexion et puissent se connecter correctement. 

Pour plus d’informations, reportez-vous à [Planifier le déploiement d’une authentification multifacteur Azure basée sur Cloud](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted).

|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : authentification multifacteur Azure](multi-factor-authentication-microsoft-365-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-mfa) pour cette étape.

<a name="identity-ident-prot"></a>
## <a name="protect-against-credential-compromise"></a>Protégez-vous contre la compromission des informations d’identification

*Cette étape est facultative et s’applique uniquement à la version E5 de Microsoft 365 Entreprise*

Cette section explique comment configurer des stratégies de protection contre la compromission d’informations d’identification consistant pour un attaquant à déterminer le nom de compte et le mot de passe d’un utilisateur afin d’accéder aux services et données cloud d’une organisation. Azure Active Directory Identity Protection offre plusieurs méthodes pour empêcher un pirate de compromettre les informations d’identification d’un compte d’utilisateur.

Azure AD Identity Protection vous permet de :

|||
|:---------|:---------|
|déterminer et résoudre les vulnérabilités potentielles dans les identités de votre organisation ;|Azure AD utilise le Machine Learning pour détecter les anomalies et les activités suspectes, telles que les connexions et les activités post-connexion. Grâce à ces données, Azure AD Identity Protection génère des rapports et des alertes qui vous permettent d’évaluer les problèmes et de prendre des mesures.|
|Détecter des actions douteuses qui sont liées aux identités de votre organisation et y répondre automatiquement|Vous pouvez configurer des stratégies qui répondent automatiquement aux problèmes détectés lorsqu’un niveau de risque spécifié est atteint. Outre les autres contrôles d’accès conditionnel fournis par Azure AD et Microsoft Intune, ces stratégies peuvent automatiquement bloquer l’accès ou prendre des mesures correctives, qui incluent des réinitialisations de mot de passe et impliquent une authentification multifacteur Azure pour les connexions suivantes.|
|Examiner les incidents suspects et les résoudre avec des actions d’administration|Vous pouvez examiner des événements à risque en utilisant les informations sur l’incident de sécurité. Des flux de travail de base sont disponibles pour effectuer le suivi des enquêtes et lancer des actions de correction, telles que des réinitialisations du mot de passe.|

[Plus d’informations sur Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection).

Reportez-vous à la rubrique des [étapes pour activer Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection-enable).

Les résultats de cette étape sont que vous avez activé Azure AD Identity Protection et que vous l’utilisez pour :

- résoudre les vulnérabilités d’identités potentielles ;
- détecter les tentatives de compromission d’informations d’identification possibles ;
- examiner et résoudre des incidents d’identités suspects en cours.

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test : Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-ident-prot) pour cette étape.

|||
|:-------|:-----|
|![Étape 4](../media/stepnumbers/Step4.png)| [Ajouter vos comptes d’utilisateurs](identity-add-user-accounts.md) |
