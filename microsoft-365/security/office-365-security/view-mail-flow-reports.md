---
title: Afficher les rapports de flux de courrier dans le tableau de bord Rapports
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
- m365-security
description: Les administrateurs peuvent en savoir plus sur les rapports de flux de courrier disponibles dans le tableau de bord Rapports du Centre de sécurité & conformité.
ms.custom: ''
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 81555650f71692864dc00abad9c65df883cf9955
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68048503"
---
# <a name="view-mail-flow-reports-in-the-reports-dashboard-in-security--compliance-center"></a>Afficher les rapports de flux de courrier dans le tableau de bord Rapports du Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> La plupart des rapports de cet article sont également disponibles dans le portail Microsoft 365 Defender ou dans le Centre d’administration Exchange (EAC). Pour plus d’informations, voir les rubriques suivantes :
>
> - [Rapports de flux de courrier dans le nouveau centre d’administration Exchange](/exchange/monitoring/mail-flow-reports/mail-flow-reports)
> - [Afficher les rapports de sécurité par e-mail dans le portail Microsoft 365 Defender](view-email-security-reports.md)

Outre les rapports de flux de courrier qui sont disponibles dans le [tableau de bord](mail-flow-insights-v2.md) flux de courrier du Centre de sécurité & conformité, divers rapports de flux de courrier supplémentaires sont disponibles dans le tableau de bord Rapports pour vous aider à surveiller votre organisation Microsoft 365.

Si vous disposez [des autorisations nécessaires](#what-permissions-are-needed-to-view-these-reports), vous pouvez afficher ces rapports dans le Centre de sécurité & conformité en accédant au <https://protection.office.com> **tableau de bord** **rapports**\>. Pour accéder directement au tableau de bord Rapports, ouvrez <https://protection.office.com/insightdashboard>.

:::image type="content" source="../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png" alt-text="Tableau de bord Rapports dans le Centre de sécurité & conformité" lightbox="../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png":::

## <a name="connector-report"></a>Rapport du connecteur

> [!NOTE]
> Ce rapport a été remplacé par le **rapport des messages entrants** et le **rapport des messages sortants** dans le CAE. Pour plus d’informations, consultez les [rapports des messages entrants et sortants dans le nouveau CENTRE](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports).

## <a name="exchange-transport-rule-report"></a>Rapport de règle de transport Exchange

Le rapport sur les **règles de transport Exchange** montre l’effet des règles de flux de courrier (également appelées règles de transport) sur les messages entrants et sortants de votre organisation.

Pour afficher le rapport, ouvrez le Centre de sécurité & conformité à <https://protection.office.com>l’adresse , accédez au **tableau de bord** **Rapports** \> et sélectionnez **la règle de transport Exchange**. Pour accéder directement au rapport, ouvrez <https://security.microsoft.com/reports/ETRRuleReport>.

:::image type="content" source="../../media/scc-transport-rule-report-widget.png" alt-text="Widget de règle de transport Exchange dans le tableau de bord Rapports" lightbox="../../media/scc-transport-rule-report-widget.png":::

> [!NOTE]
> Le **rapport de règle de transport Exchange** est désormais disponible dans le CENTRE. Pour plus d’informations, consultez [le rapport sur les règles de transport Exchange dans le nouveau CENTRE](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report).

## <a name="forwarding-report"></a>Rapport de transfert

> [!NOTE]
> Le **rapport de transfert** est maintenant disponible dans le CAE. Pour plus d’informations, consultez le [rapport des messages transférés automatiquement dans le nouveau CENTRE](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report).

## <a name="mailflow-status-report"></a>Rapport d’état du flux de courrier

Le **rapport d’état du flux** de courrier est similaire au [rapport d’e-mail envoyé et reçu](#sent-and-received-email-report), avec des informations supplémentaires sur les e-mails autorisés ou bloqués sur la périphérie. Il s’agit du seul rapport qui contient des informations de protection de périphérie et indique la quantité de courriers électroniques bloqués avant d’être autorisés dans le service pour évaluation par Exchange Online Protection (EOP). Il est important de comprendre que si un message est envoyé à cinq destinataires, nous le comptabilisons comme cinq messages différents et non comme un seul message.

Pour afficher le rapport, ouvrez le [Centre de sécurité & conformité](https://protection.office.com), accédez au **tableau de bord** **Rapports** \> et sélectionnez **Rapport d’état du flux de courrier**. Pour accéder directement au **rapport d’état du flux de** courrier, ouvrez <https://security.microsoft.com/reports/mailflowStatusReport>.

:::image type="content" source="../../media/scc-mail-flow-status-report-widget.png" alt-text="Widget rapport d’état du flux de courrier dans le tableau de bord Rapports" lightbox="../../media/scc-mail-flow-status-report-widget.png":::

> [!NOTE]
> Cliquez sur le widget de ce rapport dans le Centre de conformité & sécurité (protection.office.com) pour accéder au rapport complet dans le portail Microsoft 365 Defender (security.microsoft.com). Pour plus d’informations sur le rapport, consultez le [rapport d’état mailflow](view-email-security-reports.md#mailflow-status-report).

## <a name="sent-and-received-email-report"></a>Rapport d’e-mail envoyé et reçu

> [!NOTE]
> Ce rapport a été remplacé par le [rapport d’état mailflow](#mailflow-status-report).

## <a name="top-senders-and-recipients-report"></a>Rapport des principaux expéditeurs et destinataires

Les principaux **expéditeurs et destinataires** affichent les principaux expéditeurs de messages de votre organisation, ainsi que les principaux destinataires des messages détectés par EOP et les fonctionnalités de protection Defender pour Office 365.

Pour afficher le rapport, ouvrez le Centre de sécurité & conformité à l’adresse , accédez au <https://protection.office.com>**tableau de bord** **Rapports** \> et sélectionnez **Principaux expéditeurs et destinataires**. Pour accéder directement au rapport, ouvrez l’une des URL suivantes :

- Defender pour Office 365 :<https://protection.office.com/TopSenderRecipientsATP>
- EOP: <https://protection.office.com/TopSenderRecipients>

:::image type="content" source="../../media/scc-top-senders-and-recipients-widget.png" alt-text="Widget Principaux expéditeurs et destinataires dans le tableau de bord Rapports" lightbox="../../media/scc-top-senders-and-recipients-widget.png":::

> [!NOTE]
> Bien que le fait de cliquer sur le widget de ce rapport dans le Centre de sécurité & conformité vous dirige vers une page protection.office.com, le contenu de la page se trouve dans le portail Microsoft 365 Defender. Pour plus d’informations sur le rapport, consultez [le rapport Des expéditeurs et des destinataires supérieurs](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Quelles sont les autorisations nécessaires pour afficher ces rapports ?

Pour afficher et utiliser les rapports décrits dans cet article, vous devez être membre de l’un des groupes de rôles suivants dans le Centre de sécurité & conformité :

- **Gestion de l'organisation**
- **Administrateur de sécurité**
- **Lecteur de sécurité**
- **Lecteur général**

Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

> [!NOTE]
> L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le centre de sécurité et de conformité _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

