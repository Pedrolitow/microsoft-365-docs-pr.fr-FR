---
title: Configurer les paramètres de proxy d’appareil et de connexion Internet
description: Configurez les paramètres proxy et Internet de Microsoft Defender pour les points de terminaison pour permettre la communication avec le service cloud.
keywords: configurer, proxy, Internet, connectivité Internet, paramètres, paramètres proxy, netsh, winhttp, serveur proxy
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: b4ae8490fadecf60d4414218f42cac83b9035270
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62354983"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy du dispositif et de connectivité Internet

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Le capteur Defender pour point de terminaison nécessite que Microsoft Windows HTTP (WinHTTP) signale les données du capteur et communique avec le service Defender for Endpoint. Le capteur Defender for Endpoint incorporé s’exécute dans le contexte système à l’aide du compte LocalSystem. Le capteur utilise Microsoft Windows HTTP Services (WinHTTP) pour permettre la communication avec le service cloud Defender for Endpoint.

> [!TIP]
> Pour les organisations qui utilisent des proxies avant comme passerelle vers Internet, vous pouvez utiliser la protection du réseau pour examiner les événements de connexion qui se produisent derrière des [proxies avant](investigate-behind-proxy.md).

Le paramètre de configuration WinHTTP est indépendant des paramètres de proxy de navigation Windows Internet (WinINet) (voir [WinINet ou WinHTTP](/windows/win32/wininet/wininet-vs-winhttp)). Il peut uniquement découvrir un serveur proxy à l’aide des méthodes de découverte suivantes :

