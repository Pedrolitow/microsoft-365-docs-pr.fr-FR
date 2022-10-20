---
title: Intégrer les appareils Windows utilisant un script local
description: Utilisez un script local pour déployer le package de configuration sur les appareils afin d’activer l’intégration des appareils au service.
keywords: configurer des appareils à l’aide d’un script local, de la gestion des appareils, de la configuration Microsoft Defender pour point de terminaison des appareils
search.appverid: met150
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
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 20f77106a290462ea01e2897c840c1b40e240d51
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68621808"
---
# <a name="onboard-windows-devices-using-a-local-script"></a>Intégrer les appareils Windows utilisant un script local

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Vous pouvez également intégrer manuellement des appareils individuels à Defender pour point de terminaison. Vous souhaiterez peut-être effectuer cette opération en premier lors du test du service avant de vous engager à intégrer tous les appareils de votre réseau.

> [!IMPORTANT]
> Ce script a été optimisé pour une utilisation sur jusqu’à dix appareils.
> Les scripts locaux sont une méthode d’intégration spéciale pour évaluer Microsoft Defender pour point de terminaison.
> La fréquence de création de rapports de données est plus élevée qu’avec d’autres méthodes d’intégration lors de l’intégration à l’aide d’un script local.
> Ce paramètre est à des fins d’évaluation et n’est normalement pas utilisé dans les déploiements de production. Pour cette raison, il existe des préoccupations concernant l’impact sur l’environnement. Nous vous recommandons donc de limiter à dix le nombre de déploiements utilisant des scripts locaux.
> Si vous effectuez un déploiement dans un environnement de production comme décrit précédemment, utilisez [d’autres options de déploiement](configure-endpoints.md) telles que stratégie de groupe ou Microsoft Endpoint Configuration Manager.

Consultez le [fichier PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)  ou  [Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.vsdx) pour voir les différents chemins d’accès dans le déploiement de Defender pour point de terminaison. 

## <a name="onboard-devices"></a>Intégration des appareils 

1.  Ouvrez le fichier de configuration de la stratégie de groupe .zip (*WindowsDefenderATPOnboardingPackage.zip*) que vous avez téléchargé à partir de l’Assistant Intégration du service. Vous pouvez également obtenir le package à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> :

    1. Dans le volet de navigation, sélectionnez **Paramètres** > **Endpoints** > **Device Management** > **Onboarding**.


Consultez le [fichier PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)  ou  [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) pour voir les différents chemins d’accès dans le déploiement de Defender pour point de terminaison.

1. Ouvrez le fichier de configuration de la stratégie de groupe .zip (*WindowsDefenderATPOnboardingPackage.zip*) que vous avez téléchargé à partir de l’Assistant Intégration du service. Vous pouvez également obtenir le package à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> :
    1. Dans le volet de navigation, sélectionnez **Paramètres** \> **Endpoints** \> **Device Management** \> **Onboarding**.
    2. Sélectionnez Windows 10 ou Windows 11 comme système d’exploitation.
    3. Dans le champ **Méthode de déploiement** , sélectionnez **Script local**.
    4. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

2. Extrayez le contenu du package de configuration à un emplacement sur l’appareil que vous souhaitez intégrer (par exemple, le Bureau). Vous devez avoir un fichier nommé *WindowsDefenderATPLocalOnboardingScript.cmd*.

3. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil et exécutez le script :
   1. Accéder à **Démarrer** et taper **cmd**.
   2. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

    :::image type="content" source="images/run-as-admin.png" alt-text="Menu Démarrer de la fenêtre pointant vers Exécuter en tant qu’administrateur" lightbox="images/run-as-admin.png":::

4.  Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le bureau, *tapez : %userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd*

5.  Appuyez sur la touche **Entrée** ou cliquez sur **OK**.

Pour plus d’informations sur la façon dont vous pouvez vérifier manuellement que l’appareil est conforme et signale correctement les données du capteur, [résolvez Microsoft Defender pour point de terminaison problèmes d’intégration](troubleshoot-onboarding.md).

> [!TIP]
> Après l’intégration de l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un point de terminaison de Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md).

## <a name="configure-sample-collection-settings"></a>Configurer des exemples de paramètres de collecte

Pour chaque appareil, vous pouvez définir une valeur de configuration pour indiquer si des exemples peuvent être collectés à partir de l’appareil lorsqu’une demande est effectuée via Microsoft 365 Defender pour envoyer un fichier à des fins d’analyse approfondie.

Vous pouvez configurer manuellement l’exemple de paramètre de partage sur l’appareil à l’aide de *regedit* ou en créant et en exécutant un fichier *.reg* .

La configuration est définie par le biais de l’entrée de clé de Registre suivante :

```console
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Où le type Name est un D-WORD. Les valeurs possibles sont les suivantes :

- 0 : n’autorise pas le partage d’exemples à partir de cet appareil
- 1 : permet le partage de tous les types de fichiers à partir de cet appareil

La valeur par défaut au cas où la clé de Registre n’existe pas est 1.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Exécuter un test de détection pour vérifier l’intégration

Après l’intégration de l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md).

## <a name="offboard-devices-using-a-local-script"></a>Désintégrage des appareils à l’aide d’un script local

Pour des raisons de sécurité, le package utilisé pour désintégrez les appareils expirera 30 jours après la date de téléchargement. Les packages de désintégrage expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package de désintégrage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de désintégrage ne doivent pas être déployées simultanément sur le même appareil, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package de désintégrage à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> :
    1. Dans le volet de navigation, sélectionnez **Paramètres** \> **Points de terminaison** \> De la **désintégration** **de la gestion** \> des appareils.
    2. Sélectionnez Windows 10 ou Windows 11 comme système d’exploitation.
    3. Dans le champ **Méthode de déploiement** , sélectionnez **Script local**.
    4. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

2. Extrayez le contenu du fichier .zip à un emplacement partagé en lecture seule accessible par les appareils. Vous devez disposer d’un fichier nommé *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil et exécutez le script :
   1. Accéder à **Démarrer** et taper **cmd**.
   2. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

      :::image type="content" source="images/run-as-admin.png" alt-text="Menu Démarrer de Windows pointant vers l’option Exécuter en tant qu’administrateur" lightbox="images/run-as-admin.png":::

4. Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le bureau, tapez : *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

5. Appuyez sur la touche **Entrée** ou cliquez sur **OK**.

> [!IMPORTANT]
> La désintégération entraîne l’arrêt de l’envoi de données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois maximum.

## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil

Vous pouvez suivre les différentes étapes de vérification de la [résolution des problèmes d’intégration](troubleshoot-onboarding.md) pour vérifier que le script s’est correctement terminé et que l’agent est en cours d’exécution.

La surveillance peut également être effectuée directement sur le portail ou à l’aide des différents outils de déploiement.

### <a name="monitor-devices-using-the-portal"></a>Surveiller les appareils à l’aide du portail

1. Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a>.
2. Cliquez sur **Inventaire des appareils**.
3. Vérifiez que les appareils apparaissent.

## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows à l’aide d’une stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer des appareils Windows à l’aide de Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer les appareils Windows à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md)
- [Résoudre les problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
