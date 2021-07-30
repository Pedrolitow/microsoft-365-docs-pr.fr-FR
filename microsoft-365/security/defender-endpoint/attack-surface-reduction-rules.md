---
title: Règles de réduction des surfaces d'attaque
description: Répertorie les détails sur les règles de réduction de la surface d’attaque par règle.
keywords: Règles de réduction de la surface d’attaque, règles de réduction de la surface d’attaque, règles asr, système de prévention des intrusions hôtes, règles de protection, règles anti-attaque, règles d’attaque, règles de prévention des infections, Microsoft Defender pour point de terminaison, configurer les règles de réduction de la surface d’attaque, description des règles de réduction de la surface d’attaque
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar, jcedola
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.openlocfilehash: b79fc88c7e69b27c6af47065ef02ada98fad4821
ms.sourcegitcommit: b3091791196828883d8284497561027df692d109
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2021
ms.locfileid: "53664056"
---
# <a name="attack-surface-reduction-rules"></a>Règles de réduction des surfaces d'attaque

Cet article fournit des informations sur les règles de réduction des attaques :  

- [Versions de système d’exploitation prise en charge](#supported-operating-systems)
- [Systèmes de gestion de la configuration pris en charge](#supported-configuration-management-systems)
- [Descriptions par règle](#per-rule-descriptions)
  - Descriptions des règles
  - GUID
  - Noms de règles du système de gestion de la configuration

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge 

Le tableau suivant répertorie les règles de réduction de la surface d’attaque par ordre alphabétique. Une coche indique que la règle est prise en charge par le système d’exploitation répertorié dans cette colonne.

> [!Note]
>
> - Sauf indication contraire, la version Windows 10 minimale est la &nbsp; version 1709 (RS3, build 16299) ou ultérieure ; la version minimale de Windows Server est &nbsp; la version 1809 ou ultérieure.
>
> - \* Toutes les règles prisent en charge les exclusions de fichiers et de dossiers, sauf indication contraire.

| Nom de la règle |  &nbsp;Windows 10 | &nbsp;Windows Server 2019 | &nbsp;Windows Serveur | &nbsp;Windows Server 2016 | &nbsp;Windows Server 2012 R2 |
|---|:---:|:---:|:---:|:---:|:---:|
|[Bloquer l’utilisation abusive des pilotes signés vulnérables exploités](#block-abuse-of-exploited-vulnerable-signed-drivers) | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> version 1803 (canal semi-annuel) ou version ultérieure |  |  |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | ![Pris en charge](images/checkmark.png) <br><br> version 1809 ou ultérieure | ![Pris en charge](images/checkmark.png) | ![Pris en charge](images/checkmark.png)  <br><br> |  |  |
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | ![Pris en charge](images/checkmark.png) <br><br> version 1803 ou ultérieure | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Bloquer le contenu exécutable du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | ![Pris en charge](images/checkmark.png) <br><br> version 1803 ou ultérieure | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Bloquer l’exécution de scripts potentiellement obscurcis](#block-execution-of-potentially-obfuscated-scripts) | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Empêcher Office applications de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Empêcher Office applications d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes)  | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Empêcher Office application de communication de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Bloquer la persistance via un abonnement à des événements WMI](#block-persistence-through-wmi-event-subscription) <br><br> \*_Les exclusions de fichiers et de dossiers ne sont pas pris en charge._ | ![Pris en charge](images/checkmark.png) <br><br> version 1903 (build 18362) ou version ultérieure| ![Pris en charge](images/checkmark.png) | ![Pris en charge](images/checkmark.png) <br><br> version 1903 (build 18362) ou version ultérieure |  |  |
|[Bloquer les créations de processus provenant de commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | ![Pris en charge](images/checkmark.png) <br><br> version 1803 ou ultérieure | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br>  |  |  |
|[Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Bloquer les appels d’API Win32 à partir Office macros](#block-win32-api-calls-from-office-macros) | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
|[Utiliser la protection avancée contre les ransomware](#use-advanced-protection-against-ransomware) | ![Pris en charge](images/checkmark.png) <br><br> version 1803 ou ultérieure | ![Pris en charge](images/checkmark.png) <br><br> | ![Pris en charge](images/checkmark.png) <br><br> |  |  |
| **Nom de la règle** |  **&nbsp;Windows 10** | **&nbsp;Windows Server 2019** | **&nbsp;Windows Serveur** | **&nbsp;Windows Server 2016** | **&nbsp;Windows Server 2012 R2** |

## <a name="supported-configuration-management-systems"></a>Systèmes de gestion de la configuration pris en charge

Les liens vers des informations sur les versions du système de gestion de la configuration référencés dans ce tableau sont répertoriés sous ce tableau.

|Nom de la règle | Intune | Gestionnaire de point de terminaison Microsoft | Microsoft Endpoint Configuration Manager | Stratégie de groupe | PowerShell |
|---|:---:|:---:|:---:|:---:|:---:|
|[Bloquer l’utilisation abusive des pilotes signés vulnérables exploités](#block-abuse-of-exploited-vulnerable-signed-drivers) | ![Pris en charge](images/checkmark.png) <br><br>  |  ![Pris en charge](images/checkmark.png) <br><br> MEM OMA-URI |   |   |  ![Pris en charge](images/checkmark.png) <br><br> |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes) | ![Pris en charge](images/checkmark.png) |   | ![Pris en charge](images/checkmark.png) |   |   |
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes) | ![Pris en charge](images/checkmark.png) |   | ![Pris en charge](images/checkmark.png) <br><br> CB 1710 |   |   |
|[Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | ![Pris en charge](images/checkmark.png)  |   |  ![Pris en charge](images/checkmark.png) <br><br> CB 1802 |   |   |
|[Bloquer le contenu exécutable du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail) | ![Pris en charge](images/checkmark.png) |  | ![Pris en charge](images/checkmark.png) <br><br> CB 1710 | ![Pris en charge](images/checkmark.png) |   |
|[Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | ![Pris en charge](images/checkmark.png) |   | ![Pris en charge](images/checkmark.png) <br><br> CB 1802 |   |   |
|[Bloquer l’exécution de scripts potentiellement obscurcis](#block-execution-of-potentially-obfuscated-scripts) | ![Pris en charge](images/checkmark.png) |   |  ![Pris en charge](images/checkmark.png)  <br><br> CB 1710 |   |   |
|[Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | ![Pris en charge](images/checkmark.png) |   |  ![Pris en charge](images/checkmark.png) <br><br> CB 1710 |   |   |
|[Empêcher Office applications de créer du contenu exécutable](#block-office-applications-from-creating-executable-content) | ![Pris en charge](images/checkmark.png) <br><br> |  | ![Pris en charge](images/checkmark.png) <br><br> CB 1710 <br><br> |   |   |
|[Empêcher Office applications d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes) | ![Pris en charge](images/checkmark.png) |  |  ![Pris en charge](images/checkmark.png) <br><br> CB 1710 |   |   |
|[Empêcher Office application de communication de créer des processus enfants](#block-office-communication-application-from-creating-child-processes) | ![Pris en charge](images/checkmark.png) |  | ![Pris en charge](images/checkmark.png) <br><br>  CB 1710 |   |   |
|[Bloquer la persistance via un abonnement à des événements WMI](#block-persistence-through-wmi-event-subscription) |  |  |  |   |   |
|[Bloquer les créations de processus provenant de commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | ![Pris en charge](images/checkmark.png) |   |   |   |   |
|[Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | ![Pris en charge](images/checkmark.png) |   | ![Pris en charge](images/checkmark.png) <br><br> CB 1802 <br><br> |   |   |
|[Bloquer les appels d’API Win32 à partir Office macros](#block-win32-api-calls-from-office-macros) | ![Pris en charge](images/checkmark.png) |   | ![Pris en charge](images/checkmark.png) <br><br> CB 1710 <br><br> |   |   |
|[Utiliser la protection avancée contre les ransomware](#use-advanced-protection-against-ransomware) | ![Pris en charge](images/checkmark.png) |   |  ![Pris en charge](images/checkmark.png) <br><br>  CB 1802 |   |   |
| **Nom de la règle** | **Intune** | **Microsoft Endpoint Manager** | **Microsoft Endpoint Configuration Manager** | **Stratégie de groupe** | **PowerShell** |

- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)
- [Microsoft Endpoint Manager CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager CB 1710 (SCCM)](/configmgr/core/servers/manage/updates) <br>_SCCM est désormais Microsoft Endpoint Configuration Manager._

## <a name="per-rule-descriptions"></a>Descriptions par règle

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>Bloquer l’utilisation abusive des pilotes signés vulnérables exploités

Cette règle empêche une application d’écrire un pilote signé vulnérable sur le disque. Les pilotes signés in-the-wild et vulnérables peuvent être exploités par des applications locales qui ont des \- _privilèges suffisants_ pour accéder \- au noyau. Les pilotes signés vulnérables permettent aux attaquants de désactiver ou de contourner les solutions de sécurité, ce qui peut conduire à la compromission du système.

La règle bloquer l’utilisation abusive des pilotes **signés vulnérables exploités** ne bloque pas le chargement d’un pilote déjà existant sur le système.

>[!NOTE]
>
> Vous pouvez configurer cette règle à l’aide de l’OMA-URI MEM. Voir [MEM OMA-URI pour](enable-attack-surface-reduction.md#mem) configurer des règles personnalisées.
>
> Vous pouvez également configurer cette règle à [l’aide de PowerShell.](enable-attack-surface-reduction.md#powershell)
>
> Pour examiner un pilote, utilisez ce site Web pour soumettre [un pilote pour analyse.](https://www.microsoft.com/wdsi/driversubmission)

Nom Intune : `Block abuse of exploited vulnerable signed drivers`

GUID :  `56a863a9-875e-4185-98a7-b882c64b5ce5`

### <a name="block-adobe-reader-from-creating-child-processes"></a>Empêcher Adobe Reader de créer des processus enfants

Cette règle empêche les attaques en empêchant Adobe Reader de créer des processus.

Grâce à l’ingénierie sociale ou aux attaques, les programmes malveillants peuvent télécharger et lancer des charges utiles, et sortir d’Adobe Reader. En empêchant les processus enfants d’être générés par Adobe Reader, les programmes malveillants qui tentent de l’utiliser comme vecteur sont empêchés de se propager.

Nom Intune : `Process creation from Adobe Reader (beta)`

Nom du Gestionnaire de configuration : pas encore disponible

GUID : `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

### <a name="block-all-office-applications-from-creating-child-processes"></a>Empêcher toutes les applications Office de créer des processus enfants

Cette règle empêche Office applications de créer des processus enfants. Office applications incluent Word, Excel, PowerPoint, OneNote et Access.

La création de processus enfants malveillants est une stratégie anti-programme malveillant courante. Les programmes malveillants qui utilisent Office comme vecteur exécutent souvent des macros VBA et exploitent du code pour télécharger et essayer d’exécuter davantage de charges utiles. Toutefois, certaines applications métier légitimes peuvent également générer des processus enfants à des fins non médicales ; par exemple, la création d’une invite de commandes ou l’utilisation de PowerShell pour configurer les paramètres de Registre.

Nom Intune : `Office apps launching child processes`

Nom du Gestionnaire de configuration : `Block Office application from creating child processes`

GUID : `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>Bloquer le vol d’informations d’identification Windows sous-système de l’autorité de sécurité locale

Cette règle empêche le vol d’informations d’identification en verrouilleant le service LSASS (Local Security Authority Subsystem Service).

LSASS authentifier les utilisateurs qui se connectent sur Windows ordinateur. Microsoft Defender Credential Guard dans Windows 10 normalement les tentatives d’extraction d’informations d’identification à partir de LSASS. Toutefois, certaines organisations ne peuvent pas activer Credential Guard sur tous leurs ordinateurs en raison de problèmes de compatibilité avec les pilotes de carte à puce personnalisés ou d’autres programmes chargés dans l’autorité de sécurité locale (LSA). Dans ce cas, les attaquants peuvent utiliser des outils de piratage tels que Mimikatz pour supprimer des mots de passe en texte clair et des hages NTLM à partir de LSASS.

> [!NOTE]
> Dans certaines applications, le code éumène tous les processus en cours d’exécution et tente de les ouvrir avec des autorisations exhaustives. Cette règle refuse l’action d’ouverture du processus de l’application et enregistre les détails dans le journal des événements de sécurité. Cette règle peut générer beaucoup de bruit. Si vous disposez d’une application qui é énumére simplement LSASS, mais qui n’a aucun impact réel sur les fonctionnalités, il n’est pas nécessaire de l’ajouter à la liste d’exclusions. En soi, cette entrée du journal des événements n’indique pas nécessairement une menace malveillante.

Nom Intune : `Flag credential stealing from the Windows local security authority subsystem`

Nom du Gestionnaire de configuration : `Block credential stealing from the Windows local security authority subsystem`

GUID : `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

### <a name="block-executable-content-from-email-client-and-webmail"></a>Bloquer le contenu exécutable du client de messagerie et de la messagerie web

Cette règle empêche le lancement des types de fichiers suivants à partir du courrier électronique ouvert dans l’application Microsoft Outlook, ou de Outlook.com et d’autres fournisseurs de messagerie web populaires :

- Fichiers exécutables (tels que .exe, .dll ou .scr)
- Fichiers de script (tels qu’un fichier .ps PowerShell, Visual Basic .vbs ou javascript .js fichier)

Nom Intune : `Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

Microsoft Endpoint Manager nom de l’Microsoft Endpoint Manager :`Block executable content from email client and webmail`

GUID : `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

> [!NOTE]
> La règle Bloquer **le contenu exécutable** à partir du client de messagerie et de la messagerie web présente les descriptions alternatives suivantes, selon l’application que vous utilisez :
>
> - Intune (Profils de configuration) : exécution du contenu exécutable (exe, dll, ps, js, vbs, etc.) supprimé de la messagerie électronique (webmail/client de messagerie) (aucune exception).
> - Endpoint Manager : bloquer le téléchargement de contenu exécutable à partir des clients de messagerie et de messagerie web.
> - Stratégie de groupe : bloquer le contenu exécutable à partir du client de messagerie et de la messagerie web.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance

Cette règle empêche le lancement des fichiers exécutables, tels que .exe, .dll ou .scr, sauf si l’une des conditions suivantes est remplie :

- Prévalence : les fichiers exécutables sont trouvés sur plus de 1 000 points de terminaison
- Âge : les fichiers exécutables ont été publiés il y a plus de 24 heures
- Emplacement : les fichiers exécutables sont inclus dans une liste de confiance ou une liste d’exclusions

Le lancement de fichiers exécutables nontrus ou inconnus peut être risqué, car il peut ne pas être évident initialement si les fichiers sont malveillants.

> [!IMPORTANT]
> Vous devez [activer la protection cloud pour](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) utiliser cette règle.
>
> La règle bloque l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de **prévalence,** d’âge ou de liste de confiance avec un GUID qui appartient à Microsoft et n’est pas spécifié par les `01443614-cd74-433a-b99e-2ecdc07bfc25` administrateurs. Cette règle utilise la protection cloud pour mettre à jour régulièrement sa liste de confiance.
>
> Vous pouvez spécifier des fichiers ou des dossiers individuels (à l’aide de chemins d’accès aux dossiers ou de noms de ressources complets), mais vous ne pouvez pas spécifier à quelles règles ou exclusions s’appliquent.

Nom Intune : `Executables that don't meet a prevalence, age, or trusted list criteria`

Nom du Gestionnaire de configuration : `Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID : `01443614-cd74-433a-b99e-2ecdc07bfc25`

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>Bloquer l’exécution de scripts potentiellement obscurcis

Cette règle détecte les propriétés suspectes dans un script obscurci.

L’obfuscation de script est une technique courante que les auteurs de programmes malveillants et les applications légitimes utilisent pour masquer la propriété intellectuelle ou réduire les temps de chargement des scripts. Les auteurs de programmes malveillants utilisent également l’obscurcissement pour rendre le code malveillant plus difficile à lire, ce qui empêche l’examen approfondi par les humains et les logiciels de sécurité.

Nom Intune : `Obfuscated js/vbs/ps/macro code`

Nom du Gestionnaire de configuration : `Block execution of potentially obfuscated scripts`

GUID : `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé

Cette règle empêche les scripts de lancer du contenu téléchargé potentiellement malveillant. Les programmes malveillants écrits en JavaScript ou VBScript agissent souvent comme un téléchargeur pour récupérer et lancer d’autres programmes malveillants à partir d’Internet.

Bien que cela ne soit pas courant, les applications métier utilisent parfois des scripts pour télécharger et lancer des programme d’installation.

Nom Intune : `js/vbs executing payload downloaded from Internet (no exceptions)`

Nom du Gestionnaire de configuration : `Block JavaScript or VBScript from launching downloaded executable content`

GUID : `d3e037e1-3eb8-44c8-a917-57927947596d`

### <a name="block-office-applications-from-creating-executable-content"></a>Empêcher Office applications de créer du contenu exécutable

Cette règle empêche les applications Office, notamment Word, Excel et PowerPoint, de créer du contenu exécutable potentiellement malveillant, en bloquant l’écriture de code malveillant sur le disque.

Les programmes malveillants qui utilisent Office comme vecteur peuvent tenter de sortir de Office et d’enregistrer des composants malveillants sur le disque. Ces composants malveillants survivraient au redémarrage d’un ordinateur et persisteraient sur le système. Par conséquent, cette règle se défendre contre une technique de persistance courante.

Nom Intune : `Office apps/macros creating executable content`

Nom SCCM : `Block Office applications from creating executable content`

GUID : `3b576869-a4ec-4529-8536-b80a7769e899`

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>Empêcher Office applications d’injecter du code dans d’autres processus

Cette règle bloque les tentatives d’injection de code Office applications dans d’autres processus.

Les personnes malveillantes peuvent tenter d’Office des applications malveillantes pour migrer du code malveillant vers d’autres processus via l’injection de code, afin que le code puisse être masqué en tant que processus propre.

Il n’existe pas d’objectifs commerciaux légitimes connus pour l’utilisation de l’injection de code.

Cette règle s’applique à Word, Excel et PowerPoint.

Nom Intune : `Office apps injecting code into other processes (no exceptions)`

Nom du Gestionnaire de configuration : `Block Office applications from injecting code into other processes`

GUID : `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

### <a name="block-office-communication-application-from-creating-child-processes"></a>Empêcher Office application de communication de créer des processus enfants

Cette règle empêche les Outlook de créer des processus enfants, tout en permettant des fonctions Outlook légitimes.

Cette règle protège contre les attaques d’ingénierie sociale et empêche l’exploitation du code d’exploiter les vulnérabilités dans Outlook. Il protège également contre les Outlook et les attaques par formulaires que les [attaquants](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) peuvent utiliser lorsque les informations d’identification d’un utilisateur sont compromises.

> [!NOTE]
> Cette règle bloque les conseils de stratégie DLP et les infos-bulles dans Outlook. Cette règle s’applique Outlook et Outlook.com uniquement.

Nom Intune : `Process creation from Office communication products (beta)`

Nom du Gestionnaire de configuration : non disponible

GUID : `26190899-1602-49e8-8b27-eb1d0a1ce869`

### <a name="block-persistence-through-wmi-event-subscription"></a>Bloquer la persistance via un abonnement à des événements WMI

Cette règle empêche les programmes malveillants d’utiliser WMI pour atteindre la persistance sur un appareil.

> [!IMPORTANT]
> Les exclusions de fichiers et de dossiers ne s’appliquent pas à cette règle de réduction de la surface d’attaque.

Les menaces sans fichier utilisent différentes tactiques pour rester masquées, pour éviter d’être vues dans le système de fichiers et pour obtenir un contrôle d’exécution périodique. Certaines menaces peuvent utiliser le référentiel WMI et le modèle d’événement pour rester masqués.

Nom Intune : non disponible

Nom du Gestionnaire de configuration : non disponible

GUID : `e6db77e5-3df2-4cf1-b95a-636979351e5b`

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>Bloquer les créations de processus provenant de commandes PSExec et WMI

Cette règle empêche l’exécution des processus créés via [PsExec](/sysinternals/downloads/psexec) [et WMI.](/windows/win32/wmisdk/about-wmi) PsExec et WMI peuvent exécuter du code à distance. Il existe donc un risque que des programmes malveillants abusent de cette fonctionnalité à des fins de commande et de contrôle, ou qu’ils propagent une infection dans le réseau d’une organisation.

> [!WARNING]
> Utilisez cette règle uniquement si vous gérez vos appareils avec [Intune](/intune) ou une autre solution MDM. Cette règle n’est pas compatible avec la gestion par [Microsoft Endpoint Configuration Manager](/configmgr) car elle bloque les commandes WMI que le client Configuration Manager utilise pour fonctionner correctement.

Nom Intune : `Process creation from PSExec and WMI commands`

Nom du Gestionnaire de configuration : non applicable

GUID : `d1e49aac-8f56-4280-b9ba-993a6d77406c`

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB

Avec cette règle, les administrateurs peuvent empêcher l’exécution de fichiers exécutables non signés ou non signés à partir de lecteurs amovibles USB, y compris les cartes SD. Les types de fichiers bloqués incluent les fichiers exécutables (tels que .exe, .dll ou .scr)

Nom Intune : `Untrusted and unsigned processes that run from USB`

Nom du Gestionnaire de configuration : `Block untrusted and unsigned processes that run from USB`

GUID : `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

### <a name="block-win32-api-calls-from-office-macros"></a>Bloquer les appels d’API Win32 à partir Office macros

Cette règle empêche les macros VBA d’appeler les API Win32.

Office VBA active les appels d’API Win32. Les programmes malveillants peuvent utiliser cette fonctionnalité de manière abusive, par exemple appeler des API Win32 pour lancer des [shellcodes](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) malveillants sans écrire quoi que ce soit directement sur le disque. La plupart des organisations ne s’appuient pas sur la possibilité d’appeler des API Win32 dans leur fonctionnement quotidien, même si elles utilisent des macros d’autres manières.

Systèmes d’exploitation pris en charge :          

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Serveur, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

Nom Intune : `Win32 imports from Office macro code`

Nom du Gestionnaire de configuration : `Block Win32 API calls from Office macros`

GUID : `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

### <a name="use-advanced-protection-against-ransomware"></a>Utiliser la protection avancée contre les ransomware

Cette règle fournit une couche supplémentaire de protection contre les ransomware. Il utilise des heuristiques client et cloud pour déterminer si un fichier ressemble à un ransomware. Cette règle ne bloque pas les fichiers qui ont une ou plusieurs des caractéristiques suivantes :

- Le fichier a déjà été trouvé comme non partageable dans le cloud Microsoft.
- Le fichier est un fichier signé valide.
- Le fichier est suffisamment répandu pour ne pas être considéré comme un ransomware.

La règle a tendance à faire preuve de prudence pour empêcher les ransomware.

> [!NOTE]
> Vous devez [activer la protection cloud pour](enable-cloud-protection-microsoft-defender-antivirus.md) utiliser cette règle.

Nom Intune : `Advanced ransomware protection`

Nom du Gestionnaire de configuration : `Use advanced protection against ransomware`

GUID : `c1db55ab-c21a-4637-bb3f-a12568109d35`