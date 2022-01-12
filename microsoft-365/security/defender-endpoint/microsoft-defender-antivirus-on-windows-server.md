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
ms.reviewer: pahuijbr, shwjha
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 6632604e426d6dad5dc7c272d343c2d6b8b59aac
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61940409"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Antivirus Microsoft Defender sur Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Antivirus Microsoft Defender est disponible dans les éditions/versions suivantes de Windows Server :

- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 ou ultérieure
- Windows Server 2016
- Windows Server 2012 R2 (Nécessite Microsoft Defender pour le point de terminaison)

Dans certains cas, Antivirus Microsoft Defender est appelé *Endpoint Protection*; toutefois, le moteur de protection est le même. Bien que les fonctionnalités, la configuration et la gestion soient en grande partie identiques pour Antivirus Microsoft Defender sur [Windows 10](microsoft-defender-antivirus-windows.md) et Windows 11, il existe quelques différences clés sur Windows Server :

- Sur Windows server, les [exclusions automatiques](configure-server-exclusions-microsoft-defender-antivirus.md) sont appliquées en fonction de votre rôle serveur défini.

- Sur Windows Server, si vous exécutez une solution antivirus/anti-programme malveillant non Microsoft, Antivirus Microsoft Defender ne passe pas en mode passif ou désactivé automatiquement. Toutefois, vous pouvez définir Antivirus Microsoft Defender en mode passif ou désactivé manuellement.

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Configuration de Antivirus Microsoft Defender sur Windows Server

Le processus de configuration et d’exécution de Antivirus Microsoft Defender sur une plateforme de serveur comprend plusieurs étapes :

