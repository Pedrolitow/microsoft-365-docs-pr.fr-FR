---
title: Périphériques Windows 10 embarqués à l’aide du gestionnaire de configuration
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Utilisez le gestionnaire de configuration pour déployer le package de configuration sur les appareils afin qu’ils soient intégrés au service.
ms.openlocfilehash: ea1b0cba10dc3e7120192e0c0ee87e2e354f1cc2
ms.sourcegitcommit: 6647055154002c7d3b8f7ce25ad53c9636bc8066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "48769433"
---
# <a name="onboard-windows-10-devices-using-configuration-manager"></a>Périphériques Windows 10 embarqués à l’aide du gestionnaire de configuration

**S’applique à :**

- [Microsoft 365 protection contre la perte de données (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)
- Gestionnaire de configuration de System Center 2012 R2

### <a name="onboard-devices-using-system-center-configuration-manager"></a>Périphériques intégrés à l’aide de System Center Configuration Manager

1. Ouvrez le fichier. zip du package de configuration du gestionnaire de configuration ( *DeviceComplianceOnboardingPackage.zip* ) que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com/).

2. Dans le volet de navigation, sélectionnez **paramètres** d’intégration de l'  >  **appareil**  >  **Onboarding** .

3. Dans le champ **méthode de déploiement** , sélectionnez **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602** .
 
4. Sélectionnez **Télécharger le package** , puis enregistrez le fichier. zip.

5. Extrayez le contenu du fichier. zip vers un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez avoir un fichier nommé *DeviceComplianceOnboardingScript. cmd* .

6. Déployez le package en suivant les étapes décrites dans l’article [packages and Programs dans System Center 2012 R2 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)) .

7. Choisissez une collection d’appareils prédéfinie dans laquelle déployer le package.

