---
title: Étape 5. Gestion des appareils et des applications pour votre Microsoft 365 pour les locataires d’entreprise
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Déployez l’option appropriée pour la gestion des appareils et des applications pour vos locataires Microsoft 365.
ms.openlocfilehash: 5650c4e11258c621a420927a73aaba380802b07e
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67730240"
---
# <a name="step-5-device-and-app-management-for-your-microsoft-365-for-enterprise-tenants"></a>Étape 5. Gestion des appareils et des applications pour votre Microsoft 365 pour les locataires d’entreprise

Microsoft 365 pour entreprise inclut des fonctionnalités permettant de gérer les appareils et l’utilisation d’applications sur ces appareils au sein de votre organisation avec la gestion des appareils mobiles (GPM) et la gestion des applications mobiles (MAM). Vous pouvez gérer des appareils iOS, Android, macOS et Windows pour protéger l’accès aux ressources de votre organisation, y compris vos données. Par exemple, vous pouvez empêcher l’envoi d’e-mails à des personnes extérieures à votre organisation ou isoler les données de l’organisation des données personnelles sur les appareils personnels de votre travailleur.

Voici un exemple de validation et de gestion des utilisateurs, de leurs appareils et de leur utilisation d’applications de productivité locales et cloud comme Microsoft Teams.

![Validation et gestion des utilisateurs, des appareils et des applications.](../media/tenant-management-overview/tenant-management-device-app-mgmt.png)

Pour vous aider à sécuriser et protéger les ressources de votre organisation, Microsoft 365 pour entreprise inclut des fonctionnalités permettant de gérer les appareils et leur accès aux applications. Il existe deux options pour la gestion des appareils :

- Microsoft Intune, qui est une solution complète de gestion des appareils et des applications pour les entreprises.
- Mobilité et sécurité de base, qui est un sous-ensemble de services Intune inclus avec tous les produits Microsoft 365 pour la gestion des appareils dans votre organisation. Pour plus d’informations, consultez [Fonctionnalités de mobilité et de sécurité de base](../admin/basic-mobility-security/capabilities.md).

Si vous avez Microsoft 365 E3 ou E5, vous devez utiliser Intune.

## <a name="microsoft-intune"></a>Microsoft Intune

Vous utilisez [Microsoft Intune](/mem/intune/fundamentals/planning-guide) pour gérer l’accès à votre organisation à l’aide de GPM ou DEM. MDM est le moment où les utilisateurs « inscrivent » leurs appareils dans Intune. Une fois qu’un appareil est inscrit, il s’agit d’un appareil géré et peut recevoir les stratégies, les règles et les paramètres de votre organisation. Par exemple, vous pouvez installer des applications spécifiques, créer une stratégie de mot de passe, installer une connexion VPN, etc.

Les utilisateurs avec leurs propres appareils personnels peuvent ne pas vouloir inscrire leurs appareils ou être gérés par Intune et les stratégies de votre organisation. Toutefois, vous devez toujours protéger les ressources et les données de votre organisation. Dans ce scénario, vous pouvez protéger vos applications à l’aide de la gestion des applications mobiles. Par exemple, vous pouvez utiliser une stratégie GAM qui exige qu’un utilisateur entre un code confidentiel lors de l’accès à SharePoint sur l’appareil.

Vous allez également déterminer comment gérer les appareils personnels et les appareils appartenant à l’organisation. Vous souhaiterez peut-être traiter les appareils différemment, en fonction de leurs utilisations.

## <a name="identity-and-device-access-configurations"></a>Configurations des identités et de l’accès aux appareils

Microsoft fournit un ensemble de configurations pour [l’accès aux identités et aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md) afin de garantir une main-d’œuvre sécurisée et productive. Ces configurations incluent l’utilisation des éléments suivants :

- Stratégies d’accès conditionnel Azure AD
- Microsoft Intune stratégies de conformité des appareils et de protection des applications
- Stratégies de risque utilisateur Azure AD Identity Protection
- Stratégies supplémentaires des applications cloud

Voici un exemple d’application de ces paramètres et stratégies pour valider et restreindre les utilisateurs, leurs appareils et leur utilisation d’applications de productivité locales et cloud comme Microsoft Teams.

![Configurations d’identité et d’accès aux appareils pour les exigences et restrictions sur les utilisateurs, leurs appareils et leur utilisation des applications.](../media/tenant-management-overview/tenant-management-device-app-mgmt-golden-config.png)

Pour l’accès aux appareils et la gestion des applications, utilisez les configurations décrites dans les articles suivants :

- [Conditions préalables](../security/office-365-security/identity-access-prerequisites.md)
- [Stratégies communes pour les identités et l’accès aux appareils](../security/office-365-security/identity-access-policies.md)

## <a name="results-of-step-5"></a>Résultats de l’étape 5

Pour la gestion des appareils et des applications pour votre locataire Microsoft 365, vous avez déterminé les paramètres et stratégies Intune pour valider et restreindre les utilisateurs, leurs appareils et leur utilisation d’applications de productivité locales et cloud.

Voici un exemple de locataire avec Intune gestion des appareils et des applications avec les nouveaux éléments mis en surbrillance.

![Exemple de locataire avec Intune gestion des appareils et des applications.](../media/tenant-management-overview/tenant-management-tenant-build-step5.png)

Dans cette illustration, le locataire a :

- Appareils appartenant à l’organisation inscrits dans Intune.
- Intune stratégies d’appareil et d’application pour les appareils inscrits et personnels.

## <a name="ongoing-maintenance-for-device-and-app-management"></a>Maintenance en cours pour la gestion des appareils et des applications

De façon continue, vous devrez peut-être : 

- Gérer l’inscription des appareils.
- Modifiez vos paramètres et stratégies pour des applications, des appareils et des exigences de sécurité supplémentaires.
