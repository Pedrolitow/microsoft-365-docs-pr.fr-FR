---
title: Prise en charge des applications client et de services Microsoft 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Dans cet article, recherchez des détails sur la prise en charge des applications clientes et de services Microsoft 365.
ms.openlocfilehash: e380efffc1bf29cbd4d3a77d32e4d1f8b2994da3
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50905007"
---
# <a name="microsoft-365-client-and-services-app-support"></a>Prise en charge des applications client et de services Microsoft 365

Microsoft prend en charge un large éventail de fonctionnalités de sécurité, d’authentification et de conformité pour assurer la sécurité des données client et permet aux administrateurs informatiques de personnaliser les stratégies dans le Centre d’administration Microsoft 365 pour leurs utilisateurs. Les fonctionnalités suivantes ne sont qu’un sous-ensemble des nombreuses fonctionnalités d’entreprise que vous pouvez configurer en fonction de votre abonnement Microsoft 365.

## <a name="client-and-service-support"></a>Prise en charge du client et du service

### <a name="continuous-access-evaluation-preview"></a>Évaluation de l’accès continu (prévisualisation)

L’évaluation de l’accès continu est implémentée en permettant aux services, tels qu’Exchange Online, SharePoint Online et Teams, de s’abonner à des événements critiques dans Azure Active Directory afin que ces événements soient évalués et appliqués en temps quasi réel. L’évaluation d’événement critique ne repose pas sur les stratégies d’accès conditionnel et est donc disponible dans n’importe quel client.

Les événements suivants sont actuellement évalués :

- Un compte d’utilisateur est supprimé ou désactivé
- Le mot de passe d’un utilisateur est modifié ou réinitialisé
- L’authentification multifacteur est activée pour l’utilisateur
- L’administrateur révoque explicitement tous les jetons d’actualisation pour un utilisateur
- Risques élevés pour les utilisateurs détectés par Azure AD Identity Protection

Pour plus d’informations sur l’évaluation de l’accès continu pour la prise en charge des applications client et de services, voir [Évaluation de l’accès continu (prévisualisation).](/azure/active-directory/conditional-access/concept-continuous-access-evaluation)

## <a name="client-support"></a>Prise en charge des clients

### <a name="certificate-based-authentication"></a>Authentification basée sur des certificats

L’authentification basée sur les certificats (CBA) est l’utilisation d’un certificat numérique pour identifier un utilisateur, un ordinateur ou un appareil avant d’accorder l’accès à une ressource, un réseau, une application ou un service. Dans l’authentification des utilisateurs, il est souvent déployé en coordination avec les méthodes traditionnelles telles que les noms d’utilisateur et les mots de passe.

Certaines solutions traditionnelles fonctionnent uniquement pour les utilisateurs, telles que la biométrie et les mots de passe à accès unique. Avec l’authentification basée sur les certificats, la même solution peut être utilisée pour tous les points de terminaison ; utilisateurs, appareils et internet des objets (IoT) croissant.

Pour plus d’informations sur l’authentification basée sur les certificats pour la prise en charge des applications clientes et de services, voir Prise en charge des applications [clientes Microsoft 365](microsoft-365-client-support-certificate-based-authentication.md): Authentification basée sur les certificats.

### <a name="conditional-access"></a>Accès conditionnel

L’accès conditionnel est l’outil utilisé par Azure Active Directory pour rassembler les signaux, prendre des décisions et appliquer des stratégies d’accès organisationnel. L’accès conditionnel est au cœur du nouveau modèle de contrôle piloté par l’identité.

Les stratégies d’accès conditionnel sont des instructions if-then pour accorder l’accès aux ressources. Si un utilisateur souhaite accéder à une ressource, il doit effectuer une action. Les signaux courants que l’accès conditionnel peut utiliser lors de la prise de décision d’accès à une stratégie sont les suivants :

