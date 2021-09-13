---
title: Intégration à l'aide de Microsoft Endpoint Manager
description: Découvrez comment intégrer Microsoft Defender pour le point de terminaison à l’aide de Microsoft Endpoint Manager
keywords: intégration, configuration, déploiement, déploiement, gestionnaire de point de terminaison, Microsoft Defender pour le point de terminaison, création de collection, réponse de détection de point de terminaison, protection nouvelle génération, réduction de la surface d’attaque, gestionnaire de point de terminaison Microsoft
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1e1a598f0a87a4bb0bd7882d2b402c43b276a24f
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59183319"
---
# <a name="onboarding-using-microsoft-endpoint-manager"></a>Intégration à l'aide de Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cet article fait partie du guide de déploiement et agit comme un exemple de méthode d’intégration.

Dans la [rubrique Planification,](deployment-strategy.md) plusieurs méthodes ont été fournies pour intégrer des appareils au service. Cette rubrique traite de l’architecture native du cloud.

![Image de l’architecture native du cloud. ](images/cloud-native-architecture.png)
 *Diagramme des architectures d’environnement*

Bien que Defender pour point de terminaison prend en charge l’intégration de différents points de terminaison et outils, cet article ne les traite pas. Pour plus d’informations sur l’intégration générale à l’aide d’autres outils et méthodes de déploiement pris en charge, voir [vue d’ensemble de l’intégration.](onboarding.md)

[Microsoft Endpoint Manager](/mem/endpoint-manager-overview) est une plateforme de solution qui unifie plusieurs services. Il inclut [des Microsoft Intune](/mem/intune/fundamentals/what-is-intune) pour la gestion des appareils en nuage.

Cette rubrique guide les utilisateurs dans :

- Étape 1 : intégration d’appareils au service en créant un groupe dans Microsoft Endpoint Manager (MEM) pour affecter des configurations sur
- Étape 2 : Configuration de Defender pour les fonctionnalités de point de terminaison à l’aide de Microsoft Endpoint Manager

Ces instructions d’intégration vous guident tout au long des étapes de base suivantes que vous devez suivre lors de l’utilisation Microsoft Endpoint Manager :

