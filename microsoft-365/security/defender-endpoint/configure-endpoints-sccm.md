---
title: Appareils Windows 10 intégrés utilisant Configuration Manager
description: Utilisez Configuration Manager pour déployer le package de configuration sur les appareils afin que les appareils soient intégrés au service.
keywords: intégrer des appareils à l’aide de sccm, gestion des appareils, configurer Microsoft Defender pour les appareils endpoint
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
ms.date: 02/07/2020
ms.technology: mde
ms.openlocfilehash: 925e76c595b8714ebc0aaf41329b5edb94967434b6acce46431d326047d4c572
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53874117"
---
# <a name="onboard-the-windows-10-devices-using-configuration-manager"></a>Intégrer les appareils Windows 10 à l’aide de Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Endpoint Configuration Manager branche actuelle
- Gestionnaire de configuration de System Center 2012 R2

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointssccm-abovefoldlink)

## <a name="supported-client-operating-systems"></a>Systèmes d’exploitation clients pris en charge

En fonction de la version de Configuration Manager que vous exécutez, les systèmes d’exploitation clients suivants peuvent être intégrés :

#### <a name="configuration-manager-version-1910-and-prior"></a>Configuration Manager version 1910 et versions antérieures

- Ordinateurs clients exécutant Windows 10 

#### <a name="configuration-manager-version-2002-and-later"></a>Configuration Manager version 2002 et ultérieures

À partir de Configuration Manager version 2002, vous pouvez intégrer les systèmes d’exploitation suivants :

- Windows 8.1
- Windows 10
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server 2016, version 1803 ou ultérieure
- Windows Server 2019

>[!NOTE]
>Pour plus d’informations sur la façon d’intégrer Windows Server 2012 R2, Windows Server 2016 et Windows Server 2019, consultez la Windows [serveurs intégrés.](configure-server-endpoints.md)



### <a name="onboard-devices-using-system-center-configuration-manager"></a>Intégrer des appareils à l’aide System Center Configuration Manager


