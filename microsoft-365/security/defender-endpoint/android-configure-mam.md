---
title: Configurer Microsoft Defender pour les signaux de risque de point de terminaison à l’aide des stratégies de protection des applications (MAM)
description: Décrit comment configurer Microsoft Defender pour les signaux de risque de point de terminaison à l’aide des stratégies de Protection des applications
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, mde, android, configuration, MAM, stratégies de protection des applications, application gérée
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: shthota
author: shthota
manager: dansimp
ms.localizationpriority: medium
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5d74fd2af61ee4047dd2728c28e6093efbc58ce9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471294"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>Configurer Microsoft Defender pour les signaux de risque de point de terminaison à l’aide des stratégies de protection des applications (MAM)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Microsoft Defender pour endpoint sur Android, qui protège déjà les utilisateurs d’entreprise sur les scénarios de gestion des périphériques mobiles (MDM), étend désormais la prise en charge de la gestion des applications mobiles (MAM) pour les appareils qui ne sont pas inscrits à l’aide de la gestion des périphériques mobiles (MDM) Intune. Il étend également cette prise en charge aux clients qui utilisent d’autres solutions de gestion de la mobilité d’entreprise, tout en utilisant Intune pour la gestion des applications mobiles (MAM). Cette fonctionnalité vous permet de gérer et de protéger les données de votre organisation au sein d’une application.

Les informations sur les menaces Microsoft Defender pour endpoint sur Android sont appliquées par les stratégies de protection des applications Intune pour protéger ces applications. Les stratégies de protection des applications (APP) sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une application gérée dispose de stratégies de protection des applications qui lui sont appliquées et peut être gérée par Intune.  

