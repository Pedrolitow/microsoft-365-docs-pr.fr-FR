---
title: Intégration à l'aide de Microsoft Endpoint Configuration Manager
description: Découvrez comment intégrer à Microsoft Defender pour point de terminaison à l’aide de Microsoft Endpoint Configuration Manager
keywords: intégration, configuration, déploiement, gestionnaire de configuration de point de terminaison, Microsoft Defender pour point de terminaison, création de collection, réponse de détection de point de terminaison, protection de nouvelle génération, réduction de la surface d’attaque, gestionnaire de configuration de point de terminaison Microsoft
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-endpointprotect
- m365solution-scenario
- highpri
- tier1
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: dc3499dad3f08f6f9e3e7346d22b97808cd807ee
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68626136"
---
# <a name="onboarding-using-microsoft-endpoint-configuration-manager"></a>Intégration à l'aide de Microsoft Endpoint Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cet article fait partie du guide de déploiement et sert d’exemple de méthode d’intégration.

Dans la rubrique [Planification](deployment-strategy.md) , plusieurs méthodes ont été fournies pour intégrer des appareils au service. Cette rubrique traite de l’architecture de cogestion.

:::image type="content" source="images/co-management-architecture.png" alt-text="L’architecture cloud native" lightbox="images/co-management-architecture.png":::
*Diagramme des architectures d’environnement*

Bien que Defender pour point de terminaison prenne en charge l’intégration de différents points de terminaison et outils, cet article ne les aborde pas. Pour plus d’informations sur l’intégration générale à l’aide d’autres outils et méthodes de déploiement pris en charge, consultez [vue d’ensemble de l’intégration](onboarding.md).

Cette rubrique guide les utilisateurs dans :

- Étape 1 : Intégration d’appareils Windows au service
- Étape 2 : Configuration des fonctionnalités de Defender pour point de terminaison

Ces conseils d’intégration vous guideront tout au long des étapes de base suivantes que vous devez effectuer lors de l’utilisation de Microsoft Endpoint Configuration Manager :

- **Création d’une collection dans microsoft endpoint Configuration Manager**
- **Configuration des fonctionnalités Microsoft Defender pour point de terminaison à l’aide de Microsoft Endpoint Configuration Manager**

> [!NOTE]
> Seuls les appareils Windows sont couverts dans cet exemple de déploiement.

## <a name="step-1-onboard-windows-devices-using-microsoft-endpoint-configuration-manager"></a>Étape 1 : Intégrer des appareils Windows à l’aide du point de terminaison Microsoft Configuration Manager

### <a name="collection-creation"></a>Création d’une collection

Pour intégrer des appareils Windows à Microsoft Endpoint Configuration Manager, le déploiement peut cibler une collection existante ou une nouvelle collection peut être créée à des fins de test.

L’intégration à l’aide d’outils tels que la stratégie de groupe ou la méthode manuelle n’installe aucun agent sur le système.

Dans la console Microsoft Endpoint Configuration Manager, le processus d’intégration est configuré dans le cadre des paramètres de conformité dans la console.

Tout système qui reçoit cette configuration requise conserve cette configuration tant que le client Configuration Manager continue de recevoir cette stratégie à partir du point de gestion.

Suivez les étapes ci-dessous pour intégrer des points de terminaison à l’aide de Microsoft Endpoint Configuration Manager.

1. Dans la console Microsoft Endpoint Configuration Manager, accédez à **Assets and Compliance \> Overview \> Device Collections**.

    :::image type="content" source="images/configmgr-device-collections.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft1" lightbox="images/configmgr-device-collections.png":::

2. Sélectionnez La **collection d’appareils** , puis **créez une collection d’appareils**.

    :::image type="content" source="images/configmgr-create-device-collection.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft 2" lightbox="images/configmgr-create-device-collection.png":::

3. Indiquez un **nom** et **limitez la collection**, puis sélectionnez **Suivant**.

    :::image type="content" source="images/configmgr-limiting-collection.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft 3" lightbox="images/configmgr-limiting-collection.png":::

4. Sélectionnez **Ajouter une règle** , puis choisissez **Règle de requête**.

    :::image type="content" source="images/configmgr-query-rule.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft 4" lightbox="images/configmgr-query-rule.png":::

