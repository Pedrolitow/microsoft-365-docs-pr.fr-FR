---
title: Microsoft Defender 365 pour les clients du gouvernement des États-Unis
description: En savoir plus sur les Microsoft 365 Defender pour les clients du gouvernement des États-Unis et les fonctionnalités disponibles
keywords: gouvernement, gcc, élevé, exigences, capacités, defender, Microsoft 365 Defender, xdr, dod
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
ms.openlocfilehash: 53fc78159580a27a8af04009f4e5ecd5b18bc4e8
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057580"
---
# <a name="microsoft-365-defender-for-us-government-customers"></a>Microsoft Defender 365 pour les clients du gouvernement des États-Unis

**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender pour les clients du gouvernement des États-Unis, intégrés à l’environnement Azure US Government, utilisent les mêmes technologies sous-jacentes que Microsoft 365 Defender dans Azure Commercial.

Cette offre est disponible pour les clients Cloud de la communauté du secteur public, Cloud de la communauté du secteur public High et DoD et est basée sur la même prévention, détection, investigation et correction que la version commerciale. Toutefois, il existe certaines différences dans la disponibilité des fonctionnalités de cette offre.

> [!NOTE]
> Si vous êtes un client Cloud de la communauté du secteur public utilisant Defender pour le cloud Apps, Defender pour point de terminaison ou Defender pour Identity dans Commercial, vous devez transférer ces services vers leurs versions Cloud de la communauté du secteur public pour être éligible Microsoft 365 Defender Cloud de la communauté du secteur public.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Microsoft 365 Defender pour les clients du gouvernement des États-Unis nécessite l’une des offres de licence en volume Microsoft suivantes :

### <a name="desktop-licensing"></a>Licences de bureau

<br />

****

|GCC|GCC High|DoD|
|---|---|---|
|Microsoft 365 Cloud de la communauté du secteur public G5|Microsoft 365 E5 pour Cloud de la communauté du secteur public High|Microsoft 365 G5 pour DOD|
|Microsoft 365 Cloud de la communauté du secteur public de sécurité G5|Microsoft 365 G5 Security pour Cloud de la communauté du secteur public High|Microsoft 365 G5 Security for DOD|
|Enterprise Mobility + Security Cloud de la communauté du secteur public G5|Enterprise Mobility + Security E5 pour Cloud de la communauté du secteur public High|Enterprise Mobility + Security E5 pour DOD|
|Office 365 Cloud de la communauté du secteur public G5|Office 365 E5 pour Cloud de la communauté du secteur public Élevé|Office 365 E5 pour DOD|
|Microsoft Defender for Cloud Apps Cloud de la communauté du secteur public|Microsoft Defender for Cloud Apps pour Cloud de la communauté du secteur public élevé|Microsoft Defender for Cloud Apps pour DOD|
|Microsoft Defender pour point de terminaison - Cloud de la communauté du secteur public|Microsoft Defender pour point de terminaison pour Cloud de la communauté du secteur public High|Microsoft Defender pour point de terminaison pour DOD|
|Microsoft Defender pour Identity - Cloud de la communauté du secteur public|Microsoft Defender pour Identity pour Cloud de la communauté du secteur public High|Microsoft Defender pour Identity pour DOD|
|Microsoft Defender pour Office 365 (Plan 2) Cloud de la communauté du secteur public|Microsoft Defender pour Office 365 (Plan 2) pour Cloud de la communauté du secteur public élevé|Microsoft Defender pour Office 365 (Plan 2) pour dod|
|Windows 10 Entreprise Cloud de la communauté du secteur public E5|Windows 10 Entreprise E5 pour Cloud de la communauté du secteur public High|Windows 10 Entreprise E5 pour DOD|
|

### <a name="server-licensing"></a>Gestion des licences serveur

<br />

****

|GCC|GCC High|DoD|
|---|---|---|
|Microsoft Defender pour point de terminaison Server Cloud de la communauté du secteur public|serveur Microsoft Defender pour point de terminaison pour Cloud de la communauté du secteur public élevé|serveur Microsoft Defender pour point de terminaison pour DOD|
|Microsoft Defender pour serveurs|Microsoft Defender pour serveurs - Gouvernement|Microsoft Defender pour serveurs - Gouvernement|
|

## <a name="portal-urls"></a>URL du portail

Voici les URL du portail Microsoft 365 Defender pour les clients du gouvernement des États-Unis :

<br />

****

|Type de client|URL du portail|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC High|En cours de déploiement|
|DoD|En cours de déploiement|
|
> [!NOTE]
> Si vous êtes un client Cloud de la communauté du secteur public et que vous êtes en train de passer de Microsoft Defender pour point de terminaison commercial à Cloud de la communauté du secteur public, utilisez-le https://transition.security.microsoft.com pour accéder à votre Microsoft Defender pour point de terminaison données commerciales.

## <a name="api"></a>API

Au lieu des URI publics répertoriés dans la documentation de notre [API](api-overview.md), vous devez utiliser les URI suivants :

<br />

****

|Type de point de terminaison|GCC|Cloud de la communauté du secteur public DoD de & élevé|
|---|---|---|
|Connexion|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|API Microsoft 365 Defender|`https://api-gcc.security.microsoft.us`|`https://api-gov.security.microsoft.us`|
|

## <a name="feature-parity-with-commercial"></a>Parité des fonctionnalités avec commercial

Microsoft 365 Defender pour les clients du gouvernement des États-Unis n’ont pas une parité complète avec l’offre commerciale. Bien que notre objectif soit de fournir toutes les fonctionnalités commerciales à nos clients du gouvernement des États-Unis, certaines fonctionnalités ne sont pas encore disponibles que nous souhaitons mettre en évidence.

Voici les lacunes connues :

<br />

****

|Nom de la fonctionnalité|GCC|GCC High|DoD|
|---|:---:|:---:|:---:|
|Intégrations : Microsoft Sentinel (incidents & données brutes)|![Oui](../defender-endpoint/images/svg/check-yes.svg) En préversion en public|![Oui](../defender-endpoint/images/svg/check-yes.svg) En préversion en public|![Oui](../defender-endpoint/images/svg/check-yes.svg) En préversion en public|
|Spécialistes des menaces Microsoft|![Non](../defender-endpoint/images/svg/check-no.svg) Sur le backlog d’ingénierie|![Non](../defender-endpoint/images/svg/check-no.svg) Sur le backlog d’ingénierie|![Non](../defender-endpoint/images/svg/check-no.svg) Sur le backlog d’ingénierie|

Pour obtenir la liste détaillée des tables d’API Event Streaming, consultez [Microsoft 365 Defender types d’événements de streaming pris en charge dans l’API Event Streaming](supported-event-types.md).

## <a name="more-details"></a>Plus de détails

Pour plus d’informations, consultez les pages US Gov des charges de travail individuelles :

- [Microsoft Defender for Cloud Apps](/enterprise-mobility-security/solutions/ems-cloud-app-security-govt-service-description).
- [Microsoft Defender pour Identity](/enterprise-mobility-security/solutions/ems-mdi-govt-service-description).
- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/gov).
