---
title: Microsoft Defender pour point de terminaison
description: Microsoft Defender pour point de terminaison est une plateforme de sécurité de point de terminaison d’entreprise qui permet de se défendre contre les menaces avancées persistantes.
keywords: introduction à Microsoft Defender pour point de terminaison, introduction à Microsoft Defender pour le point de terminaison, cybersécurité, menace avancée persistante, sécurité d’entreprise, capteur de comportement ordinateur, sécurité cloud, analyse, intelligence des menaces, réduction de la surface d’attaque, protection nouvelle génération, investigation et correction automatisées, experts microsoft en matière de menaces, score de sécurité, recherche avancée, Microsoft 365 Defender, recherche de cybermenace
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
ms.openlocfilehash: 23a9b99a71d700bdeddb3398c592eeb778ceef23
ms.sourcegitcommit: 337e8d8a2fee112d799edd8a0e04b3a2f124f900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "52879263"
---
# <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

> Pour plus d’informations sur Windows 10 Entreprise et les fonctionnalités de la [Windows 10 Entreprise Edition, consultez](https://www.microsoft.com/WindowsForBusiness/buy)la Windows 10 Entreprise edition.

Microsoft Defender pour point de terminaison est une plateforme de sécurité de point de terminaison d’entreprise conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées.
<p></p>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wDob]

Defender pour le point de terminaison utilise la combinaison de technologie suivante intégrée à Windows 10 et au service cloud robuste de Microsoft :

-   Capteurs comportementaux de point de terminaison : incorporés dans Windows 10, ces capteurs collectent et traitéent les signaux comportementaux du système d’exploitation et envoient ces données de capteur à votre instance privée, isolée et cloud de Microsoft Defender pour point de terminaison.


-   Analyse de la sécurité cloud : tirant parti du Big Data, de l’apprentissage des appareils et de l’optique Microsoft unique dans l’écosystème Windows, des produits cloud d’entreprise (tels que Office 365) et des ressources en ligne, les signaux comportementaux sont convertis en analyses, détections et réponses recommandées aux menaces avancées.

-   Intelligence contre les menaces : générée par les chercheurs de Microsoft, les équipes de sécurité et renforcée par l’intelligence contre les menaces fournie par les partenaires, l’intelligence des menaces permet à Defender for Endpoint d’identifier les outils, techniques et procédures de l’attaquant et de générer des alertes lorsqu’elles sont observées dans les données de capteur collectées.

<center><h2>Microsoft Defender pour point de terminaison</center></h2>
<table>
<tr>
<td><a href="#tvm"><center><img src="images/TVM_icon.png" alt="Threat & Vulnerability Management"> <br><b>Gestion des & des menaces</b></center></a></td>
<td><a href="#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>Réduction de la surface d’attaque</b></center></a></td>
<td><center><a href="#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>Protection nouvelle génération</b></a></center></td>
<td><center><a href="#edr"><img src="images/edr-icon.png" alt="Endpoint detection and response"><br> <b>Détection et réponse des points de terminaison</b></a></center></td>
<td><center><a href="#ai"><img src="images/air-icon.png" alt="Automated investigation and remediation"><br> <b>Examen et correction automatisés</b></a></center></td>
<td><center><a href="#mte"><img src="images/mte-icon.png" alt="Microsoft Threat Experts"><br> <b>Spécialistes des menaces Microsoft</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="#apis"><center><b>Configuration et administration centralisées, API</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="#mtp"><center><b>Microsoft 365 Defender</a></center></b></td>
</tr>
</table>
<br>

<p></p>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vnC4?rel=0] 

