---
title: Configurer les paramètres de proxy d’appareil et de connexion Internet
description: Configurez les paramètres proxy et Internet Microsoft Defender pour point de terminaison pour permettre la communication avec le service cloud.
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
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1faff638c9b33b933277dc74248c2d7daa43331c
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669669"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy du dispositif et de connectivité Internet

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Le capteur Defender pour point de terminaison requiert Microsoft Windows HTTP (WinHTTP) pour signaler les données du capteur et communiquer avec le service Defender pour point de terminaison. Le capteur Defender pour point de terminaison incorporé s’exécute dans le contexte système à l’aide du compte LocalSystem. Le capteur utilise Microsoft Windows HTTP Services (WinHTTP) pour activer la communication avec le service cloud Defender pour point de terminaison.

> [!TIP]
> Pour les organisations qui utilisent des proxys de transfert comme passerelle vers Internet, vous pouvez utiliser la protection réseau pour [examiner les événements de connexion qui se produisent derrière les proxys de transfert](investigate-behind-proxy.md).

Le paramètre de configuration WinHTTP est indépendant des paramètres de proxy de navigation Windows Internet (WinINet) (voir [WinINet et WinHTTP](/windows/win32/wininet/wininet-vs-winhttp)). Il peut uniquement découvrir un serveur proxy à l’aide des méthodes de découverte suivantes :

