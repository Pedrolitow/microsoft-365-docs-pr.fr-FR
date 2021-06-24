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
ms.openlocfilehash: 819f78883aa75fbbdded2e47c1bb85945f080233
ms.sourcegitcommit: ebb1c3b4d94058a58344317beb9475c8a2eae9a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2021
ms.locfileid: "53108402"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>Configurer la remise de simulations de hameçonnage tiers aux utilisateurs et de messages non filtrés dans des boîtes aux lettres SecOps

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> La fonctionnalité décrite dans cet article est en prévisualisation, n’est pas disponible pour tout le monde et peut faire l’objet de changements.

Pour sécuriser votre organisation par [défaut,](secure-by-default.md)Exchange Online Protection (EOP) n’autorise pas les listes sécurisées ou le contournement de filtrage pour les messages identifiés comme programmes malveillants ou hameçonnage à haut niveau de confiance. Toutefois, il existe des scénarios spécifiques qui nécessitent la remise de messages non filtrés. Par exemple :

- **Simulations de hameçonnage tierces**: les attaques simulées peuvent vous aider à identifier les utilisateurs vulnérables avant qu’une attaque réelle n’impacte votre organisation.
- Boîtes aux lettres d’opérations de sécurité **(SecOps)**: boîtes aux lettres dédiées utilisées par les équipes de sécurité pour collecter et analyser les messages non filtrés (bonnes et mauvaises).

Vous utilisez la _stratégie de remise_ avancée dans Microsoft 365 pour empêcher le filtrage de ces messages dans ces _scénarios spécifiques._ <sup>\*</sup> La stratégie de remise avancée garantit que les messages dans ces scénarios atteignent les résultats suivants :

- Les filtres dans EOP et Microsoft Defender Office 365 aucune action sur ces messages.<sup>\*</sup>
- [La purge zéro heure (ZAP) pour](zero-hour-auto-purge.md) le courrier indésirable et le hameçonnage n’a aucune action sur ces messages.<sup>\*</sup>
- [Les alertes système par](alerts.md) défaut ne sont pas déclenchées pour ces scénarios.
- [Air and clustering in Defender for Office 365](office-365-air.md) ignores these messages.
- Plus spécifiquement pour les simulations de hameçonnage tierces :
  - [Les soumissions d’administrateur](admin-submission.md) génèrent une réponse automatique qui dit que le message fait partie d’une campagne de simulation de hameçonnage et qu’il ne constitue pas une menace réelle. Les alertes et AIR ne sont pas déclenchées.
  - [Coffre liens dans Defender pour Office 365](safe-links.md) ne bloque pas ou ne désaxique pas les URL spécifiquement identifiées dans ces messages.
  - [Coffre pièces jointes dans Defender Office 365](safe-attachments.md) les pièces jointes de ces messages ne sont pas détonation.

<sup>\*</sup> Vous ne pouvez pas contourner le filtrage des programmes malveillants ou zap pour les programmes malveillants.

Les messages identifiés par la stratégie de remise avancée ne sont pas des menaces de sécurité. Les messages sont donc marqués comme étant des remplacements système. Les administrateurs peuvent filtrer et analyser ces substitutions système dans les expériences suivantes :

