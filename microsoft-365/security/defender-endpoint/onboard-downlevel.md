---
title: Intégrer les versions précédentes de Windows sur Microsoft Defender for Endpoint
description: Intégrer les versions antérieures des appareils Windows pris en charge afin qu’ils peuvent envoyer des données de capteur au capteur Microsoft Defender for Endpoint
keywords: onboard, windows, 7, 81, oms, sp1, enterprise, pro, down level
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 70ef9aabd86169cd64f252f26a792a380dc6fe44ddb7060bd6c7a8f19d3c6c22
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53806195"
---
# <a name="onboard-previous-versions-of-windows"></a>Intégrer des versions antérieures de Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateformes**
- Windows 7 SP1 Enterprise
- Windows 7 SP1 Pro
- Windows 8.1 Professionnel
- Windows 8.1 Entreprise


> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

Defender for Endpoint étend la prise en charge pour inclure des systèmes d’exploitation de bas niveau, fournissant des fonctionnalités avancées de détection d’attaques et d’investigation sur les versions Windows pris en charge.

Pour intégrer des points de terminaison Windows client de niveau inférieur à Defender for Endpoint, vous devez :

- Configurez et mettez à jour System Center Endpoint Protection clients.
- Installez et configurez Microsoft Monitoring Agent (MMA) pour signaler les données de capteur à Defender for Endpoint comme indiqué ci-dessous.

> [!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’il est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un point de terminaison [Defender pour point de terminaison nouvellement intégré.](run-detection-test.md)

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>Configurer et mettre à jour System Center Endpoint Protection clients
> [!IMPORTANT]
> Cette étape est requise uniquement si votre organisation utilise System Center Endpoint Protection (SCEP).

Defender pour le point de terminaison s’intègre à System Center Endpoint Protection pour fournir une visibilité aux détections de programmes malveillants et pour arrêter la propagation d’une attaque dans votre organisation en interdit les fichiers potentiellement malveillants ou les programmes malveillants suspects.

Les étapes suivantes sont nécessaires pour activer cette intégration :

- Installer la mise à jour de la plateforme anti-programme malveillant de janvier [2017 pour Endpoint Protection clients](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie) 
- Configurer l’appartenance au service protection cloud client SCEP sur le **paramètre** Avancé
- Configurez votre réseau pour autoriser les connexions au Antivirus Microsoft Defender cloud. Pour plus d’informations, voir [Autoriser les connexions au Antivirus Microsoft Defender cloud](/windows/security/threat-protection/microsoft-defender-antivirus/configure-network-connections-microsoft-defender-antivirus#allow-connections-to-the-microsoft-defender-antivirus-cloud)

## <a name="install-and-configure-microsoft-monitoring-agent-mma-to-report-sensor-data-to-microsoft-defender-for-endpoint"></a>Installer et configurer Microsoft Monitoring Agent (MMA) pour signaler les données de capteur à Microsoft Defender pour le point de terminaison

### <a name="before-you-begin"></a>Avant de commencer

Examinez les détails suivants pour vérifier la minimale requise :

- Installer le rapport de mise à jour mensuelle de [février 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
  
  > [!NOTE]
  > Applicable uniquement pour Windows 7 SP1 Enterprise et Windows 7 SP1 Pro.

- Installer la mise [à jour pour la télémétrie d’expérience client et de diagnostic](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- Installer [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (ou ultérieur) ou [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

    > [!NOTE]
    > Applicable uniquement pour Windows 7 SP1 Enterprise et Windows 7 SP1 Pro.
    > N’installez pas .NET Framework 4.0.x, car cela va annuler l’installation ci-dessus.

- Respectez la taille minimale requise de l’agent Azure Log Analytics. Pour plus d’informations, voir [Collecter des données à partir d’ordinateurs](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites)de votre environnement avec Log Analytics.

1. Téléchargez le fichier de configuration de [l’agent : Windows agent 64 bits](https://go.microsoft.com/fwlink/?LinkId=828603) ou Windows agent [32 bits.](https://go.microsoft.com/fwlink/?LinkId=828604)

2. Obtenez l’ID de l’espace de travail :
   - Dans le volet de navigation Defender pour les points de terminaison, sélectionnez Paramètres > points de terminaison > gestion des > **l’intégration**
   - Sélectionnez **Windows 7 SP1 et 8.1 comme** système d’exploitation
   - Copier l’ID d’espace de travail et la clé d’espace de travail

3. À l’aide de l’ID d’espace de travail et de la clé d’espace de travail, choisissez l’une des méthodes d’installation suivantes pour installer l’agent :
    - [Installez manuellement l’agent à l’aide du programme d’installation.](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard)

      Dans la page **Options de configuration** de l’agent, **sélectionnez Connecter l’agent dans Azure Log Analytics (OMS)**

    - [Installez l’agent à l’aide de la ligne de commande.](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line)
    - [Configurez l’agent à l’aide d’un script.](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation)

   > [!NOTE]
   > Si vous [](gov.md)êtes un client du gouvernement des États-Unis, sous « Azure Cloud », vous devez choisir « Azure US Government » si vous utilisez l’Assistant Installation, ou si vous utilisez une ligne de commande ou un script , définissez le paramètre « OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE » sur 1.

4. Si vous utilisez un proxy pour vous connecter à Internet, consultez la section Configurer les paramètres du proxy.

Une fois terminé, vous devriez voir les points de terminaison intégrés dans le portail dans un délai d’une heure.

### <a name="configure-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy et de connectivité Internet

- Chaque Windows point de terminaison doit pouvoir se connecter à Internet à l’aide du protocole HTTPS. Cette connexion peut être directe, à l’aide d’un proxy ou via la [passerelle OMS.](/azure/log-analytics/log-analytics-oms-gateway)
- Si un proxy ou un pare-feu bloque tout le trafic par défaut et n’autorise que des domaines spécifiques ou que l’analyse HTTPS (inspection SSL) est activée, assurez-vous d’activer l’accès aux URL du [service Defender for Endpoint.](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server)

## <a name="offboard-client-endpoints"></a>Points de terminaison du client de hors-carte

Pour désinstaller, vous pouvez désinstaller l’agent MMA du point de terminaison ou le détacher des rapports à votre espace de travail Defender for Endpoint. Après l’arrêt de l’agent, le point de terminaison n’envoie plus de données de capteur à Defender for Endpoint.

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevele-belowfoldlink)