- [Identification des appareils ou des utilisateurs cibles](#identify-target-devices-or-users)
  - Création d’Azure Active Directory groupe (utilisateur ou appareil)
- [Création d’un profil de configuration](#step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities)
  - Dans Microsoft Endpoint Manager, nous vous guiderons dans la création d’une stratégie distincte pour chaque fonctionnalité.

## <a name="resources"></a>Ressources

Voici les liens dont vous aurez besoin pour le reste du processus :

- [Portail MEM](https://aka.ms/memac)
- [Centre de sécurité](https://securitycenter.windows.com/)
- [Bases de référence de sécurité Intune](/mem/intune/protect/security-baseline-settings-defender-atp#microsoft-defender)

Pour plus d’informations Microsoft Endpoint Manager, consultez les ressources ci-après :

- [Microsoft Endpoint Manager page](/mem/)
- [Billet de blog sur la convergence d’Intune et configMgr](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace/)
- [Vidéo d’introduction sur MEM](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace)

## <a name="step-1-onboard-devices-by-creating-a-group-in-mem-to-assign-configurations-on"></a>Étape 1 : intégrer des appareils en créant un groupe dans MEM pour affecter des configurations

### <a name="identify-target-devices-or-users"></a>Identifier les appareils ou les utilisateurs cibles

Dans cette section, nous allons créer un groupe de test pour affecter vos configurations.

> [!NOTE]
> Intune utilise Azure Active Directory groupes (Azure AD) pour gérer les appareils et les utilisateurs. En tant qu’administrateur Intune, vous pouvez configurer des groupes en fonction des besoins de votre organisation.
>
> Pour plus d’informations, voir [Ajouter des groupes pour organiser les utilisateurs et les appareils.](/mem/intune/fundamentals/groups-add)

### <a name="create-a-group"></a>Créer un groupe

1. Ouvrez le portail MEM.

2. Ouvrez **groupes > nouveau groupe.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal1.](images/66f724598d9c3319cba27f79dd4617a4.png)

3. Entrez des détails et créez un groupe.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal2.](images/b1e0206d675ad07db218b63cd9b9abc3.png)

4. Ajoutez votre utilisateur ou appareil de test.

5. Dans le **volet Groupes >** tous les groupes, ouvrez votre nouveau groupe.

6. Sélectionnez **membres > ajouter des membres.**

7. Recherchez votre utilisateur ou appareil de test et sélectionnez-le.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal3.](images/149cbfdf221cdbde8159d0ab72644cd0.png)

8. Votre groupe de test a maintenant un membre à tester.

## <a name="step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities"></a>Étape 2 : Créer des stratégies de configuration pour configurer microsoft Defender pour les fonctionnalités de point de terminaison

Dans la section suivante, vous allez créer un certain nombre de stratégies de configuration.

Tout d’abord, il s’agit d’une stratégie de configuration qui permet de sélectionner les groupes d’utilisateurs ou d’appareils qui seront intégrés à Defender for Endpoint :

- [Détection et réponse du point de terminaison](#endpoint-detection-and-response)

Ensuite, vous allez continuer en créant différents types de stratégies de sécurité de point de terminaison :

- [Protection de nouvelle génération](#next-generation-protection)
- [Réduction de la surface d’attaque](#attack-surface-reduction---attack-surface-reduction-rules)

### <a name="endpoint-detection-and-response"></a>Détection et réponse du point de terminaison

1. Ouvrez le portail MEM.

2. Accédez à **Endpoint security > endpoint detection and response**. Cliquez sur **Créer un profil.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal4.](images/58dcd48811147feb4ddc17212b7fe840.png)

3. Sous **Plateforme, sélectionnez Windows 10 et ultérieure, Profil - Détection** de point de terminaison et réponse > créer.

4. Entrez un nom et une description, puis sélectionnez **Suivant.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal5.](images/a5b2d23bdd50b160fef4afd25dda28d4.png)

5. Sélectionnez les paramètres selon les besoins, puis sélectionnez **Suivant.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal6.](images/cea7e288b5d42a9baf1aef0754ade910.png)

    > [!NOTE]
    > Dans cette instance, cela a été automatiquement rempli comme Defender pour point de terminaison a déjà été intégré à Intune. Pour plus d’informations sur l’intégration, voir [Activer Microsoft Defender pour le point de terminaison dans Intune.](/mem/intune/protect/advanced-threat-protection-configure#to-enable-microsoft-defender-atp)
    >
    > L’image suivante illustre ce que vous voyez lorsque Microsoft Defender pour le point de terminaison n’est PAS intégré à Intune :
    >
    > ![Image de Microsoft Endpoint Manager portal7.](images/2466460812371ffae2d19a10c347d6f4.png)

6. Ajoutez des balises d’étendue si nécessaire, puis sélectionnez **Suivant.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal8.](images/ef844f52ec2c0d737ce793f68b5e8408.png)

7. Ajoutez un groupe de test en cliquant sur **Sélectionner les groupes à inclure** et choisissez votre groupe, puis sélectionnez **Suivant.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal9.](images/fc3525e20752da026ec9f46ab4fec64f.png)

8. Examinez et acceptez, puis sélectionnez **Créer.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal10.](images/289172dbd7bd34d55d24810d9d4d8158.png)

9. Vous pouvez afficher votre stratégie terminée.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal11.](images/5a568b6878be8243ea2b9d82d41ed297.png)

### <a name="next-generation-protection"></a>Protection de nouvelle génération

1. Ouvrez le portail MEM.

2. Accédez **à Endpoint Security > Antivirus > Create Policy**.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal12.](images/6b728d6e0d71108d768e368b416ff8ba.png)

3. Select **Platform - Windows 10 and Later - Windows and Profile - Microsoft Defender Antivirus > Create**.

4. Entrez le nom et la description, puis sélectionnez **Suivant.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal13.](images/a7d738dd4509d65407b7d12beaa3e917.png)

5. Dans la **page Paramètres** de configuration : définissez les configurations dont vous avez besoin pour Antivirus Microsoft Defender (protection cloud, exclusions, Real-Time protection et correction).

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal14.](images/3840b1576d6f79a1d72eb14760ef5e8c.png)

6. Ajoutez des balises d’étendue si nécessaire, puis sélectionnez **Suivant.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal15.](images/2055e4f9b9141525c0eb681e7ba19381.png)

7. Sélectionnez les groupes à inclure, affectez à votre groupe de test, puis sélectionnez  **Suivant**.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal16.](images/48318a51adee06bff3908e8ad4944dc9.png)

8. Examinez et créez, puis sélectionnez **Créer.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal17.](images/dfdadab79112d61bd3693d957084b0ec.png)

9. Vous verrez la stratégie de configuration que vous avez créée.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal18.](images/38180219e632d6e4ec7bd25a46398da8.png)

### <a name="attack-surface-reduction---attack-surface-reduction-rules"></a>Réduction de la surface d’attaque : règles de réduction de la surface d’attaque

1. Ouvrez le portail MEM.

2. Accédez à **Endpoint Security > Attack surface reduction**.

3. Sélectionnez **Créer une stratégie.**

