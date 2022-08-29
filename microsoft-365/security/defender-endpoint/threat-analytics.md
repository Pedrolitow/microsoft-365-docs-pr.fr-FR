---
title: Suivre et répondre aux menaces émergentes avec Microsoft Defender pour point de terminaison analyse des menaces
ms.reviewer: ''
description: Comprendre les menaces émergentes et les techniques d’attaque et comment les arrêter. Évaluez leur impact sur votre organisation et évaluez la résilience de votre organisation.
keywords: analyse des menaces, évaluation des risques, atténuation du système d’exploitation, atténuation des microcodes, état d’atténuation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4a21b62e7ab8cad349dbcabebdd1e0d6eeceacd7
ms.sourcegitcommit: 48a75b40e607542e5fe219b6e75ffc757804a9c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67345148"
---
# <a name="track-and-respond-to-emerging-threats-through-threat-analytics"></a>Suivre et répondre aux menaces émergentes par le biais de l’analytique des menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Avec des adversaires plus sophistiqués et de nouvelles menaces qui apparaissent fréquemment et de manière répandue, il est essentiel de pouvoir rapidement :

- Évaluer l’impact des nouvelles menaces
- Passer en revue votre résilience ou votre exposition aux menaces
- Identifier les actions que vous pouvez effectuer pour arrêter ou contenir les menaces

L’analytique des menaces est un ensemble de rapports d’experts en sécurité Microsoft qui couvrent les menaces les plus pertinentes, notamment :

- Acteurs de menaces actifs et leurs campagnes
- Techniques d’attaque populaires et nouvelles
- Vulnérabilités critiques
- Surface d'attaque courantes
- Programmes malveillants répandus

Chaque rapport fournit une analyse détaillée d’une menace et des conseils détaillés sur la façon de se défendre contre cette menace. Il incorpore également des données de votre réseau, indiquant si la menace est active et si des protections applicables sont en place.

Regardez cette courte vidéo pour en savoir plus sur la façon dont l’analytique des menaces peut vous aider à suivre les dernières menaces et à les arrêter.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bw1f]

## <a name="required-roles-and-permissions"></a>Rôles et des autorisations requis
Le tableau suivant décrit les rôles et les autorisations nécessaires pour accéder à Threat Analytics. Les rôles définis dans le tableau ci-dessous font référence à des rôles personnalisés dans des portails individuels et ne sont pas connectés à des rôles globaux dans Azure AD, même s’ils sont également nommés.

| **L’un des rôles suivants est requis pour Microsoft 365 Defender**  | **L’un des rôles suivants est requis pour Defender pour point de terminaison**  | **L’un des rôles suivants est requis pour Defender pour Office 365** | **L’un des rôles suivants est requis pour Defender pour Cloud Apps** | 
|---------|---------|---------|---------|
| Analyses de menaces | Données d’alertes et d’incidents : <ul><li>Afficher les opérations de sécurité des données</li></ul>Atténuations de la gestion des vulnérabilités Defender :<ul><li>Afficher les données - Gestion des menaces et des vulnérabilités</li></ul> | Données d’alertes et d’incidents :<ul> <li>Gérer les alertes en mode affichage uniquement</li> <li>Gérer des alertes</li> <li>Configuration de l'organisation</li><li>Journaux d’audit</li> <li>Afficher uniquement les journaux d’audit</li><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires d’affichage uniquement</li> </ul> Tentatives d’e-mail empêchées : <ul><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires d’affichage uniquement</li> | Non disponible pour les utilisateurs Defender pour Cloud Apps ou MDI |

## <a name="view-the-threat-analytics-dashboard"></a>Afficher le tableau de bord Analyse des menaces

Le tableau de bord Analyse des menaces est un excellent point de départ pour accéder aux rapports les plus pertinents pour votre organisation. Il récapitule les menaces dans les sections suivantes :

- **Dernières menaces** : répertorie les derniers rapports sur les menaces publiés, ainsi que le nombre d’appareils avec des alertes actives et résolues.
- **Menaces à fort impact** : répertorie les menaces qui ont eu le plus d’impact sur l’organisation. Cette section classe les menaces en fonction du nombre d’appareils qui ont des alertes actives.
- **Résumé des menaces** : affiche l’impact global des menaces suivies en affichant le nombre de menaces avec des alertes actives et résolues.

Sélectionnez une menace dans le tableau de bord pour afficher le rapport correspondant à cette menace.

:::image type="content" source="images/ta_dashboard.png" alt-text="Tableau de bord Analyse des menaces" lightbox="images/ta_dashboard.png":::

## <a name="view-a-threat-analytics-report"></a>Afficher un rapport d’analyse des menaces

Chaque rapport d’analyse des menaces fournit des informations en trois sections : **Vue d’ensemble**, **Rapport d’analyste** et **Atténuations**.

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Vue d’ensemble : comprendre rapidement la menace, évaluer son impact et examiner les défenses

La section **Vue d’ensemble** fournit un aperçu du rapport détaillé de l’analyste. Il fournit également des graphiques qui mettent en évidence l’impact de la menace sur votre organisation et votre exposition par le biais d’appareils mal configurés et non corrigés.