5. Sélectionnez **Suivant** dans **l’Assistant Appartenance directe** , puis **sélectionnez Modifier l’instruction de requête**.

    :::image type="content" source="images/configmgr-direct-membership.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft5" lightbox="images/configmgr-direct-membership.png":::

6. Sélectionnez **Critères** , puis choisissez l’icône en étoile.

    :::image type="content" source="images/configmgr-criteria.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft 6" lightbox="images/configmgr-criteria.png":::

7. Conservez le type de critère comme **valeur simple**, choisissez où en tant que **système d’exploitation : numéro de build**, opérateur tel **qu’il est supérieur ou égal à** et valeur **14393** , puis sélectionnez **OK**.

    :::image type="content" source="images/configmgr-simple-value.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft 7" lightbox="images/configmgr-simple-value.png":::

8. Sélectionnez **Suivant** et **Fermer**.

    :::image type="content" source="images/configmgr-membership-rules.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft8" lightbox="images/configmgr-membership-rules.png":::

9. Sélectionnez **Suivant**.

    :::image type="content" source="images/configmgr-confirm.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft9" lightbox="images/configmgr-confirm.png":::

Une fois cette tâche terminée, vous disposez maintenant d’une collection d’appareils avec tous les points de terminaison Windows dans l’environnement.

## <a name="step-2-configure-microsoft-defender-for-endpoint-capabilities"></a>Étape 2 : Configurer les fonctionnalités Microsoft Defender pour point de terminaison

Cette section vous guide dans la configuration des fonctionnalités suivantes à l’aide de Microsoft Endpoint Configuration Manager sur les appareils Windows :

