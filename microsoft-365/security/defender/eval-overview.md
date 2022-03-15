---
title: Évaluer et piloter Microsoft 365 Defender, une solution XDR
description: Qu’est-ce que la sécurité XDR ? Comment évaluer une XDR Microsoft en Microsoft 365 Defender ? Utilisez cette série de blogs pour planifier votre laboratoire d Microsoft 365 Defender ou votre environnement pilote pour tester et piloter une solution de sécurité conçue pour protéger les appareils, l’identité, les données et les applications. Commencez votre parcours en matière de cybersécurité XDR ici et faites ce test en production.
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
ms.openlocfilehash: 5c0ef6ce393f7c79ee6fca9b591d99c46d864a52
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504533"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>Évaluer et piloter Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender

# <a name="how-this-article-series-works"></a>Fonctionnement de cette série d’articles

Cette série d’articles est conçue pour vous aider tout au long du processus de configuration d’un environnement XDR d’évaluation *de bout* en bout, afin de pouvoir évaluer les fonctionnalités de Microsoft 365 Defender et même promouvoir directement l’environnement d’évaluation en production quand et si vous êtes prêt.

Si vous débutez avec XDR, vous pouvez analyser ces 7 articles liés pour vous faire une idée de l’ensemble de la solution.

- [Comment créer l’environnement](eval-create-eval-environment.md)
- Configurer ou en savoir plus sur chaque technologie de cette XDR Microsoft
    - [Microsoft Defender pour l’identité](eval-defender-identity-overview.md)
    - [Microsoft Defender pour Office](eval-defender-office-365-overview.md)
    - [Microsoft Defender pour point de terminaison](eval-defender-endpoint-overview.md)
    - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [Comment examiner et répondre à l’aide de cette XDR](eval-defender-investigate-respond.md)
- [Promouvoir l’environnement d’essai en production](eval-defender-promote-to-production.md)

## <a name="microsoft-365-defender-is-a-microsoft-xdr-cyber-security-solution"></a>Microsoft 365 Defender est une solution de cybersécurité XDR Microsoft

Microsoft 365 Defender est une solution de détection et de réponse **(XDR) eXtended** qui collecte, met en corrélation et analyse automatiquement les données de signal, de menace et d’alerte à  partir de votre environnement Microsoft 365, y compris les points de terminaison, la messagerie, les applications et les *identités*. Il tire parti de l’intelligence artificielle (IA) et de l’automatisation pour arrêter automatiquement les attaques et corriger les ressources affectées dans un état sûr.

Pensez à XDR comme l’étape suivante en matière de sécurité, unifiant le point de terminaison (protection évolutive des points de terminaison ou PEPT), la messagerie électronique, l’application et la sécurité des identités au même endroit.

## <a name="microsoft-recommendations-for-evaluating-microsoft-365-defender"></a>Recommandations de Microsoft pour l’évaluation des Microsoft 365 Defender

Microsoft vous recommande de créer votre évaluation dans un abonnement de production existant de Office 365. De cette façon, vous allez obtenir des informations réelles immédiatement et vous pouvez régler les paramètres pour qu’ils fonctionnent contre les menaces actuelles dans votre environnement. Une fois que vous avez acquis de l’expérience et que vous êtes à l’aise avec la plateforme, il vous suffit de promouvoir chaque composant, un par un, en production.

## <a name="the-anatomy-of-a-cyber-security-attack"></a>Anatomie d’une attaque de cybersécurité

Microsoft 365 Defender est une suite de défense d’entreprise en nuage, unifiée, avant et après la violation. Il coordonne la *prévention*, la *détection*,  *l’examen* et la réponse entre les points de terminaison, les identités, les applications, le courrier électronique, les applications collaboratives et toutes leurs données.

Dans cette illustration, une attaque est en cours. Le courrier électronique de hameçonnage arrive dans la boîte de réception d’un employé de votre organisation, qui ouvre sans le savoir la pièce jointe du courrier électronique. Cela installe les programmes malveillants, ce qui entraîne une chaîne d’événements qui peut se terminer par le vol de données sensibles. Mais dans ce cas, Defender for Office 365 est en cours d’utilisation.

![Comment Microsoft 365 Defender arrêter une chaîne de menaces.](../../media/defender/m365-defender-eval-threat-chain.png)

Dans cette illustration :

