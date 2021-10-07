---
title: Intégrer Windows appareils à l’aide d’un script local
description: Utilisez un script local pour déployer le package de configuration sur les appareils afin d’activer l’intégration des appareils au service.
keywords: configurer des appareils à l’aide d’un script local, la gestion des appareils, configurer Microsoft Defender pour les appareils endpoint
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c00130dba6dcb742ff3f321d7a51edcbfb378f62
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60205678"
---
# <a name="onboard-the-windows-devices-using-a-local-script"></a>Intégrer les appareils Windows à l’aide d’un script local

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Vous pouvez également intégrer manuellement des appareils individuels à Defender for Endpoint. Vous pouvez d’abord le faire lors du test du service avant de vous engager à intégrer tous les appareils de votre réseau.

> [!IMPORTANT]
> Ce script a été optimisé pour une utilisation sur jusqu’à 10 appareils.
>
> Pour déployer à grande échelle, utilisez [d’autres options de déploiement.](configure-endpoints.md) Par exemple, vous pouvez déployer un script d’intégration sur plus de 10 appareils en production avec le script disponible dans les appareils Windows à l’aide de la stratégie [de groupe.](configure-endpoints-gp.md)

## <a name="onboard-devices"></a>Intégration des appareils


Consultez le [fichier PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [ou Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) pour voir les différents chemins d’accès dans le déploiement de Defender for Endpoint.

1. Ouvrez le fichier de package de configuration de .zip de groupe (*WindowsDefenderATPOnboardingPackage.zip*) que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir [du portail Microsoft 365 Defender](https://security.microsoft.com/):
    1. Dans le volet de navigation, sélectionnez **Paramètres** \> **Endpoints** \> **Device Management** \> **Onboarding**.
    2. Sélectionnez Windows 10 ou Windows 11 comme système d’exploitation.
    3. Dans le **champ Méthode de** déploiement, sélectionnez Script **local.**
    4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

2. Extrayez le contenu du package de configuration vers un emplacement sur l’appareil que vous souhaitez intégrer (par exemple, le Bureau). Vous devez avoir un fichier nommé *WindowsDefenderATPLocalOnboardingScript.cmd*.

3. Ouvrez une invite de ligne de commande avec élévation de niveaux sur l’appareil et exécutez le script :
   1. Accéder à **Démarrer** et taper **cmd**.
   2. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

    ![Fenêtre menu Démarrer pointant sur Exécuter en tant qu’administrateur.](images/run-as-admin.png)

4.  Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le Bureau, tapez : *%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd*

5.  Appuyez sur **entrée** ou cliquez sur **OK.**

Pour plus d’informations sur la façon dont vous pouvez vérifier manuellement que l’appareil est conforme et signale correctement les données du capteur, consultez La procédure de résolution des problèmes d’intégration de Microsoft Defender pour les points [de terminaison.](troubleshoot-onboarding.md)

> [!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un point de terminaison [Microsoft Defender pour point de terminaison nouvellement intégré.](run-detection-test.md)

## <a name="configure-sample-collection-settings"></a>Configurer des paramètres de collection d’exemples

Pour chaque appareil, vous pouvez définir une valeur de configuration pour déterminer si des échantillons peuvent être collectés à partir de l’appareil lorsqu’une demande est faite via Microsoft 365 Defender pour soumettre un fichier pour analyse approfondie.

Vous pouvez configurer manuellement le paramètre de partage d’exemples sur l’appareil à l’aide de *regedit* ou en créant et en exécutant *un fichier .reg.*

La configuration est définie par le biais de l’entrée de clé de Registre suivante :

```console
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Où Type de nom est un D-WORD. Les valeurs possibles sont les suivantes :

- 0 : n’autorise pas le partage d’exemples à partir de cet appareil
- 1 : autorise le partage de tous les types de fichiers à partir de cet appareil

La valeur par défaut au cas où la clé de Registre n’existe pas est 1.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Exécuter un test de détection pour vérifier l’intégration

Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un appareil [Microsoft Defender pour point de terminaison nouvellement intégré.](run-detection-test.md)

## <a name="offboard-devices-using-a-local-script"></a>Hors-carte des appareils à l’aide d’un script local

Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages deboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package deboarding à partir [Microsoft 365 Defender portail :](https://security.microsoft.com/)
    1. Dans le volet de navigation, sélectionnez **le Paramètres** de gestion des appareils \> **endpoints.** \>  \> 
    2. Sélectionnez Windows 10 ou Windows 11 comme système d’exploitation.
    3. Dans le **champ Méthode de** déploiement, sélectionnez Script **local.**
    4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

2. Extrayez le contenu du fichier .zip vers un emplacement partagé en lecture seule accessible par les appareils. Vous devez avoir un fichier nommé *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Ouvrez une invite de ligne de commande avec élévation de niveaux sur l’appareil et exécutez le script :
   1. Accéder à **Démarrer** et taper **cmd**.
   2. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

        ![Fenêtre menu Démarrer pointant sur Exécuter en tant qu’administrateur.](images/run-as-admin.png)

4. Tapez l’emplacement du fichier de script. Si vous avez copié le fichier sur le Bureau, tapez : *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

5. Appuyez sur **entrée** ou cliquez sur **OK.**

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.

## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil

Vous pouvez suivre les différentes [](troubleshoot-onboarding.md) étapes de vérification dans la résolution des problèmes d’intégration pour vérifier que le script s’est correctement terminé et que l’agent est en cours d’exécution.

La surveillance peut également être effectuée directement sur le portail ou à l’aide des différents outils de déploiement.

### <a name="monitor-devices-using-the-portal"></a>Surveiller les appareils à l’aide du portail

1. Go to Microsoft 365 Defender portal.
2. Cliquez sur **Inventaire des appareils.**
3. Vérifiez que les appareils apparaissent.

## <a name="related-topics"></a>Rubriques connexes

- [Intégrer des Windows à l’aide de la stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer Windows appareils à l’aide Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer des Windows à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
