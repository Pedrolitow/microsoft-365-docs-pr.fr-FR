---
title: Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis
description: En savoir plus sur le Microsoft Defender for Endpoint pour les besoins et les capacités des clients du gouvernement américain disponibles
keywords: gouvernement, gcc, élevé, exigences, capacités, défenseur, Microsoft Defender pour Endpoint, point final, dod
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 0276f0464f898d3675e4cc1d6b69185e7e390a87
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572668"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender for Endpoint pour les clients du gouvernement américain, construit dans l’environnement Azure US Government, utilise les mêmes technologies sous-jacentes que Defender for Endpoint dans Azure Commercial.

Cette offre est disponible pour les clients Cloud de la communauté du secteur public, Cloud de la communauté du secteur public High et DoD et est basée sur la même prévention, détection, enquête et assainissement que la version commerciale. Toutefois, il existe certaines différences dans la disponibilité des capacités pour cette offre.

> [!NOTE]
> Si vous êtes un client Cloud de la communauté du secteur public utilisant Defender for Endpoint in Commercial, veuillez consulter les pages de documentation publique.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence
Microsoft Defender for Endpoint pour les clients du gouvernement américain nécessite l’une des offres de licences microsoft en volume suivantes :

### <a name="desktop-licensing"></a>Licence de bureau
GCC | GCC High | DoD
:---|:---|:---
Windows 10 Entreprise E5 Cloud de la communauté du secteur public | Windows 10 Entreprise E5 pour Cloud de la communauté du secteur public High | Windows 10 Entreprise E5 pour DOD
| | Microsoft 365 E5 pour Cloud de la communauté du secteur public High | Microsoft 365 G5 pour dod
| | Microsoft 365 G5 Sécurité pour Cloud de la communauté du secteur public Élevé | Microsoft 365 Sécurité G5 pour dod
Microsoft Defender pour Endpoint - Cloud de la communauté du secteur public | Microsoft Defender pour Endpoint pour Cloud de la communauté du secteur public High | Microsoft Defender pour Endpoint pour DOD

### <a name="server-licensing"></a>Licence serveur
GCC | GCC High | DoD
:---|:---|:---
Microsoft Defender pour endpoint server Cloud de la communauté du secteur public | Microsoft Defender pour endpoint server pour Cloud de la communauté du secteur public High | Microsoft Defender pour Endpoint Server pour DOD
Azure Defender pour serveurs | Défenseur azuréen pour les serveurs - Gouvernement | Défenseur azuréen pour les serveurs - Gouvernement

<br />

## <a name="portal-urls"></a>URL portail
Voici le Microsoft Defender pour les URL portail Endpoint pour les clients du gouvernement américain:

Type de client | URL du portail
:---|:---
GCC | https://gcc.securitycenter.microsoft.us
GCC High | https://securitycenter.microsoft.us
DoD | https://securitycenter.microsoft.us

<br />

## <a name="endpoint-versions"></a>Versions de point de terminaison

### <a name="standalone-os-versions"></a>Versions autonomes d’OS
Les versions OS suivantes sont prises en charge :