- [**Détection et réponse des points de terminaison**](#endpoint-detection-and-response)
- [**Protection de nouvelle génération**](#next-generation-protection)
- [**Réduction de la surface d’attaque**](#attack-surface-reduction)

### <a name="endpoint-detection-and-response"></a>Détection et réponse du point de terminaison

#### <a name="windows-10-and-windows-11"></a>Windows 10 et Windows 11

À partir du portail Microsoft 365 Defender, il est possible de télécharger la `.onboarding` stratégie qui peut être utilisée pour créer la stratégie dans System Center Configuration Manager et déployer cette stratégie sur Windows 10 et Windows 11 appareils.

1. Dans un <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, sélectionnez [Paramètres, puis Intégration](https://security.microsoft.com/preferences2/onboarding).

2. Sous Méthode de déploiement, sélectionnez la version prise en charge de **Microsoft Endpoint Configuration Manager**.

    :::image type="content" source="images/mdatp-onboarding-wizard.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft 10" lightbox="images/mdatp-onboarding-wizard.png":::

3. Sélectionnez **Télécharger le package**.

   :::image type="content" source="images/mdatp-download-package.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft11" lightbox="images/mdatp-download-package.png":::

4. Enregistrez le package à un emplacement accessible.
5. Dans Microsoft Endpoint Configuration Manager, accédez à : **Ressources et conformité > Vue d’ensemble > Endpoint Protection > Microsoft Defender stratégies ATP**.

6. Cliquez avec le bouton droit **sur Microsoft Defender stratégies ATP**, puis sélectionnez **Créer Microsoft Defender stratégie ATP**.

    :::image type="content" source="images/configmgr-create-policy.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft12" lightbox="images/configmgr-create-policy.png":::

7. Entrez le nom et la description, vérifiez que **l’intégration** est sélectionnée, puis sélectionnez **Suivant**.

    :::image type="content" source="images/configmgr-policy-name.png" alt-text="Assistant Configuration Manager du point de terminaison Microsoft13" lightbox="images/configmgr-policy-name.png":::

8. Sélectionnez **Parcourir**.

9. Accédez à l’emplacement du fichier téléchargé à l’étape 4 ci-dessus.

10. Sélectionnez **Suivant**.
11. Configurez l’Agent avec les exemples appropriés (**aucun** ou **tous les types de fichiers**).

    :::image type="content" source="images/configmgr-config-settings.png" alt-text="Paramètres de configuration1" lightbox="images/configmgr-config-settings.png":::

12. Sélectionnez les données de télémétrie appropriées (**Normale** ou **Accélérée**), puis **sélectionnez Suivant**.

    :::image type="content" source="images/configmgr-telemetry.png" alt-text="Paramètres de configuration2" lightbox="images/configmgr-telemetry.png":::

13. Vérifiez la configuration, puis sélectionnez **Suivant**.

    :::image type="content" source="images/configmgr-verify-configuration.png" alt-text="Paramètres de configuration3" lightbox="images/configmgr-verify-configuration.png":::

14. Sélectionnez **Fermer** une fois l’Assistant terminé.

15. Dans la console Microsoft Endpoint Configuration Manager, cliquez avec le bouton droit sur la stratégie Defender pour point de terminaison que vous venez de créer, puis sélectionnez **Déployer**.

    :::image type="content" source="images/configmgr-deploy.png" alt-text="Paramètres de configuration4" lightbox="images/configmgr-deploy.png":::

16. Dans le volet droit, sélectionnez la collection créée précédemment, puis **sélectionnez OK**.

    :::image type="content" source="images/configmgr-select-collection.png" alt-text="Paramètres de configuration5" lightbox="images/configmgr-select-collection.png":::

#### <a name="previous-versions-of-windows-client-windows-7-and-windows-81"></a>Versions précédentes du client Windows (Windows 7 et Windows 8.1)

Suivez les étapes ci-dessous pour identifier l’ID d’espace de travail Defender pour point de terminaison et la clé d’espace de travail qui seront nécessaires pour l’intégration des versions précédentes de Windows.

1. Dans un <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, sélectionnez **Paramètres** \> **Endpoints** \> **Onboarding** (sous **Gestion des appareils**).

2. Sous système d’exploitation, choisissez **Windows 7 SP1 et 8.1**.

3. Copiez **l’ID d’espace de travail** et la **clé de l’espace de travail** et enregistrez-les. Ils seront utilisés ultérieurement dans le processus.

   :::image type="content" source="images/91b738e4b97c4272fd6d438d8c2d5269.png" alt-text="Le processus d’intégration" lightbox="images/91b738e4b97c4272fd6d438d8c2d5269.png":::

4. Installez Microsoft Monitoring Agent (MMA).

   MMA est actuellement pris en charge (depuis janvier 2019) sur les systèmes d’exploitation Windows suivants :

   - Références SKU de serveur : Windows Server 2008 SP1 ou version ultérieure
   - Références SKU clientes : Windows 7 SP1 et versions ultérieures

   L’agent MMA doit être installé sur les appareils Windows. Pour installer l’agent, certains systèmes devront télécharger la [mise à jour pour l’expérience client et la télémétrie de diagnostic](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry) afin de collecter les données avec MMA. Ces versions système incluent, mais ne peuvent pas être limitées aux éléments suivants :

   - Windows 8.1
   - Windows 7
   - Windows Server 2016
   - Windows Server 2012 R2
   - Windows Server 2008 R2

   Plus précisément, pour Windows 7 SP1, les correctifs suivants doivent être installés :

   - Installer [KB4074598](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
   - Installez [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (ou version ultérieure) **ou** [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework). N’installez pas les deux sur le même système.

5. Si vous utilisez un proxy pour vous connecter à Internet, consultez la section Configurer les paramètres du proxy.

Une fois l’opération terminée, vous devez voir les points de terminaison intégrés dans le portail dans une heure.

### <a name="next-generation-protection"></a>Protection de nouvelle génération

Microsoft Defender Antivirus est une solution anti-programme malveillant intégrée qui fournit une protection de nouvelle génération pour les ordinateurs de bureau, les ordinateurs portables et les serveurs.

1. Dans la console Microsoft Endpoint Configuration Manager, accédez à **Assets and Compliance \> Overview \> Endpoint Protection \> Antimalware Polices** et choisissez **Créer une stratégie anti-programme malveillant**.

   :::image type="content" source="images/9736e0358e86bc778ce1bd4c516adb8b.png" alt-text="Stratégie anti-programme malveillant" lightbox="images/9736e0358e86bc778ce1bd4c516adb8b.png":::

2. Sélectionnez **Analyses planifiées**, **paramètres d’analyse**, **actions par défaut**, **protection en temps réel**, **paramètres d’exclusion**, **Options avancées**, **remplacements de menaces**, mises à jour **du service de protection cloud** et **du renseignement de sécurité** , puis choisissez **OK**.

   :::image type="content" source="images/1566ad81bae3d714cc9e0d47575a8cbd.png" alt-text="Volet de protection de nouvelle génération1" lightbox="images/1566ad81bae3d714cc9e0d47575a8cbd.png":::

    Dans certains secteurs d’activité ou certains clients d’entreprise, certains clients peuvent avoir des besoins spécifiques sur la façon dont l’antivirus est configuré.

    [Analyse rapide et analyse complète et analyse personnalisée](/windows/security/threat-protection/microsoft-defender-antivirus/scheduled-catch-up-scans-microsoft-defender-antivirus#quick-scan-versus-full-scan-and-custom-scan)

    Pour plus d’informations, consultez [Sécurité Windows framework de configuration](/windows/security/threat-protection/windows-security-configuration-framework/windows-security-configuration-framework).
  
    :::image type="content" source="images/cd7daeb392ad5a36f2d3a15d650f1e96.png" alt-text="Volet de protection de nouvelle génération2" lightbox="images/cd7daeb392ad5a36f2d3a15d650f1e96.png":::

    :::image type="content" source="images/36c7c2ed737f2f4b54918a4f20791d4b.png" alt-text="Volet de protection de nouvelle génération3" lightbox="images/36c7c2ed737f2f4b54918a4f20791d4b.png":::

    :::image type="content" source="images/a28afc02c1940d5220b233640364970c.png" alt-text="Volet de protection de nouvelle génération4" lightbox="images/a28afc02c1940d5220b233640364970c.png":::

    :::image type="content" source="images/5420a8790c550f39f189830775a6d4c9.png" alt-text="Volet de protection de nouvelle génération5" lightbox="images/5420a8790c550f39f189830775a6d4c9.png":::

    :::image type="content" source="images/33f08a38f2f4dd12a364f8eac95e8c6b.png" alt-text="Volet de protection de nouvelle génération6" lightbox="images/33f08a38f2f4dd12a364f8eac95e8c6b.png":::

    :::image type="content" source="images/41b9a023bc96364062c2041a8f5c344e.png" alt-text="Volet de protection de nouvelle génération7" lightbox="images/41b9a023bc96364062c2041a8f5c344e.png":::

    :::image type="content" source="images/945c9c5d66797037c3caeaa5c19f135c.png" alt-text="Volet de protection de nouvelle génération8" lightbox="images/945c9c5d66797037c3caeaa5c19f135c.png":::

    :::image type="content" source="images/3876ca687391bfc0ce215d221c683970.png" alt-text="Le volet de protection de nouvelle génération 9" lightbox="images/3876ca687391bfc0ce215d221c683970.png":::

3. Cliquez avec le bouton droit sur la stratégie anti-programme malveillant nouvellement créée, puis sélectionnez **Déployer**.

    :::image type="content" source="images/f5508317cd8c7870627cb4726acd5f3d.png" alt-text="Volet de protection de nouvelle génération10" lightbox="images/f5508317cd8c7870627cb4726acd5f3d.png":::

4. Ciblez la nouvelle stratégie anti-programme malveillant dans votre collection Windows, puis sélectionnez **OK**.

    :::image type="content" source="images/configmgr-select-collection.png" alt-text="Volet de protection de nouvelle génération11" lightbox="images/configmgr-select-collection.png":::

Une fois cette tâche terminée, vous avez correctement configuré Microsoft Defender Antivirus.

### <a name="attack-surface-reduction"></a>Réduction de la surface d'attaque

Le pilier de réduction de la surface d’attaque de Defender pour point de terminaison inclut l’ensemble de fonctionnalités disponible sous Exploit Guard. Règles de réduction de la surface d’attaque (ASR), Accès contrôlé aux dossiers, Protection réseau et Exploit Protection.

Toutes ces fonctionnalités fournissent un mode test et un mode bloc. En mode test, il n’y a aucun impact sur l’utilisateur final. Tout ce qu’il fait est de collecter des données de télémétrie supplémentaires et de les rendre disponibles dans le portail Microsoft 365 Defender. L’objectif d’un déploiement est de déplacer pas à pas les contrôles de sécurité en mode bloc.

Pour définir des règles ASR en mode test :

1. Dans la console Configuration Manager du point de terminaison Microsoft, accédez à La **vue d’ensemble \> des ressources et de la conformité \> Endpoint Protection \> Windows Defender Exploit Guard** et choisissez **Créer une stratégie Exploit Guard**.

   :::image type="content" source="images/728c10ef26042bbdbcd270b6343f1a8a.png" alt-text="Console microsoft endpoint Configuration Manager 0" lightbox="images/728c10ef26042bbdbcd270b6343f1a8a.png":::

2. Sélectionnez **Réduction de la surface d’attaque**.

3. Définissez les règles sur **Audit et** sélectionnez **Suivant**.

   :::image type="content" source="images/d18e40c9e60aecf1f9a93065cb7567bd.png" alt-text="Console microsoft endpoint Configuration Manager 1" lightbox="images/d18e40c9e60aecf1f9a93065cb7567bd.png":::

4. Confirmez la nouvelle stratégie Exploit Guard en sélectionnant **Suivant**.

   :::image type="content" source="images/0a6536f2c4024c08709cac8fcf800060.png" alt-text="Microsoft Endpoint Configuration Manager console2" lightbox="images/0a6536f2c4024c08709cac8fcf800060.png":::

5. Une fois la stratégie créée, sélectionnez **Fermer**.

   :::image type="content" source="images/95d23a07c2c8bc79176788f28cef7557.png" alt-text="Le point de terminaison Microsoft Configuration Manager console3" lightbox="images/95d23a07c2c8bc79176788f28cef7557.png":::

6. Cliquez avec le bouton droit sur la stratégie nouvellement créée et choisissez **Déployer**.

   :::image type="content" source="images/8999dd697e3b495c04eb911f8b68a1ef.png" alt-text="Console Configuration Manager du point de terminaison Microsoft 4" lightbox="images/8999dd697e3b495c04eb911f8b68a1ef.png":::

7. Ciblez la stratégie sur la collection Windows nouvellement créée, puis sélectionnez **OK**.

   :::image type="content" source="images/0ccfe3e803be4b56c668b220b51da7f7.png" alt-text="Console microsoft endpoint Configuration Manager 5" lightbox="images/0ccfe3e803be4b56c668b220b51da7f7.png":::

Une fois cette tâche terminée, vous avez correctement configuré les règles ASR en mode test.

Vous trouverez ci-dessous des étapes supplémentaires pour vérifier si les règles ASR sont correctement appliquées aux points de terminaison. (Cela peut prendre quelques minutes)

1. À partir d’un navigateur web, accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

2. Sélectionnez **Gestion de la configuration** dans le menu de gauche.

3. Sélectionnez **Accéder à la gestion de la surface d’attaque** dans le panneau de gestion de la surface d’attaque.

   :::image type="content" source="images/security-center-attack-surface-mgnt-tile.png" alt-text="Gestion de la surface d’attaque" lightbox="images/security-center-attack-surface-mgnt-tile.png":::

4. Sélectionnez **l’onglet Configuration** dans les rapports de règles de réduction de la surface d’attaque. Il présente la vue d’ensemble de la configuration des règles ASR et l’état des règles ASR sur chaque appareil.

   :::image type="content" source="images/f91f406e6e0aae197a947d3b0e8b2d0d.png" alt-text="Les règles de réduction de la surface d’attaque indiquent1" lightbox="images/f91f406e6e0aae197a947d3b0e8b2d0d.png":::

5. Sélectionnez chaque appareil pour afficher les détails de configuration des règles ASR.

   :::image type="content" source="images/24bfb16ed561cbb468bd8ce51130ca9d.png" alt-text="Les règles de réduction de la surface d’attaque indiquent2" lightbox="images/24bfb16ed561cbb468bd8ce51130ca9d.png":::

Pour plus d’informations, consultez [Optimiser le déploiement de règles ASR et les détections](/microsoft-365/security/defender-endpoint/configure-machines-asr) .

#### <a name="set-network-protection-rules-in-test-mode"></a>Définir des règles de protection réseau en mode test

1. Dans la console Configuration Manager du point de terminaison Microsoft, accédez à La **vue d’ensemble \> des ressources et de la conformité \> Endpoint Protection \> Windows Defender Exploit Guard** et choisissez **Créer une stratégie Exploit Guard**.

   :::image type="content" source="images/728c10ef26042bbdbcd270b6343f1a8a.png" alt-text="The System Center Configuration Manager1" lightbox="images/728c10ef26042bbdbcd270b6343f1a8a.png":::

2. Sélectionnez **Protection réseau**.

3. Définissez le paramètre **sur Audit et** sélectionnez **Suivant**.

   :::image type="content" source="images/c039b2e05dba1ade6fb4512456380c9f.png" alt-text="The System Center Configuration Manager2" lightbox="images/c039b2e05dba1ade6fb4512456380c9f.png":::

4. Confirmez la nouvelle stratégie Exploit Guard en sélectionnant **Suivant**.

   :::image type="content" source="images/0a6536f2c4024c08709cac8fcf800060.png" alt-text="La stratégie Exploit Guard1" lightbox="images/0a6536f2c4024c08709cac8fcf800060.png":::

5. Une fois la stratégie créée, sélectionnez **Fermer**.

   :::image type="content" source="images/95d23a07c2c8bc79176788f28cef7557.png" alt-text="La stratégie Exploit Guard2" lightbox="images/95d23a07c2c8bc79176788f28cef7557.png":::

6. Cliquez avec le bouton droit sur la stratégie nouvellement créée et choisissez **Déployer**.

   :::image type="content" source="images/8999dd697e3b495c04eb911f8b68a1ef.png" alt-text="Le point de terminaison Microsoft Configuration Manager-1" lightbox="images/8999dd697e3b495c04eb911f8b68a1ef.png":::

7. Sélectionnez la stratégie dans la collection Windows nouvellement créée, puis choisissez **OK**.

   :::image type="content" source="images/0ccfe3e803be4b56c668b220b51da7f7.png" alt-text="Le point de terminaison Microsoft Configuration Manager-2" lightbox="images/0ccfe3e803be4b56c668b220b51da7f7.png":::

Une fois cette tâche terminée, vous avez correctement configuré la protection réseau en mode test.

#### <a name="to-set-controlled-folder-access-rules-in-test-mode"></a>Pour définir des règles d’accès contrôlé aux dossiers en mode test

1. Dans la console Microsoft Endpoint Configuration Manager, accédez à **Assets and Compliance** > **Overview** > **Endpoint Protection** >  **Windows Defender Exploit Guard**, puis choisissez **Créer une stratégie Exploit Guard**.

   :::image type="content" source="images/728c10ef26042bbdbcd270b6343f1a8a.png" alt-text="Le point de terminaison Microsoft Configuration Manager-3" lightbox="images/728c10ef26042bbdbcd270b6343f1a8a.png":::

2. Sélectionnez **Accès contrôlé aux dossiers**.

3. Définissez la configuration sur **Audit et** sélectionnez **Suivant**.

   :::image type="content" source="images/a8b934dab2dbba289cf64fe30e0e8aa4.png" alt-text="Le point de terminaison Microsoft Configuration Manager-4" lightbox="images/a8b934dab2dbba289cf64fe30e0e8aa4.png":::

4. Confirmez la nouvelle stratégie Exploit Guard en sélectionnant **Suivant**.

   :::image type="content" source="images/0a6536f2c4024c08709cac8fcf800060.png" alt-text="Le point de terminaison Microsoft Configuration Manager-5" lightbox="images/0a6536f2c4024c08709cac8fcf800060.png":::

5. Une fois la stratégie créée, sélectionnez **Fermer**.

   :::image type="content" source="images/95d23a07c2c8bc79176788f28cef7557.png" alt-text="Le point de terminaison Microsoft Configuration Manager-6" lightbox="images/95d23a07c2c8bc79176788f28cef7557.png":::

6. Cliquez avec le bouton droit sur la stratégie nouvellement créée et choisissez **Déployer**.

   :::image type="content" source="images/8999dd697e3b495c04eb911f8b68a1ef.png" alt-text="Le point de terminaison Microsoft Configuration Manager-7" lightbox="images/8999dd697e3b495c04eb911f8b68a1ef.png":::

7. Ciblez la stratégie sur la collection Windows nouvellement créée, puis sélectionnez **OK**.

:::image type="content" source="images/0ccfe3e803be4b56c668b220b51da7f7.png" alt-text="Le point de terminaison Microsoft Configuration Manager-8" lightbox="images/0ccfe3e803be4b56c668b220b51da7f7.png":::

Vous avez maintenant correctement configuré l’accès contrôlé aux dossiers en mode test.

## <a name="related-topic"></a>Rubrique connexe

- [Intégration à l'aide de Microsoft Endpoint Manager](onboarding-endpoint-manager.md)