Microsoft Defender pour point de terminaison sur Android prend en charge les deux configurations de MAM
- **Intune MDM + MAM** : les administrateurs informatiques peuvent uniquement gérer les applications à l’aide des stratégies de protection des applications sur les appareils inscrits auprès de la gestion des périphériques mobiles Intune.
- **MAM sans** inscription d’appareils : MAM sans inscription d’appareil, ou MAM-WE, permet aux administrateurs informatiques de gérer les applications à l’aide de stratégies de [protection](/mem/intune/app/app-protection-policy) des applications sur les appareils non inscrits auprès de la gestion des appareils mobiles Intune. Cette mise en service signifie que les applications peuvent être gérées par Intune sur les appareils inscrits auprès de fournisseurs EMM tiers. Pour gérer les applications à l’aide des deux configurations ci-dessus, les clients doivent utiliser Intune [dans Microsoft Endpoint Manager’administration.](https://go.microsoft.com/fwlink/?linkid=2109431)

Pour activer cette fonctionnalité, un administrateur doit configurer la connexion entre Microsoft Defender pour Endpoint et Intune, créer la stratégie de protection des applications et appliquer la stratégie sur les appareils et applications ciblés. 
 
Les utilisateurs finaux doivent également prendre des mesures pour installer Microsoft Defender pour le point de terminaison sur leur appareil et activer le flux d’intégration.


## <a name="admin-prerequisites"></a>Conditions préalables pour l’administrateur

- **Vérifier que le connecteur Microsoft Defender pour Endpoint-Intune est activé**

  a. Go to security.microsoft.com. 

  b. **Sélectionnez Paramètres > points de terminaison> fonctionnalités avancées > Microsoft Intune connexion** est allumée.

  c. Si la connexion n’est pas allumée, sélectionnez le basculement pour l’activer, puis **sélectionnez Enregistrer les préférences**.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Section Fonctionnalités avancées du portail Microsoft 365 Defender web" lightbox="images/enable-intune-connection.png":::

  d. Go to **Microsoft Endpoint Manager (Intune)** and Validate whether Microsoft Defender for Endpoint-Intune connector is enabled.

  :::image type="content" source="images/validate-intune-connector.png" alt-text="Volet d’état intune-connector dans le portail Microsoft 365 Defender client" lightbox="images/validate-intune-connector.png":::

- **Activer Microsoft Defender pour le point de terminaison sur le connecteur Android pour la stratégie de protection des applications (APP)**
  
  Configurez le connecteur sur Intune Microsoft Endpoint Manager stratégies de protection des applications :

  a. Go to **Tenant Administration > Connectors and Tokens > Microsoft Defender for Endpoint**.

  b. Activer le basculement pour la stratégie de protection des applications pour Android (comme indiqué dans la capture d’écran suivante).

  c. Sélectionnez **Enregistrer**.

  :::image type="content" source="images/app-settings.png" alt-text="Volet Paramètres de l’application dans le portail Microsoft 365 Defender applications" lightbox="images/app-settings.png":::

- **Créer une stratégie de protection des applications** 
 
Bloquez l’accès ou effacez les données d’une application gérée en fonction des signaux de risque de Microsoft Defender for Endpoint en créant une stratégie de protection des applications.
Microsoft Defender pour le point de terminaison peut être configuré pour envoyer des signaux de menace à utiliser dans les stratégies de protection des applications (APP, également appelée MAM). Avec cette fonctionnalité, vous pouvez utiliser Microsoft Defender pour point de terminaison pour protéger les applications gérées.

1. Créer une stratégie <br>
Les stratégies de protection des applications (APP) sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une stratégie peut être une règle qui est appliquée lorsque l’utilisateur tente d’accéder à des données « d’entreprise » ou de les déplacer, ou s’il tente un ensemble d’actions interdites ou surveillées lorsqu’il se trouve dans l’application. 

:::image type="content" source="images/create-policy.png" alt-text="Onglet Créer une stratégie dans la page Stratégies de protection des applications du portail Microsoft 365 Defender web" lightbox="images/create-policy.png":::

2. Ajouter des applications <br>
    a. Choisissez la façon dont vous souhaitez appliquer cette stratégie aux applications sur différents appareils. Ajoutez ensuite au moins une application. <br>
    Utilisez cette option pour spécifier si cette stratégie s’applique aux appareils non utilisés. Dans Android, vous pouvez spécifier que la stratégie s’applique aux appareils Android Enterprise, Administrateur d’appareil ou Appareils non utilisés. Vous pouvez également choisir de cibler votre stratégie sur les applications sur les appareils de n’importe quel état de gestion.
Étant donné que la gestion des applications mobiles ne nécessite pas de gestion des appareils, vous pouvez protéger les données d’entreprise à la fois sur les appareils gérés et non gérés. La gestion est centrée autour de l’identité de l’utilisateur, ce qui supprime la nécessité de gérer les appareils. Les entreprises peuvent utiliser des stratégies de protection des applications avec ou sans mdm en même temps. Considérons, par exemple, un employé qui utilise à la fois un téléphone fourni par l’entreprise et sa propre tablette personnelle. Le téléphone de l’entreprise est inscrit dans la gestion des périphériques de gestion des périphériques multi-appareils et protégé par les stratégies de protection des applications, tandis que l’appareil personnel est protégé uniquement par les stratégies de protection des applications.

    b. Sélectionner des applications<br>
    Une application gérée est une application à laquelle sont appliquées des stratégies de protection des applications et qui peut être gérée par Intune. Toute application qui a été intégrée au [SDK Intune](/mem/intune/developer/app-sdk) ou enveloppée par le App Wrapping Tool [Intune](/mem/intune/developer/apps-prepare-mobile-application-management) peut être gérée à l’aide de stratégies de protection des applications Intune. Voir la liste officielle des [applications protégées Microsoft Intune](/mem/intune/apps/apps-supported-intune-apps) qui ont été construites à l'aide de ces outils et sont disponibles pour un usage public.

    *Exemple : Outlook en tant qu’application gérée*

  :::image type="content" source="images/managed-app.png" alt-text="Volet Applications publiques dans le portail Microsoft 365 Defender public" lightbox="images/managed-app.png":::


 3. Définissez les exigences de sécurité de la signature pour votre stratégie de protection. <br>
**Sélectionnez Paramètre > niveau de menace** d’appareil autorisé maximum dans **Les conditions** d’appareil, puis entrez une valeur. Sélectionnez  **Ensuite Action : « Bloquer l’accès** ». Microsoft Defender pour point de terminaison sur Android partage ce niveau de menace d’appareil.

  :::image type="content" source="images/conditional-launch.png" alt-text="Volet Conditions de l’appareil dans le portail Microsoft 365 Defender périphérique" lightbox="images/conditional-launch.png":::
  
- **Affecter des groupes d’utilisateurs auxquels la stratégie doit être appliquée.**<br>
  Sélectionnez **Groupes inclus**. Ajoutez ensuite les groupes appropriés. 

    :::image type="content" source="images/assignment.png" alt-text="Volet Groupes inclus dans le portail Microsoft 365 Defender web" lightbox="images/assignment.png":::


## <a name="end-user-prerequisites"></a>Conditions préalables pour l’utilisateur final
- L’application Broker doit être installée
    - Portail d’entreprise Intune
    
- Les utilisateurs ont les licences requises pour l’application gérée et l’application est installée

### <a name="end-user-onboarding"></a>Intégration de l’utilisateur final 

1. Connectez-vous à une application gérée, par exemple, Outlook. L’appareil est inscrit et la stratégie de protection de l’application est synchronisée avec l’appareil. La stratégie de protection des applications reconnaît l’état d’état d’état de l’appareil.  

2. Cliquez sur **Continuer**. Un écran s’affiche, qui recommande le téléchargement et la configuration de Microsoft Defender pour Endpoint sur l’application Android.

3. Sélectionnez **Télécharger**. Vous serez redirigé vers l’App Store (Google Play). 

4.  Installez l’application Microsoft Defender pour point de terminaison (mobile) et lancez à nouveau l’écran d’intégration de l’application gérée.

  :::image type="content" source="images/download-mde.png" alt-text="Pages d’illustration qui contiennent la procédure de téléchargement de MDE et de lancement de l’écran d’intégration d’application" lightbox="images/download-mde.png":::
  

5.  Cliquez **sur Continuer > lancement**. Le flux d’intégration/activation de l’application Microsoft Defender for Endpoint est lancé. Suivez les étapes pour terminer l’intégration. Vous serez automatiquement redirigé vers l’écran d’intégration d’application gérée, ce qui indique maintenant que l’appareil est sain.

6. **Sélectionnez Continuer** à vous connecter à l’application gérée. 



## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble de Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md)
- [Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune](android-intune.md)
