---
title: Alertes du service MRS
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appveyor:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: Utilisez les alertes du service de migration de boîtes aux lettres pour surveiller les retards dans les demandes de migration de boîtes aux lettres dans votre organisation.
ms.openlocfilehash: 6b4b618bae602c7c06b2d6371e39cc865d0a3407
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64567981"
---
# <a name="service-alerts-for-mrs-source-delays-in-exchange-online-monitoring"></a>Alertes de service pour les retards de source MRS dans la surveillance Exchange Online

Les alertes du service de réplication de boîte aux lettres (MRS) source vous informent des limitations de stockage ou des problèmes d’utilisation élevée du processeur côté client (source de migration) qui peuvent retarder les migrations de boîtes aux lettres dans votre organisation Microsoft 365. Ces alertes de service incluent également des liens vers des ressources Microsoft pour vous aider à résoudre ces problèmes.

Ces alertes de service sont affichées dans le Centre d'administration Microsoft 365. Pour afficher ces alertes de service,<a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank"></a> >  >  État des services **Exchange Online** puis cliquez sur **l’onglet Problèmes** actifs.

## <a name="what-do-these-service-alerts-indicate"></a>Qu’indiquent ces alertes de service ?

Cette alerte de service vous informe des retards potentiels pour les migrations de boîtes aux lettres dans votre organisation. Cela inclut les migrations entre forêts, les migrations d’intégration et les migrations d’intégration. L’alerte de service contient un tableau contenant des informations sur les migrations en cours dans votre organisation. Voici un exemple de tableau avec des informations sur les retards de migration.

| BatchName | ExchangeGuid | RequestGuid | DelayReason |QueuedHours | DelayInHours | SourceServer | RemoteDatabaseName |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|MRS Migration|246c21f7-ca3c-4bba-ab5d-23456558c52a|3d7fab16-7d8e-4c81-a849-e0795054292a|DiskLatency|35.2|27.3|RD1GBL01EXCH003|GBL01EDAG001-db002|
|Surveillance du client MRS|21e9a608-78c3-44ef-a4dd-d5e7222aae82|9974aeb4-2aa4-4a2c-aeb6-d94d78cc25c9|DiskLatency|0.4|0.9|RD1GBL01EXCH010|GBL01EDAG010-db003|

La liste suivante décrit chaque colonne de l’exemple précédent.

- **BatchName :** nom unique de la tâche de migration.

- **ExchangeGuid :** identificateur global unique (GUID) de la boîte aux lettres utilisateur en cours de migration.

- **RequestGuid :** GUID de la demande de migration.

- **DelayReason :** raison de la migration différée.

- **QueueHours :** durée de la migration en file d’attente.

- **DelayInHours** : durée de retard de la migration.

- **SourceServer :** serveur local dont provient la migration.

- **RemoteDatabaseName** : nom de la base de données dont provient la migration.

## <a name="more-information"></a>Plus d’informations

Pour plus d’informations sur les migrations de boîtes aux lettres et mrs, consultez les articles suivants :

- [Déplacements de boîtes aux lettres Exchange](/exchange/recipients/mailbox-moves)

- [meilleures pratiques Microsoft 365 et Office 365 migration](/exchange/mailbox-migration/office-365-migration-best-practices)

- [Analyse des performances de migration des boîtes aux lettres](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)

- [Résolution des problèmes de migration lente](https://techcommunity.microsoft.com/t5/exchange-team-blog/troubleshooting-slow-migrations/ba-p/1795706)

- [Méthodes de migration des comptes de messagerie vers Microsoft 365](/exchange/mailbox-migration/mailbox-migration)