> [!NOTE]
> La protection contre la perte de données de point de terminaison Microsoft 365 ne prend pas en charge l’intégration pendant la phase [OOBE (out-of-Box Experience)](https://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87) . Assurez-vous que les utilisateurs ont terminé OOBE après l’installation ou la mise à niveau de Windows.

>[!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, reportez-vous à [la rubrique Run a Detection test on a nouvellement Onboard Microsoft Defender ATP Device](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/run-detection-test).
>
> Notez qu’il est possible de créer une règle de détection sur une application du gestionnaire de configuration pour vérifier en permanence si un périphérique a été intégré. Une application est un autre type d’objet qu’un package et un programme.
> Si un périphérique n’est pas encore intégré (en raison d’une exécution OOBE en attente ou toute autre raison), le gestionnaire de configuration tente de l’intégrer à l’appareil jusqu’à ce que la règle détecte le changement d’État.
> 
> Ce comportement peut être obtenu en créant une règle de détection vérifiant si la valeur de Registre « OnboardingState » (de type REG_DWORD) = 1.
> Cette valeur de Registre se trouve sous « HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status ».
Pour plus d’informations, consultez la rubrique [configure Detection Methods in System Center 2012 R2 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Configurer des paramètres de collection d’exemples

Pour chaque appareil, vous pouvez définir une valeur de configuration indiquant si les échantillons peuvent être collectés à partir de l’appareil lorsqu’une demande est effectuée via le centre de sécurité Microsoft Defender pour soumettre un fichier à une analyse approfondie.

>[!NOTE]
>Ces paramètres de configuration sont généralement effectués via le gestionnaire de configuration. 

Vous pouvez définir une règle de conformité pour l’élément de configuration dans le gestionnaire de configuration afin de modifier le paramètre de partage de l’exemple sur un appareil.

Cette règle doit être un élément de configuration de règle de conformité de *Correction* qui définit la valeur d’une clé de Registre sur les appareils cibles afin de s’assurer qu’ils sont des plaintes.

La configuration est définie par le biais de l’entrée de clé de Registre suivante :

```
Path: “HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection”
Name: "AllowSampleCollection"
Value: 0 or 1
```
Où :<br>
Le type de clé est un D-WORD. <br>
Les valeurs possibles sont les suivantes :
- 0-n’autorise pas le partage d’exemples à partir de cet appareil
- 1-autorise le partage de tous les types de fichiers à partir de cet appareil

La valeur par défaut s’il n’existe pas de clé de Registre est 1.

Pour plus d’informations sur la conformité de System Center Configuration Manager, voir [Introduction to Compliance Settings in System center 2012 R2 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).


## <a name="other-recommended-configuration-settings"></a>Autres paramètres de configuration recommandés
Une fois les périphériques d’intégration au service, il est important de tirer parti des fonctionnalités de protection contre les menaces incluses en les activant avec les paramètres de configuration recommandés suivants.

### <a name="device-collection-configuration"></a>Configuration de la collection d’appareils
Si vous utilisez le gestionnaire de configuration de point de terminaison, la version 2002 ou une version ultérieure, vous pouvez choisir d’élargir le déploiement pour inclure des serveurs ou des clients de bas niveau.


### <a name="next-generation-protection-configuration"></a>Configuration de la protection nouvelle génération

Les paramètres de configuration suivants sont recommandés :

**Analyser**

- Analyser les périphériques de stockage amovibles tels que les lecteurs USB : Oui

**Protection en temps réel**

- Activer la surveillance comportementale : Oui
- Activer la protection contre les applications potentiellement indésirables lors du téléchargement et avant l’installation : Oui

**Service de protection du Cloud**

- Type d’appartenance au service protection du Cloud : appartenance avancée

**Réduction** de la surface d’attaque Configurez toutes les règles disponibles pour l’audit.

>[!NOTE]
> Le blocage de ces activités peut interrompre des processus de gestion légitimes. La meilleure approche consiste à définir tous les éléments sur audit, à identifier ceux qui peuvent être activés, puis à activer ces paramètres sur les points de terminaison qui n’ont pas de détections fausses.

**Protection réseau**

Avant d’activer la protection réseau en mode d’audit ou de blocage, vérifiez que vous avez installé la mise à jour du logiciel anti-programme malveillant, qui peut être obtenue à partir de la [page support](https://support.microsoft.com/en-us/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).


**Accès contrôlé aux dossiers**

Activez la fonctionnalité en mode audit pendant au moins 30 jours. Après cette période, passez en revue les détections et créez une liste des applications autorisées à écrire dans les répertoires protégés.

Pour plus d’informations, consultez la rubrique [Evaluate controled Folder Access](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/evaluate-controlled-folder-access).


## <a name="offboard-devices-using-configuration-manager"></a>Appareils débarquement à l’aide du gestionnaire de configuration

Pour des raisons de sécurité, le package utilisé pour les appareils débarquement expire 30 jours après la date de téléchargement. Les packages par débarquement expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package par débarquement, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et de par débarquement ne doivent pas être déployées sur le même appareil simultanément, sinon cette opération entraîne des collisions imprévisibles.

### <a name="offboard-devices-using-microsoft-endpoint-configuration-manager-current-branch"></a>Périphériques débarquement utilisant la branche actuelle du gestionnaire de configuration de point de terminaison Microsoft

Si vous utilisez la branche actuelle du gestionnaire de configuration de point de terminaison Microsoft, consultez la rubrique [créer un fichier de configuration par débarquement](https://docs.microsoft.com/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Appareils débarquement à l’aide du gestionnaire de configuration System Center 2012 R2

1. Obtenir le package par débarquement à partir du [Centre de conformité Microsoft](https://compliance.microsoft.com/):

2. Dans le volet de navigation, sélectionnez **paramètres** d'  >   **intégration d’appareil** >  **par débarquement** .

3. Sélectionnez Windows 10 comme système d’exploitation.

4. Dans le champ **méthode de déploiement** , sélectionnez **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602** .
    
5. Sélectionnez **Télécharger le package** , puis enregistrez le fichier. zip.

6. Extrayez le contenu du fichier. zip vers un emplacement partagé en lecture seule accessible par les administrateurs réseau qui déploieront le package. Vous devez avoir un fichier nommé *DeviceComplianceOffboardingScript_valid_until_YYYY-mm-dd. cmd* .

7. Déployez le package en suivant les étapes décrites dans l’article [packages and Programs dans System Center 2012 R2 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)) .

8. Choisissez une collection d’appareils prédéfinie dans laquelle déployer le package.

> [!IMPORTANT]
> Par débarquement entraîne l’arrêt de l’envoi des données de capteur au portail, mais les données de l’appareil, y compris la référence à toutes les alertes qu’il a subi, seront conservées pendant 6 mois maximum.


## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil

Si vous utilisez la branche actuelle du gestionnaire de configuration de point de terminaison Microsoft, utilisez le tableau de bord Microsoft Defender ATP intégré dans la console du gestionnaire de configuration. Pour plus d’informations, consultez la rubrique [Microsoft Defender Advanced Threat Protection-Monitor](https://docs.microsoft.com/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Si vous utilisez System Center 2012 R2 Configuration Manager, la surveillance se compose de deux parties :

1. La confirmation du package de configuration a été correctement déployée et est en cours d’exécution (ou s’est exécutée correctement) sur les périphériques de votre réseau.

2. Vérifier que les appareils sont conformes au service de protection contre la perte de données de point de terminaison de Microsoft 365 (cela garantit que l’appareil peut effectuer le processus d’intégration et continuer à signaler les données au service).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Vérifiez que le package de configuration a été correctement déployé

1. Dans la console Configuration Manager, cliquez sur **analyse** en bas du volet de navigation.

2. Sélectionnez **vue d’ensemble** , puis **déploiements** .

3. Sélectionnez sur le déploiement avec le nom du package.

4. Examinez les indicateurs d’État sous **statistiques de saisie semi-automatique** et **État du contenu** .

    En cas d’échec de déploiement (appareils avec **erreur** , **conditions non satisfaites** ou **État d’échec** ), vous devrez peut-être dépanner les appareils. Pour plus d’informations, reportez-vous à la rubrique Dépannage des problèmes d’intégration de la [protection avancée contre les menaces Microsoft](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

    ![Gestionnaire de configuration affichant le déploiement réussi sans erreur](../media/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-365-endpoint-data-loss-prevention-service"></a>Vérifier que les appareils sont compatibles avec le service de protection contre la perte de données du point de terminaison Microsoft 365

Vous pouvez définir une règle de conformité pour l’élément de configuration dans System Center 2012 R2 Configuration Manager pour surveiller votre déploiement.

> [!NOTE]
> Cette procédure et l’entrée de registre s’appliquent au point de terminaison DLP ainsi qu’à la protection avancée contre les menaces.

Cette règle doit être un élément de configuration de règle de conformité *sans correction* qui analyse la valeur d’une clé de Registre sur des appareils ciblés.

Surveillez l’entrée de clé de Registre suivante :
```
Path: “HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status”
Name: “OnboardingState”
Value: “1”
```
Pour plus d’informations, reportez-vous [à Introduction to Compliance Settings dans System Center 2012 R2 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="related-topics"></a>Voir aussi
- [Périphériques Windows 10 embarqués à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md)
- [Périphériques Windows 10 intégrés à l’aide des outils de gestion des appareils mobiles](dlp-configure-endpoints-mdm.md)
- [Périphériques Windows 10 embarqués à l’aide d’un script local](dlp-configure-endpoints-script.md)
- [Périphériques VDI (Virtual Desktop Infrastructure) non persistants](dlp-configure-endpoints-vdi.md)
- [Exécution d’un test de détection sur un appareil Microsoft Defender nouvellement intégré](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Résoudre les problèmes d’intégration de la protection avancée contre les menaces Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
