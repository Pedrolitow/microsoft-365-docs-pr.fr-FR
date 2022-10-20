---
title: Microsoft Defender hors connexion dans Windows
description: Vous pouvez utiliser Microsoft Defender hors connexion directement à partir de l’application antivirus Microsoft Defender. Vous pouvez également gérer la façon dont il est déployé sur votre réseau.
keywords: analyse, defender, hors connexion
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.date: 08/30/2022
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.topic: conceptual
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 8ab9082f907b4f4b732aa85e3deb2943d2bbd90d
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68623738"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>Exécuter et examiner les résultats d’une analyse en mode Microsoft Defender hors ligne

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Microsoft Defender hors connexion est un outil d’analyse anti-programme malveillant qui vous permet de démarrer et d’exécuter une analyse à partir d’un environnement approuvé. L’analyse s’exécute en dehors du noyau Windows normal afin de cibler les programmes malveillants qui tentent de contourner l’interpréteur de commandes Windows, tels que les virus et les rootkits qui infectent ou remplacent l’enregistrement de démarrage maître (MBR).

Vous pouvez utiliser Microsoft Defender hors connexion si vous soupçonnez une infection par un programme malveillant, ou si vous souhaitez confirmer un nettoyage complet du point de terminaison après une flambée de programmes malveillants.

Dans Windows 10 et Windows 11, Microsoft Defender hors connexion peut être exécuté en un clic directement à partir de [l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md). Dans les versions précédentes de Windows, un utilisateur devait installer Microsoft Defender hors connexion sur un média démarrable, redémarrer le point de terminaison et charger le média de démarrage.

## <a name="prerequisites-and-requirements"></a>conditions préalables et exigences

Microsoft Defender hors connexion dans Windows 10 et Windows 11 a les mêmes exigences matérielles que Windows 10.

Pour plus d’informations sur les exigences Windows 10 et Windows 11, consultez les rubriques suivantes :

