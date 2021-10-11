---
title: Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis
description: En savoir plus sur les exigences et fonctionnalités de Microsoft Defender pour endpoint pour le gouvernement des États-Unis disponibles
keywords: government, gcc, high, requirements, capabilities, defender, Microsoft Defender for Endpoint, endpoint, dod
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
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c4faa3c7edcdbf9e7d4eae7b19746b7aaa43e1d6
ms.sourcegitcommit: e3b0515fd8f2aad7b8cb308159c7bcecc2bcaa24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2021
ms.locfileid: "60264755"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender pour le point de terminaison pour les clients du gouvernement des États-Unis, intégré à l’environnement Azure US Government, utilise les mêmes technologies sous-jacentes que Defender pour endpoint dans Azure Commercial.

Cette offre est disponible pour les clients Cloud de la communauté du secteur public, Cloud de la communauté du secteur public High et DoD et est basée sur les mêmes prévention, détection, examen et correction que la version commerciale. Toutefois, il existe certaines différences dans la disponibilité des fonctionnalités de cette offre.

> [!NOTE]
> Si vous êtes un client Cloud de la communauté du secteur public à l’aide de Defender for Endpoint in Commercial, reportez-vous aux pages de documentation publique.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Microsoft Defender pour le point de terminaison pour les clients du gouvernement des États-Unis nécessite l’une des offres de licence en volume Microsoft suivantes :

### <a name="desktop-licensing"></a>Licences de bureau

<br />

****

|GCC|GCC High|DoD|
|---|---|---|
|Microsoft 365 Cloud de la communauté du secteur public G5|Microsoft 365 E5 for Cloud de la communauté du secteur public High|Microsoft 365 G5 pour DOD|
|Microsoft 365 Sécurité G5 Cloud de la communauté du secteur public|Microsoft 365 Sécurité G5 pour Cloud de la communauté du secteur public élevé|Microsoft 365 Sécurité G5 pour DOD|
|Microsoft Defender pour le point de terminaison - Cloud de la communauté du secteur public|Microsoft Defender for Endpoint for Cloud de la communauté du secteur public High|Microsoft Defender pour point de terminaison pour DOD|
|Windows 10 Entreprise E5 Cloud de la communauté du secteur public|Windows 10 Entreprise E5 pour Cloud de la communauté du secteur public élevé|Windows 10 Entreprise E5 pour DOD|
|

### <a name="server-licensing"></a>Gestion des licences de serveur

<br />

****

|GCC|GCC High|DoD|
|---|---|---|
|Microsoft Defender pour Endpoint Server Cloud de la communauté du secteur public|Microsoft Defender for Endpoint Server for Cloud de la communauté du secteur public High|Microsoft Defender pour Endpoint Server pour DOD|
|Azure Defender pour les serveurs|Azure Defender pour les serveurs - Gouvernement|Azure Defender pour les serveurs - Gouvernement|
|

## <a name="portal-urls"></a>URL du portail

Les URL du portail Microsoft Defender pour les points de terminaison pour les clients du gouvernement des États-Unis sont les suivantes :

<br />

****

|Type de client|URL du portail|
|---|---|
|GCC|<https://gcc.securitycenter.microsoft.us>|
|GCC High|<https://securitycenter.microsoft.us>|
|DoD|<https://securitycenter.microsoft.us>|
|

## <a name="endpoint-versions"></a>Versions des points de terminaison

### <a name="standalone-os-versions"></a>Versions de système d’exploitation autonomes

Les versions de système d’exploitation suivantes sont pris en charge :

<br />

****