> [!TIP]
> - Découvrez les dernières améliorations de Defender pour point de terminaison : nouveautés de [Microsoft Defender pour point de terminaison.](whats-new-in-microsoft-defender-atp.md)
> - Microsoft Defender pour le point de terminaison a démontré les fonctionnalités d’optique et de détection de pointe du secteur dans l’évaluation MITRE récente. Read: [Insights from the MITRE ATT&CK-based evaluation](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

<a name="tvm"></a>

**[Gestion des & des menaces](next-gen-threat-and-vuln-mgt.md)**<br>
Cette fonctionnalité intégrée utilise une approche basée sur les risques qui modifie le jeu pour la découverte, la hiér doncisation et la correction des vulnérabilités et des mauvaises configurations des points de terminaison. 

<a name="asr"></a>

**[Réduction de la surface d’attaque](overview-attack-surface-reduction.md)**<br>
L’ensemble de fonctionnalités de réduction de la surface d’attaque fournit la première ligne de défense dans la pile. En s’assurant que les paramètres de configuration sont correctement définies et que des techniques d’atténuation des attaques sont appliquées, les fonctionnalités résistant aux attaques et à l’exploitation. Cet ensemble de fonctionnalités inclut également la [protection](network-protection.md) réseau et [la protection web,](web-protection-overview.md)qui régulent l’accès aux adresses IP, domaines et URL malveillants. 

<a name="ngp"></a>

**[Protection de nouvelle génération](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)**<br>
Pour renforcer davantage le périmètre de sécurité de votre réseau, Microsoft Defender pour Endpoint utilise une protection nouvelle génération conçue pour capturer tous les types de menaces émergentes.

<a name="edr"></a>

**[Détection et réponse du point de terminaison](overview-endpoint-detection-response.md)**<br>
Des fonctionnalités de détection et de réponse de point de terminaison sont mises en place pour détecter, examiner et répondre aux menaces avancées qui ont peut-être passé les deux premiers piliers de sécurité. [Le repérage avancé](advanced-hunting-overview.md) fournit un outil de repérage de menaces basé sur une requête qui vous permet de rechercher de manière proactive les violations et de créer des détections personnalisées.

<a name="ai"></a>

**[Examen et correction automatisés](automated-investigations.md)**<br>
En plus de pouvoir répondre rapidement aux attaques avancées, Microsoft Defender pour point de terminaison offre des fonctionnalités d’examen et de correction automatiques qui permettent de réduire le volume d’alertes en minutes à l’échelle. 

<a name="ss"></a>

**[Niveau de sécurité Microsoft pour les appareils](tvm-microsoft-secure-score-devices.md)**<br>

Defender pour le point de terminaison inclut le Niveau de sécurité Microsoft pour les appareils pour vous aider à évaluer dynamiquement l’état de sécurité de votre réseau d’entreprise, à identifier les systèmes non protégés et à prendre les mesures recommandées pour améliorer la sécurité globale de votre organisation.

<a name="mte"></a>

**[Spécialistes des menaces Microsoft](microsoft-threat-experts.md)**<br>
Le nouveau service de recherche de menaces gérées de Microsoft Defender pour les points de terminaison fournit une recherche proactive, la hiér doncisation, ainsi que des informations et un contexte supplémentaires qui permettent aux centres d’opérations de sécurité (SOC) d’identifier et de répondre aux menaces rapidement et avec précision.

>[!IMPORTANT]
>Les clients Defender for Endpoint doivent demander au service Spécialistes des menaces Microsoft de recherche de menace gérée pour obtenir des notifications d’attaques ciblées proactives et collaborer avec des experts à la demande. Experts à la demande est un service de modules. Les notifications d’attaque ciblée sont toujours incluses une fois que vous avez été accepté dans Spécialistes des menaces Microsoft service de recherche de menaces gérées.<p>
><p>Si vous n’êtes pas encore inscrit et que <b></b> vous souhaitez profiter de ses avantages, Paramètres > <b>fonctionnalités</b> > <b></b> générales avancées > <b>Spécialistes des menaces Microsoft</b> à appliquer. Une fois accepté, vous bénéficiez des avantages des notifications d’attaques ciblées et démarrez une version d’essai de 90 jours d’Experts à la demande. Contactez votre représentant Microsoft pour obtenir un abonnement Experts à la demande complet.

<a name="apis"></a>

**[Configuration et administration centralisées, API](management-apis.md)**<br>
Intégrez Microsoft Defender for Endpoint à vos flux de travail existants.

<a name="mtp"></a>

**[Intégration aux solutions Microsoft](threat-protection-integration.md)** <br>
Defender pour le point de terminaison s’intègre directement à différentes solutions Microsoft, notamment :
- Azure Defender
- Azure Sentinel
- Intune
- Microsoft Cloud App Security
- Microsoft Defender pour l’identité
- Microsoft Defender pour Office
- Skype Entreprise

**[Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-threat-protection)**<br>
Avec Microsoft 365 Defender, Defender pour le point de terminaison et diverses solutions de sécurité Microsoft forment une suite de défense d’entreprise unifiée avant et après la violation qui s’intègre en mode natif à travers le point de terminaison, l’identité, le courrier électronique et les applications pour détecter, empêcher, examiner et répondre automatiquement aux attaques sophistiquées.


## <a name="related-topic"></a>Rubrique connexe
[Microsoft Defender pour point de terminaison permet de détecter les menaces sophistiquées](https://www.microsoft.com/itshowcase/microsoft-defender-atps-antivirus-capabilities-boost-malware-protection)
