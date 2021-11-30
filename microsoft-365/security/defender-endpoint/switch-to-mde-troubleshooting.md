---
title: Résolution des problèmes lors du basculement vers Microsoft Defender pour point de terminaison
description: Découvrez comment résoudre les problèmes lorsque vous basculez vers Microsoft Defender pour le point de terminaison.
keywords: migration, windows defender, protection avancée des points de terminaison, antivirus, logiciel anti-programme malveillant, mode passif, mode actif, résolution des problèmes
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
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-overview
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.topic: conceptual
ms.custom: migrationguides
ms.date: 11/30/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: bbde6e79f35bf69b29d589186054bc072124d1ea
ms.sourcegitcommit: aacf895ba20ecec4312a447ff4432e257e41edee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2021
ms.locfileid: "61234530"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>Résolution des problèmes lors du basculement vers Microsoft Defender pour point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Cet article fournit des informations de dépannage pour les administrateurs de sécurité qui rencontrent des problèmes lors du passage d’une solution de protection de point de terminaison non-Microsoft à Microsoft Defender pour point de terminaison.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Antivirus Microsoft Defender est désinstallé sur Windows Server

Lorsque vous basculez vers Defender pour le point de terminaison, vous commencez par votre protection antivirus/anti-programme malveillant non-Microsoft en mode actif. Dans le cadre du processus d’installation, vous configurez Antivirus Microsoft Defender en mode passif. Parfois, votre solution antivirus/anti-programme malveillant non Microsoft peut empêcher l Antivirus Microsoft Defender’exécution sur Windows Server. En fait, il peut ressembler à Antivirus Microsoft Defender a été supprimé de Windows Server.

Pour résoudre ce problème, prenez les mesures suivantes :

1. [Définissez la clé de Registre DisableAntiSpyware sur false](#set-the-disableantispyware-registry-key-to-false).
2. [Ajoutez Microsoft Defender pour le point de terminaison à la liste d’exclusions.](#add-microsoft-defender-for-endpoint-to-the-exclusion-list)
3. [Définissez Antivirus Microsoft Defender le mode passif manuellement.](#set-microsoft-defender-antivirus-to-passive-mode-manually)

### <a name="set-the-disableantispyware-registry-key-to-false"></a>Définir la clé de Registre DisableAntiSpyware sur false

La clé de Registre [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) a été utilisée dans le passé pour désactiver Antivirus Microsoft Defender et déployer un autre produit antivirus, tel que Mc Symantec, etc. **En règle générale,** vous ne devez pas avoir cette clé de Registre sur  vos appareils et points de terminaison Windows ; toutefois, si vous avez configuré, voici comment définir sa valeur sur `DisableAntiSpyware` false :

1. Sur votre Windows server, ouvrez l’Éditeur du Registre.

2. Accédez à `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

3. Dans ce dossier, recherchez une entrée DWORD appelée **DisableAntiSpyware**.
   - Si vous ne voyez pas cette entrée, vous êtes prêt.
   - Si vous voyez **DisableAntiSpyware,** procédez à l’étape 4.

4. Cliquez avec le bouton droit sur la DWORD DisableAntiSpyware, puis choisissez **Modifier**.

5. Définissez la valeur sur `0` . (Cette action définit la valeur de la clé de Registre sur *false*.)

> [!TIP]
> Pour en savoir plus sur cette clé de Registre, voir [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware).

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>Ajouter Microsoft Defender pour le point de terminaison à la liste d’exclusions

Certaines exclusions de Defender pour point de terminaison doivent être définies dans votre solution de protection de point de terminaison non Microsoft existante. Veillez à ajouter les exclusions suivantes :

`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`

### <a name="set-microsoft-defender-antivirus-to-passive-mode-manually"></a>Définir Antivirus Microsoft Defender mode passif manuellement

Sur Windows Server 2019, Windows Server, version 1803 ou plus récente, Windows Server 2016 ou Windows Server 2012 R2, vous devez définir Antivirus Microsoft Defender en mode passif manuellement. Cette action permet d’éviter les problèmes causés par l’installation de plusieurs produits antivirus sur un serveur. Vous pouvez définir Antivirus Microsoft Defender mode passif à l’aide de PowerShell, d’une stratégie de groupe ou d’une clé de Registre.

Vous pouvez définir Antivirus Microsoft Defender en mode passif en réglant la clé de Registre suivante :

Chemin d’accès : `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

Nom : `ForceDefenderPassiveMode`

Type : `REG_DWORD`

Valeur : `1`

> [!NOTE]
> Pour que le mode passif fonctionne sur les points de terminaison exécutant Windows Server 2016 et Windows Server 2012 R2, ces points de terminaison doivent être intégrés à l’aide des instructions des serveurs Windows [intégrés.](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016)

Pour plus d’informations, [voir Antivirus Microsoft Defender sur Windows Server.](microsoft-defender-antivirus-on-windows-server.md)

## <a name="i-am-having-trouble-reinstalling-microsoft-defender-antivirus-on-windows-server-2016"></a>J’ai des difficultés à réinstaller des Antivirus Microsoft Defender sur Windows Server 2016

Si vous utilisez une solution antivirus/anti-programme malveillant non Microsoft sur Windows Server 2016, il se peut que votre solution existante Antivirus Microsoft Defender soit désactivée ou désinstallée. Vous pouvez utiliser l’utilitaire Command-Line protection contre les programmes[ malveillants](command-line-arguments-microsoft-defender-antivirus.md) pour ré-activer Antivirus Microsoft Defender sur Windows Server 2016.

1. En tant qu’administrateur local sur le serveur, ouvrez l’invite de commandes.

2. Exécutez la commande suivante : `MpCmdRun.exe -wdenable`

3. Redémarrez lʼappareil.

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité](microsoft-defender-antivirus-compatibility.md)

- [Outils et méthodes d’intégration pour les Windows dans Defender for Endpoint](configure-endpoints.md) 