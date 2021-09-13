---
title: Intégrer Windows 10 appareils à Microsoft Defender pour le point de terminaison via la stratégie de groupe
description: Utilisez la stratégie de groupe pour déployer le package de configuration sur les Windows 10 afin qu’ils soient intégrés au service.
keywords: configurer des appareils à l’aide de la stratégie de groupe, de la gestion des appareils, configurer Microsoft Defender pour les appareils endpoint, intégrer Microsoft Defender pour les appareils endpoint, stratégie de groupe
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 4bd6726550e444ffc31e241b8fb5c52c9967a267
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59203166"
---
# <a name="onboard-the-windows-10-devices-using-group-policy"></a>Intégrer les appareils Windows 10 à l’aide de la stratégie de groupe

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- Stratégie de groupe
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsgp-abovefoldlink)

> [!NOTE]
> Pour utiliser les mises à jour de stratégie de groupe (GP) pour déployer le package, vous devez être sur Windows Server 2008 R2 ou version ultérieure.
>
> Pour Windows Server 2019, vous devrez peut-être remplacer NT AUTHORITY\Well-Known-System-Account par NT AUTHORITY\SYSTEM du fichier XML créé par la préférence de stratégie de groupe.

## <a name="onboard-devices-using-group-policy"></a>Intégrer des appareils à l’aide d’une stratégie de groupe

