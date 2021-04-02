---
title: Comprendre la section du rapport d’analyste dans l’analyse des menaces
ms.reviewer: ''
description: Découvrez la section du rapport d’analyste de chaque rapport d’analyse des menaces. Comprendre comment il fournit des informations sur les menaces, les atténuations, les détections, les requêtes de repérage avancé, etc.
keywords: rapport d’analyste, analyse des menaces, détections, requêtes de repérage avancé, atténuations,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f916137be71dffeaed7e3718286032a17c9f8e04
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51498480"
---
# <a name="understand-the-analyst-report-in-threat-analytics"></a>Comprendre le rapport d’analyste dans l’analyse des menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

> Vous voulez essayer Microsoft 365 Defender ? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).
>

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Chaque [rapport d’analyse des](threat-analytics.md) menaces inclut des sections dynamiques et une section écrite complète appelée rapport _d’analyste._ Pour accéder à cette section, ouvrez le rapport sur la menace de suivi et sélectionnez **l’onglet Rapport d’analyste.**

![Image de la section du rapport d’analyste d’un rapport d’analyse des menaces](../../media/threat-analytics/ta_analystreport_mtp.png)

_Section Rapport d’analyste d’un rapport d’analyse des menaces_

## <a name="scan-the-analyst-report"></a>Analyser le rapport d’analyste 
Chaque section du rapport d’analyste est conçue pour fournir des informations actionnables. Bien que les rapports varient, la plupart des rapports incluent les sections décrites dans le tableau suivant.

