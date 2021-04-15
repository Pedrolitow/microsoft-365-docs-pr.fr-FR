---
title: Microsoft Defender hors ligne dans Windows 10
description: Vous pouvez utiliser Microsoft Defender hors ligne directement à partir de l Windows Defender antivirus. Vous pouvez également gérer la façon dont elle est déployée dans votre réseau.
keywords: analyse, defender, hors connexion
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 3b1e7e70c6ca217d3ad8859c1493598d71054f84
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51765334"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>Exécuter et passer en revue les résultats d'une analyse Microsoft Defender hors ligne

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Microsoft Defender hors ligne est un outil d'analyse anti-programme malveillant qui vous permet de démarrer et d'exécuter une analyse à partir d'un environnement approuvé. L'analyse s'exécute en dehors du noyau Windows normal afin qu'elle puisse cibler les programmes malveillants qui tentent de contourner l'shell Windows, tels que les virus et rootkits qui infectent ou éviennent l'enregistrement de démarrage maître (MBR).

Vous pouvez utiliser Microsoft Defender hors ligne si vous suspectez une infection par un programme malveillant ou si vous souhaitez confirmer un nettoyage complet du point de terminaison après une attaque par programme malveillant.

Dans Windows 10, Microsoft Defender hors ligne peut être exécuté en un clic directement à partir de [l'application Sécurité Windows.](microsoft-defender-security-center-antivirus.md) Dans les versions précédentes de Windows, un utilisateur devait installer Microsoft Defender hors ligne sur un support démarrable, redémarrer le point de terminaison et charger le support démarrable.

## <a name="prerequisites-and-requirements"></a>conditions préalables et conditions requises

Microsoft Defender hors ligne dans Windows 10 présente la même configuration matérielle requise que Windows 10. 

Pour plus d'informations sur les conditions requises pour Windows 10, consultez les rubriques suivantes :

- [Configuration matérielle minimale requise](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)

- [Recommandations en matière de composants matériels](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender hors ligne n'est pas pris en charge sur les ordinateurs ARM processeurs ou sur les unités de conservation de stock Windows Server.

Pour exécuter Microsoft Defender hors ligne à partir du point de terminaison, l'utilisateur doit être connecté avec des privilèges d'administrateur.
 
## <a name="microsoft-defender-offline-updates"></a>Mises à jour De Microsoft Defender hors ligne

Microsoft Defender hors ligne utilise les dernières mises à jour de protection disponibles sur le point de terminaison . Il est mis à jour chaque fois Windows Defender antivirus est mis à jour. 

> [!NOTE]
> Avant d'exécution d'une analyse hors connexion, vous devez essayer de mettre à jour la protection de l'Antivirus Microsoft Defender. Vous pouvez forcer une mise à jour à l'aide d'une stratégie de groupe ou toutefois déployer normalement des mises à jour sur les points de terminaison, ou vous pouvez télécharger et installer manuellement les dernières mises à jour de la protection à partir du [Centre de protection Microsoft contre les programmes malveillants](https://www.microsoft.com/security/portal/definitions/adl.aspx).

Pour plus d'informations, consultez la rubrique Gérer les mises à jour de [l'Antivirus Security de Microsoft Defender.](manage-protection-updates-microsoft-defender-antivirus.md)

## <a name="usage-scenarios"></a>Scénarios d'utilisation

Dans Windows 10, version 1607, vous pouvez forcer manuellement une analyse hors connexion. Sinon, si Windows Defender que Microsoft Defender hors ligne doit s'exécuter, il invite l'utilisateur sur le point de terminaison. 

La nécessité d'effectuer une analyse hors connexion sera également révélée dans Microsoft Endpoint Manager si vous l'utilisez pour gérer vos points de terminaison.

L'invite peut se produire via une notification, semblable à ce qui suit :

![Notification Windows indiquant la nécessité d'exécuter Microsoft Defender hors ligne](images/defender/notification.png)

L'utilisateur est également informé dans le client Windows Defender client.

Dans Configuration Manager, vous pouvez identifier l'état des points de terminaison en naviguant vers Surveillance > Vue d'ensemble > Sécurité **> Endpoint Protection Status > System Center Endpoint Protection Status**. 

Les analyses Microsoft Defender hors  ligne sont indiquées sous l'état de correction des programmes malveillants comme **analyse hors connexion requise.**

![Microsoft Endpoint Manager indiquant qu'une analyse Microsoft Defender hors ligne est requise](images/defender/sccm-wdo.png)

## <a name="configure-notifications"></a>Configurer les notifications

Les notifications Microsoft Defender hors ligne sont configurées dans le même paramètre de stratégie que les autres notifications De l'Antivirus Microsoft Defender.

Pour plus d'informations sur les notifications Windows Defender, consultez la rubrique Configurer les [notifications](configure-notifications-microsoft-defender-antivirus.md) qui apparaissent sur les points de terminaison.

## <a name="run-a-scan"></a>Effectuer une analyse 

> [!IMPORTANT]
> Avant d'utiliser Microsoft Defender hors ligne, veillez à enregistrer les fichiers et à arrêter les programmes en cours d'exécution. L'analyse Microsoft Defender hors ligne prend environ 15 minutes. Il redémarre le point de terminaison une fois l'analyse terminée. L'analyse est effectuée en dehors de l'environnement d'exploitation Windows habituel. L'interface utilisateur s'affiche différemment d'une analyse normale effectuée par Windows Defender. Une fois l'analyse terminée, le point de terminaison est redémarré et Windows se charge normalement.

Vous pouvez exécuter une analyse Microsoft Defender hors ligne avec les fonctionnalités suivantes :

- PowerShell
- WMI (Windows Management Instrumentation)
- Application Sécurité Windows



### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>Utiliser les cmdlets PowerShell pour exécuter une analyse hors connexion

Utilisez les cmdlets suivantes :

```PowerShell
Start-MpWDOScan
```

Pour [plus d'informations](use-powershell-cmdlets-microsoft-defender-antivirus.md) sur l'utilisation de PowerShell avec l'Antivirus Microsoft Defender, voir les [cmdlets](/powershell/module/defender/) Utiliser PowerShell pour configurer et exécuter l'Antivirus Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>Utiliser Windows Management Instruction (WMI) pour exécuter une analyse hors connexion

Utilisez la [**MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour exécuter une analyse hors connexion.

L'extrait de script WMI suivant exécute immédiatement une analyse Microsoft Defender hors ligne, ce qui entraîne le redémarrage du point de terminaison, l'analyse hors connexion, puis le redémarrage et le démarrage dans Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start 
```

Pour plus d'informations, voir les informations suivantes :
- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)


### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>Utiliser l'application Windows Defender security pour exécuter une analyse hors connexion

1. Ouvrez l'application Sécurité Windows en cliquant sur l'icône de bouclier dans la barre des tâches ou en recherchant Defender dans le menu **Démarrer.**

2. Cliquez sur la **vignette & protection** antivirus contre les menaces (ou sur l'icône de bouclier dans la barre de menus de gauche), puis sur l'étiquette **d'analyse** avancée :
    
3. Sélectionnez **Analyse Microsoft Defender hors ligne,** puis cliquez sur Analyser **maintenant.**

    > [!NOTE]
    > Dans Windows 10, version 1607, l'analyse hors connexion peut être exécuté à partir de la Windows Defender de sécurité de la mise à jour des paramètre **& s Windows** ou à partir du  >    >   client Windows Defender.


## <a name="review-scan-results"></a>Passer en revue les résultats de l'analyse

Les résultats de l'analyse Microsoft Defender hors ligne sont répertoriés dans la section Historique d'analyse [de l'application Sécurité Windows.](microsoft-defender-security-center-antivirus.md) 


## <a name="related-articles"></a>Articles connexes

- [Personnaliser, lancer et examiner les résultats des analyses et des corrections](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)