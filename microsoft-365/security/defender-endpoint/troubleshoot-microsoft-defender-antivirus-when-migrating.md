---
title: Résoudre des problèmes de l’antivirus Microsoft Defender lors de la migration à partir d’une solution tierce
description: Résoudre les erreurs courantes lors de la migration vers l’antivirus Microsoft Defender
keywords: événement, code d’erreur, journalisation, dépannage, antivirus Microsoft Defender, antivirus Windows Defender, migration, antivirus microsoft defender
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: martyav
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.collection: M365-security-compliance
search.appverid: met150
ms.openlocfilehash: 0c40e3396baac6cdf066e8371c6633094f68ef8d
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67684296"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Résoudre des problèmes de l’antivirus Microsoft Defender lors de la migration à partir d’une solution tierce

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Antivirus Microsoft Defender](https://www.microsoft.com/windows/comprehensive-security)

**Plateformes**
- Windows

Vous trouverez de l’aide ici si vous rencontrez des problèmes lors de la migration d’une solution de sécurité tierce vers l’antivirus Microsoft Defender.

## <a name="review-event-logs"></a>Examiner les journaux des événements

1. Ouvrez l’application Observateur d’événements en sélectionnant l’icône **Rechercher** dans la barre des tâches et en recherchant *l’observateur d’événements*.

    Vous trouverez des informations sur l’Antivirus Microsoft Defender sous **Les journaux des applications et des** \> services **Microsoft** \> **Windows** \> **Windows Defender**.

1. À partir de là, sélectionnez **Ouvrir** sous **Opérationnel**.

    La sélection d’un événement dans le volet d’informations vous montre plus d’informations sur un événement dans le volet inférieur, sous les **onglets** **Général** et Détails.

## <a name="microsoft-defender-antivirus-wont-start"></a>L’antivirus Microsoft Defender ne démarre pas

Ce problème peut se manifester sous la forme de plusieurs ID d’événement différents, qui ont tous la même cause sous-jacente.

### <a name="associated-event-ids"></a>ID d’événement associés

ID d’événement|Nom du journal|Description|Source
---|---|---|---
15|Application|Mise à jour réussie de l’état Windows Defender à SECURITY_PRODUCT_STATE_OFF.|Security Center
5007|Microsoft-Windows-Windows Defender/Operational|La configuration de l’antivirus Microsoft Defender a changé. S’il s’agit d’un événement inattendu, vous devez examiner les paramètres, car cela peut être le résultat d’un programme malveillant. <p> **Ancienne valeur :** Default\IsServiceRunning = 0x0 <p> **Nouvelle valeur :** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/Operational|L’analyse antivirus Microsoft Defender pour les logiciels espions et d’autres logiciels potentiellement indésirables est désactivée.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Comment savoir si l’antivirus Microsoft Defender ne démarre pas, car un antivirus tiers est installé

Sur un appareil Windows 10 ou Windows 11, si vous n’utilisez pas Microsoft Defender pour point de terminaison et que vous avez installé un antivirus tiers, l’antivirus Microsoft Defender est automatiquement désactivé. Si vous utilisez Microsoft Defender pour point de terminaison avec un antivirus tiers installé, l’antivirus Microsoft Defender démarre en mode passif, avec des fonctionnalités réduites.

> [!TIP]
> Le scénario décrit s’applique uniquement à Windows 10 et Windows 11. Les autres versions de Windows ont [des réponses différentes](microsoft-defender-antivirus-compatibility.md) à l’antivirus Microsoft Defender exécuté avec des logiciels de sécurité tiers.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Utiliser l’application Services pour vérifier si l’antivirus Microsoft Defender est désactivé

Pour ouvrir l’application Services, sélectionnez l’icône **Rechercher** dans la barre des tâches et recherchez *des services*. Vous pouvez également ouvrir l’application à partir de la ligne de commande en tapant *services.msc*.

Les informations sur l’Antivirus Microsoft Defender sont répertoriées dans l’application Services sous **Windows Defender** \> **Operational**. Le nom du service antivirus est *Microsoft Defender Antivirus Service*.

Lors de la vérification de l’application, vous pouvez voir que *le service antivirus Microsoft Defender* est défini sur manuel, mais lorsque vous essayez de démarrer ce service manuellement, vous recevez un avertissement indiquant que *le service antivirus Microsoft Defender sur l’ordinateur local a démarré, puis s’est arrêté. Certains services s’arrêtent automatiquement s’ils ne sont pas utilisés par d’autres services ou programmes.*

Cela indique que l’antivirus Microsoft Defender a été automatiquement désactivé pour préserver la compatibilité avec un antivirus tiers.

#### <a name="generate-a-detailed-report"></a>Générer un rapport détaillé

Vous pouvez générer un rapport détaillé sur les stratégies de groupe actuellement actives en ouvrant une invite de commandes en mode **d’exécution en tant qu’administrateur** , puis en entrant la commande suivante :

```console
GPresult.exe /h gpresult.html
```

Cela génère un rapport situé à *./gpresult.html*. Ouvrez ce fichier et vous pouvez voir les résultats suivants, en fonction de la façon dont l’antivirus Microsoft Defender a été désactivé.

##### <a name="group-policy-results"></a>Résultats de la stratégie de groupe

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Si les paramètres de sécurité sont implémentés par le biais d’une stratégie de groupe (GPO) au niveau local ou du domaine, ou via System Center Configuration Manager (SCCM)

Dans le rapport GPResults, sous l’en-tête *Composants Windows/Antivirus Microsoft Defender*, vous pouvez voir quelque chose comme l’entrée suivante, indiquant que l’antivirus Microsoft Defender est désactivé.

Stratégie|Setting|Objet de stratégie de groupe gagnant
---|---|---
Désactiver l’antivirus Microsoft Defender|Activé|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Si les paramètres de sécurité sont implémentés via la préférence de stratégie de groupe (GPP)

Sous *l’en-tête, élément de Registre (chemin de la clé : HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, nom de la valeur : DisableAntiSpyware)* , vous pouvez voir quelque chose comme l’entrée suivante, indiquant que l’antivirus Microsoft Defender est désactivé.

DisableAntiSpyware|-
---|---
Objet de stratégie de groupe gagnant|Win10-Workstations
Résultat : Réussite|
**Général**|
Action|Update
**Properties**|
Ruche|HKEY_LOCAL_MACHINE
Chemin de la clé|SOFTWARE\Policies\Microsoft\Windows Defender
Nom de la valeur|DisableAntiSpyware
Type de valeur|REG_DWORD
Données de la valeur|0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>Si les paramètres de sécurité sont implémentés via la clé de Registre

Le rapport peut contenir le texte suivant, indiquant que l’antivirus Microsoft Defender est désactivé :

> Registre (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (hex)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Si les paramètres de sécurité sont définis dans Windows ou votre image Windows Server

Votre administrateur imaginant peut avoir défini la stratégie de sécurité **[, DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)**, localement via *GPEdit.exe*, *LGPO.exe* ou en modifiant le registre dans leur séquence de tâches. Vous pouvez [configurer un identificateur d’image approuvé](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) pour l’antivirus Microsoft Defender.

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Réactiver l’Antivirus Microsoft Defender

L’antivirus Microsoft Defender s’active automatiquement si aucun autre antivirus n’est actuellement actif. Vous devez désactiver complètement l’antivirus tiers pour vous assurer que l’antivirus Microsoft Defender peut s’exécuter avec toutes les fonctionnalités.

> [!WARNING]
> Les solutions qui suggèrent de modifier les valeurs *de début Windows Defender* pour *wdboot*, *wdfilter*, *wdnisdrv*, *wdnissvc* et *windefend* dans HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services ne sont pas prises en charge et peuvent vous forcer à réinitialiser votre système.

Le mode passif est disponible si vous commencez à utiliser Microsoft Defender pour point de terminaison et un antivirus tiers avec l’antivirus Microsoft Defender. Le mode passif permet à l’Antivirus Microsoft Defender d’analyser les fichiers et de se mettre à jour, mais il ne corrige pas les menaces. En outre, la surveillance du comportement via la [protection en temps réel](configure-real-time-protection-microsoft-defender-antivirus.md) n’est pas disponible en mode passif, sauf si [la protection contre la perte de données de point de terminaison (DLP)](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) est déployée.

Une autre fonctionnalité, appelée [analyse périodique limitée](limited-periodic-scanning-microsoft-defender-antivirus.md), est disponible pour les utilisateurs finaux lorsque l’antivirus Microsoft Defender est configuré pour être désactivé automatiquement. Cette fonctionnalité permet à l’Antivirus Microsoft Defender d’analyser régulièrement des fichiers avec un antivirus tiers, à l’aide d’un nombre limité de détections.

> [!IMPORTANT]
> L’analyse périodique limitée n’est pas recommandée dans les environnements d’entreprise. Les fonctionnalités de détection, de gestion et de création de rapports disponibles lors de l’exécution de l’Antivirus Microsoft Defender dans ce mode sont réduites par rapport au mode actif.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)


### <a name="see-also"></a>Voir aussi

- [Compatibilité de l’antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md)
- [Antivirus Microsoft Defender dans l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md)
