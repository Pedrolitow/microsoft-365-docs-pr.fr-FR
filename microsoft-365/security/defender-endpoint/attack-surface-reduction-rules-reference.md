---
title: Référence des règles de réduction de la surface d’attaque
description: Répertorie les détails sur les règles de réduction de la surface d’attaque par règle.
keywords: Règles de réduction de la surface d’attaque, règles de réduction de la surface d’attaque, règles asr, système de prévention des intrusions hôtes, règles de protection, règles anti-attaque, règles d’attaque, règles de prévention des infections, Microsoft Defender pour point de terminaison, configurer des règles de réduction de la surface d’attaque, description des règles de réduction de la surface d’attaque
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
ms.openlocfilehash: 377ae12eb2436dcafe84e521fd4b35d712283e74
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64637981"
---
# <a name="attack-surface-reduction-rules-reference"></a>Référence des règles de réduction de la surface d’attaque

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Cet article fournit des informations sur les règles de réduction des attaques :

- [Versions de système d’exploitation prise en charge](#supported-operating-systems)
- [Systèmes de gestion de la configuration pris en charge](#supported-configuration-management-systems)
- [Informations sur les alertes et les notifications par règle](#per-rule-alert-and-notification-details)
- [Matrice des RÈGLES ET DEST ET DES GRAPHIQUES](#asr-rules-and-guids-matrix)
- [Modes de règle ASR](#asr-rule-modes)
- [Descriptions par règle](#per-rule-descriptions)
  - Descriptions des règles
  - Noms de règles du système de gestion de la configuration

## <a name="public-preview-supported-operating-systems"></a>Prévisualisation publique : systèmes d’exploitation pris en charge

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Le tableau suivant répertorie les systèmes d’exploitation pris en charge pour les règles de réduction de la surface d’attaque qui sont actuellement des produits de préparation. Les règles sont répertoriées par ordre alphabétique. Sauf indication contraire, la version Windows&nbsp; 10 minimale est la version 1709 (RS3, build 16299) ou ultérieure ; la version minimale de Windows&nbsp; Server est la version 1809 ou ultérieure.

> [!NOTE]
> Les règles de réduction de la surface d’attaque dans Windows&nbsp; Server2012R2&nbsp;&nbsp; et Windows&nbsp; Server2016&nbsp; sont disponibles pour les appareils intégrés à l’aide du package de solution unifiée moderne. Pour plus d’informations, voir Nouvelle fonctionnalité dans [la solution unifiée moderne pour Windows Server 2012 R2 et 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).
>

| Nom de la règle | &nbsp;Windows Server 2016 <sup>[[1](#fn1)]<sup></sup> | &nbsp;Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup> |
|---|:---:|:---:|
|[Bloquer l’utilisation abusive des pilotes signés vulnérables exploités](#block-abuse-of-exploited-vulnerable-signed-drivers) | v | v |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | v | v |
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) | v | v |
|[Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | v | v |
|[Bloquer le contenu exécutable du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) | v | v |
|[Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | v | v |
|[Bloquer l’exécution de scripts potentiellement obscurcis](#block-execution-of-potentially-obfuscated-scripts) | v | v |
|[Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | N | N |
|[Empêcher Office applications de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) | v | v |
|[Empêcher Office applications d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes)  | v | v |
|[Empêcher Office application de communication de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) | v | v |
|[Bloquer la persistance via un abonnement à des événements](#block-persistence-through-wmi-event-subscription) \* WMI _Exclusions de fichiers et de dossiers non pris en charge._ | N | N |
|[Bloquer les créations de processus provenant de commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | v | v |
|[Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | v | v |
|[Bloquer les appels d’API Win32 à Office macros](#block-win32-api-calls-from-office-macros) | N | N |
|[Utiliser la protection avancée contre les ransomware](#use-advanced-protection-against-ransomware) | v | v |
|  |  |  |

(<a id="fn1">1</a>) Fait référence à la solution moderne et unifiée pour Windows Server 2012 et 2016. Pour plus d’informations, [voir Onboard Windows Servers to the Defender for Endpoint service](configure-server-endpoints.md).

_Fin de la prévisualisation publique : systèmes d’exploitation pris en charge_

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge 

Le tableau suivant répertorie les systèmes d’exploitation pris en charge pour les règles actuellement publiées à la disponibilité générale. Les règles sont répertoriées par ordre alphabétique.

> [!Note]
>
> Sauf indication contraire, la version Windows&nbsp; 10 minimale est la version 1709 (RS3, build 16299) ou ultérieure ; la version minimale de Windows&nbsp; Server est la version 1809 ou ultérieure.
>

|Nom de la règle|&nbsp;Windows 10|&nbsp;Windows Server 2019|&nbsp;Windows Server|
|---|:---:|:---:|:---:|
|[Bloquer l’utilisation abusive des pilotes signés vulnérables exploités](#block-abuse-of-exploited-vulnerable-signed-drivers) | v | v | v <br><br> version 1803 (canal semi-annuel) ou version ultérieure |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | Y version 1809 ou ultérieure | v | v  <br><br> |
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) | v | v | v <br><br> |
|[Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y version 1803 ou ultérieure | v <br><br> | v <br><br> |
|[Bloquer le contenu exécutable du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) | v | v <br><br> | v <br><br> |
|[Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y version 1803 ou ultérieure | v <br><br> | v <br><br> |
|[Bloquer l’exécution de scripts potentiellement obscurcis](#block-execution-of-potentially-obfuscated-scripts) | v | v <br><br> | v <br><br> |
|[Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | v | v <br><br> | v <br><br> |
|[Empêcher Office applications de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) | v | v <br><br> | v <br><br> |
|[Empêcher Office applications d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes)  | v | v <br><br> | v <br><br> |
|[Empêcher Office application de communication de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) | v | v <br><br> | v <br><br> |
|[Bloquer la persistance via un abonnement à des événements WMI](#block-persistence-through-wmi-event-subscription) <br><br> \*_Exclusions de fichiers et de dossiers non pris en charge._ | Y version 1903 (build 18362) ou version ultérieure| v | v <br><br> version 1903 (build 18362) ou version ultérieure |
|[Bloquer les créations de processus provenant de commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y version 1803 ou ultérieure | v <br><br> | v <br><br>  |
|[Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | v | v <br><br> | v <br><br> |
|[Bloquer les appels d’API Win32 à Office macros](#block-win32-api-calls-from-office-macros) | v | v <br><br> | v <br><br> |
|[Utiliser la protection avancée contre les ransomware](#use-advanced-protection-against-ransomware) | Y version 1803 ou ultérieure | v <br><br> | v <br><br> |
|  |  |  |  |

## <a name="supported-configuration-management-systems"></a>Systèmes de gestion de la configuration pris en charge

Les liens vers des informations sur les versions du système de gestion de la configuration référencés dans ce tableau sont répertoriés sous ce tableau.

|Nom de la règle | Intune | Gestionnaire de point de terminaison Microsoft |Microsoft Endpoint Configuration Manager |<sup>stratégie de groupe[[1](#fn1)]<sup></sup> | PowerShell<sup>[[1](#fn1)]<sup></sup>  |
|---|:---:|:---:|:---:|:---:|:---:|
|[Bloquer l’utilisation abusive des pilotes signés vulnérables exploités](#block-abuse-of-exploited-vulnerable-signed-drivers) | v  | Y MEM OMA-URI |   | v  |  v  |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | v |   |  | v  | v  |
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) | v |   |v <br><br> CB 1710 | v  | v  |
|[Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | v  |   | v <br><br>CB 1802 | v  | v  |
|[Bloquer le contenu exécutable du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) | v |  |v <br><br> CB 1710 | v | v  |
|[Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | v |   | v <br><br> CB 1802 |  v |  v |
|[Bloquer l’exécution de scripts potentiellement obscurcis](#block-execution-of-potentially-obfuscated-scripts) | v |   |  v  <br><br> CB 1710 | v  | v  |
|[Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | v |   | v <br><br> CB 1710 | v  | v  |
|[Empêcher Office applications de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) | v |  |v <br><br> CB 1710 | v  | v  |
|[Empêcher Office applications d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes) | v |  | v <br><br> CB 1710 | v  | v  |
|[Empêcher Office application de communication de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) | v |  |v <br><br> CB 1710 | v  | v  |
|[Bloquer la persistance via un abonnement à des événements WMI](#block-persistence-through-wmi-event-subscription) |  |  |  |v   | v  |
|[Bloquer les créations de processus provenant de commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | v |   |   |  v | v  |
|[Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | v |   |v <br><br> CB 1802  | v  | v  |
|[Bloquer les appels d’API Win32 à Office macros](#block-win32-api-calls-from-office-macros) | v |   | v <br><br> CB 1710  | v  |  v |
|[Utiliser la protection avancée contre les ransomware](#use-advanced-protection-against-ransomware) | v |   | v <br><br> CB 1802 | v  | v  |
|  |  |  |  |  |  |

  (<a id="fn1">1</a>) Vous pouvez configurer des règles de réduction de la surface d’attaque pour chaque règle à l’aide du GUID de n’importe quelle règle.

- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)
- [Microsoft Endpoint Manager CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager CB 1710 (SCCM)](/configmgr/core/servers/manage/updates) <br>_SCCM est désormais Microsoft Endpoint Configuration Manager._

## <a name="per-rule-alert-and-notification-details"></a>Informations sur l’alerte et la notification par règle

Les notifications toast sont générées pour toutes les règles en mode blocage. Les règles dans n’importe quel autre mode ne génèreront pas de notifications toast

Pour les règles dont l'« état de règle » est spécifié :

- Les règles asr avec \<ASR Rule, Rule State\> combinaisons sont utilisées pour faire surface des alertes (notifications toast) sur Microsoft Defender pour point de terminaison uniquement pour les appareils au niveau du bloc cloud élevé. Les appareils qui ne sont pas au niveau de blocage élevé du cloud ne génèreront pas d’alertes <règle asr, état de règle> combinaisons
- PEPT alertes sont générées pour les règles de asr dans les états spécifiés, mais uniquement pour les appareils au niveau de blocage cloud élevé.

| Nom de la règle : | État de la règle : | Génère des alertes dans PEPT ? <br> (Oui)&nbsp;\|&nbsp;Non) | Génère des notifications toast ? <br> (Oui)&nbsp;\|&nbsp;Non) |
|---|:---:|:---:|:---:|
|   |   |  _Uniquement pour les appareils au niveau du bloc cloud élevé_ | _En mode Blocage uniquement_ |
|[Bloquer l’utilisation abusive des pilotes signés vulnérables exploités](#block-abuse-of-exploited-vulnerable-signed-drivers) |   | N  | v |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | Bloquer  | v <br> Nécessite un appareil au niveau du bloc cloud élevé  | v <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) |   | N | v |
|[Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) |   | N | v |
|[Bloquer le contenu exécutable du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) |   | v <br> Nécessite un appareil au niveau du bloc cloud élevé | v <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) |   | N | v |
|[Bloquer l’exécution de scripts potentiellement obscurcis](#block-execution-of-potentially-obfuscated-scripts) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Bloquer | v <br> Nécessite un appareil au niveau du bloc cloud élevé  | v <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Empêcher Office applications de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) |   | N | v |
|[Empêcher Office applications d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes)  |   | N | v |
|[Empêcher Office application de communication de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) |  |  N | v |
|[Bloquer la persistance via un abonnement à des événements WMI](#block-persistence-through-wmi-event-subscription) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Bloquer les créations de processus provenant de commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) |   | N | v |
|[Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé |
|[Bloquer les appels d’API Win32 à Office macros](#block-win32-api-calls-from-office-macros) |   | N | v |
|[Utiliser la protection avancée contre les ransomware](#use-advanced-protection-against-ransomware) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé  | N \| Y <br> Nécessite un appareil au niveau du bloc cloud élevé |
|   |   |   |   |
  
## <a name="asr-rules-and-guids-matrix"></a>Matrice des RÈGLES ET DEST ET DES GRAPHIQUES

| Nom de la règle | GUID de règle |
|:-----|:-----|
| Bloquer l’utilisation abusive des pilotes signés vulnérables exploités | 56a863a9-875e-4185-98a7-b882c64b5ce5 |
| Empêcher Adobe Reader de créer des processus enfants | 7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c |
| Empêcher toutes les applications Office de créer des processus enfants | d4f940ab-401b-4efc-aadc-ad5f3c50688a |
| Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe) | 9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2 |
| Bloquer le contenu exécutable du client de messagerie et de la messagerie web | be9ba2d9-53ea-4cdc-84e5-9b1eeee46550 |
| Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance | 01443614-cd74-433a-b99e-2ecdc07bfc25 |
| Bloquer l’exécution de scripts potentiellement obscurcis | 5beb7efe-fd9a-4556-801d-275e5ffc04cc |
| Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé | d3e037e1-3eb8-44c8-a917-57927947596d |
| Empêcher Office applications de créer du contenu exécutable | 3b576869-a4ec-4529-8536-b80a7769e899 |
| Empêcher Office applications d’injecter du code dans d’autres processus | 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84 |
| Empêcher Office application de communication de créer des processus enfants | 26190899-1602-49e8-8b27-eb1d0a1ce869 |
| Bloquer la persistance via un abonnement à des événements WMI <br>* Les exclusions de fichiers et de dossiers ne sont pas pris en charge. | e6db77e5-3df2-4cf1-b95a-636979351e5b |
| Bloquer les créations de processus provenant de commandes PSExec et WMI | d1e49aac-8f56-4280-b9ba-993a6d77406c |
| Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB | b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4 |
| Bloquer les appels d’API Win32 à Office macros | 92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b |
| Utiliser la protection avancée contre les ransomware | c1db55ab-c21a-4637-bb3f-a12568109d35 |

## <a name="asr-rule-modes"></a>Modes de règle ASR

- **Non configurée ou** **désactivée** : il s’agit de l’état dans lequel la règle asr n’a pas été activée ou désactivée. Code de cet état = 0.
- **Bloc** : il s’agit de l’état dans lequel la règle asr est activée. Le code de cet état est 1.
- **Audit** : il s’agit de l’état dans lequel la règle de astéreur est évaluée pour son comportement d’impact sur l’organisation ou l’environnement dans lequel elle est déployée. Le code de cet état est 2.
- **Avertir** Il s’agit de l’état dans lequel la règle asr est activée et présente une notification à l’utilisateur final, mais permet à l’utilisateur final de contourner le blocage. Le code de cet état est 6.

_Le mode Avertissement_ est un type de blocage qui avertit les utilisateurs des actions potentiellement risquées. Les utilisateurs peuvent choisir d’ignorer le message d’avertissement de blocage et d’autoriser l’action sous-jacente. Les utilisateurs peuvent sélectionner **OK** pour appliquer le bloc, ou sélectionner l’option de contournement **- Débloquer** - via la notification toast de l’utilisateur final générée au moment du blocage. Une fois l’avertissement débloqué, l’opération est autorisée jusqu’au prochain message d’avertissement, auquel cas l’utilisateur final devra reformer l’action.

Si vous cliquez sur le bouton autoriser, le bloc sera supprimé pendant 24 heures. Au bout de 24 heures, l’utilisateur final doit autoriser à nouveau le blocage. Le mode d’avertissement pour les règles de récupération automatique est uniquement pris en charge pour les appareils RS5+ (1809+). Si le contournement est affecté à des règles de récupération automatique sur des appareils avec des versions antérieures, la règle sera en mode bloqué.

Vous pouvez également définir une règle en mode d’avertissement via PowerShell en spécifiant simplement l’AttackSurfaceReductionRules_Actions comme « Avertir ». Par exemple :

```powershell
-command "& {&'Add-MpPreference' -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Warn"} 
```

## <a name="per-rule-descriptions"></a>Descriptions par règle

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>Bloquer l’utilisation abusive des pilotes signés vulnérables exploités

Cette règle empêche une application d’écrire un pilote signé vulnérable sur le disque. Les pilotes signés in-the-wild et vulnérables peuvent être exploités par des applications \- locales qui ont des _privilèges suffisants_ \- pour accéder au noyau. Les pilotes signés vulnérables permettent aux attaquants de désactiver ou de contourner les solutions de sécurité, ce qui peut conduire à une compromission du système.

La **règle bloquer l’utilisation abusive des pilotes signés vulnérables exploités** ne bloque pas le chargement d’un pilote déjà existant sur le système.

> [!NOTE]
>
> Vous pouvez configurer cette règle à l’aide de l’OMA-URI MEM. Voir [MEM OMA-URI pour](enable-attack-surface-reduction.md#mem) configurer des règles personnalisées.
>
> Vous pouvez également configurer cette règle à l’aide [de PowerShell](enable-attack-surface-reduction.md#powershell).
>
> Pour examiner un pilote, utilisez ce site Web pour soumettre [un pilote pour analyse](https://www.microsoft.com/en-us/wdsi/driversubmission).

<!--The above link is the 'only link' that exists for having drivers examined. The 'en-us' component is required to make the link work. Any alterations to this link will result in a 404.
-->

Intune nom : `Block abuse of exploited vulnerable signed drivers` (pas encore disponible)

Configuration Manager : pas encore disponible
  
GUID :  `56a863a9-875e-4185-98a7-b882c64b5ce5`

<!-- Hide this intro with no subsequent list items
Advanced hunting action type:
-->

<!-- 
Dependencies: none provided by engineering
-->

### <a name="block-adobe-reader-from-creating-child-processes"></a>Empêcher Adobe Reader de créer des processus enfants

Cette règle empêche les attaques en empêchant Adobe Reader de créer des processus.

Grâce à l’ingénierie sociale ou aux attaques, les programmes malveillants peuvent télécharger et lancer des charges utiles, et sortir d’Adobe Reader. En bloquant la production de processus enfants par Adobe Reader, les programmes malveillants qui tentent de l’utiliser comme vecteur sont empêchés de se propager.

Intune nom :`Process creation from Adobe Reader (beta)`

Configuration Manager : pas encore disponible

GUID : `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

Type d’action de recherche avancée :

- AsrAdobeReaderChildProcessAudited
- AsrAdobeReaderChildProcessBlocked

Dépendances : MDAV

### <a name="block-all-office-applications-from-creating-child-processes"></a>Empêcher toutes les applications Office de créer des processus enfants

Cette règle empêche Office applications de créer des processus enfants. Office applications incluent Word, Excel, PowerPoint, OneNote et Access.

La création de processus enfants malveillants est une stratégie anti-programme malveillant courante. Les programmes malveillants qui utilisent Office comme vecteur exécutent souvent des macros VBA et exploitent du code pour télécharger et essayer d’exécuter davantage de charges utiles. Toutefois, certaines applications métier légitimes peuvent également générer des processus enfants à des fins médicales ; par exemple, la création d’une invite de commandes ou l’utilisation de PowerShell pour configurer les paramètres de Registre.

Intune nom :`Office apps launching child processes`

Configuration Manager nom :`Block Office application from creating child processes`

GUID : `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

Type d’action de recherche avancée :

- AsrOfficeChildProcessAudited
- AsrOfficeChildProcessBlocked

Dépendances : MDAV

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>Bloquer le vol d’informations d’identification Windows sous-système de l’autorité de sécurité locale

Cette règle empêche le vol d’informations d’identification en verrouilleant le service LSASS (Local Security Authority Subsystem Service).

LSASS authentifier les utilisateurs qui se connectent sur Windows ordinateur. Microsoft Defender Credential Guard dans Windows normalement les tentatives d’extraction des informations d’identification de LSASS. Toutefois, certaines organisations ne peuvent pas activer Credential Guard sur tous leurs ordinateurs en raison de problèmes de compatibilité avec les pilotes de carte à puce personnalisés ou d’autres programmes chargés dans l’autorité de sécurité locale (LSA). Dans ce cas, les attaquants peuvent utiliser des outils de piratage tels que Mimikatz pour supprimer des mots de passe en texte clair et des hages NTLM à partir de LSASS.

> [!NOTE]
> Dans certaines applications, le code éumène tous les processus en cours d’exécution et tente de les ouvrir avec des autorisations exhaustives. Cette règle refuse l’action d’ouverture du processus de l’application et enregistre les détails dans le journal des événements de sécurité. Cette règle peut générer beaucoup de bruit. Si vous disposez d’une application qui é énumére simplement LSASS, mais n’a aucun impact réel sur les fonctionnalités, il n’est pas nécessaire de l’ajouter à la liste d’exclusions. En soi, cette entrée du journal des événements n’indique pas nécessairement une menace malveillante.
  
> [!IMPORTANT]
> L’état par défaut de la règle de réduction de la surface d’attaque (ASR) « Bloquer le vol d’informations d’identification du sous-système de l’autorité de  sécurité locale (lsass.exe) Windows » change de Non configuré à Configuré et le mode par défaut est configuré sur **Bloquer**. Toutes les autres règles de la asr. restent dans leur état par défaut : **Non configuré.** Une logique de filtrage supplémentaire a déjà été incorporée dans la règle pour réduire les notifications des utilisateurs finaux. Les clients peuvent configurer la règle sur **les modes Audit**,  **Avertir** ou Désactivé, ce qui remplacera le mode par défaut. La fonctionnalité de cette règle est la même, que la règle soit configurée en mode par défaut ou si vous activez le mode Blocage manuellement.  

Intune nom :`Flag credential stealing from the Windows local security authority subsystem`

Configuration Manager nom :`Block credential stealing from the Windows local security authority subsystem`

GUID : `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

Type d’action de recherche avancée :

- AsrLsassCredentialTheftAudited
- AsrLsassCredentialTheftBlocked

Dépendances : MDAV

### <a name="block-executable-content-from-email-client-and-webmail"></a>Bloquer le contenu exécutable du client de messagerie et de la messagerie web

Cette règle empêche le lancement des types de fichiers suivants à partir du courrier électronique ouvert dans l’application Microsoft Outlook, ou Outlook.com et d’autres fournisseurs de messagerie web populaires :

- Fichiers exécutables (tels que .exe, .dll ou .scr)
- Fichiers de script (tels qu’un fichier .ps PowerShell, Visual Basic .vbs ou javascript .js fichier)

Intune nom :`Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

Microsoft Endpoint Manager nom complet :`Block executable content from email client and webmail`

GUID : `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

Type d’action de recherche avancée :

- AsrExecutableEmailContentAudited
- AsrExecutableEmailContentBlocked

Dépendances : MDAV

> [!NOTE]
> La règle Bloquer **le contenu exécutable à** partir du client de messagerie et de la messagerie web présente les descriptions alternatives suivantes, selon l’application que vous utilisez :
>
> - Intune (profils de configuration) : exécution du contenu exécutable (exe, dll, ps, js, vbs, etc.) supprimé de la messagerie électronique (client de messagerie web) (aucune exception).
> - Endpoint Manager : bloquer le téléchargement de contenu exécutable à partir des clients de messagerie et de messagerie web.
> - stratégie de groupe : bloquer le contenu exécutable du client de messagerie et de la messagerie web.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance

Cette règle empêche le lancement des fichiers exécutables, tels .exe, .dll ou .scr. Par conséquent, le lancement de fichiers exécutables nontrus ou inconnus peut être risqué, car il peut ne pas être évident initialement si les fichiers sont malveillants.

> [!IMPORTANT]
> Vous devez [activer la protection cloud pour](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) utiliser cette règle.
>
> La règle bloque l’exécution des fichiers **exécutables** , sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance avec un GUID `01443614-cd74-433a-b99e-2ecdc07bfc25` qui appartient à Microsoft et n’est pas spécifié par les administrateurs. Cette règle utilise la protection cloud pour mettre à jour régulièrement sa liste de confiance.
>
> Vous pouvez spécifier des fichiers ou des dossiers individuels (à l’aide de chemins d’accès aux dossiers ou de noms de ressources complets), mais vous ne pouvez pas spécifier à quelles règles ou exclusions s’appliquent.

Intune nom :`Executables that don't meet a prevalence, age, or trusted list criteria`

Configuration Manager nom :`Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID : `01443614-cd74-433a-b99e-2ecdc07bfc25`

Type d’action de recherche avancée :

- AsrUntrustedExecutableAudited
- AsrUntrustedExecutableBlocked

Dépendances : MDAV, Cloud Protection

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>Bloquer l’exécution de scripts potentiellement obscurcis

Cette règle détecte les propriétés suspectes dans un script obscurci.

L’obfuscation de script est une technique courante que les auteurs de programmes malveillants et les applications légitimes utilisent pour masquer la propriété intellectuelle ou réduire les temps de chargement des scripts. Les auteurs de programmes malveillants utilisent également l’obscurcissement pour rendre le code malveillant plus difficile à lire, ce qui empêche l’examen approfondi par les humains et les logiciels de sécurité.

Intune nom :`Obfuscated js/vbs/ps/macro code`

Configuration Manager nom :`Block execution of potentially obfuscated scripts`

GUID : `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

Type d’action de recherche avancée :

- AsrObfuscatedScriptAudited
- AsrObfuscatedScriptBlocked

Dépendances : MDAV, AMSI

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé

Cette règle empêche les scripts de lancer du contenu téléchargé potentiellement malveillant. Les programmes malveillants écrits en JavaScript ou VBScript agissent souvent comme un téléchargeur pour récupérer et lancer d’autres programmes malveillants à partir d’Internet.

Bien que cela ne soit pas courant, les applications métier utilisent parfois des scripts pour télécharger et lancer des programme d’installation.

Intune nom :`js/vbs executing payload downloaded from Internet (no exceptions)`

Configuration Manager nom :`Block JavaScript or VBScript from launching downloaded executable content`

GUID : `d3e037e1-3eb8-44c8-a917-57927947596d`

Type d’action de recherche avancée :

- AsrScriptExecutableDownloadAudited
- AsrScriptExecutableDownloadBlocked

Dépendances : MDAV, AMSI

### <a name="block-office-applications-from-creating-executable-content"></a>Empêcher Office applications de créer du contenu exécutable

Cette règle empêche les applications Office, notamment Word, Excel et PowerPoint, de créer du contenu exécutable potentiellement malveillant, en bloquant l’écriture de code malveillant sur le disque.

Les programmes malveillants qui utilisent Office comme vecteur peuvent tenter de sortir de Office et d’enregistrer des composants malveillants sur le disque. Ces composants malveillants survivraient au redémarrage d’un ordinateur et persisteraient sur le système. Par conséquent, cette règle se défendre contre une technique de persistance courante.

Intune nom :`Office apps/macros creating executable content`

Nom SCCM : `Block Office applications from creating executable content`

GUID : `3b576869-a4ec-4529-8536-b80a7769e899`

Type d’action de recherche avancée :

- AsrExecutableOfficeContentAudited
- AsrExecutableOfficeContentBlocked

Dépendances : MDAV, RPC

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>Empêcher Office applications d’injecter du code dans d’autres processus

Cette règle bloque les tentatives d’injection de code Office applications dans d’autres processus.

Les personnes malveillantes peuvent tenter d Office des applications malveillantes pour migrer du code malveillant vers d’autres processus via l’injection de code, afin que le code puisse être masqué en tant que processus propre.

Il n’existe pas d’objectifs commerciaux légitimes connus pour l’utilisation de l’injection de code.

Cette règle s’applique à Word, Excel et PowerPoint.

Intune nom :`Office apps injecting code into other processes (no exceptions)`

Configuration Manager nom :`Block Office applications from injecting code into other processes`

GUID : `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

Type d’action de recherche avancée :

- AsrOfficeProcessInjectionAudited
- AsrOfficeProcessInjectionBlocked

Dépendances : MDAV

### <a name="block-office-communication-application-from-creating-child-processes"></a>Empêcher Office application de communication de créer des processus enfants

Cette règle empêche les Outlook de créer des processus enfants, tout en permettant des Outlook légitimes.

Cette règle protège contre les attaques d’ingénierie sociale et empêche l’exploitation du code d’exploiter les vulnérabilités dans Outlook. Il protège également contre les Outlook et les [attaques par formulaires](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) que les attaquants peuvent utiliser lorsque les informations d’identification d’un utilisateur sont compromises.

> [!NOTE]
> Cette règle bloque les conseils de stratégie DLP et les infos-bulles dans Outlook. Cette règle s’applique Outlook et Outlook.com uniquement.

Intune nom :`Process creation from Office communication products (beta)`

Configuration Manager: Non disponible

GUID : `26190899-1602-49e8-8b27-eb1d0a1ce869`

Type d’action de recherche avancée :

- AsrOfficeCommAppChildProcessAudited
- AsrOfficeCommAppChildProcessBlocked

Dépendances : MDAV

### <a name="block-persistence-through-wmi-event-subscription"></a>Bloquer la persistance via un abonnement à des événements WMI

Cette règle empêche les programmes malveillants d’utiliser WMI à mauvais escient pour obtenir une persistance sur un appareil.

> [!IMPORTANT]
> Les exclusions de fichiers et de dossiers ne s’appliquent pas à cette règle de réduction de la surface d’attaque.

Les menaces sans fichier emploient diverses tactiques pour rester cachées, éviter d’être vues dans le système de fichiers et obtenir un contrôle d’exécution périodique. Certaines menaces peuvent utiliser à mauvais escient le dépôt WMI et le modèle d’événement pour rester cachées.

Intune: Non disponible

Configuration Manager: Non disponible

GUID : `e6db77e5-3df2-4cf1-b95a-636979351e5b`

Type d’action de recherche avancée :

- AsrPersistenceThroughWmiAudited
- AsrPersistenceThroughWmiBlocked

Dépendances : MDAV, RPC

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>Bloquer les créations de processus provenant de commandes PSExec et WMI

Cette règle empêche l’exécution des processus [créés via PsExec](/sysinternals/downloads/psexec) [et WMI](/windows/win32/wmisdk/about-wmi) . PsExec et WMI peuvent exécuter du code à distance. Il existe donc un risque que des programmes malveillants abusent de cette fonctionnalité à des fins de commande et de contrôle, ou qu’ils propagent une infection dans le réseau d’une organisation.

> [!WARNING]
> Utilisez cette règle uniquement si vous gérez vos appareils avec [Intune ou une](/intune) autre solution MDM. Cette règle n’est pas compatible avec la gestion par [Microsoft Endpoint Configuration Manager](/configmgr) car elle bloque les commandes WMI que le client Configuration Manager utilise pour fonctionner correctement.

Intune nom :`Process creation from PSExec and WMI commands`

Configuration Manager : non applicable

GUID : `d1e49aac-8f56-4280-b9ba-993a6d77406c`

Type d’action de recherche avancée :

- AsrPsexecWmiChildProcessAudited
- AsrPsexecWmiChildProcessBlocked

Dépendances : MDAV

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB

Avec cette règle, les administrateurs peuvent empêcher l’exécution de fichiers exécutables non signés ou non signés à partir de lecteurs amovibles USB, y compris les cartes SD. Les types de fichiers bloqués incluent les fichiers exécutables (tels que .exe, .dll ou .scr)

Intune nom :`Untrusted and unsigned processes that run from USB`

Configuration Manager nom :`Block untrusted and unsigned processes that run from USB`

GUID : `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

Type d’action de recherche avancée :

- AsrUntrustedUsbProcessAudited
- AsrUntrustedUsbProcessBlocked

Dépendances : MDAV

### <a name="block-win32-api-calls-from-office-macros"></a>Bloquer les appels d’API Win32 à Office macros

Cette règle empêche les macros VBA d’appeler les API Win32.

Office VBA active les appels d’API Win32. Les programmes malveillants peuvent utiliser cette fonctionnalité de manière abusive, par exemple appeler des API [Win32 pour lancer des shellcodes](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) malveillants sans écrire quoi que ce soit directement sur le disque. La plupart des organisations ne s’appuient pas sur la possibilité d’appeler des API Win32 dans leur fonctionnement quotidien, même si elles utilisent des macros d’autres manières.

Systèmes d’exploitation pris en charge :          

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

Intune nom :`Win32 imports from Office macro code`

Configuration Manager nom :`Block Win32 API calls from Office macros`

GUID : `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

Type d’action de recherche avancée :

- AsrOfficeMacroWin32ApiCallsAudited
- AsrOfficeMacroWin32ApiCallsBlocked

Dépendances : MDAV, AMSI

### <a name="use-advanced-protection-against-ransomware"></a>Utiliser la protection avancée contre les ransomware

Cette règle fournit une couche supplémentaire de protection contre les ransomware. Il utilise des heuristiques client et cloud pour déterminer si un fichier ressemble à un ransomware. Cette règle ne bloque pas les fichiers qui ont une ou plusieurs des caractéristiques suivantes :

- Le fichier a déjà été trouvé comme non partageable dans le cloud Microsoft.
- Le fichier est un fichier signé valide.
- Le fichier est suffisamment répandu pour ne pas être considéré comme un ransomware.

La règle a tendance à faire preuve de prudence pour empêcher les ransomware.

> [!NOTE]
> Vous devez [activer la protection cloud pour](enable-cloud-protection-microsoft-defender-antivirus.md) utiliser cette règle.

Intune nom :`Advanced ransomware protection`

Configuration Manager nom :`Use advanced protection against ransomware`

GUID : `c1db55ab-c21a-4637-bb3f-a12568109d35`

Type d’action de recherche avancée :

- AsrRansomwareAudited
- AsrRansomwareBlocked

Dépendances : MDAV, Cloud Protection
