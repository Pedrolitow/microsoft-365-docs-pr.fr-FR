---
title: Microsoft 365 Defender pour les clients du gouvernement américain
description: En savoir plus sur les Microsoft 365 Defender pour les clients du gouvernement des États-Unis et les fonctionnalités disponibles
keywords: government, gcc, high, requirements, capabilities, defender, Microsoft 365 Defender, xdr, dod
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
ms.technology: m365d
ms.openlocfilehash: 3e8f6e523a5483de99beb0af7d01ab96951b7a3e
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61375072"
---
# <a name="microsoft-365-defender-for-us-government-customers"></a>Microsoft 365 Defender pour les clients du gouvernement américain

**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender pour les clients du gouvernement américain, intégrés dans l’environnement Azure US Government, utilisent les mêmes technologies sous-jacentes que Microsoft 365 Defender dans Azure Commercial.

Cette offre est disponible pour les clients Cloud de la communauté du secteur public, Cloud de la communauté du secteur public High et DoD et est basée sur les mêmes prévention, détection, examen et correction que la version commerciale. Toutefois, il existe certaines différences dans la disponibilité des fonctionnalités de cette offre.

> [!NOTE]
> Si vous êtes un client Cloud de la communauté du secteur public utilisant Defender pour les applications cloud, Defender pour le point de terminaison ou Defender pour l’identité dans commercial, vous devez faire passer ces services vers leurs versions Cloud de la communauté du secteur public pour être éligible pour Microsoft 365 Defender Cloud de la communauté du secteur public.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Microsoft 365 Defender pour les clients du gouvernement des États-Unis nécessite l’une des offres de licence en volume Microsoft suivantes :

### <a name="desktop-licensing"></a>Licences de bureau

<br />

****

|GCC|GCC High|DoD|
|---|---|---|
|Microsoft 365 Cloud de la communauté du secteur public G5|Microsoft 365 E5 pour Cloud de la communauté du secteur public Élevé|Microsoft 365 G5 pour DOD|
|Microsoft 365 sécurité G5 Cloud de la communauté du secteur public|Microsoft 365 sécurité G5 pour Cloud de la communauté du secteur public élevé|Microsoft 365 G5 pour DOD|
|Enterprise Mobility + Security G5 Cloud de la communauté du secteur public|Enterprise Mobility + Security E5 pour Cloud de la communauté du secteur public élevé|Enterprise Mobility + Security E5 pour DOD|
|Office 365 G5 Cloud de la communauté du secteur public|Office 365 E5 for Cloud de la communauté du secteur public High|Office 365 E5 pour DOD|
|Microsoft Defender pour les applications cloud Cloud de la communauté du secteur public|Microsoft Defender for Cloud Apps for Cloud de la communauté du secteur public High|Microsoft Defender pour les applications cloud pour DOD|
|Microsoft Defender pour le point de terminaison - Cloud de la communauté du secteur public|Microsoft Defender for Endpoint for Cloud de la communauté du secteur public High|Microsoft Defender pour point de terminaison pour DOD|
|Microsoft Defender pour l’identité - Cloud de la communauté du secteur public|Microsoft Defender for Identity for Cloud de la communauté du secteur public High|Microsoft Defender for Identity for DOD|
|Microsoft Defender for Office 365 (Plan 2) Cloud de la communauté du secteur public|Microsoft Defender for Office 365 (Plan 2) for Cloud de la communauté du secteur public High|Microsoft Defender pour Office 365 (Plan 2) pour DOD|
|Windows 10 Entreprise E5 Cloud de la communauté du secteur public|Windows 10 Entreprise E5 pour Cloud de la communauté du secteur public élevé|Windows 10 Entreprise E5 pour DOD|
|

### <a name="server-licensing"></a>Gestion des licences de serveur

<br />

****

|GCC|GCC High|DoD|
|---|---|---|
|Microsoft Defender pour Endpoint Server Cloud de la communauté du secteur public|Microsoft Defender for Endpoint Server for Cloud de la communauté du secteur public High|Microsoft Defender pour Endpoint Server pour DOD|
|Microsoft Defender pour les serveurs|Microsoft Defender pour les serveurs - Gouvernement|Microsoft Defender pour les serveurs - Gouvernement|
|

## <a name="portal-urls"></a>URL du portail

Les URL du portail Microsoft 365 Defender pour les clients du gouvernement des États-Unis sont les suivantes :

<br />

****

|Type de client|URL du portail|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC High|En cours de déploiement|
|DoD|En cours de déploiement|
|
> [!NOTE]
> Si vous êtes un client Cloud de la communauté du secteur public et que vous êtes en train de passer de Microsoft Defender for Endpoint commercial à Cloud de la communauté du secteur public, utilisez cette procédure pour accéder à vos données commerciales https://transition.security.microsoft.com Microsoft Defender for Endpoint.

## <a name="api"></a>API

Au lieu des URIs publics répertoriés dans la documentation de notre [API,](api-overview.md)vous devez utiliser les URIs suivants :

<br />

****

|Type de point de terminaison|GCC|Cloud de la communauté du secteur public DoD & haut niveau|
|---|---|---|
|Connexion|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|MICROSOFT 365 DEFENDER API|`https://api-gcc.security.microsoft.us`|`https://api-gov.security.microsoft.us`|
|

## <a name="feature-parity-with-commercial"></a>Parité des fonctionnalités avec commercial

Microsoft 365 Defender pour les clients du gouvernement américain n’a pas une parité complète avec l’offre commerciale. Bien que notre objectif soit de fournir toutes les fonctionnalités commerciales à nos clients du gouvernement des États-Unis, certaines fonctionnalités ne sont pas encore disponibles que nous voulons mettre en évidence.

Voici les lacunes connues :

<br />

****

|Nom de la fonctionnalité|GCC|GCC High|DoD|
|---|:---:|:---:|:---:|
|Intégrations : Microsoft Sentinel (incidents & données brutes)|![Oui](../defender-endpoint/images/svg/check-yes.svg)|![Oui](../defender-endpoint/images/svg/check-yes.svg) En prévisualisation privée|![Oui](../defender-endpoint/images/svg/check-yes.svg) En prévisualisation privée|
|Spécialistes des menaces Microsoft|![Non](../defender-endpoint/images/svg/check-no.svg) On engineering backlog|![Non](../defender-endpoint/images/svg/check-no.svg) On engineering backlog|![Non](../defender-endpoint/images/svg/check-no.svg) On engineering backlog|

## <a name="more-details"></a>Plus de détails

Pour plus d’informations, consultez les pages de charges de travail individuelles us Gov :
- [Microsoft Defender pour les applications cloud.](/enterprise-mobility-security/solutions/ems-cloud-app-security-govt-service-description)
- [Microsoft Defender pour l’identité](/enterprise-mobility-security/solutions/ems-mdi-govt-service-description).
- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/gov).
