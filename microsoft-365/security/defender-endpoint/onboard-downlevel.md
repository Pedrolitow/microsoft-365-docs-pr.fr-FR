---
title: Intégrer des versions antérieures de Windows sur Microsoft Defender pour point de terminaison
description: Intégrer les versions antérieures prises en charge des appareils Windows afin qu’ils puissent envoyer des données de capteur au capteur Microsoft Defender pour point de terminaison
keywords: onboard, windows, 7, 81, oms, sp1, enterprise, pro, down level
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8ca88340ae90889c0e45c5905863373d930949b2
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872959"
---
# <a name="onboard-previous-versions-of-windows"></a>Intégrer des versions antérieures de Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateformes**

- Windows 7 Enterprise SP1
- Windows 7 Pro SP1
- Windows 8.1 Professionnel
- Windows 8.1 Entreprise
- Windows Server 2008 R2 SP1

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

Defender pour point de terminaison étend la prise en charge pour inclure des systèmes d’exploitation de bas niveau, fournissant des fonctionnalités avancées de détection des attaques et d’investigation sur les versions Windows prises en charge.

Pour intégrer des points de terminaison clients Windows de bas niveau à Defender pour point de terminaison, vous devez :

- [Configurer et mettre à jour System Center Endpoint Protection clients](#configure-and-update-system-center-endpoint-protection-clients)
- [Installer et configurer Microsoft Monitoring Agent (MMA) pour signaler des données de capteur](#install-and-configure-microsoft-monitoring-agent-mma)

Pour Windows Server 2008 R2 SP1, vous avez la possibilité [d’intégrer via Microsoft Defender pour le cloud](#onboard-windows-servers-through-microsoft-defender-for-cloud).

> [!NOTE]
> Une licence serveur autonome Defender pour point de terminaison est requise, par nœud, pour intégrer un serveur Windows via Microsoft Monitoring Agent (option 1). Une licence Microsoft Defender pour serveurs est également nécessaire, par nœud, pour intégrer un serveur Windows via Microsoft Defender pour le cloud (option 2), consultez [les fonctionnalités prises en charge disponibles dans Microsoft Defender pour le cloud](/azure/defender-for-cloud/supported-machines-endpoint-solutions-clouds-servers).

> [!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’il est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un point de terminaison Defender pour point de terminaison nouvellement intégré](run-detection-test.md).

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>Configurer et mettre à jour System Center Endpoint Protection clients

> [!IMPORTANT]
> Cette étape n’est requise que si votre organisation utilise System Center Endpoint Protection (SCEP).

Defender pour point de terminaison s’intègre à System Center Endpoint Protection pour fournir une visibilité aux détections de programmes malveillants et pour arrêter la propagation d’une attaque dans votre organisation en interdisant les fichiers potentiellement malveillants ou les programmes malveillants suspects.

Les étapes suivantes sont requises pour activer cette intégration :

- Installer la [mise à jour de la plateforme anti-programme malveillant de janvier 2017 pour les clients Endpoint Protection](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie)
- Configurer l’appartenance du service de protection cloud du client SCEP au paramètre **Avancé**
- Configurez votre réseau pour autoriser les connexions au cloud Antivirus Microsoft Defender. Pour plus d’informations, consultez [Configurer et valider Antivirus Microsoft Defender connexions réseau](/microsoft-365/security/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## <a name="install-and-configure-microsoft-monitoring-agent-mma"></a>Installer et configurer Microsoft Monitoring Agent (MMA)

### <a name="before-you-begin"></a>Avant de commencer

Passez en revue les détails suivants pour vérifier la configuration minimale requise :

- Installer le [correctif cumulatif mensuel de février 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)

  > [!NOTE]
  > Applicable uniquement pour Windows Server 2008 R2, Windows 7 Enterprise SP1 et Windows 7 Pro SP1.

- Installer la [mise à jour pour l’expérience client et la télémétrie de diagnostic](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- Installer [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (ou version ultérieure) ou [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

    > [!NOTE]
    > Applicable uniquement pour Windows Server 2008 R2, Windows 7 Enterprise SP1 et Windows 7 Pro SP1.
    >
    > N’installez pas .NET Framework 4.0.x, car il annule l’installation ci-dessus.
    >
    > L’installation de .NET 4.5 peut vous obliger à redémarrer votre ordinateur après l’installation.

- Répondez à la configuration système minimale requise pour l’agent Azure Log Analytics. Pour plus d’informations, consultez [Collecter des données à partir d’ordinateurs de votre environnement avec Log Analytics](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites)

### <a name="installation-steps"></a>Étapes d'installation

1. Téléchargez le fichier d’installation de l’agent : [Windows agent 64 bits](https://go.microsoft.com/fwlink/?LinkId=828603) ou [Windows agent 32 bits](https://go.microsoft.com/fwlink/?LinkId=828604).

    >[!NOTE]
    >En raison [de la dépréciation de la prise en charge de SHA-1 par l’agent MMA](/azure/azure-monitor/agents/agent-windows#sha-2-code-signing-support-requirement), l’agent MMA doit être version 10.20.18029 ou ultérieure.
    

2. Obtenez l’ID d’espace de travail :
   - Dans le volet de navigation Defender pour point de terminaison, sélectionnez **Paramètres > Gestion des appareils > Intégration**
   - Sélectionner le système d’exploitation
   - Copier l’ID d’espace de travail et la clé d’espace de travail

3. À l’aide de l’ID d’espace de travail et de la clé d’espace de travail, choisissez l’une des méthodes d’installation suivantes pour installer l’agent :
    - [Installez manuellement l’agent à l’aide de l’installation](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard).

      Dans la page **Options d’installation** de **l’agent, sélectionnez Connecter l’agent dans Azure Log Analytics (OMS)**

    - [Installez l’agent à l’aide de la ligne de commande](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line).
    - [Configurez l’agent à l’aide d’un script](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation).

   > [!NOTE]
   > Si vous êtes un [client du gouvernement des États-Unis](gov.md), sous « Azure Cloud », vous devez choisir « Azure US Government » si vous utilisez l’Assistant Installation, ou si vous utilisez une ligne de commande ou un script, définissez le paramètre « OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE » sur 1.

4. Si vous utilisez un proxy pour vous connecter à Internet, consultez la section Configurer le proxy et les paramètres de connectivité Internet.

Une fois l’opération terminée, vous devez voir les points de terminaison intégrés dans le portail dans une heure.

## <a name="configure-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy et de connectivité Internet
Si vos serveurs doivent utiliser un proxy pour communiquer avec Defender pour point de terminaison, utilisez l’une des méthodes suivantes pour configurer MMA afin d’utiliser le serveur proxy :

- [Configurer MMA pour utiliser un serveur proxy](/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [Configurer Windows pour utiliser un serveur proxy pour toutes les connexions](configure-proxy-internet.md)

Si un proxy ou un pare-feu est utilisé, assurez-vous que les serveurs peuvent accéder à toutes les URL de service Microsoft Defender pour point de terminaison directement et sans interception SSL. Pour plus d’informations, consultez [Activer l’accès aux URL du service Defender pour point de terminaison](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). L’utilisation de l’interception SSL empêche le système de communiquer avec le service Defender pour point de terminaison.

Une fois l’opération terminée, vous devez voir les serveurs Windows intégrés dans le portail dans une heure.

## <a name="onboard-windows-servers-through-microsoft-defender-for-cloud"></a>Intégrer des serveurs Windows via Microsoft Defender pour le cloud

1. Dans le volet de navigation Microsoft 365 Defender, sélectionnez **Paramètres** >  **Device management** > **Onboarding**.

2. Sélectionnez **Windows Server 2008 R2 SP1** comme système d’exploitation.

3. Cliquez sur **Serveurs intégrés dans Microsoft Defender pour le cloud**.

4. Suivez les instructions d’intégration dans [Microsoft Defender pour point de terminaison avec Microsoft Defender pour le cloud](/azure/security-center/security-center-wdatp) et si vous utilisez Azure ARC, suivez les instructions d’intégration dans [l’activation de intégration Microsoft Defender pour point de terminaison](/azure/security-center/security-center-wdatp#enabling-the-microsoft-defender-for-endpoint-integration).

Une fois les étapes d’intégration terminées, vous devez [configurer et mettre à jour System Center Endpoint Protection clients](#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
>
> - Pour que l’intégration via Microsoft Defender pour que les serveurs fonctionnent comme prévu, le serveur doit disposer d’un espace de travail et d’une clé appropriés configurés dans les paramètres Microsoft Monitoring Agent (MMA).
> - Une fois configuré, le pack d’administration cloud approprié est déployé sur l’ordinateur et le processus de capteur (MsSenseS.exe) est déployé et démarré.
> - Cela est également nécessaire si le serveur est configuré pour utiliser un serveur de passerelle OMS en tant que proxy.



## <a name="verify-onboarding"></a>Vérifier l’intégration

Vérifiez que Microsoft Defender AV et Microsoft Defender pour point de terminaison sont en cours d’exécution. 

> [!NOTE]
> L’exécution de Microsoft Defender AV n’est pas obligatoire, mais elle est recommandée. Si un autre produit du fournisseur d’antivirus est la solution principale de protection des points de terminaison, vous pouvez exécuter l’antivirus Defender en mode passif. Vous pouvez uniquement confirmer que le mode passif est activé après avoir vérifié que Microsoft Defender pour point de terminaison capteur (SENSE) est en cours d’exécution. 

1. Exécutez la commande suivante pour vérifier que Microsoft Defender AV est installé :

   ```sc.exe query Windefend```

    Si le résultat est « Le service spécifié n’existe pas en tant que service installé », vous devez installer Microsoft Defender AV. Pour plus d’informations, consultez [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-windows.md).

    Pour plus d’informations sur l’utilisation de stratégie de groupe pour configurer et gérer des Antivirus Microsoft Defender sur vos serveurs Windows, consultez [Utiliser stratégie de groupe paramètres pour configurer et gérer Antivirus Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md).


2. Exécutez la commande suivante pour vérifier que Microsoft Defender pour point de terminaison est en cours d’exécution :

    ```sc.exe query sense```
    
    Le résultat doit indiquer qu’il est en cours d’exécution. Si vous rencontrez des problèmes d’intégration, consultez [Résolution des problèmes d’intégration](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Exécuter un test de détection
Suivez les étapes décrites dans [Exécuter un test de détection sur un appareil nouvellement intégré](run-detection-test.md) pour vérifier que le serveur fait rapport à Defender pour le service point de terminaison.





## <a name="onboarding-endpoints-with-no-management-solution"></a>Intégration de points de terminaison sans solution de gestion 

### <a name="using-group-policy"></a>Utilisation de la stratégie de groupe

**Étape 1 : Téléchargez l’udpate correspondant pour votre point de terminaison.**

1. Accédez à c:\windows\sysvol\domain\scripts (le contrôle de modification peut être nécessaire sur l’un des contrôleurs de domaine.)
1. Créez un dossier nommé MMA.
1. Téléchargez les éléments suivants et placez-les dans le dossier MMA :
   
    - Mise à jour pour l’expérience client et la télémétrie de diagnostic :
      - [Pour Windows Server 2008 R2 x64](https://www.microsoft.com/download/details.aspx?familyid=1bd1d18d-4631-4d8e-a897-327925765f71)
     
    Pour Windows Server 2008 R2 SP1, les mises à jour suivantes sont également requises :

    Cumul mensuel de février 2018 - KB4074598 (Windows Server 2008 R2)

    [Catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)<br>
    Télécharger les mises à jour pour Windows Server 2008 R2 x64
    
    .NET Framework 3.5.1 (KB315418)<br>
    [Pour Windows Server 2008 R2 x64](/iis/install/installing-iis-7/install-windows-server-2008-and-windows-server-2008-r2)
    
    >[!NOTE]
    > Cet article part du principe que vous utilisez des serveurs x64 (agent MMA .exe nouvelle version compatible SHA-2 x64).


**Étape 2 : Créer un nom de fichier DeployMMA.cmd (à l’aide du bloc-notes)** Ajoutez les lignes suivantes au fichier cmd. Notez que vous aurez besoin de votre ID d’espace de travail et de votre clé.

La commande suivante est un exemple. Remplacez les valeurs suivantes :
- Base de connaissances : utilisez la base de connaissances applicable pour le point de terminaison que vous intègrez
- ID d’espace de travail et CLÉ - Utiliser votre ID et votre clé


```dos
@echo off 
cd "C:"
IF EXIST "C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe" ( 
exit
) ELSE (

wusa.exe C:\Windows\MMA\Windows6.1-KB3080149-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows6.1-KB4074598-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows6.1-KB3154518-x64.msu /quiet /norestart
wusa.exe C:\Windows\MMA\Windows8.1-KB3080149-x64.msu /quiet /norestart
"c:\windows\MMA\MMASetup-AMD64.exe" /c /t: "C:\Windows\MMA"c:\windows\MMA\ setup.exe /qn NOAPM=1 ADD_OPINSIGHTS_WORKSPACE=1
OPINSIGHTS_WORKSPACE_ID="<your workspace ID>"
OPINSIGHTS_WORKSPACE_KEY="<your workspace key>" AcceptEndUserLicenseAgreement=1
)

)
```





### <a name="group-policy-configuration"></a>configuration stratégie de groupe

Créez une stratégie de groupe spécifiquement pour l’intégration d’appareils tels que « Microsoft Defender pour point de terminaison Intégration ».

- Créer un dossier stratégie de groupe nommé « c:\windows\MMA »

     :::image type="content" source="images/grppolicyconfig1.png" alt-text="Emplacement des dossiers" lightbox="images/grppolicyconfig1.png":::

    **Cela ajoute un nouveau dossier sur chaque serveur qui obtient l’objet de stratégie de groupe appliqué, appelé MMA, et sera stocké dans c:\windows. Cela contiendra les fichiers d’installation du MMA, les prérequis et le script d’installation.**

- Créez une préférence stratégie de groupe Files pour chacun des fichiers stockés dans l’ouverture de session Net.

     :::image type="content" source="images/grppolicyconfig2.png" alt-text="Stratégie de groupe - 1" lightbox="images/grppolicyconfig2.png":::

Il copie les fichiers de DOMAIN\NETLOGON\MMA\filename vers C:\windows\MMA\filename. Les **fichiers d’installation sont donc locaux sur le serveur** :

:::image type="content" source="images/deploymma.png" alt-text="Propriétés de la cmd mma de déploiement" lightbox="images/deploymma.png":::

Répétez le processus, mais créez un ciblage au niveau de l’élément sous l’onglet COMMON, afin que le fichier soit copié uniquement dans la version appropriée de la plateforme/du système d’exploitation dans l’étendue :

:::image type="content" source="images/targeteditor.png" alt-text="Éditeur cible" lightbox="images/targeteditor.png":::

Pour Windows Server 2008 R2, vous avez besoin (et il ne sera copié que vers le bas) les éléments suivants :
- Windows6.1-KB3080149-x64.msu
- Windows6.1-KB3154518-x64.msu
- Windows6.1-KB4075598-x64.msu


Une fois cette opération effectuée, vous devez créer une stratégie de script de démarrage :

:::image type="content" source="images/startupprops.png" alt-text="Propriétés de démarrage" lightbox="images/startupprops.png":::

Le nom du fichier à exécuter ici est c:\windows\MMA\DeployMMA.cmd.
Une fois le serveur redémarré dans le cadre du processus de démarrage, il installe la mise à jour pour l’expérience client et la base de connaissances de télémétrie de diagnostic, puis installe l’agent MMA, tout en définissant l’ID et la clé de l’espace de travail, et le serveur est intégré.

Vous pouvez également utiliser une **tâche immédiate** pour exécuter deployMMA.cmd si vous ne souhaitez pas redémarrer tous les serveurs.

Cette opération peut être effectuée en deux phases. Commencez par créer **les fichiers et le dossier dans l’objet** de stratégie de groupe : donnez au système le temps de s’assurer que l’objet de stratégie de groupe a été appliqué et que tous les serveurs disposent des fichiers d’installation. Ajoutez ensuite la tâche immédiate. Cela permet d’obtenir le même résultat sans avoir besoin d’un redémarrage.

Étant donné que le script a une méthode de sortie et ne sera pas réexécuter si le MMA est installé, vous pouvez également utiliser une tâche planifiée quotidienne pour obtenir le même résultat. À l’instar d’une stratégie de conformité Configuration Manager, elle vérifie quotidiennement la présence de MMA.

:::image type="content" source="images/schtask.png" alt-text="tâche de planification" lightbox="images/schtask.png":::

:::image type="content" source="images/newtaskprops.png" alt-text="Propriétés des nouvelles tâches" lightbox="images/newtaskprops.png":::

:::image type="content" source="images/deploymmadowmload.png" alt-text="Propriétés de téléchargement mma de déploiement" lightbox="images/deploymmadowmload.png":::

:::image type="content" source="images/tasksch.png" alt-text="Planificateur de tâches" lightbox="images/tasksch.png":::

Comme indiqué dans la documentation d’intégration pour Server, plus précisément autour de Server 2008 R2, consultez ci-dessous : Pour Windows Server 2008 R2 SP1, vérifiez que vous remplissez les conditions suivantes :

- Installer le [correctif cumulatif mensuel de février 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
- Installer [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (ou version ultérieure) ou [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

Vérifiez que les bases de connaissances sont présentes avant d’intégrer Windows Server 2008 R2. Ce processus vous permet d’intégrer tous les serveurs si vous n’avez pas Configuration Manager gérer les serveurs.


## <a name="offboard-endpoints"></a>Points de terminaison hors-bord

Vous avez deux options pour déconnecter Windows points de terminaison du service :

- Désinstaller l’agent MMA
- Supprimer la configuration de l’espace de travail Defender pour point de terminaison

> [!NOTE]
> La désintégration entraîne l’arrêt de l’envoi de données de capteur au portail par le point de terminaison Windows, mais les données du point de terminaison, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois maximum.

### <a name="uninstall-the-mma-agent"></a>Désinstaller l’agent MMA

Pour déconnecter le point de terminaison Windows, vous pouvez désinstaller l’agent MMA ou le détacher de la création de rapports à votre espace de travail Defender pour point de terminaison. Après la désinstégation de l’agent, le point de terminaison n’envoie plus de données de capteur à Defender pour point de terminaison.
Pour plus d’informations, consultez [Pour désactiver un agent](/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent).

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>Supprimer la configuration de l’espace de travail Defender pour point de terminaison

Vous pouvez utiliser l’une des méthodes suivantes :

- Supprimer la configuration de l’espace de travail Defender pour point de terminaison de l’agent MMA
- Exécuter une commande PowerShell pour supprimer la configuration

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>Supprimer la configuration de l’espace de travail Defender pour point de terminaison de l’agent MMA

1. Dans **l’Microsoft Monitoring Agent Propriétés**, sélectionnez l’onglet **Azure Log Analytics (OMS**).

2. Sélectionnez l’espace de travail Defender pour point de terminaison, puis cliquez sur **Supprimer**.

    :::image type="content" source="images/atp-mma.png" alt-text="Volet Espaces de travail" lightbox="images/atp-mma.png":::

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>Exécuter une commande PowerShell pour supprimer la configuration

1. Obtenez votre ID d’espace de travail :

   1. Dans le volet de navigation, sélectionnez **Paramètres** >  **Onboarding**.

   1. Sélectionnez le système d’exploitation approprié et obtenez votre ID d’espace de travail.

    
2. Ouvrez un PowerShell avec élévation de privilèges et exécutez la commande suivante. Utilisez l’ID d’espace de travail que vous avez obtenu et remplacez `WorkspaceID`:

    ```   
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```
