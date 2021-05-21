---
title: Configurer la remise de simulations de hameçonnage tiers aux utilisateurs et de messages non filtrés dans des boîtes aux lettres SecOps
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Les administrateurs peuvent apprendre à utiliser la stratégie de remise avancée dans Exchange Online Protection (EOP) pour identifier les messages qui ne doivent pas être filtrés dans des scénarios pris en charge spécifiques (simulations de hameçonnage tiers et messages remis à des boîtes aux lettres d’opérations de sécurité (SecOps).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8bebc094b56a20a43f92d1acf8d374110de43d71
ms.sourcegitcommit: b0d3abbccf4dd37e32d69664d3ebc9ab8dea760d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2021
ms.locfileid: "52594120"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>Configurer la remise de simulations de hameçonnage tiers aux utilisateurs et de messages non filtrés dans des boîtes aux lettres SecOps

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> La fonctionnalité décrite dans cet article est en prévisualisation, n’est pas disponible pour tout le monde et peut faire l’objet de changements.

Pour assurer la sécurité de votre organisation par [défaut,](secure-by-default.md)Exchange Online Protection (EOP) n’autorise pas les listes sécurisées ou le contournement de filtrage pour les messages qui entraînent des programmes malveillants ou des verdicts de hameçonnage à haut niveau de confiance. Toutefois, il existe des scénarios spécifiques qui nécessitent la remise de messages non filtrés. Par exemple :

- **Simulations de hameçonnage tierces**: les attaques simulées peuvent vous aider à identifier les utilisateurs vulnérables avant qu’une attaque réelle n’impacte votre organisation.
- Boîtes aux lettres d’opérations de sécurité **(SecOps)**: boîtes aux lettres dédiées utilisées par les équipes de sécurité pour collecter et analyser les messages non filtrés (bonnes et mauvaises).

Vous utilisez la _stratégie de remise_ avancée dans Microsoft 365 pour empêcher le filtrage de ces messages dans ces _scénarios spécifiques._ <sup>\*</sup> La stratégie de remise avancée garantit que les messages dans ces scénarios ne sont pas filtrés :

- Les filtres dans EOP et Microsoft Defender Office 365 aucune action sur ces messages.<sup>\*</sup>
- [La purge sans heure (ZAP)](zero-hour-auto-purge.md) pour le courrier indésirable et le hameçonnage n’a aucune action sur ces messages.<sup>\*</sup>
- [Les alertes système par défaut](alerts.md) ne sont pas déclenchées pour ces scénarios.
- [Air and clustering in Defender for Office 365](office-365-air.md) ignores these messages.
- Plus spécifiquement pour les simulations de hameçonnage tierces :
  - [Les soumissions d’administrateur](admin-submission.md) génèrent une réponse automatique qui dit que le message fait partie d’une campagne de simulation de hameçonnage et qu’il ne constitue pas une menace réelle. Les alertes et air ne sont pas déclenchés.
  - [Les liens sécurisés dans Defender Office 365](safe-links.md) ne bloquent pas ou ne désaxiquent pas les URL spécifiquement identifiées dans ces messages.
  - [Les pièces jointes sécurisées](safe-attachments.md) dans Defender Office 365 ne désaxiquent pas les pièces jointes dans ces messages.

<sup>\*</sup> Vous ne pouvez pas contourner le filtrage des programmes malveillants ou zap pour les programmes malveillants.

Les messages identifiés par la stratégie de remise avancée ne sont pas des menaces de sécurité. Les messages sont donc marqués comme étant des remplacements système. Les administrateurs peuvent filtrer et analyser ces substitutions système dans les expériences suivantes :

- [Détections de l’Explorateur de menaces/En temps réel dans Defender Office 365 plan 2](threat-explorer.md)
- Page [Entité de messagerie dans l’Explorateur de menaces/Détections en temps réel](mdo-email-entity-page.md)
- Rapport [d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Recherche avancée dans Microsoft Defender pour point de terminaison](../defender-endpoint/advanced-hunting-overview.md)
- [Vues de campagne](campaigns.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de sécurité et conformité sur <https://protection.office.com/>. Pour aller directement à la page **de remise avancée,** ouvrez <https://protection.office.com/advanceddelivery> .

- Des autorisations doivent vous être attribuées avant de pouvoir suivre les procédures de cet article :
  - Pour créer, modifier ou supprimer des paramètres configurés dans la stratégie  de remise avancée, vous devez être membre du groupe  de rôles Administrateur de la sécurité dans le Centre de sécurité **&** conformité et membre du groupe de rôles Gestion de l’organisation dans **Exchange Online**.  
  - Pour accéder en lecture seule à la stratégie de remise  avancée,  vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité.

  Pour plus d’informations, [voir Autorisations](permissions-in-the-security-and-compliance-center.md) dans le Centre de sécurité & conformité et [autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo).

## <a name="use-the-security--compliance-center-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Utiliser le Centre de sécurité & conformité pour configurer des simulations d’hameçonnage tiers dans la stratégie de remise avancée

1. Dans le Centre de sécurité & conformité, allez à **La** remise avancée des stratégies de gestion \>  \> **des menaces.**

2. Dans la page **Remise avancée,** sélectionnez l’onglet **Simulation** de hameçonnage, puis cliquez sur **Modifier.**

3. Dans le volant de simulation de **hameçonnage** tiers qui s’ouvre, configurez les paramètres suivants :

   - **Domaine d’envoi**: au moins un domaine d’adresse de messagerie est requis (par exemple, contoso.com). Vous pouvez ajouter jusqu’à 10 entrées.
   - **Adresse IP d’envoi**: au moins une adresse IPv4 valide est requise. Vous pouvez ajouter jusqu’à 10 entrées. Les valeurs valides sont les suivantes :
     - Adresse IP unique : par exemple, 192.168.1.1.
     - Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.
     - ADRESSE IP CIDR : par exemple, 192.168.0.1/25.
   - **URL de** simulation à autoriser : vous pouvez éventuellement entrer des URL spécifiques qui font partie de votre campagne de simulation de hameçonnage qui ne doivent pas être bloquées ou détonées. Vous pouvez ajouter jusqu’à 10 entrées.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer.**

Les entrées de simulation de hameçonnage tierces que vous avez configurées sont affichées sous l’onglet **Simulation de hameçonnage.** Pour apporter des modifications, cliquez **sur Modifier** sous l’onglet.

## <a name="use-the-security--compliance-center-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>Utiliser le Centre de sécurité & conformité pour configurer les boîtes aux lettres SecOps dans la stratégie de remise avancée

1. Dans le Centre de sécurité & conformité, go to **Threat Management** \> **Policy** \> **Advanced delivery**.

2. Dans la page **Remise avancée,** sélectionnez l’onglet Boîte aux lettres **SecOps,** puis cliquez sur **Modifier.**

3. Dans le volant de boîte aux lettres **SecOps** qui s’ouvre, entrez les adresses de messagerie des boîtes aux lettres Exchange Online existantes que vous souhaitez désigner comme boîtes aux lettres SecOps. Les groupes de distribution ne sont pas autorisés.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

Les entrées de boîte aux lettres SecOps que vous avez configurées sont affichées sous l’onglet Boîte aux lettres **SecOps.** Pour apporter des modifications, cliquez **sur Modifier** sous l’onglet.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>Scénarios supplémentaires nécessitant le contournement du filtrage

Outre les deux scénarios que la stratégie de remise avancée peut vous aider, il existe d’autres scénarios qui peuvent nécessiter que vous contourniez le filtrage :

- **Filtres tiers**: si l’enregistrement MX de votre domaine ne pointe pas vers Office 365 (les messages sont d’abord acheminés [ailleurs),](secure-by-default.md) la sécurité par défaut *n’est* *pas disponible.*

  Pour contourner le filtrage Microsoft pour les messages qui ont déjà été évalués par un filtrage tiers, utilisez des règles de flux de messagerie (également appelées règles de transport), voir Utiliser des règles de flux de messagerie pour définir le SCL dans les [messages.](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md)

- **Faux positifs** en cours d’examen : vous souhaitez peut-être autoriser temporairement certains messages en cours d’analyse par Microsoft via des [envois](admin-submission.md) d’administrateur à signaler les messages de bonne qualité connus qui sont marqués à tort comme incorrects pour Microsoft (faux positifs). Comme pour toutes les substitutions, il est vivement recommandé **_d’annuler_** temporairement ces allocations.
