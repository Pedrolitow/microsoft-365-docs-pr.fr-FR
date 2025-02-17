---
title: Microsoft Defender pour point de terminaison
description: Microsoft Defender pour point de terminaison est une plateforme de sécurité de point de terminaison d’entreprise qui permet de se défendre contre les menaces persistantes avancées.
keywords: introduction à Microsoft Defender pour point de terminaison, présentation de Microsoft Defender pour point de terminaison, cybersécurité, menace persistante avancée, sécurité d’entreprise, capteur de comportement de l’ordinateur, sécurité cloud, analytique, renseignement sur les menaces, réduction de la surface d’attaque, protection nouvelle génération, investigation et correction automatisée, experts en menaces Microsoft, degré de sécurisation, repérage avancé, Microsoft 365 Defender, repérage de cybermenaces
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: high
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.custom: intro-overview
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 40450ed20daaa4c3520386aad7d6a416b8b84889
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68234033"
---
# <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender pour point de terminaison est une plate-forme de sécurité de point de terminaison d’entreprise conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées.

> [!TIP]
> Microsoft Defender pour point de terminaison est disponible en deux plans : Defender pour point de terminaison Plan 1 et Plan 2. Un nouveau module complémentaire de Gestion des vulnérabilités de Microsoft Defender est désormais disponible pour le plan 2.
>
> Pour plus d’informations sur les fonctionnalités et possibilités incluses dans chaque plan, y compris le nouveau module complémentaire de Gestion des vulnérabilités Defender, consultez [Comparer les plans de Microsoft Defender pour de points de terminaison](defender-endpoint-plan-1-2.md).

<p><p>

Regardez la vidéo suivante pour en savoir plus sur Defender pour point de terminaison :

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wDob]

Microsoft Defender pour point de terminaison utilise la combinaison de technologies suivante intégrée à Windows 10 et au service cloud puissant de Microsoft :

- **Capteurs de point de terminaison**: intégrés dans Windows 10, ces capteurs collectent et traitent des signaux de comportement par le système d’exploitation et envoient les données de ce capteur à votre instance privée, isolée et Cloud de Microsoft Defender pour point de terminaison.

- **Analyse de sécurité cloud** : Grâce à l'exploitation des données du Big Data, de l’apprentissage sur appareil et des investigations approfondies uniques de l’écosystème Microsoft Windows, des produits cloud d’entreprise (tels qu’Office 365) et des ressources en ligne, les signaux comportementaux sont convertis en informations, détections et réponses recommandées aux menaces avancées.

- **Intelligence des menaces** : générée par les agents de repérage, les équipes de sécurité Microsoft et augmentée par l’intelligence des menaces fournie par les partenaires, l’intelligence des menaces permet à Microsoft Defender pour point de terminaison d’identifier les outils, les techniques et les procédures de l’agresseur, et de générer des alertes lorsqu’il est observé dans les données du capteur collectées.

<center><h2>Microsoft Defender pour point de terminaison</center></h2>
<table>
<tr>
<td><a href="#tvm"><center><img src="images/logo-mdvm.png" alt="Vulnerability Management"> <br><b>Gestion des vulnérabilités Core Defender</b></center></a></td>
<td><a href="#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>Réduction de la surface d’attaque</b></center></a></td>
<td><center><a href="#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>Protection de nouvelle génération</b></a></center></td>
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

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vnC4?rel=0]

> [!TIP]
> - Découvrez les dernières améliorations apportées à Defender pour point de terminaison : [Nouveautés de Microsoft Defender pour point de terminaison](whats-new-in-microsoft-defender-endpoint.md).
> - Microsoft Defender pour point de terminaison a démontré les fonctionnalités de détection optique et de détection dans la dernière version d’évaluation de MITRE. Lire : [Informations tirées de l’évaluation de MITRE basée sur ATT&CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).


> [!IMPORTANT]
> Les fonctionnalités des plates-formes non Windows peuvent être différentes de celles de Windows. Pour plus d’informations sur les fonctionnalités disponibles pour les plates-formes non Windows, consultez [Microsoft Defender pour point de terminaison pour les plates-formes non Windows](/microsoft-365/security/defender-endpoint/non-windows).

<a name="tvm"></a>

**[Gestion des vulnérabilités Defender](../defender-vulnerability-management/defender-vulnerability-management.md)**

La gestion des menaces et vulnérabilités de base intégrées utilisent une approche moderne basée sur les risques pour la découverte, l’évaluation, la hiérarchisation et la correction des vulnérabilités de point de terminaison et des erreurs de configuration. Pour améliorer davantage votre capacité à évaluer votre posture de sécurité et à réduire les risques, un nouveau module complémentaire de Gestion des vulnérabilités Defender pour le plan 2 est disponible.

Pour plus d’informations sur les différentes fonctionnalités de gestion des vulnérabilités disponibles, consultez [Comparer les offres de gestion des vulnérabilités Microsoft Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md).

<a name="asr"></a>

**[Réduction de la surface d’attaque](overview-attack-surface-reduction.md)**

