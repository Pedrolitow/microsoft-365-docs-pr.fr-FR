---
title: 'Étape 4 : Ajouter vos comptes d’utilisateurs'
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
description: Vous pouvez ajouter des comptes d’utilisateurs et des groupes directement dans le Cloud ou par synchronisation avec votre répertoire local.
ms.openlocfilehash: 324d4662f868a4a92693b43c6bc0f75c11f20519
ms.sourcegitcommit: 93e6bf1b541e22129f8c443051375d0ef1374150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "42633102"
---
# <a name="step-4-add-your-user-accounts"></a>Étape 4 : Ajouter vos comptes d’utilisateurs

![Phase 2 - Identité](../media/deploy-foundation-infrastructure/identity_icon-small.png)

<a name="identity-cloud-only"></a>
## <a name="create-your-user-accounts-for-cloud-only-identity"></a>Créer vos comptes d’utilisateur pour l’identité Cloud uniquement

Pour l’identité Cloud uniquement, créez vos utilisateurs et groupes dans Azure Active Directory (Azure AD). Vous pouvez utiliser :

- Le Centre d’administration Microsoft 365
- Le Portail Microsoft Azure
- Azure PowerShell

<a name="identity-sync"></a>
## <a name="synchronize-identities-for-hybrid-identity"></a>Synchroniser les identités pour l’identité hybride

*Cette opération, obligatoire pour les environnements hybrides, s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans cette section, vous allez synchroniser votre instance locale de Services de domaine Active Directory (AD DS) avec le client Azure AD utilisé par Office 365, Microsoft Intune et d’autres services cloud, parmi lesquels Microsoft 365 Entreprise.

Azure AD Connect est l’outil Microsoft pris en charge qui vous guide tout au long de la synchronisation des identités dont vous avez réellement besoin, des environnements AD DS à une ou plusieurs forêts à votre locataire Azure AD. La figure suivante illustre le processus de base de la synchronisation Azure AD Connect.

![Comment Azure AD Connect synchronise votre annuaire local avec Azure AD](../media/identity-add-user-accounts/azure-ad-connect.png)

1. Azure AD Connect exécuté sur un serveur interroge AD DS pour identifier les modifications apportées aux comptes, aux groupes et aux contacts.
2. Azure AD Connect envoie ces modifications au locataire Azure AD de votre abonnement Microsoft 365.

La première décision dans votre solution d’identité hybride est votre exigence d’authentification. Vous disposez des options suivantes :

- Avec l’**authentification gérée**, Azure AD gère le processus d’authentification pour la connexion de l’utilisateur. Il existe deux méthodes pour l’authentification gérée : 
    - **Synchronisation du hachage de mot de passe (PHS)** [recommandée et requise pour certaines fonctionnalités premium]. Il s’agit du moyen le plus simple d’activer l’authentification des objets d’annuaire locaux dans Azure AD. Azure AD Connect extrait le mot de passe haché d’AD DS, lui applique un traitement de sécurité supplémentaire et le synchronise avec Azure AD. Pour plus d’informations, consultez [Implémenter la synchronisation de hachage du mot de passe avec la synchronisation Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).
    - L’**authentification directe** fournit une solution de validation du mot de passe simple pour les services Azure AD. L’authentification directe utilise un agent qui s’exécute sur un ou plusieurs serveurs locaux pour valider les authentifications des utilisateurs directement auprès de votre instance locale d’AD DS. Pour plus d’informations, consultez [Connexion utilisateur avec l’authentification directe Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication).
- Avec l’**authentification fédérée**, le processus d’authentification est redirigé vers un autre fournisseur d’identité via un serveur de fédération des identités, tels que les services de fédération Active Directory (AD FS), pour la connexion d’un utilisateur. Le fournisseur d’identité peut fournir des méthodes d’authentification supplémentaires, telles que l’authentification par carte à puce. Pour en savoir plus, reportez-vous à l’article [Choisir la méthode d’authentification adaptée à votre solution d’identité hybride Azure Active Directory](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).

Regardez cette vidéo pour obtenir une vue d’ensemble des modèles d’identité et de l’authentification pour Microsoft 365 Entreprise.

<p> </p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

