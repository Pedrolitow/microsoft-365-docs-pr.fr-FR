---
title: Suivre les menaces émergentes et y répondre avec Microsoft Defender pour l’analyse des menaces de point de terminaison
ms.reviewer: ''
description: Comprendre les menaces émergentes et les techniques d’attaque et comment les arrêter. Évaluez leur impact sur votre organisation et évaluez la résilience de votre organisation.
keywords: analyse des menaces, évaluation des risques, atténuation du système d’exploitation, atténuation des microcodes, état de l’atténuation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 184190e57e5f1478dd40e64f4291fa55eb49768f
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53649118"
---
# <a name="track-and-respond-to-emerging-threats-through-threat-analytics"></a>Suivre les menaces émergentes et y répondre par le biais de l’analyse des menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Avec des adversaires plus sophistiqués et de nouvelles menaces émergentes fréquemment et répandues, il est essentiel de pouvoir rapidement :

- Évaluer l’impact des nouvelles menaces
- Examiner votre résilience par rapport aux menaces ou leur exposition
- Identifier les actions que vous pouvez prendre pour arrêter ou contenir les menaces

L’analyse des menaces est un ensemble de rapports d’experts en matière de sécurité Microsoft couvrant les menaces les plus pertinentes, notamment :

- Acteurs actifs contre les menaces et leurs campagnes
- Techniques d’attaques nouvelles et populaires
- Vulnérabilités critiques
- Surface d'attaque courantes
- Programmes malveillants répandus

Chaque rapport fournit une analyse détaillée d’une menace et des instructions complètes sur la façon de se défendre contre cette menace. Il intègre également des données de votre réseau, ce qui indique si la menace est active et si vous avez des protections applicables en place.

Regardez cette courte vidéo pour en savoir plus sur la façon dont l’analyse des menaces peut vous aider à suivre les dernières menaces et à les arrêter.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bw1f]

## <a name="view-the-threat-analytics-dashboard"></a>Afficher le tableau de bord d’analyse des menaces

Le tableau de bord d’analyse des menaces constitue un excellent point de départ pour obtenir les rapports les plus pertinents pour votre organisation. Il récapitule les menaces dans les sections suivantes :

- **Menaces les** plus récentes : répertorie les derniers rapports sur les menaces publiés, ainsi que le nombre d’appareils avec des alertes actives et résolues.
- **Menaces à fort impact**: répertorie les menaces qui ont eu l’impact le plus élevé sur l’organisation. Cette section classe les menaces par le nombre d’appareils qui ont des alertes actives.
- **Résumé des menaces**: affiche l’impact global des menaces de suivi en affichant le nombre de menaces avec des alertes actives et résolues.

Sélectionnez une menace dans le tableau de bord pour afficher le rapport de cette menace.

![Image d’un tableau de bord d’analyse des menaces](images/ta_dashboard.png)

## <a name="view-a-threat-analytics-report"></a>Afficher un rapport d’analyse des menaces

Chaque rapport d’analyse des menaces fournit des informations en trois sections : **Vue** d’ensemble, rapport **d’analyste** et **atténuations.**

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Vue d’ensemble : comprendre rapidement la menace, évaluer son impact et examiner les défenses

La section **Vue d’ensemble** fournit un aperçu du rapport d’analyste détaillé. Il fournit également des graphiques qui mettent en évidence l’impact de la menace sur votre organisation et votre exposition par le biais d’appareils mal configurés et non configurés.

![Image de la section vue d’ensemble d’un rapport d’analyse des ](images/ta-overview.png)
 _menaces d’un rapport d’analyse des menaces_

#### <a name="assess-the-impact-to-your-organization"></a>Évaluer l’impact sur votre organisation

Chaque rapport inclut des graphiques conçus pour fournir des informations sur l’impact organisationnel d’une menace :

