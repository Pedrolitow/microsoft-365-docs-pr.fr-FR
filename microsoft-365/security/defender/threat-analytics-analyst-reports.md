---
title: Comprendre la section rapport des analystes dans l’analyse des menaces dans Microsoft 365 Defender
ms.reviewer: ''
description: Découvrez la section rapport d’analyste de chaque rapport d’analyse des menaces. Découvrez comment il fournit des informations sur les menaces, les atténuations, les détections, les requêtes de chasse avancées, etc.
keywords: rapport d’analyste, analyse des menaces, détections, requêtes de repérage avancées, atténuations,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f325ec8c2024bb5e1f00c42811863c7673eeced2
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68084416"
---
# <a name="understand-the-analyst-report-in-threat-analytics-in-microsoft-365-defender"></a>Comprendre le rapport d’analyste dans l’analyse des menaces dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Chaque [rapport d’analyse des menaces](threat-analytics.md) comprend des sections dynamiques et une section écrite complète appelée _rapport d’analyste_. Pour accéder à cette section, ouvrez le rapport sur la menace suivie et sélectionnez l’onglet **Rapport de l’analyste** .

:::image type="content" source="../../media/threat-analytics/ta_analystreport_mtp.png" alt-text="Section Rapport d’analyste d’un rapport d’analyse des menaces" lightbox="../../media/threat-analytics/ta_analystreport_mtp.png":::

_Section Rapport d’analyste d’un rapport d’analyse des menaces_

## <a name="scan-the-analyst-report"></a>Analyser le rapport d’analyste

Chaque section du rapport d’analyste est conçue pour fournir des informations exploitables. Bien que les rapports varient, la plupart des rapports incluent les sections décrites dans le tableau suivant.

