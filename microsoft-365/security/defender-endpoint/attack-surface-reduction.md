---
title: Utiliser des règles de réduction de la surface d’attaque pour empêcher l’infection par des programmes malveillants
description: Les règles de réduction de la surface d’attaque peuvent aider à empêcher les attaques d’utiliser des applications et des scripts pour infecter les appareils à l’aide de programmes malveillants.
keywords: Règles de réduction de la surface d’attaque, asr, hips, système de prévention des intrusions hôtes, règles de protection, anti-attaque, attaque, prévention des infections, Microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde, sugamar, jcedola
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 7360087e1863e81e4dc9e8acc2817e1320d6f4d8
ms.sourcegitcommit: d904f04958a13a514ce10219ed822b9e4f74ca2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "53028786"
---
# <a name="use-attack-surface-reduction-rules-to-prevent-malware-infection"></a>Utiliser des règles de réduction de la surface d’attaque pour empêcher l’infection par des programmes malveillants

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="why-attack-surface-reduction-rules-are-important"></a>Pourquoi les règles de réduction de la surface d’attaque sont-elles importantes ?

La surface d’attaque de votre organisation inclut tous les endroits où un attaquant peut compromettre les appareils ou les réseaux de votre organisation. Réduire votre surface d’attaque signifie protéger les appareils et le réseau de votre organisation, ce qui laisse aux attaquants moins de moyens d’effectuer des attaques. La configuration des règles de réduction de la surface d’attaque dans Microsoft Defender pour endpoint peut vous aider !

Les règles de réduction de la surface d’attaque ciblent certains comportements logiciels, tels que :

- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter des fichiers
- Exécution de scripts obscurcis ou suspects
- Comportement d’une application qui n’est généralement pas initiée pendant le travail quotidien normal

De tels comportements logiciels sont parfois observés dans les applications légitimes. Toutefois, ces comportements sont souvent considérés comme risqués, car ils sont couramment abusés par des personnes malveillantes par le biais de programmes malveillants. Les règles de réduction de la surface d’attaque peuvent limiter les comportements à risque logiciels et contribuer à la sécurité de votre organisation.

Pour plus d’informations sur la configuration des règles de réduction de la surface d’attaque, voir Activer les règles de [réduction de la surface d’attaque.](enable-attack-surface-reduction.md)

## <a name="assess-rule-impact-before-deployment"></a>Évaluer l’impact des règles avant le déploiement

