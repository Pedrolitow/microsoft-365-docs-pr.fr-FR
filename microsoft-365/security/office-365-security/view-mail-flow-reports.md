---
title: Afficher les rapports de flux de messagerie dans le tableau de bord Rapports
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur les rapports de flux de messagerie disponibles dans le tableau de bord Rapports du Centre de sécurité & conformité.
ms.custom: ''
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1b73410170b0a869010f0c0c40b9363eed7475e6
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61370902"
---
# <a name="view-mail-flow-reports-in-the-reports-dashboard-in-security--compliance-center"></a>Afficher les rapports de flux de messagerie dans le tableau de bord Rapports du Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> La plupart des rapports de cet article sont également disponibles dans le portail Microsoft 365 Defender ou le Centre d’administration Exchange (EAC). Pour plus d’informations, voir les rubriques suivantes :
>
> - [Rapports de flux de messagerie dans le nouveau centre Exchange’administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports)
> - [Afficher les rapports de sécurité du courrier dans le portail Microsoft 365 Defender messagerie](view-email-security-reports.md)

Outre les rapports de flux de [](mail-flow-insights-v2.md) messagerie disponibles dans le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité, plusieurs rapports de flux de messagerie supplémentaires sont disponibles dans le tableau de bord Rapports pour vous aider à surveiller votre organisation Microsoft 365.