- [Détections de l’Explorateur de menaces/En temps réel dans Defender Office 365 plan 2](threat-explorer.md)
- Page [Entité de messagerie dans l’Explorateur de menaces/Détections en temps réel](mdo-email-entity-page.md)
- Rapport [d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Recherche avancée dans Microsoft Defender pour point de terminaison](../defender-endpoint/advanced-hunting-overview.md)
- [Vues de campagne](campaigns.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour aller directement à la page **de remise avancée,** ouvrez <https://security.microsoft.com/advanceddelivery> .

- Des autorisations doivent vous être attribuées avant de pouvoir suivre les procédures de cet article :
  - Pour créer, modifier ou supprimer des paramètres configurés dans la stratégie  de remise avancée, vous devez être membre du  groupe de rôles Administrateur de la sécurité dans le portail **Microsoft 365 Defender** et membre du groupe de rôles Gestion de l’organisation **dans Exchange Online**.  
  - Pour un accès en lecture seule à la stratégie de  remise  avancée, vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité.

  Pour plus d’informations, [voir Autorisations dans le portail Microsoft 365 Defender et](permissions-microsoft-365-security-center.md) [autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > L’ajout d’utilisateurs au rôle Azure Active Directory leur donne les autorisations  requises dans le portail Microsoft 365 Defender et les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>Utiliser le portail Microsoft 365 Defender pour configurer les boîtes aux lettres SecOps dans la stratégie de remise avancée

1. In the Microsoft 365 Defender portal, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** page \> **Rules** section \> **Advanced delivery**.

2. Dans la page **Remise** avancée, vérifiez que l’onglet Boîte aux lettres **SecOps** est sélectionné, puis faites l’une des étapes suivantes :
   - Cliquez sur ![ Modifier ](../../media/m365-cc-sc-edit-icon.png) **l’icône Modifier.**
   - S’il n’existe aucune simulation de hameçonnage configurée, cliquez sur **Ajouter.**

3. Dans le volant modifier les boîtes aux lettres **SecOps** qui s’ouvre, entrez une boîte aux lettres Exchange Online existante que vous souhaitez désigner comme boîte aux lettres SecOps en suivant l’une des étapes suivantes :
   - Cliquez dans la zone, laissez la liste des boîtes aux lettres résoudre, puis sélectionnez la boîte aux lettres.
   - Cliquez dans la zone commencer à taper un identificateur pour la boîte aux lettres (nom, nom complet, alias, adresse e-mail, nom du compte, etc.), puis sélectionnez la boîte aux lettres (nom complet) dans les résultats.

     Répétez cette étape autant de fois que nécessaire. Les groupes de distribution ne sont pas autorisés.

     Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Suppression](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

Les entrées de boîte aux lettres SecOps que vous avez configurées sont affichées sous l’onglet Boîte aux lettres **SecOps.** Pour apporter des modifications, cliquez ![ sur Modifier ](../../media/m365-cc-sc-edit-icon.png) **l’icône Modifier** sous l’onglet.

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Utiliser le portail Microsoft 365 Defender pour configurer des simulations de hameçonnage tiers dans la stratégie de remise avancée

1. In the Microsoft 365 Defender portal, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** page \> **Rules** section \> **Advanced delivery**.

2. Dans la page **Remise avancée,** sélectionnez l’onglet **Simulation** de hameçonnage, puis faites l’une des étapes suivantes :
   - Cliquez sur ![ Modifier ](../../media/m365-cc-sc-edit-icon.png) **l’icône Modifier.**
   - S’il n’existe aucune simulation de hameçonnage configurée, cliquez sur **Ajouter.**

3. Dans le **flyout de simulation** de hameçonnage tiers qui s’ouvre, configurez les paramètres suivants :

   - **Domaine** d’envoi : développez ce paramètre et entrez au moins un domaine d’adresse de messagerie (par exemple, contoso.com) en cliquant dans la zone, en entrant une valeur, puis en appuyant sur Entrée ou en sélectionnant la valeur affichée sous la zone. Répétez cette étape autant de fois que nécessaire. Vous pouvez ajouter jusqu’à 10 entrées.
   - **Adresse IP** d’envoi : développez ce paramètre et entrez au moins une adresse IPv4 valide en cliquant dans la zone, en entrant une valeur, puis en appuyant sur Entrée ou en sélectionnant la valeur affichée sous la zone. Répétez cette étape autant de fois que nécessaire. Vous pouvez ajouter jusqu’à 10 entrées. Les valeurs valides sont les suivantes :
     - Adresse IP unique : par exemple, 192.168.1.1.
     - Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.
     - ADRESSE IP CIDR : par exemple, 192.168.0.1/25.
   - **URL** de simulation pour autoriser : développez ce paramètre et entrez éventuellement des URL spécifiques qui font partie de votre campagne de simulation de hameçonnage qui ne doivent pas être bloquées ou détonées en cliquant dans la zone, en entrant une valeur, puis en appuyant sur Entrée ou en sélectionnant la valeur qui s’affiche sous la zone. Vous pouvez ajouter jusqu’à 10 entrées.

   Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Suppression](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

4. Lorsque vous avez terminé, faites l’une des étapes suivantes :
   - **Première fois**: cliquez **sur Ajouter,** puis sur **Fermer.**
   - **Modifier une version existante**: cliquez sur **Enregistrer,** puis sur **Fermer.**

Les entrées de simulation de hameçonnage tierces que vous avez configurées sont affichées sous l’onglet **Simulation de hameçonnage.** Pour apporter des modifications, cliquez ![ sur Modifier ](../../media/m365-cc-sc-edit-icon.png) **l’icône Modifier** sous l’onglet.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>Scénarios supplémentaires nécessitant le contournement du filtrage

Outre les deux scénarios que la stratégie de remise avancée peut vous aider, il existe d’autres scénarios qui peuvent nécessiter que vous contourniez le filtrage :

- **Filtres tiers**: si l’enregistrement MX de votre domaine ne pointe pas vers Office 365 (les messages sont d’abord acheminés [ailleurs),](secure-by-default.md) la sécurité par défaut *n’est* *pas disponible.*

  Pour contourner le filtrage Microsoft pour les messages qui ont déjà été évalués par un filtrage tiers, utilisez des règles de flux de messagerie (également appelées règles de transport). Pour plus d’informations, voir [Utiliser des règles de flux de messagerie pour définir le SCL dans les messages.](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl.md)

- **Faux positifs** en cours d’examen : vous souhaitez peut-être autoriser temporairement certains messages en cours d’analyse par Microsoft via des [envois](admin-submission.md) d’administrateur à signaler les messages de bonne qualité connus qui sont marqués à tort comme incorrects pour Microsoft (faux positifs). Comme pour toutes les substitutions, il est **_vivement_** recommandé que ces allocations soient temporaires.
