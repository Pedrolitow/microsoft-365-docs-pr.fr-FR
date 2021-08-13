---
title: Antivirus Microsoft Defender sur Windows Server
description: Découvrez comment activer et configurer Antivirus Microsoft Defender sur Windows Server 2016 et Windows Server 2019.
keywords: windows defender, serveur, scep, system center endpoint protection, server 2016, current branch, server 2012
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr, shwjha
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 05/13/2021
ms.openlocfilehash: d31f60c05e8b07f3230bddf242f58fe1f38595942c9e6d4ea9722c828f319f0c
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53845162"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Antivirus Microsoft Defender sur Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Antivirus Microsoft Defender est disponible sur les éditions/versions suivantes de Windows Server :
- Windows Server 2019
- Windows Serveur, version 1803 ou ultérieure
- Windows Server 2016. 

Dans certains cas, Antivirus Microsoft Defender est appelé *Endpoint Protection*; toutefois, le moteur de protection est le même. Bien que les fonctionnalités, la configuration et la gestion soient en grande partie identiques pour Antivirus Microsoft Defender sur [Windows 10,](microsoft-defender-antivirus-in-windows-10.md)il existe quelques différences clés sur Windows Server :

- Sur Windows server, les [exclusions automatiques](configure-server-exclusions-microsoft-defender-antivirus.md) sont appliquées en fonction de votre rôle serveur défini.
 
- Sur Windows Server, si vous exécutez une solution antivirus/anti-programme malveillant non Microsoft, Antivirus Microsoft Defender ne passe pas en mode passif ou désactivé automatiquement. Toutefois, vous pouvez définir Antivirus Microsoft Defender le mode passif ou désactivé manuellement.

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Configuration de Antivirus Microsoft Defender sur Windows Server

Le processus de configuration et d’exécution de Antivirus Microsoft Defender sur une plateforme de serveur comprend plusieurs étapes :

