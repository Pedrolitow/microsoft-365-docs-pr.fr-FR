---
title: Informations de référence sur les règles de réduction de la surface d’attaque
description: Répertorie des détails sur les règles de réduction de la surface d’attaque (ASR) Microsoft Defender pour point de terminaison (MDE) par règle.
keywords: Règles de réduction de la surface d’attaque Microsoft, Microsoft Defender pour point de terminaison règles ASR, liste des règles ASR, ASR, règles asr, hanches, système de prévention des intrusions de l’hôte, règles de protection, règles anti-exploit, antiexploitation, règles d’exploitation, règles de prévention des infections, Microsoft Defender pour point de terminaison, configurer des règles ASR, description de la règle ASR
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.service: microsoft-365-security
ms.subservice: mde
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar,
manager: dansimp
ms.custom: asr
ms.topic: reference
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 2072af8e0591ae0657457b00dbcfec6c7b21ff82
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68718235"
---
# <a name="attack-surface-reduction-asr-rules-reference"></a>Référence des règles de réduction de la surface d’attaque (ASR)

**S’applique à :**

- [Microsoft Microsoft 365 Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plates-formes:**

- Windows

Cet article fournit des informations sur Microsoft Defender pour point de terminaison règles de réduction de la surface d’attaque (ASR) :

- [Versions de système d’exploitation prises en charge par les règles ASR](#asr-rules-supported-operating-systems)
- [Règles ASR prises en charge des systèmes de gestion de configuration](#asr-rules-supported-configuration-management-systems)
- [Par règle ASR, détails de l’alerte et de la notification](#per-asr-rule-alert-and-notification-details)
- [Règle ASR en matrice GUID](#asr-rule-to-guid-matrix)
- [Modes de règle ASR](#asr-rule-modes)
- [Descriptions par règle](#per-rule-descriptions)

## <a name="attack-surface-reduction-rules-by-type"></a>Règles de réduction de la surface d’attaque par type

Les règles ASR sont classées comme l’un des deux types suivants :

1. **Règles de protection standard** : il s’agit de l’ensemble minimal de règles que Microsoft vous recommande de toujours activer, pendant que vous évaluez l’impact et les besoins de configuration des autres règles ASR. Ces règles ont généralement un impact minime ou nul sur l’utilisateur final.
1. **Autres règles** : règles qui nécessitent une certaine mesure de suivre les étapes de déploiement documentées [Planifier > test (audit) > Activer (mode bloc/avertissement)], comme indiqué dans le guide de déploiement des règles de réduction de la surface d’attaque [(ASR)](attack-surface-reduction-rules-deployment.md)

Pour obtenir la méthode la plus simple permettant d’activer les règles de protection standard, consultez : [Option de protection standard simplifiée](attack-surface-reduction-rules-report.md#simplified-standard-protection-option).

| Nom de la règle ASR : | Règle de protection standard ? | Une autre règle ? |
|:---|:---|:---|
| Bloquer les abus de conducteurs vulnérables exploités signés| Oui | |
| Empêcher Adobe Reader de créer des processus enfants | | Oui |
| Empêcher toutes les applications Office de créer des processus enfants | | Oui |
| Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe) | Oui | |
| Bloquer le contenu exécutable du client de messagerie et de la messagerie web | | Oui |
| Bloquer l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance | | Oui |
| Bloquer l’exécution de scripts potentiellement obfusqués | | Oui |
| Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé | | Oui |
| Empêcher les applications Office de créer du contenu exécutable | | Oui |
| Empêcher les applications Office d’injecter du code dans d’autres processus | | Oui |
| Empêcher l’application de communication Office de créer des processus enfants | | Oui |
| Bloquer la persistance via un abonnement aux événements WMI | Oui | |
| Bloquer les créations de processus provenant des commandes PSExec et WMI | | Oui |
| Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB | | Oui |
| Bloquer les appels d’API Win32 à partir de macros Office | | Oui |
| Utiliser une protection avancée contre les rançongiciels | | Oui |

## <a name="asr-rules-supported-operating-systems"></a>Systèmes d’exploitation pris en charge par les règles ASR

Le tableau suivant répertorie les systèmes d’exploitation pris en charge pour les règles actuellement publiées en disponibilité générale. Les règles sont répertoriées par ordre alphabétique dans ce tableau.

> [!NOTE]
>
> Sauf indication contraire, la version minimale de Windows&nbsp;10 est la version 1709 (RS3, build 16299) ou ultérieure ; la version minimale de Windows&nbsp;Server est la version 1809 ou ultérieure.
>
> Les règles de réduction de la surface d’attaque dans Windows&nbsp;Server&nbsp;2012&nbsp;R2 et Windows&nbsp;Server&nbsp;2016 sont disponibles pour les appareils intégrés à l’aide du package de solution unifiée moderne. Pour plus d’informations, consultez [Nouvelles fonctionnalités de la solution unifiée moderne pour Windows Server 2012 R2 et 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

| Nom de la règle| Windows&nbsp;11 <br>et<br> Windows&nbsp;10 | Windows&nbsp;Server <br> 2022 <br>et<br>  Windows&nbsp;Server <br> 2019 | Windows Server | Windows&nbsp;Server <br> 2016 <sup>[[1, 2](#fn1)]<sup></sup> | Windows&nbsp;Server <br> 2012&nbsp;R2 <sup>[[1, 2](#fn1)]<sup></sup> |
|:---|:---:|:---:|:---:|:---:|:---:|
| [Bloquer les abus de conducteurs vulnérables exploités signés](#block-abuse-of-exploited-vulnerable-signed-drivers) | v | v | v <br> version 1803 (Canal Entreprise semi-annuel) ou ultérieure | v | v |
| [Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | v <br> version 1809 ou ultérieure <sup>[[3](#fn1)]<sup></sup> | v | v | v | v |
| [Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) | v | v | v | v | v |
| [Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | v <br> version 1803 ou ultérieure <sup>[[3](#fn1)]<sup></sup> | v | v | v | v |
| [Bloquer le contenu exécutable du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) | v | v | v | v | v |
| [Bloquer l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | v <br> version 1803 ou ultérieure <sup>[[3](#fn1)]<sup></sup> | v | v | v | v |
| [Bloquer l’exécution de scripts potentiellement obfusqués](#block-execution-of-potentially-obfuscated-scripts) | v | v | v | v | v |
| [Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | v | v | v | N | N |
| [Empêcher les applications Office de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) | v | v | v | v | v |
| [Empêcher les applications Office d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes)  | v | v | v | v | v |
| [Empêcher l’application de communication Office de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) | v | v | v | v | v |
| [Bloquer la persistance via l’abonnement aux événements WMI (Windows Management Instrumentation)](#block-persistence-through-wmi-event-subscription) <br> \*_Exclusions de fichiers et de dossiers non prises en charge._ | v <br> version 1903 (build 18362) ou ultérieure <sup>[[3](#fn1)]<sup></sup> | v | v <br> version 1903 (build 18362) ou ultérieure | N | N |
| [Bloquer les créations de processus provenant des commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | v <br> version 1803 ou ultérieure <sup>[[3](#fn1)]<sup></sup> | v | v | v | v |
| [Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | v | v | v | v | v |
| [Bloquer les appels d’API Win32 à partir de macros Office](#block-win32-api-calls-from-office-macros) | v | v | v | N | N |
| [Utiliser une protection avancée contre les rançongiciels](#use-advanced-protection-against-ransomware) | v <br> version 1803 ou ultérieure <sup>[[3](#fn1)]<sup></sup> | v | v | v | v |

(<a id="fn1">1</a>) Fait référence à la solution unifiée moderne pour Windows Server 2012 et 2016. Pour plus d’informations, consultez [Intégrer des serveurs Windows au service Defender pour point de terminaison](configure-server-endpoints.md).

(<a id="fn1">2</a>) Pour Windows&nbsp;Server 2016 et Windows&nbsp;Server 2012&nbsp;R2, la version minimale requise de Microsoft Endpoint Configuration Manager est la version 2111.

(<a id="fn1">3</a>) La version et le numéro de build s’appliquent uniquement à Windows&nbsp;10.

## <a name="asr-rules-supported-configuration-management-systems"></a>Règles ASR prises en charge des systèmes de gestion de configuration

Les liens vers des informations sur les versions du système de gestion de la configuration référencées dans ce tableau sont répertoriés sous ce tableau.

|Nom de la règle | Microsoft Intune | Microsoft Endpoint Configuration Manager |<sup>stratégie de groupe[[1](#fn1)]<sup></sup> | PowerShell<sup>[[1](#fn1)]<sup></sup>  |
|---|:---:|:---:|:---:|:---:|
|[Bloquer les abus de conducteurs vulnérables exploités signés](#block-abuse-of-exploited-vulnerable-signed-drivers) | v |   | v  |  v  |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | v |  | v  | v  |
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) | v |v <br><br> CB 1710 | v  | v  |
|[Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | v  | v <br><br>CB 1802 | v  | v  |
|[Bloquer le contenu exécutable du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) | v |v <br><br> CB 1710 | v | v  |
|[Bloquer l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | v | v <br><br> CB 1802 |  v |  v |
|[Bloquer l’exécution de scripts potentiellement obfusqués](#block-execution-of-potentially-obfuscated-scripts) | v |v  <br><br> CB 1710 | v  | v  |
|[Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | v |v <br><br> CB 1710 | v  | v  |
|[Empêcher les applications Office de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) | v |v <br><br> CB 1710 | v  | v  |
|[Empêcher les applications Office d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes) | v |v <br><br> CB 1710 | v  | v  |
|[Empêcher l’application de communication Office de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) | v |v <br><br> CB 1710 | v  | v  |
|[Bloquer la persistance via un abonnement aux événements WMI](#block-persistence-through-wmi-event-subscription) |v  |  |v   | v  |
|[Bloquer les créations de processus provenant des commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | v |   |  v | v  |
|[Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | v |v <br><br> CB 1802  | v  | v  |
|[Bloquer les appels d’API Win32 à partir de macros Office](#block-win32-api-calls-from-office-macros) | v |v <br><br> CB 1710  | v  |  v |
|[Utiliser une protection avancée contre les rançongiciels](#use-advanced-protection-against-ransomware) | v |v <br><br> CB 1802 | v  | v  |

  (<a id="fn1">1</a>) Vous pouvez configurer des règles de réduction de la surface d’attaque par règle à l’aide du GUID de n’importe quelle règle.

- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)
- [Microsoft Endpoint Manager CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager (SCCM) CB 1710](/configmgr/core/servers/manage/updates) <br>_SCCM est désormais Microsoft Endpoint Configuration Manager._

## <a name="per-asr-rule-alert-and-notification-details"></a>Par règle ASR, détails de l’alerte et de la notification

Les notifications toast sont générées pour toutes les règles en mode Bloc. Les règles dans un autre mode ne génèrent pas de notifications toast

Pour les règles dont l’état de la règle est spécifié :

- Les règles ASR avec \<ASR Rule, Rule State\> combinaisons sont utilisées pour exposer des alertes (notifications toast) sur Microsoft Defender pour point de terminaison uniquement pour les appareils au niveau du bloc cloud élevé. Les appareils qui ne sont pas au niveau du bloc cloud élevé ne génèrent pas d’alertes pour les combinaisons <règle ASR, État de la règle>
- Les alertes EDR sont générées pour les règles ASR dans les états spécifiés, mais uniquement pour les appareils au niveau du bloc cloud élevé.

| Nom de la règle : | État de la règle : | Génère des alertes dans EDR ? <br> (Oui)&nbsp;\|&nbsp;Non) | Génère des notifications toast ? <br> (Oui)&nbsp;\|&nbsp;Non) |
|---|:---:|:---:|:---:|
|   |   |  _Uniquement pour les appareils au niveau du bloc de cloud élevé_ | _En mode Bloc uniquement_ |
|[Bloquer les abus de conducteurs vulnérables exploités signés](#block-abuse-of-exploited-vulnerable-signed-drivers) |   | N  | v |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | Bloquer  | v <br> Nécessite l’appareil au niveau du bloc cloud élevé  | v <br> Nécessite l’appareil au niveau du bloc cloud élevé |
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) |   | N | v |
|[Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) |   | N | v |
|[Bloquer le contenu exécutable du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) |   | v <br> Nécessite l’appareil au niveau du bloc cloud élevé | v <br> Nécessite l’appareil au niveau du bloc cloud élevé |
|[Bloquer l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) |   | N | v |
|[Bloquer l’exécution de scripts potentiellement obfusqués](#block-execution-of-potentially-obfuscated-scripts) |  Bloc d’audit&nbsp;\|&nbsp; | Y \| Y <br> Nécessite l’appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite l’appareil au niveau du bloc cloud élevé |
|[Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Bloquer | v <br> Nécessite l’appareil au niveau du bloc cloud élevé  | v <br> Nécessite l’appareil au niveau du bloc cloud élevé |
|[Empêcher les applications Office de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) |   | N | v |
|[Empêcher les applications Office d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes)  |   | N | v |
|[Empêcher l’application de communication Office de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) |  |  N | v |
|[Bloquer la persistance via un abonnement aux événements WMI](#block-persistence-through-wmi-event-subscription) |  Bloc d’audit&nbsp;\|&nbsp; | Y \| Y <br> Nécessite l’appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite l’appareil au niveau du bloc cloud élevé |
|[Bloquer les créations de processus provenant des commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) |   | N | v |
|[Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Bloc d’audit&nbsp;\|&nbsp; | Y \| Y <br> Nécessite l’appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite l’appareil au niveau du bloc cloud élevé |
|[Bloquer les appels d’API Win32 à partir de macros Office](#block-win32-api-calls-from-office-macros) |   | N | v |
|[Utiliser une protection avancée contre les rançongiciels](#use-advanced-protection-against-ransomware) | Bloc d’audit&nbsp;\|&nbsp; | Y \| Y <br> Nécessite l’appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite l’appareil au niveau du bloc cloud élevé |
  
## <a name="asr-rule-to-guid-matrix"></a>Règle ASR en matrice GUID

| Nom de la règle | GUID de règle |
|:-----|:-----|
| Bloquer les abus de conducteurs vulnérables exploités signés | 56a863a9-875e-4185-98a7-b882c64b5ce5 |
| Empêcher Adobe Reader de créer des processus enfants | 7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c |
| Empêcher toutes les applications Office de créer des processus enfants | d4f940ab-401b-4efc-aadc-ad5f3c50688a |
| Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe) | 9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2 |
| Bloquer le contenu exécutable du client de messagerie et de la messagerie web | be9ba2d9-53ea-4cdc-84e5-9b1eeeeee46550 |
| Bloquer l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance | 01443614-cd74-433a-b99e-2ecdc07bfc25 |
| Bloquer l’exécution de scripts potentiellement obfusqués | 5beb7efe-fd9a-4556-801d-275e5ffc04cc |
| Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé | d3e037e1-3eb8-44c8-a917-57927947596d |
| Empêcher les applications Office de créer du contenu exécutable | 3b576869-a4ec-4529-8536-b80a7769e899 |
| Empêcher les applications Office d’injecter du code dans d’autres processus | 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84 |
| Empêcher l’application de communication Office de créer des processus enfants | 26190899-1602-49e8-8b27-eb1d0a1ce869 |
| Bloquer la persistance via un abonnement aux événements WMI <br>* Exclusions de fichiers et de dossiers non prises en charge. | e6db77e5-3df2-4cf1-b95a-636979351e5b |
| Bloquer les créations de processus provenant des commandes PSExec et WMI | d1e49aac-8f56-4280-b9ba-993a6d77406c |
| Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB | b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4 |
| Bloquer les appels d’API Win32 à partir de macros Office | 92e97fa1-2edf-4476-bdd6-9dd0b4ddddc7b |
| Utiliser une protection avancée contre les rançongiciels | c1db55ab-c21a-4637-bb3f-a12568109d35 |

## <a name="asr-rule-modes"></a>Modes de règle ASR

- **Non configuré** ou **Désactivé** : état dans lequel la règle ASR n’a pas été activée ou a été désactivée. Code de cet état = 0.
- **Bloquer** : état dans lequel la règle ASR est activée. Le code de cet état est 1.
- **Audit** : état dans lequel la règle ASR est évaluée pour l’effet qu’elle aurait sur l’organisation ou l’environnement si elle est activée (définie sur bloquer ou avertir). Le code de cet état est 2.
- **Avertir** État dans lequel la règle ASR est activée et présente une notification à l’utilisateur final, mais permet à l’utilisateur final de contourner le bloc. Le code pour cet état est 6.

_Le mode d’avertissement_ est un type de mode bloc qui avertit les utilisateurs des actions potentiellement risquées. Les utilisateurs peuvent choisir de contourner le message d’avertissement de blocage et d’autoriser l’action sous-jacente. Les utilisateurs peuvent sélectionner **OK** pour appliquer le bloc, ou sélectionner l’option de contournement - **Débloquer** - via la notification toast contextuelle de l’utilisateur final qui est générée au moment du blocage. Une fois l’avertissement débloqué, l’opération est autorisée jusqu’à la prochaine fois que le message d’avertissement se produit, à laquelle l’utilisateur final doit effectuer une nouvelle exécution de l’action.

Lorsque vous cliquez sur le bouton Autoriser, le bloc est supprimé pendant 24 heures. Après 24 heures, l’utilisateur final doit autoriser à nouveau le bloc. Le mode d’avertissement pour les règles ASR est pris en charge uniquement pour les appareils RS5+ (1809+). Si le contournement est affecté à des règles ASR sur des appareils avec des versions antérieures, la règle est en mode bloqué.

Vous pouvez également définir une règle en mode d’avertissement via PowerShell en spécifiant le AttackSurfaceReductionRules_Actions « Avertir ». Par exemple :

```powershell
-command "& {&'Add-MpPreference' -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Warn"} 
```

## <a name="per-rule-descriptions"></a>Descriptions par règle

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>Bloquer les abus de conducteurs vulnérables exploités signés

Cette règle empêche une application d’écrire un pilote signé vulnérable sur le disque. Les pilotes signés in-the-wild et vulnérables peuvent être exploités par des applications \- locales _qui disposent de privilèges suffisants_ \- pour accéder au noyau. Les pilotes signés vulnérables permettent aux attaquants de désactiver ou de contourner les solutions de sécurité, ce qui aboutit à la compromission du système.

La règle **Bloquer l’abus des pilotes signés vulnérables exploités** n’empêche pas le chargement d’un pilote existant déjà sur le système.

> [!NOTE]
>
> Vous pouvez configurer cette règle à l’aide de MEM OMA-URI. Consultez [MEM OMA-URI](enable-attack-surface-reduction.md#mem) pour configurer des règles personnalisées.
>
> Vous pouvez également configurer cette règle à l’aide de [PowerShell](enable-attack-surface-reduction.md#powershell).
>
> Pour qu’un pilote soit examiné, utilisez ce site Web [pour soumettre un pilote à des fins d’analyse](https://www.microsoft.com/en-us/wdsi/driversubmission).

<!--The above link is the 'only link' that exists for having drivers examined. The 'en-us' component is required to make the link work. Any alterations to this link will result in a 404.
-->

nom de Intune :`Block abuse of exploited vulnerable signed drivers`

nom de Configuration Manager : pas encore disponible
  
GUID:  `56a863a9-875e-4185-98a7-b882c64b5ce5`

Type d’action de repérage avancé :

- AsrVulnerableSignedDriverAudited
- AsrVulnerableSignedDriverBlocked

<!-- 
Dependencies: none provided by engineering
-->

### <a name="block-adobe-reader-from-creating-child-processes"></a>Empêcher Adobe Reader de créer des processus enfants

Cette règle empêche les attaques en empêchant Adobe Reader de créer des processus.

Les programmes malveillants peuvent télécharger et lancer des charges utiles et sortir d’Adobe Reader par le biais d’une ingénierie sociale ou d’exploits. En empêchant les processus enfants d’être générés par Adobe Reader, les programmes malveillants qui tentent d’utiliser Adobe Reader comme vecteur d’attaque sont empêchés de se propager.

nom de Intune :`Process creation from Adobe Reader (beta)`

nom de Configuration Manager : pas encore disponible

GUID : `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

Type d’action de repérage avancé :

- AsrAdobeReaderChildProcessAudited
- AsrAdobeReaderChildProcessBlocked

Dépendances : antivirus Microsoft Defender

### <a name="block-all-office-applications-from-creating-child-processes"></a>Empêcher toutes les applications Office de créer des processus enfants

Cette règle empêche les applications Office de créer des processus enfants. Les applications Office incluent Word, Excel, PowerPoint, OneNote et Access.

La création de processus enfants malveillants est une stratégie de programme malveillant courante. Les programmes malveillants qui abusent d’Office en tant que vecteur exécutent souvent des macros VBA et exploitent du code pour télécharger et tenter d’exécuter davantage de charges utiles. Toutefois, certaines applications métier légitimes peuvent également générer des processus enfants à des fins bénignes; par exemple, la génération d’une invite de commandes ou l’utilisation de PowerShell pour configurer les paramètres du Registre.

nom de Intune :`Office apps launching child processes`

nom de Configuration Manager :`Block Office application from creating child processes`

GUID : `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

Type d’action de repérage avancé :

- AsrOfficeChildProcessAudited
- AsrOfficeChildProcessBlocked

Dépendances : antivirus Microsoft Defender

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows

Cette règle permet d’empêcher le vol d’informations d’identification en verrouillant le service LSASS (Local Security Authority Subsystem Service).

LSASS authentifie les utilisateurs qui se connectent sur un ordinateur Windows. Microsoft Defender Credential Guard dans Windows empêche normalement les tentatives d’extraction d’informations d’identification à partir de LSASS. Certaines organisations ne peuvent pas activer Credential Guard sur tous leurs ordinateurs en raison de problèmes de compatibilité avec les pilotes de carte à puce personnalisés ou d’autres programmes qui se chargent dans l’autorité de sécurité locale (LSA). Dans ces cas, les attaquants peuvent utiliser des outils tels que Mimikatz pour récupérer des mots de passe en texte clair et des hachages NTLM à partir de LSASS.

> [!NOTE]
> Dans certaines applications, le code énumère tous les processus en cours d’exécution et tente de les ouvrir avec des autorisations exhaustives. Cette règle refuse l’action d’ouverture du processus de l’application et enregistre les détails dans le journal des événements de sécurité. Cette règle peut générer beaucoup de bruit. Si vous avez une application qui énumère simplement LSASS, mais n’a aucun impact réel sur les fonctionnalités, il n’est pas nécessaire de l’ajouter à la liste d’exclusions. En soi, cette entrée du journal des événements n’indique pas nécessairement une menace malveillante.
  
> [!IMPORTANT]
> L’état par défaut de la règle de réduction de la surface d’attaque (ASR) « Bloquer le vol d’informations d’identification du sous-système d’autorité de sécurité locale Windows (lsass.exe) » passe de **Non configuré** à **Configuré** et le mode par défaut est défini sur **Bloquer**. Toutes les autres règles ASR restent dans leur état par défaut : **Non configuré**. Une logique de filtrage supplémentaire a déjà été incorporée dans la règle pour réduire les notifications des utilisateurs finaux. Les clients peuvent configurer la règle en mode **Audit**, **Avertissement** ou **Désactivé** , ce qui remplacera le mode par défaut. La fonctionnalité de cette règle est la même, que la règle soit configurée en mode activé par défaut ou si vous activez le mode Bloquer manuellement.

nom de Intune :`Flag credential stealing from the Windows local security authority subsystem`

nom de Configuration Manager :`Block credential stealing from the Windows local security authority subsystem`

GUID : `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

Type d’action de repérage avancé :

- AsrLsassCredentialTheftAudited
- AsrLsassCredentialTheftBlocked

Dépendances : antivirus Microsoft Defender

### <a name="block-executable-content-from-email-client-and-webmail"></a>Bloquer le contenu exécutable du client de messagerie et de la messagerie web

Cette règle empêche le lancement des types de fichiers suivants à partir d’un e-mail ouvert dans l’application Microsoft Outlook, ou Outlook.com et d’autres fournisseurs de messagerie web populaires :

- Fichiers exécutables (tels que .exe, .dll ou .scr)
- Fichiers de script (tels qu’un fichier .ps1 PowerShell, Visual Basic .vbs ou JavaScript .js)

nom de Intune :`Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

Nom de Microsoft Endpoint Manager : `Block executable content from email client and webmail`

GUID : `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

Type d’action de repérage avancé :

- AsrExecutableEmailContentAudited
- AsrExecutableEmailContentBlocked

Dépendances : antivirus Microsoft Defender

> [!NOTE]
> La règle **Bloquer le contenu exécutable du client de messagerie et de la messagerie web** contient les descriptions alternatives suivantes, selon l’application que vous utilisez :
>
> - Intune (profils de configuration) : exécution du contenu exécutable (exe, dll, ps, js, vbs, etc.) supprimé de l’e-mail (webmail/client de messagerie) (aucune exception).
> - Endpoint Manager : bloquer le téléchargement de contenu exécutable à partir des clients de messagerie et de messagerie web.
> - stratégie de groupe : bloquer le contenu exécutable du client de messagerie et de la messagerie web.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>Bloquer l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance

Cette règle empêche le lancement des fichiers exécutables, tels que .exe, .dll ou .scr. Par conséquent, le lancement de fichiers exécutables non approuvés ou inconnus peut être risqué, car il peut ne pas être clair au départ si les fichiers sont malveillants.

> [!IMPORTANT]
> Vous devez [activer la protection fournie par le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) pour utiliser cette règle.
>
> La règle **Bloquer l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste approuvée** avec GUID `01443614-cd74-433a-b99e-2ecdc07bfc25` , appartient à Microsoft et n’est pas spécifiée par les administrateurs. Cette règle utilise la protection fournie par le cloud pour mettre à jour régulièrement sa liste approuvée.
>
> Vous pouvez spécifier des fichiers ou dossiers individuels (à l’aide de chemins d’accès aux dossiers ou de noms de ressources complets), mais vous ne pouvez pas spécifier les règles ou exclusions qui s’appliquent.

nom de Intune :`Executables that don't meet a prevalence, age, or trusted list criteria`

nom de Configuration Manager :`Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID : `01443614-cd74-433a-b99e-2ecdc07bfc25`

Type d’action de repérage avancé :

- AsrUntrustedExecutableAudited
- AsrUntrustedExecutableBlocked

Dépendances : antivirus Microsoft Defender, protection cloud

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>Bloquer l’exécution de scripts potentiellement obfusqués

Cette règle détecte les propriétés suspectes dans un script obfusqué.
  
> [!IMPORTANT]
> Les scripts PowerShell ont été temporairement exclus de la règle « Bloquer l’exécution de scripts potentiellement obfusqués » en raison des problèmes fp à grande échelle rencontrés dans le passé.

L’obfuscation de script est une technique courante que les auteurs de programmes malveillants et les applications légitimes utilisent pour masquer la propriété intellectuelle ou réduire les temps de chargement des scripts. Les auteurs de programmes malveillants utilisent également l’obfuscation pour rendre le code malveillant plus difficile à lire, ce qui empêche l’examen de près par les humains et les logiciels de sécurité.

> [!IMPORTANT]
> En raison du nombre élevé de faux positifs, cette règle ne détecte actuellement pas les scripts PowerShell ; il s’agit d’une solution temporaire. La règle sera mise à jour et commencera à détecter à nouveau les scripts PowerShell bientôt.

nom de Intune :`Obfuscated js/vbs/ps/macro code`

nom de Configuration Manager :`Block execution of potentially obfuscated scripts`

GUID : `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

Type d’action de repérage avancé :

- AsrObfuscatedScriptAudited
- AsrObfuscatedScriptBlocked

Dépendances : antivirus Microsoft Defender, interface d’analyse anti-programme malveillant (AMSI)

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé

Cette règle empêche les scripts de lancer du contenu téléchargé potentiellement malveillant. Les logiciels malveillants écrits en JavaScript ou VBScript agissent souvent comme un téléchargeur pour extraire et lancer d’autres programmes malveillants à partir d’Internet.

Bien qu’elles ne soient pas courantes, les applications métier utilisent parfois des scripts pour télécharger et lancer des programmes d’installation.

nom de Intune :`js/vbs executing payload downloaded from Internet (no exceptions)`

nom de Configuration Manager :`Block JavaScript or VBScript from launching downloaded executable content`

GUID : `d3e037e1-3eb8-44c8-a917-57927947596d`

Type d’action de repérage avancé :

- AsrScriptExecutableDownloadAudited
- AsrScriptExecutableDownloadBlocked

Dépendances : antivirus Microsoft Defender, AMSI

### <a name="block-office-applications-from-creating-executable-content"></a>Empêcher les applications Office de créer du contenu exécutable

Cette règle empêche les applications Office, notamment Word, Excel et PowerPoint, de créer du contenu exécutable potentiellement malveillant, en empêchant l’écriture de code malveillant sur le disque.

Les programmes malveillants qui abusent d’Office en tant que vecteur peuvent tenter de sortir d’Office et d’enregistrer des composants malveillants sur le disque. Ces composants malveillants survivraient à un redémarrage de l’ordinateur et persistaient sur le système. Par conséquent, cette règle se défend contre une technique de persistance courante.

nom de Intune :`Office apps/macros creating executable content`

Nom SCCM : `Block Office applications from creating executable content`

GUID : `3b576869-a4ec-4529-8536-b80a7769e899`

Type d’action de repérage avancé :

- AsrExecutableOfficeContentAudited
- AsrExecutableOfficeContentBlocked

Dépendances : antivirus Microsoft Defender, RPC

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>Empêcher les applications Office d’injecter du code dans d’autres processus

Cette règle bloque les tentatives d’injection de code des applications Office dans d’autres processus.

Les attaquants peuvent tenter d’utiliser des applications Office pour migrer du code malveillant vers d’autres processus via l’injection de code, de sorte que le code peut se faire passer pour un processus propre.

Il n’existe pas d’objectif commercial légitime connu pour l’utilisation de l’injection de code.

Cette règle s’applique à Word, Excel et PowerPoint.

nom de Intune :`Office apps injecting code into other processes (no exceptions)`

nom de Configuration Manager :`Block Office applications from injecting code into other processes`

GUID : `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

Type d’action de repérage avancé :

- AsrOfficeProcessInjectionAudited
- AsrOfficeProcessInjectionBlocked

Dépendances : antivirus Microsoft Defender

### <a name="block-office-communication-application-from-creating-child-processes"></a>Empêcher l’application de communication Office de créer des processus enfants

Cette règle empêche Outlook de créer des processus enfants, tout en autorisant les fonctions Outlook légitimes.

Cette règle protège contre les attaques d’ingénierie sociale et empêche l’exploitation du code d’abuser des vulnérabilités dans Outlook. Il protège également contre les [règles et les attaques de formulaires Outlook](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) que les attaquants peuvent utiliser quand les informations d’identification d’un utilisateur sont compromises.

> [!NOTE]
> Cette règle bloque les conseils de stratégie DLP et les info-bulles dans Outlook. Cette règle s’applique uniquement à Outlook et Outlook.com.

nom de Intune :`Process creation from Office communication products (beta)`

Configuration Manager nom : non disponible

GUID : `26190899-1602-49e8-8b27-eb1d0a1ce869`

Type d’action de repérage avancé :

- AsrOfficeCommAppChildProcessAudited
- AsrOfficeCommAppChildProcessBlocked

Dépendances : antivirus Microsoft Defender

### <a name="block-persistence-through-wmi-event-subscription"></a>Bloquer la persistance via un abonnement aux événements WMI

Cette règle empêche les programmes malveillants d’utiliser WMI à mauvais escient pour obtenir une persistance sur un appareil.

> [!IMPORTANT]
> Les exclusions de fichiers et de dossiers ne s’appliquent pas à cette règle de réduction de la surface d’attaque.

Les menaces sans fichier emploient diverses tactiques pour rester cachées, éviter d’être vues dans le système de fichiers et obtenir un contrôle d’exécution périodique. Certaines menaces peuvent utiliser à mauvais escient le dépôt WMI et le modèle d’événement pour rester cachées.

Intune nom : non disponible

Configuration Manager nom : non disponible

GUID : `e6db77e5-3df2-4cf1-b95a-636979351e5b`

Type d’action de repérage avancé :

- AsrPersistenceThroughWmiAudited
- AsrPersistenceThroughWmiBlocked

Dépendances : antivirus Microsoft Defender, RPC

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>Bloquer les créations de processus provenant des commandes PSExec et WMI

Cette règle empêche l’exécution des processus créés via [PsExec](/sysinternals/downloads/psexec) et [WMI](/windows/win32/wmisdk/about-wmi) . PsExec et WMI peuvent exécuter du code à distance. Il existe un risque de programmes malveillants qui abusent des fonctionnalités de PsExec et WMI à des fins de commande et de contrôle, ou de propager une infection sur le réseau d’une organisation.

> [!WARNING]
> Utilisez cette règle uniquement si vous gérez vos appareils avec [Intune](/intune) ou une autre solution MDM. Cette règle n’est pas compatible avec la gestion via [Microsoft Endpoint Configuration Manager](/configmgr), car elle bloque les commandes WMI que le client Configuration Manager utilise pour fonctionner correctement.

nom de Intune :`Process creation from PSExec and WMI commands`

nom de Configuration Manager : Non applicable

GUID : `d1e49aac-8f56-4280-b9ba-993a6d77406c`

Type d’action de repérage avancé :

- AsrPsexecWmiChildProcessAudited
- AsrPsexecWmiChildProcessBlocked

Dépendances : antivirus Microsoft Defender

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB

Avec cette règle, les administrateurs peuvent empêcher l’exécution de fichiers exécutables non signés ou non approuvés à partir de lecteurs usb amovibles, y compris les cartes SD. Les types de fichiers bloqués incluent des fichiers exécutables (tels que .exe, .dll ou .scr)

> [!IMPORTANT]
> Les fichiers copiés à partir de l’USB vers le lecteur de disque sont bloqués par cette règle si et quand il est sur le point d’être exécuté sur le lecteur de disque.

nom de Intune :`Untrusted and unsigned processes that run from USB`

nom de Configuration Manager :`Block untrusted and unsigned processes that run from USB`

GUID : `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

Type d’action de repérage avancé :

- AsrUntrustedUsbProcessAudited
- AsrUntrustedUsbProcessBlocked

Dépendances : antivirus Microsoft Defender

### <a name="block-win32-api-calls-from-office-macros"></a>Bloquer les appels d’API Win32 à partir de macros Office

Cette règle empêche les macros VBA d’appeler des API Win32.

Office VBA active les appels d’API Win32. Les programmes malveillants peuvent abuser de cette fonctionnalité, comme [appeler des API Win32 pour lancer un shellcode malveillant](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) sans écrire quoi que ce soit directement sur le disque. La plupart des organisations ne s’appuient pas sur la possibilité d’appeler des API Win32 dans leur fonctionnement quotidien, même si elles utilisent des macros d’une autre manière.

Systèmes d’exploitation pris en charge :          

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

nom de Intune :`Win32 imports from Office macro code`

nom de Configuration Manager :`Block Win32 API calls from Office macros`

GUID : `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

Type d’action de repérage avancé :

- AsrOfficeMacroWin32ApiCallsAudited
- AsrOfficeMacroWin32ApiCallsBlocked

Dépendances : antivirus Microsoft Defender, AMSI

### <a name="use-advanced-protection-against-ransomware"></a>Utiliser une protection avancée contre les rançongiciels

Cette règle fournit une couche supplémentaire de protection contre les rançongiciels. Il utilise à la fois les heuristiques client et cloud pour déterminer si un fichier ressemble à un ransomware. Cette règle ne bloque pas les fichiers qui ont une ou plusieurs des caractéristiques suivantes :

- Le fichier est déjà introuvable dans le cloud Microsoft.
- Le fichier est un fichier signé valide.
- Le fichier est suffisamment répandu pour ne pas être considéré comme un ransomware.

La règle a tendance à errer du côté de la prudence pour empêcher les rançongiciels.

> [!NOTE]
> Vous devez [activer la protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) pour utiliser cette règle.

nom de Intune :`Advanced ransomware protection`

nom de Configuration Manager :`Use advanced protection against ransomware`

GUID : `c1db55ab-c21a-4637-bb3f-a12568109d35`

Type d’action de repérage avancé :

- AsrRansomwareAudited
- AsrRansomwareBlocked

Dépendances : antivirus Microsoft Defender, protection cloud

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment.md)
- [Planifier le déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-plan.md)
- [Tester des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-test.md)
- [Activer des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-implement.md)
- [Utiliser des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)
- [Rapport sur les règles ASR\) de réduction de la \(surface d’attaque](attack-surface-reduction-rules-report.md)
- [Informations de référence sur les règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md)