4. Sélectionner **la plateforme - Windows 10 et ultérieures - Profil - Règles** de réduction de la surface d’attaque > créer .

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal19.](images/522d9bb4288dc9c1a957392b51384fdd.png)

5. Entrez un nom et une description, puis sélectionnez **Suivant.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal20.](images/a5a71fd73ec389f3cdce6d1a6bd1ff31.png)

6. Dans la **page Paramètres de configuration**: définissez les configurations dont vous avez besoin pour les règles de réduction de la surface d’attaque, puis sélectionnez **Suivant.**

    > [!NOTE]
    > Nous allons configurer toutes les règles de réduction de la surface d’attaque sur Audit.
    >
    > Pour plus d’informations, voir [Règles de réduction de la surface d’attaque.](attack-surface-reduction.md)

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal21.](images/dd0c00efe615a64a4a368f54257777d0.png)

7. Ajoutez des balises d’étendue selon les besoins, puis sélectionnez **Suivant.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal22.](images/6daa8d347c98fe94a0d9c22797ff6f28.png)

8. Sélectionnez les groupes à inclure et à affecter au groupe de test, puis sélectionnez  **Suivant**.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal23.](images/45cefc8e4e474321b4d47b4626346597.png)

9. Examinez les détails, puis sélectionnez **Créer.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal24.](images/2c2e87c5fedc87eba17be0cdeffdb17f.png)

10. Afficher la stratégie.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal25.](images/7a631d17cc42500dacad4e995823ffef.png)

### <a name="attack-surface-reduction---web-protection"></a>Réduction de la surface d’attaque - Protection Web

1. Ouvrez le portail MEM.

2. Accédez à **Endpoint Security > Attack surface reduction**.

3. Sélectionnez **Créer une stratégie.**

4. Select **Windows 10 and Later - Web protection > Create**.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal26.](images/cd7b5a1cbc16cc05f878cdc99ba4c27f.png)

5. Entrez un nom et une description, puis sélectionnez **Suivant.**

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal27.](images/5be573a60cd4fa56a86a6668b62dd808.png)

6. Dans la **page Paramètres de configuration**: définissez les configurations dont vous avez besoin pour la protection web, puis sélectionnez **Suivant.**

    > [!NOTE]
    > Nous configurons la protection Web sur Bloquer.
    >
    > Pour plus d’informations, voir [Web Protection](web-protection-overview.md).

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal28.](images/6104aa33a56fab750cf30ecabef9f5b6.png)

7. Ajoutez **des balises d’étendue comme > suivant**.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal29.](images/6daa8d347c98fe94a0d9c22797ff6f28.png)

8. Sélectionnez **Affecter au groupe de test > Suivant**.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal30.](images/45cefc8e4e474321b4d47b4626346597.png)

9. Select **Review and Create > Create**.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal31.](images/8ee0405f1a96c23d2eb6f737f11c1ae5.png)

10. Afficher la stratégie.

    > [!div class="mx-imgBorder"]
    > ![Image de Microsoft Endpoint Manager portal32.](images/e74f6f6c150d017a286e6ed3dffb7757.png)

## <a name="validate-configuration-settings"></a>Valider les paramètres de configuration

### <a name="confirm-policies-have-been-applied"></a>Confirmer que les stratégies ont été appliquées

Une fois que la stratégie de configuration a été affectée, l’application prend un certain temps.

Pour plus d’informations sur le minutage, consultez [les informations de configuration d’Intune.](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)

Pour vérifier que la stratégie de configuration a été appliquée à votre périphérique de test, suivez le processus suivant pour chaque stratégie de configuration.

