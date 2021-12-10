---
title: Intégrer les versions précédentes de Windows sur Microsoft Defender for Endpoint
description: Intégrer des versions antérieures de Windows pris en charge afin qu’ils peuvent envoyer des données de capteur au capteur Microsoft Defender pour endpoint
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
ms.openlocfilehash: 39e01e614ebe2467899f179bc1ef3905ac0ca388
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61164909"
---
# <a name="onboard-previous-versions-of-windows"></a>Intégrer des versions antérieures de Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateformes**

- Windows 7 SP1 Enterprise
- Windows 7 SP1 Pro
- Windows 8.1 Professionnel
- Windows 8.1 Entreprise
- Windows Server 2008 R2 SP1

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

Defender for Endpoint étend la prise en charge pour inclure des systèmes d’exploitation de bas niveau, fournissant des fonctionnalités avancées de détection d’attaques et d’investigation sur les versions Windows pris en charge.

Pour intégrer des points de terminaison Windows client de niveau inférieur à Defender for Endpoint, vous devez :

- [Configurer et mettre à jour System Center Endpoint Protection clients](#configure-and-update-system-center-endpoint-protection-clients)
- [Installer et configurer Microsoft Monitoring Agent (MMA) pour signaler les données du capteur](#install-and-configure-microsoft-monitoring-agent-mma)

Pour Windows Server 2008 R2 SP1, vous avez la possibilité d’intégrer via [Microsoft Defender pour le Cloud.](#onboard-windows-servers-through-microsoft-defender-for-cloud)

> [!NOTE]
> Une licence de serveur autonome Defender pour point de terminaison est requise, par nœud, pour intégrer un serveur Windows via Microsoft Monitoring Agent (option 1). Une licence Microsoft Defender pour les serveurs est également requise, par nœud, pour intégrer un serveur Windows via Microsoft Defender pour le cloud (option 2), voir Fonctionnalités prise en charge disponibles dans [Microsoft Defender pour le Cloud.](/azure/security-center/security-center-services)

> [!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’il est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un point de terminaison [Defender pour point de terminaison nouvellement intégré.](run-detection-test.md)

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>Configurer et mettre à jour System Center Endpoint Protection clients

> [!IMPORTANT]
> Cette étape est requise uniquement si votre organisation utilise System Center Endpoint Protection (SCEP).

Defender pour le point de terminaison s’intègre à System Center Endpoint Protection pour fournir une visibilité aux détections de programmes malveillants et pour arrêter la propagation d’une attaque dans votre organisation en interdit les fichiers potentiellement malveillants ou les programmes malveillants suspects.

Les étapes suivantes sont nécessaires pour activer cette intégration :

- Installer la mise à jour de la plateforme anti-programme malveillant de janvier [2017 pour Endpoint Protection clients](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie)
- Configurer l’appartenance au service protection cloud client SCEP sur le **paramètre** Avancé
- Configurez votre réseau pour autoriser les connexions au Antivirus Microsoft Defender cloud. Pour plus d’informations, voir Configurer et [valider Antivirus Microsoft Defender connexions réseau](/microsoft-365/security/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## <a name="install-and-configure-microsoft-monitoring-agent-mma"></a>Installer et configurer Microsoft Monitoring Agent (MMA)

### <a name="before-you-begin"></a>Avant de commencer

Examinez les détails suivants pour vérifier la minimale requise :

- Installer le rapport de mise à jour mensuelle de [février 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)

  > [!NOTE]
  > Applicable uniquement pour Windows Server 2008 R2, Windows 7 SP1 Enterprise et Windows 7 SP1 Pro.

- Installer la mise [à jour pour la télémétrie d’expérience client et de diagnostic](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- Installer [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (ou ultérieur) ou [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

    > [!NOTE]
    > Applicable uniquement pour Windows Server 2008 R2, Windows 7 SP1 Enterprise et Windows 7 SP1 Pro.
    >
    > N’installez pas .NET Framework 4.0.x, car cela va annuler l’installation ci-dessus.
    >
    > L’installation de .NET 4.5 peut nécessiter le redémarrage de votre ordinateur après l’installation.

- Respectez la taille minimale requise de l’agent Azure Log Analytics. Pour plus d’informations, voir [Collecter des données à partir d’ordinateurs](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites) dans votre environnement avec Log Analytics

### <a name="installation-steps"></a>Étapes d'installation

1. Téléchargez le fichier de configuration de [l’agent : Windows agent 64 bits](https://go.microsoft.com/fwlink/?LinkId=828603) ou Windows agent [32 bits.](https://go.microsoft.com/fwlink/?LinkId=828604)

2. Obtenez l’ID de l’espace de travail :
   - Dans le volet de navigation Defender pour les points de terminaison, sélectionnez Paramètres > **gestion des > l’intégration**
   - Sélectionner le système d’exploitation
   - Copier l’ID d’espace de travail et la clé d’espace de travail

3. À l’aide de l’ID d’espace de travail et de la clé d’espace de travail, choisissez l’une des méthodes d’installation suivantes pour installer l’agent :
    - [Installer manuellement l’agent à l’aide du programme d’installation.](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard)

      Dans la page **Options de configuration** de l’agent, **sélectionnez Connecter l’agent dans Azure Log Analytics (OMS)**

    - [Installez l’agent à l’aide de la ligne de commande.](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line)
    - [Configurez l’agent à l’aide d’un script.](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation)

   > [!NOTE]
   > Si vous êtes un client du gouvernement [américain,](gov.md)sous « Azure Cloud », vous devez choisir « Azure US Government » si vous utilisez l’Assistant Installation, ou si vous utilisez une ligne de commande ou un script , définissez le paramètre « OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE » sur 1.

4. Si vous utilisez un proxy pour vous connecter à Internet, consultez la section Configurer les paramètres de proxy et de connectivité Internet.

Une fois terminé, vous devriez voir les points de terminaison intégrés dans le portail dans un délai d’une heure.

## <a name="configure-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy et de connectivité Internet
Si vos serveurs doivent utiliser un proxy pour communiquer avec Defender pour le point de terminaison, utilisez l’une des méthodes suivantes pour configurer MMA afin qu’il utilise le serveur proxy :

- [Configurer MMA pour utiliser un serveur proxy](/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [Configurer Windows pour utiliser un serveur proxy pour toutes les connexions](configure-proxy-internet.md)

Si un proxy ou un pare-feu est en cours d’utilisation, assurez-vous que les serveurs peuvent accéder à toutes les URL du service Microsoft Defender for Endpoint directement et sans interception SSL. Pour plus d’informations, voir [activer l’accès aux URL du service Defender for Endpoint.](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) L’utilisation de l’interception SSL empêche le système de communiquer avec le service Defender for Endpoint.

Une fois terminé, vous devriez voir les serveurs Windows intégrés dans le portail dans un délai d’une heure.

## <a name="onboard-windows-servers-through-microsoft-defender-for-cloud"></a>Intégrer Windows serveurs de messagerie via Microsoft Defender pour le cloud

1. Dans le volet Centre de sécurité Microsoft Defender navigation, **sélectionnez** Paramètres  >  **intégration de la gestion des**  >  **appareils.**

2. Sélectionnez **Windows Server 2008 R2 SP1** comme système d’exploitation.

3. Cliquez **sur Serveurs intégrés dans Microsoft Defender pour le cloud.**

4. Suivez les instructions d’intégration dans [Microsoft Defender pour point](/azure/security-center/security-center-wdatp) de terminaison avec Microsoft Defender pour le cloud et si vous utilisez Azure ARC, suivez les instructions d’intégration dans l’activation de Microsoft Defender pour l’intégration de Point de [terminaison.](/azure/security-center/security-center-wdatp#enabling-the-microsoft-defender-for-endpoint-integration)

Après avoir effectué les étapes d’intégration, vous devez configurer et mettre à jour [System Center Endpoint Protection clients.](#configure-and-update-system-center-endpoint-protection-clients)

> [!NOTE]
>
> - Pour que l’intégration via Microsoft Defender fonctionne comme prévu, le serveur doit avoir un espace de travail et une clé appropriés configurés dans les paramètres Microsoft Monitoring Agent (MMA).
> - Une fois configuré, le pack d’administration cloud approprié est déployé sur l’ordinateur et le processus de capteur (MsSenseS.exe) est déployé et démarré.
> - Cette configuration est également requise si le serveur est configuré pour utiliser un serveur de passerelle OMS comme proxy.



## <a name="verify-onboarding"></a>Vérifier l’intégration

Vérifiez que Microsoft Defender AV et Microsoft Defender pour le point de terminaison sont en cours d’exécution. 

> [!NOTE]
> L’exécution de Microsoft Defender AV n’est pas requise, mais elle est recommandée. Si un autre produit fournisseur d’antivirus est la solution de protection de point de terminaison principale, vous pouvez exécuter l’Antivirus Defender en mode passif. Vous pouvez uniquement confirmer que le mode passif est en cours d’exécution après avoir vérifié que le capteur Sense (Microsoft Defender for Endpoint) est en cours d’exécution. 

1. Exécutez la commande suivante pour vérifier que Microsoft Defender AV est installé :

   ```sc.exe query Windefend```

    Si le résultat est « Le service spécifié n’existe pas en tant que service installé » , vous devez installer Microsoft Defender AV. Pour plus d’informations, [voir Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-windows.md).

    Pour plus d’informations sur l’utilisation de la stratégie de groupe pour configurer et gérer des Antivirus Microsoft Defender sur vos serveurs Windows, voir Utiliser les [paramètres](use-group-policy-microsoft-defender-antivirus.md)de stratégie de groupe pour configurer et gérer Antivirus Microsoft Defender .


2. Exécutez la commande suivante pour vérifier que Microsoft Defender pour le point de terminaison est en cours d’exécution :

    ```sc.exe query sense```
    
    Le résultat doit montrer qu’il est en cours d’exécution. Si vous rencontrez des problèmes avec l’intégration, voir [Résoudre les problèmes d’intégration.](troubleshoot-onboarding.md)

## <a name="run-a-detection-test"></a>Exécuter un test de détection
Suivez les étapes de [l’étape Exécuter](run-detection-test.md) un test de détection sur un appareil nouvellement intégré pour vérifier que le serveur fait des rapports à Defender pour le service Endpoint.





## <a name="onboarding-endpoints-with-no-management-solution"></a>Intégration de points de terminaison sans solution de gestion 

### <a name="using-group-policy"></a>Utilisation de la stratégie de groupe

**Étape 1 : Téléchargez l’udpate correspondante pour votre point de terminaison.**

1. Accédez à c:\windows\sysvol\domain\scripts (le contrôle de modification peut être nécessaire sur l’un des contrôleurs de domaine.)
1. Créez un dossier nommé MMA.
1. Téléchargez les fichiers suivants et placez-les dans le dossier MMA :
   
    - Mise à jour pour la télémétrie d’expérience client et de diagnostic :
      - [Pour Windows Server 2008 R2 x64](https://www.microsoft.com/download/details.aspx?familyid=1bd1d18d-4631-4d8e-a897-327925765f71)
     
    Pour Windows Server 2008 R2 SP1, les mises à jour suivantes sont également requises :

    Déploiement mensuel de février 2018 - KB4074598 (Windows Server 2008 R2)

    [Catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)<br>
    Télécharger les mises à jour Windows Server 2008 R2 x64
    
    .NET Framework 3.5.1 (KB315418)<br>
    [Pour Windows Server 2008 R2 x64](https://download.microsoft.com/download/6/8/0/680ee424-358c-4fdf-a0de-b45dee07b711/windows6.1-kb3154518-x64.msu)
    
    >[!NOTE]
    > Cet article suppose que vous utilisez des serveurs x64 (agent MMA .exe version x64 nouvelle compatible SHA-2).


**Étape 2 : Créer un nom de fichier DeployMMA.cmd (à l’aide du bloc-notes)** Ajoutez les lignes suivantes au fichier cmd. Notez que vous aurez besoin de votre ID d’espace de travail et de votre CLÉ.

La commande suivante est un exemple. Remplacez les valeurs suivantes :
- KB : utiliser la ko applicable en rapport avec le point de terminaison que vous intégrerez
- ID d’espace de travail et CLÉ : utiliser votre ID et votre clé


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





### <a name="group-policy-configuration"></a>Configuration de la stratégie de groupe

Créez une stratégie de groupe spécifique pour l’intégration d’appareils tels que « Microsoft Defender pour l’intégration de point de terminaison ».

- Créer un dossier de stratégie de groupe nommé « c:\windows\MMA »

     :::image type="content" source="images/grppolicyconfig1.png" alt-text="dossiers":::

    **Cela ajoute un nouveau dossier sur chaque serveur qui obtient l’GPO appliqué, appelé MMA, et qui sera stocké dans c:\windows. Il contient les fichiers d’installation pour le MMA, les éléments prérequis et le script d’installation.**

- Créez une préférence de fichiers de stratégie de groupe pour chacun des fichiers stockés dans l’ouverture de boutique Net.

     :::image type="content" source="images/grppolicyconfig2.png" alt-text="image1 de stratégie de groupe":::

Il copie les fichiers de DOMAIN\NETLOGON\MMA\filename vers C:\windows\MMA\filename, afin que les fichiers **d’installation** soient locaux sur le serveur :

:::image type="content" source="images/deploymma.png" alt-text="déployer mma cmd":::

Répétez le processus, mais créez un ciblage au niveau de l’élément sous l’onglet COMMON, afin que le fichier ne soit copié que dans la version de plateforme/système d’exploitation appropriée dans l’étendue :

:::image type="content" source="images/targeteditor.png" alt-text="éditeur cible":::

Pour Windows Server 2008 R2, vous aurez besoin (et uniquement de copier vers le bas) les ressources suivantes :
- Windows6.1-KB3080149-x64.msu
- Windows6.1-KB3154518-x64.msu
- Windows6.1-KB4075598-x64.msu


Une fois cette stratégie effectuée, vous devez créer une stratégie de script de démarrage :

:::image type="content" source="images/startupprops.png" alt-text="démarrer les propriétés":::

Le nom du fichier à exécuter ici est c:\windows\MMA\DeployMMA.cmd.
Une fois que le serveur est redémarré dans le cadre du processus de démarrage, il installe la mise à jour de la base de données de télémétrie de diagnostic et d’expérience client, puis installe l’agent MMA, lors de la définition de l’ID et de la clé de l’espace de travail, et le serveur est intégré.

Vous pouvez également utiliser une **tâche immédiate** pour exécuter le deployMMA.cmd si vous ne souhaitez pas redémarrer tous les serveurs.

Cette étape peut être effectuée en deux phases. Tout **d’abord,** créez les fichiers et le dossier dans l’GPO : donnez au système le temps de s’assurer que l’GPO a été appliqué et que tous les serveurs disposent des fichiers d’installation. Ensuite, ajoutez la tâche immédiate. Cela permettra d’obtenir le même résultat sans nécessiter de redémarrage.

Étant donné que le script dispose d’une méthode de sortie et ne sera pas ré-exécuté si le MMA est installé, vous pouvez également utiliser une tâche programmée quotidienne pour obtenir le même résultat. Similaire à une stratégie de conformité Configuration Manager qu’elle vérifie quotidiennement pour s’assurer que le MMA est présent.

:::image type="content" source="images/schtask.png" alt-text="planifier une tâche":::

:::image type="content" source="images/newtaskprops.png" alt-text="nouvelles propriétés de tâche":::

:::image type="content" source="images/deploymmadowmload.png" alt-text="déployer les props de téléchargement mma":::

:::image type="content" source="images/tasksch.png" alt-text="programmeur de tâches":::

Comme mentionné dans la documentation d’intégration pour Server spécifiquement autour de Server 2008 R2, voir ci-dessous : Pour Windows Server 2008 R2 SP1, assurez-vous que vous remplissez les conditions suivantes :

- Installer le rapport de mise à jour mensuelle de [février 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
- Installer [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (ou ultérieur) ou [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

Vérifiez que les ko sont présents avant l’intégration Windows Server 2008 R2. Ce processus vous permet d’intégrer tous les serveurs si configuration Manager ne gère pas les serveurs.


## <a name="offboard-endpoints"></a>Points de terminaison de hors-carte

Deux options s’offrent à vous pour Windows points de terminaison du service :

- Désinstaller l’agent MMA
- Supprimer la configuration de l’espace de travail Defender pour le point de terminaison

> [!NOTE]
> La non-boardation entraîne l’arrêt du point de terminaison Windows pour arrêter l’envoi de données de capteur au portail, mais les données du point de terminaison, y compris la référence aux alertes qu’il Windows eues, seront conservées pendant 6 mois.

### <a name="uninstall-the-mma-agent"></a>Désinstaller l’agent MMA

Pour désinsérez le point de terminaison Windows, vous pouvez désinstaller l’agent MMA ou le détacher de la notification à votre espace de travail Defender for Endpoint. Après l’arrêt de l’agent, le point de terminaison n’envoie plus de données de capteur à Defender for Endpoint.
Pour plus d’informations, [voir Pour désactiver un agent.](/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent)

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>Supprimer la configuration de l’espace de travail Defender pour le point de terminaison

Vous pouvez utiliser l’une des méthodes suivantes :

- Supprimer la configuration de l’espace de travail Defender pour le point de terminaison de l’agent MMA
- Exécuter une commande PowerShell pour supprimer la configuration

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>Supprimer la configuration de l’espace de travail Defender pour le point de terminaison de l’agent MMA

1. Dans la **Microsoft Monitoring Agent propriétés,** sélectionnez **l’onglet Azure Log Analytics (OMS).**

2. Sélectionnez l’espace de travail Defender pour le point de terminaison, puis cliquez sur **Supprimer.**

    ![Image des propriétés Microsoft Monitoring Agent de l’entreprise](images/atp-mma.png)

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>Exécuter une commande PowerShell pour supprimer la configuration

1. Obtenez votre ID d’espace de travail :

   1. Dans le volet de navigation, sélectionnez  >  **Paramètres’intégration.**

   1. Sélectionnez le système d’exploitation approprié et obtenez votre ID d’espace de travail.

    
2. Ouvrez un PowerShell élevé et exécutez la commande suivante. Utilisez l’ID d’espace de travail que vous avez obtenu et remplacez `WorkspaceID` :

    ```   
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```
