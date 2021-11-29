---
title: Déployer Microsoft Defender pour le point de terminaison sur les fonctionnalités iOS
description: Décrit comment déployer Microsoft Defender pour Endpoint sur des appareils iOS non inscrits.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, ios, configurer, fonctionnalités, ios
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8e50139b1ef17871762e12ccd4aec1e90071033b
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2021
ms.locfileid: "61218153"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>Déployer Microsoft Defender pour endpoint sur des appareils iOS non inscrits

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Defender pour le point de terminaison sur iOS utilise un VPN pour fournir la fonctionnalité de protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local/en boucle autonome qui ne prend pas le trafic en dehors de l’appareil.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>Configurer Microsoft Defender pour les signaux de risque de point de terminaison dans la stratégie de protection des applications (MAM)

Microsoft Defender pour endpoint sur Android, qui protège déjà les utilisateurs d’entreprise sur les scénarios de gestion des périphériques mobiles (MDM), étend désormais la prise en charge de la gestion des applications mobiles (MAM) pour les appareils qui ne sont pas inscrits à l’aide de la gestion des périphériques mobiles (MDM) Intune. Il étend également cette prise en charge aux clients qui utilisent d’autres solutions de gestion de la mobilité d’entreprise, tout en utilisant Intune pour la gestion des applications mobiles (MAM). Cette fonctionnalité vous permet de gérer et de protéger les données de votre organisation au sein d’une application.

Les informations sur les menaces Microsoft Defender pour Endpoint sur Android sont utilisées par les stratégies intune App Protection pour protéger ces applications. Les stratégies de protection des applications (APP) sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une application gérée dispose de stratégies de protection des applications qui lui sont appliquées et peut être gérée par Intune.  