1. Ouvrez le portail MEM et accédez à la stratégie pertinente, comme indiqué dans les étapes ci-dessus. L’exemple suivant illustre les paramètres de protection nouvelle génération.

    > [!div class="mx-imgBorder"]
    > [![Image de Microsoft Endpoint Manager portal33.](images/43ab6aa74471ee2977e154a4a5ef2d39.png)](images/43ab6aa74471ee2977e154a4a5ef2d39.png#lightbox)

2. Sélectionnez la **stratégie de configuration** pour afficher l’état de la stratégie.

    > [!div class="mx-imgBorder"]
    > [![Image de Microsoft Endpoint Manager portal34.](images/55ecaca0e4a022f0e29d45aeed724e6c.png)](images/55ecaca0e4a022f0e29d45aeed724e6c.png#lightbox)

3. Sélectionnez  **État de l’appareil** pour voir l’état.

    > [!div class="mx-imgBorder"]
    > [![Image de Microsoft Endpoint Manager portal35.](images/18a50df62cc38749000dbfb48e9a4c9b.png)](images/18a50df62cc38749000dbfb48e9a4c9b.png#lightbox)

4. Sélectionnez  **État de l’utilisateur** pour voir l’état.

    > [!div class="mx-imgBorder"]
    > [![Image de Microsoft Endpoint Manager portal36.](images/4e965749ff71178af8873bc91f9fe525.png)](images/4e965749ff71178af8873bc91f9fe525.png#lightbox)

5. Sélectionnez  **l’état par paramètre** pour voir l’état.

    > [!TIP]
    > Cet affichage est très utile pour identifier les paramètres qui entrent en conflit avec une autre stratégie.

    > [!div class="mx-imgBorder"]
    > [![Image de Microsoft Endpoint Manager portal37.](images/42acc69d0128ed09804010bdbdf0a43c.png)](images/42acc69d0128ed09804010bdbdf0a43c.png#lightbox)

### <a name="confirm-endpoint-detection-and-response"></a>Confirmez protection évolutive des points de terminaison

1. Avant d’appliquer la configuration, le service Defender pour Endpoint Protection ne doit pas être démarré.

    > [!div class="mx-imgBorder"]
    > [![Image du panneau Services 1.](images/b418a232a12b3d0a65fc98248dbb0e31.png)](images/b418a232a12b3d0a65fc98248dbb0e31.png#lightbox)

2. Une fois la configuration appliquée, le service Defender for Endpoint Protection doit être démarré.

    > [!div class="mx-imgBorder"]
    > [![Image du panneau Services2.](images/a621b699899f1b41db211170074ea59e.png)](images/a621b699899f1b41db211170074ea59e.png#lightbox)

3. Une fois que les services sont en cours d’exécution sur l’appareil, l’appareil apparaît dans le Centre de sécurité Microsoft Defender.

    > [!div class="mx-imgBorder"]
    > [![Image de Centre de sécurité Microsoft Defender.](images/df0c64001b9219cfbd10f8f81a273190.png)](images/df0c64001b9219cfbd10f8f81a273190.png#lightbox)

### <a name="confirm-next-generation-protection"></a>Confirmer la protection nouvelle génération

1. Avant d’appliquer la stratégie sur un périphérique de test, vous devez être en mesure de gérer manuellement les paramètres, comme illustré ci-dessous.

    > [!div class="mx-imgBorder"]
    > ![Image du paramètre page1.](images/88efb4c3710493a53f2840c3eac3e3d3.png)

2. Une fois la stratégie appliquée, vous ne devez pas être en mesure de gérer manuellement les paramètres.

    > [!NOTE]
    > Dans l’image **suivante,** activer la protection cloud et activer la **protection** en temps réel sont affichés comme gérés.

    > [!div class="mx-imgBorder"]
    > ![Image du paramètre page2.](images/9341428b2d3164ca63d7d4eaa5cff642.png)

### <a name="confirm-attack-surface-reduction---attack-surface-reduction-rules"></a>Confirmer la Réduction de la surface d’attaque : règles de réduction de la surface d’attaque

1. Avant d’appliquer la stratégie sur un périphérique de test, stylet une fenêtre PowerShell et tapez `Get-MpPreference` .

2. Cela doit répondre avec les lignes suivantes sans contenu :

    > AttackSurfaceReductionOnlyExclusions :
    >
    > AttackSurfaceReductionRules_Actions :
    >
    > AttackSurfaceReductionRules_Ids :

    ![Image de la ligne de commande 1.](images/cb0260d4b2636814e37eee427211fe71.png)

3. Après avoir appliqué la stratégie sur un périphérique de test, ouvrez un Windows PowerShell et tapez `Get-MpPreference` .

4. Cela doit répondre avec les lignes suivantes avec le contenu comme indiqué ci-dessous :

    ![Image de la ligne de commande 2.](images/619fb877791b1fc8bc7dfae1a579043d.png)

### <a name="confirm-attack-surface-reduction---web-protection"></a>Confirmer la Réduction de la surface d’attaque - Protection Web

1. Sur le périphérique de test, ouvrez une Windows PowerShell et tapez `(Get-MpPreference).EnableNetworkProtection` .

2. Cela doit répondre avec un 0 comme illustré ci-dessous.

    ![Image de la ligne de commande 3.](images/196a8e194ac99d84221f405d0f684f8c.png)

3. Après avoir appliqué la stratégie, ouvrez un Windows PowerShell et tapez `(Get-MpPreference).EnableNetworkProtection` .

4. Cela doit répondre avec un 1, comme illustré ci-dessous.

    ![Image de la ligne de commande 4.](images/c06fa3bbc2f70d59dfe1e106cd9a4683.png)
