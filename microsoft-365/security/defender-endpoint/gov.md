---
title: Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis
description: En savoir plus sur les Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis et les fonctionnalités disponibles
keywords: government, gcc, high, requirements, capabilities, defender, Microsoft Defender pour point de terminaison, endpoint, dod
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
ms.date: 10/12/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 6de59878f5e1488e06c695584e9c0665bac225bf
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68732666"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis, intégré à l’environnement Azure US Government, utilise les mêmes technologies sous-jacentes que Defender pour point de terminaison dans Azure Commercial.

Cette offre est disponible pour les clients GCC, GCC High et DoD et est basée sur les mêmes prévention, détection, investigation et correction que la version commerciale. Toutefois, il existe des différences dans la disponibilité des fonctionnalités de cette offre.

> [!NOTE]
> Si vous êtes un client GCC utilisant Defender pour point de terminaison dans Commercial, reportez-vous aux pages de documentation publiques.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Microsoft Defender pour point de terminaison pour les clients du gouvernement des États-Unis nécessite l’une des offres de licence en volume Microsoft suivantes :

### <a name="desktop-licensing"></a>Licences des ordinateurs de bureau

<br />

****

|GCC|GCC High|DoD|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 pour GCC High|Microsoft 365 G5 pour DOD|
|Microsoft 365 G5 Security GCC|Sécurité Microsoft 365 G5 pour GCC High|Microsoft 365 G5 Security for DOD|
|Microsoft Defender pour point de terminaison - GCC|Microsoft Defender pour point de terminaison pour GCC High|Microsoft Defender pour point de terminaison pour DOD|
|Windows 10 Entreprise E5 GCC|Windows 10 Entreprise E5 pour GCC High|Windows 10 Entreprise E5 pour DOD|

### <a name="server-licensing"></a>Gestion des licences du serveur

<br />

****

|GCC|GCC High|DoD|
|---|---|---|
|Microsoft Defender pour point de terminaison Server GCC|Microsoft Defender pour point de terminaison Server pour GCC High|Microsoft Defender pour point de terminaison Server pour DOD|
|Microsoft Defender pour les serveurs|Microsoft Defender pour les serveurs - Secteur public|Microsoft Defender pour les serveurs - Secteur public|

## <a name="portal-urls"></a>URL du portail

Voici les URL du portail Microsoft Defender pour point de terminaison pour les clients us Government :

<br />

****

|Type de client|URL du portail|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC High|<https://security.microsoft.us>|
|DoD|<https://security.apps.mil>|

> [!NOTE]
> Si vous êtes un client gcc et que vous êtes en train de passer de Microsoft Defender pour point de terminaison commercial à GCC, utilisez https://transition.security.microsoft.com pour accéder à vos données commerciales Microsoft Defender pour point de terminaison.

## <a name="endpoint-versions"></a>Versions de point de terminaison

### <a name="standalone-os-versions"></a>Versions du système d’exploitation autonome

Les versions de système d’exploitation suivantes sont prises en charge :

<br />

****

