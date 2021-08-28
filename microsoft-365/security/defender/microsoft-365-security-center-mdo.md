---
title: Microsoft Defender pour Office 365 dans Microsoft 365 Defender
description: Découvrez les modifications apportées au Centre de sécurité & conformité à Microsoft 365 Defender.
keywords: Microsoft 365 sécurité, mise en place de Microsoft 365 Defender, Microsoft Defender pour Office 365, Microsoft Defender pour le point de terminaison, MDO, MDE, volet unique, nouveau portail de sécurité, nouveau portail de sécurité Defender
ms.date: 02/21/2021
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: Admin
ms.topic: overview
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.prod: m365-security
ms.technology: m365d
ms.openlocfilehash: e65d7e869011cbbc6a55828f693782a6b7e0dfd6
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58575935"
---
# <a name="microsoft-defender-for-office-365-in-microsoft-365-defender"></a>Microsoft Defender pour Office 365 dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)

## <a name="quick-reference"></a>Référence rapide

Le tableau ci-dessous répertorie les modifications apportées à la navigation entre le Centre de sécurité & conformité et Microsoft 365 Defender.

<br>

****

|[Centre de sécurité et conformité](https://protection.office.com)|[Microsoft 365 Defender](https://security.microsoft.com)|[Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage)|[Centre d’administration Exchange](https://admin.exchange.microsoft.com)|
|---|---|---|---|
|Alertes|<ul><li>[Stratégies d’alerte](https://security.microsoft.com/alertpolicies)</li><li>[Incidents et & alertes](https://security.microsoft.com/alerts)</li></ul>|[Page Alertes](https://compliance.microsoft.com/homepage)||
|Classification||Voir [Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage)||
|Protection contre la perte de données||Voir [Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage)||
|Gestion des enregistrements||Voir [Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage)||
|Gouvernance des informations||Voir [Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage)||
|Gestion des menaces|[Collaboration par & messagerie](https://security.microsoft.com/homepage)|||
|Autorisations|[Autorisations & rôles](https://security.microsoft.com/emailandcollabpermissions)|Voir [Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage)||
|Flux de messagerie|||Voir [Exchange admin center](https://admin.exchange.microsoft.com/#/)|
|Confidentialité des données||Voir [Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage)||
|Rechercher|[Audit](https://security.microsoft.com/auditlogsearch?viewid=Async%20Search)|Recherche (recherche de contenu)||
|Rapports|[Report](https://security.microsoft.com/emailandcollabreport)|||
|Certification de service||Voir [Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage)||
|Surveillance||Voir [Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage)||
|eDiscovery||Voir [Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage)||
|||||

[Microsoft 365 Defender](./overview-security-center.md) combine les fonctionnalités de sécurité des portails de sécurité Microsoft existants, notamment le Centre de sécurité <https://security.microsoft.com> & conformité. Ce centre amélioré aide les équipes de sécurité à protéger leur organisation contre les menaces de façon plus pratique et efficace.

Si vous êtes familiarisé avec le Centre de sécurité & conformité (protection.office.com), cet article décrit certaines des modifications et améliorations apportées à Microsoft 365 Defender.

En savoir plus sur les avantages : [vue d’Microsoft 365 Defender](overview-security-center.md)

Si vous recherchez des éléments liés à la conformité, visitez le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/homepage).

## <a name="new-and-improved-capabilities"></a>Fonctionnalités nouvelles et améliorées

La barre de navigation gauche, ou la barre de lancement rapide, vous semblera familière. Toutefois, ce centre de sécurité contient des éléments nouveaux et mis à jour.

Avec la solution Microsoft 365 Defender unifiée, vous pouvez assembler les signaux de menace et déterminer l’étendue et l’impact complets de la menace, ainsi que son impact actuel sur l’organisation.

:::image type="content" source="../../media/M365-defender-converge-experience.png" alt-text="Image de Microsoft 365 Defender expérience convergée.":::

Defender for Office 365 protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration.

:::image type="content" source="../../media/Defender-for-O365.png" alt-text="Image de Defender pour Office 365.":::

### <a name="incidents-and-alerts"></a>Incidents et alertes

Réunit les incidents et la gestion des alertes de vos e-mail, appareils, et identités. Les alertes sont désormais disponibles sous le nœud Enquête et permettent d’avoir une vue d’ensemble des attaques. La page d’alerte fournit un contexte complet à l’alerte, en combinant les signaux d’attaque pour créer un article détaillé. Auparavant, les alertes étaient spécifiques à différentes charges de travail. Une nouvelle expérience unifiée réunit désormais un affichage cohérent des alertes des charges de travail. Vous pouvez rapidement trier, examiner et prendre des mesures efficaces.

- [En savoir plus sur les enquêtes](incidents-overview.md).
- [En savoir plus sur la gestion des alertes](/windows/security/threat-protection/microsoft-defender-atp/review-alerts).

![Barre de lancement rapide alertes et actions.](../../media/converge-1-alerts-and-actions.png)

### <a name="hunting"></a>Repérage

Recherchez de façon proactive les menaces, les programmes malveillants et des activités malveillantes sur vos points de terminaison, boîtes aux lettres Office 365, etc. à l’aide de [Requêtes de repérage avancé](advanced-hunting-overview.md). Ces requêtes puissantes peuvent être utilisées pour localiser et examiner des indicateurs et entités de menaces connues et de menaces potentielles.

[Les](/windows/security/threat-protection/microsoft-defender-atp/custom-detection-rules) règles de détection personnalisées peuvent être conçues à partir de requêtes de repérage avancées pour vous aider à surveiller de manière proactive les événements qui peuvent indiquer une activité de violation et des appareils mal configurés.

Voici un exemple [de recherche avancée dans](advanced-hunting-example.md) Microsoft Defender pour Office 365.

### <a name="action-center"></a>Centre de notifications

Le centre d’action montre les enquêtes créées par les fonctionnalités automatisées d’enquête et de réponse. Ce système automatisé et self-healing dans Microsoft 365 Defender peut aider les équipes de sécurité en répondant automatiquement à des événements spécifiques.

En savoir plus sur le [Centre de l’action.](m365d-action-center.md)

#### <a name="threat-analytics"></a>Analyses de menaces

Obtenez des informations sur threat Intelligence auprès de chercheurs chevronnés de la sécurité Microsoft. Les analyses de menaces permettent aux équipes de sécurité d’être plus efficaces face aux menaces émergentes. L’analyse des menaces inclut :

- Détections et atténuations liées à la messagerie à partir de Microsoft Defender pour Office 365. Cela s’ajoute aux données de point de terminaison déjà disponibles auprès de Microsoft Defender pour les points de terminaison.
- Les affichages d’incidents liés aux menaces.
- Expérience améliorée pour identifier et utiliser rapidement les informations utilisables dans les rapports.

Vous pouvez accéder à l’analyse des menaces à partir de la barre de navigation supérieure gauche dans Microsoft 365 Defender ou à partir d’une carte de tableau de bord dédiée qui présente les principales menaces pour votre organisation.

En savoir plus sur le suivi et la réponse aux menaces émergentes avec [l’analyse des menaces.](./threat-analytics.md)

### <a name="email--collaboration"></a>E-mail et collaboration

Suivez et examinez les menaces contre l’e-mail, le suivi des campagnes et autres de vos utilisateurs. Si vous avez utilisé le Centre de sécurité & conformité, cela vous sera familier.

:::image type="content" source="../../media/converge-3-email-and-collab-new.png" alt-text="Menu de lancement rapide pour Email & Collab (ou MSDO), à gauche de la Microsoft 365 Defender.":::

#### <a name="email-entity-page"></a>Page de l’entité d’e-mail

La [page Entité de messagerie](../office-365-security/mdo-email-entity-page.md) *unifie* les informations de courrier qui ont été dispersées sur différentes pages ou vues dans le passé. L’étude de l’e-mail en matière de menaces et de tendances est *centralisée*. Les informations d’en-tête et l’aperçu d’e-mail sont accessibles via la même page e-mail, ainsi que d’autres informations utiles liées à l’e-mail. De même, vous pouvez trouver l’état de détonation des pièces jointes ou URL de fichiers malveillants dans un onglet de la même page. La page Entité d’e-mail permet aux administrateurs et aux équipes des opérations de sécurité de comprendre une menace d’e-mail et son état, rapidement, puis d’agir rapidement pour déterminer la gestion.

### <a name="access-and-reports"></a>Accès et rapports

Afficher des rapports, modifier vos paramètres, et modifier les rôles d’un utilisateur.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Menu de lancement rapide pour Microsoft 365 Defender autorisations et de rapports, sur le côté gauche du centre de sécurité.":::

> [!NOTE]
> DKIM (DomainKeys Identified Mail) garantit que les systèmes de messagerie de destination font confiance aux messages sortants envoyés à partir de votre domaine personnalisé.
> Pour les utilisateurs de Defender pour  Office 365, vous pouvez désormais gérer et faire pivoter les clés DKIM via Microsoft 365 Defender : ou accédez à la section Règles de stratégie & stratégies contre les menaces <https://security.microsoft.com/threatpolicy> section  \>  \> \>  \> **DKIM**.
>
> Pour plus d’informations, voir Utiliser DKIM pour valider les messages [sortants envoyés à partir de votre domaine personnalisé.](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)

## <a name="whats-changed"></a>Fonctionnalités modifiées

Ce tableau est une référence rapide de la gestion des menaces où des changements ont eu lieu entre le Centre de sécurité **& conformité** et le **portail Microsoft 365 Defender** de sécurité. Cliquez sur les liens pour en savoir plus sur ces zones.

<br>

****

|Zone|Description de la modification|
|---|---|
|[Enquête](../office-365-security/office-365-air.md#changes-are-coming-soon-in-your-microsoft-365-defender-portal)|Regroupe les fonctionnalités ERA dans [Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365) et [Defender pour les points de terminaison](../defender-endpoint/automated-investigations.md). Avec ces mises à jour et améliorations, votre équipe des opérations de sécurité sera en mesure d’afficher des détails sur les enquêtes automatisées et les actions de correction d’e-mail, le contenu de collaboration, les comptes d’utilisateurs, et les appareils, le tout au même endroit.|
|[File d’attente des alertes](../../compliance/alert-policies.md)|Le **volet volant Afficher les alertes** dans le Centre de sécurité & conformité inclut désormais des liens vers Microsoft 365 Defender. Cliquez sur le **lien Ouvrir la page d’alerte** Microsoft 365 Defender s’ouvre. Vous pouvez accéder à la page **Affichage des alertes** en cliquant sur une alerte Office 365 dans la file d’attente Alertes.|
|[Formation par simulation d’attaque](../office-365-security/attack-simulation-training-insights.md)|Utilisez la formation par simulation d’attaque pour exécuter des scénarios d’attaque réaliste dans votre organisation. Ces attaques simulées peuvent aider à former vos employés avant qu’une attaque réelle n’impacte votre organisation. La formation par simulation d’attaque inclut d’autres options supplémentaires, des rapports améliorés et des flux de formation améliorés pour faciliter l’exécution et la gestion des scénarios de simulation d’attaque et de formation.|
|

Aucune modification apportée à ces zones :

- [Explorer](../office-365-security/threat-explorer.md)
- [Stratégies et règles](../../compliance/alert-policies.md)
- [Campagne](../office-365-security/campaigns.md)
- [Soumissions](../office-365-security/admin-submission.md)
- [Révision](./m365d-action-center.md)
- [Suivi des menaces](../office-365-security/threat-trackers.md)

Consultez également la section **Informations connexes** au bas de cet article.

> [!IMPORTANT]
> Le Microsoft 365 Defender ( <https://security.microsoft.com> ) combine les fonctionnalités de sécurité <https://securitycenter.windows.com> dans , et <https://protection.office.com> . Toutefois, ce que vous voyez dépend de votre abonnement. Si vous n’avez que Microsoft Defender pour Office 365 (plan 1 ou 2), par exemple en tant qu’abonnements autonomes, vous ne pouvez pas afficher les fonctionnalités de sécurité pour les points de terminaison et les clients Defender pour Office Plan 1 ne peuvent pas afficher des éléments tels que Analyses de menaces.

> [!TIP]
> Toutes les Exchange Online Protection (EOP) seront incluses dans Microsoft 365 Defender, car EOP est un élément principal de Defender pour Office 365.

## <a name="microsoft-365-defender-home-page"></a>Microsoft 365 Defender Page d’accueil

La page d’accueil du portail propose des informations récapitulatifs importantes sur l’état de sécurité de Microsoft 365 environnement.

Grâce à l’aide de la **Visite guidée** vous pouvez faire une visite rapide des pages Point de terminaison ou E-mail et collaboration. Notez que ce que vous voyez ici dépend de la licence de Defender pour Office 365 et/ou Defender pour les points de terminaison.

Un lien vers le Centre de sécurité & **conformité** est également inclus à des fins de comparaison. Le dernier lien mène à la **Nouveautés** qui décrit les mises à jour récentes.

## <a name="related-information"></a>Informations connexes

- [Redirection du Centre de sécurité & conformité vers Microsoft 365 Defender](microsoft-365-security-mdo-redirection.md)
- [Le centre des actions](./m365d-action-center.md)
- [Alertes d’e-mail et collaboration](../../compliance/alert-policies.md#default-alert-policies)
- [Règles de détection personnalisée](/microsoft-365/security/defender-endpoint/custom-detection-rules)
- [Créer une simulation d’attaque par hameçonnage](../office-365-security/attack-simulation-training.md) et [Créer une charge utile pour former vos contacts](../office-365-security/attack-simulation-training-payloads.md)
