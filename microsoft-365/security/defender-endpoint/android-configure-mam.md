---
title: Configurer Microsoft Defender pour point de terminaison signaux de risque à l’aide de stratégies de protection des applications (MAM)
description: Décrit comment configurer Microsoft Defender pour point de terminaison signaux de risque à l’aide de stratégies App Protection
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mde, android, configuration, MAM, stratégies de protection des applications, application managée
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
ms.openlocfilehash: 9918763732fa828f17b395a3f96b24e8fbed46f2
ms.sourcegitcommit: d7193ee954c01c4172e228d25b941026c8d92d30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2022
ms.locfileid: "67174979"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>Configurer Microsoft Defender pour point de terminaison signaux de risque à l’aide de stratégies de protection des applications (MAM)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Microsoft Defender pour point de terminaison sur Android, qui protège déjà les utilisateurs d’entreprise dans les scénarios de Gestion des appareils mobiles (GPM), étend désormais la prise en charge de la gestion des applications mobiles (GAM) pour les appareils qui ne sont pas inscrits à l’aide de Intune gestion des appareils mobiles (GPM). Il étend également ce support aux clients qui utilisent d’autres solutions de gestion de la mobilité d’entreprise, tout en continuant à utiliser Intune pour la gestion des applications mobiles (MAM). Cette fonctionnalité vous permet de gérer et de protéger les données de votre organisation au sein d’une application.

Microsoft Defender pour point de terminaison sur les informations sur les menaces Android est appliquée par Intune stratégies de protection des applications pour protéger ces applications. Les stratégies de protection des applications (APP) sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une application managée a des stratégies de protection des applications qui lui sont appliquées et peuvent être gérées par Intune.  

