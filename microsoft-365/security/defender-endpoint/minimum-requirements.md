---
title: Exigences minimales pour Microsoft Defender pour point de terminaison
description: Comprendre les exigences en matière de licences pour l’intégration d’appareils au service
keywords: exigences minimales, licences, table de comparaison
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 23c02b6df071c8eabd21ecce48d5d0ec2c33e3a2
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68232207"
---
# <a name="minimum-requirements-for-microsoft-defender-for-endpoint"></a>Exigences minimales pour Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-minreqs-abovefoldlink)

Il existe des exigences minimales pour l’intégration d’appareils au service. Découvrez les licences, les exigences matérielles et logicielles, ainsi que d’autres paramètres de configuration pour intégrer des appareils au service.

> [!TIP]
>
> - Cet article décrit la configuration minimale requise pour Microsoft Defender pour point de terminaison plan 2. Si vous recherchez des informations sur Defender pour point de terminaison Plan 1, consultez [La configuration requise pour Defender pour point de terminaison Plan 1](mde-p1-setup-configuration.md#review-the-requirements).
> - Découvrez les dernières améliorations de Defender pour point de terminaison : [Defender pour point de terminaison Tech Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
> - Defender pour point de terminaison a démontré des fonctionnalités d’optique et de détection de pointe dans l’évaluation MITRE récente. Lire : [Informations tirées de l’évaluation de MITRE basée sur ATT&CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Les versions autonomes de [Defender pour point de terminaison Plan 1 et Plan 2](defender-endpoint-plan-1-2.md), même lorsqu’elles sont incluses dans le cadre d’autres plans Microsft 365, n’incluent pas de licences serveur. Pour intégrer des serveurs à ces plans, vous avez besoin de Defender pour serveurs Plan 1 ou Plan 2 dans le cadre de l’offre [Defender pour cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) . Pour en savoir plus, consultez la vue d’ensemble de [Microsoft Defender pour les serveurs](/azure/defender-for-cloud/defender-for-servers-introduction).

Pour plus d’informations sur les exigences en matière de licences pour Microsoft Defender pour point de terminaison, consultez [Microsoft Defender pour point de terminaison informations sur les licences](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint).

Pour obtenir des informations détaillées sur les licences, consultez le [site Termes du produit](https://www.microsoft.com/licensing/terms/) et collaborez avec votre équipe de compte pour en savoir plus sur les conditions générales.

Pour plus d’informations sur le tableau des fonctionnalités des éditions Windows, consultez [Comparer les éditions Windows](https://www.microsoft.com/windowsforbusiness/compare).
## <a name="browser-requirements"></a>Configuration requise pour le navigateur

L’accès à Defender pour point de terminaison s’effectue via un navigateur, qui prend en charge les navigateurs suivants :

- Microsoft Edge
- Google Chrome

> [!NOTE]
> Bien que d’autres navigateurs fonctionnent, ce sont les navigateurs mentionnés qui sont pris en charge.

## <a name="hardware-and-software-requirements"></a>Configuration matérielle et logicielle requise

### <a name="supported-windows-versions"></a>Versions de Windows prises en charge

- Windows 11 Entreprise
- Windows 11 Éducation
- Windows 11 Professionnel
- Windows 11 Professionnel Éducation
- Windows 10 Entreprise
- [Windows 10 Entreprise LTSC 2016 (ou version ultérieure)](/windows/whats-new/ltsc/)
- Windows 10 Entreprise loT

    >[!NOTE]
    >Bien que Windows 10 IoT Entreprise soit un système d’exploitation pris en charge dans Microsoft Defender pour point de terminaison et permet aux OEM/ODM de le distribuer dans le cadre de leur produit ou solution, les clients doivent suivre les instructions de l’OEM/ODM concernant les logiciels installés basés sur l’hôte et la prise en charge.

- Windows 10 Éducation
- Windows 10 Professionnel
- Windows 10 Professionnel Éducation
- Windows 8.1 Entreprise
- Windows 8.1 Professionnel
- Windows 7 SP1 Entreprise ([nécessite esu pour la prise en charge](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq).)
- Windows 7 SP1 Professionnel ([nécessite esu pour la prise en charge](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq).)
- Serveur Windows
  - Windows Server 2008 R2 SP1 ([nécessite esu pour la prise en charge](/windows-server/get-started/extended-security-updates-deploy))
  - Windows Server 2012 R2
  - Windows Server 2016
  - Windows Server, version 1803 ou ultérieure
  - Windows Server 2019
  - Windows Server 2022
- Windows Virtual Desktop
- Windows 365

Les appareils de votre réseau doivent exécuter l’une de ces éditions.

La configuration matérielle requise pour Defender pour point de terminaison sur les appareils est la même pour les éditions prises en charge.

> Cœurs : 2 minimum, 4 mémoires préférées : 1 Go minimum, 4 préférés

Pour plus d’informations sur les versions prises en charge de Windows 10, consultez [Windows 10 informations de publication](/windows/release-health/release-information).

> [!NOTE]
> - Les points de terminaison exécutant des versions mobiles de Windows (par exemple, Windows CE et Windows 10 Mobile) ne sont pas pris en charge.
>
> - Machines Virtuelles Windows 10 Entreprise 2016 LTSB en cours d’exécution peuvent rencontrer des problèmes de performances s’ils sont exécutés sur des plateformes de virtualisation autres que Microsoft.
>
> - Pour les environnements virtuels, nous vous recommandons d’utiliser Windows 10 Entreprise LTSC 2019 ou version ultérieure.
>
> - Les versions autonomes de [Defender pour point de terminaison Plan 1 et Plan 2](defender-endpoint-plan-1-2.md) n’incluent pas de licences serveur. Pour intégrer des serveurs à ces plans, vous avez besoin de Defender pour serveurs Plan 1 ou Plan 2 dans le cadre de l’offre [Defender pour cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) . Pour en savoir plus. Consultez [vue d’ensemble de Microsoft Defender pour les serveurs](/azure/defender-for-cloud/defender-for-servers-introduction).

Lorsque les composants sont à jour sur les systèmes d’exploitation Microsoft Windows, Microsoft Defender pour point de terminaison prise en charge suit le cycle de vie du système d’exploitation respectif. Pour plus d’informations, consultez la [FAQ sur le cycle de vie](/lifecycle/faq/general-lifecycle). Les nouvelles fonctionnalités sont généralement fournies uniquement sur les systèmes d’exploitation qui n’ont pas encore atteint la fin de leur cycle de vie. Les mises à jour du renseignement de sécurité (mises à jour de définition et de moteur) et la logique de détection continueront d’être fournies jusqu’au moins :

- Date [de fin du support](/lifecycle/products/) (pour les systèmes d’exploitation qui n’ont pas de programme esu (Extended Security Mises à jour).
- Fin [de la date ESU](/lifecycle/faq/extended-security-updates) (pour les systèmes d’exploitation qui ont un programme ESU).

### <a name="other-supported-operating-systems"></a>Autres systèmes d’exploitation pris en charge

- [Android](microsoft-defender-endpoint-android.md)
- [iOS](microsoft-defender-endpoint-ios.md)
- [Linux](microsoft-defender-endpoint-linux.md)
- [MacOS](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> Vous devez vérifier que les distributions linux et les versions d’Android, iOS et macOS sont compatibles avec Defender pour point de terminaison pour que l’intégration fonctionne.

### <a name="network-and-data-storage-and-configuration-requirements"></a>Configuration requise pour le stockage réseau et les données

Lorsque vous exécutez l’Assistant Intégration pour la première fois, vous devez choisir l’emplacement où vos informations relatives à Microsoft Defender pour point de terminaison sont stockées : dans l’Union européenne, au Royaume-Uni ou dans le centre de données États-Unis.

> [!NOTE]
>
> - Vous ne pouvez pas modifier votre emplacement de stockage de données après la première configuration.
> - Passez en revue les [Microsoft Defender pour point de terminaison le stockage des données et la confidentialité](data-storage-privacy.md) pour plus d’informations sur l’emplacement et la façon dont Microsoft stocke vos données.

### <a name="diagnostic-data-settings"></a>Paramètres des données de diagnostic

> [!NOTE]
> Microsoft Defender pour point de terminaison ne nécessite pas de niveau de diagnostic spécifique tant qu’il est activé.

Assurez-vous que le service de données de diagnostic est activé sur tous les appareils de votre organisation.
Par défaut, ce service est activé. Il est recommandé de vérifier que vous obtiendrez des données de capteur à partir d’eux.

#### <a name="use-the-command-line-to-check-the-windows-diagnostic-data-service-startup-type"></a>Utiliser la ligne de commande pour vérifier le type de démarrage du service de données de diagnostic Windows

1. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil :
   1. Accéder à **Démarrer** et taper **cmd**.
   2. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante, puis **appuyez sur Entrée** :

   ```console
   sc qc diagtrack
   ```

   Si le service est activé, le résultat doit ressembler à la capture d’écran suivante :

   :::image type="content" source="images/windefatp-sc-qc-diagtrack.png" alt-text="Résultat de la commande de requête sc pour diagtrack" lightbox="images/windefatp-sc-qc-diagtrack.png":::

Vous devez définir le démarrage automatique du service si le **START_TYPE** n’est pas défini sur **AUTO_START**.

#### <a name="use-the-command-line-to-set-the-windows-diagnostic-data-service-to-automatically-start"></a>Utiliser la ligne de commande pour définir le service de données de diagnostic Windows pour démarrer automatiquement

1. Ouvrez une invite de ligne de commande avec élévation de privilèges sur le point de terminaison :
    1. Accéder à **Démarrer** et taper **cmd**.
    2. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante, puis **appuyez sur Entrée** :

    ```console
    sc config diagtrack start=auto
    ```

3. Un message de réussite s’affiche. Vérifiez la modification en entrant la commande suivante, puis **appuyez sur Entrée** :

    ```console
    sc qc diagtrack
    ```

#### <a name="internet-connectivity"></a>Connexion à Internet

La connectivité Internet sur les appareils est requise directement ou par le biais d’un proxy.

Le capteur Defender pour point de terminaison peut utiliser une bande passante moyenne quotidienne de 5 Mo pour communiquer avec le service cloud Defender pour point de terminaison et signaler les cyberdonnées. Les activités ponctuelles telles que les chargements de fichiers et la collecte de packages d’investigation ne sont pas incluses dans cette bande passante moyenne quotidienne.

Pour plus d’informations sur les paramètres de configuration de proxy supplémentaires, consultez [Configurer le proxy d’appareil et les paramètres de connectivité Internet](configure-proxy-internet.md).

Avant d’intégrer des appareils, le service de données de diagnostic doit être activé. Le service est activé par défaut dans Windows 10 et Windows 11.

## <a name="microsoft-defender-antivirus-configuration-requirement"></a>Microsoft Defender configuration de l’antivirus

L’agent Defender pour point de terminaison dépend de la capacité de Microsoft Defender Antivirus à analyser les fichiers et à fournir des informations à leur sujet.

Configurez les mises à jour du renseignement de sécurité sur les appareils Defender pour point de terminaison, que Microsoft Defender Antivirus soit le logiciel anti-programme malveillant actif ou non. Pour plus d’informations, consultez [Gérer les mises à jour antivirus Microsoft Defender et appliquer des lignes de base](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus).

Quand Microsoft Defender Antivirus n’est pas le logiciel anti-programme malveillant actif de votre organisation et que vous utilisez le service Defender pour point de terminaison, Microsoft Defender Antivirus passe en mode passif.

Si votre organisation a désactivé Microsoft Defender Antivirus via une stratégie de groupe ou d’autres méthodes, les appareils intégrés doivent être exclus de cette stratégie de groupe.

Si vous insérez des serveurs et Microsoft Defender Antivirus n’est pas le logiciel anti-programme malveillant actif sur vos serveurs, Microsoft Defender Antivirus doit être configuré pour passer en mode passif ou désinstallé. La configuration dépend de la version du serveur. Pour plus d’informations, consultez [Microsoft Defender compatibilité](microsoft-defender-antivirus-compatibility.md) antivirus.

> [!NOTE]
> Votre stratégie de groupe standard ne s’applique pas à la protection contre les falsifications, et les modifications apportées aux paramètres de l’antivirus Microsoft Defender sont ignorées lorsque la protection contre les falsifications est activée.

## <a name="microsoft-defender-antivirus-early-launch-antimalware-elam-driver-is-enabled"></a>Microsoft Defender pilote ELAM (Early Launch Antimalware) antivirus est activé

Si vous exécutez Microsoft Defender Antivirus en tant que produit anti-programme malveillant principal sur vos appareils, l’agent Defender pour point de terminaison sera correctement intégré.

Si vous exécutez un client anti-programme malveillant tiers et que vous utilisez des solutions Mobile Gestion des appareils ou Microsoft Endpoint Manager (current branch), vous devez vous assurer que le pilote ELAM antivirus Microsoft Defender est activé. Pour plus d’informations, consultez [Vérifier que Microsoft Defender Antivirus n’est pas désactivé par la stratégie](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="related-topics"></a>Voir aussi

- [Configurer Microsoft Defender pour point de terminaison déploiement](production-deployment.md)
- [Intégrer des appareils](onboard-configure.md)
