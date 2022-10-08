---
title: Évaluer et piloter Microsoft 365 Defender, une solution XDR
description: Qu’est-ce que la sécurité XDR ? Comment évaluer un XDR Microsoft dans Microsoft 365 Defender ? Utilisez cette série de blog pour planifier votre laboratoire d’essai ou votre environnement pilote Microsoft 365 Defender afin de tester et de piloter une solution de sécurité conçue pour protéger les appareils, l’identité, les données et les applications. Commencez votre parcours de cybersécurité XDR ici et effectuez ce test en production.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 09/15/2022
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-overview
- m365solution-evalutatemtp
- zerotrust-solution
- highpri
- tier1
ms.topic: conceptual
ms.openlocfilehash: 52a060ff551467fc053c08c460d4a1f9601dec5f
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68084775"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>Évaluer et piloter Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender

## <a name="how-this-article-series-works"></a>Fonctionnement de cette série d’articles

Cette série d’articles est conçue pour vous permettre d’effectuer tout le processus de configuration d’un environnement XDR d’essai, de *bout en bout*, afin que vous puissiez évaluer les fonctionnalités et les fonctionnalités de Microsoft 365 Defender et même promouvoir l’environnement d’évaluation directement en production quand et si vous êtes prêt.

Si vous débutez avec la réflexion sur XDR, vous pouvez analyser ces 7 articles liés pour avoir une idée de l’exhaustivité de la solution.

- [Comment créer l’environnement](eval-create-eval-environment.md)
- Configurer ou en savoir plus sur chaque technologie de ce XDR Microsoft
  - [Microsoft Defender pour l’identité](eval-defender-identity-overview.md)
  - [Microsoft Defender pour Office](eval-defender-office-365-overview.md)
  - [Microsoft Defender pour point de terminaison](eval-defender-endpoint-overview.md)
  - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [Comment examiner et répondre à l’aide de ce XDR](eval-defender-investigate-respond.md)
- [Promouvoir l’environnement d’essai en production](eval-defender-promote-to-production.md)

## <a name="microsoft-365-defender-is-a-microsoft-xdr-cyber-security-solution"></a>Microsoft 365 Defender est une solution de cybersécurité Microsoft XDR

Microsoft 365 Defender est une **solution de détection et de réponse (XDR) destinée** à collecter, mettre en corrélation et analyser automatiquement les données de signal, de menace et d’alerte de *l’ensemble* de votre environnement Microsoft 365, notamment le *point de terminaison, le courrier électronique, les applications et les identités*. Il tire parti de l’intelligence artificielle (IA) et de l’automatisation pour arrêter *automatiquement* les attaques et corriger les ressources affectées dans un état sûr.

Considérez XDR comme l’étape suivante en matière de sécurité, d’unifier le point de terminaison (détection et réponse de point de terminaison ou EDR), de l’e-mail, de l’application et de la sécurité des identités au même endroit.

## <a name="microsoft-recommendations-for-evaluating-microsoft-365-defender"></a>Recommandations Microsoft pour l’évaluation des Microsoft 365 Defender

Microsoft vous recommande de créer votre évaluation dans un abonnement de production existant de Office 365. De cette façon, vous obtenez des insights réels immédiatement et pouvez paramétrer les paramètres pour travailler contre les menaces actuelles dans votre environnement. Une fois que vous avez acquis de l’expérience et que vous êtes à l’aise avec la plateforme, il vous suffit de promouvoir chaque composant, un par un, en production.

## <a name="the-anatomy-of-a-cyber-security-attack"></a>Anatomie d’une cyberattaque

Microsoft 365 Defender est une suite de défense d’entreprise basée sur le cloud, unifiée, avant et après la violation. Il coordonne *la prévention, la* *détection*, *l’investigation* et *la réponse* entre les points de terminaison, les identités, les applications, les e-mails, les applications collaboratives et toutes leurs données.

Dans cette illustration, une attaque est en cours. L’e-mail de hameçonnage arrive dans la boîte de réception d’un employé de votre organisation, qui ouvre sans le savoir la pièce jointe. Cela installe des programmes malveillants, ce qui entraîne une chaîne d’événements qui pourraient se terminer par le vol de données sensibles. Mais dans ce cas, Defender pour Office 365 est en cours d’exécution.

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="Les différentes tentatives d’attaque" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

Dans cette illustration :

