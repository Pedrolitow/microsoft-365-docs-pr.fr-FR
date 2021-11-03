---
title: Évaluer et piloter Microsoft 365 Defender, une XDR
description: Planifiez votre laboratoire d Microsoft 365 Defender d’essai ou votre environnement pilote pour tester et tester une solution de sécurité conçue pour protéger les appareils, l’identité, les données et les applications.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 06/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 31f8c9dd4e2d7fc1dac79eea22ede9836df6606a
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60667025"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>Évaluer et piloter Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender

Microsoft 365 Defender est une solution XDR (détection et réponse étendue) qui collecte, met automatiquement en corrélation et analyse les données de signal, de menace et d’alerte à partir de votre environnement Microsoft 365, y compris les points de terminaison, la messagerie, les applications et les identités. Il tire parti de l’IA et de l’automatisation étendues pour arrêter automatiquement les attaques et corriger les ressources affectées dans un état sûr. Les articles suivants vous étapent tout au long du processus de configuration d’un environnement d’évaluation afin que vous pouvez évaluer les fonctionnalités de Microsoft 365 Defender. 

Au fil de ces articles, les étapes montrent comment activer chaque composant, configurer les paramètres et commencer la surveillance avec un groupe pilote. Lorsque vous êtes prêt, vous pouvez terminer par promouvoir votre environnement d’évaluation directement dans la production.

Microsoft vous recommande de créer votre évaluation dans un abonnement de production existant de Office 365. De cette façon, vous allez obtenir des informations réelles immédiatement et vous pouvez régler les paramètres pour qu’ils fonctionnent contre les menaces actuelles dans votre environnement. Une fois que vous avez acquis de l’expérience et que vous êtes à l’aise avec la plateforme, il vous suffit de promouvoir chaque composant, un par un, en production.

## <a name="the-anatomy-of-an-attack"></a>Anatomie d’une attaque

Microsoft 365 Defender est une suite de défense d’entreprise en nuage, unifiée, avant et après la violation. Il coordonne la *prévention,* la  *détection,* *l’examen* et la réponse entre les points de terminaison, les identités, les applications, le courrier électronique, les applications collaboratives et toutes leurs données.

Dans cette illustration, une attaque est en cours. Le courrier électronique de hameçonnage arrive dans la boîte de réception d’un employé de votre organisation, qui ouvre sans le savoir la pièce jointe du courrier électronique. Cela installe les programmes malveillants, ce qui entraîne une chaîne d’événements qui peut se terminer par le vol de données sensibles. Mais dans ce cas, Defender pour Office 365 est en cours d’utilisation.

![Comment Microsoft 365 Defender arrêter une chaîne de menaces.](../../media/defender/m365-defender-eval-threat-chain.png)

Dans cette illustration :

- **Exchange Online Protection**, qui fait partie de Microsoft Defender pour Office 365, peut détecter le courrier d’hameçonnage et utiliser des règles de flux de messagerie pour s’assurer qu’il n’arrive jamais dans la boîte de réception.
- **Defender pour Office 365** pièces jointes sécurisées teste la pièce jointe et la détermine comme dangereuses, de sorte que le courrier qui arrive n’est pas actionnable par l’utilisateur ou les stratégies empêchent le courrier d’arriver du tout.
- **Defender pour le point de terminaison** gère les appareils qui se connectent au réseau d’entreprise et détectent les vulnérabilités des périphériques et du réseau qui pourraient autrement être exploitées.
- **Defender for Identity prend** note des changements soudains de compte tels que l’escalade des privilèges ou le mouvement latéral à haut risque. Il signale également les problèmes d’identité facilement exploités, tels que la délégation Kerberos sans contrainte, pour la correction par l’équipe de sécurité.
- **Microsoft Cloud App Security** remarque un comportement anormal tel qu’un déplacement impossible, l’accès aux informations d’identification et un téléchargement inhabituel, un partage de fichiers ou une activité de transport de courrier, et les signale à l’équipe de sécurité.

