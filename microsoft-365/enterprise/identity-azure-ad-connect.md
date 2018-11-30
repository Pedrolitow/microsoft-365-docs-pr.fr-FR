---
title: 'Étape 7 : Synchroniser les identités'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez les options d’identité et configurez Azure AD Connect pour synchroniser votre version locale de Windows Server AD avec Azure AD.
ms.openlocfilehash: 2391ee11a1706bbbfdeb248c5967822d3ea68f72
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866913"
---
# <a name="step-7-synchronize-identities"></a>Étape 7 : Synchroniser les identités

*Cette étape est requise pour les environnements hybrides et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

Dans cette étape, vous allez synchroniser votre version locale de Windows Server Active Directory (AD) avec le client Azure Active Directory (AD) utilisé par vos abonnements Office 365 et Enterprise Mobility + Security (EMS).

Azure AD Connect est l’outil Microsoft pris en charge qui vous guide à travers la synchronisation des identités dont vous avez vraiment besoin seulement, à partir d’environnements Windows Server AD uniques ou à plusieurs forêts avec votre client Azure AD.

![Comment Azure AD Connect synchronise votre répertoire local avec Azure AD](./media/identity-azure-ad-connect/azure-ad-connect.png)

*Comment Azure AD Connect synchronise votre répertoire local avec Azure AD*

La première décision dans votre solution d’identité hybride est votre exigence d’authentification. Vous disposez des options suivantes :

- Avec l’**authentification gérée**, Azure AD gère le processus d’authentification pour la connexion de l’utilisateur. Il existe deux méthodes pour l’authentification gérée : 
    - **Synchronisation de hachage de mot de passe** [recommandée et requise pour certaines fonctionnalités premium]. Cette méthode est la plus simple pour activer l’authentification pour les objets de répertoire locaux dans Azure AD. Azure AD Connect extrait le mot de passe haché de Windows Server AD, effectue un traitement de sécurité supplémentaire sur le mot de passe et l’enregistre dans Azure AD. Pour plus d’informations, reportez-vous à la rubrique relative à l’[implémentation de la synchronisation de hachage de mot de passe avec la synchronisation d’Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-synchronization).
    - L’**authentification directe** fournit une solution de validation de mot de passe simple pour les services basés sur Azure AD. L’authentification directe utilise un agent exécuté sur un ou plusieurs serveurs locaux pour valider les authentifications utilisateur directement avec votre version locale de Windows Server AD. Pour plus d’informations, reportez-vous à la rubrique relative à la [connexion utilisateur avec l’authentification directe Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication).
- Avec l’**authentification fédérée**, le processus d’authentification est redirigé vers un autre fournisseur d’identité via un serveur de fédération des identités, tels que les services de fédération Active Directory (AD FS), pour la connexion d’un utilisateur. Le fournisseur d’identité peut fournir des méthodes d’authentification supplémentaires, telles que l’authentification par carte à puce. Pour en savoir plus, reportez-vous à l’article [Choisir la méthode d’authentification adaptée à votre solution d’identité hybride Azure Active Directory](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).

Une fois que vous avez déterminé votre solution d’identité hybride, téléchargez et exécutez l’[outil de correction d’erreurs de synchronisation d’annuaires IdFix](https://www.microsoft.com/download/details.aspx?id=36832) pour analyser votre Windows Server AD et les problèmes.

Une fois que tous les problèmes identifiés sont résolus par l’outil IdFix, consultez l’article [Implémenter la synchronisation de hachage de mot de passe avec la synchronisation Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-hash-synchronization) pour savoir comment installer l’outil Azure AD Connect et configurer la synchronisation d’annuaires entre votre version locale de Windows Server AD et le client Azure AD pour vos abonnements Office 365 et EMS. Une fois que la synchronisation démarre, conservez vos groupes et comptes d’utilisateur avec votre fournisseur d’identité local, par exemple, Windows Server AD.

Microsoft fournit un ensemble de recommandations sur l’[accès aux appareils et à l’identité](microsoft-365-policies-configurations.md) pour garantir un personnel conforme et productif. 
- Concernant la configuration recommandée pour les environnements hybrides, consultez la colonne **Active Directory avec la synchronisation de hachage de mot de passe** de la section [Travail préparatoire](identity-access-prerequisites.md#prerequisites). 

- Pour la configuration recommandée pour les environnements cloud uniquement, reportez-vous à la colonne **Cloud uniquement** de la section [Travail préparatoire](identity-access-prerequisites.md#prerequisites).

|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test : Synchronisation de hachage de mot de passe](password-hash-sync-m365-ent-test-environment.md)<br> [Guide de laboratoire de test : Authentification directe](pass-through-auth-m365-ent-test-environment.md) |
|||

Comme point de contrôle intermédiaire, consultez les [critères de sortie](identity-exit-criteria.md#crit-identity-sync) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step8.png)| [Surveiller l’état de la synchronisation](identity-azure-ad-connect-health.md) |