- Méthodes de découverte automatique :

  - Proxy transparent
  
  - Protocole WPAD (Web Proxy Auto-Discovery Protocol)

    > [!NOTE]
    > Si vous utilisez un proxy transparent ou WPAD dans votre topologie réseau, vous n’avez pas besoin de paramètres de configuration spéciaux. Pour plus d’informations sur les exclusions d’URL defender pour point de terminaison dans le proxy, voir Activer l’accès à Defender pour les [URL de service de point de terminaison dans le serveur proxy](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- Configuration manuelle du proxy statique :

  - Configuration basée sur le registre
  
  - WinHTTP configuré à l’aide de la commande netsh : convient uniquement aux ordinateurs de bureau dans une topologie stable (par exemple : un bureau dans un réseau d’entreprise derrière le même proxy)

> [!NOTE]
> L’antivirus defender et PEPT proxies peuvent être définies indépendamment.  Dans les sections qui suivent, n’ignorez pas ces distinctions.

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Configurer le serveur proxy manuellement en utilisant un proxy statique basé sur le registre

Configurez un proxy statique basé sur le Registre pour le capteur defender de détection et de réponse de point de terminaison (PEPT) pour signaler les données de diagnostic et communiquer avec Defender pour les services de point de terminaison si un ordinateur n’est pas autorisé à se connecter à Internet.

> [!NOTE]
> Lorsque vous utilisez cette option sur Windows 10, Windows 11, Windows Server 2019 ou Windows Server 2022, il est recommandé d’avoir les mises à jour cumulatives et de build suivantes (ou ultérieures) :
>
> - Windows 11
> - Windows 10, version 1809 ou Windows Server 2019 ou Windows Server 2022 -<https://support.microsoft.com/kb/5001384>
> - Windows 10, version 1909 -<https://support.microsoft.com/kb/4601380>
> - Windows 10, version 2004 -<https://support.microsoft.com/kb/4601382>
> - Windows 10, version 20H2 -<https://support.microsoft.com/kb/4601382>
>
> Ces mises à jour améliorent la connectivité et la fiabilité du canal CnC (Commande et contrôle).

Le proxy statique est configurable par le biais de la stratégie de groupe ( GP), les deux paramètres sous les valeurs de stratégie de groupe doivent être configurés sur le serveur proxy pour l’utilisation PEPT. La stratégie de groupe est disponible dans les modèles d’administration.

- **Les modèles d’administration > Windows composants >** collecte de données et les builds d’aperçu > l’utilisation du proxy authentifié pour le service Expériences des utilisateurs connectés et télémétrie.

  Définissez-le **sur Activé et** sélectionnez **Désactiver l’utilisation du proxy authentifié**.

  ![Image du paramètre de stratégie de groupe 1.](images/atp-gpo-proxy1.png)

- **Modèles d’administration > Windows composants >** collecte de données et builds d’aperçu > configurer les expériences des utilisateurs connectés et la télémétrie :

  Configurez le proxy.

  ![Image du paramètre de stratégie de groupe2.](images/atp-gpo-proxy2.png)


| Stratégie de groupe | Clé du Registre | Entrée de Registre | Valeur |
|:---|:---|:---|:---|
| Configurer l’utilisation du proxy authentifié pour l’expérience utilisateur connectée et le service de télémétrie | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `DisableEnterpriseAuthProxy` | 1 (REG_DWORD) |
| Configurer les expériences des utilisateurs connectés et la télémétrie | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `TelemetryProxyServer` | ```servername:port or ip:port``` <br> <br> Par exemple : ```10.0.0.6:8080``` (REG_SZ) |

## <a name="configure-a-static-proxy-for-microsoft-defender-antivirus"></a>Configurer un proxy statique pour Antivirus Microsoft Defender

Antivirus Microsoft Defender [protection cloud fournit une protection](cloud-protection-microsoft-defender-antivirus.md) automatisée et quasi instantanée contre les menaces nouvelles et émergentes. Notez que la connectivité est requise pour les [indicateurs personnalisés lorsque](manage-indicators.md) l’Antivirus Defender est votre solution anti-programme malveillant active. Par [PEPT en mode blocage](edr-in-block-mode.md) dispose d’une solution anti-programme malveillant principale lors de l’utilisation d’une solution non Microsoft.

Configurez le proxy statique à l’aide de la stratégie de groupe disponible dans les modèles d’administration :

1. **Modèles d'> Windows composants > Antivirus Microsoft Defender > définir un serveur proxy pour la connexion au réseau**. 

2. Définissez-le **sur Activé et** définissez le serveur proxy. Notez que l’URL doit être http:// ou https://. Pour les versions de https://, voir [Gérer Antivirus Microsoft Defender mises à jour](manage-updates-baselines-microsoft-defender-antivirus.md).

   :::image type="content" source="images/proxy-server-mdav.png" alt-text="Serveur proxy pour Antivirus Microsoft Defender.":::

3. Sous la clé de Registre `HKLM\Software\Policies\Microsoft\Windows Defender`, la stratégie définit la valeur de Registre `ProxyServer` comme REG_SZ. 

   La valeur de Registre prend `ProxyServer` le format de chaîne suivant :

    ```text
    <server name or ip>:<port>

    For example: http://10.0.0.6:8080
    ```

> [!NOTE]
>
> À des fins de résilience et de nature en temps réel de la protection cloud, Antivirus Microsoft Defender mettre en cache le dernier proxy de travail connu. Assurez-vous que votre solution proxy n’effectue pas d’inspection SSL. Cela va rompre la connexion cloud sécurisée. 
>
> Antivirus Microsoft Defender n’utilisera pas le proxy statique pour se connecter à Windows update ou Microsoft Update pour télécharger les mises à jour. Au lieu de cela, il utilise un proxy à l’échelle du système s’il est configuré pour utiliser Windows Update ou la source de mise à jour interne configurée en fonction de l’ordre de remplacement [configuré](manage-protection-updates-microsoft-defender-antivirus.md). 
>
> Si nécessaire, vous pouvez utiliser des **modèles d’administration > Windows composants > Antivirus Microsoft Defender > définir la config automatique du proxy (.pac)** pour la connexion au réseau. Si vous devez configurer des configurations avancées avec plusieurs proxys, utilisez modèles d’administration **> Windows Composants > Antivirus Microsoft Defender >** Définissez des adresses pour contourner le serveur proxy et empêcher les Antivirus Microsoft Defender d’utiliser un serveur proxy pour ces destinations. 
>
> Vous pouvez utiliser PowerShell avec l’cmdlet `Set-MpPreference` pour configurer ces options : 
>
> - ProxyBypass 
> - ProxyPacUrl 
> - ProxyServer 

> [!NOTE]
> Pour utiliser correctement le proxy, configurez ces trois paramètres de proxy différents :
>  - Microsoft Defender pour point de terminaison (MDE)
>  - ANTIVIRUS (Antivirus)
>  - Endpoint Detection and Response (PEPT)

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Configurer le serveur proxy manuellement à l’aide de la commande netsh

Utiliser netsh pour configurer un proxy statique à l’échelle du système.

> [!NOTE]
>
> - Cela affectera toutes les applications, y compris les services Windows qui utilisent WinHTTP avec un proxy par défaut.</br>
> - Les ordinateurs portables qui changent de topologie (par exemple, de bureau à domicile) ne fonctionneront pas correctement avec la commande netsh. Utiliser la configuration statique du proxy basée sur le registre.

1. Ouvrez une invite de commandes avec élévation de privilèges :
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

Par défaut, si un proxy ou un pare-feu bloque tout le trafic par défaut et n’autorise que des domaines spécifiques, ajoutez les domaines répertoriés dans la feuille téléchargeable à la liste des domaines autorisés.

La feuille de calcul téléchargeable suivante répertorie les services et les URL associées que votre réseau doit pouvoir connecter. Assurez-vous qu’il n’existe aucune règle de pare-feu ou de filtrage réseau pour refuser l’accès à ces URL. Facultatif, vous devrez peut-être créer une *règle* d’autoriser spécifiquement pour eux.

<br>

**** 
|Liste de feuilles de calcul de domaines| Description|
|---|---|
|Liste d’URL Microsoft Defender pour les points de terminaison pour les clients commerciaux| Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation pour les clients commerciaux. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Liste d’URL Microsoft Defender pour les points de terminaison pour les clients Gov/Cloud de la communauté du secteur public/DoD | Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation pour les clients Gov/Cloud de la communauté du secteur public/DoD. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Si l’analyse HTTPS (inspection SSL) est activée pour un proxy ou un pare-feu, excluez les domaines répertoriés dans le tableau ci-dessus de l’analyse HTTPS.
Dans votre pare-feu, ouvrez toutes les URL où la colonne de géographie est WW. Pour les lignes où la colonne de géographie n’est pas WW, ouvrez les URL vers votre emplacement de données spécifique. Pour vérifier votre paramètre d’emplacement des données, voir Vérifier l’emplacement de stockage des données et mettre à jour les paramètres de rétention des données [pour Microsoft Defender pour endpoint](/microsoft-365/security/defender-endpoint/data-retention-settings).

> [!NOTE]
> Windows appareils exécutant la version 1803 ou antérieure.`settings-win.data.microsoft.com`  <br>
>
> Les URL qui incluent la version 20 sont nécessaires uniquement si vous avez des Windows exécutant la version 1803 ou ultérieure. Par exemple, est `us-v20.events.data.microsoft.com` nécessaire pour un appareil Windows exécutant la version 1803 ou ultérieure et intégré à la région Stockage données américaines.
>

Si un proxy ou un pare-feu bloque le trafic anonyme en tant que capteur Defender pour point de terminaison et qu’il se connecte à partir du contexte système pour s’assurer que le trafic anonyme est autorisé dans les URL répertoriées précédemment.

> [!NOTE]
> Microsoft ne fournit pas de serveur proxy. Ces URL sont accessibles via le serveur proxy que vous configurez.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (MMA) : exigences relatives au proxy et au pare-feu pour les versions antérieures Windows client ou Windows Server

Les informations de la liste des informations de configuration du proxy et du pare-feu sont requises pour communiquer avec l’agent d’analyse des journaux (souvent appelé Microsoft Monitoring Agent) pour les versions précédentes de Windows, telles que Windows 7 SP1, Windows 8.1 et Windows Server 2008 R2*.

<br>

****

|Ressource d'agent|Ports|Direction|Contournement de l’inspection HTTPS|
|---|---|---|---|
|*.ods.opinsights.azure.com|Port 443|Sortant|Oui|
|*.oms.opinsights.azure.com|Port 443|Sortant|Oui|
|*.blob.core.windows.net|Port 443|Sortant|Oui|
|*.azure-automation.net|Port 443|Sortant|Oui|

> [!NOTE]
> *Ces exigences de connectivité s’appliquent au précédent point de terminaison Microsoft Defender pour Windows Server 2016 et Windows Server 2012 R2 qui nécessite MMA. Les instructions d’intégration de ces systèmes d’exploitation avec la nouvelle solution unifiée se font sur les serveurs [Windows](configure-server-endpoints.md) intégrés ou migrent vers la nouvelle solution unifiée dans les scénarios de migration de serveur dans [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> En tant que solution informatique, la plage d’adresses IP peut changer. Il est recommandé de passer au paramètre de résolution DNS.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>Confirmer la Microsoft Monitoring Agent’URL du service (MMA) 

 Consultez les instructions suivantes pour éliminer les caractères génériques (*) requis pour votre environnement spécifique lors de l’utilisation de la Microsoft Monitoring Agent (MMA) pour les versions précédentes de Windows.

1. Intégrer un système d’exploitation précédent avec l’Microsoft Monitoring Agent (MMA) dans Defender pour endpoint (pour plus d’informations, voir Intégrer les versions précédentes de [Windows sur les serveurs Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2010326) et [Onboard Windows](configure-server-endpoints.md)).

2. Assurez-vous que l’ordinateur est correctement signalé dans Microsoft 365 Defender portail.

3. Exécutez l’outil TestCloudConnection.exe à partir de « C:\Program Files\Microsoft Monitoring Agent\Agent » pour valider la connectivité et obtenir les URL requises pour votre espace de travail spécifique.

4. Consultez la liste des URL des points de terminaison De Microsoft Defender pour obtenir la liste complète des conditions [requises pour](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) votre région (reportez-vous à la feuille de calcul URL de service).

    ![Image de l’administrateur dans Windows PowerShell.](images/admin-powershell.png)

Les caractères génériques (\*) \*utilisés dans les points de terminaison d’URL .ods.opinsights.azure.com, \*\*.oms.opinsights.azure.com et .agentsvc.azure-automation.net peuvent être remplacés par votre ID d’espace de travail spécifique. L’ID d’espace de travail est spécifique à votre environnement et à votre espace de travail. Elle se trouve dans la section Intégration de votre client dans le portail Microsoft 365 Defender client.

Le \*point de terminaison de l’URL .blob.core.windows.net peut être remplacé par les URL affichées dans la section « Règle \*de pare-feu : .blob.core.windows.net » des résultats du test.

> [!NOTE]
> Dans le cas de l’intégration via Microsoft Defender pour le cloud, plusieurs espaces de travail peuvent être utilisés. Vous devrez effectuer la procédure TestCloudConnection.exe sur l’ordinateur intégré à partir de chaque espace de travail (pour déterminer s’il existe des modifications aux URL *.blob.core.windows.net entre les espaces de travail).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>Vérifier la connectivité du client aux URL du service Microsoft Defender pour les points de terminaison

Vérifiez que la configuration du proxy s’est correctement terminée. WinHTTP peut ensuite découvrir et communiquer via le serveur proxy dans votre environnement, puis le serveur proxy autorise le trafic vers les URL du service Defender for Endpoint.

1. Téléchargez [l’outil Analyseur de client Microsoft Defender pour point](https://aka.ms/mdeanalyzer) de terminaison sur le PC, sur lequel le capteur Defender for Endpoint est en cours d’exécution.

2. Extrayez le contenu des MDEClientAnalyzer.zip sur l’appareil.

3. Ouvrez une invite de commandes avec élévation de privilèges :
   1. Accéder à **Démarrer** et taper **cmd**.
   1. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

4. Entrez la commande suivante et appuyez sur **Entrée** :

    ```PowerShell
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    *Remplacez HardDrivePath* par le chemin d’accès, où l’outil MDEClientAnalyzer a été téléchargé. Par exemple :

    ```PowerShell
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. L’outil crée et extrait le *MDEClientAnalyzerResult.zip* dans le dossier à utiliser dans *HardDrivePath*.

6. *OuvrezMDEClientAnalyzerResult.txt* et vérifiez que vous avez effectué les étapes de configuration du proxy pour activer la découverte de serveur et l’accès aux URL de service.

   L’outil vérifie la connectivité des URL du service Defender for Endpoint. Assurez-vous que le client Defender pour point de terminaison est configuré pour interagir. L’outil imprime les résultats dans le *fichierMDEClientAnalyzerResult.txt* pour chaque URL pouvant potentiellement être utilisée pour communiquer avec les services Defender for Endpoint. Par exemple :

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

Si l’une des options de connectivité renvoie un état (200), le client Defender for Endpoint peut communiquer correctement avec l’URL testée à l’aide de cette méthode de connectivité.

Toutefois, si les résultats du contrôle de la connectivité indiquent un échec, une erreur HTTP est affichée (voir Codes d'état HTTP). Vous pouvez ensuite utiliser les URL du tableau indiqué dans Activer l’accès aux URL du [service Defender pour le point de terminaison sur le serveur proxy](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). Les URL disponibles dépendent de la région sélectionnée au cours de la procédure d’intégration.

> [!NOTE]
> Les vérifications de connectivité cloud de l’outil Analyseur de connectivité ne sont pas compatibles avec les créations de processus de blocage des règles de réduction de la surface d’attaque provenant des commandes [PSExec et WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands). Vous devrez désactiver temporairement cette règle pour exécuter l’outil de connectivité. Vous pouvez également ajouter temporairement des [exclusions DE LAS](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) lors de l’exécution de l’analyseur.
>
> Lorsque telemetryProxyServer est défini dans le Registre ou via une stratégie de groupe, Defender pour le point de terminaison échoue à accéder au proxy défini.

## <a name="related-articles"></a>Articles connexes

- [Utiliser les paramètres de stratégie de groupe pour configurer et gérer les Antivirus Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md)
- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
