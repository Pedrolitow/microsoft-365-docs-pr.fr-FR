---
title: Configurer les paramètres de proxy d’appareil et de connexion Internet
description: Configurez les paramètres proxy et Internet de Microsoft Defender pour les points de terminaison afin d’activer la communication avec le service cloud.
keywords: configurer, proxy, Internet, connectivité Internet, paramètres, paramètres proxy, netsh, winhttp, serveur proxy
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7e3077980755f81a3ca86569b53051a2851191de
ms.sourcegitcommit: b3c4816b55657b87ed4a5f6a4abe3d505392218e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2021
ms.locfileid: "53757053"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy du dispositif et de connectivité Internet

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Le capteur Defender pour point de terminaison nécessite que Microsoft Windows HTTP (WinHTTP) signale les données du capteur et communique avec le service Defender for Endpoint.

Le capteur Defender for Endpoint incorporé s’exécute dans le contexte système à l’aide du compte LocalSystem. Le capteur utilise Microsoft Windows HTTP Services (WinHTTP) pour permettre la communication avec le service cloud Defender for Endpoint.

> [!TIP]
> Pour les organisations qui utilisent des proxies de transfert comme passerelle vers l'Internet, vous pouvez utiliser la protection du réseau pour enquêter derrière un proxy. Pour plus d'informations, voir [Enquêter sur les événements de connexion qui se produisent derrière les procurations](investigate-behind-proxy.md).

Le paramètre de configuration WinHTTP est indépendant des paramètres de proxy de navigation Internet Windows Internet (WinINet) et ne peut découvrir un serveur proxy qu’à l’aide des méthodes de découverte suivantes :

- Méthodes de découverte automatique :
  - Proxy transparent
  - Protocole WPAD (Web Proxy Auto-Discovery Protocol)

    > [!NOTE]
    > Si vous utilisez un proxy transparent ou WPAD dans votre topologie réseau, vous n’avez pas besoin de paramètres de configuration spéciaux. Pour plus d’informations sur les exclusions d’URL defender pour point de terminaison dans le proxy, voir Activer l’accès à Defender pour les URL de service de point de terminaison dans [le serveur proxy.](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- Configuration manuelle du proxy statique :

  - Configuration basée sur le registre
  - WinHTTP configuré à l’aide de la commande netsh : convient uniquement aux ordinateurs de bureau dans une topologie stable (par exemple : un bureau dans un réseau d’entreprise derrière le même proxy)

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Configurer le serveur proxy manuellement en utilisant un proxy statique basé sur le registre

Configurez un proxy statique basé sur le Registre pour autoriser uniquement le capteur Defender for Endpoint à signaler les données de diagnostic et à communiquer avec Defender pour les services Endpoint si un ordinateur n’est pas autorisé à se connecter à Internet.

> [!NOTE]
> Lorsque vous utilisez cette option sur Windows 10 ou Windows Server 2019, il est recommandé d’avoir la version suivante (ou ultérieure) et le cumul des mises à jour cumulatives :
>
> - Windows 10, version 1809 ou Windows Server 2019 -<https://support.microsoft.com/kb/5001384>
> - Windows 10, version 1909 -<https://support.microsoft.com/kb/4601380>
> - Windows 10, version 2004 -<https://support.microsoft.com/kb/4601382>
> - Windows 10, version 20H2 -<https://support.microsoft.com/kb/4601382>
>
> Ces mises à jour améliorent la connectivité et la fiabilité du canal CnC (Commande et contrôle).

Le proxy statique est configurable via une stratégie de groupe. La stratégie de groupe se trouve sous :

- **Modèles d’administration > Windows composants > collecte de données et builds d’aperçu > configurer l’utilisation du proxy authentifié pour le service Expériences des utilisateurs connectés et télémétrie**

  Définissez-le **sur Activé et** sélectionnez Désactiver l’utilisation du proxy **authentifié.**

  ![Image du paramètre de stratégie de groupe1](images/atp-gpo-proxy1.png)

- **Modèles d’administration > Windows composants >** collecte de données et builds d’aperçu > configurer les expériences des utilisateurs connectés et la télémétrie :

  Configurer le proxy

  ![Image du paramètre de stratégie de groupe2](images/atp-gpo-proxy2.png)

  La stratégie définit deux valeurs de Registre, comme REG_SZ et comme REG_DWORD, sous `TelemetryProxyServer` la clé de Registre `DisableEnterpriseAuthProxy` `HKLM\Software\Policies\Microsoft\Windows\DataCollection` .

  La valeur de Registre `TelemetryProxyServer` prend le format de chaîne suivant :

  ```text
  <server name or ip>:<port>
  ```

  Par exemple, 10.0.0.6:8080

  Cette valeur de registre `DisableEnterpriseAuthProxy` doit être égale à 1.

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Configurer le serveur proxy manuellement à l’aide de la commande netsh

Utiliser netsh pour configurer un proxy statique à l’échelle du système.

> [!NOTE]
>
> - Cela affectera toutes les applications, y compris les services Windows qui utilisent WinHTTP avec un proxy par défaut.</br>
> - Les ordinateurs portables qui changent de topologie (par exemple, de bureau à domicile) ne fonctionneront pas correctement avec netsh. Utiliser la configuration statique du proxy basée sur le registre.

1. Ouvrir une ligne de commandes avec élévation de privilèges :
   1. Accéder à **Démarrer** et taper **cmd**.
   1. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante et appuyez sur **Entrée** :

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Par exemple : `netsh winhttp set proxy 10.0.0.6:8080`

Pour réinitialiser le proxy winhttp, entrez la commande suivante et appuyez sur **Entrée** :

```PowerShell
netsh winhttp reset proxy
```

Pour plus d’informations, voir [la syntaxe, les contextes et le formatage de la commande Netsh](/windows-server/networking/technologies/netsh/netsh-contexts).

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>Activer l’accès aux URL du service Microsoft Defender pour les points de terminaison dans le serveur proxy

Si un proxy ou un pare-feu bloque tout le trafic par défaut et n'autorise le passage que de domaines spécifiques, ajoutez les domaines énumérés dans la feuille téléchargeable à la liste des domaines autorisés.

La feuille de calcul téléchargeable suivante répertorie les services et les URL associées à qui votre réseau doit pouvoir se connecter. Vous devez vous assurer qu’il n’existe aucune règle de pare-feu ou de  filtrage réseau qui refuserait l’accès à ces URL, ou que vous devrez peut-être créer une règle d’autoriser spécifiquement pour eux.

<br>

**** 
|Liste de feuilles de calcul de domaines|Description|
|---|---|
|![Image miniature de la feuille de calcul DES URL de Microsoft Defender pour les points de terminaison](images/mdatp-urls.png)|Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)|
|