- **Appareils avec alertes**: indique le nombre actuel d’appareils distincts qui ont été touchés par la menace. Un appareil est classé comme **actif** s’il existe au  moins  une alerte associée à cette menace et résolu si toutes les alertes associées à la menace sur l’appareil ont été résolues.
- **Appareils avec des alertes au fil** du temps  : indique le nombre d’appareils distincts avec des alertes **actives** et résolues au fil du temps. Le nombre d’alertes résolues indique la rapidité de réponse de votre organisation aux alertes associées à une menace. Dans l’idéal, le graphique doit afficher les alertes résolues dans un délai de quelques jours.

#### <a name="review-security-resilience-and-posture"></a>Passer en revue la résilience et la posture de sécurité

Chaque rapport inclut des graphiques qui fournissent une vue d’ensemble de la résilience de votre organisation face à une menace donnée :

- **État de la configuration** de la sécurité : indique le nombre d’appareils qui ont appliqué les paramètres de sécurité recommandés qui peuvent aider à atténuer la menace. Les appareils sont considérés **comme sécurisés** s’ils ont _appliqué tous_ les paramètres suivis.
- **État de correction des** vulnérabilités : indique le nombre d’appareils qui ont appliqué des mises à jour de sécurité ou des correctifs qui adressent les vulnérabilités exploitées par la menace.

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Rapport d’analyste : obtenir des informations d’expert de la part de chercheurs en matière de sécurité Microsoft

Go to the **Analyst report** section to read through the detailed expert write-up. La plupart des rapports fournissent des descriptions détaillées des chaînes d’attaques, notamment des tactiques et des [](advanced-hunting-overview.md) techniques mappées à l’infrastructure CK MITRE ATT&, des listes exhaustives de recommandations et de puissants conseils de recherche de menaces.

[En savoir plus sur le rapport d’analyste](threat-analytics-analyst-reports.md)

### <a name="mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Atténuations : examiner la liste des atténuations et l’état de vos appareils

Dans la section **Atténuations,** examinez la liste des recommandations actionnables spécifiques qui peuvent vous aider à renforcer la résilience de votre organisation contre la menace. La liste des mesures de prévention de suivi inclut :

- **Mises à jour de sécurité**: déploiement de mises à jour de sécurité ou de correctifs pour les vulnérabilités
- **Antivirus Microsoft Defender paramètres**
  - Version de l’intelligence de la sécurité
  - Protection fournie par le cloud
  - Protection des applications potentiellement indésirables (PUA)
  - Protection en temps réel

Les informations d’atténuation de cette section intègrent des données de [Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md), qui fournissent également des informations détaillées d’analyse à partir de différents liens dans le rapport.

![Image de la section préventions d’un rapport d’analyse des menaces](images/ta-mitigations.png)

_Section Atténuations d’un rapport d’analyse des menaces_

## <a name="additional-report-details-and-limitations"></a>Détails et limitations supplémentaires du rapport

Lorsque vous utilisez les rapports, gardez les informations suivantes à l’esprit :

- Les données sont limitées en fonction de votre étendue de contrôle d’accès basé sur un rôle (RBAC). Vous verrez l’état des appareils dans les [groupes accessibles.](machine-groups.md)
- Les graphiques reflètent uniquement les atténuations qui sont suivis. Consultez la vue d’ensemble du rapport pour les atténuations supplémentaires qui ne sont pas affichées dans les graphiques.
- Les atténuations ne garantissent pas une résilience complète. Les atténuations fournies reflètent les meilleures actions possibles nécessaires pour améliorer la résilience.
- Les appareils sont comptés comme « indisponibles » s’ils n’ont pas transmis de données au service.
- Les statistiques antivirus sont basées sur Antivirus Microsoft Defender paramètres. Les appareils avec des solutions antivirus tierces peuvent apparaître comme « exposés ».

## <a name="related-topics"></a>Voir aussi

- [Rechercher de manière proactive les menaces avec le recherche avancée](advanced-hunting-overview.md)
- [Comprendre la section rapport d’analyste](threat-analytics-analyst-reports.md)
- [Évaluer et résoudre les faiblesses et les exposition de sécurité](next-gen-threat-and-vuln-mgt.md)