Vous pouvez évaluer l’impact d’une règle de réduction de la surface d’attaque sur votre réseau en ouvrant la recommandation de sécurité pour cette règle [dans Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/#tvm).

:::image type="content" source="images/asrrecommendation.png" alt-text="Contrôle de sécurité pour la règle de réduction de la surface d’attaque":::

Dans le volet d’informations de recommandation, vérifiez l’impact sur l’utilisateur pour déterminer quel pourcentage de vos appareils peuvent accepter une nouvelle stratégie permettant d’activer la règle en mode de blocage sans affecter la productivité.

## <a name="audit-mode-for-evaluation"></a>Mode audit pour l’évaluation

Utilisez le [mode audit pour](audit-windows-defender.md) évaluer l’impact des règles de réduction de la surface d’attaque sur votre organisation si elle est activée. Exécutez d’abord toutes les règles en mode audit pour comprendre comment elles affectent vos applications métier. De nombreuses applications métier sont écrites avec des problèmes de sécurité limités et peuvent effectuer des tâches qui semblent similaires aux programmes malveillants. En surveillant les données d’audit et en ajoutant [des exclusions](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) pour les applications nécessaires, vous pouvez déployer des règles de réduction de la surface d’attaque sans réduire la productivité.

## <a name="warn-mode-for-users"></a>Mode Avertissement pour les utilisateurs

(**NOUVEAU**!) Avant d’avertir les fonctionnalités du mode, les règles de réduction de la surface d’attaque activées pouvaient être définies sur le mode audit ou le mode blocage. Avec le nouveau mode d’avertissement, chaque fois que le contenu est bloqué par une règle de réduction de la surface d’attaque, les utilisateurs voient une boîte de dialogue qui indique que le contenu est bloqué. La boîte de dialogue offre également à l’utilisateur la possibilité de débloquer le contenu. L’utilisateur peut ensuite réessayer son action et l’opération se termine. Lorsqu’un utilisateur débloque du contenu, il reste débloqué pendant 24 heures, puis bloque les reprises.

Le mode Avertissement aide votre organisation à mettre en place des règles de réduction de la surface d’attaque sans empêcher les utilisateurs d’accéder au contenu dont ils ont besoin pour effectuer leurs tâches.

### <a name="requirements-for-warn-mode-to-work"></a>Conditions requises pour que le mode d’avertissement fonctionne

Le mode Avertissement est pris en charge sur les appareils exécutant les versions suivantes de Windows :

- [Windows 10, version 1809](/windows/whats-new/whats-new-windows-10-version-1809) ou ultérieure
- [Windows Server, version 1809 ou](/windows-server/get-started/whats-new-in-windows-server-1809) ultérieure

Antivirus Microsoft Defender doit être en cours d’exécution avec une protection en temps réel [en mode actif.](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state)

En outre, assurez-vous [Antivirus Microsoft Defender mises](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) à jour du logiciel anti-programme malveillant sont installées.

- Conditions minimales requises pour la publication de la plateforme : `4.18.2008.9`
- Conditions minimales requises pour la publication du moteur : `1.1.17400.5`

Pour plus d’informations et pour obtenir vos mises à jour, voir Mise à jour [pour la plateforme de logiciel anti-programme malveillant Microsoft Defender.](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform)

### <a name="cases-where-warn-mode-is-not-supported"></a>Cas où le mode d’avertissement n’est pas pris en charge

Le mode Avertissement n’est pas pris en charge pour trois règles de réduction de la surface d’attaque lorsque vous les configurez dans Microsoft Endpoint Manager. (Si vous utilisez une stratégie de groupe pour configurer vos règles de réduction de la surface d’attaque, le mode d’avertissement est pris en charge.) Les trois règles qui ne viennent pas en charge le mode d’avertissement lorsque vous les configurez Microsoft Endpoint Manager sont les suivantes :

- [Empêcher JavaScript ou VBScript de lancer le contenu exécutable](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) téléchargé (GUID) `d3e037e1-3eb8-44c8-a917-57927947596d`
- [Bloquer la persistance via l’abonnement aux événements WMI](#block-persistence-through-wmi-event-subscription) (GUID) `e6db77e5-3df2-4cf1-b95a-636979351e5b`
- [Utiliser la protection avancée contre les ransomware](#use-advanced-protection-against-ransomware) (GUID) `c1db55ab-c21a-4637-bb3f-a12568109d35`

En outre, le mode avertissement n’est pas pris en charge sur les appareils exécutant des versions antérieures Windows. Dans ce cas, les règles de réduction de la surface d’attaque configurées pour s’exécuter en mode avertissement s’exécutent en mode blocage.

## <a name="notifications-and-alerts"></a>Notifications et alertes

Chaque fois qu’une règle de réduction de la surface d’attaque est déclenchée, une notification s’affiche sur l’appareil. Vous pouvez [personnaliser la notification](customize-attack-surface-reduction.md#customize-the-notification) avec les informations et les coordonnées de l’entreprise.

En outre, lorsque certaines règles de réduction de la surface d’attaque sont déclenchées, des alertes sont générées.

Les notifications et les alertes générées peuvent être vues dans le portail Microsoft 365 Defender ( ) (anciennement appelé Centre de sécurité Microsoft Defender [https://security.microsoft.com](https://security.microsoft.com) ). [](microsoft-defender-security-center.md)

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>Événements de réduction de la surface d’attaque et de recherche avancée

Vous pouvez utiliser la recherche avancée pour afficher les événements de réduction de la surface d’attaque. Pour simplifier le volume des données entrantes, seuls les processus uniques pour chaque heure sont consultables avec le hunting avancé. L’heure d’un événement de réduction de la surface d’attaque est la première fois que cet événement est vu dans l’heure.

Par exemple, supposons qu’un événement de réduction de la surface d’attaque se produise sur 10 appareils pendant l’heure de 14 h 00. Supposons que le premier événement s’est produit à 2:15 et le dernier à 2:45. Avec le hunting avancé, vous verrez une instance de cet événement (même si elle s’est réellement produite sur 10 appareils) et son timestamp sera 14:15 PM.

Pour plus d’informations sur le chasse avancée, consultez la recherche proactive de [menaces avec le chasse avancée.](advanced-hunting-overview.md)

## <a name="attack-surface-reduction-features-across-windows-versions"></a>Fonctionnalités de réduction de la surface d’attaque Windows versions

Vous pouvez définir des règles de réduction de la surface d’attaque pour les appareils qui exécutent l’une des éditions et versions suivantes de Windows :

- Windows 10 Professionnel, [version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows 10 Entreprise, [version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows Serveur, [version 1803 (canal semi-annuel)](/windows-server/get-started/whats-new-in-windows-server-1803) ou version ultérieure
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)

Bien que les règles de réduction de la surface d’attaque ne nécessitent pas [Windows licence E5,](/windows/deployment/deploy-enterprise-licenses)si vous avez Windows E5, vous obtenez des fonctionnalités de gestion avancées. Les fonctionnalités avancées, disponibles uniquement dans Windows E5, sont les suivantes :

- Surveillance, analyse et flux de travail disponibles dans [Defender for Endpoint](microsoft-defender-endpoint.md)
- Fonctionnalités de rapport et de configuration dans [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Ces fonctionnalités avancées ne sont pas disponibles avec une licence Windows Professional ou Windows E3. Toutefois, si vous avez ces licences, vous pouvez utiliser l’Observateur d’événements et les journaux Antivirus Microsoft Defender pour passer en revue vos événements de règle de réduction de la surface d’attaque.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>Passer en revue les événements de réduction de la surface d’attaque dans Microsoft 365 Defender portail

Defender pour le point de terminaison fournit des rapports détaillés pour les événements et les blocages dans le cadre de scénarios d’investigation d’alerte.

Vous pouvez interroger Defender pour obtenir des données de point de terminaison [dans Microsoft 365 Defender](microsoft-defender-security-center.md) à l’aide d’un [recherche avancée.](advanced-hunting-query-language.md) Si vous exécutez le [mode audit,](audit-windows-defender.md)vous pouvez utiliser la recherche avancée pour comprendre l’impact des règles de réduction de la surface d’attaque sur votre environnement.

Voici un exemple de requête :

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Passer en revue les événements de réduction de la surface d’Windows l’Observateur d’événements

Vous pouvez consulter le journal Windows événements pour afficher les événements générés par les règles de réduction de la surface d’attaque :

1. Téléchargez le [package d’évaluation](https://aka.ms/mp7z2w) et *extrayez* le fichiercfa-events.xmlun emplacement facilement accessible sur l’appareil.

2. Entrez les mots, *Observateur d’événements,* dans le menu Démarrer pour ouvrir l Windows’observateur d’événements.

3. Sous **Actions,** **sélectionnez Importer un affichage personnalisé...**.

4. Sélectionnez le fichier *cfa-events.xml'où* il a été extrait. Vous pouvez également [copier le XML directement.](event-views.md)

5. Sélectionnez **OK**.

Vous pouvez créer une vue personnalisée qui filtre les événements pour afficher uniquement les événements suivants, tous liés à l’accès contrôlé aux dossiers :

|ID d’événement|Description|
|---|---|
|5007|Événement lorsque les paramètres sont modifiés|
|1121|Événement lorsque la règle se déclenche en mode blocage|
|1122|Événement lorsque la règle se déclenche en mode audit|

La « version du moteur » répertoriée pour les événements de réduction de la surface d’attaque dans le journal des événements est générée par Defender pour le point de terminaison, et non par le système d’exploitation. Defender pour le point de terminaison est intégré à Windows 10, de sorte que cette fonctionnalité fonctionne sur tous les appareils sur Windows 10 installé.

## <a name="attack-surface-reduction-rules"></a>Règles de réduction des surfaces d'attaque

Le tableau et les sous-sections suivants décrivent chacune des 16 règles de réduction de la surface d’attaque. Les règles de réduction de la surface d’attaque sont répertoriées par ordre alphabétique, par nom de règle.

Si vous configurez des règles de réduction de la surface d’attaque à l’aide de la stratégie de groupe ou de PowerShell, vous aurez besoin des GUID. En revanche, si vous utilisez Microsoft Endpoint Manager ou Microsoft Intune, vous n’avez pas besoin des GUID.

|Nom de la règle|GUID|Exclusions de & fichiers|Système d’exploitation minimal pris en charge|
|---|:---:|---|---|
|[Bloquer l’utilisation abusive des pilotes signés vulnérables exploités](#block-abuse-of-exploited-vulnerable-signed-drivers)|`56a863a9-875e-4185-98a7-b882c64b5ce5`|Pris en charge|[Windows 10 version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure) |
|[Empêcher Adobe Reader de créer des processus enfants](#block-adobe-reader-from-creating-child-processes)|`7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Empêcher toutes les applications Office de créer des processus enfants](#block-all-office-applications-from-creating-child-processes)|`D4F940AB-401B-4EFC-AADC-AD5F3C50688A`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem)|`9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Bloquer le contenu exécutable du client de messagerie et de la messagerie web](#block-executable-content-from-email-client-and-webmail)|`BE9BA2D9-53EA-4CDC-84E5-9B1EEEE46550`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)|`01443614-cd74-433a-b99e-2ecdc07bfc25`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Bloquer l’exécution de scripts potentiellement obscurcis](#block-execution-of-potentially-obfuscated-scripts)|`5BEB7EFE-FD9A-4556-801D-275E5FFC04CC`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé](#block-javascript-or-vbscript-from-launching-downloaded-executable-content)|`D3E037E1-3EB8-44C8-A917-57927947596D`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Empêcher Office applications de créer du contenu exécutable](#block-office-applications-from-creating-executable-content)|`3B576869-A4EC-4529-8536-B80A7769E899`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Empêcher Office applications d’injecter du code dans d’autres processus](#block-office-applications-from-injecting-code-into-other-processes)|`75668C1F-73B5-4CF0-BB93-3ECF5CB7CC84`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Empêcher Office application de communication de créer des processus enfants](#block-office-communication-application-from-creating-child-processes)|`26190899-1602-49e8-8b27-eb1d0a1ce869`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Bloquer la persistance via un abonnement à des événements WMI](#block-persistence-through-wmi-event-subscription)|`e6db77e5-3df2-4cf1-b95a-636979351e5b`|Non pris en charge|[Windows 10, version 1903](/windows/whats-new/whats-new-windows-10-version-1903) (build 18362) ou supérieure|
|[Bloquer les créations de processus provenant de commandes PSExec et WMI](#block-process-creations-originating-from-psexec-and-wmi-commands)|`d1e49aac-8f56-4280-b9ba-993a6d77406c`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB](#block-untrusted-and-unsigned-processes-that-run-from-usb)|`b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Bloquer les appels d’API Win32 à partir Office macros](#block-win32-api-calls-from-office-macros)|`92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|[Utiliser la protection avancée contre les ransomware](#use-advanced-protection-against-ransomware)|`c1db55ab-c21a-4637-bb3f-a12568109d35`|Pris en charge|[Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) (RS3, build 16299) ou version supérieure|
|

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>Bloquer l’utilisation abusive des pilotes signés vulnérables exploités

Cette règle empêche une application d’écrire un pilote signé vulnérable sur le disque. Les pilotes signés in-the-wild et vulnérables peuvent être exploités par des applications locales qui ont des \- _privilèges suffisants_ pour accéder \- au noyau. Les pilotes signés vulnérables permettent aux attaquants de désactiver ou de contourner les solutions de sécurité, ce qui peut conduire à la compromission du système.

La règle bloquer l’utilisation abusive des pilotes **signés vulnérables exploités** ne bloque pas le chargement d’un pilote déjà existant sur le système.

>[!NOTE]
>
> Vous pouvez configurer cette règle à l’aide [de MEM OMA-URI](enable-attack-surface-reduction.md#mem) pour les informations procédurales des règles personnalisées OMA-URI MEM.
>
> Vous pouvez également configurer cette règle à [l’aide de PowerShell.](enable-attack-surface-reduction.md#powershell)
>
> Pour examiner un pilote, utilisez ce site Web pour soumettre [un pilote pour analyse.](https://www.microsoft.com/en-us/wdsi/driversubmission)

Cette règle est prise en charge dans toutes les versions dans lesquelles la RSA est prise en charge ; qui est :

- [Windows 10 Professionnel, version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- [Windows 10 Entreprise, version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- [Windows Server, version 1803 (canal semi-annuel)](/windows-server/get-started/whats-new-in-windows-server-1803) ou version ultérieure
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)

Nom Intune : `Block abuse of exploited vulnerable signed drivers`

GUID :  `56a863a9-875e-4185-98a7-b882c64b5ce5`

### <a name="block-adobe-reader-from-creating-child-processes"></a>Empêcher Adobe Reader de créer des processus enfants

Cette règle empêche les attaques en empêchant Adobe Reader de créer des processus.

Grâce à l’ingénierie sociale ou aux attaques, les programmes malveillants peuvent télécharger et lancer des charges utiles, et sortir d’Adobe Reader. En empêchant les processus enfants d’être générés par Adobe Reader, les programmes malveillants qui tentent de l’utiliser comme vecteur sont empêchés de se propager.

Cette règle a été introduite dans :

- [Windows 10, version 1809](/windows/whats-new/whats-new-windows-10-version-1809)
- [Windows Serveur, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)

Nom Intune : `Process creation from Adobe Reader (beta)`

Nom du Gestionnaire de configuration : pas encore disponible

GUID : `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

### <a name="block-all-office-applications-from-creating-child-processes"></a>Empêcher toutes les applications Office de créer des processus enfants

Cette règle empêche Office applications de créer des processus enfants. Office applications incluent Word, Excel, PowerPoint, OneNote et Access.

La création de processus enfants malveillants est une stratégie anti-programme malveillant courante. Les programmes malveillants qui utilisent Office comme vecteur exécutent souvent des macros VBA et exploitent du code pour télécharger et essayer d’exécuter davantage de charges utiles. Toutefois, certaines applications métier légitimes peuvent également générer des processus enfants à des fins non médicales ; par exemple, la création d’une invite de commandes ou l’utilisation de PowerShell pour configurer les paramètres de Registre.

Cette règle a été introduite dans :

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Serveur, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

Nom Intune : `Office apps launching child processes`

Nom du Gestionnaire de configuration : `Block Office application from creating child processes`

GUID : `D4F940AB-401B-4EFC-AADC-AD5F3C50688A`

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>Bloquer le vol d’informations d’identification Windows sous-système de l’autorité de sécurité locale

Cette règle empêche le vol d’informations d’identification en verrouilleant le service LSASS (Local Security Authority Subsystem Service).

LSASS authentifier les utilisateurs qui se connectent sur Windows ordinateur. Microsoft Defender Credential Guard dans Windows 10 normalement les tentatives d’extraction d’informations d’identification à partir de LSASS. Toutefois, certaines organisations ne peuvent pas activer Credential Guard sur tous leurs ordinateurs en raison de problèmes de compatibilité avec les pilotes de carte à puce personnalisés ou d’autres programmes chargés dans l’autorité de sécurité locale (LSA). Dans ce cas, les attaquants peuvent utiliser des outils de piratage tels que Mimikatz pour supprimer des mots de passe en texte clair et des hages NTLM à partir de LSASS.

> [!NOTE]
> Dans certaines applications, le code éumène tous les processus en cours d’exécution et tente de les ouvrir avec des autorisations exhaustives. Cette règle refuse l’action d’ouverture du processus de l’application et enregistre les détails dans le journal des événements de sécurité. Cette règle peut générer beaucoup de bruit. Si vous disposez d’une application qui é énumére simplement LSASS, mais qui n’a aucun impact réel sur les fonctionnalités, il n’est pas nécessaire de l’ajouter à la liste d’exclusions. En soi, cette entrée du journal des événements n’indique pas nécessairement une menace malveillante.

Cette règle a été introduite dans :

- [Windows 10, version 1803](/windows/whats-new/whats-new-windows-10-version-1803)
- [Windows Serveur, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)

Nom Intune : `Flag credential stealing from the Windows local security authority subsystem`

Nom du Gestionnaire de configuration : `Block credential stealing from the Windows local security authority subsystem`

GUID : `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

### <a name="block-executable-content-from-email-client-and-webmail"></a>Bloquer le contenu exécutable du client de messagerie et de la messagerie web

Cette règle empêche le lancement des types de fichiers suivants à partir du courrier électronique ouvert dans l’application Microsoft Outlook, ou de Outlook.com et d’autres fournisseurs de messagerie web populaires :

- Fichiers exécutables (tels que .exe, .dll ou .scr)
- Fichiers de script (tels qu’un fichier .ps PowerShell, Visual Basic .vbs ou javascript .js fichier)

Cette règle a été introduite dans :

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Serveur, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Microsoft Endpoint Manager CB 1710](/configmgr/core/servers/manage/updates)

Nom Intune : `Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

Microsoft Endpoint Manager nom de l’Microsoft Endpoint Manager :`Block executable content from email client and webmail`

GUID : `BE9BA2D9-53EA-4CDC-84E5-9B1EEEE46550`

> [!NOTE]
> La règle Bloquer **le contenu exécutable** à partir du client de messagerie et de la messagerie web présente les descriptions alternatives suivantes, selon l’application que vous utilisez :
>
> - Intune (Profils de configuration) : exécution du contenu exécutable (exe, dll, ps, js, vbs, etc.) supprimé de la messagerie électronique (webmail/client de messagerie) (aucune exception).
> - Endpoint Manager : bloquer le téléchargement de contenu exécutable à partir des clients de messagerie et de messagerie web.
> - Stratégie de groupe : bloquer le contenu exécutable à partir du client de messagerie et de la messagerie web.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance

Cette règle empêche le lancement des types de fichiers suivants, sauf s’ils répondent à des critères de prévalence ou d’âge, ou s’ils se retrouvent dans une liste de confiance ou d’exclusion :

- Fichiers exécutables (tels que .exe, .dll ou .scr)

Le lancement de fichiers exécutables nontrus ou inconnus peut être risqué, car il peut ne pas être évident initialement si les fichiers sont malveillants.

> [!IMPORTANT]
> Vous devez [activer la protection cloud pour](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) utiliser cette règle.
>
> La règle bloque l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de **prévalence,** d’âge ou de liste de confiance avec un GUID qui appartient à Microsoft et n’est pas spécifié par les `01443614-cd74-433a-b99e-2ecdc07bfc25` administrateurs. Cette règle utilise la protection cloud pour mettre à jour régulièrement sa liste de confiance.
>
> Vous pouvez spécifier des fichiers ou des dossiers individuels (à l’aide de chemins d’accès aux dossiers ou de noms de ressources complets), mais vous ne pouvez pas spécifier à quelles règles ou exclusions s’appliquent.

Cette règle a été introduite dans :

- [Windows 10, version 1803](/windows/whats-new/whats-new-windows-10-version-1803)
- [Windows Serveur, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)

Nom Intune : `Executables that don't meet a prevalence, age, or trusted list criteria`

Nom du Gestionnaire de configuration : `Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID : `01443614-cd74-433a-b99e-2ecdc07bfc25`

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>Bloquer l’exécution de scripts potentiellement obscurcis

Cette règle détecte les propriétés suspectes dans un script obscurci.

L’obfuscation de script est une technique courante que les auteurs de programmes malveillants et les applications légitimes utilisent pour masquer la propriété intellectuelle ou réduire les temps de chargement des scripts. Les auteurs de programmes malveillants utilisent également l’obscurcissement pour rendre le code malveillant plus difficile à lire, ce qui empêche l’examen approfondi par les humains et les logiciels de sécurité.

Cette règle a été introduite dans :

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Serveur, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

Nom Intune : `Obfuscated js/vbs/ps/macro code`

Nom du Gestionnaire de configuration : `Block execution of potentially obfuscated scripts`

GUID : `5BEB7EFE-FD9A-4556-801D-275E5FFC04CC`

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé

Cette règle empêche les scripts de lancer du contenu téléchargé potentiellement malveillant. Les programmes malveillants écrits en JavaScript ou VBScript agissent souvent comme un téléchargeur pour récupérer et lancer d’autres programmes malveillants à partir d’Internet.

Bien que cela ne soit pas courant, les applications métier utilisent parfois des scripts pour télécharger et lancer des programme d’installation.

Cette règle a été introduite dans :

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Serveur, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

Nom Intune : `js/vbs executing payload downloaded from Internet (no exceptions)`

Nom du Gestionnaire de configuration : `Block JavaScript or VBScript from launching downloaded executable content`

GUID : `D3E037E1-3EB8-44C8-A917-57927947596D`

### <a name="block-office-applications-from-creating-executable-content"></a>Empêcher Office applications de créer du contenu exécutable

Cette règle empêche Office applications, notamment Word, Excel et PowerPoint, de créer du contenu exécutable potentiellement malveillant, en bloquant l’écriture de code malveillant sur le disque.

Les programmes malveillants qui utilisent Office comme vecteur peuvent tenter de sortir de Office et d’enregistrer des composants malveillants sur le disque. Ces composants malveillants survivraient au redémarrage d’un ordinateur et persisteraient sur le système. Par conséquent, cette règle se défendre contre une technique de persistance courante.

Cette règle a été introduite dans :

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Serveur, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [System Center Configuration Manager](/configmgr/core/servers/manage/updates) (SCCM) CB 1710 (SCCM est désormais Microsoft Endpoint Configuration Manager)

Nom Intune : `Office apps/macros creating executable content`

Nom SCCM : `Block Office applications from creating executable content`

GUID : `3B576869-A4EC-4529-8536-B80A7769E899`

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>Empêcher Office applications d’injecter du code dans d’autres processus

Cette règle bloque les tentatives d’injection de code Office applications dans d’autres processus.

Les personnes malveillantes peuvent tenter d’Office des applications malveillantes pour migrer du code malveillant vers d’autres processus via l’injection de code, afin que le code puisse être masqué en tant que processus propre.

Il n’existe pas d’objectifs commerciaux légitimes connus pour l’utilisation de l’injection de code.

Cette règle s’applique à Word, Excel et PowerPoint.

Cette règle a été introduite dans :

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Serveur, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

Nom Intune : `Office apps injecting code into other processes (no exceptions)`

Nom du Gestionnaire de configuration : `Block Office applications from injecting code into other processes`

GUID : `75668C1F-73B5-4CF0-BB93-3ECF5CB7CC84`

### <a name="block-office-communication-application-from-creating-child-processes"></a>Empêcher Office application de communication de créer des processus enfants

Cette règle empêche Outlook de créer des processus enfants, tout en permettant des fonctions Outlook légitimes.

Cette règle protège contre les attaques d’ingénierie sociale et empêche l’exploitation du code d’exploiter les vulnérabilités dans Outlook. Il protège également contre les attaques par formulaire et les règles Outlook que les [attaquants](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) peuvent utiliser lorsque les informations d’identification d’un utilisateur sont compromises.

> [!NOTE]
> Cette règle bloque les conseils et les infos-bulles de stratégie DLP dans Outlook. Cette règle s’applique à Outlook et Outlook.com uniquement.

Cette règle a été introduite dans :

- [Windows 10, version 1809](/windows/whats-new/whats-new-windows-10-version-1809)
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)

Nom Intune : `Process creation from Office communication products (beta)`

Nom du Gestionnaire de configuration : non disponible

GUID : `26190899-1602-49e8-8b27-eb1d0a1ce869`

### <a name="block-persistence-through-wmi-event-subscription"></a>Bloquer la persistance via un abonnement à des événements WMI

Cette règle empêche les programmes malveillants d’utiliser WMI pour atteindre la persistance sur un appareil.

> [!IMPORTANT]
> Les exclusions de fichiers et de dossiers ne s’appliquent pas à cette règle de réduction de la surface d’attaque.

Les menaces sans fichier utilisent différentes tactiques pour rester masquées, pour éviter d’être vues dans le système de fichiers et pour obtenir un contrôle d’exécution périodique. Certaines menaces peuvent utiliser le référentiel WMI et le modèle d’événement pour rester masqués.

Cette règle a été introduite dans :

- [Windows 10, version 1903](/windows/whats-new/whats-new-windows-10-version-1903)
- [Windows Server 1903](/windows-server/get-started-19/whats-new-in-windows-server-1903-1909)

Nom Intune : non disponible

Nom du Gestionnaire de configuration : non disponible

GUID : `e6db77e5-3df2-4cf1-b95a-636979351e5b`

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>Bloquer les créations de processus provenant de commandes PSExec et WMI

Cette règle empêche l’exécution des processus créés via [PsExec](/sysinternals/downloads/psexec) [et WMI.](/windows/win32/wmisdk/about-wmi) PsExec et WMI peuvent exécuter du code à distance. Il existe donc un risque que des programmes malveillants abusent de cette fonctionnalité à des fins de commande et de contrôle, ou qu’ils propagent une infection dans le réseau d’une organisation.

> [!WARNING]
> Utilisez cette règle uniquement si vous gérez vos appareils avec [Intune](/intune) ou une autre solution MDM. Cette règle n’est pas compatible avec la gestion via [Microsoft Endpoint Configuration Manager,](/configmgr) car elle bloque les commandes WMI que le client Configuration Manager utilise pour fonctionner correctement.

Cette règle a été introduite dans :

- [Windows 10, version 1803](/windows/whats-new/whats-new-windows-10-version-1803)
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)

Nom Intune : `Process creation from PSExec and WMI commands`

Nom du Gestionnaire de configuration : non applicable

GUID : `d1e49aac-8f56-4280-b9ba-993a6d77406c`

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB

Avec cette règle, les administrateurs peuvent empêcher l’exécution de fichiers exécutables non signés ou non signés à partir de lecteurs amovibles USB, y compris les cartes SD. Les types de fichiers bloqués incluent les fichiers exécutables (tels que .exe, .dll ou .scr)

Cette règle a été introduite dans :

- [Windows 10, version 1803](/windows/whats-new/whats-new-windows-10-version-1803)
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)

Nom Intune : `Untrusted and unsigned processes that run from USB`

Nom du Gestionnaire de configuration : `Block untrusted and unsigned processes that run from USB`

GUID : `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

### <a name="block-win32-api-calls-from-office-macros"></a>Bloquer les appels d’API Win32 à partir de macros Office

Cette règle empêche les macros VBA d’appeler les API Win32.

Office VBA active les appels d’API Win32. Les programmes malveillants peuvent utiliser cette fonctionnalité de manière abusive, par exemple appeler des API Win32 pour lancer des [shellcodes](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) malveillants sans écrire quoi que ce soit directement sur le disque. La plupart des organisations ne s’appuient pas sur la possibilité d’appeler des API Win32 dans leur fonctionnement quotidien, même si elles utilisent des macros d’autres manières.

Cette règle a été introduite dans :

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

Nom Intune : `Win32 imports from Office macro code`

Nom du Gestionnaire de configuration : `Block Win32 API calls from Office macros`

GUID : `92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B`

### <a name="use-advanced-protection-against-ransomware"></a>Utiliser la protection avancée contre les ransomware

Cette règle fournit une couche supplémentaire de protection contre les ransomware. Il utilise des heuristiques client et cloud pour déterminer si un fichier ressemble à un ransomware. Cette règle ne bloque pas les fichiers qui ont une ou plusieurs des caractéristiques suivantes :

- Le fichier a déjà été trouvé comme non partageable dans le cloud Microsoft.
- Le fichier est un fichier signé valide.
- Le fichier est suffisamment répandu pour ne pas être considéré comme un ransomware.

La règle a tendance à faire preuve de prudence pour empêcher les ransomware.

> [!NOTE]
> Vous devez [activer la protection cloud pour](enable-cloud-protection-microsoft-defender-antivirus.md) utiliser cette règle.

Cette règle a été introduite dans :

- [Windows 10, version 1803](/windows/whats-new/whats-new-windows-10-version-1803)
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)

Nom Intune : `Advanced ransomware protection`

Nom du Gestionnaire de configuration : `Use advanced protection against ransomware`

GUID : `c1db55ab-c21a-4637-bb3f-a12568109d35`