Microsoft Defender pour point de terminaison sur Android prend en charge les deux configurations de MAM
- **Intune MDM + MAM**: les administrateurs informatiques peuvent uniquement gérer les applications à l’aide des stratégies de protection des applications sur les appareils inscrits auprès de la gestion des périphériques mobiles Intune.
- **MAM sans** inscription d’appareils : MAM sans inscription d’appareil, ou MAM-WE, permet aux administrateurs informatiques de gérer les applications à l’aide de stratégies de [protection](/mem/intune/app/app-protection-policy) des applications sur les appareils non inscrits auprès de la gestion des appareils mobiles Intune. Cela signifie que les applications peuvent être gérées par Intune sur des appareils inscrits auprès de fournisseurs EMM tiers. Pour gérer les applications à l’aide des deux configurations ci-dessus, les clients doivent utiliser Intune [dans Microsoft Endpoint Manager’administration centrale](https://go.microsoft.com/fwlink/?linkid=2109431)

Pour activer cette fonctionnalité, un administrateur doit configurer la connexion entre Microsoft Defender pour Endpoint et Intune, créer la stratégie de protection des applications et appliquer la stratégie sur les appareils et applications ciblés. 
 
Les utilisateurs finaux doivent également prendre des mesures pour installer Microsoft Defender pour le point de terminaison sur leur appareil et activer le flux d’intégration.

### <a name="pre-requisites"></a>Conditions préalables

1. **Vérifiez que le connecteur est activé.** <br> Sur la console de  [sécurité unifiée,](https://security.microsoft.com)Paramètres points de terminaison fonctionnalités avancées et assurez-vous que Microsoft Intune  >    >   **connexion** est activée.

  ![Image de Defender pour point de terminaison -Connecteur Intune](images/enable-intune-connection.png)
  
2. **Vérifiez que le connecteur est activé sur le portail Intune.** <br> Dans [le Centre d’administration microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)allez à **Endpoint Security** Microsoft Defender for Endpoint et assurez-vous que l’état de  >   connexion est activé.

  ![Paramètres de l’application](images/app-settings.png)

### <a name="create-an-app-protection-policy"></a>Créer une stratégie de protection des applications
 
Bloquez l’accès ou effacez les données d’une application gérée en fonction des signaux de risque de Microsoft Defender for Endpoint en créant une stratégie de protection des applications.
Microsoft Defender pour le point de terminaison peut être configuré pour envoyer des signaux de menace à utiliser dans les stratégies de protection des applications (APP, également appelée MAM). Avec cette fonctionnalité, vous pouvez utiliser Microsoft Defender pour point de terminaison pour protéger les applications gérées.

1. Créer une stratégie <br>
Les stratégies de protection des applications (APP) sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une stratégie peut être une règle qui est appliquée lorsque l’utilisateur tente d’accéder à des données « d’entreprise » ou de les déplacer, ou s’il tente un ensemble d’actions interdites ou surveillées lorsqu’il se trouve dans l’application. 

![Image de création de stratégie](images/create-policy.png)

2. Ajouter des applications <br>
    a. Choisissez la façon dont vous souhaitez appliquer cette stratégie aux applications sur différents appareils. Ajoutez ensuite au moins une application. <br>
    Utilisez cette option pour spécifier si cette stratégie s’applique aux appareils non utilisés. Vous pouvez également choisir de cibler votre stratégie sur les applications sur les appareils de n’importe quel état de gestion.
Étant donné que la gestion des applications mobiles ne nécessite pas de gestion des appareils, vous pouvez protéger les données d’entreprise à la fois sur les appareils gérés et non gérés. La gestion est centrée autour de l’identité de l’utilisateur, ce qui supprime la nécessité de gérer les appareils. Les entreprises peuvent utiliser des stratégies de protection des applications avec ou sans mdm en même temps. Considérons, par exemple, un employé qui utilise à la fois un téléphone fourni par l’entreprise et sa propre tablette personnelle. Le téléphone de l’entreprise est inscrit dans la gestion des périphériques de gestion des périphériques multi-appareils et protégé par les stratégies de protection des applications, tandis que l’appareil personnel est protégé uniquement par les stratégies de protection des applications.

    b. Sélectionner des applications<br>
    Une application gérée est une application à laquelle des stratégies de protection d’application sont appliquées et pouvant être gérée par Intune. Toute application qui a été intégrée au [SDK Intune](/mem/intune/developer/app-sdk) ou enveloppée par le App Wrapping Tool [Intune](/mem/intune/developer/apps-prepare-mobile-application-management) peut être gérée à l’aide de stratégies de protection des applications Intune. Voir la liste officielle des [applications protégées Microsoft Intune](/mem/intune/apps/apps-supported-intune-apps) qui ont été construites à l'aide de ces outils et sont disponibles pour un usage public.

    *Exemple : Outlook en tant qu’application gérée*

    ![Image Outlook en tant qu’application gérée](images/managed-app.png)

 3. Définissez les exigences de sécurité de la signature pour votre stratégie de protection. <br>
Sélectionnez **Paramètre > niveau de menace** d’appareil autorisé maximum dans Les **conditions** d’appareil et entrez une valeur. Ensuite,  **sélectionnez Action : « Bloquer l’accès**». Microsoft Defender pour point de terminaison sur Android partage ce niveau de menace d’appareil.

    ![Image du lancement conditionnel](images/conditional-launch.png)

4. Affecter des groupes d’utilisateurs auxquels la stratégie doit être appliquée.<br>
  Sélectionnez **Groupes inclus.** Ajoutez ensuite les groupes appropriés. 


Pour plus d’informations sur la stratégie de protection des applications ou de gestion des applications, voir les paramètres de stratégie de protection des [applications iOS.](/mem/intune/apps/app-protection-policy-settings-ios)

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Déployer Microsoft Defender pour le point de terminaison pour MAM ou sur des appareils non inscrits

Microsoft Defender pour le point de terminaison sur iOS active le scénario de stratégie de protection des applications et est disponible dans l’App Store d’Apple.

Lorsque des stratégies de protection des applications sont configurées pour que les applications incluent les signaux de risque de l’appareil de Microsoft Defender pour le point de terminaison, les utilisateurs sont redirigés vers l’installation de Microsoft Defender pour le point de terminaison lors de l’utilisation de ces applications. Les utilisateurs peuvent également installer la dernière version de l’application directement à partir de l’App Store d’Apple.