1. [Activez l’interface.](#enable-the-user-interface-on-windows-server)
2. [Installez Antivirus Microsoft Defender](#install-microsoft-defender-antivirus-on-windows-server).
3. [Vérifiez Antivirus Microsoft Defender est en cours d’exécution.](#verify-microsoft-defender-antivirus-is-running)
4. [Mettez à jour votre intelligence de sécurité anti-programme malveillant.](#update-antimalware-security-intelligence)
5. (Selon les besoins) [Envoyer des exemples.](#submit-samples)
6. (Selon les besoins) [Configurez les exclusions automatiques.](#configure-automatic-exclusions)
7. (Uniquement si nécessaire) Définissez [Windows Server en mode passif.](#passive-mode-and-windows-server)

## <a name="enable-the-user-interface-on-windows-server"></a>Activer l’interface utilisateur sur Windows Server

Par défaut, Antivirus Microsoft Defender est installé et fonctionnel sur Windows Server. Parfois, l’interface utilisateur (GUI) est installée par défaut, mais l’interface utilisateur graphique n’est pas requise. Vous pouvez utiliser PowerShell, une stratégie de groupe ou d’autres méthodes pour gérer les Antivirus Microsoft Defender.

Si l’interface graphique graphique n’est pas installée sur  votre serveur et que vous souhaitez l’installer, l’Assistant Ajout de rôles et de fonctionnalités ou les cmdlets PowerShell.

> [!NOTE]
> Cette option n’est pas disponible Windows Server 2012 R2. Pour plus d’informations, voir [Options d’installation de Microsoft Defender pour le point de terminaison.](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

### <a name="turn-on-the-gui-using-the-add-roles-and-features-wizard"></a>Activer l’interface graphique à l’aide de l’Assistant Ajout de rôles et de fonctionnalités

1. Voir [Installer des rôles, des services de rôles](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard)et des fonctionnalités à l’aide de l’Assistant Ajout de rôles et de fonctionnalités et utiliser l’Assistant Ajout de **rôles et de fonctionnalités.**

2. Lorsque vous arrivez à l’étape **Fonctionnalités** de l’Assistant, sous Windows Defender **fonctionnalités,** sélectionnez l’interface graphique graphique pour **Windows Defender’option.**

   Dans Windows Server 2016, l’Assistant Ajout **de rôles et de fonctionnalités** se présente comme ceci :

   ![Assistant Ajouter des rôles et des fonctionnalités affichant l’interface graphique graphique Windows Defender option.](images/server-add-gui.png)

   Dans Windows Server 2019 et Windows Server 2022, l’Assistant Ajout de rôles et de **fonctionnalités** est similaire.

### <a name="turn-on-the-gui-using-powershell"></a>Activer l’interface graphique graphique à l’aide de PowerShell

L’cmdlet PowerShell suivante active l’interface :

```powershell
Install-WindowsFeature -Name Windows-Defender-GUI
```

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Installer Antivirus Microsoft Defender sur Windows Server

Si vous devez installer ou réinstaller Antivirus Microsoft Defender sur Windows Server, vous pouvez  le faire à l’aide de l’Assistant Ajout de rôles et de fonctionnalités ou de PowerShell.

### <a name="use-the-add-roles-and-features-wizard-to-install-microsoft-defender-antivirus"></a>Utiliser l’Assistant Ajout de rôles et de fonctionnalités pour installer Antivirus Microsoft Defender

1. [Reportez-vous à cet article](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard)et utilisez l’Assistant Ajout **de rôles et de fonctionnalités.**

2. Lorsque vous arrivez à l’étape **Fonctionnalités** de l’Assistant, sélectionnez Antivirus Microsoft Defender option. Sélectionnez également **l’interface graphique graphique Windows Defender** option.

### <a name="use-powershell-to-install-microsoft-defender-antivirus"></a>Utiliser PowerShell pour installer des Antivirus Microsoft Defender

Pour utiliser PowerShell pour installer Antivirus Microsoft Defender, exécutez l’cmdlet suivante :

```powershell
Install-WindowsFeature -Name Windows-Defender
```

Les messages d’événement pour le moteur de logiciel anti-programme malveillant inclus dans Antivirus Microsoft Defender peuvent être trouvés dans les événements [de l’Antivirus Microsoft Defender.](troubleshoot-microsoft-defender-antivirus.md)

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Vérifier Antivirus Microsoft Defender est en cours d’exécution

Une Antivirus Microsoft Defender est installée, l’étape suivante consiste à vérifier qu’elle est en cours d’exécution. Sur votre point Windows serveur, exécutez l’cmdlet PowerShell suivante :

```powershell
Get-Service -Name windefend
```

Pour vérifier que la protection pare-feu est allumée, exécutez l’cmdlet PowerShell suivante :

```powershell
Get-Service -Name mpssvc
```

En remplacement de PowerShell, vous pouvez utiliser l’invite de commandes pour vérifier que Antivirus Microsoft Defender est en cours d’exécution. Pour ce faire, exécutez la commande suivante à partir d’une invite de commandes :

```console
sc query Windefend
```

La `sc query` commande renvoie des informations sur le service Antivirus Microsoft Defender service. Lorsque Antivirus Microsoft Defender est en cours d’exécution, `STATE` la valeur s’affiche. `RUNNING`

## <a name="update-antimalware-security-intelligence"></a>Mettre à jour l’intelligence de sécurité contre les programmes malveillants

Pour obtenir des informations de sécurité contre les programmes malveillants mises à jour, vous devez avoir le service de mise à jour Windows en cours d’exécution. Si vous utilisez un service de gestion des mises à jour, tel que Windows Server Update Services (WSUS), assurez-vous que les mises à jour pour Antivirus Microsoft Defender Security intelligence sont approuvées pour les ordinateurs que vous gérez.

Par défaut, Windows Update ne télécharge pas et n’installe pas automatiquement les mises à jour sur Windows Server 2019 ou Windows Server 2022 ou Windows Server 2016. Vous pouvez modifier cette configuration à l’aide de l’une des méthodes suivantes :

<br/><br/>

| Méthode | Description |
|---|---|
| **Windows jour dans** le Panneau de contrôle | **L’installation des mises à** jour entraîne automatiquement l’installation automatique de toutes les mises à jour, y Windows Defender mises à jour de l’intelligence de sécurité. <br/><br/> **Téléchargez les** mises à jour, mais laissez-moi choisir de les installer, ce qui permet à Windows Defender de télécharger et d’installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement. |
| **Stratégie de groupe** | Vous pouvez configurer et gérer Windows Update à l’aide des paramètres disponibles dans la stratégie de groupe, dans le chemin d’accès suivant : **Administrative Templates\Windows Components\Windows Update\Configure Automatic Updates** |
| Clé de Registre **AUOptions** | Les deux valeurs suivantes permettent à Windows Update de télécharger et d’installer automatiquement les mises à jour security intelligence : <br/><br/> **4**  -  **Installez automatiquement les mises à jour.** Cette valeur entraîne l’installation automatique de toutes les mises à jour, y Windows Defender mises à jour de l’intelligence de sécurité. <br/><br/> **3**  -  **Téléchargez les mises à jour, mais laissez-moi choisir s’il faut les installer.** Cette valeur permet Windows Defender télécharger et installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement. |

Pour vous assurer que la protection contre les programmes malveillants est maintenue, nous vous recommandons d’activer les services suivants :

- Rapport d'erreurs Windows service
- Windows service de mise à jour

Le tableau suivant répertorie les services pour Antivirus Microsoft Defender et les services dépendants.

<br/><br/>


| Nom du service | Emplacement du fichier | Description |
|---|---|---|
| Windows Defender Service (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Il s’agit du Antivirus Microsoft Defender principal qui doit être en cours d’exécution en permanence.|
| Rapport d'erreurs Windows Service (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Ce service renvoie des rapports d’erreur à Microsoft. |
| Windows Defender Pare-feu (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Nous vous recommandons de laisser le service Windows Defender pare-feu activé. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows mise à jour est nécessaire pour obtenir les mises à jour de l’intelligence de sécurité et les mises à jour du moteur du logiciel anti-programme malveillant |

## <a name="submit-samples"></a>Envoyer des exemples

La soumission d’exemples permet à Microsoft de collecter des exemples de logiciels potentiellement malveillants. Pour assurer une protection continue et à jour, les chercheurs De Microsoft utilisent ces exemples pour analyser les activités suspectes et produire des informations de sécurité contre les programmes malveillants mises à jour. Nous collectons des fichiers exécutables de programme, tels que .exe et .dll fichiers. Nous ne collectons pas les fichiers qui contiennent des données personnelles, comme Microsoft Word documents et fichiers PDF.

### <a name="submit-a-file"></a>Envoyer un fichier

1. Examinez le [guide de soumission.](/windows/security/threat-protection/intelligence/submission-guide)
2. Visitez [l’exemple de portail de soumission](https://www.microsoft.com/wdsi/filesubmission)et soumettez votre fichier.

### <a name="enable-automatic-sample-submission"></a>Activer l’envoi automatique d’échantillons

Pour activer l’envoi automatique d’échantillons, démarrez une console Windows PowerShell en tant qu’administrateur et définissez les données de valeur **SubmitSamplesConsent** en fonction de l’un des paramètres suivants :

<br/><br/>

|Paramètre|Description|
|---|---|
| **0**  -  **Toujours invite** | Le service Antivirus Microsoft Defender vous invite à confirmer l’envoi de tous les fichiers requis. Il s’agit du paramètre par défaut pour Antivirus Microsoft Defender, mais il n’est pas recommandé pour les installations sur Windows Server 2016 ou 2019, ou Windows Server 2022 sans interface graphique graphique. |
| **1**   -  **Envoyer automatiquement des échantillons sécurisés** | Le service Antivirus Microsoft Defender envoie tous les fichiers marqués comme « sûrs » et demande le reste des fichiers. |
| **2**  -  **Ne jamais envoyer** | Le service Antivirus Microsoft Defender n’invite pas et n’envoie aucun fichier. |
| **3**  -  **Envoyer tous les échantillons automatiquement** | Le service Antivirus Microsoft Defender envoie tous les fichiers sans invite de confirmation. |

> [!NOTE]
> Cette option n’est pas disponible Windows Server 2012 R2. 


## <a name="configure-automatic-exclusions"></a>Configurer les exclusions automatiques

Pour garantir la sécurité et les performances, certaines exclusions sont automatiquement ajoutées en fonction des rôles et des fonctionnalités que vous installez lors de l’utilisation de Antivirus Microsoft Defender sur Windows Server 2016 ou 2019 ou Windows Server 2022.

Voir [Configurer les exclusions dans Antivirus Microsoft Defender sur Windows Server.](configure-server-exclusions-microsoft-defender-antivirus.md)

## <a name="passive-mode-and-windows-server"></a>Mode passif et serveur Windows serveur

Si vous utilisez un produit antivirus non Microsoft comme solution antivirus principale sur Windows Server, vous devez définir Antivirus Microsoft Defender sur le mode passif ou désactivé.

Pour plus d’informations, [voir Install Antivirus Microsoft Defender on Windows Server](microsoft-defender-antivirus-on-windows-server.md#install-microsoft-defender-antivirus-on-windows-server).


### <a name="set-microsoft-defender-antivirus-to-passive-mode-using-a-registry-key"></a>Définir Antivirus Microsoft Defender mode passif à l’aide d’une clé de Registre

Vous pouvez définir Antivirus Microsoft Defender en mode passif en réglant la clé de Registre suivante :
- Chemin d’accès : `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nom : `ForceDefenderPassiveMode`
- Type : `REG_DWORD`
- Valeur : `1`

### <a name="disable-microsoft-defender-antivirus-using-the-remove-roles-and-features-wizard"></a>Désactiver la Antivirus Microsoft Defender à l’aide de l’Assistant Suppression de rôles et de fonctionnalités

1. Voir [Installer ou désinstaller des rôles, des services de rôles](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard)ou des fonctionnalités, et utiliser l’Assistant Suppression de rôles **et de fonctionnalités.**

2. Lorsque vous arrivez à l’étape **Fonctionnalités** de l’Assistant, Windows Defender **l’option Fonctionnalités.**

    Si vous supprimez **Windows Defender** vous-même sous la section **fonctionnalités Windows Defender,** vous serez invité à supprimer l’interface utilisateur graphique de l’option d’interface **Windows Defender**.

    Antivirus Microsoft Defender s’exécutent toujours normalement sans l’interface utilisateur, mais l’interface utilisateur ne peut pas être activée si vous désactivez la fonctionnalité Windows Defender **principale.**

### <a name="turn-off-the-microsoft-defender-antivirus-user-interface-using-powershell"></a>Désactiver l’interface Antivirus Microsoft Defender’utilisateur à l’aide de PowerShell

Pour désactiver l’interface Antivirus Microsoft Defender graphique graphique, utilisez l’cmdlet PowerShell suivante :

```powershell
Uninstall-WindowsFeature -Name Windows-Defender-GUI
```

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Utilisez-vous Windows Server 2012 R2 ou Windows Server 2016 ?

Vous pouvez désormais exécuter Antivirus Microsoft Defender en mode passif sur Windows Server 2012 R2 et Windows Server 2016. Pour plus d’informations, voir [Options d’installation de Microsoft Defender pour le point de terminaison.](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

<br/><br/>

| Procedure | Description |
|---|---|
| Désactiver l’Antivirus Microsoft Defender à l’aide de la stratégie de groupe | Dans votre Éditeur de stratégie de groupe local, accédez à Modèle d’administration Windows composant Endpoint Protection Désactiver Endpoint Protection, puis  >    >    >   **sélectionnez**  >  **Ok activé.** |
| Désactiver la Antivirus Microsoft Defender à l’aide d’une clé de Registre | Pour utiliser la clé de Registre [DisableAntiSpyware,](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) accédez à , et définissez ou créez une entrée `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender` DWORD appelée `DisableAntiSpyware` . Définissez sa valeur sur (qui définit la valeur de la clé de `1` Registre sur *true*). |
| Désactiver la Antivirus Microsoft Defender à l’aide de PowerShell | Utilisez l’cmdlet PowerShell suivante : `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Désinstaller Antivirus Microsoft Defender à l’aide de PowerShell | Utilisez l’cmdlet PowerShell suivante : `Uninstall-WindowsFeature -Name Windows-Defender` |


## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows](microsoft-defender-antivirus-windows.md)
- [Antivirus Microsoft Defender compatibilité](microsoft-defender-antivirus-compatibility.md)