Après avoir déterminé votre solution d’identité hybride, téléchargez et exécutez l’[outil de correction d’erreurs de synchronisation d’annuaires IdFix](https://www.microsoft.com/download/details.aspx?id=36832) pour analyser les problèmes de votre instance d’AD.

Après avoir résolu tous les problèmes identifiés par l’outil IdFix, consultez [Implémenter la synchronisation de hachage de mot de passe avec la synchronisation](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-hash-synchronization) pour savoir comment installer l’outil Azure AD Connect et configurer la synchronisation d’annuaires entre votre instance locale d’AD DS et le locataire Azure AD de vos abonnements Microsoft 365. Une fois la synchronisation lancée, vous gérerez vos groupes et comptes d’utilisateur avec votre fournisseur d’identité local, par exemple AD DS.

Microsoft fournit un ensemble de recommandations sur l’[accès aux appareils et à l’identité](microsoft-365-policies-configurations.md) pour garantir un personnel conforme et productif. 

- Concernant la configuration recommandée pour les environnements hybrides, consultez la colonne **Active Directory avec la synchronisation de hachage de mot de passe** de la section [Travail préparatoire](identity-access-prerequisites.md#prerequisites). 

- Pour la configuration recommandée pour les environnements cloud uniquement, reportez-vous à la colonne **Cloud uniquement** de la section [Travail préparatoire](identity-access-prerequisites.md#prerequisites).

Une fois vos groupes et utilisateurs locaux présents dans Azure AD, vous pouvez commencer à attribuer des charges de travail de productivité telles que OneDrive Entreprise et Exchange Online.

|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de laboratoire de test : Synchronisation de hachage de mot de passe](password-hash-sync-m365-ent-test-environment.md)<br> [Guide de laboratoire de test : Authentification directe](pass-through-auth-m365-ent-test-environment.md) |
|||

Comme point de contrôle intermédiaire, consultez les [critères de sortie](identity-exit-criteria.md#crit-identity-sync) correspondant à cette section.

<a name="identity-sync-health"></a>
## <a name="monitor-synchronization-health"></a>Surveiller l’état de la synchronisation

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365*

Dans cette section, vous allez installer un agent d’intégrité Azure AD Connect sur chacun de vos contrôleurs de domaine AD DS pour surveiller votre infrastructure d’identité et les services de synchronisation fournis par Azure AD Connect. Les informations de surveillance sont disponibles sur un portail Azure AD Connect Health, où vous pouvez afficher les alertes, surveiller les performances, analyser les utilisations, etc.

![Composants d’Azure AD Connect Health](../media/identity-add-user-accounts/identity-azure-ad-connect-health.png)

La décision de conception clé concernant l’utilisation d’Azure AD Connect Health est basée sur la manière dont vous utilisez Azure AD Connect :

- Si vous utilisez de nouveau l’option d’**authentification gérée**, commencez avec la rubrique relative à l’[utilisation d’Azure AD Connect Health avec la synchronisation](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) pour comprendre et configurer Azure AD Connect Health.
- Si vous synchronisez uniquement les noms des comptes et des groupes à l’aide de l’**authentification fédérée** avec Active Directory Federation Services (AD FS), commencez avec la rubrique [Utilisation d’Azure AD Connect Health avec AD FS](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) pour comprendre et configurer Azure AD Connect Health.

Au terme de cette section, vous aurez :

- l’agent Azure AD Connect Health installé sur vos serveurs de fournisseur d’identité local ;
- le portail Azure AD Connect Health qui affiche l’état actuel de vos activités d’infrastructure et de synchronisation locales avec le client Azure AD pour votre abonnement Microsoft 365.

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-sync-health) pour cette étape.



<a name="identity-pw-writeback"></a>
## <a name="simplify-password-updates"></a>Simplifiez les mises à jour du mot de passe

*Cette étape est facultative pour les environnements hybrides et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans cette section, vous devez autoriser les utilisateurs à réinitialiser leur mot de passe via Azure Active Directory (Azure AD), qui est ensuite répliqué sur votre Active Directory Domain Services (AD DS)local. Ce processus est appelé écriture différée de mot de passe. Avec l’écriture différée de mot de passe, les utilisateurs n’ont pas besoin de mettre à jour leur mot de passe via la version locale Active Directory Domain Services où sont stockés les comptes d’utilisateurs et leurs attributs. C’est utile pour les utilisateurs itinérants ou distants qui ne possèdent pas de connexion d’accès à distance au réseau local.

L’écriture différée de mot de passe est requise pour exploiter pleinement les fonctionnalités Azure AD Identity Protection, comme obliger les utilisateurs à modifier leur mot de passe en local lorsqu’un risque élevé de compromission de compte a été détecté.

Pour obtenir plus d’informations et les instructions de configuration, consultez l’article [Azure AD SSPR avec l’écriture différée de mot de passe](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>Procédez à la mise à niveau vers la dernière version d’Azure AD Connect pour vous assurer la meilleure expérience possible et les nouvelles fonctionnalités dès leur diffusion. Pour obtenir plus d’informations, consultez l’article [Installation personnalisée d’Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : Écriture différée de mot de passe](password-writeback-m365-ent-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-pw-writeback) pour cette étape.

|||
|:-------|:-----|
|![Étape 5](../media/stepnumbers/Step5.png)| [Utiliser des groupes pour la gestion](identity-use-group-management.md) |