- Appartenance à un utilisateur ou à un groupe
- Informations d’emplacement IP
- Informations sur l’appareil
- Informations sur l’application
- Détection des risques calculés et en temps réel
- Microsoft Cloud App Security (MCAS)

Lorsque vous prenez ces décisions d’accès, les stratégies peuvent effectuer différentes actions :

- La stratégie peut bloquer l’accès : cette configuration est l’action la plus restrictive et empêche l’utilisateur d’accéder à la ressource.
- La stratégie peut accorder l’accès : cette configuration est une décision moins restrictive et peut nécessiter une ou plusieurs des options suivantes :

    - Authentification multifacteur
    - L’appareil à marquer comme conforme
    - L’appareil est joint à Azure AD hybride
    - Une application cliente approuvée
    - Stratégie de protection des applications configurée (aperçu)

Pour plus d’informations sur l’accès conditionnel pour la prise en charge des applications client et de services, voir :

- [Prise en charge des applications clientes Microsoft 365 : accès conditionnel basé sur l’appareil](microsoft-365-client-support-conditional-access.md)

### <a name="mobile-application-management"></a>Gestion des applications mobiles

Les utilisateurs accèdent souvent à la fois aux documents d’organisation et personnels, aux e-mails et aux données à partir du même appareil mobile. Ces appareils sont souvent personnels et doivent être configurés pour protéger les données de l’organisation et la confidentialité personnelle de l’utilisateur.

Lorsqu’un utilisateur accède aux données de l’organisation, l’organisation doit être sûre que les stratégies d’organisation, telles que les stratégies de configuration et les stratégies de protection, sont appliquées pour protéger les données de l’organisation sur l’appareil. En outre, le contenu personnel de l’utilisateur sur l’appareil doit rester en dehors du contrôle de l’organisation.

Pour le contenu géré par l’organisation, vous pouvez appliquer des stratégies de gestion des applications pour contrôler la façon dont les données sont accessibles, partagées et utilisées à l’aide de Microsoft Intune. Par exemple, les actions suivantes sont prises en charge :

- Effacer à distance le contenu de l’organisation gérée (également appelé données d’organisation)
- Empêcher le pasting de contenu d’organisation dans des emplacements autres que l’organisation
- Exiger un code confidentiel pour accéder au contenu de l’organisation
- Empêcher l’exécution d’applications gérées sur des appareils jailbreakés ou racines
- Empêcher l’enregistrée du contenu de l’organisation dans les fournisseurs de stockage cloud non désapprouvés
- Empêcher le transfert de contenu non désapprouvé dans des applications gérées
- Autoriser l’accès au contenu de l’organisation uniquement après l’application des stratégies
- Fournir la configuration de l’application pour gérer le comportement et les paramètres de l’application
- Limiter l’application gérée à une identité définie en désactivant les fonctionnalités multi-identité ou l’utilisation personnelle

Pour plus d’informations sur la gestion des applications mobiles avec Microsoft Intune, voir [Qu’est-ce que la](/mem/intune/apps/app-management) gestion des applications Microsoft Intune ?

### <a name="multi-factor-authentication"></a>Authentification multifacteur

