---
title: Référence des règles de réduction de la surface d’attaque
description: Répertorie des détails sur les règles de réduction de la surface d’attaque par règle.
keywords: Règles de réduction de la surface d’attaque, ASR, règles asr, hanches, système de prévention des intrusions de l’hôte, règles de protection, règles anti-exploitation, antiexploitation, règles d’exploitation, règles de prévention des infections, Microsoft Defender pour point de terminaison, configurer des règles ASR, description des règles ASR
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar,
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.date: 02/04/2022
ms.openlocfilehash: 64162b83376facddbdeffd1c3079baa49f9d8924
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788015"
---
# <a name="attack-surface-reduction-rules-reference"></a>Référence des règles de réduction de la surface d’attaque

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Cet article fournit des informations sur les règles de réduction des attaques :

- [Versions de système d’exploitation prises en charge](#supported-operating-systems)
- [Systèmes de gestion de configuration pris en charge](#supported-configuration-management-systems)
- [Détails des alertes et des notifications par règle](#per-rule-alert-and-notification-details)
- [Matrice des règles ASR et des GUID](#asr-rules-and-guids-matrix)
- [Modes de règle ASR](#asr-rule-modes)
- [Descriptions par règle](#per-rule-descriptions)
  - Descriptions des règles
  - Noms des règles du système de gestion de la configuration

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge 

Le tableau suivant répertorie les systèmes d’exploitation pris en charge pour les règles actuellement publiées en disponibilité générale. Les règles sont répertoriées par ordre alphabétique dans ce tableau.

> [!Note]
>
> Sauf indication contraire, la version minimale Windows&nbsp; 10 est la version 1709 (RS3, build 16299) ou ultérieure ; la version minimale Windows&nbsp; Server est la version 1809 ou ultérieure.
>
> Les règles de réduction de la surface d’attaque dans Windows&nbsp; Server2012R2&nbsp;&nbsp; et Windows&nbsp; Server2016&nbsp; sont disponibles pour les appareils intégrés à l’aide du package de solution unifié moderne. Pour plus d’informations, consultez [Nouvelles fonctionnalités de la solution unifiée moderne pour Windows Server 2012 R2 et 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

| Nom de la règle|Windows 10 | Windows Server 2019 | &nbsp;Windows Server | <sup>Windows Server 2016 [[1, 2](#fn1)]<sup></sup> | &nbsp;Windows Server 2012 R2 <sup>[[1, 2](#fn1)]<sup></sup> |
|:---|:---:|:---:|:---:|:---:|:---:|
| [Bloquer l’abus de pilotes signés vulnérables exploités](#block-abuse-of-exploited-vulnerable-signed-drivers) | v | v | v <br> version 1803 (canal semi-annuel) ou ultérieure | v | v |
| [Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | Y version 1809 ou ultérieure | v | v | v | v |
| [Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) | v | v | v | v | v |
| [Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | v <br> version 1803 ou ultérieure | v | v | v | v |
| [Bloquer le contenu exécutable à partir du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) | v | v | v | v | v |
| [Empêcher l’exécution de fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste approuvée](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | v <br> version 1803 ou ultérieure | v | v | v | v |
| [Bloquer l’exécution de scripts potentiellement masqués](#block-execution-of-potentially-obfuscated-scripts) | v | v | v | v | v |
| [Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | v | v | v | N | N |
| [Empêcher Office applications de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) | v | v | v | v | v |
| [Empêcher Office applications d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes)  | v | v | v | v | v |
| [Empêcher Office application de communication de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) | v | v | v | v | v |
| [Bloquer la persistance via l’abonnement aux événements WMI](#block-persistence-through-wmi-event-subscription) <br> \*_Exclusions de fichiers et de dossiers non prises en charge._ | v <br> version 1903 (build 18362) ou ultérieure | v | v <br> version 1903 (build 18362) ou ultérieure | N | N |
| [Bloquer les créations de processus provenant des commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | v <br> version 1803 ou ultérieure | v | v | v | v |
| [Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | v | v | v | v | v |
| [Bloquer les appels d’API Win32 à partir de macros Office](#block-win32-api-calls-from-office-macros) | v | v | v | N | N |
| [Utiliser une protection avancée contre les ransomware](#use-advanced-protection-against-ransomware) | v <br> version 1803 ou ultérieure | v | v | v | v |

(<a id="fn1">1</a>) Fait référence à la solution unifiée moderne pour Windows Server 2012 et 2016. Pour plus d’informations, consultez [Intégrer des serveurs Windows au service Defender pour point de terminaison](configure-server-endpoints.md).

(<a id="fn1">2</a>) Pour Windows&nbsp; Server 2016 et Windows&nbsp; Server 2012R2&nbsp;, la version minimale requise de Microsoft Endpoint Configuration Manager est la version 2111.

## <a name="supported-configuration-management-systems"></a>Systèmes de gestion de configuration pris en charge

Les liens vers des informations sur les versions du système de gestion de la configuration référencées dans ce tableau sont répertoriés sous ce tableau.

|Nom de la règle | Intune | Gestionnaire de point de terminaison Microsoft |Microsoft Endpoint Configuration Manager |<sup>stratégie de groupe[[1](#fn1)]<sup></sup> | PowerShell<sup>[[1](#fn1)]<sup></sup>  |
|---|:---:|:---:|:---:|:---:|:---:|
|[Bloquer l’abus de pilotes signés vulnérables exploités](#block-abuse-of-exploited-vulnerable-signed-drivers) | v  | Y MEM OMA-URI |   | v  |  v  |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | v |   |  | v  | v  |
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) | v |   |v <br><br> CB 1710 | v  | v  |
|[Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | v  |   | v <br><br>CB 1802 | v  | v  |
|[Bloquer le contenu exécutable à partir du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) | v |  |v <br><br> CB 1710 | v | v  |
|[Empêcher l’exécution de fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste approuvée](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | v |   | v <br><br> CB 1802 |  v |  v |
|[Bloquer l’exécution de scripts potentiellement masqués](#block-execution-of-potentially-obfuscated-scripts) | v |   |  v  <br><br> CB 1710 | v  | v  |
|[Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | v |   | v <br><br> CB 1710 | v  | v  |
|[Empêcher Office applications de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) | v |  |v <br><br> CB 1710 | v  | v  |
|[Empêcher Office applications d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes) | v |  | v <br><br> CB 1710 | v  | v  |
|[Empêcher Office application de communication de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) | v |  |v <br><br> CB 1710 | v  | v  |
|[Bloquer la persistance via l’abonnement aux événements WMI](#block-persistence-through-wmi-event-subscription) |  |  |  |v   | v  |
|[Bloquer les créations de processus provenant des commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | v |   |   |  v | v  |
|[Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | v |   |v <br><br> CB 1802  | v  | v  |
|[Bloquer les appels d’API Win32 à partir de macros Office](#block-win32-api-calls-from-office-macros) | v |   | v <br><br> CB 1710  | v  |  v |
|[Utiliser une protection avancée contre les ransomware](#use-advanced-protection-against-ransomware) | v |   | v <br><br> CB 1802 | v  | v  |
|  |  |  |  |  |  |

  (<a id="fn1">1</a>) Vous pouvez configurer des règles de réduction de la surface d’attaque sur une base par règle à l’aide du GUID de n’importe quelle règle.

- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)
- [Microsoft Endpoint Manager CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager (SCCM) CB 1710](/configmgr/core/servers/manage/updates) <br>_SCCM est maintenant Microsoft Endpoint Configuration Manager._

## <a name="per-rule-alert-and-notification-details"></a>Détails des alertes et des notifications par règle

Les notifications toast sont générées pour toutes les règles en mode bloc. Les règles d’un autre mode ne génèrent pas de notifications toast

Pour les règles avec l'« état de règle » spécifié :

- Les règles ASR avec \<ASR Rule, Rule State\> des combinaisons sont utilisées pour afficher des alertes (notifications toast) sur Microsoft Defender pour point de terminaison uniquement pour les appareils au niveau du bloc cloud élevé. Les appareils qui n’ont pas un niveau de bloc cloud élevé ne génèrent pas d’alertes pour les combinaisons <règle ASR, état de règle>
- PEPT alertes sont générées pour les règles ASR dans les états spécifiés, mais uniquement pour les appareils au niveau de bloc cloud élevé.

| Nom de la règle : | État de la règle : | Génère des alertes dans PEPT ? <br> (Oui&nbsp;\|&nbsp;Non) | Génère des notifications toast ? <br> (Oui&nbsp;\|&nbsp;Non) |
|---|:---:|:---:|:---:|
|   |   |  _Uniquement pour les appareils au niveau du bloc cloud élevé_ | _En mode bloc uniquement_ |
|[Bloquer l’abus de pilotes signés vulnérables exploités](#block-abuse-of-exploited-vulnerable-signed-drivers) |   | N  | v |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | Bloquer  | v <br> Nécessite un appareil au niveau du bloc cloud élevé  | v <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) |   | N | v |
|[Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) |   | N | v |
|[Bloquer le contenu exécutable à partir du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) |   | v <br> Nécessite un appareil au niveau du bloc cloud élevé | v <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Empêcher l’exécution de fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste approuvée](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) |   | N | v |
|[Bloquer l’exécution de scripts potentiellement masqués](#block-execution-of-potentially-obfuscated-scripts) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Bloquer | v <br> Nécessite un appareil au niveau du bloc cloud élevé  | v <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Empêcher Office applications de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) |   | N | v |
|[Empêcher Office applications d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes)  |   | N | v |
|[Empêcher Office application de communication de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) |  |  N | v |
|[Bloquer la persistance via l’abonnement aux événements WMI](#block-persistence-through-wmi-event-subscription) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Bloquer les créations de processus provenant des commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) |   | N | v |
|[Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Bloquer les appels d’API Win32 à partir de macros Office](#block-win32-api-calls-from-office-macros) |   | N | v |
|[Utiliser une protection avancée contre les ransomware](#use-advanced-protection-against-ransomware) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé |
|   |   |   |   |
  
## <a name="asr-rules-and-guids-matrix"></a>Matrice des règles ASR et des GUID

| Nom de la règle | GUID de règle |
|:-----|:-----|
| Bloquer l’abus de pilotes signés vulnérables exploités | 56a863a9-875e-4185-98a7-b882c64b5ce5 |
| Empêcher Adobe Reader de créer des processus enfants | 7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c |
| Empêcher toutes les applications Office de créer des processus enfants | d4f940ab-401b-4efc-aadc-ad5f3c50688a |
| Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe) | 9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2 |
| Bloquer le contenu exécutable à partir du client de messagerie et de la messagerie web | be9ba2d9-53ea-4cdc-84e5-9b1eeee46550 |
| Empêcher l’exécution de fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste approuvée | 01443614-cd74-433a-b99e-2ecdc07bfc25 |
| Bloquer l’exécution de scripts potentiellement masqués | 5beb7efe-fd9a-4556-801d-275e5ffc04cc |
| Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé | d3e037e1-3eb8-44c8-a917-57927947596d |
| Empêcher Office applications de créer du contenu exécutable | 3b576869-a4ec-4529-8536-b80a7769e899 |
| Empêcher Office applications d’injecter du code dans d’autres processus | 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84 |
| Empêcher Office application de communication de créer des processus enfants | 26190899-1602-49e8-8b27-eb1d0a1ce869 |
| Bloquer la persistance via l’abonnement aux événements WMI <br>* Exclusions de fichiers et de dossiers non prises en charge. | e6db77e5-3df2-4cf1-b95a-636979351e5b |
| Bloquer les créations de processus provenant des commandes PSExec et WMI | d1e49aac-8f56-4280-b9ba-993a6d77406c |
| Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB | b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4 |
| Bloquer les appels d’API Win32 à partir de macros Office | 92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b |
| Utiliser une protection avancée contre les ransomware | c1db55ab-c21a-4637-bb3f-a12568109d35 |

## <a name="asr-rule-modes"></a>Modes de règle ASR

- **Non configuré** ou **désactivé** : il s’agit de l’état dans lequel la règle ASR n’a pas été activée ou a été désactivée. Code de cet état = 0.
- **Bloc** : il s’agit de l’état dans lequel la règle ASR est activée. Le code de cet état est 1.
- **Audit** : il s’agit de l’état dans lequel la règle ASR est évaluée pour son comportement impactif envers l’organisation ou l’environnement dans lequel elle est déployée. Le code de cet état est 2.
- **Avertir** Il s’agit de l’état dans lequel la règle ASR est activée et présente une notification à l’utilisateur final, mais permet à l’utilisateur final de contourner le bloc. Le code de cet état est 6.

_Le mode d’avertissement_ est un type de mode bloc qui alerte les utilisateurs sur les actions potentiellement risquées. Les utilisateurs peuvent choisir de contourner le message d’avertissement de bloc et d’autoriser l’action sous-jacente. Les utilisateurs peuvent sélectionner **OK** pour appliquer le bloc, ou sélectionner l’option de contournement - **Débloquer** - via la notification toast contextuelle de l’utilisateur final générée au moment du bloc. Une fois l’avertissement débloqué, l’opération est autorisée jusqu’à la prochaine fois que le message d’avertissement se produit, auquel cas l’utilisateur final doit réformer l’action.

Si vous cliquez sur le bouton Autoriser, le bloc est supprimé pendant 24 heures. Après 24 heures, l’utilisateur final doit autoriser à nouveau le bloc. Le mode d’avertissement pour les règles ASR est uniquement pris en charge pour les appareils RS5+ (1809+). Si le contournement est affecté aux règles ASR sur les appareils avec des versions antérieures, la règle est en mode bloqué.

Vous pouvez également définir une règle en mode d’avertissement via PowerShell en spécifiant simplement le AttackSurfaceReductionRules_Actions en tant que « Avertir ». Par exemple :

```powershell
-command "& {&'Add-MpPreference' -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Warn"} 
```

## <a name="per-rule-descriptions"></a>Descriptions par règle

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>Bloquer l’abus de pilotes signés vulnérables exploités

Cette règle empêche une application d’écrire un pilote signé vulnérable sur le disque. Dans la nature, les pilotes signés vulnérables peuvent être exploités par des applications \- locales _qui disposent de privilèges suffisants_ \- pour accéder au noyau. Les pilotes signés vulnérables permettent aux attaquants de désactiver ou de contourner les solutions de sécurité, ce qui finit par compromettre le système.

La règle **bloquer l’abus de pilotes signés vulnérables exploités** n’empêche pas le chargement d’un pilote existant sur le système.

> [!NOTE]
>
> Vous pouvez configurer cette règle à l’aide de MEM OMA-URI. Consultez [MEM OMA-URI](enable-attack-surface-reduction.md#mem) pour configurer des règles personnalisées.
>
> Vous pouvez également configurer cette règle à l’aide de [PowerShell](enable-attack-surface-reduction.md#powershell).
>
> Pour qu’un pilote soit examiné, utilisez ce site Web pour [soumettre un pilote à des fins d’analyse](https://www.microsoft.com/en-us/wdsi/driversubmission).

<!--The above link is the 'only link' that exists for having drivers examined. The 'en-us' component is required to make the link work. Any alterations to this link will result in a 404.
-->

nom Intune : `Block abuse of exploited vulnerable signed drivers` (pas encore disponible)

nom Configuration Manager : non encore disponible
  
GUID:  `56a863a9-875e-4185-98a7-b882c64b5ce5`

<!-- Hide this intro with no subsequent list items
Advanced hunting action type:
-->

<!-- 
Dependencies: none provided by engineering
-->

### <a name="block-adobe-reader-from-creating-child-processes"></a>Empêcher Adobe Reader de créer des processus enfants

Cette règle empêche les attaques en empêchant Adobe Reader de créer des processus.

Grâce à l’ingénierie sociale ou les exploits, les programmes malveillants peuvent télécharger et lancer des charges utiles, et sortir d’Adobe Reader. En empêchant les processus enfants d’être générés par Adobe Reader, les programmes malveillants qui tentent de l’utiliser comme vecteur sont empêchés de se propager.

nom Intune :`Process creation from Adobe Reader (beta)`

nom Configuration Manager : non encore disponible

GUID : `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

Type d’action de chasse avancé :

- AsrAdobeReaderChildProcessAudited
- AsrAdobeReaderChildProcessBlocked

Dépendances : MDAV

### <a name="block-all-office-applications-from-creating-child-processes"></a>Empêcher toutes les applications Office de créer des processus enfants

Cette règle empêche Office applications de créer des processus enfants. Office applications incluent Word, Excel, PowerPoint, OneNote et Access.

La création de processus enfants malveillants est une stratégie de programmes malveillants courante. Les programmes malveillants qui abusent Office en tant que vecteur exécutent souvent des macros VBA et exploitent le code pour télécharger et tenter d’exécuter davantage de charges utiles. Toutefois, certaines applications métier légitimes peuvent également générer des processus enfants à des fins bénignes; par exemple générer une invite de commandes ou utiliser PowerShell pour configurer les paramètres du Registre.

nom Intune :`Office apps launching child processes`

nom Configuration Manager :`Block Office application from creating child processes`

GUID : `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

Type d’action de chasse avancé :

- AsrOfficeChildProcessAudited
- AsrOfficeChildProcessBlocked

Dépendances : MDAV

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>Bloquer le vol d’informations d’identification dans le sous-système de l’autorité de sécurité locale Windows

Cette règle permet d’éviter le vol d’informations d’identification en verrouillant le service de sous-système de l’autorité de sécurité locale (LSASS).

LSASS authentifie les utilisateurs qui se connectent sur un ordinateur Windows. Microsoft Defender Credential Guard dans Windows empêche normalement les tentatives d’extraction d’informations d’identification à partir de LSASS. Toutefois, certaines organisations ne peuvent pas activer Credential Guard sur tous leurs ordinateurs en raison de problèmes de compatibilité avec des pilotes de carte à puce personnalisés ou d’autres programmes qui se chargent dans l’autorité de sécurité locale (LSA). Dans ces cas, les attaquants peuvent utiliser des outils de piratage tels que Mimikatz pour gratter des mots de passe en clair et des hachages NTLM à partir de LSASS.

> [!NOTE]
> Dans certaines applications, le code énumère tous les processus en cours d’exécution et tente de les ouvrir avec des autorisations exhaustives. Cette règle refuse l’action d’ouverture du processus de l’application et enregistre les détails dans le journal des événements de sécurité. Cette règle peut générer beaucoup de bruit. Si vous avez une application qui énumère simplement LSASS, mais n’a aucun impact réel sur les fonctionnalités, il n’est pas nécessaire de l’ajouter à la liste d’exclusions. En soi, cette entrée de journal des événements n’indique pas nécessairement une menace malveillante.
  
> [!IMPORTANT]
> L’état par défaut de la règle de réduction de la surface d’attaque (ASR) « Bloquer le vol d’informations d’identification du sous-système d’autorité de sécurité locale Windows (lsass.exe) » passe de **Non configuré** à **Configuré** et le mode par défaut défini sur **Bloquer**. Toutes les autres règles ASR resteront dans leur état par défaut : **Non configuré.** Une logique de filtrage supplémentaire a déjà été incorporée dans la règle pour réduire les notifications de l’utilisateur final. Les clients peuvent configurer la règle pour **les modes Audit**, **Avertir** ou **Désactivé** , ce qui remplacera le mode par défaut. Les fonctionnalités de cette règle sont les mêmes, que la règle soit configurée en mode on-by-default ou si vous activez manuellement le mode Bloc.

nom Intune :`Flag credential stealing from the Windows local security authority subsystem`

nom Configuration Manager :`Block credential stealing from the Windows local security authority subsystem`

GUID : `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

Type d’action de chasse avancé :

- AsrLsassCredentialTheftAudited
- AsrLsassCredentialTheftBlocked

Dépendances : MDAV

### <a name="block-executable-content-from-email-client-and-webmail"></a>Bloquer le contenu exécutable à partir du client de messagerie et de la messagerie web

Cette règle empêche le lancement des types de fichiers suivants à partir de l’e-mail ouvert dans l’application Microsoft Outlook, ou Outlook.com et d’autres fournisseurs de messagerie web populaires :

- Fichiers exécutables (tels que .exe, .dll ou .scr)
- Fichiers de script (tels qu’un fichier .ps PowerShell, Visual Basic .vbs ou JavaScript .js)

nom Intune :`Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

Microsoft Endpoint Manager nom :`Block executable content from email client and webmail`

GUID : `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

Type d’action de chasse avancé :

- AsrExecutableEmailContentAudited
- AsrExecutableEmailContentBlocked

Dépendances : MDAV

> [!NOTE]
> La règle **Bloquer le contenu exécutable du client de messagerie et de la messagerie web** contient les descriptions alternatives suivantes, en fonction de l’application que vous utilisez :
>
> - Intune (profils de configuration) : exécution de contenu exécutable (exe, dll, ps, js, vbs, etc.) supprimé de l’e-mail (webmail/client de messagerie) (aucune exception).
> - Endpoint Manager : bloquer le téléchargement de contenu exécutable à partir de clients de messagerie et de messagerie web.
> - stratégie de groupe : bloquer le contenu exécutable à partir du client de messagerie et de la messagerie web.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>Empêcher l’exécution de fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste approuvée

Cette règle empêche le lancement de fichiers exécutables, tels que .exe, .dll ou .scr. Par conséquent, le lancement de fichiers exécutables non approuvés ou inconnus peut être risqué, car il peut ne pas être clair initialement si les fichiers sont malveillants.

> [!IMPORTANT]
> Vous devez [activer la protection fournie par le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) pour utiliser cette règle.
>
> La règle **empêche l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste approuvée** avec GUID `01443614-cd74-433a-b99e-2ecdc07bfc25` appartenant à Microsoft et n’est pas spécifié par les administrateurs. Cette règle utilise la protection fournie par le cloud pour mettre à jour régulièrement sa liste approuvée.
>
> Vous pouvez spécifier des fichiers ou des dossiers individuels (à l’aide de chemins d’accès aux dossiers ou de noms de ressources complets), mais vous ne pouvez pas spécifier à quelles règles ou exclusions s’appliquent.

nom Intune :`Executables that don't meet a prevalence, age, or trusted list criteria`

nom Configuration Manager :`Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID : `01443614-cd74-433a-b99e-2ecdc07bfc25`

Type d’action de chasse avancé :

- AsrUntrustedExecutableAudited
- AsrUntrustedExecutableBlocked

Dépendances : MDAV, Protection cloud

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>Bloquer l’exécution de scripts potentiellement masqués

Cette règle détecte les propriétés suspectes dans un script masqué.

L’obfuscation de script est une technique courante que les auteurs de programmes malveillants et les applications légitimes utilisent pour masquer la propriété intellectuelle ou réduire les temps de chargement des scripts. Les auteurs de programmes malveillants utilisent également l’obfuscation pour rendre le code malveillant plus difficile à lire, ce qui empêche un examen approfondi par les humains et les logiciels de sécurité.

nom Intune :`Obfuscated js/vbs/ps/macro code`

nom Configuration Manager :`Block execution of potentially obfuscated scripts`

GUID : `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

Type d’action de chasse avancé :

- AsrObfuscatedScriptAudited
- AsrObfuscatedScriptBlocked

Dépendances : MDAV, AMSI

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé

Cette règle empêche les scripts de lancer du contenu téléchargé potentiellement malveillant. Les programmes malveillants écrits en JavaScript ou VBScript jouent souvent le rôle de téléchargeur pour extraire et lancer d’autres programmes malveillants à partir d’Internet.

Bien qu’elles ne soient pas courantes, les applications métier utilisent parfois des scripts pour télécharger et lancer des programmes d’installation.

nom Intune :`js/vbs executing payload downloaded from Internet (no exceptions)`

nom Configuration Manager :`Block JavaScript or VBScript from launching downloaded executable content`

GUID : `d3e037e1-3eb8-44c8-a917-57927947596d`

Type d’action de chasse avancé :

- AsrScriptExecutableDownloadAudited
- AsrScriptExecutableDownloadBlocked

Dépendances : MDAV, AMSI

### <a name="block-office-applications-from-creating-executable-content"></a>Empêcher Office applications de créer du contenu exécutable

Cette règle empêche Office applications, notamment Word, Excel et PowerPoint, de créer du contenu exécutable potentiellement malveillant, en bloquant l’écriture de code malveillant sur le disque.

Les programmes malveillants qui abusent Office en tant que vecteur peuvent tenter de se décomposer en Office et d’enregistrer des composants malveillants sur le disque. Ces composants malveillants survivraient au redémarrage d’un ordinateur et seraient conservés sur le système. Par conséquent, cette règle se défend contre une technique de persistance commune.

nom Intune :`Office apps/macros creating executable content`

Nom SCCM : `Block Office applications from creating executable content`

GUID : `3b576869-a4ec-4529-8536-b80a7769e899`

Type d’action de chasse avancé :

- AsrExecutableOfficeContentAudited
- AsrExecutableOfficeContentBlocked

Dépendances : MDAV, RPC

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>Empêcher Office applications d’injecter du code dans d’autres processus

Cette règle bloque les tentatives d’injection de code de Office applications vers d’autres processus.

Les attaquants peuvent tenter d’utiliser Office applications pour migrer du code malveillant vers d’autres processus via l’injection de code, afin que le code puisse se masquer comme un processus propre.

Il n’existe aucun objectif commercial légitime connu pour l’utilisation de l’injection de code.

Cette règle s’applique à Word, Excel et PowerPoint.

nom Intune :`Office apps injecting code into other processes (no exceptions)`

nom Configuration Manager :`Block Office applications from injecting code into other processes`

GUID : `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

Type d’action de chasse avancé :

- AsrOfficeProcessInjectionAudited
- AsrOfficeProcessInjectionBlocked

Dépendances : MDAV

### <a name="block-office-communication-application-from-creating-child-processes"></a>Empêcher Office application de communication de créer des processus enfants

Cette règle empêche Outlook de créer des processus enfants, tout en autorisant des fonctions Outlook légitimes.

Cette règle protège contre les attaques d’ingénierie sociale et empêche l’exploitation du code d’abus de vulnérabilités dans Outlook. Il protège également contre [Outlook règles et les attaques de formulaires](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) que les attaquants peuvent utiliser lorsque les informations d’identification d’un utilisateur sont compromises.

> [!NOTE]
> Cette règle bloque les conseils de stratégie DLP et les info-bulles dans Outlook. Cette règle s’applique uniquement à Outlook et Outlook.com.

nom Intune :`Process creation from Office communication products (beta)`

nom Configuration Manager : Non disponible

GUID : `26190899-1602-49e8-8b27-eb1d0a1ce869`

Type d’action de chasse avancé :

- AsrOfficeCommAppChildProcessAudited
- AsrOfficeCommAppChildProcessBlocked

Dépendances : MDAV

### <a name="block-persistence-through-wmi-event-subscription"></a>Bloquer la persistance via l’abonnement aux événements WMI

Cette règle empêche les programmes malveillants d’utiliser WMI à mauvais escient pour obtenir une persistance sur un appareil.

> [!IMPORTANT]
> Les exclusions de fichiers et de dossiers ne s’appliquent pas à cette règle de réduction de la surface d’attaque.

Les menaces sans fichier emploient diverses tactiques pour rester cachées, éviter d’être vues dans le système de fichiers et obtenir un contrôle d’exécution périodique. Certaines menaces peuvent utiliser à mauvais escient le dépôt WMI et le modèle d’événement pour rester cachées.

nom Intune : Non disponible

nom Configuration Manager : Non disponible

GUID : `e6db77e5-3df2-4cf1-b95a-636979351e5b`

Type d’action de chasse avancé :

- AsrPersistenceThroughWmiAudited
- AsrPersistenceThroughWmiBlocked

Dépendances : MDAV, RPC

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>Bloquer les créations de processus provenant des commandes PSExec et WMI

Cette règle empêche l’exécution des processus [créés via PsExec](/sysinternals/downloads/psexec) et [WMI](/windows/win32/wmisdk/about-wmi) . PsExec et WMI peuvent exécuter du code à distance. Il existe donc un risque que des programmes malveillants abusent de cette fonctionnalité à des fins de commande et de contrôle, ou pour propager une infection dans le réseau d’une organisation.

> [!WARNING]
> Utilisez cette règle uniquement si vous gérez vos appareils avec [Intune](/intune) ou une autre solution GPM. Cette règle est incompatible avec la gestion via [Microsoft Endpoint Configuration Manager](/configmgr), car cette règle bloque les commandes WMI utilisées par le client Configuration Manager pour fonctionner correctement.

nom Intune :`Process creation from PSExec and WMI commands`

nom Configuration Manager : non applicable

GUID : `d1e49aac-8f56-4280-b9ba-993a6d77406c`

Type d’action de chasse avancé :

- AsrPsexecWmiChildProcessAudited
- AsrPsexecWmiChildProcessBlocked

Dépendances : MDAV

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB

Avec cette règle, les administrateurs peuvent empêcher l’exécution de fichiers exécutables non signés ou non approuvés à partir de lecteurs amovibles USB, y compris les cartes SD. Les types de fichiers bloqués incluent des fichiers exécutables (tels que .exe, .dll ou .scr)

nom Intune :`Untrusted and unsigned processes that run from USB`

nom Configuration Manager :`Block untrusted and unsigned processes that run from USB`

GUID : `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

Type d’action de chasse avancé :

- AsrUntrustedUsbProcessAudited
- AsrUntrustedUsbProcessBlocked

Dépendances : MDAV

### <a name="block-win32-api-calls-from-office-macros"></a>Bloquer les appels d’API Win32 à partir de macros Office

Cette règle empêche les macros VBA d’appeler des API Win32.

Office VBA active les appels d’API Win32. Les programmes malveillants peuvent abuser de cette fonctionnalité, comme [appeler des API Win32 pour lancer un code shell malveillant](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) sans écrire quoi que ce soit directement sur le disque. La plupart des organisations ne s’appuient pas sur la possibilité d’appeler des API Win32 dans leur fonctionnement quotidien, même si elles utilisent des macros d’autres façons.

Systèmes d’exploitation pris en charge :          

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

nom Intune :`Win32 imports from Office macro code`

nom Configuration Manager :`Block Win32 API calls from Office macros`

GUID : `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

Type d’action de chasse avancé :

- AsrOfficeMacroWin32ApiCallsAudited
- AsrOfficeMacroWin32ApiCallsBlocked

Dépendances : MDAV, AMSI

### <a name="use-advanced-protection-against-ransomware"></a>Utiliser une protection avancée contre les ransomware

Cette règle fournit une couche supplémentaire de protection contre les ransomware. Il utilise des heuristiques clientes et cloud pour déterminer si un fichier ressemble à un ransomware. Cette règle ne bloque pas les fichiers qui ont une ou plusieurs des caractéristiques suivantes :

- Le fichier n’est pas partageable dans le cloud Microsoft.
- Le fichier est un fichier signé valide.
- Le fichier est suffisamment répandu pour ne pas être considéré comme un ransomware.

La règle tend à errer du côté de la prudence pour empêcher les ransomware.

> [!NOTE]
> Vous devez [activer la protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) pour utiliser cette règle.

nom Intune :`Advanced ransomware protection`

nom Configuration Manager :`Use advanced protection against ransomware`

GUID : `c1db55ab-c21a-4637-bb3f-a12568109d35`

Type d’action de chasse avancé :

- AsrRansomwareAudited
- AsrRansomwareBlocked

Dépendances : MDAV, Protection cloud
