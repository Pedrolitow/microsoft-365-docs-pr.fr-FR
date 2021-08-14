---
title: Informations sur le flux de messagerie dans le tableau de bord flux de messagerie
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
audience: ITPro
ms.topic: overview
localization_priority: Normal
ms.assetid: beb6acaa-6016-4d54-ba7e-3d6d035e2b46
description: Les administrateurs peuvent en savoir plus sur les informations et les rapports disponibles dans le tableau de bord de flux de messagerie du Centre de sécurité & conformité.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7b38bb50bd72ea3391cd908e6e058e050003a17b41777df9d8d2663a50977904
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "56852517"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>Informations sur le flux de courriers dans le Centre de sécurité et de conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les administrateurs peuvent utiliser le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité pour découvrir les tendances, les informations et prendre des mesures pour résoudre les problèmes liés au flux de messagerie dans leur organisation.

![Tableau de bord flux de messagerie dans le Centre de sécurité & conformité](../../media/mail-flow-dashboard-v2.png)

Les informations disponibles sont les :

- [Aperçu des messages transférés automatiquement](mfi-auto-forwarded-messages-report.md)

- [Résoudre les problèmes de boucle de courrier 1](mfi-mail-loop-insight.md)<sup></sup>

- [Corriger les règles de flux de messagerie lentes Insight](mfi-slow-mail-flow-rules-insight.md)<sup>1</sup>

- [Carte du flux de courriers](mfi-mail-flow-map-report.md)

- [Nouveaux domaines en cours de forwarded email insight](mfi-new-domains-being-forwarded-email.md)<sup>2</sup>

- [Nouveaux utilisateurs qui envoient des informations sur le courrier](mfi-new-users-forwarding-email.md)électronique<sup>2</sup>

- [Rapport de domaine non accepté](mfi-non-accepted-domain-report.md)

- [Rapport de non-remise](mfi-non-delivery-report.md)

- [Informations sur le flux de courrier entrant et sortant](mfi-outbound-and-inbound-mail-flow.md)

- [Aperçu des files d’attente](mfi-queue-alerts-and-queues.md)

- [Aperçu et rapport sur les clients utilisant l’authentification SMTP](mfi-smtp-auth-clients-report.md)

- [Informations sur l’état du flux de courrier des principaux domaines](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> Cette information apparaît dans la zone **Recommandé** pour vous du tableau de bord de flux de messagerie uniquement après la détection du problème. Sinon, vous ne le verrez pas.

<sup>2</sup> Cette information n’apparaît pas dans le tableau de bord de flux de messagerie, mais elle est visible dans la [page](view-mail-flow-reports.md#forwarding-report) du rapport de forwarding une fois le problème détecté. Sinon, vous ne le verrez pas.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>Autorisations requises pour afficher le tableau de bord de flux de messagerie

Le tableau de bord de flux de messagerie est disponible pour les membres des groupes de rôles suivants :

- **Gestion de l’organisation** dans le Centre de sécurité & conformité (administrateurs globaux).

- **[Exchange administrateur dans](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#exchange-administrator)** Azure Active Directory.

- **Administrateur de flux de** messagerie dans le Centre de sécurité & conformité. Si le compte n’est pas également membre des groupes de rôles Gestion de l’organisation ou Administrateur Exchange, prenons en compte les problèmes suivants :
  - L’utilisateur doit se connecter au Centre de sécurité & conformité directement sur <https://protection.office.com> .
  - L’utilisateur aura uniquement une autorisation en lecture seule sur le tableau de bord de flux de messagerie.
  - L’utilisateur n’aura pas accès au Centre d’administration Microsoft 365.

Pour plus d’informations sur les [autorisations,](permissions-in-the-security-and-compliance-center.md) voir Autorisations dans le Centre de sécurité & conformité et autoriser les utilisateurs à accéder au Centre de sécurité [& conformité.](grant-access-to-the-security-and-compliance-center.md)

## <a name="where-to-find-the-mail-flow-dashboard"></a>Où trouver le tableau de bord de flux de messagerie

Ouvrez le Centre de sécurité & conformité à l’adresse , développez flux de <https://protection.office.com> **messagerie,** puis sélectionnez Tableau de **bord.**

Pour aller directement au tableau de bord de flux de messagerie, ouvrez <https://protection.office.com/mailflow/dashboard> .