[L’authentification multifacteur (MFA) est une méthode de contrôle d’accès à l’ordinateur dans laquelle un utilisateur n’a accès qu’après avoir réussi à présenter plusieurs preuves distinctes à un mécanisme d’authentification. Cette méthode utilise généralement au moins deux des catégories suivantes :

- Connaissances (qu’ils connaissent)
- Possession (quelque chose qu’ils ont)
- Inherence (quelque chose qu’ils sont)

Pour plus d’informations sur l’authentification multifacteur pour la prise en charge des applications client et de services, voir Prise en charge des applications [clientes Microsoft 365](microsoft-365-client-support-multi-factor-authentication.md): authentification multifacteur.

### <a name="single-sign-on"></a>Authentification unique

L' sign-on unique (SSO) ajoute sécurité et commodité lorsque vos utilisateurs se connectent aux applications dans Azure Active Directory. Avec l' sign-on unique, les utilisateurs se connectent une fois avec un compte pour accéder aux appareils joints au domaine AD DS (Active Directory Domain Services) locaux, aux applications SaaS (Software as a Service) et aux applications web de votre organisation.

Pour plus d’informations sur l' sign-on unique pour la prise en charge des applications client et de services, voir Prise en charge des applications [clientes Microsoft 365 : Sign-on unique](microsoft-365-client-support-single-sign-on.md).

## <a name="services-support"></a>Prise en charge des services

### <a name="modern-authentication"></a>Authentification moderne

L’authentification moderne permet aux clients de s’authentifier sur Office 365 et aux administrateurs clients d’appliquer des exigences d’authentification spécifiques au sein de la location Office 365, telles que :

- Prise en charge de l’authentification multifacteur pour l’interaction administrative avec le client et les services, et l’interaction de l’utilisateur final avec les applications et leurs données
- Accès conditionnel
- Se connecte au fournisseur d’identité tiers SAML
- Connexion par carte à puce sur des ordinateurs personnels
- Authentification basée sur les certificats sur les appareils mobiles
- Ne nécessite plus la transmission des informations d’identification sur l’authentification de base.

Pour plus d’informations sur la prise en charge des services d’authentification modernes, voir [Authentification et autorisation.](/azure/active-directory/develop/authentication-vs-authorization)

### <a name="azure-active-directory-conditional-access"></a>Accès conditionnel Azure Active Directory

Les règles d’accès conditionnel Azure Active Directory (Azure AD) permettent aux clients de contrôler l’accès aux services en ligne, en fonction d’attributs tels que la conformité des appareils ou l’emplacement réseau. Les solutions suivantes peuvent être utilisées :

- Accès conditionnel basé sur l’authentification multifacteur Azure AD
- Accès conditionnel basé sur l’emplacement Azure AD
- Accès conditionnel basé sur l’appareil Azure AD

Les règles d’accès conditionnel Azure AD sont appliquées par application et sont disponibles pour que les clients contrôlent l’accès en fonction de différentes conditions. À l’aide de la gestion des périphériques mobiles [(MDM) ou d’Intune,](/mem/intune/fundamentals/what-is-device-management)les clients doivent être en mesure de restreindre l’accès à Microsoft 365 uniquement aux utilisateurs qui utilisent un appareil de l’organisation ou qui ont inscrit leur appareil personnel pour la gestion. Par exemple, les clients peuvent configurer des règles d’accès conditionnel pour appliquer des contrôles tels que :

- Autoriser uniquement l’accès à partir d’appareils joints à un domaine ou conformes à un domaine
- Appliquer l’authentification multifacteur pour tout accès aux services Exchange Online

Pour plus d’informations sur l’accès conditionnel Azure Active Directory, voir [qu’est-ce que l’accès conditionnel ?](/azure/active-directory/conditional-access/overview)

### <a name="tls-12-support"></a>Prise en charge de TLS 1.2

Pour fournir le meilleur chiffrement de classe à nos clients, Microsoft prévoit d’arrêter la prise en charge des versions TLS 1.0 et 1.1 dans Office 365 et Office 365 GCC.

Nous savons que la sécurité de vos données est importante et nous nous engageons à assurer la transparence des modifications susceptibles d’affecter votre utilisation du service TLS. Il est recommandé que toutes les combinaisons client-serveur et navigateur-serveur utilisent TLS 1.2 (ou une version ultérieure) pour maintenir la connexion aux services Office 365. Il se peut que vous deviez procéder à la mise à jour de certaines combinaisons client-serveur et navigateur-serveur.

Pour plus d’informations sur la prise en charge de TLS 1.2 et la prise en charge des services, voir Préparation de [TLS 1.2 dans Office 365 et Office 365 GCC](../compliance/prepare-tls-1.2-in-office-365.md).