Microsoft Defender pour point de terminaison sur Android prend en charge les deux configurations de MAM
- **Intune GPM + GAM** : les administrateurs informatiques peuvent uniquement gérer les applications à l’aide de stratégies de protection des applications sur les appareils inscrits auprès de Intune gestion des appareils mobiles (GPM).
- Gestion des applications mobiles **sans inscription d’appareil** : la gestion des applications mobiles sans inscription d’appareil, ou MAM-WE, permet aux administrateurs informatiques de gérer les applications à l’aide de stratégies [de protection](/mem/intune/apps/app-protection-policy) des applications sur les appareils qui ne sont pas inscrits auprès de Intune GPM. Cette disposition signifie que les applications peuvent être gérées par Intune sur les appareils inscrits auprès de fournisseurs EMM tiers. Pour gérer les applications dans ces deux configurations, les clients doivent utiliser Intune dans le Centre d’administration [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

Pour activer cette fonctionnalité, un administrateur doit configurer la connexion entre Microsoft Defender pour point de terminaison et Intune, créer la stratégie de protection des applications et appliquer la stratégie sur les appareils et applications ciblés. 
 
Les utilisateurs finaux doivent également prendre des mesures pour installer Microsoft Defender pour point de terminaison sur leur appareil et activer le flux d’intégration.


## <a name="admin-prerequisites"></a>Administration prérequis

- **Vérifier que le connecteur Microsoft Defender pour Endpoint-Intune est activé**

  a. Allez à security.microsoft.com. 

  b. Sélectionnez **Paramètres > points de terminaison> fonctionnalités avancées > Microsoft Intune la connexion** est activée.

  c. Si la connexion n’est pas activée, sélectionnez le bouton bascule pour l’activer, puis **sélectionnez Enregistrer les préférences**.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Section Fonctionnalités avancées dans le portail Microsoft 365 Defender" lightbox="images/enable-intune-connection.png":::

  d. Accédez à **Microsoft Endpoint Manager (Intune)** et vérifiez si Microsoft Defender pour Endpoint-Intune connecteur est activé.

  :::image type="content" source="images/validate-intune-connector.png" alt-text="Volet d’état intune-connecteur dans le portail Microsoft 365 Defender" lightbox="images/validate-intune-connector.png":::

- **Activer Microsoft Defender pour point de terminaison sur le connecteur Android pour la stratégie app protection (APP)**
  
  Configurez le connecteur sur Intune Microsoft Endpoint Manager pour les stratégies de Protection d'applications :

  a. Accédez à **l'> Microsoft Defender pour point de terminaison d’administration des locataires > connecteurs et jetons**.

  b. Activez le bouton bascule pour la stratégie de protection des applications pour Android (comme illustré dans la capture d’écran suivante).

  c. Sélectionnez **Enregistrer**.

  :::image type="content" source="images/app-settings.png" alt-text="Volet Paramètres de l’application dans le portail Microsoft 365 Defender" lightbox="images/app-settings.png":::

- **Créer une stratégie de protection des applications** 
 
Bloquez l’accès ou réinitez les données d’une application managée en fonction de Microsoft Defender pour point de terminaison signaux de risque en créant une stratégie de protection des applications.
Microsoft Defender pour point de terminaison peut être configuré pour envoyer des signaux de menace à utiliser dans les stratégies de protection des applications (APP, également appelée GAM). Avec cette fonctionnalité, vous pouvez utiliser Microsoft Defender pour point de terminaison pour protéger les applications gérées.

1. Créer une stratégie <br>
Les stratégies de protection des applications (APP) sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une stratégie peut être une règle qui est appliquée lorsque l’utilisateur tente d’accéder à des données « d’entreprise » ou de les déplacer, ou s’il tente un ensemble d’actions interdites ou surveillées lorsqu’il se trouve dans l’application. 

:::image type="content" source="images/create-policy.png" alt-text="Onglet Créer une stratégie dans la page Protection d'applications stratégies dans le portail Microsoft 365 Defender" lightbox="images/create-policy.png":::

2. Ajouter des applications <br>
    a. Choisissez comment appliquer cette stratégie aux applications sur différents appareils. Ajoutez ensuite au moins une application. <br>
    Utilisez cette option pour spécifier si cette stratégie s’applique aux appareils non gérés. Dans Android, vous pouvez spécifier que la stratégie s’applique aux appareils Android Enterprise, Device Administration ou Non managés. Vous pouvez également choisir de cibler votre stratégie sur des applications sur des appareils de n’importe quel état de gestion.
Étant donné que la gestion des applications mobiles ne nécessite pas de gestion des appareils, vous pouvez protéger les données d’entreprise à la fois sur les appareils gérés et non gérés. La gestion est centrée autour de l’identité de l’utilisateur, ce qui supprime la nécessité de gérer les appareils. Les entreprises peuvent utiliser des stratégies de protection des applications avec ou sans GPM en même temps. Considérons, par exemple, un employé qui utilise à la fois un téléphone fourni par l’entreprise et sa propre tablette personnelle. Le téléphone de l’entreprise est inscrit dans la gestion des appareils mobiles (MAM) et protégé par des stratégies de protection des applications, tandis que l’appareil personnel est protégé uniquement par des stratégies de protection des applications.

    b. Sélectionner des applications<br>
    Une application gérée est une application à laquelle sont appliquées des stratégies de protection des applications et qui peut être gérée par Intune. Toute application qui a été intégrée au [SDK Intune](/mem/intune/developer/app-sdk) ou encapsulée par le [Intune App Wrapping Tool](/mem/intune/developer/apps-prepare-mobile-application-management) peut être gérée à l’aide de Intune stratégies de protection des applications. Voir la liste officielle des [applications protégées Microsoft Intune](/mem/intune/apps/apps-supported-intune-apps) qui ont été construites à l'aide de ces outils et sont disponibles pour un usage public.

    *Exemple : Outlook en tant qu’application managée*

  :::image type="content" source="images/managed-app.png" alt-text="Volet Applications publiques dans le portail Microsoft 365 Defender" lightbox="images/managed-app.png":::


 3. Définissez les exigences de sécurité de connexion pour votre stratégie de protection. <br>
Sélectionnez **Paramètre > niveau maximal autorisé de menace d’appareil** dans **Les conditions de l’appareil** et entrez une valeur. Sélectionnez ensuite **Action : « Bloquer l’accès ».** Microsoft Defender pour point de terminaison sur Android partage ce niveau de menace d’appareil.

  :::image type="content" source="images/conditional-launch.png" alt-text="Volet Conditions de l’appareil dans le portail Microsoft 365 Defender" lightbox="images/conditional-launch.png":::
  
- **Affectez des groupes d’utilisateurs pour lesquels la stratégie doit être appliquée.**<br>
  Sélectionnez **Groupes inclus**. Ajoutez ensuite les groupes appropriés. 

    :::image type="content" source="images/assignment.png" alt-text="Volet Groupes inclus dans le portail Microsoft 365 Defender" lightbox="images/assignment.png":::


## <a name="end-user-prerequisites"></a>Prérequis de l’utilisateur final
- L’application broker doit être installée
    - Portail d’entreprise Intune
    
- Les utilisateurs disposent des licences requises pour l’application managée et l’application est installée

### <a name="end-user-onboarding"></a>Intégration des utilisateurs finaux 

1. Connectez-vous à une application managée, par exemple Outlook. L’appareil est inscrit et la stratégie de protection des applications est synchronisée avec l’appareil. La stratégie de protection des applications reconnaît l’état d’intégrité de l’appareil.  

2. Cliquez sur **Continuer**. Un écran est présenté qui recommande le téléchargement et la configuration de Microsoft Defender pour point de terminaison sur l’application Android.

3. Sélectionnez **Télécharger**. Vous serez redirigé vers l’App Store (Google Play). 

4.  Installez l’application Microsoft Defender pour point de terminaison (Mobile) et lancez l’écran d’intégration de l’application managée.

  :::image type="content" source="images/download-mde.png" alt-text="Pages d’illustration qui contiennent la procédure de téléchargement de MDE et de lancement de l’écran d’intégration d’application" lightbox="images/download-mde.png":::
  

5.  Cliquez sur **Continuer > lancer**. Le flux d’intégration/activation de l’application Microsoft Defender pour point de terminaison est lancé. Suivez les étapes pour terminer l’intégration. Vous serez automatiquement redirigé vers l’écran d’intégration de l’application managée, qui indique maintenant que l’appareil est sain.

6. Sélectionnez **Continuer** à vous connecter à l’application managée. 

### <a name="configure-privacy-controls"></a>Configurer les contrôles de confidentialité 
Les administrateurs peuvent utiliser les étapes suivantes pour activer la confidentialité et ne pas collecter le nom de domaine, les détails de l’application et les informations réseau dans le cadre du rapport d’alerte pour les menaces correspondantes.

1. Dans le Centre d’administration Microsoft Endpoint Manager, accédez aux **stratégies de configuration des applications > app > Ajouter des applications managées >**.

2. Donner à la stratégie un **nom**.

3. Sous Sélectionner les applications publiques, choisissez **Microsoft Defender pour point de terminaison** comme application cible.

4. Dans la page Paramètres, sous Paramètres de configuration générale, ajoutez **DefenderExcludeURLInReport**, **DefenderExcludeAppInReport** comme clés et valeur true.

5. Affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur false.

6. Examinez et créez la stratégie.

## <a name="optional-permissions"></a>Autorisations facultatives 

Microsoft Defender pour point de terminaison sur Android active les autorisations facultatives dans le flux d’intégration. Actuellement, les autorisations requises par MDE sont obligatoires dans le flux d’intégration. Avec cette fonctionnalité, l’administrateur peut déployer MDE sur des appareils Android avec des stratégies GAM sans appliquer les autorisations VPN et d’accessibilité obligatoires lors de l’intégration. Les utilisateurs finaux peuvent intégrer l’application sans les autorisations obligatoires et passer en revue ultérieurement ces autorisations. 

### <a name="configure-optional-permission"></a>Configurer l’autorisation facultative

Utilisez les étapes suivantes pour activer les autorisations facultatives pour les appareils.

1. Dans le Centre d’administration Microsoft Endpoint Manager, accédez aux **stratégies de configuration des applications > app > Ajouter des applications managées >**.

2. Donner à la stratégie un **nom**.

3. Sélectionnez **Microsoft Defender pour point de terminaison*** dans les applications publiques.

4. Dans la page Paramètres, **sélectionnez Utiliser le concepteur de configuration** et ajoutez **DefenderOptionalVPN** ou **DefenderOptionalAccessibility** , ou **les deux** comme type clé et valeur booléen. 

5. Pour activer les autorisations facultatives, entrez la valeur **true** et affectez cette stratégie aux utilisateurs. Par défaut, cette valeur est définie sur false.
Pour les utilisateurs avec la clé définie comme true, les utilisateurs pourront intégrer l’application sans accorder ces autorisations.

6. Sélectionnez **Suivant** et affectez ce profil aux appareils/utilisateurs ciblés.

### <a name="user-flow"></a>Flux utilisateur 

Les utilisateurs peuvent installer et ouvrir l’application pour démarrer le processus d’intégration.

1. Si un administrateur dispose d’autorisations facultatives de configuration, les utilisateurs peuvent choisir d’ignorer l’autorisation VPN ou d’accessibilité ou les deux et d’effectuer l’intégration.
2. Même si l’utilisateur a ignoré ces autorisations, l’appareil sera en mesure d’intégrer et une pulsation sera envoyée.
3. Étant donné que les autorisations sont désactivées, la protection web n’est pas active. Elle sera partiellement active si l’une des autorisations est accordée.
4. Par la suite, les utilisateurs peuvent activer la protection web à partir de l’application. Cela permet d’installer la configuration VPN sur l’appareil.

>[!NOTE] 
> Le paramètre Autorisations facultatives est différent du paramètre Désactiver la protection web. Les autorisations facultatives permettent uniquement d’ignorer les autorisations pendant l’intégration, mais l’utilisateur final peut les examiner et les activer ultérieurement, tandis que la désactivation de la protection web permet aux utilisateurs d’intégrer l’application Microsoft Defender pour point de terminaison sans protection web. Il ne peut pas être activé ultérieurement.

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md)
- [Déployer Microsoft Defender pour point de terminaison Android via Microsoft Intune](android-intune.md)
