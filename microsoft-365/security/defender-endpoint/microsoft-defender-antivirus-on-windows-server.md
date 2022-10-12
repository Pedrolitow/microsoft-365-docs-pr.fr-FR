---
title: Antivirus Microsoft Defender sur Windows Server
description: Découvrez comment activer et configurer Microsoft Defender Antivirus sur Windows Server 2016, Windows Server 2019 et Windows Server 2022.
keywords: windows defender, server, scep, system center endpoint protection, server 2016, Current Branch, server 2012
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.topic: article
ms.date: 10/10/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 74d56fe8f7c2ceeee23017a7932cd642438a3a69
ms.sourcegitcommit: 8d3c027592a638f411f87d89772dd3d39e92aab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68536189"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Antivirus Microsoft Defender sur Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Antivirus est disponible dans les éditions/versions suivantes de Windows Server :

- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 ou ultérieure
- Windows Server 2016
- Windows Server 2012 R2 (nécessite Microsoft Defender pour point de terminaison)

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Configuration de Microsoft Defender Antivirus sur Windows Server

Le processus de configuration et d’exécution de Microsoft Defender Antivirus sur Windows Server comprend les étapes suivantes :

1. [Activez l’interface](#enable-the-user-interface-on-windows-server).
2. [Installez Microsoft Defender Antivirus](#install-microsoft-defender-antivirus-on-windows-server).
3. [Vérifiez Microsoft Defender antivirus est en cours d’exécution](#verify-microsoft-defender-antivirus-is-running).
4. [Mettez à jour votre renseignement de sécurité anti-programme malveillant](#update-antimalware-security-intelligence).
5. (Si nécessaire) [Envoyez des exemples](#submit-samples).
6. (Si nécessaire) [Configurez les exclusions automatiques](#configure-automatic-exclusions).
7. (Uniquement si nécessaire) [Définissez Windows Server en mode passif](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Activer l’interface utilisateur sur Windows Server

> [!IMPORTANT]
> Si vous utilisez Windows Server 2012 R2, consultez [Options pour installer Microsoft Defender pour point de terminaison](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

Par défaut, Microsoft Defender Antivirus est installé et fonctionnel sur Windows Server. Parfois, l’interface utilisateur (GUI) est installée par défaut. L’interface utilisateur graphique n’est pas obligatoire ; vous pouvez utiliser PowerShell, stratégie de groupe ou d’autres méthodes pour gérer Microsoft Defender Antivirus. Toutefois, de nombreuses organisations préfèrent utiliser l’interface graphique utilisateur pour Microsoft Defender Antivirus. Pour installer l’interface graphique utilisateur, utilisez l’une des procédures du tableau suivant :

| Procedure | Procédure |
|:---|:---|
| Activer l’interface graphique utilisateur à l’aide de l’Assistant Ajout de rôles et de fonctionnalités | 1. Consultez [Installer des rôles, des services de rôle et des fonctionnalités à l’aide de l’Assistant Ajout de rôles et de fonctionnalités](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard), et utilisez **l’Assistant Ajout de rôles et de fonctionnalités**. <br/><br/>2. Lorsque vous accédez à l’étape **Fonctionnalités** de l’Assistant, sous **Windows Defender Fonctionnalités**, sélectionnez l’interface **utilisateur utilisateur pour Windows Defender** option. |
| Activer l’interface graphique utilisateur à l’aide de PowerShell | 1. Sur votre serveur Windows Server, ouvrez Windows PowerShell en tant qu’administrateur. <br/><br/>2. Exécutez l’applet de commande PowerShell suivante : `Install-WindowsFeature -Name Windows-Defender-GUI` |

Pour plus d’informations, consultez [Prise en main avec PowerShell](/powershell/scripting/learn/ps101/01-getting-started).

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Installer Microsoft Defender Antivirus sur Windows Server

Si vous devez installer ou réinstaller Microsoft Defender Antivirus sur Windows Server, utilisez l’une des procédures du tableau suivant :

| Procedure | Procédure |
|:---|:---|
| Utiliser l’Assistant Ajout de rôles et de fonctionnalités pour installer Microsoft Defender Antivirus | 1. Consultez [Installer ou désinstaller des rôles, des services de rôle ou des fonctionnalités](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard), et utilisez l’Assistant **Ajout de rôles et de fonctionnalités**. <br/><br/>2. Lorsque vous accédez à l’étape **Fonctionnalités** de l’Assistant, sélectionnez l’option Microsoft Defender Antivirus. Sélectionnez également **l’interface graphique utilisateur pour Windows Defender** option. |
| Utiliser PowerShell pour installer Microsoft Defender Antivirus | 1. Sur votre serveur Windows Server, ouvrez Windows PowerShell en tant qu’administrateur. <br/><br/>2. Exécutez l’applet de commande PowerShell suivante : `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> Les messages d’événements pour le moteur de logiciel anti-programme malveillant inclus dans Microsoft Defender Antivirus se trouvent dans [Microsoft Defender événements antivirus](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Vérifier Microsoft Defender antivirus est en cours d’exécution

Une fois que vous avez installé (ou réinstallé) Microsoft Defender Antivirus, l’étape suivante consiste à vérifier qu’il est en cours d’exécution. Utilisez les applets de commande PowerShell dans le tableau suivant :

| Procedure | Applet de commande PowerShell |
|:---|:---|
| Vérifier que Microsoft Defender Antivirus est en cours d’exécution | `Get-Service -Name windefend` |
| Vérifier que la protection pare-feu est activée | `Get-Service -Name mpssvc` |

En guise d’alternative à PowerShell, vous pouvez utiliser l’invite de commandes pour vérifier que Microsoft Defender Antivirus est en cours d’exécution. Pour ce faire, exécutez la commande suivante à partir d’une invite de commandes :

```cmd
sc query Windefend
```

La `sc query` commande retourne des informations sur le service antivirus Microsoft Defender. Lorsque Microsoft Defender Antivirus est en cours d’exécution, la valeur s’affiche `STATE` `RUNNING`.

Pour afficher tous les services qui ne sont pas en cours d’exécution, exécutez l’applet de commande PowerShell suivante :

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Mettre à jour le renseignement de sécurité anti-programme malveillant

> [!IMPORTANT]
> À partir de [la plateforme version 4.18.2208.0 et ultérieure](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions) : si un serveur a été intégré à Microsoft Defender pour point de terminaison, le paramètre de stratégie de [groupe](configure-endpoints-gp.md#update-endpoint-protection-configuration) « Désactiver Windows Defender » ne désactive plus complètement Windows Defender Antivirus activé Windows Server 2012 R2 et versions ultérieures. Au lieu de cela, il le place en mode passif. En outre, la fonctionnalité [de protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) permet de basculer en mode actif, mais pas en mode passif.
> 
> - Si « Désactiver Windows Defender » est déjà en place avant l’intégration à Microsoft Defender pour point de terminaison, aucune modification n’est apportée et l’antivirus Defender reste désactivé.
> - Pour basculer l’antivirus Defender en mode passif, même s’il a été désactivé avant l’intégration, vous pouvez appliquer la [configuration ForceDefenderPassiveMode](switch-to-mde-phase-2.md#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) avec la valeur .`1` Pour la placer en mode actif, basculez vers cette valeur à la `0` place.
> 
> Notez la logique modifiée pour `ForceDefenderPassiveMode` le moment où la protection contre les falsifications est activée : une fois que Microsoft Defender Antivirus est activé en mode actif, la protection contre les falsifications l’empêche de revenir en mode passif, même lorsque `ForceDefenderPassiveMode` la valeur est définie `1`sur .

Pour obtenir vos mises à jour régulières du renseignement de sécurité, le service Windows Update doit être en cours d’exécution. Si vous utilisez un service de gestion des mises à jour, comme Windows Server Update Services (WSUS), assurez-vous que les mises à jour pour Microsoft Defender Antivirus Security Intelligence sont approuvées pour les ordinateurs que vous gérez.

Par défaut, Windows Update ne télécharge pas et n’installe pas automatiquement les mises à jour sur Windows Server 2019, Windows Server 2022 ou Windows Server 2016. Vous pouvez modifier cette configuration à l’aide de l’une des méthodes suivantes :

| Méthode | Description |
|---|---|
| **Windows Update** dans Panneau de configuration | **L’installation des mises à jour entraîne automatiquement** l’installation de toutes les mises à jour, y compris Windows Defender mises à jour du renseignement de sécurité. <br/><br/> **Télécharger les mises à jour, mais permettez-moi de choisir de les installer** permet à Windows Defender de télécharger et d’installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement. |
| **Stratégie de groupe** | Vous pouvez configurer et gérer Windows Update à l’aide des paramètres disponibles dans stratégie de groupe, dans le chemin suivant : Modèles d’administration **\Composants Windows\Windows Update\Configurer les Mises à jour automatiques** |
| Clé de Registre **AUOptions** | Les deux valeurs suivantes permettent à Windows Update de télécharger et d’installer automatiquement les mises à jour security intelligence : <br/><br/> **4** -  **Installez automatiquement les mises à jour**. Cette valeur entraîne l’installation automatique de toutes les mises à jour, y compris Windows Defender mises à jour du renseignement de sécurité. <br/><br/> **3** -  **Téléchargez les mises à jour, mais laissez-moi choisir de les installer**. Cette valeur permet à Windows Defender de télécharger et d’installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement. |

Pour vous assurer que la protection contre les programmes malveillants est maintenue, activez les services suivants :

- service Rapport d'erreurs Windows
- service Windows Update

Le tableau suivant répertorie les services pour Microsoft Defender Antivirus et les services dépendants.

| Nom du service | Emplacement du fichier | Description |
|---|---|---|
| service Windows Defender (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Ce service est le principal service antivirus Microsoft Defender qui doit toujours s’exécuter.|
| Rapport d'erreurs Windows Service (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Ce service renvoie les rapports d’erreurs à Microsoft. |
| pare-feu Windows Defender (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Nous vous recommandons de maintenir le service de pare-feu Windows Defender activé. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update est nécessaire pour obtenir des mises à jour du renseignement de sécurité et des mises à jour du moteur de logiciel anti-programme malveillant |

## <a name="submit-samples"></a>Envoyer des exemples

L’exemple de soumission permet à Microsoft de collecter des exemples de logiciels potentiellement malveillants. Pour vous aider à fournir une protection continue et à jour, les chercheurs microsoft utilisent ces exemples pour analyser les activités suspectes et produire des informations de sécurité anti-programme malveillant mises à jour. Nous collectons des fichiers exécutables de programme, tels que des fichiers .exe et des fichiers .dll. Nous ne collectons pas de fichiers qui contiennent des données personnelles, comme des documents Microsoft Word et des fichiers PDF.

### <a name="submit-a-file"></a>Envoyer un fichier

1. Passez en revue le [guide de soumission](/windows/security/threat-protection/intelligence/submission-guide).

2. Visitez [l’exemple de portail de soumission](https://www.microsoft.com/wdsi/filesubmission) et envoyez votre fichier.

### <a name="enable-automatic-sample-submission"></a>Activer la soumission automatique d’exemples

Pour activer la soumission automatique d’exemples, démarrez une console Windows PowerShell en tant qu’administrateur et définissez les données de valeur **SubmitSamplesConsent** en fonction de l’un des paramètres suivants :

|Setting|Description|
|---|---|
| **0** -  **Toujours demander** | Le service antivirus Microsoft Defender vous invite à confirmer la soumission de tous les fichiers requis. Il s’agit du paramètre par défaut pour Microsoft Defender Antivirus, mais il n’est pas recommandé pour les installations sur Windows Server 2016 ou 2019, ou Windows Server 2022 sans interface graphique utilisateur. |
| **1**  -  **Envoyer automatiquement des exemples sécurisés** | Le service antivirus Microsoft Defender envoie tous les fichiers marqués comme « sécurisés » et demande le reste des fichiers. |
| **2** -  **Ne jamais envoyer** | Le service antivirus Microsoft Defender n’invite pas et n’envoie aucun fichier. |
| **3** -  **Envoyer tous les exemples automatiquement** | Le service antivirus Microsoft Defender envoie tous les fichiers sans invite de confirmation. |

> [!NOTE]
> Cette option n’est pas disponible pour Windows Server 2012 R2. 

## <a name="configure-automatic-exclusions"></a>Configurer les exclusions automatiques

Pour garantir la sécurité et les performances, certaines exclusions sont automatiquement ajoutées en fonction des rôles et fonctionnalités que vous installez lors de l’utilisation de Microsoft Defender Antivirus sur Windows Server 2016 ou 2019 ou Windows Server 2022.

Consultez [Configurer les exclusions dans Microsoft Defender Antivirus sur Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>Mode passif et Windows Server

Si vous utilisez un produit antivirus non Microsoft comme solution antivirus principale sur Windows Server, vous devez définir Microsoft Defender Antivirus en mode passif ou désactivé. Si votre point de terminaison Windows Server est intégré à Microsoft Defender pour point de terminaison, vous pouvez définir Microsoft Defender Antivirus en mode passif. Si vous n’utilisez pas Microsoft Defender pour point de terminaison, définissez Microsoft Defender Antivirus en mode désactivé. 

> [!TIP]
> Consultez [Microsoft Defender compatibilité antivirus avec d’autres produits de sécurité](microsoft-defender-antivirus-compatibility.md).

Le tableau suivant décrit les méthodes permettant de définir Microsoft Defender Antivirus en mode passif, de désactiver Microsoft Defender Antivirus et de désinstaller Microsoft Defender Antivirus :

| Procedure | Description |
|---|---|
| Définir Microsoft Defender Antivirus en mode passif à l’aide d’une clé de Registre | Définissez la `ForceDefenderPassiveMode` clé de Registre comme suit : <br/>-Chemin: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>-Nom: `ForceDefenderPassiveMode` <br/>-Type: `REG_DWORD` <br/>-Valeur: `1` |
| Désactiver l’interface utilisateur de l’antivirus Microsoft Defender à l’aide de PowerShell | Ouvrez Windows PowerShell en tant qu’administrateur et exécutez l’applet de commande PowerShell suivante :`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| Désactiver Microsoft Defender Antivirus à l’aide de PowerShell | Utilisez l’applet de commande PowerShell suivante : `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Désactiver Microsoft Defender Antivirus à l’aide de l’Assistant Suppression de rôles et de fonctionnalités | Consultez [Installer ou désinstaller des rôles, des services de rôle ou des fonctionnalités](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard), et utilisez **l’Assistant Suppression de rôles et de fonctionnalités**. <br/><br/>Lorsque vous accédez à l’étape **Fonctionnalités** de l’Assistant, désactivez l’option **Windows Defender Fonctionnalités**. <br/><br/> Si vous effacez **Windows Defender** par lui-même dans la section **Fonctionnalités Windows Defender**, vous êtes invité à supprimer l’interface graphique utilisateur de l’option d’interface **graphique pour Windows Defender**.<br/><br/>Microsoft Defender Antivirus s’exécute toujours normalement sans l’interface utilisateur, mais l’interface utilisateur ne peut pas être activée si vous désactivez la fonctionnalité **principale Windows Defender**. |
| Désinstaller Microsoft Defender Antivirus à l’aide de PowerShell | Utilisez l’applet de commande PowerShell suivante : `Uninstall-WindowsFeature -Name Windows-Defender` |
| Désactiver Microsoft Defender Antivirus à l’aide de stratégie de groupe | Dans votre éditeur de stratégie de groupe local, accédez à Administrative **Template** > **Windows Component** > **Endpoint Protection** > **Disable Endpoint Protection**, puis sélectionnez **Ok activé** > . |

Pour plus d’informations, consultez [Utilisation des clés de Registre](/powershell/scripting/samples/working-with-registry-keys).

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Utilisez-vous Windows Server 2012 R2 ou Windows Server 2016 ?

Si votre serveur Windows Server est intégré à Microsoft Defender pour point de terminaison, vous pouvez maintenant exécuter Microsoft Defender Antivirus en mode passif sur Windows Server 2012 R2 et Windows Server 2016. Consultez les articles suivants :

- [Options d’installation de Microsoft Defender pour point de terminaison](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [Microsoft Defender compatibilité de l’antivirus avec d’autres produits de sécurité](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows](microsoft-defender-antivirus-windows.md)
