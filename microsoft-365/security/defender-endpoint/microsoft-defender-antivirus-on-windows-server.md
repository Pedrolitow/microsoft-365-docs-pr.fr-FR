---
title: Antivirus Microsoft Defender sur Windows Server
description: Découvrez comment activer et configurer l'Antivirus Microsoft Defender sur Windows Server 2016 et Windows Server 2019.
keywords: windows defender, serveur, scep, system center endpoint protection, server 2016, current branch, server 2012
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr, shwjha
manager: dansimp
ms.technology: mde
ms.openlocfilehash: d9452b6d2eeaad3880894b9ec66c8bc71797b429
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51764602"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Antivirus Microsoft Defender sur Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

L'Antivirus Microsoft Defender est disponible sur les éditions/versions suivantes de Windows Server :
- Windows Server 2019
- Windows Server, version 1803 ou ultérieure
- Windows Server 2016. 

Dans certains cas, l'Antivirus Microsoft Defender est appelé *Endpoint Protection*; toutefois, le moteur de protection est le même. Bien que les fonctionnalités, la configuration et la gestion soient en grande partie identiques pour l'Antivirus Microsoft Defender sur [Windows 10,](microsoft-defender-antivirus-in-windows-10.md)il existe quelques différences clés sur Windows Server :

- Dans Windows Server, les [exclusions automatiques](configure-server-exclusions-microsoft-defender-antivirus.md) sont appliquées en fonction de votre rôle serveur défini.
- Dans Windows Server, l'Antivirus Microsoft Defender ne se désactive pas automatiquement si vous exécutez un autre produit antivirus.

## <a name="the-process-at-a-glance"></a>Le processus en un clin d’œil

Le processus de configuration et d'exécution de l'Antivirus Microsoft Defender sur une plateforme de serveur comprend plusieurs étapes :

