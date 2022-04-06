---
title: Informations sur le flux de messagerie dans le tableau de bord flux de messagerie
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
description: Les administrateurs peuvent en savoir plus sur les informations et les rapports disponibles dans le tableau de bord de flux de messagerie du Centre de sécurité & conformité.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b5cc3eba5807838b0a797f606d8a6aa3c152f60c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476464"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>Informations sur le flux de messagerie dans le centre de sécurité et conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les administrateurs peuvent utiliser le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité pour découvrir les tendances, les informations et prendre des mesures pour résoudre les problèmes liés au flux de messagerie dans leur organisation.

:::image type="content" source="../../media/mail-flow-dashboard-v2.png" alt-text="Tableau de bord flux de messagerie dans le Centre de sécurité & conformité" lightbox="../../media/mail-flow-dashboard-v2.png":::

Les informations disponibles sont les :

- [Aperçu des messages transférés automatiquement](mfi-auto-forwarded-messages-report.md)

- [Résoudre les problèmes de boucle de messagerie possibles1](mfi-mail-loop-insight.md)<sup></sup>

- [Corriger les règles de flux de messagerie lentes Insight1](mfi-slow-mail-flow-rules-insight.md)<sup></sup>

- [Carte du flux de messagerie](mfi-mail-flow-map-report.md)

- [Nouveaux domaines en cours de forwarded email insight2](mfi-new-domains-being-forwarded-email.md)<sup></sup>

- [Nouveaux utilisateurs qui ont transmis des informations sur les e-mails2](mfi-new-users-forwarding-email.md)<sup></sup>

- [Rapport de domaine non accepté](mfi-non-accepted-domain-report.md)

- [Rapport de non-remise](mfi-non-delivery-report.md)

- [Informations sur le flux de courrier entrant et sortant](mfi-outbound-and-inbound-mail-flow.md)

- [Informations sur les files d’attente](mfi-queue-alerts-and-queues.md)

- [Informations et rapports sur les clients SMTP AUTH](mfi-smtp-auth-clients-report.md)

- [Informations sur l’état du flux de courrier des principaux domaines](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> Cette information apparaît dans la zone **Recommandé** pour vous du tableau de bord de flux de messagerie uniquement après la détection du problème. Sinon, vous ne le verrez pas.

<sup>2</sup> Cette information n’apparaît pas dans le tableau de bord de flux de messagerie, mais elle est visible dans [la page du](view-mail-flow-reports.md#forwarding-report) rapport de forwarding une fois le problème détecté. Sinon, vous ne le verrez pas.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>Autorisations requises pour afficher le tableau de bord de flux de messagerie

Le tableau de bord de flux de messagerie est disponible pour les membres des groupes de rôles suivants :

- **Gestion de l’organisation** dans le Centre de sécurité & conformité (administrateurs globaux).

- **[Exchange administrateur dans](/azure/active-directory/roles/permissions-reference#exchange-administrator)** Azure Active Directory.

- **Administrateur de flux de** messagerie dans le Centre de sécurité & conformité. Si le compte n’est pas également membre des groupes de rôles Gestion de l’organisation ou Administrateur Exchange, prenons en compte les problèmes suivants :
  - L’utilisateur doit se connecter au Centre de sécurité & conformité directement à l’accueil.<https://protection.office.com>
  - L’utilisateur aura uniquement une autorisation en lecture seule sur le tableau de bord de flux de messagerie.
  - L’utilisateur n’aura pas accès au Centre d'administration Microsoft 365.

Pour plus d’informations sur les [autorisations, voir Autorisations](permissions-in-the-security-and-compliance-center.md) dans le Centre de sécurité & conformité et autoriser les utilisateurs à accéder au Centre de sécurité [& conformité](grant-access-to-the-security-and-compliance-center.md).

## <a name="where-to-find-the-mail-flow-dashboard"></a>Où trouver le tableau de bord de flux de messagerie

Ouvrez le Centre de sécurité & conformité <https://protection.office.com>à l’adresse , développez **le** flux de messagerie, puis sélectionnez **Tableau de bord**.

Pour aller directement au tableau de bord de flux de messagerie, ouvrez <https://protection.office.com/mailflow/dashboard>.