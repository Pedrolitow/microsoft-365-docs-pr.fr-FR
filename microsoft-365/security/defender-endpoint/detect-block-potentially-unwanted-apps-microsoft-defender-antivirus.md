---
title: Bloquer des applications potentiellement indésirables avec l’Antivirus Microsoft Defender
description: Activer la fonctionnalité antivirus de l’application de protection contre les applications potentiellement indésirables (PUA) pour bloquer des logiciels non souhaités tels qu’un logiciel de publicité.
keywords: applications potentiellement indésirables (pua), activer, logiciel non souhaité, applications indésirables, logiciel de publicité, barre d’outils du navigateur, détecter, bloquer, Antivirus Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: detect
ms.sitesec: library
ms.localizationpriority: high
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
audience: ITPro
ms.reviewer: mimilone, julih
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: m365-security-compliance
ms.openlocfilehash: ea8df5216464feb0cd1807e7f64d8adbdde3f2e7
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61110198"
---
# <a name="detect-and-block-potentially-unwanted-applications"></a>Détecter et bloquer des applications potentiellement indésirables

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- [Microsoft Edge](/microsoft-edge/deploy/microsoft-edge)

Les applications potentiellement indésirables (PUA) est une catégorie de logiciel qui peut amener votre ordinateur à fonctionner lentement, afficher des publicités inattendues ou, au pire, installer un autre programme pouvant être imprévu ou non souhaité. Les applications potentiellement indésirables (PUA) ne sont pas considérées comme des virus, des programmes malveillants ou d’autres types de menace, mais elles peuvent effectuer des actions sur les points de terminaison qui affectent négativement l’utilisation ou les performances des points de terminaison. Le terme *PUA* peut également faire référence à une application ayant une réputation médiocre, tel qu’évalué par Microsoft Defender pour point de terminaison, en raison de types de comportement indésirables.

Voici quelques exemples :

- **Logiciel de publicité** qui affiche des publicités ou des promotions, notamment le programme qui insert des publicités sur des pages web.
- **Logiciel de regroupement** qui propose d’installer un autre programme qui n’est pas signé numériquement par la même entité. En outre, un logiciel qui propose d’installer un autre programme qui est considéré comme application potentiellement indésirable.
- **Logiciel type évasion** qui tente de manière active d’éviter la détection par les produits de sécurité, y compris le programme qui agit différemment en présence de produits de sécurité.

> [!TIP]
> Pour d’autres exemples et une discussion sur les critères que nous utilisons pour étiqueter des applications auxquelles il convient que les fonctionnalités de sécurité accordent une attention particulière, voir [Comment Microsoft identifie les programmes malveillants et les applications potentiellement indésirables](/windows/security/threat-protection/intelligence/criteria).

Les applications potentiellement indésirables peuvent augmenter le risque que votre réseau soit infecté par un vrai programme malveillant, rendre les infections de programme malveillant plus difficiles à détecter ou gaspiller des ressources informatiques pour les nettoyer. La protection PUA est prise en charge sur Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 et Windows Server 2016. Dans Windows 10 (version 2004 et ultérieure), l’Antivirus Microsoft Defender bloque les applications considérées par défaut comme applications potentiellement indésirables pour les appareils Entreprise (E5).

## <a name="microsoft-edge"></a>Microsoft Edge

