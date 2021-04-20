---
title: Bloquer les applications potentiellement indésirables avec l'Antivirus Microsoft Defender
description: Activez la fonctionnalité antivirus d'application potentiellement indésirable (PUA) pour bloquer les logiciels indésirables tels que les logiciels adware.
keywords: pua, enable, unwanted software, unwanted apps, adware, browser toolbar, detect, block, Microsoft Defender Antivirus
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: detect
ms.sitesec: library
localization_priority: priority
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
audience: ITPro
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 8350db473580fd4d1728c3473742da5b63196c52
ms.sourcegitcommit: 55791ddab9ae484f76b30f0470eec8a4cf7b46d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2021
ms.locfileid: "51893576"
---
# <a name="detect-and-block-potentially-unwanted-applications"></a>Détecter et bloquer les applications potentiellement indésirables

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- [Microsoft Edge](/microsoft-edge/deploy/microsoft-edge)

Les applications potentiellement indésirables (PUA) sont une catégorie de logiciels qui peuvent ralentir votre ordinateur, afficher des publicités inattendues ou, au pire, installer d'autres logiciels qui peuvent être inattendus ou indésirables. PuA n'est pas considéré comme un virus, un programme malveillant ou un autre type de menace, mais il peut effectuer des actions sur les points de terminaison qui affectent négativement les performances ou l'utilisation des points de terminaison. Le terme *PUA* peut également faire référence à une application dont la réputation est médiocre, tel qu'évalué par Microsoft Defender for Endpoint, en raison de certains types de comportement indésirable.

Voici quelques exemples :

- **Logiciels publicitaires** qui affichent des publicités ou des promotions, y compris les logiciels qui insère des publicités dans des pages web.
- **Regroupement de logiciels** qui offrent l'installation d'autres logiciels qui ne sont pas signés numériquement par la même entité. En outre, les logiciels qui offrent d'installer d'autres logiciels éligibles en tant que PUA.
- **Logiciels de production** qui tentent activement d'éviter la détection par les produits de sécurité, y compris les logiciels qui se comportent différemment en présence des produits de sécurité.

> [!TIP]
> Pour obtenir plus d'exemples et une discussion sur les critères que nous utilisons pour étiqueter les applications pour attirer une attention particulière des fonctionnalités de sécurité, voir Comment Microsoft identifie les programmes malveillants et les [applications potentiellement indésirables.](/windows/security/threat-protection/intelligence/criteria)

Les applications potentiellement indésirables peuvent augmenter le risque que votre réseau soit infecté par des programmes malveillants réels, rendre l'identification des programmes malveillants plus difficile à identifier ou perdre des ressources informatiques lors de leur nettoyage. La protection PUA est prise en charge sur Windows 10, Windows Server 2019 et Windows Server 2016. Dans Windows 10 (version 2004 et ultérieure), l'Antivirus Microsoft Defender bloque par défaut les applications considérées comme des appareils PUA pour Entreprise (E5).

## <a name="microsoft-edge"></a>Microsoft Edge

