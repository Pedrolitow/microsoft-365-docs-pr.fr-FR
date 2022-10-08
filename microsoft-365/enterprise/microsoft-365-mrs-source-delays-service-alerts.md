---
title: Alertes de service MRS
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appveyor:
- MET150
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: Utilisez les conseils du service de migration de boîtes aux lettres pour surveiller les retards dans les demandes de migration de boîte aux lettres dans votre organisation.
ms.openlocfilehash: 1be39c430b790a63263d668edd198ccd80401799
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68169428"
---
# <a name="service-advisories-for-mrs-source-delays-in-exchange-online-monitoring"></a>Avis de service pour les retards de source MRS dans la surveillance Exchange Online

Les avis de service de retard du service de réplication de boîte aux lettres (MRS) vous informent des limitations de stockage ou des problèmes d’utilisation élevée du processeur côté client (source de migration) qui peuvent retarder les migrations de boîtes aux lettres dans votre organisation Microsoft 365. Ces conseils de service incluent également des liens vers des ressources Microsoft pour vous aider à résoudre ces problèmes.

Ces avis de service sont affichés dans le Centre d'administration Microsoft 365. Pour afficher ces avis de service, accédez à **Health** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**État des services**</a> >  **Exchange Online**, puis cliquez sur l’onglet **Problèmes actifs**.

## <a name="what-do-these-service-advisories-indicate"></a>Que indiquent ces avis de service ?

Cet avis de service vous informe des retards potentiels dans les migrations de boîtes aux lettres dans votre organisation. Cela inclut les migrations inter-forêts, les migrations d’intégration et les migrations de désintégrage. L’avis de service contient un tableau contenant des informations sur les migrations actuelles dans votre organisation. Voici un exemple de tableau contenant des informations sur les retards de migration.

| BatchGuid | ExchangeGuid | RequestGuid | DelayReason |QueuedHours | DelayInHours | SourceServer | RemoteDatabaseName |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|12345678-1234-1234-1234-1234567891011|246c21f7-ca3c-4bba-ab5d-23456558c52a|3d7fab16-7d8e-4c81-a849-e0795054292a|DiskLatency|35.2|27.3|RD1GBL01EXCH003|GBL01EDAG001-db002|
|87654321-4321-4321-4321-1101987654321|21e9a608-78c3-44ef-a4dd-d5e7222aae82|9974aeb4-2aa4-4a2c-aeb6-d94d78cc25c9|DiskLatency|0.4|0.9|RD1GBL01EXCH010|GBL01EDAG010-db003|

La liste suivante décrit chaque colonne de l’exemple précédent.

- **BatchGuid** : GUID unique pour le travail de migration.

- **ExchangeGuid** : identificateur global unique (GUID) de la boîte aux lettres utilisateur en cours de migration.

- **RequestGuid** : GUID de la demande de migration.

- **DelayReason** : raison du retard de migration.

- **QueueHours** : durée de mise en file d’attente de la migration.

- **DelayInHours** : durée de retard de la migration.

- **SourceServer** : serveur local d’où provient la migration.

- **RemoteDatabaseName** : nom de la base de données d’où provient la migration.

## <a name="more-information"></a>Plus d’informations

Pour plus d’informations sur les migrations mrs et de boîte aux lettres, consultez les articles suivants :

- [La boîte aux lettres se déplace dans Exchange](/exchange/recipients/mailbox-moves)

- [Performances et bonnes pratiques de migration de Microsoft 365 et Office 365](/exchange/mailbox-migration/office-365-migration-best-practices)

- [Analyse des performances de migration de boîte aux lettres](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)

- [Résolution des problèmes de migration lente](https://techcommunity.microsoft.com/t5/exchange-team-blog/troubleshooting-slow-migrations/ba-p/1795706)

- [Méthodes de migration des comptes de messagerie vers Microsoft 365](/exchange/mailbox-migration/mailbox-migration)