Version du système d'exploitation|GCC|GCC High|DoD
:---|:---:|:---:|:---:
Windows 11|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 21H1 et versions ultérieures|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 20H2 (avec [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 10, version 2004 (avec [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-version-2004-end-of-servicing), veuillez effectuer une mise à niveau|![Oui](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-version-2004-end-of-servicing), veuillez effectuer une mise à niveau|![Oui](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-version-2004-end-of-servicing), veuillez effectuer une mise à niveau
Windows 10, version 1909 (avec [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1909-end-of-servicing), veuillez effectuer une mise à niveau|![Oui](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1909-end-of-servicing), veuillez effectuer une mise à niveau|![Oui](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1909-end-of-servicing), veuillez effectuer une mise à niveau
Windows 10, version 1903 (avec [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1903-end-of-servicing), veuillez effectuer une mise à niveau|![Oui](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1903-end-of-servicing), veuillez effectuer une mise à niveau|![Oui](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1903-end-of-servicing), veuillez effectuer une mise à niveau
Windows 10, version 1809 (avec [KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1803-1809-end-of-servicing), veuillez effectuer une mise à niveau|![Oui](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1803-1809-end-of-servicing), veuillez effectuer une mise à niveau|![Oui](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1803-1809-end-of-servicing), veuillez effectuer une mise à niveau
Windows 10, version 1803 (avec [KB4598245](https://support.microsoft.com/help/4598245) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1803-1809-end-of-servicing), veuillez effectuer une mise à niveau|![Oui](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1803-1809-end-of-servicing), veuillez effectuer une mise à niveau|![Oui](images/svg/check-yes.svg) <br /> Remarque : [Déconseillé](/lifecycle/announcements/windows-10-1803-1809-end-of-servicing), veuillez effectuer une mise à niveau
Windows 10, version 1709|![Non.](images/svg/check-no.svg) <br /> Remarque : ne sera pas pris en charge|![Oui](images/svg/check-yes.svg) avec [KB4499147](https://support.microsoft.com/help/4499147) <sup>1</sup> <br /> Remarque : [Déconseillé](/lifecycle/announcements/revised-end-of-service-windows-10-1709), veuillez effectuer une mise à niveau|![Non](images/svg/check-no.svg) <br /> Remarque : ne sera pas pris en charge
Windows 10, version 1703 et antérieure|![Non.](images/svg/check-no.svg) <br /> Remarque : ne sera pas pris en charge|![Non](images/svg/check-no.svg) <br /> Remarque : ne sera pas pris en charge|![Non](images/svg/check-no.svg) <br /> Remarque : ne sera pas pris en charge
Windows Server 2022|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2019 (avec [KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2016 (moderne) <sup>2</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2012 R2 (moderne) <sup>2</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2016 (hérité) <sup>3</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2012 R2 (hérité) <sup>3</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1 (hérité) <sup>3</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 8.1 Entreprise (hérité) <sup>3</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 8 Professionnel (hérité) <sup>3</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 7 SP1 Entreprise (hérité) <sup>3</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows 7 SP1 Professionnel (hérité) <sup>3</sup>|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Linux|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
macOS|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Android|![Oui.](images/svg/check-yes.svg) <br /> |![Oui](images/svg/check-yes.svg) <br /> |![Oui](images/svg/check-yes.svg) <br /> 
iOS|![Oui.](images/svg/check-yes.svg) <br /> |![Oui](images/svg/check-yes.svg) <br /> |![Oui](images/svg/check-yes.svg) <br /> 

**Footnotes**

<sup>1</sup> Le correctif doit être déployé avant l’intégration de l’appareil afin de configurer Defender pour point de terminaison dans l’environnement approprié.

<sup>2</sup> Découvrez la [solution moderne unifiée pour Windows 2016 et 2012 R2](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution). Si vous avez déjà intégré vos serveurs à l’aide de MMA, suivez les instructions fournies dans [Migration de serveur](server-migration.md) pour migrer vers la nouvelle solution.

<sup>3</sup> Lorsque vous utilisez [Microsoft Monitoring Agent](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) , vous devez choisir « Azure US Government » sous « Azure Cloud » si vous utilisez l’Assistant [Installation](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard), ou si vous utilisez une [ligne de commande](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) ou un [script](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) , définissez le paramètre « OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE » sur 1. <br /> La version minimale prise en charge par MMA est 10.20.18029 (mars 2020).

### <a name="os-versions-when-using-microsoft-defender-for-servers"></a>Versions du système d’exploitation lors de l’utilisation de Microsoft Defender pour les serveurs

Les versions de système d’exploitation suivantes sont prises en charge lors de [l’utilisation de Microsoft Defender pour les serveurs](/azure/security-center/security-center-wdatp) :

<br />

****

Version du système d'exploitation|GCC|GCC High|DoD
:---|:---:|:---:|:---:
Windows Server 2022|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2019|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2016|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2012 R2|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1|![Oui.](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)

## <a name="required-connectivity-settings"></a>Paramètres de connectivité requis

Si un proxy ou un pare-feu bloque tout le trafic par défaut et n'autorise le passage que de domaines spécifiques, ajoutez les domaines énumérés dans la feuille téléchargeable à la liste des domaines autorisés.

La feuille de calcul téléchargeable suivante répertorie les services et les URL associées auxquels votre réseau doit être en mesure de se connecter. Vérifiez qu’il n’existe aucune règle de pare-feu ou de filtrage réseau qui refuserait l’accès à ces URL, ou créez une règle *d’autorisation* spécifique pour celles-ci.

|Feuille de calcul de la liste des domaines| Description|
|---|---|
|liste d’URL Microsoft Defender pour point de terminaison pour les clients commerciaux| Feuille de calcul des enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation pour les clients commerciaux. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| liste d’URL Microsoft Defender pour point de terminaison pour Gov/GCC/DoD | Feuille de calcul des enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation pour les clients Gov/GCC/DoD. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Pour plus d’informations, consultez [Configurer les paramètres de proxy d’appareil et de connectivité Internet](configure-proxy-internet.md).

> [!NOTE]
> La feuille de calcul contient également des URL commerciales, veillez à vérifier les onglets « US Gov ».
>
> Lors du filtrage, recherchez les enregistrements étiquetés « US Gov » et votre cloud spécifique sous la colonne geography.

## <a name="api"></a>API

Au lieu des URI publics répertoriés dans notre [documentation sur l’API](apis-intro.md), vous devez utiliser les URI suivants :

<br />

****

|Type de point de terminaison|GCC|GCC High & DoD|
|---|---|---|
|Connexion|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|API Defender pour point de terminaison|`https://api-gcc.securitycenter.microsoft.us`|`https://api-gov.securitycenter.microsoft.us`|

## <a name="feature-parity-with-commercial"></a>Parité des fonctionnalités avec les fonctionnalités commerciales

Les clients Defender pour point de terminaison pour le gouvernement des États-Unis n’ont pas de parité complète avec l’offre commerciale. Bien que notre objectif soit de fournir toutes les fonctionnalités commerciales à nos clients du secteur public américain, certaines fonctionnalités ne sont pas encore disponibles.

Voici les lacunes connues :

<br />

****

|Nom de la fonctionnalité|GCC|GCC High|DoD|
|----|:---:|:---:|:---:|
|Rapports : filtrage de contenu web|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|
|Rapports : Intégrité de l’appareil|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|
|Degré de sécurisation Microsoft|![Oui](images/svg/check-yes.svg) <sup>1</sup>|![Non](images/svg/check-no.svg)|![Non](images/svg/check-no.svg)|  
|Spécialistes des menaces Microsoft|![Non](images/svg/check-no.svg)|![Non](images/svg/check-no.svg)|![Non](images/svg/check-no.svg)|  

**Note**

<sup>1</sup> Bien que microsoft Secure Score soit disponible pour les clients GCC, certaines recommandations de sécurité ne sont pas disponibles.


Voici les fonctionnalités et les lacunes connues pour [Mobile Threat Defense (Microsoft Defender pour point de terminaison sur Android & iOS)](mtd.md) :

|Nom de la fonctionnalité|GCC|GCC High|DoD|
|---|:---:|:---:|:---:|
|Protection web (anti-hameçonnage et indicateurs personnalisés)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|
|Protection contre les programmes malveillants (Android uniquement)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|
|Détection de jailbreak (iOS uniquement)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|
|Accès conditionnel/Lancement conditionnel|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|
|Prise en charge de la gestion des applications mobiles|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|
|Contrôles de confidentialité|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|
|Gestion des vulnérabilités Microsoft Defender (MDVM))|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|![Oui](images/svg/check-yes.svg)|
