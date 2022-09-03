---
title: Comprendre la section rapport d’analyste dans l’analyse des menaces.
ms.reviewer: ''
description: La façon dont la section rapport des rapports d’analyse des menaces fournit des informations sur les menaces, l’atténuation, les détections, les requêtes de chasse avancées, etc.
keywords: rapport d’analyste, analyse des menaces, détections, requêtes de repérage avancées, atténuations,
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 9ba1903ceb1940b7be8aaddca4fd9659b3d12e0d
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586267"
---
# <a name="the-analyst-report-in-threat-analytics"></a>Rapport d’analyste dans l’analyse des menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Chaque [rapport d’analyse des menaces](threat-analytics.md) comprend des sections dynamiques et une section écrite complète appelée _rapport d’analyste_. Pour accéder à cette section, ouvrez le rapport sur la menace suivie et sélectionnez l’onglet **Rapport de l’analyste** .

:::image type="content" source="images/ta-analyst-report-small.png" alt-text="Section Rapport d’analyste d’un rapport d’analyse des menaces" lightbox="images/ta-analyst-report-small.png":::

_Section Rapport d’analyste d’un rapport d’analyse des menaces_

## <a name="scan-the-analyst-report"></a>Analyser le rapport d’analyste

Chaque section du rapport d’analyste est conçue pour fournir des informations exploitables. Bien que les rapports varient, la plupart des rapports incluent les sections décrites dans le tableau suivant.

<br>

****

