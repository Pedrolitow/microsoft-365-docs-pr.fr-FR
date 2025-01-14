---
title: Étape 4. Exiger des appareils sains et conformes avec Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Conditional access policy
- Microsoft Intune
- Intune device management
manager: dougeby
audience: ITPro
description: Créez une stratégie d’accès conditionnel dans Azure AD pour exiger des appareils conformes, en conservant la sécurité des données d’entreprise lorsque les utilisateurs travaillent à partir de n’importe quel appareil dans n’importe quel emplacement.
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: high
ms.collection:
- highpri
- Conditional access policy
- Microsoft Intune
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
ms.openlocfilehash: 1425f01b5cd2cf2c50cfa1f31acb358cda871e39
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67986111"
---
# <a name="step-4-require-healthy-and-compliant-devices-with-intune"></a>Étape 4. Exiger des appareils sains et conformes avec Intune

L’accès conditionnel permet une vérification supplémentaire de l’état de l’appareil avant d’autoriser l’accès à un service. L’accès conditionnel ne fonctionne que si vous spécifiez des conditions. À [l’étape 3. Configurer des stratégies de conformité](manage-devices-with-intune-compliance-policies.md). Vous avez défini des stratégies de conformité qui spécifient les exigences minimales qu’un appareil doit respecter pour accéder à votre environnement. Dans cet article, vous allez créer la stratégie d’accès conditionnel correspondante dans Azure AD pour exiger des appareils conformes. Cela permet de sécuriser vos données d’entreprise tout en donnant aux utilisateurs la possibilité de travailler depuis n’importe quel appareil et quelque soit la localisation.

Après la configuration des stratégies de conformité des appareils et leur affectation à des groupes d’utilisateurs, Intune informe Azure AD si un appareil est conforme ou non. Pour utiliser cet état comme condition d’accès, vous devez travailler avec votre administrateur Azure AD pour créer une règle d’accès conditionnel afin d’exiger des PC et des appareils mobiles conformes.


![Étapes de gestion des appareils](../media/devices/intune-mdm-step-3.png#lightbox)

L’ensemble recommandé de règles d’accès aux identités et aux appareils avec confiance zéro inclut cette règle. Consultez [Exiger des PC et des appareils mobiles conformes](../security/office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices), comme illustré ci-dessous.


[![Stratégies d’accès aux appareils et aux identités de confiance zéro](../media/devices/identity-device-require-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-require-compliance.png)



Veillez à :
- Coordonner les groupes d’utilisateurs affectés à vos stratégies de conformité avec les groupes d’utilisateurs affectés à la stratégie d’accès conditionnel.
- Testez vos stratégies d’accès conditionnel à l’aide des fonctionnalités What If et Audit Mode avant d’attribuer entièrement la stratégie d’accès conditionnel. Cela vous permet de comprendre les résultats de la stratégie.
- Définissez une période de grâce en respectant la confidentialité des données et/ou de l’application accessibles. 
- Assurez-vous que vos stratégies de conformité n’interfèrent pas avec les exigences réglementaires ou autres exigences de conformité. 
- Comprendre les intervalles d’archivage de l’appareil pour les stratégies de conformité.
- Évitez les conflits entre les stratégies de conformité et les profils de configuration. Comprenez les résultats si vous faites ce choix.

Pour résoudre les problèmes de profils d’appareil dans Intune, y compris les conflits entre les stratégies, consultez [Questions et réponses fréquentes avec les stratégies et les profils d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-troubleshoot).

Remarque : si vous souhaitez commencer par exiger des PC conformes, mais pas des appareils mobiles, consultez [Exiger des PC conformes (mais pas des téléphones et des tablettes)](../security/office-365-security/identity-access-policies.md) 

## <a name="next-steps"></a>Prochaines étapes

Allez à l’étape [5. Déployer des profils d’appareil dans Microsoft Intune](manage-devices-with-intune-configuration-profiles.md)
