---
title: Intégrer des appareils Windows à Microsoft Defender pour point de terminaison via stratégie de groupe
description: Utilisez stratégie de groupe pour déployer le package de configuration sur les appareils Windows afin qu’ils soient intégrés au service.
keywords: configurer des appareils à l’aide d’une stratégie de groupe, de la gestion des appareils, configurer Microsoft Defender pour point de terminaison appareils, intégrer des appareils Microsoft Defender pour point de terminaison, stratégie de groupe
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 12/07/2021
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 0afaf3d635e04a4592f2cadb24ab582da3a94727
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67683690"
---
# <a name="onboard-windows-devices-using-group-policy"></a>Intégrer des appareils Windows à l’aide d’une stratégie de groupe 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**S’applique à :**

- Stratégie de groupe
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsgp-abovefoldlink)

> [!NOTE]
> Pour utiliser les mises à jour stratégie de groupe (GP) pour déployer le package, vous devez être sur Windows Server 2008 R2 ou version ultérieure.
>
> Pour Windows Server 2019 et Windows Server 2022, vous devrez peut-être remplacer NT AUTHORITY\Well-Known-System-Account par NT AUTHORITY\SYSTEM du fichier XML créé par la préférence stratégie de groupe.

> [!NOTE]
> Si vous utilisez la nouvelle solution de Microsoft Defender pour point de terminaison unifiée pour Windows Server 2012 R2 et 2016, vérifiez que vous utilisez les derniers fichiers ADMX dans votre magasin central pour accéder au fichier correct. Microsoft Defender pour point de terminaison options de stratégie. Reportez-vous [à la rubrique How to create and manage the Central Store for stratégie de groupe Administrative Templates in Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) et téléchargez les derniers fichiers **à utiliser avec Windows 10**.

Consultez le [fichier PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)  ou  [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) pour voir les différents chemins d’accès dans le déploiement de Defender pour point de terminaison.

1. Ouvrez le fichier de package de configuration de la stratégie de groupe (`WindowsDefenderATPOnboardingPackage.zip`) que vous avez téléchargé à partir de l’Assistant Intégration du service. Vous pouvez également obtenir le package à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> :

    1. Dans le volet de navigation, sélectionnez **Paramètres** > **Endpoints** > **Device Management**  > **Onboarding**.

    1. Sélectionnez le système d’exploitation.

    1. Dans le champ **Méthode de déploiement** , sélectionnez **Stratégie de groupe**.

    1. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

2. Extrayez le contenu du fichier .zip à un emplacement partagé en lecture seule accessible par l’appareil. Vous devez disposer d’un dossier appelé *OptionalParamsPolicy* et du fichier *WindowsDefenderATPOnboardingScript.cmd*.

3. Pour créer un objet de stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), cliquez avec le bouton droit **sur stratégie de groupe Objets** que vous souhaitez configurer, puis cliquez sur **Nouveau**. Entrez le nom du nouvel objet de stratégie de groupe dans la boîte de dialogue qui s’affiche, puis cliquez sur **OK**.

4. Ouvrez la [console de gestion stratégie de groupe](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), cliquez avec le bouton droit sur l’objet stratégie de groupe (GPO) que vous souhaitez configurer, puis cliquez sur **Modifier**.

5. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **Configuration de l’ordinateur**, puis **Préférences**, puis **aux paramètres du Panneau de configuration**.

6. Cliquez avec le bouton droit sur **Tâches planifiées**, **pointez sur Nouveau**, puis cliquez sur **Tâche immédiate (Au moins Windows 7).**

7. Dans la fenêtre **Tâche** qui s’ouvre, accédez à l’onglet **Général** . Sous **Options de sécurité** , cliquez sur **Modifier l’utilisateur ou le groupe** et tapez SYSTEM, puis cliquez sur **Vérifier les noms** , puis **SUR OK**. NT AUTHORITY\SYSTEM apparaît sous la forme du compte d’utilisateur sous lequel la tâche s’exécutera.

8. Sélectionnez **Exécuter si l’utilisateur est connecté ou non** et cochez la case **Exécuter avec les privilèges les plus élevés** .

9. Dans le champ Nom, tapez un nom approprié pour la tâche planifiée (par exemple, Defender pour le déploiement de point de terminaison).