- **Exchange Online Protection**, qui fait partie de Microsoft Defender pour Office 365, peut détecter l’e-mail de hameçonnage et utiliser des règles de flux de courrier (également appelées règles de transport) pour vous assurer qu’il n’arrive jamais dans la boîte de réception.
- **Defender pour Office 365** utilise des pièces jointes sécurisées pour tester la pièce jointe et déterminer qu’elle est dangereuse, de sorte que le courrier qui arrive n’est pas actionnable par l’utilisateur ou que les stratégies empêchent le courrier d’arriver du tout.
- **Defender pour point de terminaison** gère les appareils qui se connectent au réseau d’entreprise et détectent les vulnérabilités d’appareil et de réseau qui pourraient autrement être exploitées.
- **Defender pour Identity** prend note des changements soudains de compte tels que l’élévation des privilèges ou le déplacement latéral à haut risque. Il signale également les problèmes d’identité facilement exploités, tels que la délégation Kerberos non contrainte, pour correction par l’équipe de sécurité.
- **Microsoft Defender for Cloud Apps** remarque un comportement anormal, comme les déplacements impossibles, l’accès aux informations d’identification et le téléchargement inhabituel, le partage de fichiers ou l’activité de transfert de courrier, et les signale à l’équipe de sécurité.

### <a name="microsoft-365-defender-components-secure-devices-identity-data-and-applications"></a>Microsoft 365 Defender composants sécurisent les appareils, l’identité, les données et les applications

Microsoft 365 Defender est constitué de ces technologies de sécurité, fonctionnant en tandem. Vous n’avez pas besoin de tous ces composants pour tirer parti des fonctionnalités de XDR et de Microsoft 365 Defender. Vous réaliserez des gains et des gains d’efficacité en utilisant un ou deux également.

|Composant|Description|Documentation de référence|
|---|---|---|
|Microsoft Defender pour l’identité|Microsoft Defender pour Identity utilise des signaux Active Directory pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation.|[Qu’est-ce que Microsoft Defender pour Identity ?](/defender-for-identity/what-is)|
|Exchange Online Protection|Exchange Online Protection est le service de relais et de filtrage SMTP basé sur le cloud natif qui permet de protéger votre organisation contre le courrier indésirable et les programmes malveillants.|[Vue d’ensemble de Exchange Online Protection (EOP) - Office 365](/microsoft-365/office-365-security/overview.md)|
|Microsoft Defender pour Office 365|Microsoft Defender pour Office 365 protège votre organisation contre les menaces malveillantes posées par les e-mails, les liens (URL) et les outils de collaboration.|[Microsoft Defender pour Office 365 - Office 365](/microsoft-365/office-365-security/overview.md)|
|Microsoft Defender pour point de terminaison|Microsoft Defender pour point de terminaison est une plateforme unifiée pour la protection des appareils, la détection post-violation, l’investigation automatisée et la réponse recommandée.|[Microsoft Defender pour point de terminaison - Sécurité Windows](../defender-endpoint/microsoft-defender-endpoint.md)|
|Microsoft Defender for Cloud Apps|Microsoft Defender for Cloud Apps est une solution multisaS complète offrant une visibilité approfondie, des contrôles de données forts et une protection renforcée contre les menaces pour vos applications cloud.|[Qu’est-ce que Defender pour les applications cloud ?](/cloud-app-security/what-is-cloud-app-security)|
|Azure AD Identity Protection|Azure AD Identity Protection évalue les données de risque provenant de milliards de tentatives de connexion et utilise ces données pour évaluer le risque de chaque connexion à votre environnement. Ces données sont utilisées par Azure AD pour autoriser ou empêcher l’accès au compte, selon la façon dont les stratégies d’accès conditionnel sont configurées. Azure AD Identity Protection est concédé sous licence séparément de Microsoft 365 Defender. Il est inclus avec Azure Active Directory Premium P2.|[Qu’est-ce qu’Identity Protection ?](/azure/active-directory/identity-protection/overview-identity-protection)|

## <a name="microsoft-365-defender-architecture"></a>architecture Microsoft 365 Defender

Le diagramme ci-dessous illustre une architecture de haut niveau pour les composants et intégrations de Microsoft 365 Defender clés. *L’architecture détaillée* de chaque composant Defender, ainsi que les scénarios d’utilisation, sont fournies tout au long de cette série d’articles.

:::image type="content" source="../../media/defender/m365-defender-eval-architecture.png" alt-text="Architecture de haut niveau du portail Microsoft 365 Defender" lightbox="../../media/defender/m365-defender-eval-architecture.png":::

Dans cette illustration :