Version du système d’exploitation|GCC|GCC High|DoD
:---|:---:|:---:|:---:
Windows 11|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 21H1 et versions supérieures|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 20H2 (avec [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 2004 (avec [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 1909 (avec [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 1903 (avec [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 1809 [(avec KB4586839](https://support.microsoft.com/help/4586839) <sup>1)</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 1803 (avec [KB4598245](https://support.microsoft.com/help/4598245) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 1709|![Non.](images/svg/check-no.svg) <br /> Remarque : ne sera pas pris en charge|![Oui ](images/svg/check-yes.svg) avec [KB4499147](https://support.microsoft.com/help/4499147) <sup>1</sup> <br /> Remarque : [Deprecated](/lifecycle/announcements/revised-end-of-service-windows-10-1709), please upgrade|![Non](images/svg/check-no.svg) <br /> Remarque : ne sera pas pris en charge
Windows 10, version 1703 et antérieures|![Non.](images/svg/check-no.svg) <br /> Remarque : ne sera pas pris en charge|![Non](images/svg/check-no.svg) <br /> Remarque : ne sera pas pris en charge|![Non](images/svg/check-no.svg) <br /> Remarque : ne sera pas pris en charge
Windows Server 2022|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2019 (avec [KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2016 (moderne) <sup>2</sup>|![Oui.](images/svg/check-yes.svg) <br /> Préversion publique|![Oui](images/svg/check-yes.svg) <br /> Préversion publique|![Oui](images/svg/check-yes.svg) <br /> Préversion publique
Windows Server 2012 R2 (moderne) <sup>2</sup>|![Oui.](images/svg/check-yes.svg) <br /> Préversion publique|![Oui](images/svg/check-yes.svg) <br /> Préversion publique|![Oui](images/svg/check-yes.svg) <br /> Préversion publique
Windows Server 2016 (Hérité) <sup>3</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2012 R2 (hérité) <sup>3</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1 (hérité) <sup>3</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 8.1 Entreprise|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 8 Pro|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 7 SP1 Enterprise|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 7 SP1 Pro|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Linux|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
macOS|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Android|![Non.](images/svg/check-no.svg) En cours de développement|![Non](images/svg/check-no.svg) En cours de développement|![Non](images/svg/check-no.svg) En cours de développement
iOS|![Non.](images/svg/check-no.svg) En cours de développement|![Non](images/svg/check-no.svg) En cours de développement|![Non](images/svg/check-no.svg) En cours de développement
|

> [!NOTE]
> <sup>1</sup> Le correctif doit être déployé avant l’intégration de l’appareil afin de configurer Defender pour endpoint dans l’environnement correct.
>
> <sup>2</sup> Découvrez la [solution moderne unifiée pour Windows 2016 et 2012 R2](configure-server-endpoints.md#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview). Si vous avez précédemment intégré vos serveurs à l’aide de MMA, suivez les instructions fournies dans la [migration](server-migration.md) de serveur pour migrer vers la nouvelle solution.
>
> <sup>3</sup> Lorsque vous utilisez [Microsoft Monitoring Agent](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) vous devez choisir « Azure US Government » sous « Azure Cloud [](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) » si vous utilisez l’Assistant [Installation,](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard)ou si vous utilisez une ligne de commande ou un [script,](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) définissez le paramètre « OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE » sur 1.

### <a name="os-versions-when-using-azure-defender-for-servers"></a>Versions du système d’exploitation lors de l’utilisation d’Azure Defender pour les serveurs

Les versions de système d’exploitation suivantes sont pris en charge lors de [l’utilisation d’Azure Defender pour les serveurs](/azure/security-center/security-center-wdatp):

<br />

****

Version du système d’exploitation|GCC|GCC High|DoD
:---|:---:|:---:|:---:
Windows Server 2022|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2019|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2016|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2012 R2|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
|

## <a name="required-connectivity-settings"></a>Paramètres de connectivité requis

Si un proxy ou un pare-feu bloque tout le trafic par défaut et n'autorise le passage que de domaines spécifiques, ajoutez les domaines énumérés dans la feuille téléchargeable à la liste des domaines autorisés.

La feuille de calcul téléchargeable suivante répertorie les services et les URL associées à qui votre réseau doit pouvoir se connecter. Vérifiez qu’il n’existe aucune règle de pare-feu ou  de filtrage réseau qui refuserait l’accès à ces URL, ou créez une règle d’autoriser spécifiquement pour eux.

Liste de feuilles de calcul de domaines|Description
:-----|:-----
![Image miniature de la feuille de calcul DES URL de Microsoft Defender pour les points de terminaison.](images/mdatp-urls.png)|Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)

Pour plus d’informations, voir [Configurer les paramètres de proxy d’appareil et de connectivité Internet.](configure-proxy-internet.md)

> [!NOTE]
> La feuille de calcul contient également des URL commerciales, veillez à vérifier les onglets « US Gov ».
>
> Lors du filtrage, recherchez les enregistrements étiquetés « US Gov » et votre nuage spécifique sous la colonne de géographie.

## <a name="api"></a>API

Au lieu des URIs publics répertoriés dans la documentation de notre [API,](apis-intro.md)vous devez utiliser les URIs suivants :

<br />

****

|Type de point de terminaison|GCC|Cloud de la communauté du secteur public DoD & haut niveau|
|---|---|---|
|Connexion|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Defender for Endpoint API|`https://api-gcc.securitycenter.microsoft.us`|`https://api-gov.securitycenter.microsoft.us`|
|SIEM|`https://wdatp-alertexporter-us.gcc.securitycenter.windows.us`|`https://wdatp-alertexporter-us.securitycenter.windows.us`|
|

## <a name="feature-parity-with-commercial"></a>Parité des fonctionnalités avec commercial

Defender for Endpoint for US Government customers doesn’t have complete parity with the commercial offering. Bien que notre objectif soit de fournir toutes les fonctionnalités commerciales à nos clients du gouvernement des États-Unis, certaines fonctionnalités ne sont pas encore disponibles que nous voulons mettre en évidence.

Voici les lacunes connues :

<br />

****

|Nom de la fonctionnalité|GCC|GCC High|DoD|
|---|:---:|:---:|:---:|
|Découverte du réseau|![Oui](images/svg/check-yes.svg)|![Non](images/svg/check-no.svg) En cours de développement|![Non](images/svg/check-no.svg) En cours de développement|
|Filtrage du contenu web|![Non](images/svg/check-no.svg) En cours de développement|![Non](images/svg/check-no.svg) En cours de développement|![Non](images/svg/check-no.svg) En cours de développement|
|Intégrations : Azure Sentinel|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg) Alertes <br /> ![Oui](images/svg/check-yes.svg) Incidents & données brutes : en prévisualisation privée|![Oui](images/svg/check-yes.svg) Alertes <br /> ![Oui](images/svg/check-yes.svg) Incidents & données brutes : en prévisualisation privée|
|Intégrations : Microsoft Power Automate & Azure Logic Apps|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg) Azure Logic Apps <br /> ![Non](images/svg/check-no.svg) Power Automate : en développement|
|Spécialistes des menaces Microsoft|![Non](images/svg/check-no.svg) On engineering backlog|![Non](images/svg/check-no.svg) On engineering backlog|![Non](images/svg/check-no.svg) On engineering backlog|