1. [Activez l’interface.](#enable-the-user-interface-on-windows-server)
2. [Installez Antivirus Microsoft Defender](#install-microsoft-defender-antivirus-on-windows-server).
3. [Vérifiez Antivirus Microsoft Defender est en cours d’exécution.](#verify-microsoft-defender-antivirus-is-running)
4. [Mettez à jour votre intelligence de sécurité anti-programme malveillant.](#update-antimalware-security-intelligence)
5. (Selon les besoins) [Envoyer des exemples.](#submit-samples)
6. (Selon les besoins) [Configurer les exclusions automatiques.](#configure-automatic-exclusions)
7. (Uniquement si nécessaire) [Définissez Antivirus Microsoft Defender en mode passif.](#need-to-set-microsoft-defender-antivirus-to-passive-mode)

## <a name="enable-the-user-interface-on-windows-server"></a>Activer l’interface utilisateur sur Windows Server

Par défaut, Antivirus Microsoft Defender est installé et fonctionnel sur Windows Server. Parfois, l’interface utilisateur (GUI) est installée par défaut, mais l’interface utilisateur graphique n’est pas requise. Vous pouvez utiliser PowerShell, une stratégie de groupe ou d’autres méthodes pour gérer les Antivirus Microsoft Defender. 

Si l’interface graphique graphique n’est pas installée sur  votre serveur et que vous souhaitez l’installer, l’Assistant Ajout de rôles et de fonctionnalités ou les cmdlets PowerShell.

### <a name="turn-on-the-gui-using-the-add-roles-and-features-wizard"></a>Activer l’interface graphique à l’aide de l’Assistant Ajout de rôles et de fonctionnalités

1. Voir [Installer des rôles, des services de rôles](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard)et des fonctionnalités à l’aide de l’Assistant Ajout de rôles et de fonctionnalités et utiliser l’Assistant Ajout de **rôles et de fonctionnalités.**

2. Lorsque vous arrivez à l’étape **Fonctionnalités** de l’Assistant, sous Windows Defender **fonctionnalités,** sélectionnez l’interface graphique graphique pour **Windows Defender’option.**

   Dans Windows Server 2016, l’Assistant Ajout **de rôles et de fonctionnalités** se présente comme ceci :

   ![Assistant Ajout de rôles et de fonctionnalités affichant l’interface graphique Windows Defender option](images/server-add-gui.png)

   Dans Windows Server 2019, l’Assistant Ajout de rôles et de **fonctionnalités** est similaire.

### <a name="turn-on-the-gui-using-powershell"></a>Activer l’interface graphique graphique à l’aide de PowerShell

L’cmdlet PowerShell suivante active l’interface : 

```PowerShell
Install-WindowsFeature -Name Windows-Defender-GUI
```

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Installer Antivirus Microsoft Defender sur Windows Server

Si vous devez installer ou réinstaller Antivirus Microsoft Defender sur Windows Server, vous pouvez  le faire à l’aide de l’Assistant Ajout de rôles et de fonctionnalités ou de PowerShell.

### <a name="use-the-add-roles-and-features-wizard-to-install-microsoft-defender-antivirus"></a>Utiliser l’Assistant Ajout de rôles et de fonctionnalités pour installer Antivirus Microsoft Defender

1. Reportez-vous [à cet article](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard)et utilisez l’Assistant Ajout de **rôles et de fonctionnalités.**

2. Lorsque vous arrivez à l’étape **Fonctionnalités** de l’Assistant, sélectionnez Antivirus Microsoft Defender option. Sélectionnez également **l’interface graphique graphique pour Windows Defender** option.

### <a name="use-powershell-to-install-microsoft-defender-antivirus"></a>Utiliser PowerShell pour installer des Antivirus Microsoft Defender

Pour utiliser PowerShell pour installer Antivirus Microsoft Defender, exécutez l’cmdlet suivante :

```PowerShell
Install-WindowsFeature -Name Windows-Defender
```

Les messages d’événement pour le moteur de logiciel anti-programme malveillant inclus dans Antivirus Microsoft Defender peuvent être trouvés dans les événements [de l’Antivirus Microsoft Defender.](troubleshoot-microsoft-defender-antivirus.md)


## <a name="verify-microsoft-defender-antivirus-is-running"></a>Vérifier Antivirus Microsoft Defender est en cours d’exécution

Une Antivirus Microsoft Defender est installée, l’étape suivante consiste à vérifier qu’elle est en cours d’exécution. Sur votre point Windows serveur, exécutez l’cmdlet PowerShell suivante :

```PowerShell
Get-Service -Name windefend
```

Pour vérifier que la protection pare-feu est allumée, exécutez l’cmdlet PowerShell suivante :

```PowerShell 
Get-Service -Name mpssvc
```

En remplacement de PowerShell, vous pouvez utiliser l’invite de commandes pour vérifier que Antivirus Microsoft Defender est en cours d’exécution. Pour ce faire, exécutez la commande suivante à partir d’une invite de commandes : 

```console
sc query Windefend
```

La `sc query` commande renvoie des informations sur Antivirus Microsoft Defender service. Lorsque Antivirus Microsoft Defender est en cours d’exécution, `STATE` la valeur s’affiche. `RUNNING`

## <a name="update-antimalware-security-intelligence"></a>Mettre à jour l’intelligence de sécurité contre les programmes malveillants 

Pour obtenir des informations de sécurité contre les programmes malveillants mises à jour, le service de mise à jour Windows logiciels malveillants doit être en cours d’exécution. Si vous utilisez un service de gestion des mises à jour, tel que Windows Server Update Services (WSUS), assurez-vous que les mises à jour pour Antivirus Microsoft Defender Security intelligence sont approuvées pour les ordinateurs que vous gérez.

Par défaut, Windows Update ne télécharge pas et n’installe pas automatiquement les mises à jour sur Windows Server 2019 ou Windows Server 2016. Vous pouvez modifier cette configuration à l’aide de l’une des méthodes suivantes :


|Méthode  |Description  |
|---------|---------|
|**Windows jour dans** le Panneau de contrôle     | **L’installation des mises à** jour entraîne automatiquement l’installation automatique de toutes les mises à jour, Windows Defender mises à jour d’informations de sécurité. <p>**Téléchargez les** mises à jour, mais laissez-moi choisir de les installer, ce qui permet à Windows Defender de télécharger et d’installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement.       |
|**Stratégie de groupe**     | Vous pouvez configurer et gérer Windows Update en utilisant les paramètres disponibles dans la stratégie de groupe, dans le chemin d’accès suivant : **Administrative Templates\Windows Components\Windows Update\Configure Automatic Updates**         |
|Clé de Registre **AUOptions**     | Les deux valeurs suivantes permettent à Windows Update de télécharger et d’installer automatiquement les mises à jour security intelligence : <p>**4**  -  **Installez automatiquement les mises à jour.** Cette valeur entraîne l’installation automatique de toutes les mises à jour, y Windows Defender mises à jour de l’intelligence de sécurité. <p>**3**  -  **Téléchargez les mises à jour, mais laissez-moi choisir s’il faut les installer.**  Cette valeur permet Windows Defender télécharger et installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement.         |

Pour vous assurer que la protection contre les programmes malveillants est maintenue, nous vous recommandons d’activer les services suivants :

- Rapport d’erreurs Windows service

- Windows Mettre à jour le service

Le tableau suivant répertorie les services pour Antivirus Microsoft Defender et les services dépendants.

|Nom du service|Emplacement du fichier|Description|
|--------|---------|--------|
|Windows Defender Service (WinDefend)|`C:\Program Files\Windows Defender\MsMpEng.exe`|Il s’agit du service Antivirus Microsoft Defender principal qui doit être en cours d’exécution en permanence.|
|Rapport d'erreurs Windows Service (Wersvc)|`C:\WINDOWS\System32\svchost.exe -k WerSvcGroup`|Ce service renvoie des rapports d’erreur à Microsoft.|
|Windows Defender Pare-feu (MpsSvc)|`C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork`|Nous vous recommandons de laisser le service Windows Defender pare-feu activé.|
|Windows Update (Wuauserv)|`C:\WINDOWS\system32\svchost.exe -k netsvcs`|Windows Une mise à jour est nécessaire pour obtenir des mises à jour de l’intelligence de sécurité et des mises à jour du moteur anti-programme malveillant|

## <a name="submit-samples"></a>Envoyer des exemples

La soumission d’exemples permet à Microsoft de collecter des exemples de logiciels potentiellement malveillants. Pour assurer une protection continue et à jour, les chercheurs De Microsoft utilisent ces exemples pour analyser les activités suspectes et produire des informations de sécurité anti-programme malveillant mises à jour. Nous collectons des fichiers exécutables de programme, tels que .exe et .dll fichiers. Nous ne collectons pas les fichiers qui contiennent des données personnelles, comme Microsoft Word documents et fichiers PDF.

### <a name="submit-a-file"></a>Envoyer un fichier

1. Examinez le [guide de soumission.](/windows/security/threat-protection/intelligence/submission-guide)

2. Visitez le [portail de soumission d’exemples](https://www.microsoft.com/wdsi/filesubmission)et envoyez votre fichier.


### <a name="enable-automatic-sample-submission"></a>Activer l’envoi automatique d’échantillons

Pour activer la soumission automatique d’échantillons, démarrez une console Windows PowerShell en tant qu’administrateur et définissez les données de valeur **SubmitSamplesConsent** en fonction de l’un des paramètres suivants :

|Paramètre  |Description  |
|---------|---------|
|**0**  -  **Toujours invite**     |Le service Antivirus Microsoft Defender vous invite à confirmer l’envoi de tous les fichiers requis. Il s’agit du paramètre par défaut pour Antivirus Microsoft Defender, mais il n’est pas recommandé pour les installations sur Windows Server 2016 ou 2019 sans interface graphique graphique.         |
|**1**   -  **Envoyer automatiquement des échantillons sécurisés**     |Le service Antivirus Microsoft Defender envoie tous les fichiers marqués comme « sûrs » et demande le reste des fichiers.         |
|**2**  -  **Ne jamais envoyer**      |Le service Antivirus Microsoft Defender n’invite pas et n’envoie aucun fichier.         |
|**3**  -  **Envoyer tous les échantillons automatiquement**     |Le service Antivirus Microsoft Defender envoie tous les fichiers sans invite de confirmation.         |

## <a name="configure-automatic-exclusions"></a>Configurer les exclusions automatiques

Pour garantir la sécurité et les performances, certaines exclusions sont automatiquement ajoutées en fonction des rôles et des fonctionnalités que vous installez lors de l’utilisation de Antivirus Microsoft Defender sur Windows Server 2016 ou 2019.

Voir [Configurer les exclusions dans Antivirus Microsoft Defender sur Windows Server.](configure-server-exclusions-microsoft-defender-antivirus.md) 

## <a name="need-to-set-microsoft-defender-antivirus-to-passive-mode"></a>Vous devez définir Antivirus Microsoft Defender en mode passif ?

Si vous utilisez un produit antivirus non Microsoft comme solution antivirus principale sur Windows Server, vous devez définir Antivirus Microsoft Defender sur le mode passif ou désactivé.

- Sur Windows Server, version 1803 ou plus récente, ou Windows Server 2019, vous pouvez définir Antivirus Microsoft Defender en mode passif.  

- Sur Windows Server 2016, Antivirus Microsoft Defender n’est pas pris en charge avec un produit antivirus/anti-programme malveillant non-Microsoft. Dans ce cas, vous devez définir Antivirus Microsoft Defender le mode désactivé.

### <a name="set-microsoft-defender-antivirus-to-passive-mode-using-a-registry-key"></a>Définir Antivirus Microsoft Defender mode passif à l’aide d’une clé de Registre

Si vous utilisez Windows Server, version 1803 ou Windows Server 2019, vous pouvez définir Antivirus Microsoft Defender en mode passif en réglant la clé de Registre suivante :
- Chemin d’accès : `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nom : `ForceDefenderPassiveMode`
- Type : `REG_DWORD`
- Valeur : `1`

### <a name="disable-microsoft-defender-antivirus-using-the-remove-roles-and-features-wizard"></a>Désactiver la Antivirus Microsoft Defender l’assistant Suppression de rôles et de fonctionnalités

1. Voir [Installer ou désinstaller des rôles, des services de rôles](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard)ou des fonctionnalités, et utiliser l’Assistant Suppression de rôles **et de fonctionnalités.** 

2. Lorsque vous arrivez à l’étape **Fonctionnalités** de l’Assistant, Windows Defender **l’option Fonctionnalités.** 

    Si vous supprimez **Windows Defender** vous-même sous la section **fonctionnalités Windows Defender,** vous serez invité à supprimer l’interface utilisateur graphique de l’option d’interface **Windows Defender**. 
    
    Antivirus Microsoft Defender s’exécutent toujours normalement sans l’interface utilisateur, mais l’interface utilisateur ne peut pas être activée si vous désactivez la fonctionnalité Windows Defender **principale.**

### <a name="turn-off-the-microsoft-defender-antivirus-user-interface-using-powershell"></a>Désactiver l’interface Antivirus Microsoft Defender’utilisateur à l’aide de PowerShell

Pour désactiver l’interface Antivirus Microsoft Defender graphique graphique, utilisez l’cmdlet PowerShell suivante :

```PowerShell
Uninstall-WindowsFeature -Name Windows-Defender-GUI
```

### <a name="are-you-using-windows-server-2016"></a>Utilisez-vous Windows Server 2016 ?

Si vous utilisez Windows Server 2016 et un logiciel anti-programme malveillant/antivirus tiers qui n’est pas proposé ou développé par Microsoft, vous devez désactiver/désinstaller Antivirus Microsoft Defender. 

> [!NOTE]
> Vous ne pouvez pas désinstaller Sécurité Windows’application, mais vous pouvez désactiver l’interface avec ces instructions.

L’cmdlet PowerShell suivante désinstalle Antivirus Microsoft Defender sur Windows Server 2016 :

```PowerShell
Uninstall-WindowsFeature -Name Windows-Defender
```

Pour désactiver la Antivirus Microsoft Defender sur Windows Server 2016, utilisez l’cmdlet PowerShell suivante :

```PowerShell
Set-MpPreference -DisableRealtimeMonitoring $true
```

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Antivirus Microsoft Defender compatibilité](microsoft-defender-antivirus-compatibility.md)