[![Image du PDF montrant les différents chemins de déploiement](images/onboard-config-mgr.png)](images/onboard-config-mgr.png#lightbox)


Consultez le [fichier PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf) [ou Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.vsdx) pour voir les différents chemins d’accès dans le déploiement de Microsoft Defender pour Endpoint. 


1. Ouvrez le fichier de package de configuration Configuration Manager .zip (*WindowsDefenderATPOnboardingPackage.zip*) que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir [Microsoft 365 Defender portail :](https://security.microsoft.com/)

    1. Dans le volet de navigation, sélectionnez **Paramètres**  >  **Endpoints**  >  **Device Management**  >  **Onboarding**.
    
    1. Sélectionnez Windows 10 comme système d’exploitation.

    1. Dans le champ Méthode **de** déploiement, **sélectionnez System Center Configuration Manager 2012/2012 R2/1511/1602**.
    
    1. Sélectionnez **le package** de téléchargement et enregistrez .zip fichier.

2. Extrayez le contenu du fichier .zip vers un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez avoir un fichier nommé *WindowsDefenderATPOnboardingScript.cmd*.

3. Déployez le package en suivant les étapes de l’article Packages et programmes [System Center 2012 R2 Configuration Manager.](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\))

    a. Choisissez une collection d’appareils prédéfiny pour déployer le package.

> [!NOTE]
> Defender pour le point de terminaison ne prend pas en charge l’intégration pendant la phase [OOBE (Out-Of-Box Experience).](https://answers.microsoft.com/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87) Assurez-vous que les utilisateurs ont terminé la OOBE après Windows’installation ou de mise à niveau.

> [!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un appareil [Defender for Endpoint nouvellement intégré.](run-detection-test.md)
>
> Notez qu’il est possible de créer une règle de détection sur une application Configuration Manager pour vérifier en permanence si un appareil a été intégré. Une application est un type d’objet différent d’un package et d’un programme.
> Si un appareil n’est pas encore intégré (en raison de l’exécution de la OOBE en attente ou d’une autre raison), Configuration Manager réessaye d’intégrer l’appareil jusqu’à ce que la règle détecte le changement d’état.
>
> Ce comportement peut être réalisé en créant une règle de détection vérifiant si la valeur de Registre « OnboardingState » (de type REG_DWORD) = 1.
> Cette valeur de Registre se trouve sous « HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status ».
Pour plus d’informations, [voir Configure Detection Methods in System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Configurer des paramètres de collection d’exemples

Pour chaque appareil, vous pouvez définir une valeur de configuration pour déterminer si des échantillons peuvent être collectés à partir de l’appareil lorsqu’une demande est faite via Microsoft 365 Defender pour soumettre un fichier pour analyse approfondie.

> [!NOTE]
> Ces paramètres de configuration sont généralement effectués via Configuration Manager.

Vous pouvez définir une règle de conformité pour l’élément de configuration dans Configuration Manager afin de modifier le paramètre de partage d’exemples sur un appareil.

Cette règle doit  être un élément de configuration de règle de conformité de correction qui définit la valeur d’une clé de Registre sur les appareils ciblés pour s’assurer qu’ils sont conformes.

La configuration est définie par le biais de l’entrée de clé de Registre suivante :

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Où Type de clé est un D-WORD. Les valeurs possibles sont les suivantes :

- 0 : n’autorise pas le partage d’exemples à partir de cet appareil
- 1 : autorise le partage de tous les types de fichiers à partir de cet appareil

La valeur par défaut au cas où la clé de Registre n’existe pas est 1.

Pour plus d’informations sur System Center Configuration Manager conformité, voir Introduction aux paramètres de conformité dans [System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="other-recommended-configuration-settings"></a>Autres paramètres de configuration recommandés

Une fois les appareils intégrés au service, il est important de tirer parti des fonctionnalités de protection contre les menaces incluses en les activant avec les paramètres de configuration recommandés suivants.

### <a name="device-collection-configuration"></a>Configuration de la collection d’appareils

Si vous utilisez Endpoint Configuration Manager, version 2002 ou ultérieure, vous pouvez choisir d’élargir le déploiement pour inclure des serveurs ou des clients de bas niveau.

### <a name="next-generation-protection-configuration"></a>Configuration de la protection nouvelle génération

Les paramètres de configuration suivants sont recommandés :

#### <a name="scan"></a>Analyser

- Analyser les périphériques de stockage amovibles tels que les lecteurs USB : Oui

#### <a name="real-time-protection"></a>Protection en temps réel

- Activer la surveillance comportementale : Oui
- Activer la protection contre les applications potentiellement indésirables au téléchargement et avant l’installation : Oui

#### <a name="cloud-protection-service"></a>Cloud Protection Service

- Type d’appartenance au service Cloud Protection : appartenance avancée

#### <a name="attack-surface-reduction"></a>Réduction de la surface d'attaque

Configurez toutes les règles disponibles pour auditer.

> [!NOTE]
> Le blocage de ces activités peut interrompre les processus d’entreprise légitimes. La meilleure approche consiste à définir tous les paramètres à auditer, à identifier ceux qui sont sûrs à activer, puis à activer ces paramètres sur les points de terminaison qui n’ont pas de détections de faux positifs.

#### <a name="network-protection"></a>Protection réseau

Avant d’activer la protection réseau en mode audit ou blocage, assurez-vous que vous avez installé la mise à jour de la plateforme anti-programme malveillant, qui peut être obtenue à partir de la [page de support.](https://support.microsoft.com/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing)

#### <a name="controlled-folder-access"></a>Accès contrôlé aux dossiers

Activez la fonctionnalité en mode audit pendant au moins 30 jours. Après cette période, examinez les détections et créez une liste d’applications autorisées à écrire dans des répertoires protégés.

Pour plus d’informations, voir [Évaluer l’accès contrôlé aux dossiers.](evaluate-controlled-folder-access.md)

## <a name="offboard-devices-using-configuration-manager"></a>Hors-carte des appareils à l’aide de Configuration Manager

Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages deboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

### <a name="offboard-devices-using-microsoft-endpoint-manager-current-branch"></a>Appareils deboard à l’aide Microsoft Endpoint Manager branche actuelle

Si vous utilisez Microsoft Endpoint Manager branche actuelle, consultez Créer un fichier [de configuration deboarding.](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file)

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Appareils de déboardage utilisant System Center Configuration Manager 2012 R2


1. Obtenez le package deboarding à partir [Microsoft 365 Defender portail :](https://security.microsoft.com/)
    1. Dans le volet de navigation, sélectionnez **le Paramètres** de gestion des appareils  >  **endpoints.**  >    >   
    1. Sélectionnez Windows 10 comme système d’exploitation.
    1. Dans le champ Méthode **de** déploiement, **sélectionnez System Center Configuration Manager 2012/2012 R2/1511/1602**.
    1. Sélectionnez **le package** de téléchargement et enregistrez .zip fichier.

2. Extrayez le contenu du fichier .zip vers un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez avoir un fichier nommé *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Déployez le package en suivant les étapes de l’article Packages et programmes [System Center 2012 R2 Configuration Manager.](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\))

   Choisissez une collection d’appareils prédéfiny pour déployer le package.

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.

## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil

Si vous utilisez la Microsoft Endpoint Manager actuelle, utilisez le tableau de bord Defender for Endpoint intégré dans la console Configuration Manager. Pour plus d’informations, [voir Defender for Endpoint - Monitor](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Si vous utilisez System Center 2012 R2 Configuration Manager, la surveillance se compose de deux parties :

1. Confirmation que le package de configuration a été correctement déployé et qu’il est en cours d’exécution (ou s’est exécuté correctement) sur les appareils de votre réseau.

2. Vérification de la conformité des appareils avec le service Defender for Endpoint (cela garantit que l’appareil peut terminer le processus d’intégration et continuer à signaler des données au service).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Vérifier que le package de configuration a été correctement déployé

1. Dans la console Configuration Manager, cliquez **sur Analyse** en bas du volet de navigation.

2. Sélectionnez **Vue d’ensemble,** puis **Déploiements.**

3. Sélectionnez le déploiement avec le nom du package.

4. Examinez les indicateurs d’état sous **Statistiques d’achèvement** et **État du contenu.**

    En cas d’échec des déploiements (appareils avec **erreur,** conditions requises non remplies ou états d’échec), vous devrez peut-être résoudre les problèmes des appareils. Pour plus d’informations, voir résoudre les problèmes d’intégration de Microsoft Defender pour les points [de terminaison.](troubleshoot-onboarding.md)

    ![Configuration Manager affichant un déploiement réussi sans erreur](images/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-defender-for-endpoint-service"></a>Vérifier que les appareils sont conformes au service Microsoft Defender for Endpoint

Vous pouvez définir une règle de conformité pour l’élément de configuration dans System Center 2012 R2 Configuration Manager pour surveiller votre déploiement.

Cette règle doit être un élément de configuration de règle de conformité *sans* correction qui surveille la valeur d’une clé de Registre sur des appareils ciblés.

Surveillez l’entrée de clé de Registre suivante :

```console
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Pour plus d’informations, voir Introduction aux paramètres de conformité [dans System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="related-topics"></a>Sujets connexes

- [Intégrer des Windows 10 à l’aide de la stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md)
- [Intégrer les appareils Windows 10 utilisant un script local](configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
