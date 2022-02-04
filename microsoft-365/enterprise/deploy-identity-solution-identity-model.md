---
title: Étape 1. Déterminer votre modèle d’identité cloud
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.date: 09/30/2020
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
  - Ent_O365
  - M365-identity-device-management
  - M365-security-compliance
f1.keywords:
  - CSH
ms.custom:
  - Adm_O365
  - seo-marvel-mar2020
search.appverid:
  - MET150
  - MOE150
  - BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Étape 1. Déterminer votre modèle d’identité cloud Microsoft
---

# <a name="step-1-determine-your-cloud-identity-model"></a>Étape 1. Déterminer votre modèle d’identité cloud

Microsoft 365 utilise Azure Active Directory (Azure AD), un service d’authentification et d’identité utilisateur basé sur le cloud inclus dans votre abonnement Microsoft 365, pour gérer les identités et l’authentification pour Microsoft 365. La configuration correcte de votre infrastructure d’identité est essentielle à la gestion Microsoft 365'accès des utilisateurs et des autorisations pour votre organisation.

Avant de commencer, regardez cette vidéo pour obtenir une vue d’ensemble des modèles d’identité et de l’authentification pour Microsoft 365.

<p> </p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

Votre premier choix de planification est votre modèle d’identité cloud.

## <a name="microsoft-cloud-identity-models"></a>Modèles d’identité cloud Microsoft

Pour planifier les comptes d’utilisateurs, vous devez d’abord comprendre les deux modèles d’identité Microsoft 365. Vous pouvez gérer les identités de votre organisation uniquement dans le cloud, ou vous pouvez conserver vos identités AD DS (Active Directory Domain Services) locales et les utiliser pour l’authentification lorsque les utilisateurs accèdent aux services cloud Microsoft 365.

Voici les deux types d’identité et leur meilleur ajustement et leurs avantages.

| Attribut | Identité cloud uniquement | Identité hybride |
|:-------|:-----|:-----|
| **Définition** | Le compte d’utilisateur n’existe que dans Azure AD client pour votre abonnement Microsoft 365 client. | Le compte d’utilisateur existe dans AD DS et une copie se trouve également dans le client Azure AD pour votre abonnement Microsoft 365 client. Le compte d’utilisateur Azure AD peut également inclure une version hachée du mot de passe du compte d’utilisateur AD DS déjà haché. |
| **Comment Microsoft 365 authentifier les informations d’identification de l’utilisateur** | Le Azure AD client de votre abonnement Microsoft 365 effectue l’authentification avec le compte d’identité cloud. | Le Azure AD client de votre abonnement Microsoft 365 gère le processus d’authentification ou redirige l’utilisateur vers un autre fournisseur d’identité. |
| **Recommandé pour** | Organisations qui n’ont pas ou n’ont pas besoin d’une AD DS locale. | Organisations utilisant AD DS ou un autre fournisseur d’identité. |
| **Plus grand avantage** | Simple à utiliser. Aucun outil ou serveur d’annuaire supplémentaire n’est requis. | Les utilisateurs peuvent utiliser les mêmes informations d’identification lors de l’accès à des ressources sur site ou en nuage. |
||||

## <a name="cloud-only-identity"></a>Identité cloud uniquement

Une identité cloud uniquement utilise les comptes utilisateur qui existent uniquement dans Azure AD. L’identité cloud uniquement est généralement utilisée par les petites organisations qui n’ont pas de serveurs locaux ou qui n’utilisent pas AD DS pour gérer les identités locales.

Voici les composants de base de l’identité cloud uniquement.

