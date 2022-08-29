---
title: Gérer les incidents et les alertes de Defender pour Office 365 dans Microsoft 365 Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Le personnel SecOps peut apprendre à utiliser la file d’attente Incidents dans Microsoft 365 Defender pour gérer les incidents dans Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ef744ec88f8ee81d33e537b5ffc9d128c724f84f
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67383829"
---
# <a name="manage-incidents-and-alerts-from-microsoft-defender-for-office-365-in-microsoft-365-defender"></a>Gérer les incidents et les alertes à partir de Microsoft Defender pour Office 365 dans Microsoft 365 Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Un [incident](/microsoft-365/security/defender/incidents-overview) dans Microsoft 365 Defender est une collection d’alertes corrélées et de données associées qui définissent l’histoire complète d’une attaque. Defender pour Office 365 [alertes](/microsoft-365/compliance/alert-policies#default-alert-policies), [l’investigation et la réponse automatisées (AIR)](office-365-air.md#the-overall-flow-of-air) et le résultat des investigations sont intégrés en mode natif et mis en corrélation sur la page **Incidents** dans Microsoft 365 Defender à <https://security.microsoft.com/incidents-queue>. Nous allons faire référence à cette page en tant que _file d’attente d’incidents_.

Des alertes sont créées lorsque des activités malveillantes ou suspectes affectent une entité (par exemple, un e-mail, des utilisateurs ou des boîtes aux lettres). Les alertes fournissent des insights précieux sur les attaques en cours ou terminées. Toutefois, une attaque en cours peut affecter plusieurs entités, ce qui entraîne plusieurs alertes provenant de différentes sources. Certaines alertes intégrées déclenchent automatiquement des playbooks AIR. Ces playbooks effectuent une série d’étapes d’investigation pour rechercher d’autres entités affectées ou une activité suspecte.

Regardez cette courte vidéo sur la gestion des alertes Microsoft Defender pour Office 365 dans Microsoft 365 Defender.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGrL2]

Defender pour Office 365 alertes, investigations et leurs données sont automatiquement corrélées. Lorsqu’une relation est déterminée, un incident est créé par le système pour donner une visibilité aux équipes de sécurité pour l’ensemble de l’attaque.

Nous recommandons vivement aux équipes SecOps de gérer les incidents et les alertes à partir de Defender pour Office 365 dans la file d’attente Incidents à l’adresse <https://security.microsoft.com/incidents-queue>. Cette approche présente les avantages suivants :

- Plusieurs options de [gestion](/microsoft-365/security/defender/manage-incidents) :
  - Priorisation
  - Filtrage
  - Classification
  - Gestion des balises

  Vous pouvez prendre des incidents directement à partir de la file d’attente ou les affecter à quelqu’un. Les commentaires et l’historique des commentaires peuvent vous aider à suivre la progression.

- Si l’attaque a un impact sur d’autres charges de travail protégées par Microsoft Defender<sup>\*</sup>, les alertes, les investigations et leurs données associées sont également corrélées au même incident.

  <sup>\*</sup>Microsoft Defender pour point de terminaison, Microsoft Defender pour Identity et Microsoft Defender for Cloud Apps.

- La logique de corrélation complexe n’est pas nécessaire, car elle est fournie par le système.

- Si la logique de corrélation ne répond pas entièrement à vos besoins, vous pouvez ajouter des alertes à des incidents existants ou créer de nouveaux incidents.

- Les alertes Defender pour Office 365 connexes, les enquêtes AIR et les actions en attente des enquêtes sont automatiquement ajoutées aux incidents.

- Si l’enquête AIR ne détecte aucune menace, les alertes associées sont automatiquement résolues par le système. Si toutes les alertes d’un incident sont résolues, l’état de l’incident passe également à **Résolu**.

- Les actions de preuve et de réponse associées sont automatiquement agrégées sous l’onglet **Preuves et réponses** de l’incident.

- Les membres de l’équipe de sécurité peuvent prendre des mesures de réponse directement à partir des incidents. Par exemple, ils peuvent supprimer de manière réversible des e-mails dans des boîtes aux lettres ou supprimer des règles de boîte de réception suspectes des boîtes aux lettres.

- Les actions de messagerie recommandées sont créées uniquement lorsque l’emplacement de remise le plus récent d’un e-mail malveillant est une boîte aux lettres cloud.

- Les actions de courrier en attente sont mises à jour en fonction de l’emplacement de remise le plus récent. Si l’e-mail a déjà été corrigé par une action manuelle, l’état le reflète.

- Les actions recommandées sont créées uniquement pour les clusters de messagerie et de messagerie qui sont déterminés comme étant les menaces les plus critiques :
  - Programme malveillant
  - Hameçonnage à haute fiabilité
  - URL malveillantes
  - Fichiers malveillants

