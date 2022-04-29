---
title: Insights sur les flux de courrier dans le tableau de bord flux de courrier
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: beb6acaa-6016-4d54-ba7e-3d6d035e2b46
description: Les administrateurs peuvent en savoir plus sur les insights et les rapports disponibles dans le tableau de bord de flux de courrier du Centre de sécurité & conformité.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: eef35eedd5a7f182160b9a6a8b27a59cf9cdd9c0
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129175"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>Informations sur le flux de messagerie dans le centre de sécurité et conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les administrateurs peuvent utiliser le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité pour découvrir les tendances, les insights et prendre des mesures pour résoudre les problèmes liés au flux de courrier dans leur organisation.

:::image type="content" source="../../media/mail-flow-dashboard-v2.png" alt-text="Tableau de bord de flux de courrier dans le Centre de sécurité & conformité" lightbox="../../media/mail-flow-dashboard-v2.png":::

Les insights disponibles sont les suivants :

- [Aperçu des messages transférés automatiquement](mfi-auto-forwarded-messages-report.md)

- [Corriger les insights de boucle de messagerie](mfi-mail-loop-insight.md) <sup>possibles1</sup>

- [Correction des règles de flux de courrier lent insight1](mfi-slow-mail-flow-rules-insight.md)<sup></sup>

- [Carte du flux de messagerie](mfi-mail-flow-map-report.md)

- [Nouveaux domaines transférés par e-mail Insight2](mfi-new-domains-being-forwarded-email.md)<sup></sup>

- [Nouveaux utilisateurs transférant email insight2](mfi-new-users-forwarding-email.md)<sup></sup>

- [Rapport de domaine non accepté](mfi-non-accepted-domain-report.md)

- [Rapport de non-remise](mfi-non-delivery-report.md)

- [Informations sur le flux de courrier entrant et sortant](mfi-outbound-and-inbound-mail-flow.md)

- [Informations sur les files d’attente](mfi-queue-alerts-and-queues.md)

- [Informations et rapports sur les clients SMTP AUTH](mfi-smtp-auth-clients-report.md)

- [Informations sur l’état du flux de courrier des principaux domaines](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> Cet aperçu s’affiche dans la zone **Recommandé pour vous** du tableau de bord de flux de courrier uniquement après la détection du problème. Sinon, vous ne le verrez pas.

<sup>2</sup> Cet aperçu n’apparaît pas dans le tableau de bord de flux de courrier, mais il est visible sur la page du [rapport de transfert](view-mail-flow-reports.md#forwarding-report) une fois le problème détecté. Sinon, vous ne le verrez pas.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>Autorisations requises pour afficher le tableau de bord de flux de courrier

Le tableau de bord de flux de messagerie est disponible pour les membres des groupes de rôles suivants :

- **Gestion de l’organisation** dans le Centre de sécurité & conformité (administrateurs généraux).

- **[administrateur Exchange](/azure/active-directory/roles/permissions-reference#exchange-administrator)** dans Azure Active Directory.

- **Administrateur MailFlow** dans le Centre de sécurité & conformité. Si le compte n’est pas également membre des groupes de rôles Gestion de l’organisation ou administrateur Exchange, tenez compte des problèmes suivants :
  - L’utilisateur doit se connecter au Centre de sécurité & conformité directement à l’adresse <https://protection.office.com>.
  - L’utilisateur dispose uniquement d’une autorisation en lecture seule sur le tableau de bord de flux de courrier.
  - L’utilisateur n’a pas accès à la Centre d'administration Microsoft 365.

Pour plus d’informations sur les autorisations, consultez [Autorisations dans le Centre de sécurité & conformité](permissions-in-the-security-and-compliance-center.md) et [Autoriser les utilisateurs à accéder au Centre de sécurité & conformité](grant-access-to-the-security-and-compliance-center.md).

## <a name="where-to-find-the-mail-flow-dashboard"></a>Où trouver le tableau de bord de flux de courrier

Ouvrez le Centre de sécurité & conformité à l’adresse <https://protection.office.com>, développez **le flux de courrier**, puis sélectionnez **Tableau de bord**.

Pour accéder directement au tableau de bord de flux de courrier, ouvrez <https://protection.office.com/mailflow/dashboard>.
