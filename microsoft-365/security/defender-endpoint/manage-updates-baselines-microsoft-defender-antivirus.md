---
title: Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquer les lignes de base
description: Gérer la façon dont l’Antivirus Microsoft Defender reçoit la protection et les mises à jour du produit.
keywords: mises à jour, bases de référence de sécurité, protection, planification des mises à jour, forcer les mises à jour, mises à jour mobiles, wsus
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.date: 05/06/2021
ms.openlocfilehash: 22a173d39c3ab8d1afd91a33b05e02e58da24aaa
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52274555"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-apply-baselines"></a>Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquer les lignes de base

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- Antivirus Microsoft Defender

Il existe deux types de mises à jour liées à la mise à jour de l’Antivirus Microsoft Defender :

- Mises à jour de l’intelligence de la sécurité
- Mises à jour de produit

> [!IMPORTANT]
> Maintenir l’Antivirus Microsoft Defender à jour est essentiel pour garantir que vos appareils disposent des dernières technologies et fonctionnalités nécessaires pour se protéger contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque.
> 
> Veillez à mettre à jour votre protection antivirus même si l’Antivirus Microsoft Defender s’exécute en [mode passif.](./microsoft-defender-antivirus-compatibility.md)
> 
> Pour voir le moteur, la plateforme et la date de signature les plus à jour, consultez les mises à jour de l’Intelligence de sécurité pour l’Antivirus Microsoft Defender et d’autres logiciels [anti-programme malveillant Microsoft.](https://www.microsoft.com/en-us/wdsi/defenderupdates)

## <a name="security-intelligence-updates"></a>Mises à jour de l’intelligence de la sécurité

L’Antivirus Microsoft Defender utilise la protection fournie par le [cloud](cloud-protection-microsoft-defender-antivirus.md) (également appelée Service de protection avancée Microsoft ou MAPS) et télécharge régulièrement les mises à jour de l’intelligence de sécurité pour fournir une protection.

> [!NOTE]
> Les mises à jour sont publiées sous les numéros de la Ko ci-dessous :  
> Antivirus Microsoft Defender : KB2267602  
> System Center Endpoint Protection : KB2461484

La protection cloud est toujours active et nécessite une connexion active à Internet pour fonctionner. Les mises à jour des informations de sécurité se produisent à une cadence programmée (configurable via une stratégie). Pour plus d’informations, voir Utiliser la protection fournie par le [cloud Microsoft dans l’Antivirus Microsoft Defender.](cloud-protection-microsoft-defender-antivirus.md) 

Pour obtenir la liste des mises à jour récentes de l’intelligence de sécurité, voir Les mises à jour d’intelligence de sécurité pour l’Antivirus Microsoft Defender et d’autres logiciels [anti-programme malveillant Microsoft.](https://www.microsoft.com/en-us/wdsi/defenderupdates)

Les mises à jour du moteur sont incluses dans les mises à jour de l’intelligence de sécurité et sont publiées à une cadence mensuelle.

## <a name="product-updates"></a>Mises à jour de produit

L’Antivirus Microsoft Defender nécessite des mises à jour [mensuelles (KB4052623)](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform) *(connues* sous le nom de mises à jour de plateforme) et recevra des mises à jour de fonctionnalités majeures parallèlement aux mises à jour de Windows 10.

Vous pouvez gérer la distribution des mises à jour via l’une des méthodes suivantes : 

- [Windows Server Update Service (WSUS)](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)
- [Microsoft Endpoint Configuration Manager](/configmgr/sum/understand/software-updates-introduction)
- La méthode habituelle que vous utilisez pour déployer les mises à jour Microsoft et Windows sur les points de terminaison de votre réseau.

Pour plus d’informations, voir Gérer les sources des mises à [jour de la protection antivirus Microsoft Defender.](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)

> [!NOTE]
> Les mises à jour mensuelles sont publiées par phases, ce qui entraîne la mise à jour de plusieurs packages dans vos services de mise à jour [de serveur Window.](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)

## <a name="monthly-platform-and-engine-versions"></a>Versions mensuelles de la plateforme et du moteur

Pour plus d’informations sur la mise à jour ou l’installation de la mise à jour de la plateforme, voir [Update for Windows Defender antimalware platform](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform).

Toutes nos mises à jour contiennent 
- améliorations des performances ;
- améliorations de la serviceabilité ; et 
- améliorations de l’intégration (Cloud, Microsoft 365 Defender).
<br/>
<details>
<summary> Avril-2021 (plateforme : 4.19.2104.9| Moteur : 1.1.18100.5)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.337.2.0**  
&ensp;Publication : **1er avril 2021**  
&ensp;Plateforme : **4.19.2104.9**  
&ensp;Moteur : **1.1.18100.5**  
&ensp;Phase de prise en charge **: Mises à jour critiques et de sécurité**
    
### <a name="whats-new"></a>Nouveautés
- Logique d’analyse de comportement supplémentaire
- Détection améliorée du keylogger en mode noyau

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu  
<br/>
</details>

<details>
<summary> Mars-2021 (plateforme : 4.19.2103.7 | Moteur : 1.1.18000.5)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.335.36.0**  
&ensp;Publication : **1er avril 2021**  
&ensp;Plateforme : **4.19.2103.7**  
&ensp;Moteur : **1.1.18000.5**  
&ensp;Phase de prise en charge **: Mises à jour critiques et de sécurité**
    
### <a name="whats-new"></a>Nouveautés

- Amélioration du moteur d’analyse du comportement 
- Préventions d’attaques par force brute du réseau étendu 
- Génération d’événements de tentative de falsification en échec supplémentaires lorsque la [protection](prevent-changes-to-security-settings-with-tamper-protection.md) contre la falsification est activée

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu  
<br/>
</details><details>
<summary> Février-2021 (plateforme : 4.19.2102.3 | Moteur : 1.1.17900.7)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.333.7.0**  
&ensp;Publication : **9 mars 2021**  
&ensp;Plateforme : **4.19.2102.3**  
&ensp;Moteur : **1.1.17900.7**  
&ensp;Phase de prise en charge **: Mises à jour critiques et de sécurité**
    
### <a name="whats-new"></a>Nouveautés

- Amélioration de la récupération du service par le biais [de la protection contre la falsification](prevent-changes-to-security-settings-with-tamper-protection.md)
- Étendre l’étendue de la protection contre la falsification

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu  
<br/>
</details>

### <a name="previous-version-updates-technical-upgrade-support-only"></a>Mises à jour de version précédente : prise en charge de la mise à niveau technique uniquement

Après la publication d’une nouvelle version de package, la prise en charge des deux versions précédentes est réduite au support technique uniquement. Les versions antérieures à celles répertoriées dans cette section sont fournies uniquement pour la prise en charge de la mise à niveau technique. 
<br/><br/>
<details>
<summary> Janvier-2021 (plateforme : 4.18.2101.9 | Moteur : 1.1.17800.5)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.327.1854.0**  
&ensp;Publication : **2 février 2021**  
&ensp;Plateforme : **4.18.2101.9**  
&ensp;Moteur : **1.1.17800.5**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
    
### <a name="whats-new"></a>Nouveautés

- Améliorations de la détection d’exploits shellcode
- Visibilité accrue des tentatives de vol d’informations d’identification
- Améliorations des fonctionnalités anti-tam dans les services antivirus Microsoft Defender
- Prise en charge améliorée de l ARM éulation x64
- Correctif : la notification de blocage EDR reste dans l’historique des menaces après la détection initiale de la protection en temps réel

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu  
<br/>
</details><details>
<summary> Novembre-2020 (plateforme : 4.18.2011.6 | Moteur : 1.1.17700.4)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.327.1854.0**  
&ensp;Publication : **03 décembre 2020**  
&ensp;Plateforme : **4.18.2011.6**  
&ensp;Moteur : **1.1.17700.4**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
    
### <a name="whats-new"></a>Nouveautés

- Amélioration de la [journalisation de la prise en](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) charge de l’état SmartScreen

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu  
<br/>
</details><details>
<summary> Octobre-2020 (plateforme : 4.18.2010.7 | Moteur : 1.1.17600.5)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.327.7.0**  
&ensp;Publication : **29 octobre 2020**  
&ensp;Plateforme : **4.18.2010.7**  
&ensp;Moteur : **1.1.17600.5**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
    
### <a name="whats-new"></a>Nouveautés

- Nouvelles descriptions pour les catégories de menaces spéciales
- Fonctionnalités d’émulation améliorées
- Fonctionnalités améliorées d’autoriser/de bloquer l’adresse hôte
- Nouvelle option dans le programme CSP Defender pour ignorer la fusion des exclusions des utilisateurs locaux

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu  
<br/>
</details><details>
<summary> Septembre-2020 (plateforme : 4.18.2009.7 | Moteur : 1.1.17500.4)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.325.10.0**  
&ensp;Publication : **01 octobre 2020**  
&ensp;Plateforme : **4.18.2009.7**  
&ensp;Moteur : **1.1.17500.4**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
    
### <a name="whats-new"></a>Nouveautés

- Des autorisations d’administrateur sont requises pour restaurer les fichiers en quarantaine
- Les événements au format XML sont désormais pris en charge
- Prise en charge du programme CSP pour ignorer les fusions d’exclusions
- Nouvelles interfaces de gestion pour :
   - UDP Inspection
   - Protection du réseau sur Server 2019
   - Exclusions d’adresses IP pour la protection du réseau
- Meilleure visibilité des mesures du TPM
- Amélioration de l Office de module VBA

### <a name="known-issues"></a>Problèmes connus

Aucun problème connu  
<br/>
</details>
<details>
<summary> Août-2020 (plateforme : 4.18.2008.9 | Moteur : 1.1.17400.5)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.323.9.0**  
&ensp;Publication : **27 août 2020**  
&ensp;Plateforme : **4.18.2008.9**  
&ensp;Moteur : **1.1.17400.5**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**

### <a name="whats-new"></a>Nouveautés

- Ajouter d’autres événements de télémétrie
- Télémétrie améliorée des événements d’analyse
- Amélioration de la surveillance du comportement pour les analyses de mémoire
- Amélioration de l’analyse des flux de macros
- Ajouté à `AMRunningMode` la Get-MpComputerStatus cmdlet PowerShell
- [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) est ignoré. Antivirus Microsoft Defender s’arrête automatiquement lorsqu’il détecte un autre programme antivirus.


### <a name="known-issues"></a>Problèmes connus
Aucun problème connu  
<br/>
</details>

<details>
<summary> Juillet-2020 (plateforme : 4.18.2007.8 | Moteur : 1.1.17300.4)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.321.30.0**  
&ensp;Publication : **28 juillet 2020**  
&ensp;Plateforme : **4.18.2007.8**  
&ensp;Moteur : **1.1.17300.4**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
    
### <a name="whats-new"></a>Nouveautés

- Télémétrie améliorée pour BITS
- Validation améliorée du certificat de signature de code Authenticode

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu  
<br/>
</details>

<details>
<summary> Juin-2020 (plateforme : 4.18.2006.10 | Moteur : 1.1.17200.2)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.319.20.0**  
&ensp;Publication : **22 juin 2020**  
&ensp;Plateforme : **4.18.2006.10**  
&ensp;Moteur : **1.1.17200.2**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
    
### <a name="whats-new"></a>Nouveautés

- Possibilité de spécifier [l’emplacement des journaux de support](./collect-diagnostic-data.md)
- Ignorer l’analyse de rattrapage agressive en mode passif.
- Autoriser Defender à se mettre à jour sur les connexions à connexions avec des compteurs
- Réglage des performances fixes lorsque la mise en cache est désactivée 
- Requête de Registre fixe 
- Randomisation du scantime fixe dans ADMX

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu  
<br/>
</details>

<details>
<summary> Mai-2020 (plateforme : 4.18.2005.4 | Moteur : 1.1.17100.2)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.317.20.0**  
&ensp;Publication : **26 mai 2020**  
&ensp;Plateforme : **4.18.2005.4**  
&ensp;Moteur : **1.1.17100.2**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
    
### <a name="whats-new"></a>Nouveautés

- Enregistrement amélioré pour les événements d’analyse
- Amélioration de la gestion des incidents en mode utilisateur.
- Suivi des événements ajouté pour la protection contre la falsification
- Envoi d’exemples AMSI fixes
- Blocage du cloud AMSI fixe
- Journal d’installation des mises à jour de sécurité fixes

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu  
<br/>
</details>

<details>
<summary> Avril-2020 (plateforme : 4.18.2004.6 | Moteur : 1.1.17000.2)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.315.12.0**  
&ensp;Publication : **30 avril 2020**  
&ensp;Plateforme : **4.18.2004.6**  
&ensp;Moteur : **1.1.17000.2**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
    
### <a name="whats-new"></a>Nouveautés
- Améliorations apportées aux filtres WDfilter
- Ajouter des données d’événements actionnables à des événements de détection de réduction de la surface d’attaque
- Informations de version fixes dans les données de diagnostic et WMI
- Version de plateforme incorrecte corrigée dans l’interface utilisateur après la mise à jour de la plateforme
- Intel d’URL dynamique pour la protection contre les menaces sans fichier
- Fonctionnalité d’analyse UEFI
- Étendre la journalisation pour les mises à jour

### <a name="known-issues"></a>Problèmes connus
Aucun problème connu  
<br/>
</details>

<details>
<summary> Mars-2020 (plateforme : 4.18.2003.8 | Moteur : 1.1.16900.2)</summary>

&ensp;Version de mise à jour des informations de sécurité **: 1.313.8.0**  
&ensp;Publication : **24 mars 2020**  
&ensp;Plateforme : **4.18.2003.8**  
&ensp;Moteur : **1.1.16900.4**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
    
### <a name="whats-new"></a>Nouveautés

- Option limitation du processeur ajoutée à [MpCmdRun](./command-line-arguments-microsoft-defender-antivirus.md)
- Améliorer les fonctionnalités de diagnostic
- réduire le délai d’out des informations de sécurité (5 min)
- Étendre la fonctionnalité de journal interne du moteur AMSI
- Améliorer la notification pour le blocage des processus
   
### <a name="known-issues"></a>Problèmes connus
[**Fixe**] L’Antivirus Microsoft Defender ignorera les fichiers lors de l’exécution d’une analyse.

<br/>
</details>

<details>

<summary> Février-2020 (plateforme : - | Moteur : 1.1.16800.2)</summary>
  

&ensp;Version de mise à jour des informations de sécurité **: 1.311.4.0**   
&ensp;Publication : **25 février 2020**  
&ensp;Plateforme/client : **-**  
&ensp;Moteur : **1.1.16800.2**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
     
### <a name="whats-new"></a>Nouveautés

  
### <a name="known-issues"></a>Problèmes connus
Aucun problème connu
<br/>
</details>

<details>
<summary> Janvier-2020 (plateforme : 4.18.2001.10 | Moteur : 1.1.16700.2)</summary>
  

Version de mise à jour des informations de sécurité **: 1.309.32.0**  
Publication : **30 janvier 2020**  
Plateforme/Client : **4.18.2001.10**  
Moteur : **1.1.16700.2**  
&ensp;Phase de support : **prise en charge de la mise à niveau technique (uniquement)**
     
### <a name="whats-new"></a>Nouveautés

- Correction du BSOD sur WS2016 avec Exchange
- Prise en charge des mises à jour de plateforme lorsque le TMP est redirigé vers le chemin d’accès réseau
- Les versions de plateforme et de moteur sont [ajoutées à WDSI](https://www.microsoft.com/en-us/wdsi/defenderupdates) <!-- The preceding URL must include "/en-us" -->
- étendre la mise à jour des signatures d’urgence [en mode passif](./microsoft-defender-antivirus-compatibility.md)
- Correction du problème de 4.18.1911.3
   
### <a name="known-issues"></a>Problèmes connus

[**Fixed**] Devices using [modern standby mode](/windows-hardware/design/device-experiences/modern-standby) may experience a hang with the Windows Defender filter driver that results in a gap of protection.  Les ordinateurs concernés semblent ne pas avoir été mis à jour vers la dernière plateforme anti-programme malveillant.  
<br/>
> [!IMPORTANT]
> Cette mise à jour est :
> - nécessaire aux appareils RS1 exécutant une version inférieure de la plateforme pour prendre en charge SHA2 ;
> - a un indicateur de redémarrage pour les systèmes qui ont des problèmes en suspension ;
> - est re-publiée en avril 2020 et ne sera pas recalée par les mises à jour plus nouvelles pour conserver la disponibilité future ;  
> - est classée en tant que mise à jour en raison de l’exigence de redémarrage ; et
> - est uniquement proposé avec [Windows Update](https://support.microsoft.com/help/4027667/windows-10-update).
<br/>
</details>

<details>
<summary> Novembre-2019 (plateforme : 4.18.1911.3 | Moteur : 1.1.16600.7)</summary>

Version de mise à jour des informations de sécurité **: 1.307.13.0**  
Publication : **7 décembre 2019**  
Plateforme : **4.18.1911.3**  
Moteur : **1.1.17000.7**  
Phase de support : **aucune prise en charge**  
     
### <a name="whats-new"></a>Nouveautés

- Niveau de suivi MpCmdRun fixe
- Informations de version de WDFilter fixes
- Améliorer les notifications (PUA)
- ajouter des journaux MRT pour prendre en charge les fichiers
   
### <a name="known-issues"></a>Problèmes connus
Lorsque cette mise à jour est installée, l’appareil a besoin du package de saut 4.10.2001.10 pour pouvoir se mettre à jour vers la dernière version de la plateforme.
<br/>
</details>


## <a name="microsoft-defender-antivirus-platform-support"></a>Prise en charge de la plateforme antivirus Microsoft Defender
Les mises à jour de la plateforme et du moteur sont fournies à une cadence mensuelle. Pour être entièrement pris en charge, tenez à jour les dernières mises à jour de plateforme. Notre structure de support est dynamique et évolue en deux phases en fonction de la disponibilité de la dernière version de plateforme :

- Phase de maintenance des mises à jour **critiques** et de sécurité : lors de l’exécution de la dernière version de la plateforme, vous serez éligible à la réception des mises à jour de sécurité et critiques sur la plateforme anti-programme malveillant.
 
- **Phase de support technique (uniquement)** : après la publication d’une nouvelle version de plateforme, la prise en charge des versions antérieures (N-2) sera réduit au support technique uniquement. Les versions de plateforme antérieures à N-2 ne seront plus pris en charge.*

\* Le support technique continuera d’être fourni pour les mises à niveau de la version de Windows 10 (voir la version de plateforme incluse avec les versions [de Windows 10)](#platform-version-included-with-windows-10-releases)vers la dernière version de la plateforme.

Pendant la phase de support technique (uniquement), les incidents de support commercialement raisonnables sont fournis par le biais du support technique du service clientèle Microsoft & et des offres de support géré de Microsoft (telles que le support Premier). Si un incident de support nécessite une escalade vers le développement pour obtenir des conseils supplémentaires, nécessite une mise à jour non de sécurité ou nécessite une mise à jour de sécurité, les clients sont invités à mettre à niveau vers la dernière version de plateforme ou une mise à jour intermédiaire (*).

### <a name="platform-version-included-with-windows-10-releases"></a>Version de plateforme incluse dans les versions de Windows 10
Le tableau ci-dessous fournit la plateforme antivirus Microsoft Defender et les versions de moteur livrées avec les dernières versions de Windows 10 :    

|Version de Windows 10  |Version de la plateforme  |Version du moteur |Phase de prise en charge |
|:---|:---|:---|:---|
|2004 (20H1/20H2) |4.18.1909.6 |1.1.17000.2 | Prise en charge de la mise à niveau technique (uniquement) |
|1909 (19H2) |4.18.1902.5 |1.1.16700.3 | Prise en charge de la mise à niveau technique (uniquement) |
|1903 (19H1) |4.18.1902.5 |1.1.15600.4 | Prise en charge de la mise à niveau technique (uniquement) |
|1809 (RS5) |4.18.1807.18075 |1.1.15000.2 | Prise en charge de la mise à niveau technique (uniquement) |
|1803 (RS4) |4.13.17134.1 |1.1.14600.4 | Prise en charge de la mise à niveau technique (uniquement) |
|1709 (RS3) |4.12.16299.15 |1.1.14104.0 | Prise en charge de la mise à niveau technique (uniquement) |
|1703 (RS2) |4.11.15603.2 |1.1.13504.0 | Prise en charge de la mise à niveau technique (uniquement) |
|1607 (RS1) |4.10.14393.3683 |1.1.12805.0 | Prise en charge de la mise à niveau technique (uniquement) |  

Pour Windows 10 de publication, consultez la [Windows de faits sur le cycle de vie.](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)

## <a name="updates-for-deployment-image-servicing-and-management-dism"></a>Mises à jour pour la gestion et la maintenance des images de déploiement (DISM)

Nous vous recommandons de mettre à jour vos images d’installation Windows 10 (Enterprise, Pro et Éditions Famille), Windows Server 2019 et Windows Server 2016 OS avec les dernières mises à jour antivirus et anti-programme malveillant. La mise à jour de vos images d’installation du système d’exploitation permet d’éviter un écart de protection. 

Pour plus d’informations, voir Mise à [jour de Microsoft Defender pour Windows images d’installation du système d’exploitation.](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)

<details>
<summary>1.1.2105.01</summary>

&ensp;Version du package **: 1.1.2105.01**    
&ensp;Version de la plateforme **: 4.18.2103.7**   
&ensp;Version du moteur **: 1.1.18100.6**  
&ensp;Version de signature **: 1.339.42.0**    
    
### <a name="fixes"></a>Correctifs
- Aucune

### <a name="additional-information"></a>Informations supplémentaires
- Aucune  
<br/>
</details><details>
<summary>1.1.2104.01</summary>

&ensp;Version du package **: 1.1.2104.01**    
&ensp;Version de la plateforme **: 4.18.2102.4**   
&ensp;Version du moteur **: 1.1.18000.5**  
&ensp;Version de signature **: 1.335.232.0**    
    
### <a name="fixes"></a>Correctifs
- Aucune

### <a name="additional-information"></a>Informations supplémentaires
- Aucune  
<br/>
</details><details>
<summary>1.1.2103.01</summary>

&ensp;Version du package **: 1.1.2103.01**    
&ensp;Version de la plateforme **: 4.18.2101.9**   
&ensp;Version du moteur **: 1.1.17800.5**  
&ensp;Version de signature **: 1.331.2302.0**    
    
### <a name="fixes"></a>Correctifs
- Aucune

### <a name="additional-information"></a>Informations supplémentaires
- Aucune  
<br/>
</details><details>
<summary>1.1.2102.03</summary>

&ensp;Version du package **: 1.1.2102.03**    
&ensp;Version de la plateforme **: 4.18.2011.6**   
&ensp;Version du moteur **: 1.1.17800.5**  
&ensp;Version de signature **: 1.331.174.0**    
    
### <a name="fixes"></a>Correctifs
- Aucune

### <a name="additional-information"></a>Informations supplémentaires
- Aucune  
<br/>
</details><details>
<summary>1.1.2101.02</summary>

&ensp;Version du package **: 1.1.2101.02**    
&ensp;Version de la plateforme **: 4.18.2011.6**   
&ensp;Version du moteur **: 1.1.17700.4**  
&ensp;Version de signature **: 1.329.1796.0**    
    
### <a name="fixes"></a>Correctifs
- Aucune

### <a name="additional-information"></a>Informations supplémentaires
- Aucune  
<br/>
</details><details>
<summary>1.1.2012.01</summary>

&ensp;Version du package **: 1.1.2012.01**    
&ensp;Version de la plateforme **: 4.18.2010.7**   
&ensp;Version du moteur **: 1.1.17600.5**  
&ensp;Version de signature **: 1.327.1991.0**    
    
### <a name="fixes"></a>Correctifs
- Aucune

### <a name="additional-information"></a>Informations supplémentaires
- Aucune  
<br/>
</details><details>
<summary>1.1.2011.02</summary>

&ensp;Version du package **: 1.1.2011.02**    
&ensp;Version de la plateforme **: 4.18.2010.7**   
&ensp;Version du moteur **: 1.1.17600.5**  
&ensp;Version de signature **: 1.327.658.0**    
    
### <a name="fixes"></a>Correctifs
- Aucune

### <a name="additional-information"></a>Informations supplémentaires
- Signatures Antivirus Microsoft Defender actualisées  
<br/>
</details><details>
<summary>1.1.2011.01</summary>

&ensp;Version du package **: 1.1.2011.01**    
&ensp;Version de la plateforme **: 4.18.2009.7**  
&ensp;Version du moteur **: 1.1.17600.5**  
&ensp;Version de signature **: 1.327.344.0**    
    
### <a name="fixes"></a>Correctifs
- Aucune

### <a name="additional-information"></a>Informations supplémentaires
- Aucune  
<br/>
</details><details>
<summary>1.1.2009.10</summary>

&ensp;Version du package **: 1.1.2011.01**    
&ensp;Version de la plateforme **: 4.18.2008.9**   
&ensp;Version du moteur **: 1.1.17400.5**  
&ensp;Version de signature **: 1.327.2216.0**    
    
### <a name="fixes"></a>Correctifs
- Aucune

### <a name="additional-information"></a>Informations supplémentaires
- Ajout de la prise en charge Windows 10 images d’installation du système d’exploitation RS1 ou ultérieure.  
<br/>
</details>

## <a name="additional-resources"></a>Ressources supplémentaires

| Article | Description  |
|:---|:---|
|[Mise à jour de Microsoft Defender Windows images d’installation du système d’exploitation](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)  | Passer en revue les packages de mise à jour anti-programme malveillant pour vos images d’installation du système d’exploitation (fichiers WIM et VHD). Obtenez Antivirus Microsoft Defender mises à jour pour Windows 10 (éditions Enterprise, Pro et Famille), Windows Server 2019 et Windows Server 2016 images d’installation.  |
|[Gérer le téléchargement et l’application des mises à jour de protection](manage-protection-updates-microsoft-defender-antivirus.md) | Les mises à jour de la protection peuvent être livrées via de nombreuses sources. |
|[Gérer le moment où les mises à jour de la protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) | Vous pouvez planifier le téléchargement des mises à jour de la protection. |
|[Gérer les mises à jour des points de terminaison qui ne sont plus à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md) | Si un point de terminaison manque une mise à jour ou une analyse programmée, vous pouvez forcer une mise à jour ou une analyse la prochaine fois qu’un utilisateur se signe. |
|[Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md) | Vous pouvez définir des mises à jour de protection à télécharger au démarrage ou après certains événements de protection livrés par le cloud. |
|[Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)| Vous pouvez spécifier des paramètres, par exemple si des mises à jour doivent être mises à jour sur l’alimentation de la batterie, qui sont particulièrement utiles pour les appareils mobiles et les ordinateurs virtuels. |