- [Configuration matérielle minimum requise](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)
- [Recommandations relatives au composant matériel](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender hors connexion n’est pas pris en charge sur les machines avec processeurs ARM ou sur les unités de conservation des stocks Windows Server.

Pour exécuter Microsoft Defender hors connexion à partir du point de terminaison, l’utilisateur doit être connecté avec des privilèges d’administrateur.

## <a name="microsoft-defender-offline-updates"></a>Microsoft Defender mises à jour hors connexion

Microsoft Defender hors connexion utilise les dernières mises à jour de protection disponibles sur le point de terminaison ; elle est mise à jour chaque fois que Microsoft Defender Antivirus est mis à jour.

> [!NOTE]
> Avant d’exécuter une analyse hors connexion, vous devez tenter de mettre à jour Microsoft Defender protection antivirus. Vous pouvez soit forcer une mise à jour avec stratégie de groupe, soit déployer normalement des mises à jour sur des points de terminaison, ou télécharger et installer manuellement les dernières mises à jour de protection à partir du [Centre de protection Microsoft contre les programmes malveillants](https://www.microsoft.com/security/portal/definitions/adl.aspx).

Pour plus d’informations, consultez la rubrique [Gérer les mises à jour du renseignement de sécurité antivirus Microsoft Defender](manage-protection-updates-microsoft-defender-antivirus.md) Antivirus.

## <a name="usage-scenarios"></a>Scénarios d'utilisation

Dans Windows 10, version 1607, vous pouvez forcer manuellement une analyse hors connexion. Sinon, si Windows Defender détermine que Microsoft Defender hors connexion doit s’exécuter, il invite l’utilisateur sur le point de terminaison.

La nécessité d’effectuer une analyse hors connexion est également indiquée dans Microsoft Endpoint Manager si vous l’utilisez pour gérer vos points de terminaison.

L’invite peut se produire via une notification, comme suit :

:::image type="content" source="../../media/notification.png" alt-text="Notification d’exécution Microsoft Defender hors connexion" lightbox="../../media/notification.png":::

L’utilisateur est également averti au sein du client Windows Defender.

Dans Configuration Manager, vous pouvez identifier l’état des points de terminaison en accédant à **Monitoring > Overview > Security > Endpoint Protection Status > System Center Endpoint Protection Status**.

Microsoft Defender les analyses hors connexion sont indiquées sous **l’état de correction des programmes malveillants** en tant **qu’analyse hors connexion requise**.

:::image type="content" source="../../media/sccm-wdo.png" alt-text="Indicateur pour une analyse de Microsoft Defender hors connexion" lightbox="../../media/sccm-wdo.png":::

## <a name="configure-notifications"></a>Configurer les notifications

Microsoft Defender notifications hors connexion sont configurées dans le même paramètre de stratégie que les autres notifications antivirus Microsoft Defender.

Pour plus d’informations sur les notifications dans Windows Defender, consultez la rubrique [Configurer les notifications qui s’affichent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md).

## <a name="run-a-scan"></a>Effectuer une analyse

> [!IMPORTANT]
> Avant d’utiliser Microsoft Defender hors connexion, veillez à enregistrer tous les fichiers et à arrêter les programmes en cours d’exécution. L’exécution de l’analyse hors connexion Microsoft Defender prend environ 15 minutes. Il redémarre le point de terminaison une fois l’analyse terminée. L’analyse est effectuée en dehors de l’environnement d’exploitation Windows habituel. L’interface utilisateur s’affiche différemment d’une analyse normale effectuée par Windows Defender. Une fois l’analyse terminée, le point de terminaison est redémarré et Windows se charge normalement.

Vous pouvez exécuter une analyse hors connexion Microsoft Defender avec les éléments suivants :

- PowerShell
- WMI (Windows Management Instrumentation)
- Application Sécurité Windows

### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>Utiliser des applets de commande PowerShell pour exécuter une analyse hors connexion

Utilisez les applets de commande suivantes :

```PowerShell
Start-MpWDOScan
```

Pour plus d’informations sur l’utilisation de PowerShell avec Microsoft Defender Antivirus, consultez Utiliser les applets de commande [PowerShell pour configurer et exécuter Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) antivirus et [Defender Antivirus](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>Utiliser WMI (Windows Management Instruction) pour exécuter une analyse hors connexion

Utilisez la classe [**MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour exécuter une analyse hors connexion.

L’extrait de code de script WMI suivant exécute immédiatement une analyse hors connexion Microsoft Defender, ce qui entraîne le redémarrage du point de terminaison, l’exécution de l’analyse hors connexion, puis le redémarrage et le démarrage dans Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

Pour plus d’informations, consultez les rubriques suivantes :

- [WINDOWS DEFENDER API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>Utiliser l’application Windows Defender Security pour exécuter une analyse hors connexion

1. Ouvrez l’application Sécurité Windows en cliquant sur l’icône du bouclier dans la barre des tâches ou en recherchant **Defender pour cloud** dans le menu démarrer.

2. Cliquez sur la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche), puis sur l’étiquette **d’analyse avancée** :

3. Sélectionnez **Microsoft Defender analyse hors connexion**, puis cliquez sur **Analyser maintenant**.

    > [!NOTE]
    > Dans Windows 10, version 1607, l’analyse hors connexion peut être exécutée sous windows **Settings** \> **Update &** **Windows Defender** de sécurité \> ou à partir du client Windows Defender.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

### <a name="where-can-i-find-the-scan-results"></a>Où puis-je trouver les résultats de l’analyse ?

Pour afficher les résultats de l’analyse hors connexion Microsoft Defender :

1. Sélectionnez **Démarrer**, puis sélectionnez Mise à jour **des paramètres**  > **& Sécurité**  >  **Sécurité Windows**  >  **Virus & protection contre les menaces**.

2. Dans l’écran **Virus & protection contre les menaces** , sous **Menaces actuelles**, sélectionnez **Options d’analyse**, puis historique **de protection**.

## <a name="related-articles"></a>Articles connexes

- [Personnaliser, lancer et examiner les résultats des analyses et de la correction](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
