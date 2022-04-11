---
title: Intégrer des appareils Windows 10 et Windows 11 à l’aide de Configuration Manager
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Utilisez Configuration Manager pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service.
ms.openlocfilehash: 2cca9cc073ca08c7fabb19511a4253e4a682057a
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760710"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-configuration-manager"></a>Intégrer des appareils Windows 10 et Windows 11 à l’aide de Configuration Manager

**S’applique à :**

- [Protection contre la perte de données de point de terminaison (DLP) pour Microsoft 365](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

### <a name="onboard-devices-using-system-center-configuration-manager"></a>Intégrer des appareils à l’aide de System Center Configuration Manager

1. Obtenez le fichier de package de configuration .zip (*DeviceComplianceOnboardingPackage.zip*) à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com/).

2. Dans le volet de navigation, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a> >  **Device OnboardingOnboarding** > .

3. Dans le champ **Méthode de déploiement**, sélectionnez **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602**.

4. Sélectionnez **Télécharger le package** et enregistrez le fichier .zip.

5. Extrayez le contenu du fichier .zip dans un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez disposer d’un fichier nommé *DeviceComplianceOnboardingScript.cmd*.

6. Déployez le package en suivant les [étapes décrites dans l’article Packages et programmes de System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)).

7. Choisissez une collection d’appareils prédéfinie sur laquelle déployer le package.