Le [nouveau Microsoft Edge,](https://support.microsoft.com/microsoft-edge/get-to-know-microsoft-edge-3f4bb0ff-58de-2188-55c0-f560b7e20bea)basé sur Chromium, bloque les téléchargements d'applications potentiellement indésirables et les URL de ressources associées. Cette fonctionnalité est fournie via [Microsoft Defender SmartScreen.](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

### <a name="enable-pua-protection-in-chromium-based-microsoft-edge"></a>Activer la protection PUA dans Microsoft Edge basé sur Chromium

Bien que la protection des applications potentiellement indésirables dans Microsoft Edge (basée sur Chromium, version 80.0.361.50) soit désactivée par défaut, elle peut facilement être désactivée à partir du navigateur.

1. Dans votre navigateur Edge, sélectionnez les ellipses, puis choisissez **Paramètres.**

2. Sélectionnez **Confidentialité, recherche et services.**

3. Sous la section **Sécurité,** activer bloquer **les applications potentiellement indésirables.**

> [!TIP]
> Si vous exécutez Microsoft Edge (basé sur Chromium), vous pouvez explorer en toute sécurité la fonctionnalité de blocage d'URL de la protection PUA en la testant sur l'une de nos pages de démonstration [Microsoft Defender SmartScreen.](https://demo.smartscreen.msft.net/)

### <a name="blocking-urls-with-microsoft-defender-smartscreen"></a>Blocage des URL avec Microsoft Defender SmartScreen

Dans edge basé sur Chromium avec une protection PUA désactivée, Microsoft Defender SmartScreen vous protège contre les URL associées à PUA.

Les administrateurs de [sécurité](/DeployEdge/configure-microsoft-edge) peuvent configurer la façon dont Microsoft Edge et Microsoft Defender SmartScreen fonctionnent ensemble pour protéger les groupes d'utilisateurs contre les URL associées à puA. Plusieurs [paramètres de stratégie de groupe](/DeployEdge/microsoft-edge-policies#smartscreen-settings) sont explicitement disponibles pour Microsoft Defender SmartScreen, y compris un pour le blocage de [PUA.](/DeployEdge/microsoft-edge-policies#smartscreenpuaenabled) En outre, les administrateurs peuvent configurer [Microsoft Defender SmartScreen](/microsoft-edge/deploy/available-policies?source=docs#configure-windows-defender-smartscreen) dans son ensemble, à l'aide des paramètres de stratégie de groupe pour activer ou désactiver Microsoft Defender SmartScreen.

Bien que Microsoft Defender pour point de terminaison possède sa propre liste de blocage basée sur un jeu de données géré par Microsoft, vous pouvez personnaliser cette liste en fonction de vos propres renseignements sur les menaces. Si vous [créez et gérez des indicateurs](manage-indicators.md) dans le portail Microsoft Defender pour points de terminaison, Microsoft Defender SmartScreen respecte les nouveaux paramètres.

## <a name="microsoft-defender-antivirus"></a>Antivirus Microsoft Defender

La fonctionnalité de protection des applications potentiellement indésirables (PUA) de l'Antivirus Microsoft Defender peut détecter et bloquer les applications potentiellement indésirables sur les points de terminaison de votre réseau.

> [!NOTE]
> Cette fonctionnalité est disponible dans Windows 10, Windows Server 2019 et Windows Server 2016.

L'Antivirus Microsoft Defender bloque les fichiers PUA détectés et toute tentative de téléchargement, de déplacement, d'exécuter ou d'installation de ces fichiers. Les fichiers PUA bloqués sont ensuite mis en quarantaine. Lorsqu'un fichier PUA est détecté sur un point de terminaison, l'Antivirus Microsoft Defender envoie une notification à l'utilisateur (sauf si les[notifications](configure-notifications-microsoft-defender-antivirus.md)ont été désactivées) dans le même format que les autres détections de menaces. La notification est précédée pour `PUA:` indiquer son contenu.

La notification apparaît dans la liste de mise en [quarantaine habituelle dans l'application Sécurité Windows.](microsoft-defender-security-center-antivirus.md)

### <a name="configure-pua-protection-in-microsoft-defender-antivirus"></a>Configurer la protection PUA dans l'Antivirus Microsoft Defender

Vous pouvez activer la protection PUA avec [Microsoft Intune,](/mem/intune/protect/device-protect) [Microsoft Endpoint Configuration Manager,](/mem/configmgr/protect/deploy-use/endpoint-protection)la stratégie de groupe [ou](/azure/active-directory-domain-services/manage-group-policy)via des [cmdlets PowerShell.](/powershell/module/defender/?preserve-view=true&view=win10-ps)

Vous pouvez également utiliser la protection PUA en mode audit pour détecter les applications potentiellement indésirables sans les bloquer. Les détections sont capturées dans le journal des événements Windows.

> [!TIP]
> Visitez le site web de démonstration microsoft Defender pour point de terminaison [sur demo.wd.microsoft.com](https://demo.wd.microsoft.com/Page/UrlRep) pour vérifier que la fonctionnalité fonctionne et la voir en action.

La protection PUA en mode audit est utile si votre entreprise effectue une vérification interne de la conformité des logiciels et que vous souhaitez éviter les faux positifs.

#### <a name="use-intune-to-configure-pua-protection"></a>Utiliser Intune pour configurer la protection PUA

Pour plus d'informations, voir Configurer les paramètres de restriction d'appareil dans [Microsoft Intune](/intune/device-restrictions-configure) et l'Antivirus Microsoft Defender pour [Windows 10 dans Intune.](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

#### <a name="use-configuration-manager-to-configure-pua-protection"></a>Utiliser Configuration Manager pour configurer la protection PUA

La protection PUA est activée par défaut dans Microsoft Endpoint Manager (Current Branch).

Découvrez comment créer et déployer des stratégies de logiciel [anti-programme](/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) malveillant : paramètres d'analyse programmés pour plus d'informations sur la configuration de Microsoft Endpoint Manager (Current Branch).

For System Center 2012 Configuration Manager, see [How to Deploy Potentially Unwanted Application Protection Policy for Endpoint Protection in Configuration Manager](/previous-versions/system-center/system-center-2012-R2/hh508770(v=technet.10)#BKMK_PUA).

> [!NOTE]
> Les événements PUA bloqués par l'Antivirus Microsoft Defender sont signalés dans l'Observateur d'événements Windows et non dans Microsoft Endpoint Configuration Manager.

#### <a name="use-group-policy-to-configure-pua-protection"></a>Utiliser une stratégie de groupe pour configurer la protection PUA

1. Télécharger et installer des modèles d'administration (.admx) pour la mise à jour [d'octobre 2020 de Windows 10 (20H2)](https://www.microsoft.com/download/details.aspx?id=102157)

2. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

3. Sélectionnez l'objet de stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier.**

4. Dans **l'Éditeur de gestion des stratégies de** groupe, sélectionnez **Configuration** ordinateur et sélectionnez **Modèles d'administration.**

5. Développez l'arborescence **des composants Windows**  >  **de l'Antivirus Microsoft Defender.**

6. Double-cliquez **sur Configurer la détection pour les applications potentiellement indésirables.**

7. Sélectionnez **Activé pour** activer la protection PUA.

8. Dans **Options,** **sélectionnez Bloquer** pour bloquer les applications potentiellement indésirables, ou sélectionnez **Mode Audit** pour tester le fonctionnement du paramètre dans votre environnement. Sélectionnez **OK**.

9. Déployez votre objet de stratégie de groupe comme vous le faites généralement.

#### <a name="use-powershell-cmdlets-to-configure-pua-protection"></a>Utiliser les cmdlets PowerShell pour configurer la protection PUA

##### <a name="to-enable-pua-protection"></a>Pour activer la protection PUA

```PowerShell
Set-MpPreference -PUAProtection Enabled
```

Définir la valeur de cette cmdlet pour `Enabled` qu'elle allume la fonctionnalité si elle a été désactivée.

##### <a name="to-set-pua-protection-to-audit-mode"></a>Pour définir la protection PUA en mode audit

```PowerShell
Set-MpPreference -PUAProtection AuditMode
```

Le `AuditMode` paramètre détecte les puAs sans les bloquer.

##### <a name="to-disable-pua-protection"></a>Pour désactiver la protection PUA

Nous vous recommandons de maintenir la protection PUA allumée. Toutefois, vous pouvez la désactiver à l'aide de l'cmdlet suivante :

```PowerShell
Set-MpPreference -PUAProtection Disabled
```

La définition de la valeur de cette cmdlet pour la mettre hors de la fonctionnalité si `Disabled` elle a été activée.

Pour [plus d'informations](use-powershell-cmdlets-microsoft-defender-antivirus.md) sur l'utilisation de PowerShell avec l'Antivirus Microsoft Defender, voir les [cmdlets](/powershell/module/defender/index) Utiliser PowerShell pour configurer et exécuter l'Antivirus Microsoft Defender.

## <a name="view-pua-events"></a>Afficher les événements PUA

Les événements PUA sont signalés dans l'Observateur d'événements Windows, mais pas dans Microsoft Endpoint Manager ou dans Intune. Vous pouvez également utiliser la cmdlet pour afficher les menaces gérées par `Get-MpThreat` l'Antivirus Microsoft Defender. Voici un exemple :

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

Vous pouvez activer les notifications par courrier électronique pour recevoir des messages sur les détections PUA.

Pour [plus d'informations](troubleshoot-microsoft-defender-antivirus.md) sur l'affichage des événements de l'Antivirus Microsoft Defender, voir Les ID d'événement de résolution des problèmes. Les événements PUA sont enregistrés sous l'ID **d'événement 1160**.

Si vous utilisez Microsoft Defender pour le point de terminaison, vous pouvez utiliser une requête de chasse avancée pour afficher les événements PUA. Voici un exemple de requête :

```console
DeviceEvents
| where ActionType == "AntivirusDetection"
| extend x = parse_json(AdditionalFields)
| evaluate bag_unpack(x)
| where ThreatName startswith_cs 'PUA:'
| project Timestamp, DeviceName, FolderPath, FileName, SHA256, ThreatName, WasExecutingWhileDetected, WasRemediated
```

## <a name="excluding-files"></a>Exclusion de fichiers

Parfois, un fichier est bloqué par erreur par la protection PUA ou une fonctionnalité d'une PUA est nécessaire pour effectuer une tâche. Dans ce cas, un fichier peut être ajouté à une liste d'exclusions.

Pour plus d'informations, voir Configurer et valider des exclusions en fonction de [l'extension de fichier et de l'emplacement du dossier.](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

## <a name="see-also"></a>Voir aussi

- [Protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md)
- [Configurer la protection comportementale, heuristique et en temps réel.](configure-protection-features-microsoft-defender-antivirus.md)