- Méthodes de découverte automatique :

  - Proxy transparent
  
  - Protocole WPAD (Web Proxy Auto-Discovery Protocol)

    > [!NOTE]
    > Si vous utilisez un proxy transparent ou WPAD dans votre topologie de réseau, vous n’avez pas besoin de paramètres de configuration spéciaux. Pour plus d’informations sur les exclusions d’URL Defender pour point de terminaison dans le proxy, consultez [Activer l’accès aux URL du service Defender pour point de terminaison dans le serveur proxy](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- Configuration manuelle du proxy statique :

  - Configuration basée sur le registre
  
  - WinHTTP configuré à l’aide de la commande netsh : convient uniquement aux bureaux dans une topologie stable (par exemple, un bureau dans un réseau d’entreprise derrière le même proxy)

> [!NOTE]
> L’antivirus Defender et les proxys PEPT peuvent être définis indépendamment.  Dans les sections qui suivent, tenez compte de ces distinctions.

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Configurer le serveur proxy manuellement en utilisant un proxy statique basé sur le registre

Configurez un capteur de détection et de réponse statique basé sur le Registre pour defender pour point de terminaison (PEPT) pour signaler les données de diagnostic et communiquer avec les services Defender pour point de terminaison si un ordinateur n’est pas autorisé à se connecter à Internet.

> [!NOTE]
> Lorsque vous utilisez cette option sur Windows 10, ou Windows 11, ou Windows Server 2019 ou Windows Server 2022, il est recommandé de disposer des éléments suivants (ou ultérieurs) pour générer et cumuler les mises à jour cumulatives :
>
> - Windows 11
> - Windows 10, version 1809 ou Windows Server 2019 ou Windows Server 2022 -<https://support.microsoft.com/kb/5001384>
> - Windows 10, version 1909 -<https://support.microsoft.com/kb/4601380>
> - Windows 10, version 2004 -<https://support.microsoft.com/kb/4601382>
> - Windows 10, version 20H2 -<https://support.microsoft.com/kb/4601382>
>
> Ces mises à jour améliorent la connectivité et la fiabilité du canal CnC (Command and Control).

Le proxy statique est configurable via une stratégie de groupe (GP), les deux paramètres sous les valeurs de stratégie de groupe doivent être configurés sur le serveur proxy pour l’utilisation de PEPT. La stratégie de groupe est disponible dans les modèles d’administration.

- **Les modèles d’administration > Windows composants > la collecte de données et les builds en préversion > configurer l’utilisation du proxy authentifié pour l’expérience utilisateur connectée et le service de télémétrie**.

  Définissez-le sur **Activé** et sélectionnez **Désactiver l’utilisation du proxy authentifié**.

  :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="Volet d’état stratégie de groupe setting1" lightbox="images/atp-gpo-proxy1.png":::

- **Les modèles d’administration > Windows composants > la collecte de données et les builds en préversion > configurer les expériences utilisateur connectées et la télémétrie** :

  Configurez le proxy.

  :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="Volet d’état stratégie de groupe setting2" lightbox="images/atp-gpo-proxy2.png":::


| Stratégie de groupe | Clé du Registre | Entrée de Registre | Valeur |
|:---|:---|:---|:---|
| Configurer l’utilisation du proxy authentifié pour l’expérience utilisateur connectée et le service de télémétrie | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `DisableEnterpriseAuthProxy` | 1 (REG_DWORD) |
| Configurer les expériences et la télémétrie des utilisateurs connectés | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `TelemetryProxyServer` | ```servername:port or ip:port``` <br> <br> Par exemple : ```10.0.0.6:8080``` (REG_SZ) |

## <a name="configure-a-static-proxy-for-microsoft-defender-antivirus"></a>Configurer un proxy statique pour Antivirus Microsoft Defender

Antivirus Microsoft Defender [protection fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md) offre une protection quasi instantanée et automatisée contre les menaces nouvelles et émergentes. Notez que la connectivité est requise pour [les indicateurs personnalisés](manage-indicators.md) lorsque l’antivirus Defender est votre solution anti-programme malveillant active. Pour [PEPT en mode bloc](edr-in-block-mode.md) dispose d’une solution anti-programme malveillant principale lors de l’utilisation d’une solution non Microsoft.

Configurez le proxy statique à l’aide des stratégie de groupe disponibles dans les modèles d’administration :

1. **Modèles d’administration > Windows composants > Antivirus Microsoft Defender > Définir un serveur proxy pour la connexion au réseau**. 

2. Définissez-le sur **Activé** et définissez le serveur proxy. Notez que l’URL doit avoir http:// ou https://. Pour les versions prises en charge pour https://, consultez [Gérer les mises à jour Antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md).

   :::image type="content" source="images/proxy-server-mdav.png" alt-text="Serveur proxy pour Antivirus Microsoft Defender" lightbox="images/proxy-server-mdav.png":::

3. Sous la clé de Registre, la stratégie `HKLM\Software\Policies\Microsoft\Windows Defender`définit la valeur `ProxyServer` de Registre comme REG_SZ. 

   La valeur `ProxyServer` du Registre prend le format de chaîne suivant :

    ```text
    <server name or ip>:<port>

    For example: http://10.0.0.6:8080
    ```

> [!NOTE]
>
> Pour des raisons de résilience et pour la nature en temps réel de la protection fournie par le cloud, Antivirus Microsoft Defender met en cache le dernier proxy de travail connu. Vérifiez que votre solution proxy n’effectue pas d’inspection SSL. Cela va interrompre la connexion cloud sécurisée. 
>
> Antivirus Microsoft Defender n’utiliserez pas le proxy statique pour se connecter à Windows Update ou à Microsoft Update pour télécharger les mises à jour. Au lieu de cela, il utilise un proxy à l’échelle du système s’il est configuré pour utiliser Windows Update, ou la source de mise à jour interne configurée en fonction de [l’ordre de secours configuré](manage-protection-updates-microsoft-defender-antivirus.md). 
>
> Si nécessaire, vous pouvez utiliser **des modèles d’administration > Windows composants > Antivirus Microsoft Defender > Définir la configuration automatique du proxy (.pac)** pour la connexion au réseau. Si vous devez configurer des configurations avancées avec plusieurs proxys, utilisez des modèles d’administration **> Windows composants > Antivirus Microsoft Defender > Définir des adresses** pour contourner le serveur proxy et empêcher Antivirus Microsoft Defender d’utiliser un serveur proxy pour ces destinations. 
>
> Vous pouvez utiliser PowerShell avec l’applet `Set-MpPreference` de commande pour configurer ces options : 
>
> - ProxyBypass 
> - ProxyPacUrl 
> - Proxyserver 

> [!NOTE]
> Pour utiliser correctement le proxy, configurez ces trois paramètres de proxy différents :
>  - Microsoft Defender pour point de terminaison (MDE)
>  - AV (Antivirus)
>  - Détection et réponse des points de terminaison (PEPT)

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Configurer le serveur proxy manuellement à l’aide de la commande netsh

Utiliser netsh pour configurer un proxy statique à l’échelle du système.

> [!NOTE]
>
> - Cela affectera toutes les applications, y compris les services Windows qui utilisent WinHTTP avec un proxy par défaut.</br>
> - Les ordinateurs portables qui changent de topologie (par exemple, d’un bureau à l’autre) ne fonctionnent pas correctement avec la commande netsh. Utiliser la configuration statique du proxy basée sur le registre.

1. Ouvrez une invite de commandes avec élévation de privilèges :
   1. Accéder à **Démarrer** et taper **cmd**.
   1. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante et appuyez sur **Entrée** :

   ```command prompt
   netsh winhttp set proxy <proxy>:<port>
   ```

   Par exemple : `netsh winhttp set proxy 10.0.0.6:8080`

Pour réinitialiser le proxy winhttp, entrez la commande suivante et appuyez sur **Entrée** :

```command prompt
netsh winhttp reset proxy
```

Pour plus d’informations, voir [la syntaxe, les contextes et le formatage de la commande Netsh](/windows-server/networking/technologies/netsh/netsh-contexts).

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>Activer l’accès aux URL de service Microsoft Defender pour point de terminaison dans le serveur proxy

Par défaut, si un proxy ou un pare-feu bloque tout le trafic par défaut et autorise uniquement des domaines spécifiques, ajoutez les domaines répertoriés dans la feuille téléchargeable à la liste des domaines autorisés.

La feuille de calcul téléchargeable suivante répertorie les services et leurs URL associées que votre réseau doit pouvoir connecter. Vérifiez qu’il n’existe aucune règle de pare-feu ou de filtrage réseau pour refuser l’accès à ces URL. Facultatif, vous devrez peut-être créer une règle *d’autorisation* spécifiquement pour eux.

<br>

|Feuille de calcul de la liste des domaines| Description|
|---|---|
|liste d’URL Microsoft Defender pour point de terminaison pour les clients commerciaux| Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation des clients commerciaux. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender pour point de terminaison liste d’URL pour Gov/Cloud de la communauté du secteur public/DoD | Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation pour les clients Gov/Cloud de la communauté du secteur public/DoD. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Si l’analyse HTTPS (inspection SSL) est activée pour un proxy ou un pare-feu, excluez les domaines répertoriés dans le tableau ci-dessus de l’analyse HTTPS.
Dans votre pare-feu, ouvrez toutes les URL où la colonne géographique est WW. Pour les lignes où la colonne géographique n’est pas WW, ouvrez les URL à votre emplacement de données spécifique. Pour vérifier votre paramètre d’emplacement de données, consultez [Vérifier l’emplacement de stockage des données et mettre à jour les paramètres de rétention des données pour Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/data-retention-settings).

> [!NOTE]
> Windows appareils s’exécutant avec la version 1803 ou des besoins antérieurs `settings-win.data.microsoft.com`.  <br>
>
> Les URL qui incluent la version 20 ne sont nécessaires que si vous avez Windows appareils exécutant la version 1803 ou ultérieure. Par exemple, `us-v20.events.data.microsoft.com` est nécessaire pour un appareil Windows exécutant la version 1803 ou ultérieure et intégré à la région US Data Stockage.
>

Si un proxy ou un pare-feu bloque le trafic anonyme en tant que capteur Defender pour point de terminaison et qu’il se connecte à partir du contexte système pour s’assurer que le trafic anonyme est autorisé dans les URL précédemment répertoriées.

> [!NOTE]
> Microsoft ne fournit pas de serveur proxy. Ces URL sont accessibles via le serveur proxy que vous configurez.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (MMA) : exigences de proxy et de pare-feu pour les versions antérieures du client Windows ou du serveur Windows

Les informations figurant dans la liste des informations de configuration de proxy et de pare-feu sont nécessaires pour communiquer avec l’agent Log Analytics (souvent appelé Microsoft Monitoring Agent) pour les versions précédentes de Windows, telles que Windows 7 SP1, Windows 8.1 et Windows Server 2008 R2*.

<br>

****

|Ressource d'agent|Ports|Direction|Contournement de l’inspection HTTPS|
|---|---|---|---|
|*.ods.opinsights.azure.com|Port 443|Sortant|Oui|
|*.oms.opinsights.azure.com|Port 443|Sortant|Oui|
|*.blob.core.windows.net|Port 443|Sortant|Oui|
|*.azure-automation.net|Port 443|Sortant|Oui|

> [!NOTE]
> *Ces exigences de connectivité s’appliquent aux Microsoft Defender pour point de terminaison précédentes de Windows Server 2016 et Windows Server 2012 R2 qui nécessite MMA. Les instructions pour intégrer ces systèmes d’exploitation à la nouvelle solution unifiée sont fournies sur [les serveurs d’intégration Windows](configure-server-endpoints.md), ou migrez vers la nouvelle solution unifiée dans [les scénarios de migration de serveur dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> En tant que solution cloud, la plage d’adresses IP peut changer. Il est recommandé de passer au paramètre de résolution DNS.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>Confirmer la configuration requise pour l’URL du service Microsoft Monitoring Agent (MMA) 

 Consultez les conseils suivants pour éliminer la spécification de caractères génériques (*) pour votre environnement spécifique lors de l’utilisation de la Microsoft Monitoring Agent (MMA) pour les versions précédentes de Windows.

1. Intégrer un système d’exploitation précédent avec le Microsoft Monitoring Agent (MMA) dans Defender pour point de terminaison (pour plus d’informations, consultez [Intégrer les versions précédentes de Windows sur Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2010326) et [intégrer des serveurs Windows](configure-server-endpoints.md)).

2. Vérifiez que l’ordinateur est correctement signalé dans le portail Microsoft 365 Defender.

3. Exécutez l’outil TestCloudConnection.exe à partir de « C:\Program Files\Microsoft Monitoring Agent\Agent » pour valider la connectivité et obtenir les URL requises pour votre espace de travail spécifique.

4. Consultez la liste des URL Microsoft Defender pour point de terminaison pour obtenir la liste complète des conditions requises pour votre région (reportez-vous à la feuille de [calcul](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx) des URL de service).

   :::image type="content" source="images/admin-powershell.png" alt-text="L’administrateur dans Windows PowerShell" lightbox="images/admin-powershell.png":::

Les caractères génériques (\*) utilisés dans \*les points de terminaison d’URL .ods.opinsights.azure.com, \*.oms.opinsights.azure.com et \*.agentsvc.azure-automation.net peuvent être remplacés par votre ID d’espace de travail spécifique. L’ID d’espace de travail est spécifique à votre environnement et à votre espace de travail. Il se trouve dans la section Intégration de votre locataire dans le portail Microsoft 365 Defender.

Le \*point de terminaison d’URL .blob.core.windows.net peut être remplacé par les URL indiquées dans la section « Règle de pare-feu : \*.blob.core.windows.net » des résultats du test.

> [!NOTE]
> Dans le cas de l’intégration via Microsoft Defender pour le cloud, plusieurs espaces de travail peuvent être utilisés. Vous devez effectuer la procédure TestCloudConnection.exe sur l’ordinateur intégré à partir de chaque espace de travail (pour déterminer s’il y a des modifications apportées aux URL *.blob.core.windows.net entre les espaces de travail).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>Vérifier la connectivité du client aux URL de service Microsoft Defender pour point de terminaison

Vérifiez que la configuration du proxy est terminée avec succès. WinHTTP peut ensuite découvrir et communiquer via le serveur proxy de votre environnement, puis le serveur proxy autorise le trafic vers les URL du service Defender pour point de terminaison.

1. Téléchargez [l’outil Microsoft Defender pour point de terminaison Client Analyzer](https://aka.ms/mdeanalyzer) sur le PC sur lequel le capteur Defender pour point de terminaison s’exécute. Pour les serveurs de niveau inférieur, utilisez la dernière édition en préversion disponible en téléchargement [Microsoft Defender pour point de terminaison l’outil Analyseur client bêta](https://aka.ms/BetaMDEAnalyzer).

2. Extrayez le contenu de MDEClientAnalyzer.zip sur l’appareil.

3. Ouvrez une invite de commandes avec élévation de privilèges :
   1. Accéder à **Démarrer** et taper **cmd**.
   1. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

4. Entrez la commande suivante et appuyez sur **Entrée** :

    ```command prompt
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    Remplacez *HardDrivePath* par le chemin d’accès, où l’outil MDEClientAnalyzer a été téléchargé. Par exemple :

    ```command prompt
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. L’outil crée et extrait le fichier *MDEClientAnalyzerResult.zip* dans le dossier à utiliser dans *HardDrivePath*.

6. Ouvrez *MDEClientAnalyzerResult.txt* et vérifiez que vous avez effectué les étapes de configuration du proxy pour activer la découverte du serveur et l’accès aux URL de service.

   L’outil vérifie la connectivité des URL du service Defender pour point de terminaison. Vérifiez que le client Defender pour point de terminaison est configuré pour interagir. L’outil imprime les résultats dans le fichier *MDEClientAnalyzerResult.txt* pour chaque URL qui peut potentiellement être utilisée pour communiquer avec les services Defender pour point de terminaison. Par exemple :

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

Si l’une des options de connectivité retourne un état (200), le client Defender pour point de terminaison peut communiquer correctement avec l’URL testée à l’aide de cette méthode de connectivité.

Toutefois, si les résultats du contrôle de la connectivité indiquent un échec, une erreur HTTP est affichée (voir Codes d'état HTTP). Vous pouvez ensuite utiliser les URL du tableau indiqué dans [Activer l’accès aux URL du service Defender pour point de terminaison dans le serveur proxy](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). Les URL disponibles dépendent de la région sélectionnée pendant la procédure d’intégration.

> [!NOTE]
> Les vérifications de connectivité cloud de l’outil Analyseur de connectivité ne sont pas compatibles avec les créations de processus de bloc de règle de réduction de la surface d’attaque [provenant des commandes PSExec et WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands). Vous devez désactiver temporairement cette règle pour exécuter l’outil de connectivité. Vous pouvez également ajouter temporairement [des exclusions ASR](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) lors de l’exécution de l’analyseur.
>
> Lorsque TelemetryProxyServer est défini dans le Registre ou via stratégie de groupe, Defender pour point de terminaison revient en arrière, il ne parvient pas à accéder au proxy défini.

## <a name="related-articles"></a>Articles connexes

- [Utiliser stratégie de groupe paramètres pour configurer et gérer Antivirus Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md)
- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Résoudre les problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
