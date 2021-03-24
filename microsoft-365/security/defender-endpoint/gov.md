---
title: Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis
description: En savoir plus sur les exigences et fonctionnalités de Microsoft Defender pour endpoint pour le gouvernement des États-Unis disponibles
keywords: government, gcc, high, requirements, capabilities, defender, defender atp, mdatp, endpoint, dod
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
ms.openlocfilehash: 31928deddc2a504cc0b6c91af287e4977791c920
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065870"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender pour le point de terminaison pour les clients du gouvernement des États-Unis, intégré à l’environnement Azure Government des États-Unis, utilise les mêmes technologies sous-jacentes que Defender pour point de terminaison dans Azure Commercial.

Cette offre est disponible pour les clients GCC, GCC High et DoD et est basée sur les mêmes prévention, détection, examen et correction que la version commerciale. Toutefois, il existe certaines différences dans la disponibilité des fonctionnalités de cette offre.

> [!NOTE]
> Si vous êtes un client GCC qui utilise Defender pour Endpoint dans Commercial, reportez-vous aux pages de documentation publique.

## <a name="licensing-requirements"></a>Critères de licence
Microsoft Defender pour le point de terminaison pour les clients du gouvernement des États-Unis nécessite l’une des offres de licence en volume Microsoft suivantes :

### <a name="desktop-licensing"></a>Licences de bureau
GCC | GCC High | DoD
:---|:---|:---
Windows 10 Entreprise E5 GCC | Windows 10 Entreprise E5 pour GCC High | Windows 10 Entreprise E5 pour DOD
| | Microsoft 365 E5 pour GCC High | 
| | Sécurité Microsoft 365 G5 pour GCC High | 
Microsoft Defender pour le point de terminaison - GCC | Microsoft Defender pour point de terminaison pour GCC High | Microsoft Defender pour point de terminaison pour DOD

### <a name="server-licensing"></a>Gestion des licences de serveur
GCC | GCC High | DoD
:---|:---|:---
Microsoft Defender pour Endpoint Server GCC | Microsoft Defender pour Endpoint Server pour GCC High | Microsoft Defender pour Endpoint Server pour DOD
Azure Defender pour les serveurs | Azure Defender pour les serveurs - Gouvernement | Azure Defender pour les serveurs - Gouvernement

> [!NOTE]
> La gestion des licences DoD sera disponible uniquement à la disponibilité générale du DoD.

<br>

## <a name="portal-urls"></a>URL du portail
Les URL du portail Microsoft Defender pour les points de terminaison pour les clients du gouvernement des États-Unis sont les suivantes :

Type de client | URL du portail
:---|:---
GCC | https://gcc.securitycenter.microsoft.us
GCC High | https://securitycenter.microsoft.us
DoD (APERÇU) | https://securitycenter.microsoft.us

<br>

## <a name="endpoint-versions"></a>Versions des points de terminaison

### <a name="standalone-os-versions"></a>Versions de système d’exploitation autonomes
Les versions de système d’exploitation suivantes sont pris en charge :

