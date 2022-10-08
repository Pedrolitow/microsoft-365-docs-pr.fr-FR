---
title: Intégrer des appareils Windows à l’aide de Configuration Manager
description: Utilisez Configuration Manager pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service Defender pour point de terminaison.
keywords: intégrer des appareils à l’aide de sccm, gestion des appareils, configurer Microsoft Defender pour point de terminaison appareils
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
- tier1
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 09/22/2021
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 2cfbb87d3ce2edad9156f73898fd7765f2aad3f3
ms.sourcegitcommit: 2ff545246fec060ea7829da5afbc1cdc698d51ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68363318"
---
# <a name="onboard-windows-devices-using-configuration-manager"></a>Intégrer des appareils Windows à l’aide de Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Endpoint Configuration Manager Current Branch
- System Center 2012 Configuration Manager R2

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointssccm-abovefoldlink)

## <a name="prerequisites"></a>Configuration requise
- [Rôle de système de site de point Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-site-role)

> [!IMPORTANT]
> Le rôle de système de site de point Endpoint Protection est requis pour que les stratégies de réduction de la surface d’attaque et antivirus soient correctement déployées sur les points de terminaison ciblés.  Sans ce rôle, les points de terminaison de la collection d’appareils ne recevront pas les stratégies de réduction de la surface d’attaque et antivirus configurées.

Vous pouvez utiliser Configuration Manager pour intégrer des points de terminaison au service Microsoft Defender pour point de terminaison. 