10. Accédez à l’onglet **Actions** et **sélectionnez Nouveau...** Vérifiez que **démarrer un programme** est sélectionné dans le champ **Action** . Entrez le chemin d’accès UNC, à l’aide du nom de domaine complet (FQDN) du fichier *WindowsDefenderATPOnboardingScript.cmd* partagé.

11. Sélectionnez **OK** et fermez toutes les fenêtres GPMC ouvertes.

12. Pour lier l’objet de stratégie de groupe à une unité d’organisation, cliquez avec le bouton droit et sélectionnez **Lier un objet de stratégie de groupe existant**. Dans la boîte de dialogue qui s’affiche, sélectionnez l’objet stratégie de groupe que vous souhaitez lier. Cliquez sur **OK**.

> [!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier que l’appareil est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un appareil Defender pour point de terminaison nouvellement intégré](run-detection-test.md).

## <a name="additional-defender-for-endpoint-configuration-settings"></a>Paramètres de configuration Defender pour point de terminaison supplémentaires

Pour chaque appareil, vous pouvez indiquer si des échantillons peuvent être collectés à partir de l’appareil lorsqu’une demande est effectuée via Microsoft 365 Defender pour envoyer un fichier à des fins d’analyse approfondie.

Vous pouvez utiliser stratégie de groupe (GP) pour configurer des paramètres, tels que des paramètres pour l’exemple de partage utilisé dans la fonctionnalité d’analyse approfondie.

### <a name="configure-sample-collection-settings"></a>Configurer des exemples de paramètres de collecte

1. Sur votre appareil de gestion de stratégie de groupe, copiez les fichiers suivants à partir du package de configuration :

    - Copier _AtpConfiguration.admx_ dans _C:\\Windows\\PolicyDefinitions_

    - Copier _AtpConfiguration.adml_ dans _C:\\Windows\\PolicyDefinitions\\en-US_

    Si vous utilisez un [magasin central pour stratégie de groupe modèles d’administration](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra), copiez les fichiers suivants à partir du package de configuration :

    - Copier _AtpConfiguration.admx_ dans _\\\\\\\<forest.root\>SysVol\\\<forest.root\>\\Policies\\PolicyDefinitions_

    - Copier _AtpConfiguration.adml_ dans _\\\\\\\<forest.root\>SysVol\\\\\<forest.root\>Policies\\PolicyDefinitions\\en-US_

2. Ouvrez la [console de gestion stratégie de groupe](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11), cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

3. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **Configuration de l’ordinateur**.

4. Cliquez sur **Stratégies**, puis **sur Modèles d’administration**.

5. Cliquez sur **les composants Windows**, puis **Windows Defender ATP**.

6. Choisissez d’activer ou de désactiver le partage d’exemples à partir de vos appareils.

> [!NOTE]
> Si vous ne définissez pas de valeur, la valeur par défaut consiste à activer la collecte d’exemples.

## <a name="other-recommended-configuration-settings"></a>Autres paramètres de configuration recommandés

### <a name="update-endpoint-protection-configuration"></a>Mettre à jour la configuration endpoint protection

Après avoir configuré le script d’intégration, continuez à modifier la même stratégie de groupe pour ajouter des configurations endpoint protection. Effectuez des modifications de stratégie de groupe à partir d’un système exécutant Windows 10 ou Server 2019, Windows 11 ou Windows Server 2022 pour vous assurer que vous disposez de toutes les fonctionnalités antivirus Microsoft Defender requises. Vous devrez peut-être fermer et rouvrir l’objet de stratégie de groupe pour inscrire les paramètres de configuration Defender ATP.

Toutes les stratégies se trouvent sous `Computer Configuration\Policies\Administrative Templates`.

**Emplacement de la stratégie :** \Windows Components\Windows Defender ATP

Stratégie|Setting
---|---
Activer\Désactiver la collection d’exemples|Activé : « Activer l’exemple de collecte sur les machines » activé

<br>

**Emplacement de la stratégie :**  \Composants Windows\Antivirus Microsoft Defender

Stratégie|Setting
---|---
Configurer la détection pour les applications potentiellement indésirables|Activé, Bloquer