Si vous avez les [autorisations](#what-permissions-are-needed-to-view-these-reports)nécessaires, vous pouvez afficher ces rapports dans le Centre de sécurité & conformité en allant au Tableau de <https://protection.office.com> bord **des** \> **rapports.** Pour aller directement au tableau de bord Rapports, ouvrez <https://protection.office.com/insightdashboard> .

![Tableau de bord Rapports dans le Centre de sécurité & conformité.](../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png)

## <a name="connector-report"></a>Rapport sur le connecteur

> [!NOTE]
> Ce rapport a été remplacé par le rapport **Messages** entrants et le rapport **Messages sortants** dans le EAC. Pour plus d’informations, voir messages entrants et rapports de [messages sortants dans le nouveau EAC.](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports)

## <a name="exchange-transport-rule-report"></a>Exchange de règles de transport

Le Exchange de règles de **transport** de messagerie affiche l’effet des règles de flux de messagerie (également appelées règles de transport) sur les messages entrants et sortants dans votre organisation.

Pour afficher le rapport, ouvrez le Centre de sécurité & conformité à l’Exchange, puis sélectionnez La <https://protection.office.com>  \>  règle **de transport.** Pour aller directement dans le rapport, ouvrez <https://security.microsoft.com/reports/ETRRuleReport> .

![Exchange widget de règle de transport dans le tableau de bord Rapports.](../../media/scc-transport-rule-report-widget.png)

> [!NOTE]
> Cliquer sur le widget pour ce rapport dans le Centre de sécurité & conformité (protection.office.com) vous permet désormais d’obtenir le rapport complet dans le portail Microsoft 365 Defender (security.microsoft.com). Pour plus d’informations sur le rapport, voir [Exchange de règles de transport.](view-email-security-reports.md#exchange-transport-rule-report)

## <a name="forwarding-report"></a>Rapport de forwarding

> [!NOTE]
> Le **rapport de forwarding** est désormais disponible dans le EAC. Pour plus d’informations, [reportez-vous au](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report)rapport des messages transmis automatiquement dans le nouveau EAC.

## <a name="mailflow-status-report"></a>Rapport d’état du flux de messagerie

Le **rapport d’état du** flux de messagerie est similaire au rapport de courrier électronique envoyé et reçu, avec des informations supplémentaires sur le courrier électronique autorisé ou bloqué sur le edge. [](#sent-and-received-email-report) Il s’agit du seul rapport qui contient des informations sur la protection edge et qui indique la quantité de messages électroniques bloqués avant d’être autorisé dans le service pour évaluation par Exchange Online Protection (EOP). Il est important de comprendre que si un message est envoyé à cinq destinataires, nous le compterons comme cinq messages différents et pas un seul message.

Pour afficher le rapport, ouvrez le Centre de  sécurité [& conformité,](https://protection.office.com)allez au tableau de bord rapports et sélectionnez Rapport d’état du \>  flux **de messagerie.** Pour aller directement au rapport d’état du **flux de messagerie,** ouvrez <https://security.microsoft.com/reports/mailflowStatusReport> .

![Widget de rapport d’état du flux de messagerie dans le tableau de bord Rapports.](../../media/scc-mail-flow-status-report-widget.png)

> [!NOTE]
> Cliquer sur le widget pour ce rapport dans le Centre de sécurité & conformité (protection.office.com) vous permet désormais d’obtenir le rapport complet dans le portail Microsoft 365 Defender (security.microsoft.com). Pour plus d’informations sur le rapport, voir [Rapport d’état du flux de messagerie.](view-email-security-reports.md#mailflow-status-report)

## <a name="sent-and-received-email-report"></a>Rapport de courrier électronique envoyé et reçu

> [!NOTE]
> Ce rapport a été remplacé par le rapport [d’état du flux de messagerie.](#mailflow-status-report)

## <a name="top-senders-and-recipients-report"></a>Rapport sur les principaux expéditeurs et destinataires

Le **rapport Des principaux expéditeurs et destinataires** est un graphique en secteurs montrant vos principaux expéditeurs et destinataires de courrier électronique.

Pour afficher le rapport, ouvrez le Centre de  sécurité [& conformité,](https://protection.office.com)puis sélectionnez Tableau de bord des rapports et sélectionnez Principaux \>  **expéditeurs et destinataires.** Pour aller directement dans le rapport, ouvrez <https://protection.office.com/reportv2?id=TopSenderRecipientsATP> .

![Widget des principaux expéditeurs et destinataires dans le tableau de bord Rapports.](../../media/top-senders-and-recipients-widget.png)

### <a name="report-view-for-the-top-senders-and-recipient-report"></a>Affichage du rapport pour le rapport des principaux expéditeurs et destinataires

Les graphiques suivants sont disponibles dans l’affichage de rapport :

- **Afficher les données pour \> les principaux expéditeurs de courrier**
- **Afficher les données pour \> les principaux destinataires du courrier**
- **Afficher les données des \> principaux destinataires du courrier indésirable**
- **Afficher les données pour \> Principaux destinataires des programmes malveillants** (EOP)
- **Afficher les données \> des principaux destinataires de programmes malveillants (Defender pour Office 365)**

La composition du graphique en secteurs change en fonction de ces sélections.

Lorsque vous pointez sur une souris dans le graphique en secteurs, vous pouvez voir le nombre de messages envoyés ou reçus.

Si vous cliquez sur **Filtres** dans un affichage de rapport, vous pouvez spécifier une plage de dates avec la **date** de début et la **date de fin.**

![Graphique en secteurs en affichage Rapport dans le rapport Des principaux expéditeurs et destinataires.](../../media/top-senders-and-recipients-report-view.png)

### <a name="details-table-view-for-the-top-senders-and-recipient-report"></a>Vue de table Détails pour le rapport des principaux expéditeurs et destinataires

Si vous cliquez sur Afficher le tableau des **détails,** les informations affichées dépendent du graphique que vous regardiez :

- **Afficher les données pour \> les principaux expéditeurs de courrier**

  - **Principaux expéditeurs de courrier**
  - **Count**

- **Afficher les données pour \> les principaux destinataires du courrier**

  - **Principaux destinataires du courrier**
  - **Count**

- **Afficher les données des \> principaux destinataires du courrier indésirable**

  - **Principaux destinataires du courrier indésirable**
  - **Count**

- **Afficher les données pour \> Principaux destinataires des programmes malveillants** (EOP)

  - **Principaux destinataires de programmes malveillants**
  - **Count**

- **Afficher les données \> des principaux destinataires de programmes malveillants (Defender pour Office 365)**

  - **Principaux destinataires des programmes malveillants (Defender pour Office 365)**
  - **Count**

Si vous cliquez sur **Filtres** dans une vue de table de détails, vous pouvez spécifier une plage de dates avec la **date** de début et la **date de fin**.

Pour revenir à l’affichage du rapport, cliquez **sur Afficher le rapport.**

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Quelles autorisations sont nécessaires pour afficher ces rapports ?

Pour afficher et utiliser les rapports décrits dans cet article, vous devez être membre de l’un des groupes de rôles suivants dans le Centre de sécurité & conformité :

- **Gestion de l'organisation**
- **Administrateur de sécurité**
- **Lecteur de sécurité**
- **Lecteur général**

Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

> [!NOTE]
> L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le centre de sécurité et de conformité _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="related-topics"></a>Voir aussi

[Rapports intelligents et aperçus dans le Centre de sécurité et conformité](reports-and-insights-in-security-and-compliance.md)

[Informations sur le flux de messagerie dans le centre de sécurité et conformité](mail-flow-insights-v2.md)

[Afficher les rapports de sécurité de courrier dans le centre de sécurité et conformité](view-email-security-reports.md)

[Afficher les rapports de Microsoft Defender pour Office 365](view-reports-for-mdo.md)
