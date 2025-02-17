---
title: Étape 3. Configurer des stratégies de conformité pour des appareils avec Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Create compliance policies
- Intune device compliance policy
manager: dougeby
audience: ITPro
description: Découvrez comment créer des stratégies de conformité d’appareil qui spécifient la configuration minimale requise pour qu’un appareil accède à votre environnement.
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: high
ms.collection:
- highpri
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
keywords: ''
ms.openlocfilehash: 89f5e55da3c53e89a8b9807788da848715e55384
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67985562"
---
# <a name="step-3-set-up-compliance-policies-for-devices-with-intune"></a>Étape 3. Configurer des stratégies de conformité pour des appareils avec Intune

L’inscription d’appareils à Intune vous permet d’obtenir une sécurité et un contrôle encore plus importants des données dans votre environnement. [Étape 2. Inscrire les appareils dans Intune](manage-devices-with-intune-enroll.md) explique comment réaliser cette opération à l'aide d'Intune. Cet article traite de l’étape suivante qui consiste à configurer les stratégies de conformité des appareils. 

![Étapes de gestion des appareils](../media/devices/intune-mdm-step-2.png#lightbox)

Vous souhaitez vous assurer que les appareils qui accèdent à vos applications et données répondent à la configuration minimale, par exemple, qu’ils sont protégés par mot de passe ou par code confidentiel et que le système d’exploitation est à jour. Les stratégies de conformité sont le moyen de définir la configuration minimale que les appareils doivent respecter. Microsoft Endpoint Manager utilise ces stratégies de conformité pour marquer un appareil comme conforme ou non conforme. Ce statut binaire est transmis à Azure AD qui peut utiliser cet état dans les règles d’accès conditionnel pour autoriser ou empêcher un appareil d’accéder aux ressources. 

## <a name="configuring-device-compliance-policies"></a>Configuration des stratégies de conformité des appareils

Ces instructions sont étroitement coordonnées avec les [Stratégies d’accès aux appareils et aux identités de confiance zéro](../security/office-365-security/microsoft-365-policies-configurations.md) recommandées.

Cette illustration met en évidence l’endroit où le travail de définition des stratégies de conformité s’inscrit dans l’ensemble des stratégies de confiance zéro recommandé. 

[![Stratégies d’accès aux appareils et aux identités de confiance zéro](../media/devices/identity-device-define-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-define-compliance.png)

Dans cette illustration, la définition de stratégies de conformité des appareils est une dépendance pour atteindre le niveau de protection recommandé dans l’infrastructure de confiance zéro. 

Pour configurer les stratégies de conformité des appareils, utilisez les recommandations et les paramètres recommandés dans les [Stratégies d’accès aux appareils et aux identités de confiance zéro](../security/office-365-security/microsoft-365-policies-configurations.md). Le tableau ci-dessous est directement lié aux instructions de configuration de ces stratégies dans Intune, y compris les paramètres recommandés pour chaque plateforme.


|Stratégies |Informations supplémentaires  |Licences |
|---------|---------|---------|
|[Définir des stratégies de conformité des appareils ](../security/office-365-security/identity-access-policies.md#define-device-compliance-policies)   |  Une stratégie pour chaque plateforme       |  Microsoft 365 E3 ou E5       |
|  |         |         |

## <a name="next-steps"></a>Prochaines étapes

Accédez à [l’Étape 4. Exiger des appareils sains et conformes](manage-devices-with-intune-require-compliance.md) pour obtenir des instructions sur la création de la règle d’accès conditionnel dans Azure AD.