---
title: Étape 5. Gestion des appareils et des applications pour vos Microsoft 365 pour les locataires d’entreprise
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Déployez l’option correcte pour la gestion des appareils et des applications pour vos Microsoft 365 client.
ms.openlocfilehash: 09fd96977fbde0f546049d24b1705d27b4c92080
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62524164"
---
# <a name="step-5-device-and-app-management-for-your-microsoft-365-for-enterprise-tenants"></a>Étape 5. Gestion des appareils et des applications pour vos Microsoft 365 pour les locataires d’entreprise

Microsoft 365 entreprise inclut des fonctionnalités pour vous aider à gérer les appareils et l’utilisation des applications sur ces appareils au sein de votre organisation à l’aide de la gestion des périphériques mobiles (MDM) et de la gestion des applications mobiles (MAM). Vous pouvez gérer les appareils iOS, Android, macOS et Windows pour protéger l’accès aux ressources de votre organisation, y compris à vos données. Par exemple, vous pouvez empêcher l’envoi de courriers électroniques à des personnes extérieures à votre organisation ou isoler les données de l’organisation des données personnelles sur les appareils personnels de votre collaborateur.

Voici un exemple de validation et de gestion des utilisateurs, de leurs appareils et de leur utilisation d’applications de productivité locales et cloud telles que Microsoft Teams.

![Validation et gestion des utilisateurs, des appareils et des applications.](../media/tenant-management-overview/tenant-management-device-app-mgmt.png)

Pour vous aider à sécuriser et protéger les ressources de votre organisation, Microsoft 365 entreprise inclut des fonctionnalités pour vous aider à gérer les appareils et leur accès aux applications. Il existe deux options de gestion des appareils :

- Microsoft Intune, qui est une solution complète de gestion des appareils et des applications pour les entreprises.
- Basic Mobility and Security, qui est un sous-ensemble de services Intune inclus avec tous les produits Microsoft 365 pour la gestion des appareils au sein de votre organisation. Pour plus d’informations, voir [Capabilities of Basic Mobility and Security](../admin/basic-mobility-security/capabilities.md).

Si vous avez Microsoft 365 E3 ou E5, vous devez utiliser Intune.

## <a name="microsoft-intune"></a>Microsoft Intune

Vous [utilisez Microsoft Intune](/mem/intune/fundamentals/planning-guide) pour gérer l’accès à votre organisation à l’aide de la gestion des données de gestion des données (MDM) ou de MAM. La gestion des périphériques mobiles est le cas lorsque les utilisateurs « inscrivent » leurs appareils dans Intune. Une fois qu’un appareil est inscrit, il s’agit d’un appareil géré et peut recevoir les stratégies, règles et paramètres de votre organisation. Par exemple, vous pouvez installer des applications spécifiques, créer une stratégie de mot de passe, installer une connexion VPN, etc.

Les utilisateurs  ayant leurs propres appareils personnels peuvent ne pas vouloir inscrire leurs appareils ou être gérés par Intune et les stratégies de votre organisation. Toutefois, vous devez toujours protéger les ressources et les données de votre organisation. Dans ce scénario, vous pouvez protéger vos applications à l’aide de MAM. Par exemple, vous pouvez utiliser une stratégie MAM qui nécessite qu’un utilisateur entre un code confidentiel lors de l’accès SharePoint sur l’appareil.

Vous déterminerez également la façon dont vous allez gérer les appareils personnels et les appareils dont l’organisation est propriétaire. Vous souhaitez peut-être traiter les appareils différemment, en fonction de leur utilisation.

## <a name="identity-and-device-access-configurations"></a>Configurations des identités et de l’accès aux appareils

Microsoft fournit un ensemble de configurations pour l’accès aux identités et aux [appareils afin de](../security/office-365-security/microsoft-365-policies-configurations.md) garantir un personnel sécurisé et productif. Ces configurations incluent l’utilisation des éléments suivants :

- Stratégies d’accès conditionnel Azure AD
- Microsoft Intune conformité des appareils et stratégies de protection des applications
- Azure AD stratégies de risque utilisateur de protection des identités
- Stratégies supplémentaires des applications cloud

Voici un exemple de l’application de ces paramètres et stratégies pour valider et restreindre les utilisateurs, leurs appareils et leur utilisation d’applications de productivité locales et cloud telles que Microsoft Teams.

![Configurations des identités et de l’accès aux appareils pour les exigences et les restrictions imposées aux utilisateurs, à leurs appareils et à leur utilisation des applications.](../media/tenant-management-overview/tenant-management-device-app-mgmt-golden-config.png)

Pour l’accès aux appareils et la gestion des applications, utilisez les configurations des articles suivants :

- [Conditions préalables](../security/office-365-security/identity-access-prerequisites.md)
- [Stratégies communes pour les identités et l’accès aux appareils](../security/office-365-security/identity-access-policies.md)

## <a name="results-of-step-5"></a>Résultats de l’étape 5

Pour la gestion des appareils et des applications pour votre client Microsoft 365, vous avez déterminé les paramètres et stratégies Intune pour valider et restreindre les utilisateurs, leurs appareils et leur utilisation des applications de productivité locales et cloud.

Voici un exemple de client avec la gestion des applications et des appareils Intune avec les nouveaux éléments mis en surbrill plan.

![Exemple de client avec gestion d’appareils et d’applications Intune.](../media/tenant-management-overview/tenant-management-tenant-build-step5.png)

Dans cette illustration, le client a :

- Appareils de l’organisation inscrits dans Intune.
- Stratégies d’appareil et d’application Intune pour les appareils inscrits et personnels.

## <a name="ongoing-maintenance-for-device-and-app-management"></a>Maintenance continue pour la gestion des appareils et des applications

Régulièrement, vous devrez peut-être : 

- Gérer l’inscription des appareils.
- Révisez vos paramètres et stratégies pour les applications, les appareils et les exigences de sécurité supplémentaires.