| Section Rapport | Description |
|--|--|
| Résumé exécutif | Vue d’ensemble de la menace, y compris la première fois qu’elle a été vue, ses motivations, les événements notables, les cibles principales et des outils et techniques distincts. Vous pouvez utiliser ces informations pour évaluer plus en détail comment hiérarchiser la menace dans le contexte de votre secteur, de votre emplacement géographique et de votre réseau. |
| Analyse | Informations techniques sur les menaces, y compris les détails d’une attaque et la façon dont les attaquants peuvent utiliser une nouvelle technique ou une nouvelle surface d’attaque | 
| Techniques MITRE ATT&CK observées | Comment les techniques observées sont m maprées à l’infrastructure d&[ATT MITRE](https://attack.mitre.org/) | 
| [Atténuations](#apply-additional-mitigations) | Recommandations qui peuvent arrêter ou réduire l’impact de la menace. Cette section inclut également les atténuations qui ne sont pas suivis dynamiquement dans le cadre du rapport d’analyse des menaces. |
| [Détails de la détection](#understand-how-each-threat-can-be-detected) | Détections spécifiques et génériques fournies par les solutions de sécurité Microsoft qui peuvent faire surface de l’activité ou des composants associés à la menace. | 
| [Repérage avancé](#find-subtle-threat-artifacts-using-advanced-hunting) | [Requêtes de recherche avancées pour](advanced-hunting-overview.md) identifier de manière proactive l’activité potentielle de menace. La plupart des requêtes sont fournies pour compléter les détections, en particulier pour localiser des composants ou des comportements potentiellement malveillants qui n’ont pas pu être évalués dynamiquement comme malveillants. | 
| Références | Publications Microsoft et tierces référencés par les analystes lors de la création du rapport. Le contenu de l’analyse des menaces est basé sur des données validées par des chercheurs Microsoft. Les informations provenant de sources tierces accessibles au public sont clairement identifiées en tant que telles. | 
| Journal des modifications | L’heure de publication du rapport et les modifications importantes apportées au rapport. |

## <a name="apply-additional-mitigations"></a>Appliquer des atténuations supplémentaires
L’analyse des menaces suit dynamiquement [l’état des mises à jour de sécurité et des configurations sécurisées.](threat-analytics.md#mitigations-review-list-of-mitigations-and-the-status-of-your-devices) Ces informations sont disponibles sous la mesure des graphiques et des tableaux de **l’onglet Atténuations.**

En plus de ces atténuations suivies, le rapport d’analyste traite également des atténuations qui ne sont _pas_ surveillées dynamiquement. Voici quelques exemples d’atténuations importantes qui ne sont pas suivis dynamiquement :

- Bloquer les e-mails avec _des pièces jointes .lnk_ ou d’autres types de fichiers suspects
- Randomiser les mots de passe d’administrateur local
- Informer les utilisateurs finaux sur le hameçonnage et d’autres vecteurs de menace
- Activer des règles de [réduction de la surface d’attaque spécifiques](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction)

Bien que vous pouvez utiliser l’onglet **Atténuations** pour évaluer votre posture de sécurité par rapport à une menace, ces recommandations vous permet de prendre des mesures supplémentaires pour améliorer votre posture de sécurité. Lisez attentivement toutes les instructions d’atténuation du rapport d’analyste et appliquez-les dès que possible.

## <a name="understand-how-each-threat-can-be-detected"></a>Comprendre comment chaque menace peut être détectée
Le rapport d’analyste fournit également les détections à partir de Microsoft Defender pour les fonctionnalités antivirus de point de terminaison et de détection et réponse de _point_ de terminaison (EDR).

### <a name="antivirus-detections"></a>Détections antivirus
Ces détections sont disponibles sur les appareils où [l’Antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) est allumé. Lorsque ces détections se produisent sur des appareils qui ont été intégrés à Microsoft Defender pour endpoint, elles déclenchent également des alertes qui allument les graphiques dans le rapport.

>[!NOTE]
>Le rapport d’analyste répertorie également les **détections génériques** qui peuvent identifier un large éventail de menaces, en plus des composants ou comportements spécifiques à la menace de suivi. Ces détections génériques ne sont pas reflétées dans les graphiques.

### <a name="endpoint-detection-and-response-edr-alerts"></a>Alertes de détection et de réponse des points de terminaison (EDR)
Les alertes EDR sont élevées pour les [appareils intégrés à Microsoft Defender pour le point de terminaison.](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure) Ces alertes s’appuient généralement sur les signaux de sécurité collectés par le capteur Microsoft Defender for Endpoint et d’autres fonctionnalités de point de terminaison, telles que les antivirus, la protection réseau, la protection contre la falsification, qui servent de sources de signal puissantes.

À l’exemple de la liste des détections antivirus, certaines alertes EDR sont conçues pour indicateur générique d’un comportement suspect qui n’est peut-être pas associé à la menace détectée. Dans ce cas, le rapport identifie clairement l’alerte comme « générique » et n’influence aucun graphique du rapport.

### <a name="email-related-detections-and-mitigations"></a>Détections et atténuations liées à la messagerie électronique
Les détections et atténuations liées à la messagerie électronique de Microsoft Defender pour Office 365 sont incluses dans les rapports d’analyste en plus des données de point de terminaison déjà disponibles dans Microsoft Defender pour Endpoint. 

Les informations sur les tentatives de courriers électroniques interdits vous donnent des informations sur la façon dont votre organisation était la cible de la menace abordée dans le rapport d’analyste, même si l’attaque a été effectivement bloquée avant la remise ou remise au dossier de courrier indésirable.

## <a name="find-subtle-threat-artifacts-using-advanced-hunting"></a>Rechercher des artefacts de menace discrets à l’aide d’un chasse avancée
Bien que les détections vous permettent d’identifier et d’arrêter automatiquement la menace de suivi, de nombreuses activités d’attaque laissent des traces subtiles qui nécessitent une inspection supplémentaire. Certaines activités d’attaque présentent des comportements qui peuvent également être normaux, de sorte que leur détection dynamique peut entraîner un bruit opérationnel, voire des faux positifs.

[Le repérage avancé](advanced-hunting-overview.md) fournit une interface de requête basée sur le langage de requête Kusto qui simplifie la recherche d’indicateurs discrets de l’activité des menaces. Il vous permet également d’surfacer des informations contextuelles et de vérifier si les indicateurs sont connectés à une menace.

Les requêtes de recherche avancées dans les rapports d’analyste ont été examinées par les analystes Microsoft et sont prêtes à être exécutés dans l’éditeur de requête [de recherche avancée.](https://security.microsoft.com/advanced-hunting) Vous pouvez également utiliser les requêtes pour créer des règles de [détection personnalisées](custom-detection-rules.md) qui déclenchent des alertes pour les correspondances futures.


>[!NOTE]
> L’analyse des menaces est également disponible [dans Microsoft Defender pour le point de terminaison.](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) Toutefois, il ne dispose pas de l’intégration de données entre Microsoft Defender pour Office et Microsoft Defender pour le point de terminaison que Microsoft 365 Defender analyse les menaces.


## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble des analyses de menaces](threat-analytics.md)
- [Rechercher de manière proactive les menaces avec le recherche avancée](advanced-hunting-overview.md) 
- [Règles de détection personnalisée](custom-detection-rules.md)