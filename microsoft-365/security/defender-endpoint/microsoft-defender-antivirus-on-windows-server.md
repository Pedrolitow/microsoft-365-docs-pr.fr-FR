---
title: Antivirus Microsoft Defender sur Windows Server
description: Découvrez comment activer et configurer Antivirus Microsoft Defender sur Windows Server 2016, Windows Server 2019 et Windows Server 2022.
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
ms.technology: mde
ms.topic: article
ms.date: 04/01/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: b93595375982e3ed61d1ac94ae410575b0d72307
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666985"
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
- Windows Server 2012 R2 (nécessite Microsoft Defender pour point de terminaison)

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Configuration de Antivirus Microsoft Defender sur Windows Server

Le processus de configuration et d’exécution de Antivirus Microsoft Defender sur Windows Server comprend les étapes suivantes :

1. [Activez l’interface](#enable-the-user-interface-on-windows-server).
2. [Installez Antivirus Microsoft Defender](#install-microsoft-defender-antivirus-on-windows-server).
3. [Vérifiez que Antivirus Microsoft Defender est en cours d’exécution](#verify-microsoft-defender-antivirus-is-running).
4. [Mettez à jour votre renseignement de sécurité anti-programme malveillant](#update-antimalware-security-intelligence).
5. (Si nécessaire) [Envoyez des exemples](#submit-samples).
6. (Si nécessaire) [Configurez les exclusions automatiques](#configure-automatic-exclusions).
7. (Uniquement si nécessaire) Définissez [Windows Server en mode passif](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Activer l’interface utilisateur sur Windows Server

> [!IMPORTANT]
> Si vous utilisez Windows Server 2012 R2, consultez [Options pour installer Microsoft Defender pour point de terminaison](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

Par défaut, Antivirus Microsoft Defender est installé et fonctionnel sur Windows Server. Parfois, l’interface utilisateur (GUI) est installée par défaut. L’interface utilisateur graphique n’est pas obligatoire ; vous pouvez utiliser PowerShell, stratégie de groupe ou d’autres méthodes pour gérer Antivirus Microsoft Defender. Toutefois, de nombreuses organisations préfèrent utiliser l’interface graphique utilisateur pour Antivirus Microsoft Defender. Pour installer l’interface graphique utilisateur, utilisez l’une des procédures du tableau suivant :

| Procedure | Procédure |
|:---|:---|
| Activer l’interface graphique utilisateur à l’aide de l’Assistant Ajout de rôles et de fonctionnalités | 1. Consultez [Installer des rôles, des services de rôle et des fonctionnalités à l’aide de l’Assistant Ajout de rôles et de fonctionnalités](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard), et utilisez **l’Assistant Ajout de rôles et de fonctionnalités**. <br/><br/>2. Lorsque vous accédez à l’étape **Fonctionnalités** de l’Assistant, sous **Windows Defender Fonctionnalités**, sélectionnez l’interface **utilisateur utilisateur pour Windows Defender** option. |
| Activer l’interface graphique utilisateur à l’aide de PowerShell | 1. Sur votre serveur Windows, ouvrez Windows PowerShell en tant qu’administrateur. <br/><br/>2. Exécutez l’applet de commande PowerShell suivante : `Install-WindowsFeature -Name Windows-Defender-GUI` |

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Installer Antivirus Microsoft Defender sur Windows Server

Si vous devez installer ou réinstaller Antivirus Microsoft Defender sur Windows Server, utilisez l’une des procédures du tableau suivant :

| Procedure | Procédure |
|:---|:---|
| Utilisez l’Assistant Ajout de rôles et de fonctionnalités pour installer Antivirus Microsoft Defender | 1. Consultez [Installer ou désinstaller des rôles, des services de rôle ou des fonctionnalités](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard), et utilisez l’Assistant **Ajout de rôles et de fonctionnalités**. <br/><br/>2. Lorsque vous accédez à l’étape **Fonctionnalités** de l’Assistant, sélectionnez l’option Antivirus Microsoft Defender. Sélectionnez également **l’interface graphique utilisateur pour Windows Defender** option. |
| Utiliser PowerShell pour installer Antivirus Microsoft Defender | 1. Sur votre serveur Windows, ouvrez Windows PowerShell en tant qu’administrateur. <br/><br/>2. Exécutez l’applet de commande PowerShell suivante : `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> Les messages d’événement pour le moteur de logiciel anti-programme malveillant inclus dans Antivirus Microsoft Defender sont disponibles dans [Antivirus Microsoft Defender Événements](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Vérifier que Antivirus Microsoft Defender est en cours d’exécution

Une fois que vous avez installé (ou réinstallé) Antivirus Microsoft Defender, l’étape suivante consiste à vérifier qu’il est en cours d’exécution. Utilisez les applets de commande PowerShell dans le tableau suivant :

| Procedure | Applet de commande PowerShell |
|:---|:---|
| Vérifier que Antivirus Microsoft Defender est en cours d’exécution | `Get-Service -Name windefend` |
| Vérifier que la protection pare-feu est activée | `Get-Service -Name mpssvc` |

En guise d’alternative à PowerShell, vous pouvez utiliser l’invite de commandes pour vérifier que Antivirus Microsoft Defender est en cours d’exécution. Pour ce faire, exécutez la commande suivante à partir d’une invite de commandes :

```cmd
sc query Windefend
```

La `sc query` commande retourne des informations sur le service Antivirus Microsoft Defender. Lorsque Antivirus Microsoft Defender est en cours d’exécution, la valeur s’affiche `STATE` `RUNNING`.

Pour afficher tous les services qui ne sont pas en cours d’exécution, exécutez l’applet de commande PowerShell suivante :

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Mettre à jour le renseignement de sécurité anti-programme malveillant

Pour obtenir vos mises à jour régulières du renseignement de sécurité, le service Windows Update doit être en cours d’exécution. Si vous utilisez un service de gestion des mises à jour, comme Windows Server Update Services (WSUS), assurez-vous que les mises à jour pour Antivirus Microsoft Defender security intelligence sont approuvées pour les ordinateurs que vous gérez.

Par défaut, Windows Update ne télécharge pas et n’installe pas automatiquement les mises à jour sur Windows Server 2019 ou Windows Server 2022 ou Windows Server 2016. Vous pouvez modifier cette configuration à l’aide de l’une des méthodes suivantes :

| Méthode | Description |
|---|---|
| **Windows Update** dans Panneau de configuration | **L’installation des mises à jour entraîne automatiquement** l’installation de toutes les mises à jour, y compris Windows Defender mises à jour du renseignement de sécurité. <br/><br/> **Télécharger les mises à jour, mais permettez-moi de choisir de les installer** permet à Windows Defender de télécharger et d’installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement. |
| **Stratégie de groupe** | Vous pouvez configurer et gérer Windows Update à l’aide des paramètres disponibles dans stratégie de groupe, dans le chemin suivant : **Modèles d’administration\composants Windows\Windows Update\Configurer les mises à jour automatiques** |
| Clé de Registre **AUOptions** | Les deux valeurs suivantes permettent à Windows Update de télécharger et d’installer automatiquement les mises à jour security intelligence : <br/><br/> **4** -  **Installez automatiquement les mises à jour**. Cette valeur entraîne l’installation automatique de toutes les mises à jour, y compris Windows Defender mises à jour du renseignement de sécurité. <br/><br/> **3** -  **Téléchargez les mises à jour, mais laissez-moi choisir de les installer**. Cette valeur permet à Windows Defender de télécharger et d’installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement. |

Pour vous assurer que la protection contre les programmes malveillants est maintenue, activez les services suivants :

- service Rapport d'erreurs Windows
- service Windows Update

Le tableau suivant répertorie les services pour Antivirus Microsoft Defender et les services dépendants.

| Nom du service | Emplacement du fichier | Description |
|---|---|---|
| service Windows Defender (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Il s’agit du principal service Antivirus Microsoft Defender qui doit toujours s’exécuter.|
| Rapport d'erreurs Windows Service (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Ce service renvoie les rapports d’erreurs à Microsoft. |
| pare-feu Windows Defender (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Nous vous recommandons de maintenir le service de pare-feu Windows Defender activé. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update est nécessaire pour obtenir des mises à jour du renseignement de sécurité et des mises à jour du moteur de logiciel anti-programme malveillant |

## <a name="submit-samples"></a>Envoyer des exemples

L’exemple de soumission permet à Microsoft de collecter des exemples de logiciels potentiellement malveillants. Pour vous aider à fournir une protection continue et à jour, les chercheurs microsoft utilisent ces exemples pour analyser les activités suspectes et produire des informations de sécurité anti-programme malveillant mises à jour. Nous collectons des fichiers exécutables de programme, tels que des fichiers .exe et des fichiers .dll. Nous ne collectons pas de fichiers qui contiennent des données personnelles, comme Microsoft Word documents et fichiers PDF.

### <a name="submit-a-file"></a>Envoyer un fichier

1. Passez en revue le [guide de soumission](/windows/security/threat-protection/intelligence/submission-guide).

2. Visitez [l’exemple de portail de soumission](https://www.microsoft.com/wdsi/filesubmission) et envoyez votre fichier.

### <a name="enable-automatic-sample-submission"></a>Activer la soumission automatique d’exemples

Pour activer la soumission automatique d’exemples, démarrez une console Windows PowerShell en tant qu’administrateur et définissez les données de valeur **SubmitSamplesConsent** en fonction de l’un des paramètres suivants :

|Paramètre|Description|
|---|---|
| **0** -  **Toujours demander** | Le service Antivirus Microsoft Defender vous invite à confirmer la soumission de tous les fichiers requis. Il s’agit du paramètre par défaut pour Antivirus Microsoft Defender, mais il n’est pas recommandé pour les installations sur Windows Server 2016 ou 2019, ou Windows Server 2022 sans interface graphique utilisateur. |
| **1**  -  **Envoyer automatiquement des exemples sécurisés** | Le service Antivirus Microsoft Defender envoie tous les fichiers marqués comme « sécurisés » et demande le reste des fichiers. |
| **2** -  **Ne jamais envoyer** | Le service Antivirus Microsoft Defender n’invite pas et n’envoie aucun fichier. |
| **3** -  **Envoyer tous les exemples automatiquement** | Le service Antivirus Microsoft Defender envoie tous les fichiers sans invite de confirmation. |

> [!NOTE]
> Cette option n’est pas disponible pour Windows Server 2012 R2. 

## <a name="configure-automatic-exclusions"></a>Configurer les exclusions automatiques

Pour garantir la sécurité et les performances, certaines exclusions sont automatiquement ajoutées en fonction des rôles et fonctionnalités que vous installez lors de l’utilisation de Antivirus Microsoft Defender sur Windows Server 2016 ou 2019, ou Windows Server 2022.

Consultez [Configurer les exclusions dans Antivirus Microsoft Defender sur Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>Mode passif et serveur Windows

Si vous utilisez un produit antivirus non Microsoft comme solution antivirus principale sur Windows Server, vous devez définir Antivirus Microsoft Defender en mode passif ou en mode désactivé. Si votre point de terminaison Windows Server est intégré à Microsoft Defender pour point de terminaison, vous pouvez définir Antivirus Microsoft Defender en mode passif. Si vous n’utilisez pas Microsoft Defender pour point de terminaison, définissez Antivirus Microsoft Defender en mode désactivé. 

> [!TIP]
> Consultez [Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité](microsoft-defender-antivirus-compatibility.md).

Le tableau suivant décrit les méthodes permettant de définir Antivirus Microsoft Defender en mode passif, de désactiver Antivirus Microsoft Defender et de désinstaller Antivirus Microsoft Defender :

| Procedure | Description |
|---|---|
| Définir Antivirus Microsoft Defender en mode passif à l’aide d’une clé de Registre | Définissez la clé de Registre ForceDefenderPassiveMode comme suit : <br/>- Chemin d’accès : `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>- Nom : `ForceDefenderPassiveMode` <br/>- Type : `REG_DWORD` <br/>- Valeur : `1` |
| Désactiver l’interface utilisateur Antivirus Microsoft Defender à l’aide de PowerShell | Ouvrez Windows PowerShell en tant qu’administrateur et exécutez l’applet de commande PowerShell suivante :`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| Désactiver Antivirus Microsoft Defender à l’aide de PowerShell | Utilisez l’applet de commande PowerShell suivante : `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Désactiver Antivirus Microsoft Defender à l’aide de l’Assistant Suppression de rôles et de fonctionnalités | Consultez [Installer ou désinstaller des rôles, des services de rôle ou des fonctionnalités](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard), et utilisez **l’Assistant Suppression de rôles et de fonctionnalités**. <br/><br/>Lorsque vous accédez à l’étape **Fonctionnalités** de l’Assistant, désactivez l’option **Windows Defender Fonctionnalités**. <br/><br/> Si vous effacez **Windows Defender** par lui-même dans la section **Fonctionnalités Windows Defender**, vous êtes invité à supprimer l’interface graphique utilisateur de l’option d’interface **graphique pour Windows Defender**.<br/><br/>Antivirus Microsoft Defender s’exécute toujours normalement sans l’interface utilisateur, mais l’interface utilisateur ne peut pas être activée si vous désactivez la fonctionnalité **de base Windows Defender**. |
| Désinstaller Antivirus Microsoft Defender à l’aide de PowerShell | Utilisez l’applet de commande PowerShell suivante : `Uninstall-WindowsFeature -Name Windows-Defender` |
| Désactiver Antivirus Microsoft Defender à l’aide de stratégie de groupe | Dans votre éditeur de stratégie de groupe local, accédez au **modèle** >  **d’administration Windows composant** >  **Endpoint Protection** >  **Disable Endpoint Protection**, puis sélectionnez **EnabledOK** > . |

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Utilisez-vous Windows Server 2012 R2 ou Windows Server 2016 ?

Si votre serveur Windows est intégré à Microsoft Defender pour point de terminaison, vous pouvez maintenant exécuter Antivirus Microsoft Defender en mode passif sur Windows Server 2012 R2 et Windows Server 2016. Consultez les articles suivants :

- [Options d’installation de Microsoft Defender pour point de terminaison](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [Antivirus Microsoft Defender compatibilité avec d’autres produits de sécurité](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows](microsoft-defender-antivirus-windows.md)

