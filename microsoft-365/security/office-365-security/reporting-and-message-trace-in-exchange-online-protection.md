---
title: Création de rapports et suivi des messages
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: f40253f2-50a1-426e-9979-be74ba74cb61
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous découvrirez les rapports et les outils de dépannage disponibles pour les administrateurs de Microsoft Exchange Online Protection (EOP).
ms.openlocfilehash: af41f1d3b6ccc7632b392f58c36344239200f915
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44206441"
---
# <a name="reporting-and-message-trace-in-eop"></a>Création de rapports et suivi des messages dans EOP

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, EOP offre un grand nombre de rapports qui peuvent vous aider à déterminer l’état général et l’intégrité de votre organisation. Il existe également des outils vous permettant de résoudre des problèmes liés à des événements spécifiques (comme un message n'arrivant pas aux destinataires appropriés) et des rapports d'audit pour vous aider à respecter les exigences de conformité.

## <a name="usage-reports"></a>Rapports d’utilisation

**Activité des groupes microsoft 365**: afficher des informations sur le nombre de groupes Microsoft 365 créés et utilisés.

**Activité de messagerie**: afficher des informations sur le nombre de messages envoyés, reçus et lus dans l’ensemble de votre organisation, ainsi que sur des utilisateurs spécifiques.

**Utilisation**des applications de messagerie : Affichez des informations sur les applications de messagerie utilisées. Ceci inclut le nombre total de connexions pour chaque application et les versions de Outlook qui se connectent.

**Utilisation des boîtes aux lettres**: afficher des informations sur l’espace de stockage utilisé, la consommation de quota, le nombre d’éléments et la dernière activité (activité d’envoi ou de lecture) pour les boîtes aux lettres.

Pour plus d'informations, consultez les ressources suivantes :

- [Rapports Microsoft 365 dans le centre d’administration-groupes Microsoft 365](https://docs.microsoft.com/office365/admin/activity-reports/office-365-groups)

- [Rapports Microsoft 365 dans le centre d’administration-activité de courrier électronique](https://docs.microsoft.com/office365/admin/activity-reports/email-activity)

- [Rapports Microsoft 365 dans le centre d’administration-utilisation des applications de messagerie](https://docs.microsoft.com/office365/admin/activity-reports/email-apps-usage)

- [Rapports Microsoft 365 dans le centre d’administration-utilisation des boîtes aux lettres](https://docs.microsoft.com/office365/admin/activity-reports/mailbox-usage)

## <a name="security--compliance-reports-in-the-microsoft-365-admin-center"></a>Sécurité & des rapports de conformité dans le centre d’administration Microsoft 365

Ces rapports améliorés fournissent une expérience de création de rapports interactive pour les administrateurs EOP, qui inclut des informations récapitulatives et la possibilité d’approfondir plus en détail.

**Protection avancée contre les menaces (ATP)**: Affichez des informations sur les liens fiables et les pièces jointes fiables qui font partie de l’ATP.

**EOP**: Affichez des informations sur les détections de programmes malveillants, le courrier falsifié, les détections de courrier indésirable et le flux de messagerie vers et depuis votre organisation.

[Afficher les rapports pour Office 365 protection avancée contre les menaces](view-reports-for-atp.md)

## <a name="custom-reports-using-microsoft-graph"></a>Rapports personnalisés à l’aide de Microsoft Graph

Créez par programme des rapports disponibles dans le centre d’administration à l’aide de Microsoft Graph. Pour plus d’informations, reportez-vous à la rubrique [vue d’ensemble de Microsoft Graph](https://docs.microsoft.com/graph/overview) et [utilisation des rapports d’utilisation d’Office 365 dans Microsoft Graph](https://docs.microsoft.com/graph/api/resources/report).

## <a name="message-trace"></a>Suivi des messages

Suit les messages électroniques pendant qu'ils circulent dans EOP. Vous pouvez déterminer si un message électronique a été reçu, rejeté, différé ou remis par le service. Cela indique également les actions entamées par rapport au message avant qu'il atteigne son statut final.

Vous pouvez ainsi répondre efficacement aux questions de vos utilisateurs, résoudre les problèmes de flux de messagerie et valider les modifications de stratégie, tout en réduisant la nécessité de demander de l'aide à l'assistance technique.

Consultez [la rubrique suivi des messages dans le centre de sécurité & conformité](message-trace-scc.md).

## <a name="audit-logging"></a>Journalisation d'audit

Effectue le suivi des modifications spécifiques apportées par les administrateurs à votre organisation. Ces rapports peuvent vous aider à résoudre les problèmes de configuration ou à trouver la cause des problèmes de sécurité ou de conformité. Consultez la rubrique [Auditing reports in EOP](auditing-reports-in-eop.md).

## <a name="reporting-and-message-trace-data-availability-and-latency"></a>Disponibilité et latence des rapports et des données de suivi des messages

Le tableau suivant présente la disponibilité des rapports et des données de suivi des messages EOP, ainsi que leur latence.

||||
|:-----|:-----|:-----|
|**Type de rapport**|**Données disponibles pendant (période rétrospective)**|**Latence**|
|Rapports de synthèse de la protection de la messagerie|90 jours|L'agrégation quasi-complète des données des messages dure entre 24 et 48 heures. Des modifications agrégées incrémentielles mineures peuvent se produire jusqu'à 5 jours.|
|Rapports détaillés de la protection de messagerie|90 jours|Pour les messages de moins de 7 jours, les données détaillées apparaissent normalement dans les 24 heures, mais leur génération peut durer jusqu'à 48 heures. Il est possible que des modifications incrémentielles mineures soient apportées pendant 5 jours. <br/><br/> Pour les messages remontant à plus de sept jours, la génération des résultats détaillés peut prendre plusieurs heures.|
|Données de suivi des messages|90 jours|Lorsque vous effectuez un suivi de messages remontant à moins de 7 jours, ces derniers apparaissent normalement dans les 5 à 30 minutes.<br/><br/> Lorsque vous effectuez un suivi de messages remontant à plus de 7 jours, la génération des résultats peut prendre plusieurs heures.|
|

> [!NOTE]
> La disponibilité et la latence des données sont les mêmes, qu’elles soient demandées via le centre d’administration ou PowerShell à distance.