- **Exchange Online Protection**, qui fait partie de Microsoft Defender pour Office 365, peut détecter le courrier d’hameçonnage et utiliser des règles de flux de messagerie pour s’assurer qu’il n’arrive jamais dans la boîte de réception.
- **Defender pour Office 365** pièces jointes sécurisées teste la pièce jointe et la détermine comme dangereuses, de sorte que le courrier qui arrive n’est pas actionnable par l’utilisateur ou les stratégies empêchent le courrier d’arriver du tout.
- **Defender pour le point de terminaison** gère les appareils qui se connectent au réseau d’entreprise et détectent les vulnérabilités des périphériques et du réseau qui pourraient autrement être exploitées.
- **Defender for Identity prend** note des changements soudains de compte tels que l’escalade des privilèges ou le mouvement latéral à haut risque. Il signale également les problèmes d’identité facilement exploités, tels que la délégation Kerberos sans contrainte, pour la correction par l’équipe de sécurité.
- **Microsoft Defender pour** les applications cloud remarque un comportement anormal tel que les déplacements impossibles, l’accès aux informations d’identification et le téléchargement inhabituel, le partage de fichiers ou l’activité de transport de courrier, et les signale à l’équipe de sécurité.

### <a name="microsoft-365-defender-components-secure-devices-identity-data-and-applications"></a>Microsoft 365 Defender sécurisés des appareils, des identités, des données et des applications

Microsoft 365 Defender est composé de ces technologies de sécurité, fonctionnant en tandem. Vous n’avez pas besoin de tous ces composants pour bénéficier des fonctionnalités de XDR et de Microsoft 365 Defender. Vous gagnerez en efficacité en utilisant également un ou deux. 

|Composant  |Description  |Documentation de référence  |
|---------|---------|---------|
|Microsoft Defender pour l’identité     |      Microsoft Defender pour l’identité utilise des signaux Active Directory pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation.     |     [Qu’est-ce que Microsoft Defender pour Identity ?](/defender-for-identity/what-is)   |
|Exchange Online Protection     |      Exchange Online Protection est le service de filtrage et de relais SMTP basé sur le cloud natif qui permet de protéger votre organisation contre le courrier indésirable et les programmes malveillants.      |   [Exchange Online Protection (EOP) : Office 365](../office-365-security/overview.md)     |
|Microsoft Defender pour Office 365     |     Microsoft Defender pour Office 365 votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration.      |    [Microsoft Defender pour Office 365 - Office 365](../office-365-security/overview.md)    |
|Microsoft Defender pour point de terminaison     |     Microsoft Defender pour point de terminaison est une plateforme unifiée pour la protection des appareils, la détection post-violation, l’examen automatisé et la réponse recommandée.      |   [Microsoft Defender pour le point de terminaison : sécurité Windows sécurité](../defender-endpoint/microsoft-defender-endpoint.md)    |
|Microsoft Defender for Cloud Apps     |      Microsoft Defender pour les applications cloud est une solution saaS complète qui apporte une visibilité approfondie, des contrôles de données forts et une protection renforcée contre les menaces à vos applications cloud.       |    [Qu’est-ce que Defender pour les applications cloud ?](/cloud-app-security/what-is-cloud-app-security)    |
|Azure AD Identity Protection|Azure AD Identity Protection évalue les données de risque provenant de milliards de tentatives de se connecte et utilise ces données pour évaluer le risque de chaque connect dans votre environnement. Ces données sont utilisées par les Azure AD pour autoriser ou empêcher l’accès au compte, selon la configuration des stratégies d’accès conditionnel. Azure AD Identity Protection est sous licence distincte de Microsoft 365 Defender. Il est inclus dans Azure Active Directory Premium P2.|[Qu’est-ce que la protection des identités ?](/azure/active-directory/identity-protection/overview-identity-protection)|
| | | |

## <a name="microsoft-365-defender-architecture"></a>Microsoft 365 Defender architecture

Le diagramme ci-dessous illustre l’architecture de haut niveau pour les composants Microsoft 365 Defender clés et les intégrations. *L’architecture* détaillée de chaque composant Defender et les scénarios d’utilisation sont donnés tout au long de cette série d’articles.

![Microsoft 365 Defender architecture de haut niveau.](../../media/defender/m365-defender-eval-architecture.png)

Dans cette illustration :

