---
title: Microsoft Defender hors ligne dans Windows
description: Vous pouvez utiliser Microsoft Defender hors ligne directement à partir de l’application Antivirus Windows Defender’application. Vous pouvez également gérer la façon dont elle est déployée dans votre réseau.
keywords: analyse, defender, hors connexion
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 23b6553970ed2c6de3128fe707e633374649024e
ms.sourcegitcommit: 2e05865beeb2051fd9ece212a46179310b946a46
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2021
ms.locfileid: "61148759"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>Exécuter et examiner les résultats d’une analyse en mode Microsoft Defender hors ligne

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Microsoft Defender hors ligne est un outil d’analyse anti-programme malveillant qui vous permet de démarrer et d’exécuter une analyse à partir d’un environnement approuvé. L’analyse s’exécute en dehors du noyau Windows normal afin qu’elle puisse cibler les programmes malveillants qui tentent de contourner l’shell Windows, tels que les virus et rootkits qui infectent ou contournent l’enregistrement de démarrage maître (MBR).

Vous pouvez utiliser Microsoft Defender hors ligne si vous suspectez une infection par un programme malveillant ou si vous souhaitez confirmer un nettoyage complet du point de terminaison après une attaque par programme malveillant.

Dans Windows 10 et Windows 11, Microsoft Defender hors ligne peut être exécuté en un clic directement à partir de [l Sécurité Windows applicer.](microsoft-defender-security-center-antivirus.md) Dans les versions précédentes de Windows, un utilisateur devait installer Microsoft Defender hors ligne sur un support de démarrage, redémarrer le point de terminaison et charger le support de démarrage.

## <a name="prerequisites-and-requirements"></a>conditions préalables et conditions requises

Microsoft Defender hors ligne dans Windows 10 et Windows 11 a la même configuration matérielle requise que Windows 10.

Pour plus d’informations sur Windows 10 et Windows 11 requises, consultez les rubriques suivantes :

- [Configuration matérielle minimum requise](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)

- [Recommandations relatives au composant matériel](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender hors ligne n’est pas pris en charge sur les ordinateurs ARM processeurs, ou sur Windows unités de conservation des stocks du serveur.

Pour exécuter Microsoft Defender hors ligne à partir du point de terminaison, l’utilisateur doit être connecté avec des privilèges d’administrateur.

## <a name="microsoft-defender-offline-updates"></a>Microsoft Defender hors ligne mises à jour

Microsoft Defender hors ligne utilise les mises à jour de protection les plus récentes disponibles sur le point de terminaison ; elle est mise à jour chaque fois que Antivirus Windows Defender est mis à jour.

> [!NOTE]
> Avant d’exécution d’une analyse hors connexion, vous devez essayer de mettre à jour la protection de l’Antivirus Microsoft Defender. Vous pouvez forcer une mise à jour à l’aide de la stratégie de groupe ou, toutefois, vous déployez normalement les mises à jour sur les points de terminaison, ou vous pouvez télécharger et installer manuellement les dernières mises à jour de protection à partir du [Centre de protection Microsoft contre les programmes malveillants](https://www.microsoft.com/security/portal/definitions/adl.aspx).

Pour plus [d’informations, consultez](manage-protection-updates-microsoft-defender-antivirus.md) la rubrique Gérer Antivirus Microsoft Defender d’informations sur la sécurité.

## <a name="usage-scenarios"></a>Scénarios d'utilisation

Dans Windows 10 version 1607, vous pouvez forcer manuellement une analyse hors connexion. Sinon, si Windows Defender détermine que Microsoft Defender hors ligne doit s’exécuter, il invite l’utilisateur sur le point de terminaison.

La nécessité d’effectuer une analyse hors connexion sera également Microsoft Endpoint Manager si vous l’utilisez pour gérer vos points de terminaison.

L’invite peut se produire via une notification, semblable à ce qui suit :

:::image type="content" source="../../media/notification.png" alt-text="Notification d’Microsoft Defender hors ligne.":::

L’utilisateur est également informé dans le client Windows Defender client.

Dans Configuration Manager, vous pouvez identifier l’état des points de terminaison en naviguant vers Monitoring **> Overview > Security > Endpoint Protection Status > System Center Endpoint Protection Status**.

Microsoft Defender hors ligne analyses sont indiquées sous  l’état de correction des programmes malveillants comme **analyse hors connexion requise.**

:::image type="content" source="../../media/sccm-wdo.png" alt-text="Microsoft Defender hors ligne’analyse est requise.":::

## <a name="configure-notifications"></a>Configurer les notifications

Microsoft Defender hors ligne notifications sont configurées dans le même paramètre de stratégie que les autres notifications de Microsoft Defender AV.

Pour plus d’informations sur les notifications Windows Defender, consultez la rubrique Configurer les notifications qui apparaissent [sur les points de terminaison.](configure-notifications-microsoft-defender-antivirus.md)

## <a name="run-a-scan"></a>Effectuer une analyse

> [!IMPORTANT]
> Avant d’utiliser Microsoft Defender hors ligne, veillez à enregistrer les fichiers et à arrêter les programmes en cours d’exécution. L Microsoft Defender hors ligne’analyse prend environ 15 minutes. Il redémarre le point de terminaison une fois l’analyse terminée. L’analyse est effectuée en dehors de l’environnement Windows d’exploitation habituel. L’interface utilisateur s’affiche différemment d’une analyse normale effectuée par Windows Defender. Une fois l’analyse terminée, le point de terminaison est redémarré et Windows charge normale.

Vous pouvez exécuter une analyse Microsoft Defender hors ligne suivante :

- PowerShell
- WMI (Windows Management Instrumentation)
- Application Sécurité Windows de messagerie



### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>Utiliser les cmdlets PowerShell pour exécuter une analyse hors connexion

Utilisez les cmdlets suivantes :

```PowerShell
Start-MpWDOScan
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter les [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Antivirus Defender.

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>Utiliser Windows Management Instruction (WMI) pour exécuter une analyse hors connexion

Utilisez la [**MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour exécuter une analyse hors connexion.

L’extrait de script WMI suivant exécute immédiatement une analyse Microsoft Defender hors ligne, ce qui entraîne le redémarrage du point de terminaison, l’analyse hors connexion, puis le redémarrage et le démarrage dans Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

Pour plus d’informations, voir les informations suivantes :

- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>Utiliser l’application Windows Defender security pour exécuter une analyse hors connexion

1. Ouvrez l Sécurité Windows application en cliquant sur l’icône de bouclier dans la barre des tâches ou en recherchant Defender pour cloud dans le menu **Démarrer.**

2. Cliquez sur la **vignette & protection** contre les virus contre les menaces (ou sur l’icône de bouclier dans la barre de menus de gauche), puis sur l’étiquette **d’analyse** avancée :

3. Sélectionnez **Microsoft Defender hors ligne scan,** puis cliquez **sur Analyser maintenant.**

    > [!NOTE]
    > Dans Windows 10 version 1607, l’analyse hors connexion peut  être exécuté à partir du Windows Defender de sécurité Windows Paramètres Update & ou à partir du \>  \>  client Windows Defender.

## <a name="review-scan-results"></a>Passer en revue les résultats de l’analyse

Microsoft Defender hors ligne résultats de l’analyse sont répertoriés dans la section Historique [d’analyse de l Sécurité Windows app.](microsoft-defender-security-center-antivirus.md)

## <a name="related-articles"></a>Articles connexes

- [Personnaliser, lancer et examiner les résultats des analyses et des corrections](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