:::image type="content" source="images/ta-overview.png" alt-text="Section Vue d’ensemble d’un rapport d’analyse des menaces" lightbox="images/ta-overview.png":::
_Section Vue d’ensemble d’un rapport d’analyse des menaces_

#### <a name="assess-the-impact-to-your-organization"></a>Évaluer l’impact sur votre organisation

Chaque rapport comprend des graphiques conçus pour fournir des informations sur l’impact organisationnel d’une menace :

- **Appareils avec alertes** : affiche le nombre actuel d’appareils distincts qui ont été affectés par la menace. Un appareil est classé comme **actif** s’il existe au moins une alerte associée à cette menace et **résolu** si *toutes les* alertes associées à la menace sur l’appareil ont été résolues.
- **Appareils avec des alertes au fil du temps** : affiche le nombre d’appareils distincts avec des alertes **actives** et **résolues** au fil du temps. Le nombre d’alertes résolues indique la rapidité avec laquelle votre organisation répond aux alertes associées à une menace. Dans l’idéal, le graphique doit afficher les alertes résolues en quelques jours.

#### <a name="review-security-resilience-and-posture"></a>Passer en revue la résilience et la posture de sécurité

Chaque rapport comprend des graphiques qui fournissent une vue d’ensemble de la résilience de votre organisation face à une menace donnée :

- **État de la configuration de la sécurité** : affiche le nombre d’appareils qui ont appliqué les paramètres de sécurité recommandés qui peuvent aider à atténuer la menace. Les appareils sont considérés comme **sécurisés** s’ils ont appliqué _tous les_ paramètres suivis.
- **État de mise à jour corrective des vulnérabilités** : affiche le nombre d’appareils qui ont appliqué des mises à jour de sécurité ou des correctifs qui traitent les vulnérabilités exploitées par la menace.

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Rapport d’analyste : Obtenir des insights d’experts auprès des chercheurs en sécurité Microsoft

Accédez à la section **Rapport de l’analyste** pour lire l’écriture détaillée de l’expert. La plupart des rapports fournissent des descriptions détaillées des chaînes d’attaque, notamment des tactiques et des techniques mappées à l’infrastructure MITRE ATT&CK, des listes exhaustives de recommandations et de puissants conseils sur [la chasse aux menaces](advanced-hunting-overview.md) .

[En savoir plus sur le rapport d’analyste](threat-analytics-analyst-reports.md)

### <a name="mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Atténuations : passez en revue la liste des atténuations et l’état de vos appareils

Dans la section **Atténuations** , passez en revue la liste des recommandations actionnables spécifiques qui peuvent vous aider à accroître la résilience de votre organisation face à la menace. La liste des atténuations suivies comprend :

- **Mises à jour de sécurité** : déploiement de mises à jour de sécurité ou de correctifs pour les vulnérabilités
- **Paramètres de l’Antivirus Microsoft Defender**
  - Version du renseignement de sécurité
  - Protection fournie par le cloud
  - Protection des applications potentiellement indésirables (PUA)
  - Protection en temps réel

Les informations d’atténuation contenues dans cette section incorporent des données de [Gestion des vulnérabilités Microsoft Defender](next-gen-threat-and-vuln-mgt.md), qui fournissent également des informations détaillées d’exploration à partir de divers liens du rapport.

:::image type="content" source="images/ta-mitigations.png" alt-text="Section Atténuations d’un rapport d’analyse des menaces" lightbox="images/ta-mitigations.png":::


_Section Atténuations d’un rapport d’analyse des menaces_

## <a name="additional-report-details-and-limitations"></a>Détails et limitations supplémentaires du rapport

Lorsque vous utilisez les rapports, gardez à l’esprit les éléments suivants :

- Les données sont limitées en fonction de votre étendue de contrôle d’accès en fonction du rôle (RBAC). Vous verrez l’état des appareils dans les [groupes auxquels vous pouvez accéder](machine-groups.md).
- Les graphiques reflètent uniquement les atténuations suivies. Consultez la vue d’ensemble du rapport pour obtenir des atténuations supplémentaires qui ne sont pas affichées dans les graphiques.
- Les atténuations ne garantissent pas une résilience complète. Les atténuations fournies reflètent les meilleures actions possibles nécessaires pour améliorer la résilience.
- Les appareils sont considérés comme « indisponibles » s’ils n’ont pas transmis de données au service.
- Les statistiques relatives aux antivirus sont basées sur les paramètres de l’Antivirus Microsoft Defender. Les appareils avec des solutions antivirus tierces peuvent apparaître comme étant « exposés ».

## <a name="related-topics"></a>Voir aussi

- [Rechercher de manière proactive les menaces avec la chasse avancée](advanced-hunting-overview.md)
- [Comprendre la section rapport de l’analyste](threat-analytics-analyst-reports.md)
- [Évaluer et résoudre les failles de sécurité et les expositions](next-gen-threat-and-vuln-mgt.md)
