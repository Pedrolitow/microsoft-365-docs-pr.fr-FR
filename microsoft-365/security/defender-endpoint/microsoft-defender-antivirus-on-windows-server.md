---
title: Antivirus Microsoft Defender sur Windows Server
description: Découvrez comment activer et configurer Antivirus Microsoft Defender sur Windows Server 2016, Windows Server 2019 et Windows Server 2022.
keywords: windows defender, serveur, scep, system center endpoint protection, server 2016, current branch, server 2012
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 04/01/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 412033e274cce22b9350292c612b91ef6e34e209
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634842"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Antivirus Microsoft Defender sur Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Antivirus Microsoft Defender est disponible dans les éditions/versions suivantes de Windows Server :

- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 ou ultérieure
- Windows Server 2016
- Windows Server 2012 R2 (nécessite une Microsoft Defender pour point de terminaison)

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Configuration de Antivirus Microsoft Defender sur Windows Server

Le processus de configuration et d’exécution Antivirus Microsoft Defender sur Windows Server comprend les étapes suivantes :

1. [Activez l’interface](#enable-the-user-interface-on-windows-server).
2. [Installez Antivirus Microsoft Defender](#install-microsoft-defender-antivirus-on-windows-server).
3. [Vérifiez Antivirus Microsoft Defender est en cours d’exécution](#verify-microsoft-defender-antivirus-is-running).
4. [Mettez à jour votre intelligence de sécurité anti-programme malveillant](#update-antimalware-security-intelligence).
5. (Selon les besoins) [Envoyez des exemples](#submit-samples).
6. (Selon les besoins) [Configurez les exclusions automatiques](#configure-automatic-exclusions).
7. (Uniquement si nécessaire) [Définissez Windows Server en mode passif](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Activer l’interface utilisateur sur Windows Server

> [!IMPORTANT]
> Si vous utilisez Windows Server 2012 R2, voir [Options pour installer Microsoft Defender pour point de terminaison](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

Par défaut, Antivirus Microsoft Defender est installé et fonctionnel sur Windows Server. Parfois, l’interface utilisateur (GUI) est installée par défaut. L’interface graphique graphique n’est pas requise . vous pouvez utiliser PowerShell, stratégie de groupe ou d’autres méthodes pour gérer les Antivirus Microsoft Defender. Toutefois, de nombreuses organisations préfèrent utiliser l’interface graphique graphique pour Antivirus Microsoft Defender. Pour installer l’interface graphique graphique, utilisez l’une des procédures du tableau suivant :

| Procedure | Procédure |
|:---|:---|
| Activer l’interface graphique à l’aide de l’Assistant Ajout de rôles et de fonctionnalités | 1. Voir Installer [des](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) rôles, des services de rôles et des fonctionnalités à l’aide de l’Assistant Ajout de rôles et de fonctionnalités, et utiliser l’Assistant **Ajout de rôles et de fonctionnalités**. <br/><br/>2. Lorsque vous arrivez à l’étape Fonctionnalités de l’Assistant, sous **Windows Defender, sélectionnez** l’interface graphique graphique pour **Windows Defender’option**. |
| Activer l’interface graphique graphique à l’aide de PowerShell | 1. Sur votre serveur Windows, ouvrez Windows PowerShell en tant qu’administrateur. <br/><br/>2. Exécutez l’cmdlet PowerShell suivante : `Install-WindowsFeature -Name Windows-Defender-GUI` |

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Installer Antivirus Microsoft Defender sur Windows Server

Si vous devez installer ou réinstaller Antivirus Microsoft Defender sur Windows Server, utilisez l’une des procédures du tableau suivant :

| Procedure | Procédure |
|:---|:---|
| Utiliser l’Assistant Ajout de rôles et de fonctionnalités pour installer Antivirus Microsoft Defender | 1. Voir [Installer ou désinstaller](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) des rôles, des services de rôles ou des fonctionnalités, et utiliser l’Assistant **Ajout de rôles et de fonctionnalités**. <br/><br/>2. Lorsque vous arrivez à l’étape **Fonctionnalités** de l’Assistant, sélectionnez l Antivirus Microsoft Defender option. Sélectionnez également **l’interface graphique graphique pour Windows Defender** option. |
| Utiliser PowerShell pour installer des Antivirus Microsoft Defender | 1. Sur votre serveur Windows, ouvrez Windows PowerShell en tant qu’administrateur. <br/><br/>2. Exécutez l’cmdlet PowerShell suivante : `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> Les messages d’événement pour le moteur de logiciel anti-programme malveillant inclus dans Antivirus Microsoft Defender peuvent être trouvés dans [Antivirus Microsoft Defender événements.](troubleshoot-microsoft-defender-antivirus.md)

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Vérifier que Antivirus Microsoft Defender est en cours d’exécution

Une fois que vous avez installé (ou réinstallé) Antivirus Microsoft Defender, l’étape suivante consiste à vérifier qu’il est en cours d’exécution. Utilisez les cmdlets PowerShell dans le tableau suivant :

| Procedure | Cmdlet PowerShell |
|:---|:---|
| Vérifier qu’Antivirus Microsoft Defender est en cours d’exécution | `Get-Service -Name windefend` |
| Vérifier que la protection pare-feu est allumée | `Get-Service -Name mpssvc` |

En remplacement de PowerShell, vous pouvez utiliser l’invite de commandes pour vérifier que Antivirus Microsoft Defender est en cours d’exécution. Pour ce faire, exécutez la commande suivante à partir d’une invite de commandes :

```cmd
sc query Windefend
```

La `sc query` commande renvoie des informations sur le service Antivirus Microsoft Defender service. Lorsque Antivirus Microsoft Defender est en cours d’exécution, la `STATE` valeur s’affiche`RUNNING`.

Pour afficher tous les services qui ne sont pas en cours d’exécution, exécutez l’cmdlet PowerShell suivante :

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Mettre à jour l’intelligence de sécurité contre les programmes malveillants

Pour obtenir vos mises à jour d’informations de sécurité régulières, le service Windows Update de sécurité doit être en cours d’exécution. Si vous utilisez un service de gestion des mises à jour, tel que Windows Server Update Services (WSUS), assurez-vous que les mises à jour pour Antivirus Microsoft Defender Security intelligence sont approuvées pour les ordinateurs que vous gérez.

Par défaut, Windows Update télécharge et n’installe pas automatiquement les mises à jour sur Windows Server 2019 ou Windows Server 2022 ou Windows Server 2016. Vous pouvez modifier cette configuration à l’aide de l’une des méthodes suivantes :

| Méthode | Description |
|---|---|
| **Windows Update** dans Panneau de configuration | **L’installation des mises à** jour entraîne automatiquement l’installation automatique de toutes les mises à jour, y Windows Defender mises à jour d’informations de sécurité. <br/><br/> **Télécharger les** mises à jour, mais me laisser choisir de les installer permet à Windows Defender de télécharger et d’installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement. |
| **Stratégie de groupe** | Vous pouvez configurer et gérer Windows Update à l’aide des paramètres disponibles dans stratégie de groupe, dans le chemin d’accès suivant : **Modèles d’administration\Composants Windows\Windows Update\Configurer** les mises à jour automatiques |
| Clé **de Registre AUOptions** | Les deux valeurs suivantes permettent Windows Update télécharger et installer automatiquement les mises à jour security intelligence : <br/><br/> **4** -  **Installez automatiquement les mises à jour**. Cette valeur entraîne l’installation automatique de toutes les mises à jour, y Windows Defender mises à jour de l’intelligence de sécurité. <br/><br/> **3** -  **Téléchargez les mises à jour, mais laissez-moi choisir s’il faut les installer**. Cette valeur permet Windows Defender télécharger et installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement. |

Pour vous assurer que la protection contre les programmes malveillants est conservée, activez les services suivants :

- Rapport d'erreurs Windows service
- Windows Update service

Le tableau suivant répertorie les services pour Antivirus Microsoft Defender et les services dépendants.

| Nom du service | Emplacement du fichier | Description |
|---|---|---|
| Windows Defender Service (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Il s’agit du principal Antivirus Microsoft Defender service qui doit être toujours en cours d’exécution.|
| Rapport d'erreurs Windows Service (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Ce service renvoie des rapports d’erreur à Microsoft. |
| Windows Defender Pare-feu (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Nous vous recommandons de maintenir le service Windows Defender pare-feu activé. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update est nécessaire pour obtenir les mises à jour de l’intelligence de sécurité et les mises à jour du moteur du logiciel anti-programme malveillant |

## <a name="submit-samples"></a>Envoyer des exemples

La soumission d’exemples permet à Microsoft de collecter des exemples de logiciels potentiellement malveillants. Pour assurer une protection continue et à jour, les chercheurs De Microsoft utilisent ces exemples pour analyser les activités suspectes et produire des informations de sécurité contre les programmes malveillants mises à jour. Nous collectons des fichiers exécutables de programme, tels que des .exe et des .dll programmes. Nous ne collectons pas les fichiers qui contiennent des données personnelles, comme Microsoft Word documents et fichiers PDF.

### <a name="submit-a-file"></a>Envoyer un fichier

1. Examinez le [guide de soumission](/windows/security/threat-protection/intelligence/submission-guide).

2. Visitez le [portail de soumission d’exemples](https://www.microsoft.com/wdsi/filesubmission) et envoyez votre fichier.

### <a name="enable-automatic-sample-submission"></a>Activer l’envoi automatique d’échantillons

Pour activer l’envoi automatique d’échantillons, démarrez une console Windows PowerShell en tant qu’administrateur et définissez les données de valeur **SubmitSamplesConsent** en fonction de l’un des paramètres suivants :

|Paramètre|Description|
|---|---|
| **0** -  **Toujours invite** | Le service Antivirus Microsoft Defender vous invite à confirmer l’envoi de tous les fichiers requis. Il s’agit du paramètre par défaut pour Antivirus Microsoft Defender, mais il n’est pas recommandé pour les installations sur Windows Server 2016 ou 2019, ou Windows Server 2022 sans interface graphique graphique. |
| **1**  -  **Envoyer automatiquement des échantillons sécurisés** | Le service Antivirus Microsoft Defender envoie tous les fichiers marqués comme « sûrs » et demande le reste des fichiers. |
| **2** -  **Ne jamais envoyer** | Le service Antivirus Microsoft Defender n’invite pas et n’envoie aucun fichier. |
| **3** -  **Envoyer tous les échantillons automatiquement** | Le service Antivirus Microsoft Defender envoie tous les fichiers sans invite de confirmation. |

> [!NOTE]
> Cette option n’est pas disponible Windows Server 2012 R2. 

## <a name="configure-automatic-exclusions"></a>Configurer les exclusions automatiques

Pour garantir la sécurité et les performances, certaines exclusions sont automatiquement ajoutées en fonction des rôles et des fonctionnalités que vous installez lors de l’utilisation de Antivirus Microsoft Defender sur Windows Server 2016 ou 2019 ou Windows Server 2022.

Voir [Configurer les exclusions dans Antivirus Microsoft Defender sur Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>Mode passif et serveur Windows serveur

Si vous utilisez un produit antivirus non Microsoft comme solution antivirus principale sur Windows Server, vous devez définir Antivirus Microsoft Defender sur le mode passif ou désactivé. Si votre point de terminaison Windows serveur est intégré à Microsoft Defender pour point de terminaison, vous pouvez définir Antivirus Microsoft Defender le mode passif. Si vous n’utilisez pas Microsoft Defender pour point de terminaison, Antivirus Microsoft Defender le mode désactivé. 

> [!TIP]
> Voir [Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité](microsoft-defender-antivirus-compatibility.md).

Le tableau suivant décrit les méthodes pour définir Antivirus Microsoft Defender mode passif, désactiver les Antivirus Microsoft Defender et désinstaller Antivirus Microsoft Defender :

| Procedure | Description |
|---|---|
| Définir Antivirus Microsoft Defender en mode passif à l’aide d’une clé de Registre | Définissez la clé de Registre ForceDefenderPassiveMode comme suit : <br/>- Chemin d’accès : `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>- Nom : `ForceDefenderPassiveMode` <br/>- Type : `REG_DWORD` <br/>- Valeur : `1` |
| Désactiver l’interface Antivirus Microsoft Defender’utilisateur à l’aide de PowerShell | Ouvrez Windows PowerShell en tant qu’administrateur et exécutez l’cmdlet PowerShell suivante :`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| Désactiver la Antivirus Microsoft Defender à l’aide de PowerShell | Utilisez l’cmdlet PowerShell suivante : `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Désactiver la Antivirus Microsoft Defender à l’aide de l’Assistant Suppression de rôles et de fonctionnalités | Voir [Installer ou désinstaller des rôles, des services de rôles](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) ou des fonctionnalités, et utiliser l’Assistant Suppression de **rôles et de fonctionnalités**. <br/><br/>Lorsque vous arrivez à l’étape **Fonctionnalités** de l’Assistant, Windows Defender **l’option Fonctionnalités**. <br/><br/> Si vous supprimez **Windows Defender** vous-même sous la section **Windows Defender Features**, vous serez invité à supprimer l’interface utilisateur graphique de l’option d’interface **Windows Defender**.<br/><br/>Antivirus Microsoft Defender s’exécutent toujours normalement sans l’interface utilisateur, mais l’interface utilisateur ne peut pas être activée si vous désactivez la fonctionnalité d’Windows Defender **principale.** |
| Désinstaller Antivirus Microsoft Defender à l’aide de PowerShell | Utilisez l’cmdlet PowerShell suivante : `Uninstall-WindowsFeature -Name Windows-Defender` |
| Désactiver l’Antivirus Microsoft Defender l’stratégie de groupe | Dans votre Éditeur de stratégie de groupe local,  >  accédez à Modèle d’administration **Windows Composant** >  **Endpoint Protection** >  Désélecteur **Endpoint Protection**, puis sélectionnez **EnabledOK** > . |

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Utilisez-vous Windows Server 2012 R2 ou Windows Server 2016 ?

Si votre serveur Windows est intégré à Microsoft Defender pour point de terminaison, vous pouvez désormais exécuter Antivirus Microsoft Defender en mode passif sur Windows Server 2012 R2 et Windows Server 2016. Consultez les articles suivants :

- [Options d’installation Microsoft Defender pour point de terminaison](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows](microsoft-defender-antivirus-windows.md)