> [!NOTE]
> Microsoft 365 protection des informations ne prend pas en charge l’intégration pendant la phase [OOBE (Out-Of-Box Experience).](https://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87) Assurez-vous que les utilisateurs effectuent une opération OOBE après avoir exécuté Windows installation ou mise à niveau.

> [!TIP]
> Après l’intégration de l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un appareil Pertahanan Microsoft untuk Titik Akhir nouvellement intégré](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test).
>
> Notez qu’il est possible de créer une règle de détection sur une application Configuration Manager pour vérifier en permanence si un appareil a été intégré. Une application est un type d’objet différent d’un package et d’un programme.
> Si un appareil n’est pas encore intégré (en raison de l’achèvement OOBE en attente ou d’une autre raison), Configuration Manager réessayez d’intégrer l’appareil jusqu’à ce que la règle détecte le changement d’état.
>
> Ce comportement peut être effectué en créant une règle de détection vérifiant si la valeur de Registre « OnboardingState » (de type REG_DWORD) = 1.
> Cette valeur de Registre se trouve sous « HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status ».
Pour plus d’informations, consultez [Configurer les méthodes de détection dans System Center Configuration Manager 2012 R2](/previous-versions/system-center/system-center-2012-R2/gg682159(v=technet.10)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Configurer des exemples de paramètres de collecte

Pour chaque appareil, vous pouvez définir une valeur de configuration pour indiquer si des exemples peuvent être collectés à partir de l’appareil lorsqu’une demande est effectuée via Centre de sécurité Microsoft Defender pour envoyer un fichier à des fins d’analyse approfondie.

> [!NOTE]
> Ces paramètres de configuration sont généralement effectués via Configuration Manager.

Vous pouvez définir une règle de conformité pour l’élément de configuration dans Configuration Manager pour modifier le paramètre d’exemple de partage sur un appareil.

Cette règle doit être un élément de configuration de règle de conformité de *correction* qui définit la valeur d’une clé de Registre sur les appareils ciblés pour s’assurer qu’elles sont plaintes.

La configuration est définie par le biais de l’entrée de clé de Registre suivante :

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Où :

Le type de clé est un D-WORD.

Les valeurs possibles sont les suivantes :

- 0 : n’autorise pas le partage d’exemples à partir de cet appareil
- 1 : permet le partage de tous les types de fichiers à partir de cet appareil

La valeur par défaut au cas où la clé de Registre n’existe pas est 1.

Pour plus d’informations sur la conformité System Center Configuration Manager, consultez [Présentation des paramètres de conformité dans System Center Configuration Manager 2012 R2](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).


## <a name="other-recommended-configuration-settings"></a>Autres paramètres de configuration recommandés

Après avoir intégré des appareils au service, il est important de tirer parti des fonctionnalités de protection contre les menaces incluses en les activant avec les paramètres de configuration recommandés suivants.

### <a name="device-collection-configuration"></a>Configuration de la collection d’appareils

Si vous utilisez endpoint Configuration Manager, version 2002 ou ultérieure, vous pouvez choisir d’élargir le déploiement pour inclure des serveurs ou des clients de bas niveau.

### <a name="next-generation-protection-configuration"></a>Configuration de la protection de nouvelle génération

Les paramètres de configuration suivants sont recommandés :

**Analyser**

- Analyser les périphériques de stockage amovibles tels que les lecteurs USB : Oui

**Protection en temps réel**

- Activer la surveillance comportementale : Oui
- Activer la protection contre les applications potentiellement indésirables au téléchargement et avant l’installation : Oui

**Cloud Protection Service**

- Type d’appartenance au service de protection cloud : appartenance avancée

**Réduction de la surface d’attaque** Configurez toutes les règles disponibles pour auditer.

> [!NOTE]
> Le blocage de ces activités peut interrompre des processus métier légitimes. La meilleure approche consiste à tout définir pour l’audit, à identifier ceux qui peuvent être activés sans risque, puis à activer ces paramètres sur les points de terminaison qui n’ont pas de détections de faux positifs.

**Protection du réseau**

Avant d’activer la protection réseau en mode audit ou bloquer, vérifiez que vous avez installé la mise à jour de la plateforme anti-programme malveillant, qui peut être obtenue à partir de la [page de support](https://support.microsoft.com/en-us/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

**Accès contrôlé aux dossiers**

Activez la fonctionnalité en mode audit pendant au moins 30 jours. Après cette période, passez en revue les détections et créez une liste d’applications autorisées à écrire dans des répertoires protégés.

Pour plus d’informations, consultez [Évaluer l’accès contrôlé aux dossiers](/windows/security/threat-protection/microsoft-defender-atp/evaluate-controlled-folder-access).

## <a name="offboard-devices-using-configuration-manager"></a>Désins border des appareils à l’aide de Configuration Manager

Pour des raisons de sécurité, le package utilisé pour désintégrez les appareils expirera 30 jours après la date de téléchargement. Les packages de désintégrage expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package de désintégrage, vous êtes averti de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de désintégrage ne doivent pas être déployées simultanément sur le même appareil, sinon cela provoquera des collisions imprévisibles.

### <a name="offboard-devices-using-microsoft-endpoint-configuration-manager-current-branch"></a>Désintégrage des appareils à l’aide de Microsoft Endpoint Configuration Manager branche active

Si vous utilisez Microsoft Endpoint Configuration Manager branche active, consultez [Créer un fichier de configuration de désintégrage](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Appareils hors carte utilisant System Center 2012 R2 Configuration Manager

1. Obtenez le package de désintégrage à partir de <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365</a> :

2. Dans le volet de navigation, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Paramètres**</a> >   **Device onboardingOffboarding**> .

3. Sélectionnez Windows 10 comme système d’exploitation.

4. Dans le champ **Méthode de déploiement**, sélectionnez **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602**.

5. Sélectionnez **Télécharger le package** et enregistrez le fichier .zip.

6. Extrayez le contenu du fichier .zip dans un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez disposer d’un fichier nommé *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

7. Déployez le package en suivant les [étapes décrites dans l’article Packages et programmes de System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)).

8. Choisissez une collection d’appareils prédéfinie sur laquelle déployer le package.

> [!IMPORTANT]
> La désintégération entraîne l’arrêt de l’envoi de données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois maximum.

## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil

Si vous utilisez Microsoft Endpoint Configuration Manager branche active, utilisez le tableau de bord intégré Pertahanan Microsoft untuk Titik Akhir dans la console Configuration Manager. Pour plus d’informations, consultez [Microsoft Defender Advanced Threat Protection - Monitor](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Si vous utilisez System Center Configuration Manager R2 2012, la surveillance se compose de deux parties :

1. Confirmer que le package de configuration a été correctement déployé et qu’il est en cours d’exécution (ou qu’il s’est exécuté avec succès) sur les appareils de votre réseau.

2. Vérifier que les appareils sont conformes au service d’intégration d’appareil Microsoft 365 (cela garantit que l’appareil peut terminer le processus d’intégration et continuer à signaler des données au service).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Vérifier que le package de configuration a été correctement déployé

1. Dans la console Configuration Manager, cliquez sur **Surveillance** en bas du volet de navigation.

2. Sélectionnez **Vue d’ensemble** , puis **Déploiements**.

3. Sélectionnez sur le déploiement avec le nom du package.

4. Passez en revue les indicateurs d’état sous **Statistiques d’achèvement** et **État du contenu**.

    En cas d’échec des déploiements (appareils avec des états **d’erreur**, **d’exigences non respectées** ou **d’échec**), vous devrez peut-être résoudre les problèmes des appareils. Pour plus d’informations, consultez [La résolution des problèmes d’intégration de Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

    ![Configuration Manager montrant un déploiement réussi sans erreur.](../media/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-365-endpoint-data-loss-prevention-service"></a>Vérifiez que les appareils sont conformes au service de protection contre la perte de données de point de terminaison Microsoft 365

Vous pouvez définir une règle de conformité pour l’élément de configuration dans System Center Configuration Manager 2012 R2 pour surveiller votre déploiement.

> [!NOTE]
> Cette procédure et cette entrée de Registre s’appliquent à Endpoint DLP ainsi qu’à Defender pour point de terminaison.

Cette règle doit être un élément *de configuration de règle de conformité qui ne corrige pas* la valeur d’une clé de Registre sur les appareils ciblés.

Surveillez l’entrée de clé de Registre suivante :

```text
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Pour plus d’informations, consultez [Présentation des paramètres de conformité dans System Center Configuration Manager R2 2012](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).

## <a name="related-topics"></a>Voir aussi

- [Intégrer des appareils Windows 10 et Windows 11 à l’aide de stratégie de groupe](device-onboarding-gp.md)
- [Intégrer les appareils Windows 10 et Windows 11 à l’aide des outils de gestion des périphériques mobiles](device-onboarding-mdm.md)
- [Intégrer les appareils Windows 10 et Windows 11 en utilisant un script local](device-onboarding-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](device-onboarding-vdi.md)
- [Exécuter un test de détection sur un appareil Pertahanan Microsoft untuk Titik Akhir nouvellement intégré](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Résoudre les problèmes d’intégration de Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