| Section Rapport | Description |
|--|--|
| Résumé | Vue d’ensemble de la menace, y compris quand elle a été vue pour la première fois, ses motivations, des événements notables, des cibles majeures, et des outils et techniques distincts. Vous pouvez utiliser ces informations pour évaluer plus en détail comment hiérarchiser la menace dans le contexte de votre secteur d’activité, de votre emplacement géographique et de votre réseau. |
| Analyse | Informations techniques sur les menaces, notamment les détails d’une attaque et la façon dont les attaquants peuvent utiliser une nouvelle technique ou une nouvelle surface d’attaque |
| Techniques MITRE ATT&CK observées | Comment les techniques observées correspondent à [l’infrastructure d’attaque MITRE ATT&CK](https://attack.mitre.org/) |
| [Atténuations](#apply-additional-mitigations) | Recommandations qui peuvent arrêter ou aider à réduire l’impact de la menace. Cette section inclut également des atténuations qui ne sont pas suivies dynamiquement dans le cadre du rapport d’analyse des menaces. |
| [Détails de la détection](#understand-how-each-threat-can-be-detected) | Détections spécifiques et génériques fournies par les solutions de sécurité Microsoft qui peuvent exposer des activités ou des composants associés à la menace. |
| [Repérage avancé](#find-subtle-threat-artifacts-using-advanced-hunting) | [Requêtes de chasse avancées](advanced-hunting-overview.md) pour identifier de manière proactive les activités de menace possibles. La plupart des requêtes sont fournies pour compléter les détections, en particulier pour localiser des composants ou des comportements potentiellement malveillants qui n’ont pas pu être évalués dynamiquement comme malveillants. |
| References | Publications Microsoft et tierces référencées par les analystes lors de la création du rapport. Le contenu de l’analyse des menaces est basé sur des données validées par des chercheurs Microsoft. L’information provenant de sources tierces accessibles au public est clairement identifiée comme telle. |
| Journal des modifications | Heure à laquelle le rapport a été publié et date à laquelle des modifications importantes ont été apportées au rapport. |

## <a name="apply-additional-mitigations"></a>Appliquer des atténuations supplémentaires

Analyse des menaces suit dynamiquement [l’état des mises à jour de sécurité et des configurations sécurisées](threat-analytics.md#exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices). Ces informations sont disponibles sous forme de graphiques et de tableaux dans l’onglet **Atténuations de l’exposition &** .

En plus de ces atténuations suivies, le rapport de l’analyste traite également des atténuations qui _ne sont pas_ surveillées dynamiquement. Voici quelques exemples d’atténuations importantes qui ne sont pas suivies dynamiquement :

- Bloquer les e-mails avec des pièces jointes _.lnk_ ou d’autres types de fichiers suspects
- Aléatoire des mots de passe d’administrateur local
- Informer les utilisateurs finaux sur l’e-mail de hameçonnage et d’autres vecteurs de menace
- Activer des règles spécifiques de [réduction de la surface d’attaque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction)

Bien que vous puissiez utiliser l’onglet **Exposition & atténuations** pour évaluer votre posture de sécurité contre une menace, ces recommandations vous permettent de prendre des mesures supplémentaires pour améliorer votre posture de sécurité. Lisez attentivement tous les conseils d’atténuation dans le rapport d’analyste et appliquez-les dans la mesure du possible.

## <a name="understand-how-each-threat-can-be-detected"></a>Comprendre comment chaque menace peut être détectée

Le rapport d’analyste fournit également les détections des fonctionnalités de détection et de réponse de Microsoft Defender antivirus et de point de _terminaison_ (EDR).

### <a name="antivirus-detections"></a>Détections antivirus

Ces détections sont disponibles sur les appareils sur lesquels [Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) est activé. Lorsque ces détections se produisent sur les appareils qui ont été intégrés à Microsoft Defender pour point de terminaison, elles déclenchent également des alertes qui éclairent les graphiques du rapport.

>[!NOTE]
>Le rapport d’analyste répertorie également **les détections génériques** qui peuvent identifier un large éventail de menaces, en plus des composants ou des comportements spécifiques à la menace suivie. Ces détections génériques ne se reflètent pas dans les graphiques.

### <a name="endpoint-detection-and-response-edr-alerts"></a>Alertes de détection et de réponse de point de terminaison (EDR)

Des alertes EDR sont déclenchées pour [les appareils intégrés à Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure). Ces alertes s’appuient généralement sur les signaux de sécurité collectés par le capteur Microsoft Defender pour point de terminaison et d’autres fonctionnalités de point de terminaison, telles que l’antivirus, la protection réseau, la protection contre les falsifications, qui servent de sources de signal puissantes.

À l’instar de la liste des détections antivirus, certaines alertes EDR sont conçues pour signaler de manière générique les comportements suspects qui peuvent ne pas être associés à la menace suivie. Dans ce cas, le rapport identifie clairement l’alerte comme « générique » et n’influence aucun des graphiques du rapport.

### <a name="email-related-detections-and-mitigations"></a>détections et atténuations liées à Email

Email détections et atténuations liées aux Microsoft Defender pour Office 365 sont incluses dans les rapports d’analystes en plus des données de point de terminaison déjà disponibles à partir de Microsoft Defender pour point de terminaison.

Les informations de tentative d’e-mail empêchées vous donnent des informations sur la cible de la menace que votre organisation a abordée dans le rapport d’analyste, même si l’attaque a été effectivement bloquée avant la remise ou remise au dossier courrier indésirable.

## <a name="find-subtle-threat-artifacts-using-advanced-hunting"></a>Rechercher des artefacts de menace subtils à l’aide de la chasse avancée

Bien que les détections vous permettent d’identifier et d’arrêter automatiquement la menace suivie, de nombreuses activités d’attaque laissent des traces subtiles qui nécessitent une inspection supplémentaire. Certaines activités d’attaque présentent des comportements qui peuvent également être normaux, de sorte que leur détection dynamique peut entraîner un bruit opérationnel ou même des faux positifs.

[La chasse avancée](advanced-hunting-overview.md) fournit une interface de requête basée sur Langage de requête Kusto qui simplifie la localisation d’indicateurs subtils d’activité de menace. Il vous permet également de faire apparaître des informations contextuelles et de vérifier si les indicateurs sont connectés à une menace.

Les requêtes de repérage avancées dans les rapports d’analystes ont été contrôlées par les analystes Microsoft et sont prêtes à être exécutées dans [l’éditeur de requête de chasse avancé](https://security.microsoft.com/advanced-hunting). Vous pouvez également utiliser les requêtes pour créer des [règles de détection personnalisées](custom-detection-rules.md) qui déclenchent des alertes pour les correspondances futures.

>[!NOTE]
> L’analyse des menaces est également disponible dans [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics). Toutefois, il n’a pas l’intégration des données entre Microsoft Defender pour Office et Microsoft Defender pour point de terminaison.

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble des analyses de menaces](threat-analytics.md)
- [Rechercher de manière proactive les menaces avec la chasse avancée](advanced-hunting-overview.md)
- [Règles de détection personnalisée](custom-detection-rules.md)
