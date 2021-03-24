---
title: Conditions minimales requises pour Microsoft Defender pour le point de terminaison
description: Comprendre les conditions requises en matière de licences pour l’intégration d’appareils au service
keywords: exigences minimales, licences, tableau de comparaison
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 7581c606a7903bd6d32c1e192f35992899289f30
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51061398"
---
# <a name="minimum-requirements-for-microsoft-defender-for-endpoint"></a>Conditions minimales requises pour Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


Certaines conditions minimales sont requises pour l’intégration d’appareils au service. Découvrez les licences, la configuration matérielle et logicielle requise et d’autres paramètres de configuration pour intégrer des appareils au service.

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à une version d’essai gratuite.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-minreqs-abovefoldlink)

> [!TIP]
> - Découvrez les dernières améliorations apportées à Defender for Endpoint : [Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
> - Defender pour le point de terminaison a démontré les fonctionnalités d’optique et de détection de pointe du secteur dans l’évaluation MITRE récente. Read: [Insights from the MITRE ATT&CK-based evaluation](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

## <a name="licensing-requirements"></a>Critères de licence
Microsoft Defender for Endpoint nécessite l’une des offres de licence en volume Microsoft suivantes :

- Windows 10 Entreprise E5
- Windows 10 Éducation A5
- Microsoft 365 E5 (M365 E5) qui inclut Windows 10 Entreprise E5
- Microsoft 365 A5 (M365 A5)
- Microsoft 365 E5 Sécurité
- Sécurité Microsoft 365 A5
- Microsoft Defender pour point de terminaison

> [!NOTE]
> Les utilisateurs titulaires d’une licence éligible peuvent utiliser Microsoft Defender pour endpoint sur cinq appareils simultanés au plus.
> Microsoft Defender for Endpoint est également disponible à l’achat auprès d’un fournisseur de solutions Cloud (CSP).

Microsoft Defender pour le point de terminaison pour les serveurs nécessite l’une des options de licence suivantes :

- [Centre de sécurité Azure avec Azure Defender activé](https://docs.microsoft.com/azure/security-center/security-center-pricing)
- Microsoft Defender for Endpoint for Server (un par serveur couvert)

> [!NOTE]
> Les clients peuvent acquérir des licences serveur (une par environnement de système d’exploitation de serveur couvert) pour Microsoft Defender pour Endpoint for Servers s’ils ont un minimum combiné de 50 licences pour une ou plusieurs des licences utilisateur suivantes :
>
> * Microsoft Defender pour point de terminaison
> * Windows E5/A5
> * Microsoft 365 E5/A5
> * Sécurité Microsoft 365 E5/A5

Pour obtenir des informations détaillées sur les licences, consultez le [site](https://www.microsoft.com/licensing/terms/) Termes du produit et travaillez avec votre équipe de compte pour en savoir plus sur les conditions générales.

Pour plus d’informations sur le tableau des fonctionnalités des éditions de Windows 10, voir [Comparer les éditions de Windows 10.](https://www.microsoft.com/windowsforbusiness/compare)

Pour obtenir un tableau de comparaison détaillé de la comparaison des éditions commerciales de Windows 10, consultez la comparaison [PDF](https://wfbdevicemanagementprod.blob.core.windows.net/windowsforbusiness/Windows10_CommercialEdition_Comparison.pdf).

## <a name="browser-requirements"></a>Configuration requise pour le navigateur
L’accès à Defender pour le point de terminaison s’fait par le biais d’un navigateur, qui permet de prendre en charge les navigateurs suivants :

- Microsoft Edge
- Internet Explorer version 11
- Google Chrome

> [!NOTE]
> Bien que d’autres navigateurs fonctionnent, les navigateurs mentionnés sont pris en charge.


## <a name="hardware-and-software-requirements"></a>Configuration matérielle et logicielle requise

### <a name="supported-windows-versions"></a>Versions de Windows prise en charge
- Windows 7 SP1 Entreprise ([Nécessite ESU pour la prise en charge](https://docs.microsoft.com/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq).)
- Windows 7 SP1 Professionnel ([Nécessite ESU pour la prise en charge](https://docs.microsoft.com/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq).)
- Windows 8.1 Entreprise
- Windows 8.1 Professionnel
- Windows 10 Entreprise
- [Windows 10 Entreprise LTSC](https://docs.microsoft.com/windows/whats-new/ltsc/)
- Windows 10 Éducation
- Windows 10 Professionnel
- Windows 10 Professionnel Éducation
- Serveur Windows
  - Windows Server 2008 R2 SP1
  - Windows Server 2012 R2
  - Windows Server 2016
  - Windows Server, version 1803 ou ultérieure
  - Windows Server 2019
- Windows Virtual Desktop

Les appareils de votre réseau doivent être en cours d’exécution dans l’une de ces éditions.

La configuration matérielle requise pour Defender pour Endpoint sur les appareils est la même pour les éditions pris en charge.

> [!NOTE]
> Les ordinateurs exécutant des versions mobiles de Windows (comme Windows CE et Windows 10 Mobile) ne sont pas pris en charge.
>
> Les ordinateurs virtuels exécutant Windows 10 Entreprise 2016 LTSB peuvent rencontrer des problèmes de performances s’ils sont exécutés sur des plateformes de virtualisation autres que Microsoft.
>
> Pour les environnements virtuels, nous vous recommandons d’utiliser Windows 10 Entreprise LTSC 2019 ou une édition ultérieure.


### <a name="other-supported-operating-systems"></a>Autres systèmes d’exploitation pris en charge
- Android
- Linux
- macOS

> [!NOTE]
> Vous devez connaître les distributions linux exactes et les versions d’Android et de macOS compatibles avec Defender for Endpoint pour que l’intégration fonctionne.



### <a name="network-and-data-storage-and-configuration-requirements"></a>Configuration requise pour le stockage réseau et les données
Lorsque vous exécutez l’Assistant d’intégration pour la première fois, vous devez choisir l’endroit où sont stockées vos informations relatives au point de terminaison Microsoft Defender : dans l’Union européenne, le Royaume-Uni ou le centre de données des États-Unis.

> [!NOTE]
> - Vous ne pouvez pas modifier votre emplacement de stockage de données après la première installation.
> - Pour plus d’informations sur l’endroit et la façon dont Microsoft stocke vos données, voir Microsoft Defender for [Endpoint data storage and privacy.](data-storage-privacy.md)


### <a name="diagnostic-data-settings"></a>Paramètres des données de diagnostic

> [!NOTE]
> Microsoft Defender pour le point de terminaison ne requiert aucun niveau de diagnostic spécifique tant qu’il est activé.

Assurez-vous que le service de données de diagnostic est activé sur tous les appareils de votre organisation.
Par défaut, ce service est activé. Il est bon de vérifier que vous obtenez des données de capteur à partir de ces données.

Utilisez la ligne de commande pour vérifier le type de démarrage du service de données de **diagnostic Windows 10**:

1. Ouvrez une invite de ligne de commande avec élévation de niveaux sur l’appareil :

   1.  Accéder à **Démarrer** et taper **cmd**.

   1.  Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante, puis appuyez sur **Entrée**:

   ```console
   sc qc diagtrack
   ```

   Si le service est activé, le résultat doit ressembler à la capture d’écran suivante :

   ![Résultat de la commande de requête sc pour diagtrack](images/windefatp-sc-qc-diagtrack.png)


Vous devez configurer le service pour qu’il démarre automatiquement si la START_TYPE **n’est** pas définie sur **AUTO_START**.


**Utilisez la ligne de commande pour configurer le service de données de diagnostic Windows 10 pour démarrer automatiquement :**

1.  Ouvrez une invite de ligne de commande avec élévation de niveaux sur le point de terminaison :

    1. Accéder à **Démarrer** et taper **cmd**.

    1. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2.  Entrez la commande suivante, puis appuyez sur **Entrée**:

    ```console
    sc config diagtrack start=auto
    ```

3.  Un message de réussite s’affiche. Vérifiez la modification en entrant la commande suivante, puis appuyez sur **Entrée**:

    ```console
    sc qc diagtrack
    ```


#### <a name="internet-connectivity"></a>Connexion à Internet
La connectivité Internet sur les appareils est requise directement ou par proxy.

Le capteur Defender pour point de terminaison peut utiliser une bande passante moyenne quotidienne de 5 Mo pour communiquer avec le service cloud Defender for Endpoint et signaler les cyber-données. Les activités non limitées, telles que les téléchargements de fichiers et la collecte de packages d’enquête, ne sont pas incluses dans cette bande passante moyenne quotidienne.

Pour plus d’informations sur les paramètres de configuration de proxy supplémentaires, voir Configurer les [paramètres de proxy d’appareil](configure-proxy-internet.md)et de connectivité Internet.

Avant d’intégrer des appareils, le service de données de diagnostic doit être activé. Le service est activé par défaut dans Windows 10.


## <a name="microsoft-defender-antivirus-configuration-requirement"></a>Configuration requise pour l’Antivirus Microsoft Defender
L’agent Defender for Endpoint dépend de la capacité de l’Antivirus Microsoft Defender à analyser les fichiers et à fournir des informations les concernant.

Configurez les mises à jour d’intelligence de sécurité sur les appareils Defender for Endpoint, que l’Antivirus Microsoft Defender soit ou non le logiciel anti-programme malveillant actif. Pour plus d’informations, voir Gérer les mises à [jour de l’Antivirus Microsoft Defender et appliquer les lignes de base.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus)

Lorsque l’Antivirus Microsoft Defender n’est pas le logiciel anti-programme malveillant actif dans votre organisation et que vous utilisez le service Defender pour point de terminaison, l’Antivirus Microsoft Defender passe en mode passif.

Si votre organisation a désactivé l’Antivirus Microsoft Defender par le biais d’une stratégie de groupe ou d’autres méthodes, les appareils intégrés doivent être exclus de cette stratégie de groupe.

Si vous intégrer des serveurs et que l’Antivirus Microsoft Defender n’est pas le logiciel anti-programme malveillant actif sur vos serveurs, l’Antivirus Microsoft Defender doit être configuré pour passer en mode passif ou désinstallé. La configuration dépend de la version du serveur. Pour plus d’informations, [voir Compatibilité de l’Antivirus Microsoft Defender.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus-compatibility.md)

> [!NOTE]
> Votre stratégie de groupe normale ne s’applique pas à la Protection contre les falsifications et les modifications apportées aux paramètres de l’Antivirus Microsoft Defender sont ignorées lorsque la protection contre la falsification est en cours.


## <a name="microsoft-defender-antivirus-early-launch-antimalware-elam-driver-is-enabled"></a>Le pilote ELAM (Logiciel anti-programme malveillant à lancement rapide) de l’Antivirus Microsoft Defender est activé
Si vous exécutez l’Antivirus Microsoft Defender en tant que produit anti-programme malveillant principal sur vos appareils, l’agent Defender pour Endpoint est correctement intégré.

Si vous exécutez un client anti-programme malveillant tiers et utilisez des solutions de gestion des périphériques mobiles ou Microsoft Endpoint Manager (branche actuelle), vous devez vous assurer que le pilote ELAM de l’Antivirus Microsoft Defender est activé. Pour plus d’informations, [voir s’assurer que l’Antivirus Microsoft Defender n’est pas désactivé par la stratégie.](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)


## <a name="related-topics"></a>Voir aussi
- [Configurer Microsoft Defender pour le déploiement de point de terminaison](production-deployment.md)
- [Appareils intégrés](onboard-configure.md)