Si l’analyse HTTPS (inspection SSL) est activée pour un proxy ou un pare-feu, excluez les domaines répertoriés dans le tableau ci-dessus de l’analyse HTTPS.
Dans votre pare-feu, ouvrez toutes les URL où la colonne de géographie est WW. Pour les lignes où la colonne de géographie n’est pas WW, ouvrez les URL vers votre emplacement de données spécifique. Pour vérifier votre paramètre d’emplacement de données, voir Vérifier l’emplacement de stockage des données et mettre à jour les paramètres de rétention des données [pour Microsoft Defender pour le point de terminaison.](/microsoft-365/security/defender-endpoint/data-retention-settings)

> [!NOTE]
> settings-win.data.microsoft.com est nécessaire uniquement si vous avez des Windows 10 exécutant la version 1803 ou une version antérieure.<br>
>
> Les URL qui incluent la version 20 sont nécessaires uniquement si vous avez des Windows 10 exécutant la version 1803 ou ultérieure. Par exemple, est nécessaire pour un appareil Windows 10 exécutant la version 1803 ou ultérieure et intégré à la région Stockage `us-v20.events.data.microsoft.com` données américaines.
>
> Si vous utilisez Antivirus Microsoft Defender dans votre environnement, voir Configurer les connexions réseau [au service cloud Antivirus Microsoft Defender.](/windows/security/threat-protection/microsoft-defender-antivirus/configure-network-connections-microsoft-defender-antivirus)

Si un proxy ou un pare-feu bloque le trafic anonyme, comme le capteur Defender for Endpoint se connecte à partir du contexte système, assurez-vous que le trafic anonyme est autorisé dans les URL répertoriées précédemment.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (MMA) : exigences relatives au proxy et au pare-feu pour les versions antérieures Windows client ou Windows Server

Les informations ci-dessous répentent les informations de configuration du proxy et du pare-feu requises pour communiquer avec l’agent d’analyse des journaux (souvent appelé Microsoft Monitoring Agent) pour les versions précédentes de Windows telles que Windows 7 SP1, Windows 8.1, Windows Server 2008 R2, Windows Server 2012 R2 et Windows Server 2016.

<br>

****

|Ressource d'agent|Ports|Direction|Contournement de l’inspection HTTPS|
|---|---|---|---|
|*.ods.opinsights.azure.com|Port 443|Sortant|Oui|
|*.oms.opinsights.azure.com|Port 443|Sortant|Oui|
|*.blob.core.windows.net|Port 443|Sortant|Oui|
|*.azure-automation.net|Port 443|Sortant|Oui|

> [!NOTE]
> En tant que solution informatique, la plage d’adresses IP peut changer. Il est recommandé de passer au paramètre de résolution DNS.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>Confirmer la Microsoft Monitoring Agent’URL du service (MMA) 

Consultez les instructions suivantes pour éliminer les caractères génériques (*) requis pour votre environnement spécifique lors de l’utilisation de la Microsoft Monitoring Agent (MMA) pour les versions précédentes de Windows.