<br>

**Emplacement de la stratégie :** \Composants Windows\Antivirus Microsoft Defender\MAPS

Stratégie|Setting
---|---
Rejoindre Microsoft MAPS|Activé, Cartes avancées
Envoyer des exemples de fichiers quand une analyse plus approfondie est requise | Activé, Envoyer des exemples sécurisés

<br>

**Emplacement de la stratégie :** \Composants Windows\Antivirus Microsoft Defender\Protection en temps réel

Stratégie|Setting
---|---
Désactiver la protection en temps réel|Désactivé
Activer la surveillance du comportement|Activé
Analyser tous les fichiers et pièces jointes téléchargés|Activé
Surveiller l’activité des fichiers et des programmes sur votre ordinateur|Activé

<br>

**Emplacement de la stratégie :**  \Composants Windows\Antivirus Microsoft Defender\Scan

Ces paramètres configurent des analyses périodiques du point de terminaison. Nous vous recommandons d’effectuer une analyse rapide hebdomadaire, en autorisant les performances.

Stratégie|Setting
---|---
Recherchez les dernières informations de sécurité sur les virus et les logiciels espions avant d’exécuter une analyse planifiée |Activé

<br>

**Emplacement de la stratégie :** \Composants Windows\Antivirus Microsoft Defender\Microsoft Defender Exploit Guard\Réduction de la surface d’attaque

Obtenez la liste actuelle des guid de réduction de la surface d’attaque à partir de [l’étape 3 de déploiement des règles de réduction de la surface d’attaque : Implémenter des règles ASR](attack-surface-reduction-rules-deployment-implement.md). Pour plus d’informations sur les règles, consultez la [référence des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md)

1. Ouvrez la **stratégie configurer la réduction de la surface d’attaque** .

1. Sélectionnez **Activé**.

1. Sélectionnez le bouton **Afficher** .

1. Ajoutez chaque GUID dans le champ **Nom de la valeur** avec une valeur de 2.

   Cela permet de configurer chacune d’elles pour l’audit uniquement.

   :::image type="content" source="images/asr-guid.png" alt-text="Configuration de la réduction de la surface d’attaque" lightbox="images/asr-guid.png":::

Stratégie|Emplacement|Setting
---|---|---
Configurer l’accès contrôlé aux dossiers| \Composants Windows\Antivirus Microsoft Defender\Microsoft Defender Exploit Guard\Accès contrôlé aux dossiers| Activé, mode Audit

## <a name="run-a-detection-test-to-verify-onboarding"></a>Exécuter un test de détection pour vérifier l’intégration

Après l’intégration de l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md).

## <a name="offboard-devices-using-group-policy"></a>Désintégrage des appareils à l’aide de stratégie de groupe

Pour des raisons de sécurité, le package utilisé pour désintégrez les appareils expirera 30 jours après la date de téléchargement. Les packages de désintégrage expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package de désintégrage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de désintégrage ne doivent pas être déployées simultanément sur le même appareil, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package de désintégrage à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> :

    1. Dans le volet de navigation, sélectionnez **Paramètres** > **Points de terminaison** >  De la **désintégration** **de la gestion** >  des appareils.

    1. Sélectionnez le système d’exploitation.
    
    1. Dans le champ **Méthode de déploiement** , sélectionnez **Stratégie de groupe**.

    1. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

2. Extrayez le contenu du fichier .zip à un emplacement partagé en lecture seule accessible par l’appareil. Vous devez disposer d’un fichier nommé *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Ouvrez la [console de gestion stratégie de groupe](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), cliquez avec le bouton droit sur l’objet stratégie de groupe (GPO) que vous souhaitez configurer, puis cliquez sur **Modifier**.

4. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **Configuration de l’ordinateur,** puis **Préférences**, puis **aux paramètres du Panneau de configuration**.

5. Cliquez avec le bouton droit sur **Tâches planifiées**, **pointez sur Nouveau**, puis cliquez sur **Tâche immédiate**.

6. Dans la fenêtre **Tâche** qui s’ouvre, accédez à l’onglet **Général** . Choisissez le compte d’utilisateur SYSTEM local (BUILTIN\SYSTEM) sous **Options de sécurité**.