- Microsoft 365 Defender combine les signaux de tous les composants Defender pour fournir une détection et une réponse étendues (XDR) sur plusieurs domaines. Cela inclut une file d’attente d’incident unifiée, une réponse automatisée pour arrêter les attaques, une auto-ressource (pour les appareils compromis, les identités des utilisateurs et les boîtes aux lettres), le recherche de menaces croisées et l’analyse des menaces.
- Microsoft Defender pour Office 365 protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. Il partage les signaux résultant de ces activités avec Microsoft 365 Defender. Exchange Online Protection (EOP) est intégré pour fournir une protection de bout en bout pour les courriers électroniques entrants et les pièces jointes.
- Microsoft Defender pour l’identité recueille les signaux des serveurs exécutant les services AD FS (Active Directory Federated Services) et les services de domaine Active Directory (AD DS) locaux. Il utilise ces signaux pour protéger votre environnement d’identité hybride, y compris la protection contre les pirates informatiques qui utilisent des comptes compromis pour se déplacer ultérieurement entre les stations de travail dans l’environnement local.
- Microsoft Defender pour le point de terminaison collecte des signaux à partir des appareils utilisés par votre organisation et les protège.
- Microsoft Defender pour les applications cloud collecte les signaux de l’utilisation des applications cloud par votre organisation et protège les données qui circulent entre votre environnement et ces applications, y compris les applications cloud sanctionnées et non nouvelles.
- Azure AD Identity Protection évalue les données de risque provenant de milliards de tentatives de se connecte et utilise ces données pour évaluer le risque de chaque connect dans votre environnement. Ces données sont utilisées par les Azure AD pour autoriser ou empêcher l’accès au compte, selon la configuration des stratégies d’accès conditionnel. Azure AD Identity Protection est sous licence distincte de Microsoft 365 Defender. Il est inclus dans Azure Active Directory Premium P2.  

## <a name="microsoft-siem-and-soar-can-use-data-from-microsoft-365-defender"></a>Microsoft SIEM et LASER peuvent utiliser les données de Microsoft 365 Defender

Composants d’architecture facultatifs supplémentaires non inclus dans cette illustration :

- **Les données de signal détaillées de tous les composants Microsoft 365 Defender peuvent être intégrées à Microsoft Sentinel** et combinées avec d’autres sources de journalisation pour offrir des fonctionnalités et des informations COMPLÈTEs SIEM et NIVEAUX.
- Pour en savoir plus sur l’utilisation de **Microsoft Sentinel, un SIEM Azure, avec Microsoft 365 Defender** en tant que XDR, lisez cet [article](/azure/sentinel/microsoft-365-defender-sentinel-integration) de présentation et les étapes d’intégration de Microsoft Sentinel et Microsoft 365 Defender [.](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE)
- Pour plus d’informations sur LA FONCTION DNS dans Microsoft Sentinel (y compris les liens vers les manuels dans le référentiel GitHub Microsoft Sentinel), lisez [cet article](/azure/sentinel/automate-responses-with-playbooks).

## <a name="the-evaluation-process-for-microsoft-365-defender-cyber-security"></a>Le processus d’évaluation de Microsoft 365 Defender cybersécurité

Microsoft recommande d’activer les composants de Microsoft 365 dans l’ordre illustré :

![Microsoft 365 Defender d’évaluation de haut niveau.](../../media/defender/m365-defender-eval-process.png)

Le tableau suivant décrit cette illustration.

|      |Étape  |Description  |
|------|---------|---------|
|1     | [Créer l’environnement d’évaluation](eval-create-eval-environment.md)       |Cette étape garantit que vous avez la licence d’essai pour Microsoft 365 Defender.         |
|2     | [Activer Defender pour l’identité](eval-defender-identity-overview.md)        | Passer en revue les exigences en matière d’architecture, activer l’évaluation et passer en revue des didacticiels pour identifier et corriger différents types d’attaques.   |
|3     | [Activer Defender pour Office 365 ](eval-defender-office-365-overview.md)       | Assurez-vous que vous répondez aux exigences d’architecture, activez l’évaluation, puis créez l’environnement pilote. Ce composant inclut Exchange Online Protection et vous évaluerez donc les *deux ici*.      |
|4     | [Activer Defender pour le point de terminaison ](eval-defender-endpoint-overview.md)       | Assurez-vous que vous répondez aux exigences d’architecture, activez l’évaluation, puis créez l’environnement pilote.         |
|5     | [Activer Microsoft Defender pour les applications cloud](eval-defender-mcas-overview.md)        |  Assurez-vous que vous répondez aux exigences d’architecture, activez l’évaluation, puis créez l’environnement pilote.        |
|6      | [Examiner et répondre aux menaces](eval-defender-investigate-respond.md)        |   Simuler une attaque et commencer à utiliser les fonctionnalités de réponse aux incidents.      |
|7      | [Promouvoir la version d’évaluation en production](eval-defender-promote-to-production.md)        | Promouvoir Microsoft 365 composants de production un par un.        |
| | | |

Il s’agit d’un ordre généralement recommandé conçu pour tirer rapidement parti de la valeur des fonctionnalités en fonction de l’effort généralement nécessaire pour déployer et configurer les fonctionnalités. Par exemple, Defender pour Office 365 peut être configuré en moins de temps qu’il ne faut pour inscrire des appareils dans Defender for Endpoint. Bien entendu, vous devez hiérarchiser les composants pour répondre aux besoins de votre entreprise et les activer dans un ordre différent.

## <a name="go-to-the-next-step"></a>Passer à l’étape suivante

[En savoir plus et/ou créer l’environnement d Microsoft 365 Defender d’évaluation](eval-create-eval-environment.md)