Vous pouvez utiliser plusieurs options pour intégrer des appareils à l’aide de Configuration Manager :
- [Intégrer des appareils à l’aide de System Center Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [Attachement du client](/mem/configmgr/tenant-attach/)



Pour Windows Server 2012 R2 et Windows Server 2016, après avoir effectué les étapes d’intégration, vous devez [configurer et mettre à jour System Center Endpoint Protection clients](onboard-downlevel.md#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
> Defender pour point de terminaison ne prend pas en charge l’intégration pendant la phase [OOBE (Out-Of-Box Experience](/windows-hardware/test/assessments/out-of-box-experience) ). Assurez-vous que les utilisateurs effectuent une opération OOBE après avoir exécuté l’installation ou la mise à niveau de Windows.
>
> Notez qu’il est possible de créer une règle de détection sur une application Configuration Manager pour vérifier en permanence si un appareil a été intégré. Une application est un type d’objet différent d’un package et d’un programme.
> Si un appareil n’est pas encore intégré (en raison de l’achèvement OOBE en attente ou d’une autre raison), Configuration Manager réessayez d’intégrer l’appareil jusqu’à ce que la règle détecte le changement d’état.
>
> Ce comportement peut être effectué en créant une règle de détection vérifiant si la valeur de Registre « OnboardingState » (de type REG_DWORD) = 1.
> Cette valeur de Registre se trouve sous « HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status ».
Pour plus d’informations, consultez [Configurer les méthodes de détection dans System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Configurer des exemples de paramètres de collecte

Pour chaque appareil, vous pouvez définir une valeur de configuration pour indiquer si des exemples peuvent être collectés à partir de l’appareil lorsqu’une demande est effectuée via Microsoft 365 Defender pour envoyer un fichier à des fins d’analyse approfondie.

> [!NOTE]
> Ces paramètres de configuration sont généralement effectués via Configuration Manager.

Vous pouvez définir une règle de conformité pour l’élément de configuration dans Configuration Manager pour modifier le paramètre d’exemple de partage sur un appareil.

Cette règle doit *être un élément* de configuration de règle de conformité qui définit la valeur d’une clé de Registre sur les appareils ciblés pour s’assurer qu’elles sont conformes.

La configuration est définie par le biais de l’entrée de clé de Registre suivante :

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Où le type de clé est un D-WORD. Les valeurs possibles sont les suivantes :

- 0 : n’autorise pas le partage d’exemples à partir de cet appareil
- 1 : Autorise le partage de tous les types de fichiers à partir de cet appareil

La valeur par défaut au cas où la clé de Registre n’existe pas est 1.

Pour plus d’informations sur la conformité System Center Configuration Manager, consultez [Présentation des paramètres de conformité dans System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="other-recommended-configuration-settings"></a>Autres paramètres de configuration recommandés

Après avoir intégré des appareils au service, il est important de tirer parti des fonctionnalités de protection contre les menaces incluses en les activant avec les paramètres de configuration recommandés suivants.

### <a name="device-collection-configuration"></a>Configuration de la collection d’appareils

Si vous utilisez endpoint Configuration Manager, version 2002 ou ultérieure, vous pouvez choisir d’élargir le déploiement pour inclure des serveurs ou des clients de bas niveau.

### <a name="next-generation-protection-configuration"></a>Configuration de la protection de nouvelle génération

Les paramètres de configuration suivants sont recommandés :

#### <a name="scan"></a>Analyser

- Analyser les périphériques de stockage amovibles tels que les lecteurs USB : Oui

#### <a name="real-time-protection"></a>Protection en temps réel

- Activer la surveillance comportementale : Oui
- Activer la protection contre les applications potentiellement indésirables au téléchargement et avant l’installation : Oui

#### <a name="cloud-protection-service"></a>Cloud Protection Service

- Type d’appartenance au service de protection cloud : appartenance avancée

#### <a name="attack-surface-reduction"></a>Réduction de la surface d'attaque

Configurez toutes les règles disponibles pour auditer.

> [!NOTE]
> Le blocage de ces activités peut interrompre des processus métier légitimes. La meilleure approche consiste à tout définir pour l’audit, à identifier ceux qui peuvent être activés sans risque, puis à activer ces paramètres sur les points de terminaison qui n’ont pas de détections de faux positifs.

Pour déployer des stratégies d’antivirus (AV) et de réduction de la surface d’attaque (ASR) via Microsoft Endpoint Configuration Manager (SCCM), procédez comme suit :

- Activez Endpoint Protection et configurez les paramètres client personnalisés.
- Installez le client Endpoint Protection à partir d’une invite de commandes.
- Vérifiez l’installation du client Endpoint Protection.

##### <a name="enable-endpoint-protection-and-configure-custom-client-settings"></a>Activer Endpoint Protection et configurer les paramètres client personnalisés
Suivez les étapes pour activer la protection des points de terminaison et la configuration des paramètres client personnalisés :

1. Dans la console Configuration Manager, cliquez sur **Administration.**
1. Dans l’espace **de travail Administration** , cliquez sur **Paramètres du client.**
1. Sous l’onglet **Accueil** , dans le groupe **Créer** , cliquez sur **Créer des paramètres d’appareil client personnalisé.**
1. Dans la boîte de dialogue **Créer des paramètres d’appareil client personnalisé** , fournissez un nom et une description pour le groupe de paramètres, puis sélectionnez **Endpoint Protection.**
1. Configurez les paramètres client Endpoint Protection dont vous avez besoin. Pour obtenir la liste complète des paramètres client Endpoint Protection que vous pouvez configurer, consultez la section Endpoint Protection dans [À propos des paramètres client.](/mem/configmgr/core/clients/deploy/about-client-settings#endpoint-protection)

    > [!IMPORTANT]
    > Installez le rôle de système de site Endpoint Protection avant de configurer les paramètres client pour Endpoint Protection.

1. Cliquez sur **OK** pour fermer la boîte de dialogue **Créer des paramètres d’appareil client personnalisé** . Les nouveaux paramètres client sont affichés dans le nœud **Paramètres client** de l’espace de travail **Administration** .
1. Ensuite, déployez les paramètres client personnalisés sur une collection. Sélectionnez les paramètres client personnalisés que vous souhaitez déployer. Sous l’onglet **Accueil** , dans le groupe **Paramètres du client** , cliquez sur **Déployer.**
1. Dans la boîte de dialogue **Sélectionner un regroupement** , choisissez la collection dans laquelle vous souhaitez déployer les paramètres client, puis cliquez sur **OK.** Le nouveau déploiement s’affiche sous l’onglet **Déploiements** du volet d’informations.

Les clients sont configurés avec ces paramètres lors du prochain téléchargement de la stratégie client. Pour plus d’informations, consultez [Lancer la récupération de stratégie pour un client Configuration Manager.](/mem/configmgr/core/clients/manage/manage-clients)


##### <a name="installation-of-endpoint-protection-client-from-a-command-prompt"></a>Installation du client Endpoint Protection à partir d’une invite de commandes
Suivez les étapes pour terminer l’installation du client Endpoint Protection à partir de l’invite de commandes.

1. Copiez **scepinstall.exe** du dossier **Client** du dossier d’installation Configuration Manager sur l’ordinateur sur lequel vous souhaitez installer le logiciel client Endpoint Protection.
1. Ouvrez une invite de commandes en tant qu’administrateur. Remplacez le répertoire par le dossier avec le programme d’installation. ```scepinstall.exe```Exécutez ensuite, en ajoutant toutes les propriétés de ligne de commande supplémentaires dont vous avez besoin :

     |**Propriété**  |**Description**  |
     |---------|---------|
     |```/s```      |Exécuter le programme d’installation en mode silencieux|
     |```/q```      |Extraire les fichiers d’installation en mode silencieux|
     |```/i```      |Exécuter le programme d’installation normalement|
     |```/policy``` |Spécifier un fichier de stratégie anti-programme malveillant pour configurer le client pendant l’installation|
     |```/sqmoptin```|Participer au Programme d’amélioration de l’expérience client (CEIP) Microsoft|

1. Suivez les instructions à l’écran pour terminer l’installation du client.
1. Si vous avez téléchargé le dernier package de définition de mise à jour, copiez-le sur l’ordinateur client, puis double-cliquez sur le package de définition pour l’installer.

     > [!NOTE]
     > Une fois l’installation du client Endpoint Protection terminée, le client effectue automatiquement une vérification de mise à jour de définition. Si cette vérification de mise à jour réussit, vous n’avez pas besoin d’installer manuellement le dernier package de mise à jour de définition.

**Exemple : installer le client avec une stratégie anti-programme malveillant**

```scepinstall.exe /policy <full path>\<policy file>```

##### <a name="verify-the-endpoint-protection-client-installation"></a>Vérifier l’installation du client Endpoint Protection

Après avoir installé le client Endpoint Protection sur votre ordinateur de référence, vérifiez que le client fonctionne correctement.

1. Sur l’ordinateur de référence, ouvrez **System Center Endpoint Protection** à partir de la zone de notification Windows.
1. Sous l’onglet **Accueil** de la **boîte de dialogue System Center Endpoint Protection**, vérifiez que la **protection en temps réel** est activée **.**
1. Vérifiez que **la mise à jour** est affichée pour **les définitions de virus et de logiciels espions.**
1. Pour vous assurer que votre ordinateur de référence est prêt pour l’imagerie, sous **Options d’analyse,** sélectionnez **Complet,** puis cliquez sur **Analyser maintenant.**


#### <a name="network-protection"></a>Protection réseau

Avant d’activer la protection réseau en mode audit ou bloquer, vérifiez que vous avez installé la mise à jour de la plateforme anti-programme malveillant, qui peut être obtenue à partir de la [page de support](https://support.microsoft.com/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

#### <a name="controlled-folder-access"></a>Accès contrôlé aux dossiers

Activez la fonctionnalité en mode audit pendant au moins 30 jours. Après cette période, passez en revue les détections et créez une liste d’applications autorisées à écrire dans des répertoires protégés.

Pour plus d’informations, consultez [Évaluer l’accès contrôlé aux dossiers](evaluate-controlled-folder-access.md).

## <a name="run-a-detection-test-to-verify-onboarding"></a>Exécuter un test de détection pour vérifier l’intégration

Après l’intégration de l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md).

## <a name="offboard-devices-using-configuration-manager"></a>Désins border des appareils à l’aide de Configuration Manager

Pour des raisons de sécurité, le package utilisé pour désintégrez les appareils expirera 30 jours après la date de téléchargement. Les packages de désintégrage expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package de désintégrage, vous êtes averti de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de désintégrage ne doivent pas être déployées simultanément sur le même appareil, sinon cela provoquera des collisions imprévisibles.

### <a name="offboard-devices-using-microsoft-endpoint-manager-current-branch"></a>Désins border des appareils à l’aide de Microsoft Endpoint Manager current branch

Si vous utilisez Microsoft Endpoint Manager current branch, consultez [Créer un fichier de configuration de désintégrage](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Appareils hors-carte utilisant System Center 2012 R2 Configuration Manager

1. Obtenez le package de désintégrage à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> :
    1. Dans le volet de navigation, sélectionnez **Paramètres** \> **Points de terminaison** \> De la **désintégration** **de la gestion** \> des appareils.  
    1. Sélectionnez Windows 10 ou Windows 11 comme système d’exploitation.
    1. Dans le champ **Méthode de déploiement**, sélectionnez **System Center Configuration Manager 2012/2012 R2/1511/1602**.
    1. Sélectionnez **Télécharger le package** et enregistrez le fichier .zip.

2. Extrayez le contenu du fichier .zip dans un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez disposer d’un fichier nommé *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Déployez le package en suivant les [étapes décrites dans l’article Packages et programmes de System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)).

   Choisissez une collection d’appareils prédéfinie sur laquelle déployer le package.

> [!IMPORTANT]
> La désintégération entraîne l’arrêt de l’envoi de données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois maximum.

## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil

Si vous utilisez Microsoft Endpoint Manager current branch, utilisez le tableau de bord Defender pour point de terminaison intégré dans la console Configuration Manager. Pour plus d’informations, consultez [Defender pour point de terminaison - Monitor](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Si vous utilisez System Center 2012 R2 Configuration Manager, la surveillance se compose de deux parties :

1. Confirmer que le package de configuration a été correctement déployé et qu’il est en cours d’exécution (ou qu’il s’est exécuté avec succès) sur les appareils de votre réseau.

2. En vérifiant que les appareils sont conformes au service Defender pour point de terminaison (cela garantit que l’appareil peut terminer le processus d’intégration et continuer à signaler des données au service).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Vérifier que le package de configuration a été correctement déployé

1. Dans la console Configuration Manager, cliquez sur **Surveillance** en bas du volet de navigation.

2. Sélectionnez **Vue d’ensemble** , puis **Déploiements**.

3. Sélectionnez sur le déploiement avec le nom du package.

4. Passez en revue les indicateurs d’état sous **Statistiques d’achèvement** et **État du contenu**.

    En cas d’échec des déploiements (appareils avec des états **d’erreur**, **d’exigences non respectées** ou **d’échec**), vous devrez peut-être résoudre les problèmes des appareils. Pour plus d’informations, consultez [La résolution des problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md).

    :::image type="content" source="images/sccm-deployment.png" alt-text="Le Configuration Manager montrant un déploiement réussi sans erreur" lightbox="images/sccm-deployment.png":::

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-defender-for-endpoint-service"></a>Vérifier que les appareils sont conformes au service Microsoft Defender pour point de terminaison

Vous pouvez définir une règle de conformité pour l’élément de configuration dans System Center 2012 R2 Configuration Manager pour surveiller votre déploiement.

Cette règle doit être un élément *de configuration de règle de conformité qui ne corrige pas* la valeur d’une clé de Registre sur les appareils ciblés.

Surveillez l’entrée de clé de Registre suivante :

```console
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Pour plus d’informations, consultez [Présentation des paramètres de conformité dans System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows à l’aide d’une stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer les appareils Windows à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md)
- [Intégrer les appareils Windows utilisant un script local](configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md)
- [Résoudre les problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