7. Sélectionnez **Exécuter si l’utilisateur est connecté ou non** et cochez la case **Exécuter avec les privilèges les plus élevés** .

8. Dans le champ Nom, tapez un nom approprié pour la tâche planifiée (par exemple, Defender pour le déploiement de point de terminaison).

9. Accédez à l’onglet **Actions** et **sélectionnez Nouveau...** Vérifiez que **démarrer un programme** est sélectionné dans le champ **Action** . Entrez le chemin d’accès UNC, en utilisant le nom de domaine complet (FQDN) du fichier *partagé WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd* .

10. Sélectionnez **OK** et fermez toutes les fenêtres GPMC ouvertes.

> [!IMPORTANT]
> La désintégération entraîne l’arrêt de l’envoi de données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois maximum.

## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil

Avec stratégie de groupe il n’existe pas d’option permettant de surveiller le déploiement de stratégies sur les appareils. La surveillance peut être effectuée directement sur le portail ou à l’aide des différents outils de déploiement.

## <a name="monitor-devices-using-the-portal"></a>Surveiller les appareils à l’aide du portail

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.
2. Cliquez sur **Inventaire des appareils**.
3. Vérifiez que les appareils apparaissent.

> [!NOTE]
> L’affichage des appareils dans la **liste Des** appareils peut prendre plusieurs jours. Cela inclut le temps nécessaire à la distribution des stratégies sur l’appareil, le temps nécessaire à l’ouverture de session de l’utilisateur et le temps nécessaire au point de terminaison pour démarrer la création de rapports.

## <a name="setup-defender-av-policies"></a>Configurer les stratégies av Defender

Créez un stratégie de groupe ou regroupez ces paramètres avec les autres stratégies. Cela dépend de l’environnement des clients et de la façon dont ils souhaitent déployer le service en ciblant différentes unités d’organisation.

1. Après avoir choisi la stratégie de groupe ou en créer une nouvelle, modifiez-la.

2. Accédez aux **modèles d’administration des** stratégies deconfiguration  >  > **de l’ordinateur****composants** >  >  Windows Protection en **temps réel** de **l’antivirus** >  Microsoft Defender.

    :::image type="content" source="images/realtime-protect.png" alt-text="Protection en temps réel" lightbox="images/realtime-protect.png":::

1. Dans le dossier Quarantaine, configurez la suppression des éléments du dossier Quarantaine.

    :::image type="content" source="images/removal-items-quarantine1.png" alt-text="Dossier de mise en quarantaine des éléments de suppression" lightbox="images/removal-items-quarantine1.png":::

    :::image type="content" source="images/config-removal-items-quarantine2.png" alt-text="mise en quarantaine config-removal" lightbox="images/config-removal-items-quarantine2.png":::

4. Dans le dossier Analyse, configurez les paramètres d’analyse.

    :::image type="content" source="images/gpo-scans.png" alt-text="Analyses de gpo" lightbox="images/gpo-scans.png":::

### <a name="monitor-all-files-in-real-time-protection"></a>Surveiller tous les fichiers dans la protection en temps réel

Accédez aux **modèles d’administration des** stratégies de  configuration \> \> **de l’ordinateur** **composants** \> \> Windows Protection en **temps réel** de **l’antivirus** \> Microsoft Defender.

:::image type="content" source="images/config-monitor-incoming-outgoing-file-act.png" alt-text="Configurer la surveillance de l’activité de fichier sortant entrant" lightbox="images/config-monitor-incoming-outgoing-file-act.png":::

### <a name="configure-windows-defender-smartscreen-settings"></a>Configurer Windows Defender paramètres SmartScreen

1. Accédez aux **modèles d’administration des** stratégies de configuration  \> \> de **l’ordinateur**, **composants** \> \> Windows **Windows Defender Explorateur SmartScreen**\>.

   :::image type="content" source="images/config-windows-def-smartscr-explorer.png" alt-text="Configurer l’Explorateur d’écrans intelligents Windows Defender" lightbox="images/config-windows-def-smartscr-explorer.png":::
 