- Microsoft 365 Defender combine les signaux de tous les composants Defender pour fournir une détection et une réponse étendues (XDR) entre les domaines. Cela inclut une file d’attente d’incidents unifiée, une réponse automatisée pour arrêter les attaques, l’auto-réparation (pour les appareils compromis, les identités utilisateur et les boîtes aux lettres), la chasse aux menaces croisées et l’analyse des menaces.
- Microsoft Defender pour Office 365 protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. Il partage les signaux résultant de ces activités avec Microsoft 365 Defender. Exchange Online Protection (EOP) est intégré pour fournir une protection de bout en bout pour les e-mails et pièces jointes entrants.
- Microsoft Defender pour Identity collecte les signaux des serveurs exécutant activement active directory Federated Services (AD FS) et Active Directory local Domain Services (AD DS). Il utilise ces signaux pour protéger votre environnement d’identité hybride, y compris la protection contre les pirates informatiques qui utilisent des comptes compromis pour se déplacer latéralement entre les stations de travail dans l’environnement local.
- Microsoft Defender pour point de terminaison collecte les signaux des appareils utilisés par votre organisation et les protège.
- Microsoft Defender for Cloud Apps collecte les signaux de l’utilisation des applications cloud par votre organisation et protège les données qui circulent entre votre environnement et ces applications, y compris les applications cloud approuvées et non approuvées.
- Azure AD Identity Protection évalue les données de risque provenant de milliards de tentatives de connexion et utilise ces données pour évaluer le risque de chaque connexion à votre environnement. Ces données sont utilisées par Azure AD pour autoriser ou empêcher l’accès au compte, selon la façon dont les stratégies d’accès conditionnel sont configurées. Azure AD Identity Protection est concédé sous licence séparément de Microsoft 365 Defender. Il est inclus avec Azure Active Directory Premium P2.

## <a name="microsoft-siem-and-soar-can-use-data-from-microsoft-365-defender"></a>Microsoft SIEM et SOAR peuvent utiliser des données de Microsoft 365 Defender

Composants d’architecture facultatifs supplémentaires non inclus dans cette illustration :

- **Les données de signal détaillées de tous les composants Microsoft 365 Defender peuvent être intégrées à Microsoft Sentinel** et combinées avec d’autres sources de journalisation pour offrir des fonctionnalités et des insights SIEM et SOAR complets.
- **Pour plus d’informations sur l’utilisation de Microsoft Sentinel, un SIEM Azure, avec Microsoft 365 Defender** en tant que XDR, consultez cet [article de vue d’ensemble](/azure/sentinel/microsoft-365-defender-sentinel-integration) et les [étapes d’intégration](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE) de Microsoft Sentinel et Microsoft 365 Defender.
- Pour plus d’informations sur SOAR dans Microsoft Sentinel (y compris les liens vers des playbooks dans le référentiel GitHub Microsoft Sentinel), lisez [cet article](/azure/sentinel/automate-responses-with-playbooks).

## <a name="the-evaluation-process-for-microsoft-365-defender-cyber-security"></a>Processus d’évaluation de la cybersécurité Microsoft 365 Defender

Microsoft recommande d’activer les composants de Microsoft 365 dans l’ordre illustré :

:::image type="content" source="../../media/defender/m365-defender-eval-process.png" alt-text="Un processus d’évaluation de haut niveau dans le portail Microsoft 365 Defender" lightbox="../../media/defender/m365-defender-eval-process.png":::

Le tableau suivant décrit cette illustration.

|Numéro de série|Étape|Description|
|---|---|---|
|1|[Créer l’environnement d’évaluation](eval-create-eval-environment.md)|Cette étape garantit que vous disposez de la licence d’évaluation pour Microsoft 365 Defender.|
|2|[Activer Defender pour Identity](eval-defender-identity-overview.md)|Passez en revue les exigences en matière d’architecture, activez l’évaluation et suivez des didacticiels pour identifier et corriger différents types d’attaques.|
|3|[Activer Defender pour Office 365](eval-defender-office-365-overview.md)|Vérifiez que vous répondez aux exigences d’architecture, activez l’évaluation, puis créez l’environnement pilote. Ce composant inclut Exchange Online Protection et vous allez donc évaluer *les deux* ici.|
|4|[Activer Defender pour point de terminaison](eval-defender-endpoint-overview.md)|Vérifiez que vous répondez aux exigences d’architecture, activez l’évaluation, puis créez l’environnement pilote.|
|5|[Activer Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)|Vérifiez que vous répondez aux exigences d’architecture, activez l’évaluation, puis créez l’environnement pilote.|
|6|[Examiner et répondre aux menaces](eval-defender-investigate-respond.md)|Simuler une attaque et commencer à utiliser des fonctionnalités de réponse aux incidents.|
|7 |[Promouvoir la version d’évaluation en production](eval-defender-promote-to-production.md)|Promouvoir les composants Microsoft 365 en production un par un.|

Cette commande est généralement recommandée et conçue pour tirer parti rapidement de la valeur des fonctionnalités en fonction de la quantité d’efforts généralement nécessaires pour déployer et configurer les fonctionnalités. Par exemple, Defender pour Office 365 peut être configuré en moins de temps que nécessaire pour inscrire des appareils dans Defender pour point de terminaison. Bien sûr, vous devez hiérarchiser les composants pour répondre aux besoins de votre entreprise et les activer dans un ordre différent.

## <a name="go-to-the-next-step"></a>Passer à l’étape suivante

[Découvrez et/ou créez l’environnement d’évaluation Microsoft 365 Defender](eval-create-eval-environment.md)
