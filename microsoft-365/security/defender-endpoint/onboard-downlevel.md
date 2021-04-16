---
title: Intégrer les versions précédentes de Windows sur Microsoft Defender pour Endpoint
description: Intégrer des versions antérieures d'appareils Windows pris en charge afin qu'ils peuvent envoyer des données de capteur au capteur Microsoft Defender for Endpoint
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
ms.openlocfilehash: 945645e0f20f316c094f746adb6ba193f6806f86
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "51861358"
---
# <a name="onboard-previous-versions-of-windows"></a>Intégrer des versions antérieures de Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateformes**
- Windows 7 SP1 Entreprise
- Windows 7 SP1 Professionnel
- Windows 8.1 Professionnel
- Windows 8.1 Entreprise


>Vous souhaitez faire l'expérience de Defender for Endpoint ? [Inscrivez-vous à une version d'essai gratuite.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-downlevel-abovefoldlink)

Defender for Endpoint étend la prise en charge pour inclure des systèmes d'exploitation de bas niveau, fournissant des fonctionnalités avancées de détection d'attaques et d'investigation sur les versions de Windows pris en charge.

Pour intégrer des points de terminaison de client Windows de bas niveau à Defender for Endpoint, vous devez :
- Configurez et mettez à jour les clients System Center Endpoint Protection.
- Installez et configurez l'Agent de surveillance Microsoft (MMA) pour signaler les données de capteur à Defender for Endpoint comme indiqué ci-dessous.

> [!TIP]
> Après avoir intégré l'appareil, vous pouvez choisir d'exécuter un test de détection pour vérifier qu'il est correctement intégré au service. Pour plus d'informations, voir Exécuter un test de détection sur un point de terminaison [Defender pour point de terminaison nouvellement intégré.](run-detection-test.md)

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>Configurer et mettre à jour les clients System Center Endpoint Protection
> [!IMPORTANT]
> Cette étape est requise uniquement si votre organisation utilise System Center Endpoint Protection (SCEP).

Defender pour le point de terminaison s'intègre à System Center Endpoint Protection pour offrir une visibilité aux détections de programmes malveillants et arrêter la propagation d'une attaque dans votre organisation en interdit les fichiers potentiellement malveillants ou les programmes malveillants suspects. 

Les étapes suivantes sont nécessaires pour activer cette intégration : 
- Installer la mise à jour de la plateforme anti-programme malveillant de janvier [2017 pour les clients Endpoint Protection](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie) 
- Configurer l'appartenance au service protection cloud client SCEP sur le **paramètre** Avancé
- Configurez votre réseau pour autoriser les connexions au cloud de l'Antivirus Microsoft Defender. Pour plus d'informations, voir [Autoriser les connexions au cloud de l'Antivirus Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-network-connections-microsoft-defender-antivirus#allow-connections-to-the-microsoft-defender-antivirus-cloud)

## <a name="install-and-configure-microsoft-monitoring-agent-mma-to-report-sensor-data-to-microsoft-defender-for-endpoint"></a>Installer et configurer l'Agent de surveillance Microsoft (MMA) pour signaler les données de capteur à Microsoft Defender pour le point de terminaison

### <a name="before-you-begin"></a>Avant de commencer
Examinez les détails suivants pour vérifier la minimale requise :
- Installer le rapport de mise à jour mensuelle de [février 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
  
  > [!NOTE]
  > Applicable uniquement pour Windows 7 SP1 Entreprise et Windows 7 SP1 Professionnel. 

- Installer la mise [à jour pour la télémétrie d'expérience client et de diagnostic](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- Installer [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (ou ultérieur) ou [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

    > [!NOTE]
    > Applicable uniquement pour Windows 7 SP1 Entreprise et Windows 7 SP1 Professionnel.
    > N'installez pas .NET Framework 4.0.x, car cela va annuler l'installation ci-dessus.

- Respectez la taille minimale requise de l'agent Azure Log Analytics. Pour plus d'informations, voir [Collecter des données à partir d'ordinateurs](https://docs.microsoft.com/azure/log-analytics/log-analytics-concept-hybrid#prerequisites) dans votre environnement avec Log Analytics



1. Téléchargez le fichier d'installation de [l'agent : agent Windows 64 bits](https://go.microsoft.com/fwlink/?LinkId=828603) ou agent Windows [32 bits.](https://go.microsoft.com/fwlink/?LinkId=828604)

2. Obtenez l'ID de l'espace de travail :
   - Dans le volet de navigation Defender pour les points de terminaison, sélectionnez **Paramètres > Gestion des > l'intégration**
   - Sélectionner **Windows 7 SP1 et 8.1 comme** système d'exploitation
   - Copier l'ID d'espace de travail et la clé d'espace de travail

3. À l'aide de l'ID d'espace de travail et de la clé d'espace de travail, choisissez l'une des méthodes d'installation suivantes pour installer l'agent :
    - [Installez manuellement l'agent à l'aide du programme d'installation.](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard) <br>
      Dans la page **Options de configuration de** l'agent, **sélectionnez Connecter l'agent à Azure Log Analytics (OMS)**
    - [Installez l'agent à l'aide de la ligne de commande.](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line)
    - [Configurez l'agent à l'aide d'un script.](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation)

   > [!NOTE]
   > Si vous êtes un client du gouvernement [américain,](gov.md)sous « Azure Cloud », vous devez choisir « Azure US Government » si vous utilisez l'Assistant Installation, ou si vous utilisez une ligne de commande ou un script , définissez le paramètre « OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE » sur 1.

4. Si vous utilisez un proxy pour vous connecter à Internet, consultez la section Configurer les paramètres du proxy.

Une fois terminé, vous devriez voir les points de terminaison intégrés dans le portail dans un délai d'une heure.

### <a name="configure-proxy-and-internet-connectivity-settings"></a>Configurer les paramètres de proxy et de connectivité Internet
 
- Chaque point de terminaison Windows doit pouvoir se connecter à Internet à l'aide du protocole HTTPS. Cette connexion peut être directe, à l'aide d'un proxy ou via la [passerelle OMS.](https://docs.microsoft.com/azure/log-analytics/log-analytics-oms-gateway)
- Si un proxy ou un pare-feu bloque l'ensemble du trafic par défaut et n'autorise que des domaines spécifiques ou que l'analyse HTTPS (inspection SSL) est activée, assurez-vous d'activer l'accès aux URL du [service Defender for Endpoint.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server)

## <a name="offboard-client-endpoints"></a>Points de terminaison du client de hors-carte
Pour désinstaller, vous pouvez désinstaller l'agent MMA du point de terminaison ou le détacher des rapports à votre espace de travail Defender for Endpoint. Après l'arrêt de l'agent, le point de terminaison n'envoie plus de données de capteur à Defender for Endpoint. 

> Vous souhaitez faire l'expérience de Defender for Endpoint ? [Inscrivez-vous à une version d'essai gratuite.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-downlevele-belowfoldlink)