> [!NOTE]
> Les incidents ne représentent pas seulement des événements statiques. Ils représentent également des histoires d’attaque qui se produisent au fil du temps. À mesure que l’attaque progresse, les nouvelles alertes Defender pour Office 365, les enquêtes AIR et leurs données sont ajoutées en continu à l’incident existant.

Gérez les incidents sur la page **Incidents** dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com/incidents-queue>suivante :

![Page Incidents dans le portail Microsoft 365 Defender.](../../media/mdo-sec-ops-incidents.png)

![Menu volant Détails sur la page Incidents dans le portail Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-details.png)

![Filtrez le menu volant sur la page Incidents dans le portail Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-filters.png)

![Onglet Résumé des détails de l’incident dans le portail Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-summary-tab.png)

![Onglet Preuves et alertes des détails de l’incident dans le portail Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-evidence-and-response-tab.png)

Gérez les incidents sur la page **Incidents** dans Microsoft Sentinel à l’adresse <https://portal.azure.com/#blade/HubsExtension/BrowseResource/resourceType/microsoft.securityinsightsarg%2Fsentinel>suivante :

![Page Incidents dans Microsoft Sentinel.](../../media/mdo-sec-ops-microsoft-sentinel-incidents.png)

![Page détails de l’incident dans Microsoft Sentinel.](../../media/mdo-sec-ops-microsoft-sentinel-incident-details.png)

## <a name="response-actions-to-take"></a>Actions de réponse à entreprendre

Les équipes de sécurité peuvent effectuer une grande variété d’actions de réponse sur le courrier électronique à l’aide d’outils Defender pour Office 365 :

- Vous pouvez supprimer des messages, mais vous pouvez également effectuer les actions suivantes sur l’e-mail :
  - Passer à la boîte de réception
  - Déplacer vers le courrier indésirable
  - Déplacer vers les éléments supprimés
  - Supprimer (récupération possible)
  - Suppression définitive.

  Vous pouvez effectuer ces actions à partir des emplacements suivants :

  - Onglet **Preuves et réponses** des détails de l’incident sur la page **Incidents** ** à <https://security.microsoft.com/incidents-queue> l’adresse (recommandé).
  - **Explorateur de menaces** à .<https://security.microsoft.com/threatexplorer>
  - Centre **d’action** unifié à  <https://security.microsoft.com/action-center/pending>.

- Vous pouvez démarrer un playbook AIR manuellement sur n’importe quel e-mail à l’aide de l’action **Déclencher une enquête** dans l’Explorateur de menaces.

- Vous pouvez signaler des détections de faux positifs ou de faux négatifs directement à Microsoft à l’aide de [l’Explorateur de menaces](threat-explorer.md) ou [des soumissions d’administrateurs](admin-submission.md).

- Vous pouvez bloquer les fichiers malveillants, les URL ou les expéditeurs non détectés à l’aide de la [liste d’autorisation/de blocage du locataire](manage-tenant-allow-block-list.md).

Defender pour Office 365 actions sont intégrées en toute transparence dans les expériences de chasse et l’historique des actions est visible sous l’onglet **Historique** dans le **centre d’action** unifié à <https://security.microsoft.com/action-center/history>.

Le moyen le plus efficace d’agir consiste à utiliser l’intégration intégrée aux incidents dans Microsoft 365 Defender. Vous pouvez simplement approuver les actions recommandées par AIR dans Defender pour Office 365 sous l’onglet [Preuve et réponse](/microsoft-365/security/defender/investigate-incidents#evidence-and-response) d’un incident dans Microsoft 365 Defender. Cette méthode d’action de tacking est recommandée pour les raisons suivantes :

- Vous examinez l’histoire complète des attaques.
- Vous bénéficiez de la corrélation intégrée avec d’autres charges de travail : Microsoft Defender pour point de terminaison, Microsoft Defender pour Identity et Microsoft Defender for Cloud Apps.
- Vous effectuez des actions sur les e-mails à partir d’un emplacement unique.

Vous prenez des mesures sur l’e-mail en fonction du résultat d’une enquête manuelle ou d’une activité de chasse. [L’Explorateur des menaces](threat-explorer.md) permet aux membres de l’équipe de sécurité d’agir sur les messages électroniques qui peuvent encore exister dans les boîtes aux lettres cloud. Ils peuvent agir sur les messages intra-organisation qui ont été envoyés entre les utilisateurs de votre organisation. Les données de l’Explorateur de menaces sont disponibles pour les 30 derniers jours.

Regardez cette courte vidéo pour découvrir comment Microsoft 365 Defender combine des alertes provenant de différentes sources de détection, comme Defender pour Office 365, en incidents. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGpcs]