Version du système d’exploitation | GCC | GCC High | DoD (APERÇU)
:---|:---|:---|:---
Windows 10, version 20H2 (avec [KB4586853)](https://support.microsoft.com/help/4586853) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg) | ![Oui](images/svg/check-yes.svg)
Windows 10, version 2004 (avec [KB4586853)](https://support.microsoft.com/help/4586853) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows 10, version 1909 (avec [KB4586819)](https://support.microsoft.com/help/4586819) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows 10, version 1903 (avec [KB4586819)](https://support.microsoft.com/help/4586819) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows 10, version 1809 (avec [KB4586839](https://support.microsoft.com/help/4586839)) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows 10, version 1803 (avec [KB4598245](https://support.microsoft.com/help/4598245)) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows 10, version 1709 | ![Non](/security/defender-endpoint/images/svg/check-no)<br>Remarque : ne sera pas pris en charge | ![Oui ](/security/defender-endpoint/images/svg/check-yes) avec [KB4499147](https://support.microsoft.com/help/4499147)<br>Remarque : [Deprecated](https://docs.microsoft.com/lifecycle/announcements/revised-end-of-service-windows-10-1709), please upgrade | ![Non](/security/defender-endpoint/images/svg/check-no)<br>Remarque : ne sera pas pris en charge
Windows 10, version 1703 et versions antérieures | ![Non](/security/defender-endpoint/images/svg/check-no)<br>Remarque : ne sera pas pris en charge | ![Non](/security/defender-endpoint/images/svg/check-no)<br>Remarque : ne sera pas pris en charge | ![Non](/security/defender-endpoint/images/svg/check-no)<br>Remarque : ne sera pas pris en charge
Windows Server 2019 (avec [KB4586839)](https://support.microsoft.com/help/4586839) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows Server 2016 | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows Server 2012 R2 | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows Server 2008 R2 SP1 | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows 8.1 Entreprise | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows 8 Pro | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows 7 SP1 Entreprise | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows 7 SP1 Professionnel | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Linux | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement
macOS | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement
Android | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog
iOS | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog

> [!NOTE]
> Lorsqu’un correctif est spécifié, il doit être déployé avant l’intégration de l’appareil afin de configurer Defender pour Endpoint dans l’environnement correct.

> [!NOTE]
> Vous essayez d’intégrer des appareils Windows plus anciens que Windows 10 ou Windows Server 2019 à l’aide de [l’Agent de surveillance Microsoft](configure-server-endpoints.md#option-1-onboard-by-installing-and-configuring-microsoft-monitoring-agent-mma)? Vous devez choisir « Azure US Government » sous « Azure Cloud » [](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) si vous utilisez l’Assistant Installation [ou](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard)si vous utilisez une ligne de commande ou un [script,](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) définissez le paramètre « OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE » sur 1.

### <a name="os-versions-when-using-azure-defender-for-servers"></a>Versions du système d’exploitation lors de l’utilisation d’Azure Defender pour les serveurs
Les versions de système d’exploitation suivantes sont pris en charge lors de [l’utilisation d’Azure Defender pour les serveurs](https://docs.microsoft.com/azure/security-center/security-center-wdatp):

Version du système d’exploitation | GCC | GCC High | DoD (APERÇU)
:---|:---|:---|:---
Windows Server 2016 | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows Server 2012 R2 | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Windows Server 2008 R2 SP1 | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)

<br>

## <a name="required-connectivity-settings"></a>Paramètres de connectivité requis
Si un proxy ou un pare-feu bloque tout le trafic par défaut et n'autorise le passage que de domaines spécifiques, ajoutez les domaines énumérés dans la feuille téléchargeable à la liste des domaines autorisés.

La feuille de calcul téléchargeable suivante répertorie les services et les URL associées à qui votre réseau doit pouvoir se connecter. Vérifiez qu’il n’existe aucune règle de pare-feu ou  de filtrage réseau qui refuserait l’accès à ces URL, ou créez une règle d’autoriser spécifiquement pour elles.

Liste de feuilles de calcul de domaines | Description
:-----|:-----
![Image miniature de la feuille de calcul DES URL de Microsoft Defender pour les points de terminaison](images/mdatp-urls.png)<br/> | Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation. <br><br>[Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) 

Pour plus d’informations, voir [Configurer les paramètres de proxy d’appareil et de connectivité Internet.](configure-proxy-internet.md)

> [!NOTE]
> La feuille de calcul contient également des URL commerciales, veillez à vérifier les onglets « US Gov ». <br> Lors du filtrage, recherchez les enregistrements étiquetés « US Gov » et votre nuage spécifique sous la colonne de géographie.

<br>

## <a name="api"></a>API
Au lieu des URIs publics répertoriés dans la documentation de notre [API,](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/apis-intro)vous devez utiliser les URIs suivants :

Type de point de terminaison | GCC | GCC High & DoD (PREVIEW)
:---|:---|:---
Connexion | `https://login.microsoftonline.com` | `https://login.microsoftonline.us`
Defender for Endpoint API | `https://api-gcc.securitycenter.microsoft.us` | `https://api-gov.securitycenter.microsoft.us`
SIEM | `https://wdatp-alertexporter-us.gcc.securitycenter.windows.us` | `https://wdatp-alertexporter-us.securitycenter.windows.us`

<br>

## <a name="feature-parity-with-commercial"></a>Parité des fonctionnalités avec commercial
Defender pour le point de terminaison n’a pas une parité complète avec l’offre commerciale. Bien que notre objectif soit de fournir toutes les fonctionnalités commerciales à nos clients du gouvernement des États-Unis, certaines fonctionnalités ne sont pas encore disponibles que nous voulons mettre en évidence.

Voici les lacunes connues depuis février 2021 :

Nom de la fonctionnalité | GCC | GCC High | DoD (APERÇU)
:---|:---|:---|:---
Examen et correction automatisés : réponse en direct | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Examen et correction automatisés : réponse aux alertes Office 365 | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog
Notifications par e-mail | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de déploiement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de déploiement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de déploiement
Laboratoire d’évaluation | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Gestion et API : rapport sur l’état et la conformité des appareils | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Gestion et API : intégration avec des produits tiers | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement
Gestion et API : API de diffusion en continu | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement
Gestion et API : rapport sur la protection contre les menaces | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Gestion des & menaces | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Analyses de menaces | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Filtrage de contenu Web | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement
Intégrations : Azure Sentinel | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement
Intégrations : Microsoft Cloud App Security | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog
Intégrations : Gestionnaire de conformité Microsoft | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog
Intégrations : Microsoft Defender pour l’identité | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog
Intégrations : Microsoft Defender pour Office 365 | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog
Intégrations : point de terminaison Microsoft DLP | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog
Intégrations : Microsoft Intune | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement
Intégrations : Microsoft Power Automate & Azure Logic Apps | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement | ![Non](/security/defender-endpoint/images/svg/check-no) En cours de développement
Intégrations : Skype Entreprise /Teams | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes) | ![Oui](/security/defender-endpoint/images/svg/check-yes)
Spécialistes des menaces Microsoft | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog | ![Non](/security/defender-endpoint/images/svg/check-no) On engineering backlog