1. [Activez l'interface.](#enable-the-user-interface-on-windows-server)
2. [Installez l'Antivirus Microsoft Defender.](#install-microsoft-defender-antivirus-on-windows-server)
3. [Vérifiez que l'Antivirus Microsoft Defender est en cours d'exécution.](#verify-microsoft-defender-antivirus-is-running)
4. [Mettez à jour votre intelligence de sécurité anti-programme malveillant.](#update-antimalware-security-intelligence)
5. (Selon les besoins) [Envoyer des exemples.](#submit-samples)
6. (Selon les besoins) [Configurer les exclusions automatiques.](#configure-automatic-exclusions)
7. (Uniquement si nécessaire) [Définissez l'Antivirus Microsoft Defender sur le mode passif.](#need-to-set-microsoft-defender-antivirus-to-passive-mode)

## <a name="enable-the-user-interface-on-windows-server"></a>Activer l'interface utilisateur sur Windows Server

Par défaut, l'Antivirus Microsoft Defender est installé et fonctionnel sur Windows Server. L'interface utilisateur (GUI) est installée par défaut sur certaines SSO, mais elle n'est pas obligatoire, car vous pouvez utiliser PowerShell ou d'autres méthodes pour gérer l'Antivirus Microsoft Defender. Si l'interface graphique graphique n'est pas installée  sur votre serveur, vous pouvez l'ajouter à l'aide de l'Assistant Ajout de rôles et de fonctionnalités, ou à l'aide des cmdlets PowerShell.

### <a name="turn-on-the-gui-using-the-add-roles-and-features-wizard"></a>Activer l'interface graphique à l'aide de l'Assistant Ajout de rôles et de fonctionnalités

1. Voir [Installer des rôles, des services de rôles](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard)et des fonctionnalités à l'aide de l'Assistant Ajout de rôles et de fonctionnalités et utiliser l'Assistant Ajout de **rôles et de fonctionnalités.**

2. Lorsque vous arrivez à l'étape **Fonctionnalités** de l'Assistant, sous Windows Defender **fonctionnalités,** sélectionnez l'interface graphique graphique pour **Windows Defender'option.**

   Dans Windows Server 2016, l'Assistant Ajout de rôles et de **fonctionnalités** se présente comme ceci :

   ![Assistant Ajout de rôles et de fonctionnalités affichant l'interface graphique graphique Windows Defender'option](images/server-add-gui.png)

   Dans Windows Server 2019, l'Assistant Ajout de **rôles** et de fonctionnalités est similaire.

### <a name="turn-on-the-gui-using-powershell"></a>Activer l'interface graphique graphique à l'aide de PowerShell

L'cmdlet PowerShell suivante active l'interface : 

```PowerShell
Install-WindowsFeature -Name Windows-Defender-GUI
```

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Installer l'Antivirus Microsoft Defender sur Windows Server

Vous pouvez utiliser l'Assistant Ajout de **rôles et** de fonctionnalités ou PowerShell pour installer l'Antivirus Microsoft Defender.

### <a name="use-the-add-roles-and-features-wizard"></a>Utiliser l'Assistant Ajout de rôles et de fonctionnalités

1. Reportez-vous [à cet article](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard)et utilisez l'Assistant Ajout de **rôles et de fonctionnalités.**

2. Lorsque vous arrivez à l'étape **Fonctionnalités** de l'Assistant, sélectionnez l'option Antivirus Microsoft Defender. Sélectionnez également **l'interface graphique graphique Windows Defender** option.

### <a name="use-powershell"></a>Utiliser PowerShell

Pour utiliser PowerShell afin d'installer l'Antivirus Microsoft Defender, exécutez l'cmdlet suivante :

```PowerShell
Install-WindowsFeature -Name Windows-Defender
```

Les messages d'événement pour le moteur anti-programme malveillant inclus avec l'Antivirus Microsoft Defender sont disponibles dans les événements [de l'Antivirus Microsoft Defender.](troubleshoot-microsoft-defender-antivirus.md)


## <a name="verify-microsoft-defender-antivirus-is-running"></a>Vérifier que l'Antivirus Microsoft Defender est en cours d'exécution

Pour vérifier que l'Antivirus Microsoft Defender est en cours d'exécution sur votre serveur, exécutez l'cmdlet PowerShell suivante :

```PowerShell
Get-Service -Name windefend
```

Pour vérifier que la protection pare-feu est allumée, exécutez l'cmdlet PowerShell suivante :

```PowerShell 
Get-Service -Name mpssvc
```

En remplacement de PowerShell, vous pouvez utiliser l'invite de commandes pour vérifier que l'Antivirus Microsoft Defender est en cours d'exécution. Pour ce faire, exécutez la commande suivante à partir d'une invite de commandes : 

```console
sc query Windefend
```

La `sc query` commande retourne des informations sur le service Antivirus Microsoft Defender. Lorsque l'Antivirus Microsoft Defender est en cours d'exécution, `STATE` la valeur s'affiche. `RUNNING`

## <a name="update-antimalware-security-intelligence"></a>Mettre à jour l'intelligence de sécurité contre les programmes malveillants 

Pour obtenir des informations de sécurité contre les programmes malveillants mises à jour, le service Windows Update doit être en cours d'exécution. Si vous utilisez un service de gestion des mises à jour, tel que Windows Server Update Services (WSUS), assurez-vous que les mises à jour de l'intelligence de sécurité antivirus Microsoft Defender sont approuvées pour les ordinateurs que vous gérez.

Par défaut, Windows Update ne télécharge et n'installe pas automatiquement les mises à jour sur Windows Server 2019 ou Windows Server 2016. Vous pouvez modifier cette configuration à l'aide de l'une des méthodes suivantes :


|Méthode  |Description  |
|---------|---------|
|**Windows Update dans** le Panneau de contrôle     |- **L'installation des mises à** jour entraîne automatiquement l'installation automatique de toutes les mises à jour, y Windows Defender mises à jour de l'intelligence de sécurité. <br/>- **Téléchargez les** mises à jour, mais laissez-moi choisir de les installer, ce qui permet à Windows Defender de télécharger et d'installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement.       |
|**Stratégie de groupe**     | Vous pouvez configurer et gérer Windows Update à l'aide des paramètres disponibles dans la stratégie de groupe, dans le chemin d'accès suivant : **Modèles d'administration\Composants Windows\Windows Update\Configurer** les mises à jour automatiques         |
|Clé de Registre **AUOptions**     |Les deux valeurs suivantes permettent à Windows Update de télécharger et d'installer automatiquement les mises à jour d'informations de sécurité : <br/>- **4**  -  **Installez automatiquement les mises à jour.** Cette valeur entraîne l'installation automatique de toutes les mises à jour, y Windows Defender mises à jour d'informations de sécurité. <br/>- **3**  -  **Téléchargez les mises à jour, mais laissez-moi choisir s'il faut les installer.**  Cette valeur permet Windows Defender télécharger et installer automatiquement les mises à jour security intelligence, mais les autres mises à jour ne sont pas installées automatiquement.         |

Pour vous assurer que la protection contre les programmes malveillants est maintenue, nous vous recommandons d'activer les services suivants :

- Service de rapport d'erreurs Windows

- Service Windows Update

Le tableau suivant répertorie les services pour l'Antivirus Microsoft Defender et les services dépendants.

|Nom du service|Emplacement du fichier|Description|
|--------|---------|--------|
|Windows Defender Service (WinDefend)|`C:\Program Files\Windows Defender\MsMpEng.exe`|Il s'agit du service antivirus Microsoft Defender principal qui doit être en cours d'exécution en permanence.|
|Service de rapport d'erreurs Windows (Wersvc)|`C:\WINDOWS\System32\svchost.exe -k WerSvcGroup`|Ce service renvoie des rapports d'erreur à Microsoft.|
|Windows Defender Pare-feu (MpsSvc)|`C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork`|Nous vous recommandons de laisser le service Windows Defender pare-feu activé.|
|Windows Update (Wuauserv)|`C:\WINDOWS\system32\svchost.exe -k netsvcs`|Windows Update est nécessaire pour obtenir des mises à jour de l'intelligence de sécurité et des mises à jour du moteur anti-programme malveillant|

## <a name="submit-samples"></a>Envoyer des exemples

La soumission d'exemples permet à Microsoft de collecter des exemples de logiciels potentiellement malveillants. Pour assurer une protection continue et à jour, les chercheurs De Microsoft utilisent ces exemples pour analyser les activités suspectes et produire des informations de sécurité anti-programme malveillant mises à jour. Nous collectons les fichiers exécutables du programme, tels que les fichiers .exe et .dll. Nous ne collectons pas les fichiers qui contiennent des données personnelles, comme les documents Microsoft Word et les fichiers PDF.

### <a name="submit-a-file"></a>Envoyer un fichier

1. Examinez le [guide de soumission.](/windows/security/threat-protection/intelligence/submission-guide)

2. Visitez le [portail de soumission d'exemples](https://www.microsoft.com/wdsi/filesubmission)et envoyez votre fichier.


### <a name="enable-automatic-sample-submission"></a>Activer l'envoi automatique d'échantillons

Pour activer l'envoi automatique d'échantillons, démarrez une console Windows PowerShell en tant qu'administrateur et définissez les données de valeur **SubmitSamplesConsent** en fonction de l'un des paramètres suivants :

|Paramètre  |Description  |
|---------|---------|
|**0**  -  **Toujours invite**     |Le service Antivirus Microsoft Defender vous invite à confirmer l'envoi de tous les fichiers requis. Il s'agit du paramètre par défaut de l'Antivirus Microsoft Defender, mais il n'est pas recommandé pour les installations sur Windows Server 2016 ou 2019 sans interface utilisateur graphique.         |
|**1**   -  **Envoyer automatiquement des échantillons sécurisés**     |Le service Antivirus Microsoft Defender envoie tous les fichiers marqués comme « sûrs » et demande le reste des fichiers.         |
|**2**  -  **Ne jamais envoyer**      |Le service Antivirus Microsoft Defender n'invite pas et n'envoie aucun fichier.         |
|**3**  -  **Envoyer tous les échantillons automatiquement**     |Le service Antivirus Microsoft Defender envoie tous les fichiers sans invite de confirmation.         |

## <a name="configure-automatic-exclusions"></a>Configurer les exclusions automatiques

Pour garantir la sécurité et les performances, certaines exclusions sont automatiquement ajoutées en fonction des rôles et des fonctionnalités que vous installez lors de l'utilisation de l'Antivirus Microsoft Defender sur Windows Server 2016 ou 2019.

Voir [Configurer les exclusions dans l'Antivirus Microsoft Defender sur Windows Server.](configure-server-exclusions-microsoft-defender-antivirus.md) 

## <a name="need-to-set-microsoft-defender-antivirus-to-passive-mode"></a>Vous devez définir l'Antivirus Microsoft Defender en mode passif ?

Si vous utilisez un produit antivirus non Microsoft comme solution antivirus principale, définissez l'Antivirus Microsoft Defender sur le mode passif.  

### <a name="set-microsoft-defender-antivirus-to-passive-mode-using-a-registry-key"></a>Définir l'Antivirus Microsoft Defender en mode passif à l'aide d'une clé de Registre

Si vous utilisez Windows Server, version 1803 ou Windows Server 2019, vous pouvez définir l'Antivirus Microsoft Defender sur le mode passif en réglant la clé de Registre suivante :
- Chemin d'accès : `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nom : `ForcePassiveMode`
- Type : `REG_DWORD`
- Valeur : `1`

### <a name="disable-microsoft-defender-antivirus-using-the-remove-roles-and-features-wizard"></a>Désactiver l'Antivirus Microsoft Defender à l'aide de l'Assistant Suppression de rôles et de fonctionnalités

1. Voir [Installer ou désinstaller des rôles, des services de rôles](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard)ou des fonctionnalités, et utiliser l'Assistant Suppression de rôles **et de fonctionnalités.** 

2. Lorsque vous arrivez à l'étape **Fonctionnalités** de l'Assistant, Windows Defender **l'option Fonctionnalités.** 

    Si vous supprimez **Windows Defender** vous-même sous la section **Fonctionnalités Windows Defender,** vous serez invité à supprimer l'interface utilisateur graphique de l'option d'interface **Windows Defender**. 
    
    L'Antivirus Microsoft Defender s'exécute toujours **normalement** sans l'interface utilisateur, mais l'interface utilisateur ne peut pas être activée si vous désactivez la fonctionnalité Windows Defender principal.

### <a name="turn-off-the-microsoft-defender-antivirus-user-interface-using-powershell"></a>Désactiver l'interface utilisateur de l'Antivirus Microsoft Defender à l'aide de PowerShell

Pour désactiver l'interface graphique de l'Antivirus Microsoft Defender, utilisez l'cmdlet PowerShell suivante :

```PowerShell
Uninstall-WindowsFeature -Name Windows-Defender-GUI
```

### <a name="are-you-using-windows-server-2016"></a>Utilisez-vous Windows Server 2016 ?

Si vous utilisez Windows Server 2016 et un produit antivirus/anti-programme malveillant tiers qui n'est pas proposé ou développé par Microsoft, vous devez désactiver/désinstaller l'Antivirus Microsoft Defender. 

> [!NOTE]
> Vous ne pouvez pas désinstaller l'application Sécurité Windows, mais vous pouvez désactiver l'interface avec ces instructions.

L'cmdlet PowerShell suivante désinstalle l'Antivirus Microsoft Defender sur Windows Server 2016 :

```PowerShell
Uninstall-WindowsFeature -Name Windows-Defender
```

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Compatibilité de l'Antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md)