### <a name="microsoft-365-defender-components"></a>Microsoft 365 Defender composants

Microsoft 365 Defender est composé de ces technologies de sécurité, fonctionnant en tandem. Vous n’avez pas besoin de tous ces composants pour bénéficier des fonctionnalités de XDR et de Microsoft 365 Defender. Vous gagnerez en efficacité en utilisant également un ou deux. 

|Composant  |Description  |Documentation de référence  |
|---------|---------|---------|
|Microsoft Defender pour l’identité     |      Microsoft Defender pour l’identité utilise des signaux Active Directory pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation.     |     [Qu’est-ce que Microsoft Defender pour Identity ?](/defender-for-identity/what-is)   |
|Exchange Online Protection     |      Exchange Online Protection est le service de filtrage et de relais SMTP basé sur le cloud natif qui permet de protéger votre organisation contre le courrier indésirable et les programmes malveillants.      |   [Exchange Online Protection (EOP) : Office 365](../office-365-security/overview.md)     |
|Microsoft Defender pour Office 365     |     Microsoft Defender pour Office 365 votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration.      |    [Microsoft Defender pour Office 365 - Office 365](../office-365-security/overview.md)    |
|Microsoft Defender pour point de terminaison     |     Microsoft Defender pour point de terminaison est une plateforme unifiée pour la protection des appareils, la détection post-violation, l’examen automatisé et la réponse recommandée.      |   [Microsoft Defender pour le point de terminaison : sécurité Windows sécurité](../defender-endpoint/microsoft-defender-endpoint.md)    |
|Microsoft Cloud App Security     |      Microsoft Cloud App Security est une solution saaS complète qui apporte une visibilité approfondie, des contrôles de données forts et une protection renforcée contre les menaces à vos applications cloud.       |    [Qu'est-ce que la sécurité des applications du Cloud ?](/cloud-app-security/what-is-cloud-app-security)    |
|Azure AD Identity Protection|Azure AD La protection des identités évalue les données de risque provenant de milliards de tentatives de se connecte et utilise ces données pour évaluer le risque de chaque connect dans votre environnement. Ces données sont utilisées par les Azure AD pour autoriser ou empêcher l’accès au compte, selon la configuration des stratégies d’accès conditionnel. Azure AD La protection des identités est sous licence distincte de Microsoft 365 Defender. Il est inclus dans Azure Active Directory Premium P2.|[Qu’est-ce que la protection des identités ?](/azure/active-directory/identity-protection/overview-identity-protection)|
| | | |

## <a name="microsoft-365-defender-architecture"></a>Microsoft 365 Defender architecture

Le diagramme ci-dessous illustre l’architecture de haut niveau pour les composants Microsoft 365 Defender clés et les intégrations. *L’architecture* détaillée de chaque composant Defender et les scénarios d’utilisation sont donnés tout au long de cette série d’articles.

![Microsoft 365 Defender architecture de haut niveau.](../../media/defender/m365-defender-eval-architecture.png)

Dans cette illustration :

- Microsoft 365 Defender combine les signaux de tous les composants Defender pour fournir une détection et une réponse étendues (XDR) sur plusieurs domaines. Cela inclut une file d’attente d’incident unifiée, une réponse automatisée pour arrêter les attaques, une auto-ressource (pour les appareils compromis, les identités des utilisateurs et les boîtes aux lettres), le recherche de menaces croisées et l’analyse des menaces.
- Microsoft 365 Defender votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. Il partage les signaux résultant de ces activités avec Microsoft 365 Defender. Exchange Online Protection (EOP) est intégré pour fournir une protection de bout en bout pour les messages électroniques et pièces jointes entrants.
- Microsoft Defender pour l’identité recueille les signaux des serveurs exécutant les services AD FS (Active Directory Federated Services) et les services de domaine Active Directory (AD DS) locaux. Il utilise ces signaux pour protéger votre environnement d’identité hybride, y compris la protection contre les pirates informatiques qui utilisent des comptes compromis pour se déplacer ultérieurement entre les stations de travail dans l’environnement local.
- Microsoft Defender pour le point de terminaison collecte des signaux à partir des appareils utilisés par votre organisation et les protège.
- Microsoft Cloud App Security collecte les signaux provenant de l’utilisation des applications cloud par votre organisation et protège les données qui circulent entre votre environnement et ces applications, y compris les applications cloud sanctionnées et non utilisées.
- Azure AD La protection des identités évalue les données de risque provenant de milliards de tentatives de se connecte et utilise ces données pour évaluer le risque de chaque connect dans votre environnement. Ces données sont utilisées par les Azure AD pour autoriser ou empêcher l’accès au compte, selon la configuration des stratégies d’accès conditionnel. Azure AD La protection des identités est sous licence distincte de Microsoft 365 Defender. Il est inclus dans Azure Active Directory Premium P2.  

Composants d’architecture facultatifs supplémentaires non inclus dans cette illustration :

- Les données de signal détaillées de tous les composants Microsoft 365 Defender peuvent être intégrées à Azure Sentinel et combinées avec d’autres sources de journalisation pour offrir des fonctionnalités et des informations COMPLÈTEs SIEM et NIVEAUX.

## <a name="the-evaluation-process"></a>Processus d’évaluation

Microsoft recommande d’activer les composants de Microsoft 365 dans l’ordre illustré :

![Microsoft 365 Defender d’évaluation de haut niveau.](../../media/defender/m365-defender-eval-process.png)

Le tableau suivant décrit cette illustration.

|      |Étape  |Description  |
|------|---------|---------|
|1     | [Créer l’environnement d’évaluation](eval-create-eval-environment.md)       |Cette étape garantit que vous avez la licence d’essai pour Microsoft 365 Defender.         |
|2     | [Activer Defender pour l’identité](eval-defender-identity-overview.md)        | Passer en revue les exigences en matière d’architecture, activer l’évaluation et passer en revue des didacticiels pour identifier et corriger différents types d’attaques.   |
|3     | [Activer Defender pour Office 365 ](eval-defender-office-365-overview.md)       | Assurez-vous que vous répondez aux exigences d’architecture, activez l’évaluation, puis créez l’environnement pilote. Ce composant inclut Exchange Online Protection et vous évaluerez donc les *deux ici.*      |
|4      | [Activer Defender pour le point de terminaison ](eval-defender-endpoint-overview.md)       | Assurez-vous que vous répondez aux exigences d’architecture, activez l’évaluation, puis créez l’environnement pilote.         |
|5     | [Activer Microsoft Cloud App Security](eval-defender-mcas-overview.md)        |  Assurez-vous que vous répondez aux exigences d’architecture, activez l’évaluation, puis créez l’environnement pilote.        |
|6      | [Examiner et répondre aux menaces](eval-defender-investigate-respond.md)        |   Simuler une attaque et commencer à utiliser les fonctionnalités de réponse aux incidents.      |
|7      | [Promouvoir la version d’évaluation en production](eval-defender-promote-to-production.md)        | Promouvoir Microsoft 365 composants de production un par un.        |
| | | |

Il s’agit d’un ordre généralement recommandé conçu pour obtenir rapidement la valeur des fonctionnalités en fonction de la quantité d’efforts généralement requise pour déployer et configurer les fonctionnalités. Par exemple, Defender pour Office 365 peut être configuré en moins de temps que la durée d’inscription des appareils dans Defender for Endpoint. Bien entendu, vous pouvez hiérarchiser les composants pour répondre aux besoins de votre entreprise et les activer dans un ordre différent.

## <a name="next-steps"></a>Prochaines étapes

[Créer l’environnement d Microsoft 365 Defender évaluation de l’environnement](eval-create-eval-environment.md)