2. Accédez aux modèles **d’administration des** stratégies deconfiguration  >  > **de l’ordinateur****composants** >  >  Windows **Windows Defender SmartScreen** > **Microsoft Edge**.

    :::image type="content" source="images/config-windows-def-smartscr-explorer.png" alt-text="Configurer Windows Defender Smart Screen Edge" lightbox="images/config-windows-def-smartscr-explorer.png":::

### <a name="configure-potentially-unwanted-applications"></a>Configurer des applications potentiellement indésirables

Accédez  aux **modèles d’administration des** stratégies de **configuration** \> \> de l’ordinateur, **composants** \> \> Windows Antivirus **Microsoft Defender**.

:::image type="content" source="images/config-potential-unwanted-apps.png" alt-text="Configurer une application indésirable potentielle" lightbox="images/config-potential-unwanted-apps.png":::

:::image type="content" source="images/config-potential-unwanted-apps2.png" alt-text="potentiel de configuration" lightbox="images/config-potential-unwanted-apps2.png":::

### <a name="configure-cloud-deliver-protection-and-send-samples-automatically"></a>Configurer Cloud Deliver Protection et envoyer automatiquement des exemples

Accédez aux  **modèles d’administration des** stratégies de **configuration** \> \> de l’ordinateur: **composants** \> \> Windows **Microsoft Defender Antivirus** \> **MAPS**.

:::image type="content" source="images/gpo-maps1.png" alt-text="Cartes" lightbox="images/gpo-maps1.png":::

:::image type="content" source="images/gpo-maps-block-atfirst-sight.png" alt-text="Bloquer à la première consultation" lightbox="images/gpo-maps-block-atfirst-sight.png":::

:::image type="content" source="images/gpo-maps-join-ms-maps.png" alt-text="Rejoindre microsoft maps" lightbox="images/gpo-maps-join-ms-maps.png":::

:::image type="content" source="images/send-file-sample-further-analysis-require.png" alt-text="Envoyer un exemple de fichier quand une analyse plus approfondie est requise" lightbox="images/send-file-sample-further-analysis-require.png":::

> [!NOTE]
> L’option **Envoyer tous les exemples** fournit l’analyse la plus approfondie des fichiers binaires/scripts/documents, ce qui augmente la posture de sécurité.
L’option **Envoyer des exemples sécurisés** limite le type de fichiers binaires/scripts/documents en cours d’analyse et réduit la posture de sécurité. 

Pour plus d’informations, consultez [Activer la protection cloud dans l’antivirus Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md), la [protection cloud et l’exemple de soumission dans l’Antivirus Microsoft Defender.](cloud-protection-microsoft-antivirus-sample-submission.md)

### <a name="check-for-signature-update"></a>Rechercher la mise à jour de signature

Accédez aux **modèles d’administration des** stratégies de **configuration** \>  \> ordinateur des **composants** \> Windows Composants \> **Microsoft Defender Antivirus** \> **Security Intelligence Mises à jour**.

:::image type="content" source="images/signature-update-1.png" alt-text="Mise à jour de signature" lightbox="images/signature-update-1.png":::

:::image type="content" source="images/signature-update-2.png" alt-text="Mise à jour de définition de signature" lightbox="images/signature-update-2.png":::

### <a name="configure-cloud-deliver-timeout-and-protection-level"></a>Configurer le délai d’expiration et le niveau de protection des livraisons cloud

Accédez aux **modèles d’administration des** stratégies de  configuration \> \> **de l’ordinateur**- **Composants** \> \> Windows **MpEngine** **de l’antivirus** \> Microsoft Defender.
Lorsque vous configurez la stratégie de niveau de protection cloud sur la **stratégie de blocage par défaut de l’Antivirus Microsoft Defender** , cette stratégie est désactivée. C’est ce qui est nécessaire pour définir le niveau de protection sur la valeur par défaut de Windows.

:::image type="content" source="images/config-extended-cloud-check.png" alt-text="configuration d’une vérification cloud étendue" lightbox="images/config-extended-cloud-check.png":::

:::image type="content" source="images/cloud-protection-level.png" alt-text="niveau de protection cloud de configuration" lightbox="images/cloud-protection-level.png":::

## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows à l’aide de Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer les appareils Windows à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md)
- [Intégrer les appareils Windows utilisant un script local](configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md)
- [Résoudre les problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