1. Intégrer un système d’exploitation précédent avec le Microsoft Monitoring Agent (MMA) dans Defender pour endpoint (pour plus d’informations, voir Intégrer les versions précédentes de Windows sur les serveurs [Defender pour endpoint](https://go.microsoft.com/fwlink/p/?linkid=2010326) et [Onboard Windows).](configure-server-endpoints.md#windows-server-2008-r2-sp1-windows-server-2012-r2-and-windows-server-2016)

2. Assurez-vous que l’ordinateur a correctement des rapports dans le Microsoft 365 Defender web.

3. Exécutez l’outil TestCloudConnection.exe à partir de « C:\Program Files\Microsoft Monitoring Agent\Agent » pour valider la connectivité et voir les URL requises pour votre espace de travail spécifique.

4. Consultez la liste des URL de point de terminaison Microsoft Defender pour obtenir la liste complète des conditions requises pour votre région (reportez-vous à la feuille de calcul URL [de](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)service).

    ![Image de l’administrateur dans Windows PowerShell](images/admin-powershell.png)

Les caractères génériques ( ) utilisés dans les points de terminaison \* \* d’URL .ods.opinsights.azure.com, .oms.opinsights.azure.com et .agentsvc.azure-automation.net peuvent être remplacés par votre ID d’espace de travail \* \* spécifique. L’ID d’espace de travail est spécifique à votre environnement et à votre espace de travail et se trouve dans la section Intégration de votre client dans le portail Microsoft 365 Defender.

Le point de terminaison de l’URL .blob.core.windows.net peut être remplacé par les URL affichées dans la section « Règle de pare-feu : .blob.core.windows.net » des résultats \* \* du test.

> [!NOTE]
> Dans le cas de l’intégration via Azure Defender, plusieurs espaces de travail peuvent être utilisés. Vous devrez effectuer la procédure TestCloudConnection.exe ci-dessus sur un ordinateur intégré à partir de chaque espace de travail (pour déterminer s’il existe des modifications apportées aux URL *.blob.core.windows.net entre les espaces de travail).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>Vérifier la connectivité du client aux URL du service Microsoft Defender pour les points de terminaison

Vérifier que la configuration du proxy a été effectuée avec succès, que WinHTTP peut découvrir et communiquer par le biais du serveur proxy dans votre environnement, et que le serveur proxy permet le trafic vers les URL du service Defender for Endpoint.

1. Téléchargez [l’outil Analyseur de client Microsoft Defender](https://aka.ms/mdeanalyzer) pour point de terminaison sur le PC sur lequel le capteur Defender for Endpoint est en cours d’exécution.

2. Extrayez le contenu des MDEClientAnalyzer.zip sur l’appareil.

3. Ouvrir une ligne de commandes avec élévation de privilèges :
   1. Accéder à **Démarrer** et taper **cmd**.
   1. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

4. Entrez la commande suivante et appuyez sur **Entrée** :

    ```PowerShell
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    Remplacez *HardDrivePath* par le chemin d’accès où l’outil MDEClientAnalyzer a été téléchargé, par exemple :

    ```PowerShell
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. *ExtrayezMDEClientAnalyzerResult.zip* fichier créé par l’outil dans le dossier utilisé dans *HardDrivePath*.

6. Ouvrez *MDEClientAnalyzerResult.txt* et vérifiez que vous avez effectué les étapes de configuration du proxy pour activer la découverte de serveur et l’accès aux URL du service.

   L'outil vérifie la connectivité des URL du service Defender for Endpoint avec lesquelles le client Defender for Endpoint est configuré pour interagir. Il imprime ensuite les résultats dans le *fichierMDEClientAnalyzerResult.txt* pour chaque URL pouvant potentiellement être utilisée pour communiquer avec les services Defender for Endpoint. Par exemple :

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

Si au moins une des options de connectivité renvoie un état (200), le client Defender pour le point de terminaison peut communiquer avec l’URL testée correctement à l’aide de cette méthode de connectivité.

Toutefois, si les résultats du contrôle de la connectivité indiquent un échec, une erreur HTTP est affichée (voir Codes d'état HTTP). Vous pouvez ensuite utiliser les URL dans le tableau indiqué dans Activer l’accès aux URL de [service Defender for Endpoint dans le serveur proxy.](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) Les URL que vous utiliserez dépendent de la région sélectionnée au cours de la procédure d’intégration.

> [!NOTE]
> Les vérifications de connectivité cloud de l’outil Analyseur de connectivité ne sont pas compatibles avec les créations de processus de blocage des règles de réduction de la surface d’attaque provenant des commandes [PSExec et WMI.](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules.md#block-process-creations-originating-from-psexec-and-wmi-commands) Vous devrez désactiver temporairement cette règle pour exécuter l'outil de connectivité. Vous pouvez également ajouter temporairement des [exclusions DE LAS](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction.md#exclude-files-and-folders) lors de l’exécution de l’analyseur.
>
> Lorsque telemetryProxyServer est défini, dans le Registre ou via la stratégie de groupe, Defender pour le point de terminaison revient à direct s’il ne peut pas accéder au proxy défini.

## <a name="related-topics"></a>Sujets connexes

- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