![Composants de base de l’identité cloud uniquement.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Les utilisateurs locaux et distants (en ligne) utilisent leur compte d Azure AD et leur mot de passe pour accéder Microsoft 365 services cloud. Azure AD authentifie les informations d'identification de l'utilisateur en fonction de son compte utilisateur et de son mot de passe stockés.

### <a name="administration"></a>Administration
Étant donné que les comptes d’utilisateurs sont stockés uniquement dans Azure AD, vous gérez les identités cloud à l’aide d’outils tels que [Centre d'administration Microsoft 365 et](/admin) [Windows PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md).

## <a name="hybrid-identity"></a>Identité hybride

L’identité hybride utilise des comptes qui proviennent d’un service AD DS local et qui ont une copie dans le client Azure AD d’un abonnement Microsoft 365 client. La plupart des modifications, à l’exception des [attributs de compte spécifiques](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized), ne s’érodent qu’à sens unique. Les modifications apportées aux comptes d’utilisateurS AD DS sont synchronisées avec leur copie dans Azure AD.

Azure AD Connecter fournit la synchronisation de compte en cours. Il s’exécute sur un serveur local, recherche les modifications dans les AD DS et les Azure AD. Azure AD Connecter permet de filtrer les comptes synchronisés et de synchroniser une version hachée des mots de passe utilisateur, appelée synchronisation de hachage de mot de passe( PHS).

Lorsque vous implémentez une identité hybride, votre AD DS local représente la source de référence pour les informations sur le compte. Cela signifie que vous effectuez des tâches d’administration principalement locales, qui sont ensuite synchronisées avec Azure AD.

Voici les composants de l’identité hybride.

![Composants de l’identité hybride.](../media/about-microsoft-365-identity/hybrid-identity.png)

Le Azure AD dispose d’une copie des comptes AD DS. Dans cette configuration, les utilisateurs locaux et distants qui accèdent Microsoft 365 services cloud s’authentifier Azure AD.

> [!NOTE]
> Vous devez toujours utiliser Azure AD Connecter pour synchroniser les comptes d’utilisateurs pour l’identité hybride. Vous avez besoin des comptes d’utilisateur synchronisés dans Azure AD pour effectuer l’attribution de licences et la gestion des groupes, configurer les autorisations et d’autres tâches administratives qui impliquent des comptes d’utilisateurs.

### <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a>Synchronisation d’annuaires et d’identités hybrides pour Microsoft 365

En fonction des besoins de votre entreprise et des exigences techniques, le modèle d’identité hybride et la synchronisation d’annuaires sont le choix le plus courant pour les clients d’entreprise qui adoptent Microsoft 365. La synchronisation d’annuaires vous permet de gérer les identités dans vos services de domaine Active Directory (AD DS) et toutes les mises à jour des comptes d’utilisateur, des groupes et des contacts sont synchronisées avec le client Azure Active Directory (Azure AD) de votre abonnement Microsoft 365.

>[!Note]
>Lorsque les comptes d’utilisateurS AD DS sont synchronisés pour la première fois, ils ne se voit pas attribuer automatiquement une licence Microsoft 365 et ne peuvent pas accéder aux services Microsoft 365, tels que la messagerie électronique. Vous devez d’abord leur attribuer un emplacement d’utilisation. Ensuite, attribuez une licence à ces comptes d’utilisateurs, individuellement ou dynamiquement par le biais de l’appartenance à un groupe.
>

#### <a name="authentication-for-hybrid-identity"></a>Authentification pour l’identité hybride

Il existe deux types d’authentification lors de l’utilisation du modèle d’identité hybride :

- Authentification gérée

  Azure AD gère le processus d’authentification à l’aide d’une version de hachage stockée localement du mot de passe ou envoie les informations d’identification à un agent logiciel local pour qu’ils soient authentifiés par les services AD DS locaux.

- Authentification fédérée

  Azure AD redirige l’ordinateur client demandant l’authentification vers un autre fournisseur d’identité.

#### <a name="managed-authentication"></a>Authentification gérée

Il existe deux types d’authentification gérée :

- Synchronisation de hachage de mot de passe (PHS)

  Azure AD effectue l’authentification proprement dite.

- Authentification directe (PTA)

  Azure AD’AD DS effectue l’authentification.


##### <a name="password-hash-synchronization-phs"></a>Synchronisation de hachage de mot de passe (PHS)

Avec PHS, vous synchronisez vos comptes d’utilisateur AD DS avec Microsoft 365 et gérez vos utilisateurs en local. Les hèses de mots de passe utilisateur sont synchronisés à partir de vos services AD DS vers Azure AD afin que les utilisateurs disposent du même mot de passe en local et dans le cloud. Il s’agit du moyen le plus simple d’activer l’authentification pour les identités AD DS Azure AD. 

![Synchronisation de hachage de mot de passe (PHS).](../media/plan-for-directory-synchronization/phs-authentication.png)

Lorsque les mots de passe sont modifiés ou réinitialisés en local, les nouveaux hésiteurs de mot de passe sont synchronisés avec Azure AD afin que vos utilisateurs peuvent toujours utiliser le même mot de passe pour les ressources cloud et les ressources sur site. Les mots de passe utilisateur ne sont jamais envoyés Azure AD ou stockés dans Azure AD texte clair. Certaines fonctionnalités premium de Azure AD, telles que identity protection, nécessitent PHS, quelle que soit la méthode d’authentification sélectionnée.
  
Pour en [savoir plus,](/azure/active-directory/hybrid/choose-ad-authn) voir choisir la méthode d’authentification la plus efficace.
  
##### <a name="pass-through-authentication-pta"></a>Authentification directe (PTA)

PTA fournit une validation de mot de passe simple pour les services d’authentification Azure AD à l’aide d’un agent logiciel s’exécutant sur un ou plusieurs serveurs locaux pour valider les utilisateurs directement avec vos services AD DS. Avec LTA, vous synchronisez les comptes d’utilisateur AD DS avec Microsoft 365 et gérez vos utilisateurs en local. 

![Authentification directe (PTA).](../media/plan-for-directory-synchronization/pta-authentication.png)

PTA permet à vos utilisateurs de se connectent à la fois aux ressources et applications Microsoft 365 locaux et aux applications à l’aide de leur compte local et de leur mot de passe. Cette configuration valide les mots de passe des utilisateurs directement par rapport à vos AD DS sur site sans stocker les h départs de mot de passe dans Azure AD. 

PTA est également pour les organisations ayant une obligation de sécurité d’appliquer immédiatement les états de compte d’utilisateur local, les stratégies de mot de passe et les heures d’ouverture de bureau. 
  
Pour en [savoir plus,](/azure/active-directory/hybrid/choose-ad-authn) voir choisir la méthode d’authentification la plus efficace.
  
##### <a name="federated-authentication"></a>Authentification fédérée

L’authentification fédérée est principalement destinée aux grandes entreprises ayant des exigences d’authentification plus complexes. Les identités AD DS sont synchronisées avec Microsoft 365 et les comptes d’utilisateurs sont gérés localement. Avec l’authentification fédérée, les utilisateurs ont le même mot de passe en local et dans le cloud et ils n’ont pas besoin de se connecter à nouveau pour utiliser Microsoft 365. 

L’authentification fédérée peut prendre en charge des exigences d’authentification supplémentaires, telles que l’authentification par carte à puce ou l’authentification multifacteur tierce. Elle est généralement requise lorsque les organisations ont une exigence d’authentification non prise en charge en Azure AD.
 
Pour en [savoir plus,](/azure/active-directory/hybrid/choose-ad-authn) voir choisir la méthode d’authentification la plus efficace.
  
Pour les fournisseurs d’identité et d’authentification tiers, les objets d’annuaire locaux peuvent être synchronisés avec l’accès aux ressources Microsoft 365 et cloud qui sont principalement gérés par un fournisseur d’identité (IdP) tiers. Si votre organisation utilise une solution de fédération tierce, vous pouvez configurer l’sign-on avec cette solution pour Microsoft 365 à condition que la solution de fédération tierce soit compatible avec Azure AD.
  
Consultez la [Azure AD de compatibilité de fédération pour](/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) en savoir plus.
  
### <a name="administration"></a>Administration

Étant donné que les comptes d’utilisateur d’origine et faisant autorité sont stockés dans les AD DS locales, vous gérez vos identités avec les mêmes outils que vous gérez vos AD DS.

Vous n’utilisez pas la Centre d'administration Microsoft 365 ou PowerShell pour gérer Microsoft 365 comptes d’utilisateur synchronisés dans Azure AD.

## <a name="next-step"></a>Étape suivante

[![Protéger vos Microsoft 365 privilégiés](../media/deploy-identity-solution-overview/protect-your-global-administrator-accounts.png)](protect-your-global-administrator-accounts.md)

Continuez [l’étape 2](protect-your-global-administrator-accounts.md) pour sécuriser vos comptes d’administrateur général.
