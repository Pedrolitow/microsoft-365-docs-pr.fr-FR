---
title: Étape 1. Implémenter des stratégies de protection des applications
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: dougeby
audience: ITPro
ms.topic: article
description: Configurez la protection des applications mobiles avec des stratégies de protection des applications (APP) pour empêcher la copie et le collage de données d’entreprise spécifiées dans d’autres applications.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- Intune App Protection policies
- APP
- mobile application management
- MAM
- set up mobile ap protection
ms.custom: ''
keywords: ''
ms.openlocfilehash: 8e458dd52121d6c7686798db85c8729ceaba9d1c
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/30/2021
ms.locfileid: "61643819"
---
# <a name="step-1-implement-app-protection-policies"></a>Étape 1. Implémenter des stratégies de protection des applications

Les stratégies Intune App Protection (APP), parfois appelées Gestion des applications mobiles (MAM), protègent les données d’entreprise même si un appareil proprement dit n’est pas géré. Cela vous permet d’activer les appareils BYO (Apportez votre propre appareil) et personnels au travail où les utilisateurs peuvent être peu enclins à « inscrire » leur appareil dans la gestion. Les stratégies de protection des applications garantissent que les données d’entreprise dans les applications que vous spécifiez ne peuvent pas être copiées et collées dans d’autres applications sur l’appareil.

![Étapes de création de stratégies de protection des applications](../media/devices/intune-app-steps.png#lightbox)

Dans cette illustration :
- Avec APP, Intune crée un mur entre les données de votre organisation et vos données personnelles. Les stratégies de protection des applications définissent les applications autorisées à accéder à vos données.
- Si un utilisateur se connecte avec ses informations d’identification de l’organisation, Intune applique une stratégie au niveau de la couche de l’application pour empêcher la copie et le collage des données de votre organisation dans des applications personnelles et exiger l’accès par PIN à ces données.
- Après avoir créé une stratégie de protection des applications, vous appliquez la protection des données avec une stratégie d’accès conditionnel. 

Cette configuration augmente considérablement votre posture de sécurité sans aucun impact sur l’expérience utilisateur.  Les employés peuvent utiliser des applications telles que Office et Microsoft Teams, qu’ils connaissent et aiment, tout en protégeant les données contenues dans les applications et les appareils au sein de votre organisation.

Si vous avez des applications métier personnalisées qui nécessitent une protection, vous pouvez actuellement utiliser l’outil de création de package de restrictions d’application pour activer l’application avec ces applications. Vous pouvez également intégrer à l’aide du Kit de développement logiciel (SDK) Intune App. Lorsque des stratégies de protection des applications sont appliquées à votre application, elle peut être gérée par Intune et elle est reconnue par Intune en tant qu’application gérée. Pour plus d’informations sur la protection de vos applications métier à l’aide d’Intune, voir [Préparer les applications pour la gestion des applications mobiles avec Microsoft Intune](/mem/intune/developer/apps-prepare-mobile-application-management).

## <a name="configuring-mobile-app-protection"></a>Configuration de la protection des applications mobiles

Ces instructions sont étroitement coordonnées avec les [Stratégies d’accès aux appareils et aux identités Confiance zéro recommandées](../security/office-365-security/microsoft-365-policies-configurations.md). Après avoir créé les stratégies de protection des applications mobiles dans Intune, travaillez avec l’équipe chargée de l’identité pour configurer les stratégies d’accès conditionnel dans Azure AD qui appliquent la protection des applications mobiles. 

Cette illustration met en évidence les deux stratégies (également décrites dans le tableau ci-dessous).

[![Stratégies d’accès aux appareils et aux identités de Confiance zéro](../media/devices/identity-device-starting-point.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-starting-point.png)

Pour configurer ces stratégies, utilisez les instructions et les paramètres recommandés dans les [Stratégies d’accès aux appareils et aux identités de Confiance zéro](../security/office-365-security/microsoft-365-policies-configurations.md). Le tableau ci-dessous est directement lié aux instructions de configuration de ces stratégies dans Intune et Azure AD.


|Étape  |Stratégies  |Informations supplémentaires  |Licences  |
|---------|---------|---------|---------|
|1   |  [Appliquer la protection des données des stratégies de protection des applications (APP)](../security/office-365-security/identity-access-policies.md#apply-app-data-protection-policies)       | Une stratégie Intune App Protection par plateforme (Windows, iOS/iPadOS, Android).        | Microsoft 365 E3 ou E5        |
|2     | [Exiger la protection des applications et des applications approuvées ](../security/office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection)       |  Applique la protection des applications mobiles pour les téléphones et les tablettes à l’aide d’iOS, iPadOS ou Android.   |  Microsoft 365 E3 ou E5       |
| | | | |

## <a name="next-steps"></a>Prochaines étapes

Allez à [Étape 2. Inscrire des appareils dans la gestion avec Intune](manage-devices-with-intune-enroll.md). 