[![Image du PDF montrant les différents chemins de déploiement.](images/onboard-gp.png)](images/onboard-gp.png#lightbox)

Consultez le [fichier PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf) [ou Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.vsdx) pour voir les différents chemins d’accès dans le déploiement de Defender for Endpoint.

1. Ouvrez le fichier de package de configuration de .zip de groupe (*WindowsDefenderATPOnboardingPackage.zip*) que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir [Microsoft 365 Defender portail :](https://security.microsoft.com/)
    1. Dans le volet de navigation, sélectionnez **Paramètres** \> **Endpoints** \> **Device Management** \> **Onboarding**.  
    2. Sélectionnez Windows 10 comme système d’exploitation.
    3. Dans le **champ Méthode de déploiement,** sélectionnez **Stratégie de groupe.**
    4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

2. Extrayez le contenu du .zip vers un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un dossier appelé *OptionalParamsPolicy* et le fichier *WindowsDefenderATPOnboardingScript.cmd*.

3. Pour créer un objet de stratégie de groupe, ouvrez la [Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) de gestion des **stratégies** de groupe (GPMC), cliquez avec le bouton droit sur Objets de stratégie de groupe à configurer, puis cliquez sur **Nouveau.** Entrez le nom du nouvel GPO dans la boîte de dialogue qui s’affiche, puis cliquez sur **OK**.

4. Ouvrez [la Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

5. Dans **l’Éditeur de gestion des stratégies** de groupe, allez à **Configuration** ordinateur, puis **Préférences,** puis **paramètres du panneau de configuration.**

6. Cliquez avec le bouton droit **sur Tâches programmées,** pointez sur **Nouveau,** puis cliquez sur **Tâche immédiate (au moins Windows 7).**

7. Dans la **fenêtre** Tâche qui s’ouvre, allez dans **l’onglet** Général. Sous **Options de sécurité,** cliquez **sur Modifier l’utilisateur ou** le groupe, puis tapez SYSTEM, puis cliquez sur Vérifier les **noms,** **puis OK.** NT AUTHORITY\SYSTEM apparaît en tant que compte d’utilisateur que la tâche exécutera.

8. Sélectionnez **Exécuter, que l’utilisateur soit** connecté ou non, puis cochez la case Exécuter avec les **privilèges les plus élevés.**

9. Dans le champ Nom, tapez un nom approprié pour la tâche programmée (par exemple, Defender pour le déploiement de point de terminaison).

10. Go to the **Actions** tab and select **New...** **Assurez-vous que démarrer un programme** est sélectionné dans le champ **Action.** Entrez le chemin d’accès UNC, à l’aide du nom de domaine complet (FQDN) du serveur de fichiers, du fichier *WindowsDefenderATPOnboardingScript.cmd* partagé.

11. Sélectionnez **OK** et fermez toutes les fenêtres GPMC ouvertes.

12. Pour lier l’GPO à une unité d’organisation, cliquez avec le bouton droit et sélectionnez **Lier un GPO existant.** Dans la boîte de dialogue qui s’affiche, sélectionnez l’objet de stratégie de groupe à lier. Cliquez sur **OK**.

> [!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier que l’appareil est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un appareil [Defender for Endpoint nouvellement intégré.](run-detection-test.md)

## <a name="additional-defender-for-endpoint-configuration-settings"></a>Paramètres de configuration defender supplémentaires pour les points de terminaison

Pour chaque appareil, vous pouvez déterminer si des échantillons peuvent être collectés à partir de l’appareil lorsqu’une demande est faite via Microsoft 365 Defender pour soumettre un fichier pour analyse approfondie.

Vous pouvez utiliser la stratégie de groupe (GP) pour configurer des paramètres, tels que les paramètres de l’exemple de partage utilisé dans la fonctionnalité d’analyse approfondie.

### <a name="configure-sample-collection-settings"></a>Configurer des paramètres de collection d’exemples

1. Sur votre appareil de gestion de la gp, copiez les fichiers suivants à partir du package de configuration :

    - Copier _AtpConfiguration.admx_ dans _C : Windows \\ \\ PolicyDefinitions_

    - Copier _AtpConfiguration.adml_ dans _C : Windows \\ \\ PolicyDefinitions \\ en-US_

    Si vous utilisez un magasin central pour les modèles d’administration de stratégie de groupe, copiez les fichiers [suivants](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra)à partir du package de configuration :

    - Copier _AtpConfiguration.admx_ dans _\\ \\ \<forest.root\> \\ SysVol \\ \<forest.root\> \\ Policies \\ PolicyDefinitions_

    - Copier _AtpConfiguration.adml_ dans _\\ \\ \<forest.root\> \\ SysVol \\ \<forest.root\> \\ Policies \\ PolicyDefinitions \\ en-US_

2. Ouvrez la [Console de gestion des stratégies](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11)de groupe, cliquez avec le bouton droit sur l’GPO que vous souhaitez configurer, puis cliquez sur **Modifier.**

3. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration de l’ordinateur.**

4. Cliquez **sur Stratégies,** **puis Modèles d’administration.**

5. Cliquez **Windows composants,** **puis Windows Defender ATP**.

6. Choisissez d’activer ou de désactiver le partage d’exemples à partir de vos appareils.

> [!NOTE]
> Si vous ne définissez pas de valeur, la valeur par défaut consiste à activer la collection d’exemples.

## <a name="other-recommended-configuration-settings"></a>Autres paramètres de configuration recommandés

### <a name="update-endpoint-protection-configuration"></a>Mettre à jour la configuration de la protection des points de terminaison

Après avoir configuré le script d’intégration, continuez à modifier la même stratégie de groupe pour ajouter des configurations de protection des points de terminaison. Effectuez des modifications de stratégie de groupe à partir d’un système exécutant Windows 10 ou Server 2019 pour vous assurer que vous avez toutes les fonctionnalités Antivirus Microsoft Defender requises. Vous devrez peut-être fermer et rouvrir l’objet de stratégie de groupe pour inscrire les paramètres de configuration de Defender ATP.

Toutes les stratégies se trouvent sous `Computer Configuration\Policies\Administrative Templates` .

**Emplacement de la stratégie** : \Windows\Windows Defender ATP

Politique|Setting
---|---
Enable\Disable Sample collection|Activé : vérification « Activer la collecte d’exemples sur les ordinateurs »

<br>

**Emplacement de la stratégie** : \Windows\Antivirus Microsoft Defender

Politique|Setting
---|---
Configurer la détection pour les applications potentiellement indésirables|Activé, Bloquer

<br>

**Emplacement de la stratégie** : \Windows\Antivirus Microsoft Defender\MAPS

Politique|Setting
---|---
Rejoindre Microsoft MAPS|Enabled, Advanced MAPS
Envoyer des exemples de fichiers lorsque des analyses plus approfondies sont requises | Activé, Envoyer des exemples sûrs

<br>

**Emplacement de la stratégie** : \Windows\Antivirus Microsoft Defender\Protection en temps réel

Politique|Setting
---|---
Désactiver la protection en temps réel|Désactivé
Activer l’analyse du comportement|Activé
Analyser tous les fichiers et pièces jointes téléchargés|Activé
Surveiller l’activité des fichiers et des programmes sur votre ordinateur|Activé

<br>

**Emplacement de la stratégie** : \Windows\Antivirus Microsoft Defender\Scan

Ces paramètres configurent des analyses périodiques du point de terminaison. Nous vous recommandons d’effectuer une analyse rapide hebdomadaire, autorisant les performances.

Politique|Setting
---|---
Recherchez les dernières informations sur la sécurité des virus et logiciels espions avant d’exécution d’une analyse programmée |Activé

<br>

**Emplacement de la stratégie** : \Windows\Antivirus Microsoft Defender\Protection contre les attaques Microsoft Defender\Réduction de la surface d’attaque

Obtenir la liste actuelle des GUID de réduction de la surface d’attaque à partir des règles de personnalisation des règles de [réduction de la surface d’attaque](customize-attack-surface-reduction.md)

1. Ouvrez la **stratégie Configurer la Réduction de la surface d’attaque.**

1. Sélectionnez **Activé**.

1. Sélectionnez le **bouton** Afficher.

1. Ajoutez chaque GUID dans le **champ Nom de** la valeur avec la valeur 2.

   Chacun d’eux est alors uniquement mis en place pour l’audit.

   ![Image de la configuration de réduction de la surface d’attaque.](images/asr-guid.png)

Politique|Setting
---|---
Configurer l’accès contrôlé aux dossiers| Activé, mode audit

## <a name="run-a-detection-test-to-verify-onboarding"></a>Exécuter un test de détection pour vérifier l’intégration

Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un appareil [Microsoft Defender pour point de terminaison nouvellement intégré.](run-detection-test.md)

## <a name="offboard-devices-using-group-policy"></a>Appareils de tableau de bord à l’aide de la stratégie de groupe

Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages deboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package deboarding à partir [Microsoft 365 Defender portail :](https://security.microsoft.com/)
    1. Dans le volet de navigation, sélectionnez **le Paramètres** de gestion des appareils \> **endpoints.** \>  \> 
    2. Sélectionnez Windows 10 comme système d’exploitation.
    3. Dans le **champ Méthode de déploiement,** sélectionnez **Stratégie de groupe.**
    4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

2. Extrayez le contenu du .zip vers un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un fichier nommé *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Ouvrez [la Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

4. Dans **l’Éditeur de gestion des stratégies** de groupe, allez à **Configuration ordinateur,** puis **Préférences,** puis **paramètres du panneau de configuration.**

5. Cliquez avec le bouton droit **sur Tâches programmées,** pointez sur **Nouveau,** puis cliquez sur **Tâche immédiate.**

6. Dans la **fenêtre** Tâche qui s’ouvre, allez dans **l’onglet** Général. Choisissez le compte d’utilisateur SYSTÈME local (BUILTIN\SYSTEM) sous **Options de sécurité.**

7. Sélectionnez **Exécuter, que l’utilisateur soit** connecté ou non, puis cochez la case Exécuter avec les privilèges les plus **élevés.**

8. Dans le champ Nom, tapez un nom approprié pour la tâche programmée (par exemple, Defender pour le déploiement de point de terminaison).

9. Go to the **Actions** tab and select **New...**. **Assurez-vous que démarrer un programme** est sélectionné dans le champ **Action.** Entrez le chemin d’accès UNC, à l’aide du nom de domaine complet (FQDN) du serveur de fichiers, du fichier *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd* partagé.

10. Sélectionnez **OK** et fermez toutes les fenêtres GPMC ouvertes.

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.

## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil

Avec la stratégie de groupe, il n’est pas possible de surveiller le déploiement des stratégies sur les appareils. La surveillance peut être effectuée directement sur le portail ou à l’aide des différents outils de déploiement.

## <a name="monitor-devices-using-the-portal"></a>Surveiller les appareils à l’aide du portail

1. Go to [Microsoft 365 Defender portal](https://security.microsoft.com/).
2. Cliquez sur **Inventaire des appareils.**
3. Vérifiez que les appareils apparaissent.

> [!NOTE]
> L’affichage des appareils dans la liste Appareils peut prendre plusieurs **jours.** Cela inclut le temps qu’il faut pour que les stratégies soient distribuées à l’appareil, le temps qu’il faut avant que l’utilisateur se connecte et le temps qu’il faut au point de terminaison pour commencer à créer des rapports.

## <a name="setup-defender-av-policies"></a>Stratégies de l’Antivirus Setup Defender

Créez une stratégie de groupe ou groupez ces paramètres avec les autres stratégies. Cela dépend de l’environnement des clients et de la façon dont ils souhaitent déployer le service en ciblant différentes unités d’organisation (unités d’organisation).

1. Après avoir choisi la gp ou en créer une nouvelle, modifiez-la.
2. Accédez à **Modèles d’administration** des stratégies de configuration ordinateur  >    >    >  **Windows composants**  >  **Antivirus Microsoft Defender**  >  **protection en temps réel.**
:::image type="content" source="images/realtime-protect.png" alt-text="protection en temps réel.":::
1. Dans le dossier Quarantaine, configurez la suppression des éléments du dossier Quarantaine.

    :::image type="content" source="images/removal-items-quarantine1.png" alt-text="dossier de mise en quarantaine des éléments de suppression.":::

    :::image type="content" source="images/config-removal-items-quarantine2.png" alt-text="mise en quarantaine de la suppression de la config.":::

4. Dans le dossier Analyse, configurez les paramètres d’analyse.

    :::image type="content" source="images/gpo-scans.png" alt-text="analyses gpo.":::

### <a name="monitor-all-files-in-real-time-protection"></a>Surveiller tous les fichiers dans la protection en temps réel

Accédez à **Modèles d’administration** des stratégies de configuration ordinateur \>  \>  \> **Windows composants** \> **Antivirus Microsoft Defender** \> **protection en temps réel.**

:::image type="content" source="images/config-monitor-incoming-outgoing-file-act.png" alt-text="configurer la surveillance de l’activité des fichiers sortants entrants.":::

### <a name="configure-windows-defender-smart-screen-settings"></a>Configurer les Windows Defender de l’écran intelligent

1. Accédez à **Modèles d’administration** des stratégies de \>  \>  \> **configuration ordinateur Windows composants** \> **Windows Defender’explorateur SmartScreen.** \> 

    :::image type="content" source="images/config-windows-def-smartscr-explorer.png" alt-text="config windows defender smart screen explorer.":::
 
2. Accédez à **Modèles d’administration** des stratégies de configuration ordinateur  >    >    >  **Windows composants**  >  **Windows Defender SmartScreen**  >  **Microsoft Edge**.

    :::image type="content" source="images/config-windows-def-smartscr-explorer.png" alt-text="Config windows defender smart screen Edge.":::

### <a name="configure-potentially-unwanted-applications"></a>Configurer les applications potentiellement indésirables

Accédez à **Modèles d’administration** des stratégies de configuration ordinateur \>  \>  \> **Windows composants** \> **Antivirus Microsoft Defender**.

:::image type="content" source="images/config-potential-unwanted-apps.png" alt-text="config de l’application potentielle indésirable.":::

:::image type="content" source="images/config-potential-unwanted-apps2.png" alt-text="potentiel de la config.":::

### <a name="configure-cloud-deliver-protection-and-send-samples-automatically"></a>Configurer cloud Deliver Protection et envoyer automatiquement des exemples

Accédez à **Modèles d’administration** des stratégies de configuration ordinateur \>  \>  \> **Windows composants** \> **Antivirus Microsoft Defender** \> **MAPS**.

:::image type="content" source="images/gpo-maps1.png" alt-text="cartes.":::

:::image type="content" source="images/gpo-maps-block-atfirst-sight.png" alt-text="bloquer à la première vue.":::

:::image type="content" source="images/gpo-maps-join-ms-maps.png" alt-text="rejoignez Microsoft Maps.":::

:::image type="content" source="images/send-file-sample-further-analysis-require.png" alt-text="envoyer un exemple de fichier lorsque des analyses plus approfondies sont requises.":::

### <a name="check-for-signature-update"></a>Vérifier la mise à jour des signatures

Accédez aux **modèles d’administration** des stratégies de configuration \>  \>  \> **ordinateur Windows composants** \> **Antivirus Microsoft Defender** \> **mises à jour des signatures**

:::image type="content" source="images/signature-update-1.png" alt-text="mise à jour de signature.":::

:::image type="content" source="images/signature-update-2.png" alt-text="mise à jour de définition de signature.":::

### <a name="configure-cloud-deliver-timeout-and-protection-level"></a>Configurer le délai d’out de livraison cloud et le niveau de protection

Accédez à **Modèles d’administration** des stratégies de configuration ordinateur \>  \>  \> **Windows composants** \> **Antivirus Microsoft Defender** \> **MpEngine**.
Lorsque vous configurez la stratégie de niveau de protection cloud Antivirus Microsoft Defender stratégie de blocage par **défaut,** la stratégie est désactivée. C’est ce qui est nécessaire pour définir le niveau de protection sur les fenêtres par défaut.

:::image type="content" source="images/config-extended-cloud-check.png" alt-text="vérification étendue du cloud.":::

:::image type="content" source="images/cloud-protection-level.png" alt-text="niveau de protection cloud de la config.":::

## <a name="related-topics"></a>Rubriques connexes

- [Intégrer Windows 10 appareils à l’aide Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md)
- [Intégrer les appareils Windows 10 utilisant un script local](configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un microsoft Defender pour les appareils de point de terminaison nouvellement intégré](run-detection-test.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
