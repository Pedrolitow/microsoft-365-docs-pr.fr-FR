---
title: Informations sur le flux de messagerie dans le tableau de bord de flux de messagerie
f1.keywords:
- NOCSH
ms.author: siosulli
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: beb6acaa-6016-4d54-ba7e-3d6d035e2b46
description: Les administrateurs peuvent en savoir plus sur les informations et les rapports disponibles dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f7781dca48e1eae4716dbe6c7c3b40da4bae0cd8
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48920007"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>Informations sur le flux de courriers dans le Centre de sécurité et de conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Les administrateurs peuvent utiliser le tableau de bord de flux de messagerie dans le centre de sécurité & conformité pour découvrir des tendances, des informations et prendre des mesures pour résoudre les problèmes liés au flux de messagerie au sein de leur organisation.

![Tableau de bord de flux de messagerie dans le centre de sécurité & conformité](../../media/mail-flow-dashboard-v2.png)

Les informations disponibles sont les suivantes :

- [Aperçu des messages transférés automatiquement](mfi-auto-forwarded-messages-report.md)

- [Correction possible de mail Loop Insight](mfi-mail-loop-insight.md)<sup>1</sup>

- [Corriger le ralentissement des règles de flux de messagerie Insight](mfi-slow-mail-flow-rules-insight.md)<sup>1</sup>

- [Carte du flux de courriers](mfi-mail-flow-map-report.md)

- [Nouveaux domaines transmis par email Insight](mfi-new-domains-being-forwarded-email.md)<sup>2</sup>

- [Nouveaux utilisateurs transfert de courriers électroniques Insight](mfi-new-users-forwarding-email.md)<sup>2</sup>

- [Rapport de domaine non accepté](mfi-non-accepted-domain-report.md)

- [Rapport de non-remise](mfi-non-delivery-report.md)

- [Informations sur le flux de courrier entrant et sortant](mfi-outbound-and-inbound-mail-flow.md)

- [Aperçu des files d’attente](mfi-queue-alerts-and-queues.md)

- [Aperçu et rapport sur les clients utilisant l’authentification SMTP](mfi-smtp-auth-clients-report.md)

- [Informations sur l’état du flux de courrier des principaux domaines](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> cette vue s’affiche dans la zone **recommandé pour vous** du tableau de bord du flux de messagerie uniquement une fois que le problème a été détecté. Dans le cas contraire, vous ne le verrez pas.

<sup>2</sup> cette vue n’apparaît pas sur le tableau de bord de flux de messagerie, mais sur la page [rapport de transfert](view-mail-flow-reports.md#forwarding-report) une fois que le problème est détecté. Dans le cas contraire, vous ne le verrez pas.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>Autorisations requises pour afficher le tableau de bord de flux de messagerie

Le tableau de bord de flux de messagerie est disponible pour les membres des groupes de rôles suivants :

- **Gestion** de l’organisation dans le centre de sécurité & conformité (administrateurs globaux).

- **[Administrateur Exchange](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#exchange-administrator)** dans Azure Active Directory.

- **Administrateur de flux** de service dans le centre de sécurité & conformité. Si le compte n’est pas également membre du groupe de rôles gestion de l’organisation ou administrateur Exchange, prenez en compte les points suivants :
  - L’utilisateur doit se connecter au centre de sécurité & conformité directement à l’adresse <https://protection.office.com> .
  - L’utilisateur disposera uniquement de l’autorisation lecture seule sur le tableau de bord du flux de messagerie.
  - L’utilisateur n’a pas accès au centre d’administration Microsoft 365.

Pour plus d’informations sur les autorisations, consultez [la rubrique autorisations dans le centre de sécurité & conformité](permissions-in-the-security-and-compliance-center.md) et [accordez aux utilisateurs l’accès au centre de sécurité & conformité](grant-access-to-the-security-and-compliance-center.md).

## <a name="where-to-find-the-mail-flow-dashboard"></a>Où trouver le tableau de bord de flux de messagerie ?

Ouvrez le centre de sécurité & conformité à l’adresse <https://protection.office.com> , développez **flux de messagerie** , puis sélectionnez **tableau de bord**.

Pour accéder directement au tableau de bord du flux de messagerie, ouvrez <https://protection.office.com/mailflow/dashboard> .