Version OS | GCC | GCC High | DoD
:---|:---|:---|:---
Windows 10, version 20H2 (avec [KB4586853](https://support.microsoft.com/help/4586853)) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 10, version 2004 (avec [KB4586853](https://support.microsoft.com/help/4586853)) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 10, version 1909 (avec [KB4586819](https://support.microsoft.com/help/4586819)) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 10, version 1903 (avec [KB4586819](https://support.microsoft.com/help/4586819)) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 10, version 1809 (avec [KB4586839](https://support.microsoft.com/help/4586839)) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 10, version 1803 (avec [KB4598245](https://support.microsoft.com/help/4598245)) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 10, version 1709 | ![Non](images/svg/check-no.svg)<br />Remarque : Ne sera pas pris en charge | ![Oui ](images/svg/check-yes.svg) avec [KB4499147](https://support.microsoft.com/help/4499147)<br />Note: [Déprécié, s’il vous](/lifecycle/announcements/revised-end-of-service-windows-10-1709)plaît mise à niveau | ![Non](images/svg/check-no.svg)<br />Remarque : Ne sera pas pris en charge
Windows 10, version 1703 et antérieure | ![Non](images/svg/check-no.svg)<br />Remarque : Ne sera pas pris en charge | ![Non](images/svg/check-no.svg)<br />Remarque : Ne sera pas pris en charge | ![Non](images/svg/check-no.svg)<br />Remarque : Ne sera pas pris en charge
Windows Server 2019 (avec [KB4586839](https://support.microsoft.com/help/4586839)) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows Server 2016 | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows Server 2012 R2 | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1 | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 8.1 Entreprise | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 8 Pro | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 7 SP1 Enterprise | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 7 SP1 Pro | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Linux | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
macOS | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Android | ![Non](images/svg/check-no.svg) Sur le carnet de commandes de l’ingénierie | ![Non](images/svg/check-no.svg) Sur le carnet de commandes de l’ingénierie | ![Non](images/svg/check-no.svg) Sur le carnet de commandes de l’ingénierie
iOS | ![Non](images/svg/check-no.svg) Sur le carnet de commandes de l’ingénierie | ![Non](images/svg/check-no.svg) Sur le carnet de commandes de l’ingénierie | ![Non](images/svg/check-no.svg) Sur le carnet de commandes de l’ingénierie

> [!NOTE]
> Lorsqu’un patch est spécifié, il doit être déployé avant l’in bord de l’appareil afin de configurer Defender for Endpoint dans l’environnement correct.

> [!NOTE]
> Vous essayez de les Windows plus anciens que Windows 10 ou Windows Server 2019 en utilisant [Microsoft Monitoring Agent](configure-server-endpoints.md#option-1-onboard-by-installing-and-configuring-microsoft-monitoring-agent-mma)? Vous devrez choisir « Azure US Government » sous « Azure Cloud » si vous utilisez l’assistant [de configuration,](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard)ou si vous utilisez une ligne [de commande](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) ou [un script](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) - définissez le paramètre « OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE » à 1.

### <a name="os-versions-when-using-azure-defender-for-servers"></a>Versions OS lors de l’utilisation d’Azure Defender pour les serveurs
Les versions OS suivantes sont prises en charge lors de [l’utilisation d’Azure Defender pour les serveurs](/azure/security-center/security-center-wdatp):

Version OS | GCC | GCC High | DoD
:---|:---|:---|:---
Windows Server 2019 | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement
Windows Server 2016 | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows Server 2012 R2 | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1 | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)

<br />

## <a name="required-connectivity-settings"></a>Paramètres de connectivité requis
Si un proxy ou un pare-feu bloque tout le trafic par défaut et n'autorise le passage que de domaines spécifiques, ajoutez les domaines énumérés dans la feuille téléchargeable à la liste des domaines autorisés.

La feuille de calcul téléchargeable suivante répertorie les services et leurs URL associées à qui votre réseau doit pouvoir se connecter. Vérifiez qu’il n’existe pas de règles de filtrage pare-feu ou réseau qui refuseraient l’accès à ces URL, ou *créeraient* une règle d’autoriser spécifiquement pour eux.

Liste de calcul des domaines | Description
:-----|:-----
![Image du pouce pour Microsoft Defender pour la feuille de calcul Endpoint URLs](images/mdatp-urls.png)<br/> | Feuille de calcul des enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation. <br /><br />[Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) 

Pour plus d’informations, consultez [les paramètres proxy et de connectivité Internet de l’appareil Configure.](configure-proxy-internet.md)

> [!NOTE]
> La feuille de calcul contient également des URL commerciales, assurez-vous de vérifier les onglets « Gov us ».
> 
> Lors du filtrage, recherchez les enregistrements étiquetés comme « Gov us » et votre nuage spécifique sous la colonne géographie.

### <a name="service-backend-ip-ranges"></a>Gammes IP backend service

Si vos périphériques réseau ne supporte pas les règles basées sur DNS, utilisez plutôt des plages IP.

Defender for Endpoint pour les clients du gouvernement américain est construit dans l’environnement azuréen du gouvernement américain, déployé dans les régions suivantes :

- AzureCloud.usgovtexas
- AzureCloud.usgovvirginia

Vous pouvez trouver les gammes IP Azure dans [azure IP Ranges and Service Tags – US Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063).

> [!NOTE]
> En tant que solution basée sur le cloud, les plages d’adresses IP peuvent changer. Il est recommandé de passer aux règles basées sur le DNS.

<br />

## <a name="api"></a>API
Au lieu des URL publiques répertoriées dans [notre documentation API,](apis-intro.md)vous devrez utiliser les URL suivantes :

Type de point final | GCC | Cloud de la communauté du secteur public DoD & haute qualité
:---|:---|:---
Connexion | `https://login.microsoftonline.com` | `https://login.microsoftonline.us`
Défenseur de l’API Endpoint | `https://api-gcc.securitycenter.microsoft.us` | `https://api-gov.securitycenter.microsoft.us`
SIEM | `https://wdatp-alertexporter-us.gcc.securitycenter.windows.us` | `https://wdatp-alertexporter-us.securitycenter.windows.us`

<br />

## <a name="feature-parity-with-commercial"></a>Parité des caractéristiques avec commercial
Defender for Endpoint pour les clients du gouvernement américain n’a pas la parité complète avec l’offre commerciale. Bien que notre objectif soit de fournir toutes les fonctionnalités et fonctionnalités commerciales à nos clients du gouvernement américain, certaines fonctionnalités ne sont pas encore disponibles que nous voulons mettre en évidence.

Ce sont les lacunes connues:

Nom de la fonctionnalité | GCC | GCC High | DoD
:---|:---|:---|:---
Gestion et API : API en streaming | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Filtrage du contenu web | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement
Intégrations: Azure Sentinel | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) Alertes <br /> ![Non](images/svg/check-no.svg) Incidents & données brutes : en développement | ![Oui](images/svg/check-yes.svg) Alertes <br /> ![Non](images/svg/check-no.svg) Incidents & données brutes : en développement
Intégrations : Microsoft Cloud App Security | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement
Intégrations : Microsoft Compliance Manager | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement
Intégrations: Microsoft Defender for Identity | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement
Intégrations: Microsoft Endpoint DLP | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement
Intégrations : Microsoft Intune | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Intégrations : Microsoft Power Automate & Azure Logic Apps | ![Oui](images/svg/check-yes.svg) | ![Non](images/svg/check-no.svg) En développement | ![Non](images/svg/check-no.svg) En développement
Spécialistes des menaces Microsoft | ![Non](images/svg/check-no.svg) Sur le carnet de commandes de l’ingénierie | ![Non](images/svg/check-no.svg) Sur le carnet de commandes de l’ingénierie | ![Non](images/svg/check-no.svg) Sur le carnet de commandes de l’ingénierie