Le jeu de fonctionnalités de réduction de surface d’attaque fournit la première ligne de défense dans la pile. En veillant à ce que les paramètres de configuration soient correctement définis et à ce que les techniques d’atténuation des risques soient appliquées, ces fonctionnalités résistent aux attaques et à l’exploitation. Ce jeu de fonctionnalités inclut également la [protection réseau](network-protection.md) et la [protection web](web-protection-overview.md), qui régulent l’accès aux adresses IP, domaines et URL malveillants.

<a name="ngp"></a>

**[Protection de nouvelle génération](next-generation-protection.md)**

Pour renforcer davantage le périmètre de sécurité de votre réseau, Microsoft Defender pour point de terminaison fait appel à une protection nouvelle génération conçue pour intercepter tous les types de menaces émergentes.

<a name="edr"></a>

**[Détection et réponse des points de terminaison](overview-endpoint-detection-response.md)**

Les fonctionnalités de détection et de réponse au point de terminaison sont mises en place pour détecter, examiner et répondre aux menaces avancées susceptibles d’avoir franchi les deux premiers piliers de sécurité. Le [repérage avancé](advanced-hunting-overview.md) fournit un outil de recherche de menace par requête qui vous permet de détecter les brèches de manière proactive et de créer des détections personnalisées.

<a name="ai"></a>

**[Examen et correction automatisés](automated-investigations.md)**

Outre la possibilité de répondre rapidement aux attaques avancées, Microsoft Defender pour point de terminaison propose des fonctionnalités d’investigation et de correction automatiques qui permettent de réduire le volume des alertes en quelques minutes à grande échelle.

<a name="ss"></a>

**[Niveau de sécurité Microsoft pour les appareils](tvm-microsoft-secure-score-devices.md)**

Defender pour point de terminaison inclut le Niveau de sécurité Microsoft pour les appareils pour vous aider à évaluer de manière dynamique l’état de sécurité de votre réseau d’entreprise, à identifier les systèmes non protégés et à prendre les mesures recommandées pour améliorer la sécurité globale de votre organisation.

<a name="mte"></a>

**[Spécialistes des menaces Microsoft](microsoft-threat-experts.md)**

Le nouveau service de chasse de menaces gérées par Microsoft Defender pour point de terminaison fournit une chasse et des priorités proactives, ainsi que des informations supplémentaires sur les centres d’opérations de sécurité (SOCs), qui permettent d’identifier et de répartir rapidement et précisément.

> [!IMPORTANT]
> Les clients Defender pour point de terminaison doivent demander le service de repérage géré par Microsoft Threat Experts pour recevoir des notifications d’attaque ciblées proactives et collaborer avec des experts à la demande. Experts à la demande est un service d’extension. Les notifications d’attaques ciblées sont toujours incluses une fois que vous êtes accepté dans le service géré de repérage des menaces Spécialistes des menaces Microsoft.
>
> Si vous n’êtes pas encore inscrit et que vous aimeriez profiter de ses avantages, accédez à **Paramètres** \> **Général** \> **Fonctionnalités avancées** \> **Spécialistes des menaces Microsoft** pour vous inscrire. Une fois accepté, vous bénéficiez des avantages des notifications d’attaques ciblées et vous débutez un essai de 90 jours d’Experts à la demande. Contactez votre représentant Microsoft pour obtenir un abonnement complet à Experts à la demande.

<a name="apis"></a>

**[Configuration et administration centralisées, API](management-apis.md)**

Intégrez Microsoft Defender pour point de terminaison à vos flux de travail existants.

<a name="mtp"></a>

**[Intégration avec les solutions Microsoft.](threat-protection-integration.md)**

Defender pour point de terminaison s’intègre directement aux différentes solutions Microsoft, notamment :

- Microsoft Defender pour le cloud
- Microsoft Sentinel
- Intune
- Microsoft Defender for Cloud Apps
- Microsoft Defender pour l’identité
- Microsoft Defender pour Office
- Skype Entreprise

**[Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)**

Avec Microsoft 365 Defender, Defender pour point de terminaison, et diverses solutions de sécurité Microsoft, forment une suite de défense d’entreprise unifiée pré et post-violation qui s’intègre en mode natif entre les points de terminaison, les identités, les e-mails et les applications pour détecter, empêcher, examiner et répondre automatiquement aux attaques sophistiquées.


## <a name="training-for-security-analysts"></a>Formation pour les analystes de sécurité

Avec ce parcours d'apprentissage de Microsoft Learn, vous pouvez comprendre Defender for Endpoint et comment il peut aider à prévenir, détecter, enquêter et répondre aux menaces sur les points d'extrémité de votre organisation - vos appareils et systèmes.

|Formation :|Détecter les cyberattaques et y répondre avec Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender de formation.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Defender pour point de terminaison est une solution de sécurité de point de terminaison qui offre la gestion des vulnérabilités, la protection des points de terminaison, la détection et la réponse des points de terminaison, la défense contre les menaces mobiles et les services managés dans une plateforme unifiée unique.<p> 2 h 25 min - Learning chemin d’accès - 9 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/training/paths/defender-endpoint-fundamentals/)
