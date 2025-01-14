---
title: Gérer les mises à jour de Antivirus Microsoft Defender et appliquer des lignes de base
description: Gérez la façon dont Antivirus Microsoft Defender reçoit les mises à jour de protection et de produit.
keywords: mises à jour, bases de référence de sécurité, protection, planification des mises à jour, mises à jour forcées, mises à jour mobiles, wsus
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: high
ms.date: 10/31/2022
audience: ITPro
ms.topic: reference
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr, mkaminska, v-vutrieu
manager: dansimp
ms.subservice: mde
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 6ecc138f1eb02dcbac6ac3c46252e45c1e91ae37
ms.sourcegitcommit: 4bae15909267a70c8842bd0cd3dceb8459b4cc29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68798252"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-apply-baselines"></a>Gérer les mises à jour de Antivirus Microsoft Defender et appliquer des lignes de base

**S’applique à :**
- [Plans 1 et 2 de Microsoft Defender pour points de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Il est essentiel de maintenir Antivirus Microsoft Defender à jour pour garantir que vos appareils disposent des dernières technologies et fonctionnalités nécessaires pour se protéger contre les nouveaux programmes malveillants et techniques d’attaque. Veillez à mettre à jour votre protection antivirus, même si Antivirus Microsoft Defender s’exécute en [mode passif](microsoft-defender-antivirus-compatibility.md). Il existe deux types de mises à jour liées à la mise à jour des Antivirus Microsoft Defender :

- [Mises à jour de la veille de sécurité](#security-intelligence-updates)
- [Mises à jour de produit](#product-updates)

> [!TIP]
> Pour connaître la date de signature, de plateforme et de moteur la plus récente, consultez les [Mises à jour de la veille de sécurité pour Antivirus Microsoft Defender et d’autres](https://www.microsoft.com/en-us/wdsi/defenderupdates)

## <a name="security-intelligence-updates"></a>Mises à jour de la veille de sécurité

Microsoft Defender Antivirus utilise [la protection fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md) (également appelé Microsoft Advanced Protection Service ou MAPS) et télécharge régulièrement des mises à jour de la veille de sécurité dynamiques pour fournir une protection supplémentaire. Ces mises à jour dynamiques ne remplacent pas les mises à jour régulières du renseignement de sécurité via la mise à jour du renseignement de sécurité KB2267602.

> [!NOTE]
> Les mises à jour sont publiées sous les bases de connaissances suivantes :
> - Antivirus Microsoft Defender : KB2267602
> - Protection du point de terminaison du centre du système : KB2461484

La protection fournie par le cloud est toujours activée et nécessite une connexion active à Internet pour fonctionner. Les mises à jour de la veille de sécurité se produisent à une cadence planifiée (configurable via une stratégie). Pour plus d’informations, consultez [Utiliser la protection fournie par le cloud dans Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

Pour obtenir la liste des mises à jour récentes de veille de sécurité de sécurité, consultez [Mises à jour de la veille de sécurité pour Antivirus Microsoft Defender et d’autres anti-programme malveillant Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates).

Les mises à jour du moteur sont incluses avec les mises à jour de la veille de sécurité et sont publiées à une cadence mensuelle.

## <a name="product-updates"></a>Mises à jour de produit

Antivirus Microsoft Defender nécessite des [mises à jour mensuelles (KB4052623)](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform) appelées *mises à jour de plateforme*.

Vous pouvez gérer la distribution des mises à jour via l’une des méthodes suivantes :

- [Service de mise à jour du serveur Windows (WSUS)](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)
- [Microsoft Endpoint Configuration Manager](/configmgr/sum/understand/software-updates-introduction)
- La méthode habituelle que vous utilisez pour déployer des mises à jour Microsoft et Windows sur des points de terminaison de votre réseau.

Pour plus d’informations, consultez [Gérer les sources des mises à jour de protection de Antivirus Microsoft Defender](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

> [!NOTE]
> - Les mises à jour mensuelles sont publiées par phases, ce qui entraîne l’affichage de plusieurs packages dans vos [Services de mise à jour du serveur Windows](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus).
> - Cet article répertorie les modifications incluses dans le canal de publication étendu. [Consultez la dernière version du canal étendu ici](https://www.microsoft.com/security/encyclopedia/adlpackages.aspx?action=info).
> - Pour en savoir plus sur le processus de déploiement progressif et pour plus d’informations sur la prochaine version, consultez [Gérer le processus de déploiement progressif pour les mises à jour Microsoft Defender](manage-gradual-rollout.md).
> - Pour en savoir plus sur les mises à jour de veille de sécurité, consultez [Mises à jour de la veille de sécurité pour Antivirus Microsoft Defender et d’autres anti-programme malveillant Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates).
> - Si vous recherchez une liste des processus Microsoft Defender, **[téléchargez le classeur mde-urls](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)**, puis sélectionnez la feuille de calcul **Processus Microsoft Defender**. Le classeur mde-urls répertorie également les services et les URL associées auxquels votre réseau doit être en mesure de se connecter, comme décrit dans [Activer l’accès aux URL du service Microsoft Defender pour point de terminaison dans le serveur proxy](configure-proxy-internet.md).

## <a name="monthly-platform-and-engine-versions"></a>Versions mensuelles de la plateforme et du moteur

Pour plus d’informations sur la mise à jour ou l’installation de la mise à jour de la plateforme, consultez [Mise à jour pour la plateforme anti-programme malveillant de Windows Defender](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform).

Toutes nos mises à jour contiennent

- Améliorations en termes de performances
- Améliorations de la facilité de service
- Améliorations de l’intégration (Cloud, [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender))
<br/><br/>
<details>
<summary>Octobre-2022 (Plateforme : 4.18.2210.4 | Moteur : 1.1.19800.x)</summary>

&ensp;Version de mise à jour du renseignement de sécurité : **x.x**<br/>
&ensp;Date de publication : **31 octobre 2022**<br/>
&ensp;Plateforme : **4.18.2210.4**<br/>
&ensp;Moteur : **1.1.19800.x**<br/>
&ensp;Phase de support : **Mises à jour critiques et relatives à la sécurité**<br/>

Version du moteur : 1.1.19800.x (*numéro de version final bientôt disponible*)<br/>
Version de mise à jour du renseignement de sécurité : x.x (*bientôt disponible*)<br/>

### <a name="whats-new"></a>Nouveautés

- Détection améliorée des blocages dans le moteur antivirus 
- Ajout de l’adhésion aux mises à jour defender pendant le processus OOBE (out-of-box experience) 
- Amélioration de la [fonctionnalité de protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) 
- Modification de la & de gestion des vulnérabilités (TVM) - alerte et action de blocage TVM pour bloquer pour résoudre le rapport de Intune 
- Suppression de l’action de nettoyage de Intune stratégie pour`ThreadSeverityDefaultAction` 
- Ajout de la configuration aléatoire des heures planifiées des tâches à Intune stratégie 
- Ajout de la facilité de gestion pour la `DisableSMTPParsing` protection réseau 
- Ajout d’une amélioration pour la surveillance du comportement 
- Format de date normalisé pour l’événement 1151 pour Windows Defender 
- Correction d’un blocage lié à la mise à jour `\device\cdrom*` des exclusions lors du montage d’un lecteur cdrom dans certaines conditions 
- Amélioration des informations PID pour la détection des menaces 

### <a name="known-issues"></a>Problèmes connus

- Aucun  
<br/><br/>
</details><details>
<summary>Septembre-2022 (Plateforme : 4.18.2209.7 | Moteur : 1.1.19700.3)</summary>

&ensp;Version de mise à jour du renseignement de sécurité : **1.377.8.0**<br/>
&ensp;Date de publication : **10 octobre 2022**<br/>
&ensp;Plateforme : **4.18.2209.7**<br/>
&ensp;Moteur : **1.1.19700.3**<br/>
&ensp;Phase de support : **Mises à jour critiques et relatives à la sécurité**<br/>

Version du moteur : 1.1.19700.3<br/>
Version de mise à jour du renseignement de sécurité : 1.377.8.0<br/>

### <a name="whats-new"></a>Nouveautés

- Amélioration du traitement de l’ordre de secours Defender sur la référence SKU du serveur
- Correction des mises à jour de Defender pendant le processus OOBE
- Correction de la vulnérabilité du descripteur de sécurité du programme d’installation approuvé
- Correction Microsoft Defender la visibilité [des exclusions antivirus](configure-exclusions-microsoft-defender-antivirus.md)
- Correction de la sortie de l’ordre de secours de l’applet de commande PowerShell
- Correction de l’échec de mise à jour de la plateforme Defender sur les références SKU Server Core 2019
- Amélioration de la prise en charge du renforcement des configurations de désactivation de Defender sur les références SKU de serveur
- Amélioration des logiques de configuration Defender pour la [protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) sur les serveurs
- Amélioration du mode WARN pour la [règle ASR](attack-surface-reduction-rules-reference.md)
- Amélioration de la gestion des certificats d’OSX  
- Journalisation améliorée pour l’analyse de l’emplacement FilesStash
- À compter de la version de plateforme 4.18.2208.0 et versions ultérieures : si un serveur a été [intégré à Microsoft Defender pour point de terminaison](onboard-configure.md#onboard-devices-to-the-service), le paramètre de stratégie de [groupe](configure-endpoints-gp.md#update-endpoint-protection-configuration) « Désactiver Windows Defender » ne désactive plus complètement Windows Defender Antivirus sur Windows Server 2012 systèmes d’exploitation R2 et ultérieurs. Au lieu de cela, il est ignoré (si [ForceDefenderPassiveMode](switch-to-mde-phase-2.md#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) est configuré explicitement) ou place Microsoft Defender Antivirus en [mode passif](microsoft-defender-antivirus-windows.md#comparing-active-mode-passive-mode-and-disabled-mode) (si `ForceDefenderPassiveMode` n’est pas configuré). En outre, la [protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) permet de passer en mode actif en passant `ForceDefenderPassiveMode` en `0`mode passif, mais pas en mode passif. Ces modifications s’appliquent uniquement aux serveurs intégrés à Microsoft Defender pour point de terminaison. Pour plus d’informations, reportez-vous à [Microsoft Defender compatibilité antivirus avec d’autres produits de sécurité](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility#microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions).

### <a name="known-issues"></a>Problèmes connus

- Certains clients ont peut-être reçu des mises à jour de plateforme 4.18.2209.2 à partir de la préversion. Cela peut entraîner le blocage du service à l’état de démarrage après la mise à jour.  
<br/><br/>
</details><details>
<summary>Août 2022 (Plateforme : 4.18.2207.7 | Moteur : 1.1.19600.3)</summary>

&ensp;Version de mise à jour du renseignement de sécurité : **1.373.1647.0**<br/>
&ensp;Date de publication : **6 septembre 2022**<br/>
&ensp;Plateforme : **4.18.2207.7**<br/>
&ensp;Moteur : **1.1.19600.3**<br/>
&ensp;Phase de support : **Mises à jour critiques et relatives à la sécurité**<br/>

Version du moteur : 1.1.19600.3<br/>
Version de mise à jour du renseignement de sécurité : 1.373.1647.0 <br/>

### <a name="whats-new"></a>Nouveautés

- Résolution des problèmes liés au programme d’installation de l’agent unifié sur le serveur et le Windows Server 2016 WS2012R2
- Correction d’un problème de correction pour la détection personnalisée
- Correction de la condition de concurrence liée à la surveillance du comportement
- Résolution de plusieurs scénarios d’interblocage dans les DLL Defender
- Amélioration de la fréquence des notifications toasts Windows pour les règles ASR

### <a name="known-issues"></a>Problèmes connus

- Aucun

<br/><br/>
</details>


### <a name="previous-version-updates-technical-upgrade-support-only"></a>Mises à jour de version précédentes : prise en charge de la mise à niveau technique uniquement

Une fois qu’une nouvelle version de package est publiée, la prise en charge des deux versions précédentes est réduite au support technique uniquement. Les versions antérieures à celles répertoriées dans cette section sont fournies uniquement pour la prise en charge de la mise à niveau technique.<br/><br/>

<details>
<summary>Juillet-2022 (Plateforme : 4.18.2207.5 | Moteur : 1.1.19500.2)</summary>

&ensp;Version de mise à jour du renseignement de sécurité : **1.373.219.0**<br/>
&ensp;Date de publication : **15 août 2022**<br/>
&ensp;Plateforme : **4.18.2207.5**<br/>
&ensp;Moteur : **1.1.19500.2**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

Version du moteur : 1.1.19300.2<br/>
Version de mise à jour du renseignement de sécurité : 1.373.219.0 <br/>

### <a name="whats-new"></a>Nouveautés

- Amélioration des performances pour le délai de [veille hybride](/windows-hardware/customize/power-settings/sleep-settings-hybrid-sleep) lorsque l’Antivirus Microsoft Defender est actif 
- Correction du comportement de détection du client lié aux [indicateurs de compromission des certificats personnalisés](indicator-certificates.md) 
- Amélioration des performances de la mise en cache [AMSI (AntiMalware Scan Interface)](/windows/win32/amsi/antimalware-scan-interface-portal) 
- Amélioration de la détection et de la correction pour les macros associées à [Microsoft Visual Basic pour Applications](/office/vba/language/concepts/getting-started/64-bit-visual-basic-for-applications-overview) (VBA) 
- Amélioration du traitement des exclusions AMSI 
- Correction de la détection des interblocages dans le traitement des règles HIPS (Host Intrusion Prevention System). (Pour plus d’informations sur HIPS et Defender pour point de terminaison, consultez [Migration d’un HIPS tiers vers des règles ASR](migrating-asr-rules.md).) 
- Correction de la fuite de mémoire pour laquelle `MsMpEng.exe` consommait des octets privés. (Si une utilisation élevée de l’UC est également un problème, consultez [Utilisation élevée du processeur en raison de l’antivirus Microsoft Defender](troubleshooting-mode-scenarios.md)) 
- Correction d’un blocage avec [surveillance du comportement](configure-real-time-protection-microsoft-defender-antivirus.md) 
- Amélioration de la validation de l’approbation 
- Résolution du problème d’incident du moteur sur les plateformes d’exploitation héritées 
- Mises à jour de l’Analyseur de performance v3 : Ajout de la prise en charge du chemin d'accès supérieur, des informations sur le saut d'analyse et de l'analyse à la demande. Consultez [Analyseur de performances pour Antivirus Microsoft Defender](tune-performance-defender-antivirus.md). 
- Améliorations des performances de Defender pendant les opérations de copie de fichiers
- Ajout d’améliorations pour le [mode résolution des problèmes](enable-troubleshooting-mode.md)  
- Ajout du correctif pour les canaux Defender WINEVT entre les mises à jour et les redémarrages. (Pour plus d’informations sur WINEVT, consultez journal [des événements Windows](/windows/win32/api/_wes/) .)
- Ajout d’un correctif pour le bogue [de gestion WMI de Defender](use-wmi-microsoft-defender-antivirus.md) lors du démarrage/des mises à jour 
- Ajout du correctif pour la version 2010/2011 dans les [événements Windows observateur d'événements Operational](troubleshoot-microsoft-defender-antivirus.md) 
- Ajout de la prise en charge du renforcement des jetons des processus de pile [defender pour point de terminaison](microsoft-defender-endpoint.md) 


### <a name="known-issues"></a>Problèmes connus

- Les clients qui déploient la mise à jour de la plateforme 4.18.2207.5 peuvent rencontrer des performances réseau en retard, ce qui peut avoir un impact sur les applications.

<br/><br/>
</details><details>
<summary>Mai 2022 (Plateforme : 4.18.2205.7 | Moteur : 1.1.19300.2)</summary>

&ensp;version de mise à jour du renseignement de sécurité : **1.369.88.0**<br/>
&ensp;publiée : **22 juin 2022**<br/>
plateforme&ensp;: **4.18.2205.7**<br/>
&ensp;moteur: **1.1.19300.2**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

Version du moteur : 1.1.19300.2<br/>
Version de mise à jour du renseignement de sécurité : 1.369.88.0<br/>

### <a name="whats-new"></a>Nouveautés

- Ajout d’un correctif pour la configuration du canal ETW pour les mises à jour 
- Ajout de la prise en charge des exclusions contextuelles permettant un ciblage d’exclusion plus spécifique 
- Taille maximale du contexte fixe
- Ajout d’un correctif pour la [détection ASR LSASS](attack-surface-reduction-rules-reference.md)
- Ajout d’un correctif à SHSetKnownFolder pour la logique d’exclusion de règle
- Ajout des limites d’utilisation du disque AMSI pour le magasin d’historique
- Ajout d’un correctif pour le service Defender refusant d’accepter les mises à jour de signature

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu

<br/><br/>
</details><details>
<summary>Mars 2022 *MISE À JOUR* (Plateforme : 4.18.2203.5 | Moteur : 1.1.19200.5)</summary>

Les *clients qui ont appliqué la mise à jour du moteur Microsoft Defender de mars 2022 (**1.1.19100.5**) ont peut-être rencontré une utilisation élevée des ressources (processeur et/ou mémoire). Microsoft Corporation a publié une mise à jour (**1.1.19200.5**) qui résout les bogues introduits dans la version précédente. Il est recommandé aux clients de mettre à jour vers au moins cette nouvelle version de moteur du moteur antivirus (**1.1.19200.5**). Pour vous assurer que les problèmes de performances sont entièrement résolus, il est recommandé de redémarrer les ordinateurs après l’application de la mise à jour.*

&ensp;Version de mise à jour de la veille de sécurité : **1.363.817.0**<br/>
&ensp;Publiée : **22 avril 2022**<br/>
&ensp;Plateforme : **4.18.2203.5**<br/>
&ensp;Moteur : **1.1.19200.5**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

Version du moteur : 1.1.19200.5 <br/>
Version de mise à jour de la veille de sécurité : 1.363.817.0<br/>

### <a name="whats-new"></a>Nouveautés

- Résolution des problèmes d’utilisation élevée des ressources (processeur et/ou mémoire) liés à la mise à jour antérieure du moteur Microsoft Defender de mars 2022 (1.1.19100.5)

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu

<br/><br/>
</details><details>
<summary>Mars 2022 (Plateforme : 4.18.2203.5 | Moteur : 1.1.19100.5)</summary>

&ensp;version de mise à jour de la veille de sécurité : **1.361.1449.0**<br/>
&ensp;Publiée : **7 avril 2022**<br/>
&ensp;Plateforme : **4.18.2203.5**<br/>
&ensp;Moteur : **1.1.19100.5**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

Version du moteur : 1.1.19100.5 <br/>
Version de mise à jour de la veille de sécurité : 1.361.1449.0<br/>

### <a name="whats-new"></a>Nouveautés

- Ajout d’un correctif pour une [règle de réduction de la surface d’attaque](attack-surface-reduction.md) qui a bloqué un complément Outlook 
- Ajout d’un correctif relatif à un problème de performance de la [surveillance du comportement](configure-protection-features-microsoft-defender-antivirus.md) lié aux processus en direct courts 
- Ajout d’un correctif pour une exclusion [AMSI](/windows/win32/amsi/antimalware-scan-interface-portal) 
- Amélioration des fonctionnalités de [protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) 
- Ajout d’un correctif relatif à la désactivation de la [protection en temps réel](configure-protection-features-microsoft-defender-antivirus.md) dans certains cas lors de l’utilisation de la `SharedSignaturesPath`configuration. Pour plus d’informations sur le paramètre `SharedSignaturesPath`, consultez [Set-MpPreference](/powershell/module/defender/set-mppreference).

### <a name="known-issues"></a>Problèmes connus

- Potentiel d’utilisation élevée des ressources (UC et/ou mémoire). Consultez la mise à jour de la plateforme 4.18.2203.5 et du moteur 1.1.19200.5 pour mars 2022.

<br/><br/>
</details><details>
<summary>Février 2022 (Plateforme : 4.18.2202.4 | Moteur : 1.1.19000.8)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.361.14.0**<br/>
&ensp;Publiée : **14 mars 2022**<br/>
&ensp;Plateforme : **4.18.2202.4**<br/>
&ensp;Moteur : **1.1.19000.8**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

Version du moteur : 1.1.19000.8 <br/>
Version de mise à jour de la veille de sécurité : 1.361.14.0 <br/>

### <a name="whats-new"></a>Nouveautés

- Améliorations apportées à la logique de détection et de surveillance du comportement
- Correction des détections de réduction de la surface d’attaque déclenchées par un faux positif
- Ajout d’un correctif qui améliore la fidélité des alertes de détection de PEPT et de Repérage avancé
- Defender ne prend plus en charge les notifications personnalisées sur les fenêtres contextuelles toast. Modification de l’objet de stratégie de groupe/Intune/SCCM et de la documentation pour refléter cette modification.
- Améliorations apportées à la capture des informations et à la copie des fichiers écrits dans le stockage amovible. Pour plus d’informations, consultez [Contrôle d’accès au stockage amovible du control de l’appareil de Microsoft Defender, support de stockage amovible](device-control-removable-storage-access-control.md).
- Amélioration de la sortie du trafic lorsque le service SmartScreen est inaccessible 
- Améliorations de la connectivité pour les clients utilisant des proxys avec des exigences d’authentification
- Correction du bogue de mise à jour d’appareil VDI pour les partages de fichiers réseau 
- PEPT en mode bloc prend désormais en charge le ciblage granulaire des appareils avec les nouveaux CSPs. Consultez [Détection et réponse de point de terminaison (PEPT) en mode bloc](edr-in-block-mode.md).

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu

<br/><br/>
</details><details>
<summary>Janvier 2022 (Plateforme : 4.18.2201.10 | Moteur : 1.1.18900.2)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.357.8.0**<br/>
&ensp;Publiée : **9 février 2022**<br/>
&ensp;Plateforme : **4.18.2201.10**<br/>
&ensp;Moteur : **1.1.18900.2**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

Version du moteur : 1.1.18900.2 <br/>
Version de mise à jour de la veille de sécurité : 1.357.8.0 <br/>

### <a name="whats-new"></a>Nouveautés

- Améliorations de la surveillance du comportement dans les performances de filtrage
- Renforcement de TrustedInstaller
- Améliorations de la protection contre les falsifications
- Replaced `ScanScheduleTime` with new `ScanScheduleOffest` cmdlet in [Set-MpPreference](/powershell/module/defender/set-mppreference). This policy configures the number of minutes after midnight to perform a scheduled scan.
- Added the `-ServiceHealthReportInterval` setting to [Set-MpPreference](/powershell/module/defender/set-mppreference). This policy configures the time interval (in minutes) to perform a scheduled scan.
- Added the `AllowSwitchToAsyncInspection` setting to [Set-MpPreference](/powershell/module/defender/set-mppreference). This policy enables a performance optimization, that allows synchronously inspected network flows, to switch to async inspection once they've been checked and validated.
- Mises à jour de l’Analyseur de performances v2 : prise en charge de PowerShell à distance et PowerShell 7.x ajoutées. Consultez [Analyseur de performances pour Antivirus Microsoft Defender](tune-performance-defender-antivirus.md).
- Correction d’un bogue potentiel de paquet en double dans Antivirus Microsoft Defender pilote système d’inspection du réseau.

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu

<br/><br/>
</details><details>
<summary>Novembre 2021 (Plateforme : 4.18.2111.5 | Moteur : 1.1.18800.4)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.355.2.0**<br/>
&ensp;Publiée : **9 décembre 2021**<br/>
&ensp;Plateforme : **4.18.2111.5**<br/>
&ensp;Moteur : **1.1.18800.4**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

Version du moteur : 1.1.18800.4 Version de la mise à jour de la veille de sécurité : 1.355.2.0

### <a name="whats-new"></a>Nouveautés

- Amélioration de l’efficacité de l’utilisation du processeur de certains scénarios intensifs sur les serveurs Exchange
- Ajout de nouveaux champs d’état de contrôle d’appareil sous Get-MpComputerStatus dans le module Defender PowerShell. Pour plus d’informations, consultez [Contrôle d’accès au stockage amovible du control de l’appareil de Microsoft Defender](device-control-removable-storage-access-control.md).
- Correction d’un bogue dans lequel `SharedSignatureRoot` valeur ne pouvait pas être supprimée lorsqu’elle était définie avec PowerShell
- Correction d’un bogue dans lequel la [protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) n’a pas pu être activée, même si Microsoft Defender pour point de terminaison a indiqué que la protection contre les falsifications était activée
- Ajout de la prise en charge et des correctifs de bogues à l’analyseur de performances pour Antivirus Microsoft Defender outil. Pour plus d’informations, consultez [Analyseur de performances pour Antivirus Microsoft Defender](tune-performance-defender-antivirus.md).   
   - Prise en charge de PowerShell ISE ajoutée pour `New-MpPerformanceRecording`
   - Correction des erreurs de bogue pour `Get-MpPerformanceReport -TopFilesPerProcess`
   - Correction de la fuite de session d’enregistrement des performances lors de l’utilisation de `New-MpPerformanceRecording` dans PowerShell 7.x, les sessions à distance et PowerShell ISE


### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Octobre 2021 (Plateforme : 4.18.2110.6 | Moteur : 1.1.18700.4)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.353.3.0**<br/>
&ensp;Publiée : **28 octobre 2021**<br/>
&ensp;Plateforme : **4.18.2110.6**<br/>
&ensp;Moteur : **1.1.18700.4**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

Version du moteur : 1.1.18700.4 Version de la mise à jour de la veille de sécurité : 1.353.3.0

### <a name="whats-new"></a>Nouveautés

- Améliorations apportées à la couverture du trafic réseau FTP (File Transfer Protocol)
- Correctif pour réduire l’utilisation du processeur Microsoft Defender dans Exchange Server exécuté sur Windows Server 2016
- Correction des interruptions d’analyse
- Correction des alertes en cas de tentatives de falsification bloquées qui n’apparaissent pas dans Security Center
- Améliorations apportées à la résilience des falsifications dans le service Microsoft Defender

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Septembre 2021 (Plateforme : 4.18.2109.6 | Moteur : 1.1.18600.4)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.351.7.0**<br/>
&ensp;Publiée : **7 octobre 2021**<br/>
&ensp;Plateforme : **4.18.2109.6**<br/>
&ensp;Moteur : **1.1.18600.4**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

Version du moteur : 1.1.18600.4 Version de la mise à jour de la veille de sécurité : 1.351.7.0

### <a name="whats-new"></a>Nouveautés
- Nouvel anneau de délai pour les mises à jour du moteur de Antivirus Microsoft Defender et de la plateforme. Les appareils qui optent pour cet anneau recevront des mises à jour avec un délai de 48 heures. Le nouvel anneau de délai est suggéré uniquement pour les environnements critiques. Consultez [Gérer le processus de déploiement progressif des mises à jour Microsoft Defender](manage-gradual-rollout.md).
- Améliorations apportées au processus de déploiement progressif des mises à jour de Microsoft Defender

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Août 2021 (Plateforme : 4.18.2108.7 | Moteur : 1.1.18500.10)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.349.22.0**<br/>
&ensp;Publiée : **2 septembre 2021**<br/>
&ensp;Plateforme : **4.18.2108.7**<br/>
&ensp;Moteur : **1.1.18500.10**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Améliorations apportées au moteur de surveillance du comportement
- Publication du nouvel [analyseur de performances pour Antivirus Microsoft Defender](tune-performance-defender-antivirus.md)
- Antivirus Microsoft Defender renforcée contre le chargement de DLL malveillantes
- Antivirus Microsoft Defender renforcée contre le contournement TrustedInstaller
- Extension des notifications de modification de fichier pour inclure plus de données pour les ransomwares gérés par l’homme (HumOR)

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Juillet 2021 (Plateforme : 4.18.2107.4 | Moteur : 1.1.18400.4)</summary>

&ensp;Version de la mise à jour de la veille de sécurité : **1.345.13.0**<br/>
&ensp;Publiée : **5 août 2021**<br/>
&ensp;Plateforme : **4.18.2107.4**<br/>
&ensp;Moteur : **1.1.18400.4**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Prise en charge du contrôle d’appareil ajoutée pour les appareils portables Windows
- La protection des applications potentiellement indésirables (PUA) est activée par défaut pour les consommateurs (voir [Bloquer les applications potentiellement indésirables avec Antivirus Microsoft Defender](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).)
- Les analyses planifiées pour les systèmes gérés par objet stratégie de groupe respectent le temps d’analyse configuré par l’utilisateur
- Améliorations apportées au moteur de surveillance du comportement

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu

<br/>
</details><details>
<summary> Juin 2021 (Plateforme : 4.18.2106.5 | Moteur : 1.1.18300.4)</summary>

&ensp;Version de mise à jour de la veille de sécurité de sécurité : **1.343.17.0**<br/>
&ensp;Publiée : **28 juin 2021**<br/>
&ensp;Plateforme : **4.18.2106.5**<br/>
&ensp;Moteur : **1.1.18300.4**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Nouveaux contrôles pour la gestion du processus de déploiement progressif des mises à jour Microsoft Defender. Consultez [Gérer le processus de déploiement progressif des mises à jour Microsoft Defender](manage-gradual-rollout.md).
- Amélioration du moteur de surveillance du comportement
- Améliorations apportées au déploiement des définitions de logiciel anti-programme malveillant
- Inspections d’événements réseau Microsoft Edge étendus

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Mai 2021 (Plateforme : 4.18.2105.4 | Moteur : 1.1.18200.4)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.341.8.0**<br/>
&ensp;Publiée : **3 juin 2021**<br/>
&ensp;Plateforme : **4.18.2105.4**<br/>
&ensp;Moteur : **1.1.18200.4**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Améliorations apportées à la [surveillance du comportement](client-behavioral-blocking.md)
- Correction de la fonctionnalité de filtrage des notifications de la [protection réseau](network-protection.md)

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Avril-2021 (Plateforme : 4.18.2104.14 | Moteur : 1.1.18100.5)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.337.2.0**<br/>
&ensp;Publiée : **26 avril 2021**  (moteur : 1.1.18100.6 publié le 5 mai 2021)<br/>
&ensp;Plateforme : **4.18.2104.14**<br/>
&ensp;Moteur : **1.1.18100.5**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Plus de logique de surveillance du comportement
- Amélioration de la détection de l’enregistreur d’événements de clé en mode noyau
- Ajout de nouveaux contrôles pour gérer le processus de déploiement progressif des [Mises à jour Microsoft Defender](manage-gradual-rollout.md)


### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Mars-2021 (Plateforme : 4.18.2103.7 | Moteur : 1.1.18000.5)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.335.36.0**<br/>
&ensp;Publiée : **2 avril 2021**<br/>
&ensp;Plateforme : **4.18.2103.7**<br/>
&ensp;Moteur : **1.1.18000.5**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Amélioration du moteur d’analyse du comportement
- Atténuations des attaques par force brute du réseau étendues
- Autres échecs de génération d’événements de tentative de falsification lorsque la [protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) est activée

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Février 2021 (Plateforme : 4.18.2102.3 | Moteur : 1.1.17900.7)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.333.7.0**<br/>
&ensp;Publiée : **9 mars 2021**<br/>
&ensp;Plateforme : **4.18.2102.3**<br/>
&ensp;Moteur : **1.1.17900.7**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Amélioration de la récupération de service grâce à la [protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md)
- Étendre l’étendue de la protection contre les falsifications

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Janvier 2021 (Plateforme : 4.18.2101.9 | Moteur : 1.1.17800.5)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.327.1854.0**<br/>
&ensp;Publiée : **2 février 2021**<br/>
&ensp;Plateforme : **4.18.2101.9**<br/>
&ensp;Moteur : **1.1.17800.5**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Améliorations de la détection de l’exploit shellcode
- Visibilité accrue des tentatives de vol d’informations d’identification
- Améliorations des fonctionnalités antitampering dans les services Antivirus Microsoft Defender
- Prise en charge améliorée de l’émulation ARM x64
- Correctif : la notification de blocage EDR reste dans l’historique des menaces après la détection initiale de la protection en temps réel

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Novembre 2020 (Plateforme : 4.18.2011.6 | Moteur : 1.1.17700.4)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.327.1854.0**<br/>
&ensp;Publiée : **le 3 décembre 2020**<br/>
&ensp;Plateforme : **4.18.2011.6**<br/>
&ensp;Moteur : **1.1.17700.4**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Amélioration de la journalisation de la prise en charge de l’état [SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details><details>
<summary> Octobre-2020 (Plateforme : 4.18.2010.7 | Moteur : 1.1.17600.5)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.327.7.0**<br/>
&ensp;Publiée : **29 octobre 2020**<br/>
&ensp;Plateforme : **4.18.2010.7**<br/>
&ensp;Moteur : **1.1.17600.5**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Nouvelles descriptions pour les catégories de menaces spéciales
- Amélioration des fonctionnalités d’émulation
- Amélioration des fonctionnalités d’autorisation/blocage de l’adresse hôte
- Nouvelle option dans defender CSP pour ignorer la fusion des exclusions d’utilisateurs locaux

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu
<br/>
</details><details>
<summary> Septembre 2020 (Plateforme : 4.18.2009.7 | Moteur : 1.1.17500.4)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.325.10.0**<br/>
&ensp;Publiée : **01 octobre 2020**<br/>
&ensp;Plateforme : **4.18.2009.7**<br/>
&ensp;Moteur : **1.1.17500.4**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Des autorisations d’administrateur sont requises pour restaurer des fichiers en quarantaine
- Les événements au format XML sont désormais pris en charge
- Prise en charge CSP pour ignorer les fusions d’exclusion
- Nouvelles interfaces de gestion pour :
   - UDP Inspection
   - Protection réseau sur server 2019
   - Exclusions d’adresses IP pour la protection réseau
- Meilleure visibilité des mesures du module de plateforme sécurisée
- Amélioration de l’analyse des modules Office VBA

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu
<br/>
</details>
<details>
<summary> Août 2020 (Plateforme : 4.18.2008.9 | Moteur : 1.1.17400.5)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.323.9.0**<br/>
&ensp;Publiée : **27 août 2020**<br/>
&ensp;Plateforme : **4.18.2008.9**<br/>
&ensp;Moteur : **1.1.17400.5**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Ajouter d’autres événements de télémétrie
- Amélioration de la télémétrie des événements d’analyse
- Amélioration de la surveillance du comportement pour les analyses de mémoire
- Analyse améliorée des flux de macros
- Ajout de `AMRunningMode` à l’applet de commande PowerShell Get-MpComputerStatus
- [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) is ignored. Microsoft Defender Antivirus automatically turns itself off when it detects another antivirus program.


### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Juillet-2020 (Plateforme : 4.18.2007.8 | Moteur : 1.1.17300.4)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.321.30.0**<br/>
&ensp;Publiée : **28 juillet 2020**<br/>
&ensp;Plateforme : **4.18.2007.8**<br/>
&ensp;Moteur : **1.1.17300.4**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Amélioration de la télémétrie pour BITS
- Amélioration de la validation du certificat de signature de code Authenticode

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Juin 2020 (Plateforme : 4.18.2006.10 | Moteur : 1.1.17200.2)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.319.20.0**<br/>
&ensp;Publiée : **22 juin 2020**<br/>
&ensp;Plateforme : **4.18.2006.10**<br/>
&ensp;Moteur : **1.1.17200.2**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Possibilité de spécifier l’[emplacement des journaux de support](./collect-diagnostic-data.md)
- L’analyse de catchup agressive est ignorée en mode passif.
- Autoriser Defender à mettre à jour sur les connexions limitées
- Correction du réglage des performances lors de la désactivation de la mise en cache
- Correction de la requête de Registre
- Correction de la randomisation du temps d’analyse dans ADMX

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Mai 2020 (Plateforme : 4.18.2005.4 | Moteur : 1.1.17100.2)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.317.20.0**<br/>
&ensp;Publiée : **26 mai 2020**<br/>
&ensp;Plateforme : **4.18.2005.4**<br/>
&ensp;Moteur : **1.1.17100.2**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Journalisation améliorée pour les événements d’analyse
- Amélioration de la gestion des incidents en mode utilisateur.
- Ajout du suivi d’événements pour la protection contre les falsifications
- Correction de l’envoi de l’exemple AMSI
- Correction du blocage du cloud AMSI
- Correction du journal d’installation des mises à jour de sécurité

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Avril 2020 (Plateforme : 4.18.2004.6 | Moteur : 1.1.17000.2)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.315.12.0**<br/>
&ensp;Publiée : **30 avril 2020**<br/>
&ensp;Plateforme : **4.18.2004.6**<br/>
&ensp;Moteur : **1.1.17000.2**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés
- Améliorations de WDfilter
- Ajouter des données d’événements plus actionnables aux événements de détection de réduction de la surface d’attaque
- Correction des informations de version dans les données de diagnostic et WMI
- Correction d’une version incorrecte de la plateforme dans l’interface utilisateur après la mise à jour de la plateforme
- Intel d’URL dynamique pour la protection contre les menaces sans fichier
- Fonctionnalité d’analyse UEFI
- Étendre la journalisation des mises à jour

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Mars 2020 (Plateforme : 4.18.2003.8 | Moteur : 1.1.16900.2)</summary>

&ensp;Version de mise à jour de la veille de sécurité : **1.313.8.0**<br/>
&ensp;Publiée : **24 mars 2020**<br/>
&ensp;Plateforme : **4.18.2003.8**<br/>
&ensp;Moteur : **1.1.16900.4**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Option de limitation de l’UC ajoutée à [MpCmdRun](./command-line-arguments-microsoft-defender-antivirus.md)
- Améliorer la fonctionnalité de diagnostic
- réduire le délai d’expiration de la veille de sécurité (5 minutes)
- Étendre la fonctionnalité de journal interne du moteur AMSI
- Améliorer la notification pour le blocage de processus

### <a name="known-issues"></a>Problèmes connus
[**Résolu** ] Antivirus Microsoft Defender ignore les fichiers lors de l’exécution d’une analyse.

<br/>
</details>

<details>

<summary> Février 2020 (Plateforme : - | Moteur : 1.1.16800.2)</summary>


&ensp;Version de mise à jour de la veille de sécurité : **1.311.4.0**<br/>
&ensp;Publiée : **25 février 2020**<br/>
&ensp;Plateforme/Client : **-**<br/>
&ensp;Moteur : **1.1.16800.2**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés


### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Janvier 2020 (Plateforme : 4.18.2001.10 | Moteur : 1.1.16700.2)</summary>


Version de mise à jour de la veille de sécurité : **1.309.32.0**<br/>
Publié : **30 janvier 2020**<br/>
Plateforme/client : **4.18.2001.10**<br/>
Moteur : **1.1.16700.2**<br/>
&ensp;Phase de support : **support technique de mise à niveau (uniquement)**<br/>

### <a name="whats-new"></a>Nouveautés

- Correction de BSOD sur WS2016 avec Exchange
- Prise en charge des mises à jour de plateforme lorsque TMP est redirigé vers le chemin d’accès réseau
- Les versions de plateforme et de moteur sont ajoutées à [WDSI](https://www.microsoft.com/en-us/wdsi/defenderupdates) <!-- The preceding URL must include "/en-us" -->
- étendre la mise à jour de signature d’urgence à [mode passif](./microsoft-defender-antivirus-compatibility.md)
- Correction du blocage 4.18.1911.3

### <a name="known-issues"></a>Problèmes connus

[**Résolu**] les appareils utilisant [mode de secours moderne](/windows-hardware/design/device-experiences/modern-standby) peuvent rencontrer un blocage avec le pilote de filtre Windows Defender qui entraîne un écart de protection.  Les ordinateurs affectés semblent ne pas avoir été mis à jour vers la dernière plateforme anti-programme malveillant.
<br/>
> [!IMPORTANT]
> Cette mise à jour est la suivante :
> - requis par les appareils RS1 exécutant une version inférieure de la plateforme pour prendre en charge SHA2 ;
> - a un indicateur de redémarrage pour les systèmes qui rencontrent des problèmes de blocage ;
> - est de nouveau publié en avril 2020 et ne sera pas remplacé par des mises à jour plus récentes pour assurer la disponibilité future ;
> - est classé comme une mise à jour en raison de l’exigence de redémarrage ; Et
> - est proposé uniquement avec [Windows Update](https://support.microsoft.com/help/4027667/windows-10-update).
<br/>
</details>

<details>
<summary> Novembre 2019 (Plateforme : 4.18.1911.3 | Moteur : 1.1.16600.7)</summary>

Version de mise à jour de la veille de sécurité : **1.307.13.0**<br/>
Publié : **7 décembre 2019**<br/>
Plateforme : **4.18.1911.3**<br/>
Moteur : **1.1.17000.7**<br/>
Phase de support : **Aucun support**<br/>

### <a name="whats-new"></a>Nouveautés

- Correction du niveau de traçage MpCmdRun
- Correction des informations de version de WDFilter
- Améliorer les notifications (PUA)
- ajouter des journaux MRT pour prendre en charge les fichiers

### <a name="known-issues"></a>Problèmes connus
Une fois cette mise à jour installée, l’appareil a besoin du package de saut 4.18.2001.10 pour pouvoir effectuer la mise à jour vers la dernière version de la plateforme.
<br/>
</details>


## <a name="microsoft-defender-antivirus-platform-support"></a>prise en charge de la plateforme Antivirus Microsoft Defender

Les mises à jour de plateforme et de moteur sont fournies à une cadence mensuelle. Pour être entièrement pris en charge, restez à jour avec les dernières mises à jour de plateforme. Notre structure de prise en charge est dynamique et évolue en deux phases en fonction de la disponibilité de la dernière version de la plateforme :

- **Phase de maintenance des mises à jour critiques et de sécurité** : lors de l’exécution de la dernière version de la plateforme, vous pouvez recevoir des mises à jour de sécurité et critiques pour la plateforme anti-programme malveillant.

- **Phase de support technique (uniquement)** : une fois qu’une nouvelle version de plateforme est publiée, la prise en charge des versions antérieures (N-2) se réduit au support technique uniquement. Les versions de plateforme antérieures à N-2 ne seront plus prises en charge.*

\* Le support technique continuera d’être fourni pour les mises à niveau de la version Windows 10 (voir [Version de la plateforme incluse avec Windows 10 versions](#platform-version-included-with-windows-10-releases)) vers la dernière version de la plateforme.

Au cours de la phase de support technique (uniquement), les incidents de support raisonnable commercialement seront fournis par le biais du service clientèle Microsoft et Support et offres de support géré de Microsoft (telles que Support Premier). Si un incident de support nécessite une réaffectation au développement pour obtenir des instructions supplémentaires, nécessite une mise à jour non relative à la sécurité ou nécessite une mise à jour de sécurité, les clients sont invités à effectuer une mise à niveau vers la dernière version de la plateforme ou une mise à jour intermédiaire (*).

> [!NOTE]
> Si vous déployez manuellement Antivirus Microsoft Defender Platform Update, ou si vous utilisez un script ou un produit de gestion non Microsoft pour déployer Antivirus Microsoft Defender Platform Update, assurez-vous que la version `4.18.2001.10` est installée à partir du [Catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=4.18.2001.10) avant l’installation de la dernière version de Platform Update (N-2).

### <a name="platform-version-included-with-windows-10-releases"></a>Version de plateforme incluse dans les versions Windows 10

Le tableau ci-dessous fournit les versions de plateforme et de moteur Antivirus Microsoft Defender fournies avec les dernières versions Windows 10 :<br/><br/>

|Version Windows 10  |Version de la plateforme  |Version du moteur |Phase de support |
|:---|:---|:---|:---|
|2004 (20H1/20H2) | `4.18.1909.6` | `1.1.17000.2` | Prise en charge de la mise à niveau technique (uniquement) |
|1909 (19H2) |`4.18.1902.5` |`1.1.16700.3` | Prise en charge de la mise à niveau technique (uniquement) |
|1903 (19H1) |`4.18.1902.5` |`1.1.15600.4` | Prise en charge de la mise à niveau technique (uniquement) |
|1809 (RS5) |`4.18.1807.1807`5 |`1.1.15000.2` | Prise en charge de la mise à niveau technique (uniquement) |
|1803 (RS4) |`4.13.17134.1` |`1.1.14600.4` | Prise en charge de la mise à niveau technique (uniquement) |
|1709  (RS3) |`4.12.16299.15` |`1.1.14104.0` | Prise en charge de la mise à niveau technique (uniquement) |
|1703  (RS2) |`4.11.15603.2` |`1.1.13504.0` | Prise en charge de la mise à niveau technique (uniquement) |
|1607 (RS1) |`4.10.14393.3683` |`1.1.12805.0` | Prise en charge de la mise à niveau technique (uniquement) |

Pour les informations de publication Windows 10, consultez [la feuille de faits sur le cycle de vie de Windows.](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)

## <a name="updates-for-deployment-image-servicing-and-management-dism"></a>Mises à jour pour Gestion et maintenance des images de déploiement (DISM)

We recommend updating your Windows 10 (Enterprise, Pro, and Home editions), Windows Server 2019, Windows Server 2022, and Windows Server 2016 OS installation images with the latest antivirus and antimalware updates. Keeping your OS installation images up to date helps avoid a gap in protection.

Pour plus d’informations, consultez [Mise à jour de Microsoft Defender pour les images d’installation du système d’exploitation Windows](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images).

<details>
<summary>20221014.1</summary>

&ensp;Version du package : **20221014.1**<br/>
&ensp;Version de la plateforme : **4.18.2209.7**<br/>
&ensp;Version du moteur : **1.1.19700.3**<br/>
&ensp;Version de signature : **1.373.208.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220929.1</summary>

&ensp;Version du package : **20220929.1**<br/>
&ensp;Version de la plateforme : **4.18.2207.7**<br/>
&ensp;Version du moteur : **1.1.19600.3**<br/>
&ensp;Version de signature : **1.373.1243.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220925.2</summary>

&ensp;Version du package : **20220925.2**<br/>
&ensp;Version de la plateforme : **4.18.2207.7**<br/>
&ensp;Version du moteur : **1.1.19600.3**<br/>
&ensp;Version de signature : **1.373.1371.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220901.4</summary>

&ensp;Version du package : **20220901.4**<br/>
&ensp;Version de la plateforme : **4.18.2205.7**<br/>
&ensp;Version du moteur : **1.1.19500.2**<br/>
&ensp;Version de signature : **1.373.1371.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220802.1</summary>

&ensp;Version du package : **20220802.1**<br/>
&ensp;Version de la plateforme : **4.18.2205.7**<br/>
&ensp;Version du moteur : **1.1.19400.3**<br/>
&ensp;Version de signature : **1.371.1205.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220629.5</summary>

&ensp;Version du package : **20220629.5**<br/>
&ensp;Version de la plateforme : **4.18.2205.7**<br/>
&ensp;Version du moteur : **1.1.19300.2**<br/>
&ensp;Version de signature : **1.369.220.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220603.3</summary>

&ensp;Version du package : **20220603.3**<br/>
&ensp;Version de la plateforme : **4.18.2203.5**<br/>
&ensp;Version du moteur : **1.1.19200.6**<br/>
&ensp;Version de signature : **1.367.1009.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220506.6</summary>

&ensp;Version du package : **20220506.6**<br/>
&ensp;Version de la plateforme : **4.18.2203.5**<br/>
&ensp;version du moteur : **1.1.19200.5**<br/>
&ensp;Version de signature : **1.363.1436.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220321.1</summary>

&ensp;Version du package : **20220321.1**<br/>
&ensp;Version de Plateforme : **4.18.2202.4**<br/>
&ensp;Version du moteur : **1.1.19000.8**<br/>
&ensp;Version de signature : **1.351.337.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220305.1</summary>

&ensp;Version du package : **20220305.1**<br/>
&ensp;Version de la plateforme : **4.18.2201.10**<br/>
&ensp;Version du moteur : **1.1.18900.3**<br/>
&ensp;Version de signature : **1.359.1405.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun

<br/>
</details><details>
<summary>20220203.1</summary>

&ensp;Version du package : **20220203.1**<br/>
&ensp;Version de plateforme : **4.18.2111.5**<br/>
&ensp;Version du moteur : **1.1.18900.2**<br/>
&ensp;Version de signature : **1.357.32.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>20220105.1</summary>

&ensp;Version du package **20220105.1**<br/>
&ensp;Version de plateforme : **4.18.2111.5**<br/>
&ensp;Version du moteur : **1.1.18800.4**<br/>
&ensp;Version de signature : **1.355.1482.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2112.01</summary>

&ensp;Version du package : **1.1.2112.01**<br/>
&ensp;Version de plateforme : **4.18.2110.6**<br/>
&ensp;Version du moteur : **1.1.18700.4**<br/>
&ensp;Version de signature : **1.353.2283.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2111.02</summary>

&ensp;Version du package : **1.1.2111.02**<br/>
&ensp;Version de plateforme : **4.18.2110.6**<br/>
&ensp;Version du moteur : **1.1.18700.4**<br/>
&ensp;Version de signature : **1.353.613.0**<br/>

### <a name="fixes"></a>Correctifs
- Correction d’un problème lié aux fichiers de localisation

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2110.01</summary>

&ensp;Version du package : **1.1.2110.01**<br/>
&ensp;Version de plateforme : **4.18.2109.6**<br/>
&ensp;Version du moteur : **1.1.18500.10**<br/>
&ensp;Version de signature : **1.349.2103.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2109.01</summary>

&ensp;Version du package : **1.1.2109.01**<br/>
&ensp;Version de plateforme : **4.18.2107.4**<br/>
&ensp;Version du moteur : **1.1.18400.5**<br/>
&ensp;Version de signature : **1.347.891.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2108.01</summary>

&ensp;Version du package : **1.1.2108.01**<br/>
&ensp;Version de plateforme : **4.18.2107.4**<br/>
&ensp;Version du moteur : **1.1.18300.4**<br/>
&ensp;Version de signature : **1.343.2244.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2107.02</summary>

&ensp;Version du package : **1.1.2107.02**<br/>
&ensp;Version de plateforme : **4.18.2105.5**<br/>
&ensp;Version du moteur : **1.1.18300.4**<br/>
&ensp;Version de signature : **1.343.658.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2106.01</summary>

&ensp;Version du package : **1.1.2106.01**<br/>
&ensp;Version de plateforme : **4.18.2104.14**<br/>
&ensp;Version du moteur : **1.1.18100.6**<br/>
&ensp;Version de signature : **1.339.1923.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2105.01</summary>

&ensp;Version du package : **1.1.2105.01**<br/>
&ensp;Version de plateforme : **4.18.2103.7**<br/>
&ensp;Version du moteur : **1.1.18100.6**<br/>
&ensp;Version de signature : **1.339.42.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2104.01</summary>

&ensp;Version du package : **1.1.2104.01**<br/>
&ensp;Version de plateforme : **4.18.2102.4**<br/>
&ensp;Version du moteur : **1.1.18000.5**<br/>
&ensp;Version de signature : **1.335.232.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2103.01</summary>

&ensp;Version du package : **1.1.2103.01**<br/>
&ensp;Version de plateforme : **4.18.2101.9**<br/>
&ensp;Version du moteur : **1.1.17800.5**<br/>
&ensp;Version de signature : **1.331.2302.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2102.03</summary>

&ensp;Version du package : **1.1.2102.03**<br/>
&ensp;Version de plateforme : **4.18.2011.6**<br/>
&ensp;Version du moteur : **1.1.17800.5**<br/>
&ensp;Version de signature : **1.331.174.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2101.02</summary>

&ensp;Version du package : **1.1.2101.02**<br/>
&ensp;Version de plateforme : **4.18.2011.6**<br/>
&ensp;Version du moteur : **1.1.17700.4**<br/>
&ensp;Version de signature : **1.329.1796.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2012.01</summary>

&ensp;Version du package : **1.1.2012.01**<br/>
&ensp;Version de plateforme : **4.18.2010.7**<br/>
&ensp;Version du moteur : **1.1.17600.5**<br/>
&ensp;Version de signature : **1.327.1991.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2011.02</summary>

&ensp;Version du package : **1.1.2011.02**<br/>
&ensp;Version de plateforme : **4.18.2010.7**<br/>
&ensp;Version du moteur : **1.1.17600.5**<br/>
&ensp;Version de signature : **1.327.658.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Signatures Antivirus Microsoft Defender actualisées
<br/>
</details><details>
<summary>1.1.2011.01</summary>

&ensp;Version du package : **1.1.2011.01**<br/>
&ensp;Version de plateforme : **4.18.2009.7**<br/>
&ensp;Version du moteur : **1.1.17600.5**<br/>
&ensp;Version de signature : **1.327.344.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Aucun
<br/>
</details><details>
<summary>1.1.2009.10</summary>

&ensp;Version du package : **1.1.2011.01**<br/>
&ensp;Version de plateforme : **4.18.2008.9**<br/>
&ensp;Version du moteur : **1.1.17400.5**<br/>
&ensp;Version de signature : **1.327.2216.0**<br/>

### <a name="fixes"></a>Correctifs
- Aucun

### <a name="additional-information"></a>Informations supplémentaires
- Ajout de la prise en charge des images d’installation de système d’exploitation Windows 10 RS1 ou version ultérieure.
<br/>
</details>

## <a name="more-resources"></a>Plus de ressources

| Article | Description  |
|:---|:---|
|[Mise à jour de Microsoft Defender poù les images d’installation du système d'exploitation de Windows](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)  | Passez en revue les packages de mise à jour anti-programme malveillant pour vos images d’installation du système d’exploitation (fichiers WIM et VHD). Obtenez Antivirus Microsoft Defender mises à jour pour Windows 10 (éditions Entreprise, Professionnel et Famille), Windows Server 2019, Windows Server 2022 et les images d’installation de Windows Server 2016.  |
|[Gérer le téléchargement et l’application des mises à jour de protection](manage-protection-updates-microsoft-defender-antivirus.md) | Les mises à jour de protection peuvent être fournies par le biais de nombreuses sources. |
|[Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) | Vous pouvez planifier le téléchargement des mises à jour de protection. |
|[Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md) | Si un point de terminaison manque une mise à jour ou une analyse planifiée, vous pouvez forcer une mise à jour ou une analyse lors de la prochaine connexion d’un utilisateur. |
|[Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md) | Vous pouvez définir des mises à jour de protection à télécharger au démarrage ou après certains événements de protection fournis par le cloud. |
|[Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)| Vous pouvez spécifier des paramètres, par exemple si des mises à jour doivent se produire sur batterie, qui sont particulièrement utiles pour les appareils mobiles et les machines virtuelles. |
| [Mise à jour de Microsoft Defender pour point de terminaison pour le capteur PEPT](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) | Vous pouvez mettre à jour le capteur PEPT (MsSense.exe) inclus dans le nouveau package de solution unifiée Microsoft Defender pour point de terminaison publié en 2021.   |

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