Le [nouveau Microsoft Edge](https://support.microsoft.com/microsoft-edge/get-to-know-microsoft-edge-3f4bb0ff-58de-2188-55c0-f560b7e20bea), qui est basé sur Chromium, bloque les téléchargements d’applications potentiellement indésirables et les URL de ressources associées. Cette fonctionnalité est proposée par [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview).

### <a name="enable-pua-protection-in-chromium-based-microsoft-edge"></a>Activer la protection contre les applications potentiellement indésirables dans Microsoft Edge basé sur Chromium

Bien que la protection contre les applications potentiellement indésirables dans Microsoft Edge (basé sur Chromium, version 80.0.361.50) soit désactivée par défaut, vous pouvez facilement l’activer dans le navigateur.

1. Dans votre navigateur Microsoft Edge, sélectionnez les ellipses, puis choisissez **Paramètres**.

2. Sélectionnez **Confidentialité, recherche et services**.

3. Sous la section **Sécurité**, activez **Bloquer les applications potentiellement indésirables**.

> [!TIP]
> Si vous exécutez Microsoft Edge (basé sur Chromium), vous pouvez explorer en toute sécurité la fonctionnalité de blocage d’URL de la protection contre les applications potentiellement indésirables en la testant sur l’une de nos [pages de démonstration Microsoft Defender SmartScreen](https://demo.smartscreen.msft.net/).

### <a name="block-urls-with-microsoft-defender-smartscreen"></a>Bloquer les URL avec Microsoft Defender SmartScreen

Dans Microsoft Edge basé sur Chromium avec la protection contre les applications potentiellement indésirables activée, Microsoft Defender SmartScreen vous protège contre les URL associées aux applications potentiellement indésirables.

Les administrateurs de sécurité peuvent [configurer](/DeployEdge/configure-microsoft-edge) comment Microsoft Edge et Microsoft Defender SmartScreen travaillent ensemble pour protéger des groupes d’utilisateurs contre des URL associées aux applications potentiellement indésirables. Il existe plusieurs [paramètres de stratégie de groupe](/DeployEdge/microsoft-edge-policies#smartscreen-settings) explicitement disponibles pour Microsoft Defender SmartScreen, notamment [une bloquant les applications potentiellement indésirables](/DeployEdge/microsoft-edge-policies#smartscreenpuaenabled). En outre, les administrateurs peuvent [configurer Microsoft Defender SmartScreen](/microsoft-edge/deploy/available-policies?source=docs#configure-windows-defender-smartscreen) dans son ensemble, en utilisant les paramètres de stratégie de groupe pour activer ou désactiver Microsoft Defender SmartScreen.

Bien que Microsoft Defender pour point de terminaison ait sa propre liste de blocage basée sur un jeu de données gérées par Microsoft, vous pouvez personnaliser cette liste en fonction de votre propre veille contre les menaces. Si vous [créez et gérez des indicateurs](manage-indicators.md) dans le portail Microsoft Defender pour point de terminaison, Microsoft Defender SmartScreen respecte les nouveaux paramètres.

## <a name="microsoft-defender-antivirus-and-pua-protection"></a>Antivirus Microsoft Defender et la protection contre les applications potentiellement indésirables (PUA)

La fonctionnalité de protection contre les applications potentiellement indésirables (PUA) dans l’Antivirus Microsoft Defender peut détecter et bloquer les applications potentiellement indésirables (PUA) sur les points de terminaison dans votre réseau.

> [!NOTE]
> Cette fonctionnalité est disponible dans Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 et Windows Server 2016.

L’Antivirus Microsoft Defender bloque les fichiers détectés d’applications potentiellement indésirables (PUA) et toutes les tentatives pour les télécharger, déplacer, exécuter ou installer. Les fichiers d’applications potentiellement indésirables (PUA) sont ensuite déplacés vers la mise en quarantaine. Lorsqu’un fichier d’applications potentiellement indésirables (PUA) est détecté sur un point de terminaison, l’Antivirus Microsoft Defender envoie une notification à l’utilisateur ([sauf si les notifications sont désactivées](configure-notifications-microsoft-defender-antivirus.md)) dans le même format que les autres détections de menaces. La notification est précédée par `PUA:` pour indiquer son contenu.

La notification s’affiche dans [la liste de quarantaine dans l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).

## <a name="configure-pua-protection-in-microsoft-defender-antivirus"></a>Configurer la protection contre les applications potentiellement indésirables (PUA) dans l’Antivirus Microsoft Defender

Vous pouvez activer la protection contre les applications potentiellement indésirables (PUA) avec [Microsoft Intune](/mem/intune/protect/device-protect), [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection), [la stratégie de groupe](/azure/active-directory-domain-services/manage-group-policy) ou via les [cmdlets PowerShell](/powershell/module/defender/?preserve-view=true&view=win10-ps).

Vous pouvez également utiliser la protection contre les applications potentiellement indésirables (PUA) dans le mode audit pour détecter les applications potentiellement indésirables (PUA) sans les bloquer. Les détections sont capturées dans le journal des événements Windows.

> [!TIP]
> Visitez le site web de démonstration Microsoft Defender pour point de terminaison sur [demo.wd.microsoft.com](https://demo.wd.microsoft.com/Page/UrlRep) pour vérifier que la fonctionnalité est opérationnelle et voir comment elle fonctionne.

La protection contre les applications potentiellement indésirables (PUA) dans le mode audit est utile si votre entreprise effectue une vérification de la conformité en matière de sécurité d’un logiciel interne et vous voulez éviter tout faux positif.

### <a name="use-intune-to-configure-pua-protection"></a>Utiliser Intune pour configurer la protection contre les applications potentiellement indésirables (PUA)

Consultez [Configurer des paramètres de restriction d’appareils dans Microsoft Intune](/intune/device-restrictions-configure) et [Paramètres de restriction d’appareil de l’Antivirus Microsoft Defender pour Windows 10](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) pour obtenir des détails supplémentaires.

### <a name="use-configuration-manager-to-configure-pua-protection"></a>Utiliser Configuration Manager pour configurer la protection contre les applications potentiellement indésirables (PUA)

La protection contre les applications potentiellement indésirables (PUA) est activée par défaut dans Microsoft Endpoint Manager (branche actuelle).

Voir [Comment créer et déployer des stratégies de logiciel anti-programme malveillant : paramètres d’analyses planifiées](/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) pour obtenir des détails sur la configuration de Microsoft Endpoint Manager (branche actuelle).

Pour System Center 2012 Configuration Manager, voir [Comment déployer la stratégie de protection contre les applications potentiellement indésirables (PUA) pour Endpoint protection dans Configuration Manager](/previous-versions/system-center/system-center-2012-R2/hh508770(v=technet.10)#BKMK_PUA).

> [!NOTE]
> Les événements d’applications potentiellement indésirables (PUA) bloqués par l’Antivirus Microsoft Defender sont signalés dans l’Observateur d'événements Windows et non dans Microsoft Endpoint Configuration Manager.

### <a name="use-group-policy-to-configure-pua-protection"></a>Utiliser la stratégie de groupe pour configurer la protection contre les applications potentiellement indésirables (PUA)

1. Télécharger et installer [Modèles d’administration (.admx) pour Windows 10, mise à jour d’octobre 2020 (20H2)](https://www.microsoft.com/download/details.aspx?id=102157).

2. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

3. Sélectionnez l’objet de stratégie de groupe que vous souhaitez configurer, puis choisissez **Modifier**.

4. Dans l’**Éditeur de gestion des stratégies de groupe**, accédez à **Configuration ordinateur**, puis sélectionnez **Modèles d’administration**.

5. Développez les trois sur **Composants Windows**\>**Antivirus Microsoft Defender**.

6. Cliquez deux fois sur **Configurer la détection pour les applications potentiellement indésirables (PUA)**.

7. Sélectionnez **Activé** pour activer la protection contre les applications potentiellement indésirables (PUA).

8. Dans **Options**, sélectionnez **Bloquer** pour bloquer les applications potentiellement indésirables ou **Mode Audit** pour tester le fonctionnement du setting dans votre environnement. Sélectionnez **OK**.

9. Déployez votre objet de stratégie de groupe comme vous le faites habituellement.

### <a name="use-powershell-cmdlets-to-configure-pua-protection"></a>Utiliser les cmdlets PowerShell pour configurer la protection contre les applications potentiellement indésirables (PUA)

#### <a name="to-enable-pua-protection"></a>Pour activer la protection contre les applications potentiellement indésirables (PUA)

```PowerShell
Set-MpPreference -PUAProtection Enabled
```

La configuration de la valeur de cette cmdlet sur `Enabled` active la fonctionnalité si elle a été désactivée.

#### <a name="to-set-pua-protection-to-audit-mode"></a>Définir la protection contre les applications potentiellement indésirables (PUA) sur le mode audit

```PowerShell
Set-MpPreference -PUAProtection AuditMode
```

La définition de `AuditMode` détecte les applications potentiellement indésirables (PUA) sans les bloquer.

#### <a name="to-disable-pua-protection"></a>Pour désactiver la protection contre les applications potentiellement indésirables (PUA)

Nous vous recommandons de maintenir la protection contre les applications potentiellement indésirables (PUA) activé. Toutefois, vous pouvez la désactiver en utilisant la cmdlet suivante :

```PowerShell
Set-MpPreference -PUAProtection Disabled
```

La configuration de la valeur de cette cmdlet sur `Disabled` désactive la fonctionnalité si elle a été activée.

Pour plus d’informations, voir Utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter Antivirus Microsoft Defender et [cmdlets Defender pour les cloud](/powershell/module/defender/index).

## <a name="view-pua-events-using-powershell"></a>Afficher les événements d’applications potentiellement indésirables (PUA)

Les événements d’applications potentiellement indésirables (PUA) sont signalés dans l’Observateur d'événements Windows, mais pas dans Microsoft Endpoint Manager ou Intune. Vous pouvez également utiliser la cmdlet `Get-MpThreat` pour afficher les menaces traitées par l’Antivirus Windows Defender. Voici un exemple :

```console
CategoryID       : 27
DidThreatExecute : False
IsActive         : False
Resources        : {webfile:_q:\Builds\Dalton_Download_Manager_3223905758.exe|http://d18yzm5yb8map8.cloudfront.net/
                    fo4yue@kxqdw/Dalton_Download_Manager.exe|pid:14196,ProcessStart:132378130057195714}
RollupStatus     : 33
SchemaVersion    : 1.0.0.0
SeverityID       : 1
ThreatID         : 213927
ThreatName       : PUA:Win32/InstallCore
TypeID           : 0
PSComputerName   :
```

## <a name="get-email-notifications-about-pua-detections"></a>Obtenir des notifications par courrier électronique à propos des détections de la protection contre les applications potentiellement indésirables (PUA)

Vous pouvez activer les notifications par -email pour recevoir le courrier à propos de la détection des applications potentiellement indésirables (PUA).

Consultez [Résoudre des problèmes relatifs aux ID d’événement](troubleshoot-microsoft-defender-antivirus.md) pour plus de détails sur l’affichage des événements de l’Antivirus Windows Defender. Les événements des applications potentiellement indésirables (PUA) sont enregistrés sous l’ID d’événement **1160**.

## <a name="view-pua-events-using-advanced-hunting"></a>Afficher les événements des applications potentiellement indésirables (PUA) à l’aide du repérage avancé

Si vous utilisez [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md), vous pouvez utiliser une requête de repérage avancé pour afficher les événements des applications potentiellement indésirables (PUA). Voici un exemple de requête :

```console
DeviceEvents
| where ActionType == "AntivirusDetection"
| extend x = parse_json(AdditionalFields)
| project Timestamp, DeviceName, FolderPath, FileName, SHA256, ThreatName = tostring(x.ThreatName), WasExecutingWhileDetected = tostring(x.WasExecutingWhileDetected), WasRemediated = tostring(x.WasRemediated)
| where ThreatName startswith_cs 'PUA:'
```

Pour en savoir plus sur le repérage avancé, voir [Repérer de manière proactive les menaces grâce au repérage avancé](advanced-hunting-overview.md).

## <a name="exclude-files-from-pua-protection"></a>Exclure des fichiers de la protection contre les applications potentiellement indésirables (PUA)

Un fichier est parfois bloqué par erreur par la protection contre les applications potentiellement indésirables (PUA) ou une fonctionnalité d’une application potentiellement indésirable (PUA) est nécessaire pour effectuer une tâche. Dans ces cas, un fichier peut être ajouté à une liste d’exclusion.

Pour plus d’informations, voir [Configurer et valider des exclusions en fonction de l’extension de fichier et de l’emplacement du dossier](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Voir aussi

- [Protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md)
- [Configurer la protection comportementale, heuristique et en temps réel.](configure-protection-features-microsoft-defender-antivirus.md)
