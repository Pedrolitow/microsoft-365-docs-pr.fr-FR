---
title: Résolution des problèmes lors du passage à Microsoft Defender pour point de terminaison
description: Découvrez comment résoudre les problèmes lorsque vous passez à Microsoft Defender pour point de terminaison.
keywords: migration, Windows Defender, protection avancée des points de terminaison, antivirus, logiciel anti-programme malveillant, mode passif, mode actif, résolution des problèmes
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.topic: conceptual
ms.custom: migrationguides
ms.date: 05/20/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 9a1a95c927c4f659510c587d2bbc81ad4b9c1264
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621633"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>Résolution des problèmes lors du passage à Microsoft Defender pour point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Cet article fournit des informations de dépannage pour les administrateurs de sécurité qui rencontrent des problèmes lors du passage d’une solution de protection de point de terminaison non Microsoft à Microsoft Defender pour point de terminaison.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Antivirus Microsoft Defender est désinstallé sur Windows Server

Lorsque vous basculez vers Defender pour point de terminaison, vous commencez par votre protection antivirus/anti-programme malveillant non Microsoft en mode actif. Dans le cadre du processus d’installation, vous configurez Antivirus Microsoft Defender en mode passif. Parfois, votre solution antivirus/anti-programme malveillant non Microsoft peut empêcher Antivirus Microsoft Defender de s’exécuter sur Windows Server. En fait, il peut sembler que Antivirus Microsoft Defender a été supprimé de Windows Server.

Pour résoudre ce problème, procédez comme suit :

1. [Ajoutez Microsoft Defender pour point de terminaison à la liste d’exclusions](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
2. [Définissez manuellement Antivirus Microsoft Defender en mode passif](#set-microsoft-defender-antivirus-to-passive-mode-manually).

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>Ajouter Microsoft Defender pour point de terminaison à la liste d’exclusions

Certaines exclusions pour Defender pour point de terminaison doivent être définies dans votre solution de protection de point de terminaison non Microsoft existante. Veillez à ajouter les exclusions suivantes :

`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`

### <a name="set-microsoft-defender-antivirus-to-passive-mode-manually"></a>Définir manuellement Antivirus Microsoft Defender en mode passif

Sur Windows Server 2019, Windows Server, version 1803 ou ultérieure, Windows Server 2016 ou Windows Server 2012 R2, vous devez définir manuellement Antivirus Microsoft Defender en mode passif. Cette action permet d’éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur. Vous pouvez définir Antivirus Microsoft Defender en mode passif à l’aide de PowerShell, d’stratégie de groupe ou d’une clé de Registre.

Vous pouvez définir Antivirus Microsoft Defender en mode passif en définissant la clé de Registre suivante :

Chemin: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

Nom : `ForceDefenderPassiveMode`

Type: `REG_DWORD`

Valeur : `1`

> [!NOTE]
> Pour que le mode passif fonctionne sur des points de terminaison exécutant Windows Server 2016 et Windows Server 2012 R2, ces points de terminaison doivent être intégrés à l’aide des instructions fournies dans [Les serveurs de Windows d’intégration](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

Pour plus d’informations, consultez [Antivirus Microsoft Defender dans Windows](microsoft-defender-antivirus-windows.md).

## <a name="microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode"></a>Antivirus Microsoft Defender semble être bloqué en mode passif

Si Antivirus Microsoft Defender est bloqué en mode passif, définissez-le manuellement en mode actif en procédant comme suit :

1. Sur votre appareil Windows, ouvrez l’Éditeur du Registre en tant qu’administrateur.

2. Accédez à `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

3. Définissez ou définissez une **entrée REG_DWORD** appelée `ForceDefenderPassiveMode`, et définissez sa valeur sur `0`.

4. Redémarrez l’appareil.

> [!IMPORTANT]
> Si vous rencontrez toujours des difficultés pour définir Antivirus Microsoft Defender en mode actif après avoir suivi cette procédure, [contactez le support technique](../../admin/get-help-support.md).

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>Je ne parviens pas à réactiver Antivirus Microsoft Defender sur Windows Server 2016

Si vous utilisez une solution antivirus/anti-programme malveillant non Microsoft sur Windows Server 2016, il se peut que votre solution existante ait requis Antivirus Microsoft Defender être désactivée ou désinstallée. Vous pouvez utiliser[ l’utilitaire de protection contre les programmes malveillants Command-Line](command-line-arguments-microsoft-defender-antivirus.md) pour réactiver Antivirus Microsoft Defender sur Windows Server 2016.

1. En tant qu’administrateur local sur le serveur, ouvrez l’invite de commandes.

2. Exécutez la commande suivante : `MpCmdRun.exe -wdenable`

3. Redémarrez lʼappareil.

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité](microsoft-defender-antivirus-compatibility.md)

- [Outils et méthodes d’intégration pour les appareils Windows dans Defender pour point de terminaison](configure-endpoints.md) 
