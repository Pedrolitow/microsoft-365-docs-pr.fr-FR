---
title: Création de rapports et suivi des messages
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
localization_priority: Normal
ms.assetid: f40253f2-50a1-426e-9979-be74ba74cb61
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous allez découvrir les rapports et les outils de dépannage disponibles pour les administrateurs Microsoft Exchange Online Protection des données (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ae55ded9d907754161813c9f7bfa7eeb14c558a8
ms.sourcegitcommit: 686f192e1a650ec805fe8e908b46ca51771ed41f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52625028"
---
# <a name="reporting-and-message-trace-in-eop"></a>Rapports et suivi des messages dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres en Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, EOP propose de nombreux rapports différents qui peuvent vous aider à déterminer l’état général et l’état de votre organisation. Il existe également des outils vous permettant de résoudre des problèmes liés à des événements spécifiques (comme un message n'arrivant pas aux destinataires appropriés) et des rapports d'audit pour vous aider à respecter les exigences de conformité.

## <a name="usage-reports"></a>Rapports d’utilisation

**Microsoft 365 groupes :** afficher des informations sur le nombre de groupes Microsoft 365 créés et utilisés.

**Activité de messagerie**: afficher des informations sur le nombre de messages envoyés, reçus et lus dans toute votre organisation, et par des utilisateurs spécifiques.

**Utilisation de l’application de messagerie**: afficher des informations sur les applications de messagerie utilisées. Ceci inclut le nombre total de connexions pour chaque application et les versions de Outlook qui se connectent.

**Utilisation des boîtes aux** lettres : afficher les informations sur le stockage utilisé, la consommation de quota, le nombre d’éléments et la dernière activité (activité d’envoi ou de lecture) pour les boîtes aux lettres.

Pour plus d'informations, consultez les ressources suivantes :

- [Microsoft 365 Rapports dans le Centre d’administration : Microsoft 365 groupes](../../admin/activity-reports/office-365-groups.md)

- [Microsoft 365 Rapports dans le Centre d’administration - Activité de messagerie](../../admin/activity-reports/email-activity.md)

- [Microsoft 365 Rapports dans le Centre d’administration - Utilisation des applications de messagerie](../../admin/activity-reports/email-apps-usage.md)

- [Microsoft 365 Rapports dans le Centre d’administration - Utilisation des boîtes aux lettres](../../admin/activity-reports/mailbox-usage.md)

## <a name="security--compliance-reports-in-the-microsoft-365-admin-center"></a>Rapports de conformité & sécurité dans le Centre d’administration Microsoft 365 de sécurité

Ces rapports améliorés offrent une expérience de rapport interactive pour les administrateurs EOP, qui inclut des informations récapitulatifs et la possibilité d’obtenir plus de détails.

**Defender pour Office 365**: afficher des informations sur les liens sécurisés et les pièces jointes sécurisées qui font partie de Microsoft Defender pour Office 365.

**EOP**: afficher des informations sur les détections de programmes malveillants, les messages usurpés, les détections de courrier indésirable et le flux de messagerie vers et depuis votre organisation.

[Afficher des rapports pour Defender pour Office 365](view-reports-for-mdo.md)

## <a name="custom-reports-using-microsoft-graph"></a>Rapports personnalisés à l’aide de Microsoft Graph

Créez par programme des rapports disponibles dans le Centre d’administration à l’aide de Microsoft Graph. Pour plus d’informations, voir [Vue d’ensemble](/graph/overview) de Microsoft Graph et utilisation des rapports [Office 365'utilisation dans Microsoft Graph](/graph/api/resources/report).

## <a name="message-trace"></a>Suivi des messages

Suit les messages électroniques pendant qu'ils circulent dans EOP. Vous pouvez déterminer si un message électronique a été reçu, rejeté, différé ou remis par le service. Cela indique également les actions entamées par rapport au message avant qu'il atteigne son statut final.

Vous pouvez ainsi répondre efficacement aux questions de vos utilisateurs, résoudre les problèmes de flux de messagerie et valider les modifications de stratégie, tout en réduisant la nécessité de demander de l'aide à l'assistance technique.

Voir [suivi des messages dans le Centre de sécurité & conformité.](message-trace-scc.md)

## <a name="audit-logging"></a>Journalisation d'audit

Effectue le suivi des modifications spécifiques apportées par les administrateurs à votre organisation. Ces rapports peuvent vous aider à résoudre les problèmes de configuration ou à trouver la cause des problèmes de sécurité ou de conformité. Consultez [les rapports d’audit dans Exchange Online](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports).

## <a name="reporting-and-message-trace-data-availability-and-latency"></a>Disponibilité et latence des rapports et des données de suivi des messages

Le tableau suivant présente la disponibilité des rapports et des données de suivi des messages EOP, ainsi que leur latence.

****

|Type de rapport|Données disponibles pendant (période rétrospective)|Latence|
|---|---|---|
|Rapports récapitulatifs sur la protection du courrier électronique|90 jours|L'agrégation quasi-complète des données des messages dure entre 24 et 48 heures. Des modifications agrégées incrémentielles mineures peuvent se produire jusqu'à 5 jours.|
|Rapports détaillés sur la protection du courrier électronique|90 jours|Pour les messages de moins de 7 jours, les données détaillées apparaissent normalement dans les 24 heures, mais leur génération peut durer jusqu'à 48 heures. Il est possible que des modifications incrémentielles mineures soient apportées pendant 5 jours. <p> Pour les messages remontant à plus de sept jours, la génération des résultats détaillés peut prendre plusieurs heures.|
|Données de suivi des messages|90 jours|Lorsque vous effectuez un suivi de messages remontant à moins de 7 jours, ces derniers apparaissent normalement dans les 5 à 30 minutes.<p> Lorsque vous effectuez un suivi de messages remontant à plus de 7 jours, la génération des résultats peut prendre plusieurs heures.|
|

> [!NOTE]
> La disponibilité et la latence des données sont les mêmes, qu’elles soient demandées via le Centre d’administration ou PowerShell à distance.