|Section Rapport|Description|
|---|---|
|Résumé|Vue d’ensemble de la menace, y compris quand elle a été vue pour la première fois, ses motivations, des événements notables, des cibles majeures, et des outils et techniques distincts. Vous pouvez utiliser ces informations pour évaluer plus en détail comment hiérarchiser la menace dans le contexte de votre secteur d’activité, de votre emplacement géographique et de votre réseau.|
|Analyse|Informations techniques sur les menaces, notamment les détails d’une attaque et la façon dont les attaquants peuvent utiliser une nouvelle technique ou une nouvelle surface d’attaque|
|Techniques MITRE ATT&CK observées|Comment les techniques observées correspondent à [l’infrastructure d’attaque MITRE ATT&CK](https://attack.mitre.org/)|
|[Atténuations](#apply-additional-mitigations)|Recommandations qui peuvent arrêter ou aider à réduire l’impact de la menace. Cette section inclut également des atténuations qui ne sont pas suivies dynamiquement dans le cadre du rapport d’analyse des menaces.|
|[Détails de la détection](#understand-how-each-threat-can-be-detected)|Détections spécifiques et génériques fournies par les solutions de sécurité Microsoft qui peuvent exposer des activités ou des composants associés à la menace.|
|[Repérage avancé](#find-subtle-threat-artifacts-using-advanced-hunting)|[Requêtes de chasse avancées](advanced-hunting-overview.md) pour identifier de manière proactive les activités de menace possibles. La plupart des requêtes sont fournies pour compléter les détections, en particulier pour localiser des composants ou des comportements potentiellement malveillants qui n’ont pas pu être évalués dynamiquement comme malveillants.|
|References|Publications Microsoft et tierces référencées par les analystes lors de la création du rapport. Le contenu de l’analyse des menaces est basé sur des données validées par des chercheurs Microsoft. L’information provenant de sources tierces accessibles au public est clairement identifiée comme telle.|
|Journal des modifications|Heure à laquelle le rapport a été publié et date à laquelle des modifications importantes ont été apportées au rapport.|
|

## <a name="apply-additional-mitigations"></a>Appliquer des atténuations supplémentaires

Analyse des menaces suit dynamiquement [l’état des mises à jour de sécurité et des configurations sécurisées](threat-analytics.md#mitigations-review-list-of-mitigations-and-the-status-of-your-devices). Ces informations sont disponibles sous forme de graphiques et de tableaux sous l’onglet **Atténuations** .

En plus de ces atténuations suivies, le rapport de l’analyste traite également des atténuations qui _ne sont pas_ surveillées dynamiquement. Voici quelques exemples d’atténuations importantes qui ne sont pas suivies dynamiquement :

- Bloquer les e-mails avec des pièces jointes _.lnk_ ou d’autres types de fichiers suspects
- Aléatoire des mots de passe d’administrateur local
- Informer les utilisateurs finaux sur l’e-mail de hameçonnage et d’autres vecteurs de menace
- Activer des règles spécifiques de [réduction de la surface d’attaque](attack-surface-reduction.md)

Bien que vous puissiez utiliser l’onglet **Atténuations** pour évaluer votre posture de sécurité par rapport à une menace, ces recommandations vous permettent de prendre des mesures supplémentaires pour améliorer votre posture de sécurité. Lisez attentivement tous les conseils d’atténuation dans le rapport d’analyste et appliquez-les dans la mesure du possible.

## <a name="understand-how-each-threat-can-be-detected"></a>Comprendre comment chaque menace peut être détectée

Le rapport d’analyste fournit également les détections de l’Antivirus Microsoft Defender et des fonctionnalités de _détection et de réponse_ des points de terminaison (EDR).

### <a name="antivirus-detections"></a>Détections antivirus

Ces détections sont disponibles sur les appareils sur lesquels [l’Antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) est activé. Lorsque ces détections se produisent sur les appareils qui ont été intégrés à Microsoft Defender pour point de terminaison, elles déclenchent également des alertes qui éclairent les graphiques du rapport.

> [!NOTE]
> Le rapport d’analyste répertorie également **les détections génériques** qui peuvent identifier un large éventail de menaces, en plus des composants ou des comportements spécifiques à la menace suivie. Ces détections génériques ne se reflètent pas dans les graphiques.

### <a name="endpoint-detection-and-response-edr-alerts"></a>Alertes de détection et de réponse de point de terminaison (EDR)

Des alertes EDR sont déclenchées pour [les appareils intégrés à Microsoft Defender pour point de terminaison](onboard-configure.md). Ces alertes reposent généralement sur les signaux de sécurité collectés par le capteur Microsoft Defender pour point de terminaison et d’autres fonctionnalités de point de terminaison (telles que l’antivirus, la protection réseau, la protection contre les falsifications) qui servent de sources de signal puissantes.

À l’instar de la liste des détections antivirus, certaines alertes EDR sont conçues pour signaler de manière générique les comportements suspects qui peuvent ne pas être associés à la menace suivie. Dans ce cas, le rapport identifie clairement l’alerte comme « générique » et n’influence aucun des graphiques du rapport.

## <a name="find-subtle-threat-artifacts-using-advanced-hunting"></a>Rechercher des artefacts de menace subtils à l’aide de la chasse avancée

Bien que les détections vous permettent d’identifier et d’arrêter automatiquement la menace suivie, de nombreuses activités d’attaque laissent des traces subtiles qui nécessitent une inspection supplémentaire. Certaines activités d’attaque présentent des comportements qui peuvent également être normaux, de sorte que leur détection dynamique peut entraîner un bruit opérationnel ou même des faux positifs.

[La chasse avancée](advanced-hunting-overview.md) fournit une interface de requête basée sur Langage de requête Kusto qui simplifie la localisation d’indicateurs subtils d’activité de menace. Il vous permet également de faire apparaître des informations contextuelles et de vérifier si les indicateurs sont connectés à une menace.

Les requêtes de repérage avancées dans les rapports d’analystes ont été contrôlées par les analystes Microsoft et sont prêtes à être exécutées dans [l’éditeur de requête de chasse avancé](https://security.microsoft.com/advanced-hunting). Vous pouvez également utiliser les requêtes pour créer des [règles de détection personnalisées](custom-detection-rules.md) qui déclenchent des alertes pour les correspondances futures.

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble des analyses de menaces](threat-analytics.md)
- [Rechercher de manière proactive les menaces avec la chasse avancée](advanced-hunting-overview.md)
- [Règles de détection personnalisée](custom-detection-rules.md)
