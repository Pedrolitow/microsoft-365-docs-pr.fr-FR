---
title: Audit avancé de Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: L’audit avancé de Microsoft 365 offre de nouvelles fonctionnalités d’audit pour aider votre organisation à effectuer des enquêtes de conformité et de légalité.
ms.openlocfilehash: 49d2e2bbf7d1c19bb4c282920008a0ca9a34188d
ms.sourcegitcommit: 570ad1c7c334476ecec00dc355dfe52e8c2bb87b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "41862389"
---
# <a name="advanced-audit-in-microsoft-365"></a>Audit avancé de Microsoft 365

La [fonctionnalité d'audit unifiée](search-the-audit-log-in-security-and-compliance.md) de Microsoft 365 offre aux organisations une visibilité dans de nombreux types d’activités auditées dans différents services de Microsoft 365. Avec la publication de l’audit avancé de Microsoft 365, nous offrons de nouvelles fonctionnalités d’audit pouvant aider votre organisation à effectuer des enquêtes de conformité et de légalité.

> [!NOTE]
> Advanced audit est à la disposition des organisations disposant d’un abonnement Office 365 ou Microsoft 365 Entreprise E5. De plus, un abonnement au composant Microsoft 365 E5 Conformité peut être attribué aux utilisateurs lorsqu'une licence par utilisateur est requise pour les fonctionnalités d’audit avancées, comme dans le cas de la conservation à long terme des journaux d’audit et des événements d’audit à valeur élevée.

Cet article offre une vue d’ensemble de ces fonctionnalités d'audit avancées.

## <a name="long-term-retention-of-audit-logs"></a>Conservation à long terme des journaux d’audit

L’audit avancé conserve tous les enregistrements d’audit Exchange, SharePoint et Azure Active Directory pendant une durée d'un an. Ceci est réalisé par une stratégie de rétention du journal d’audit par défaut qui conserve tout enregistrement d’audit contenant la valeur **Exchange**, **SharePoint**ou **AzureActiveDirectory** pour la propriété **Charge de travail** (indiquant le service dans lequel l’activité s’est produite) pendant un an. Cela peut vous aider lors d'enquêtes en cours portant sur la conformité ou la légalité. Pour plus d’informations, voir la section « Stratégie de rétention du journal d’audit par défaut » dans [Gérer les stratégies de rétention du journal d’audit](audit-log-retention-policies.md#default-audit-log-retention-policy).

## <a name="audit-log-retention-policies"></a>Stratégies de rétention du journal d'audit

Tous les enregistrements d’audit générés dans d’autres services qui ne sont pas couverts par la stratégie de rétention par défaut du journal d’audit (décrits dans la section précédente) sont conservés pendant une durée de 90 jours. Toutefois, vous pouvez désormais créer des stratégies de rétention de journal d’audit personnalisées pour conserver d'autres enregistrements d’audit pendant un an. Vous pouvez créer une stratégie pour conserver les enregistrements d’audit basés sur un ou plusieurs critères énumérés ci-après :

- Service Microsoft 365 dans lequel les activités d’audit se produisent

- Activités auditées spécifiques

- Utilisateur effectuant l'activité auditée

Vous pouvez également spécifier la durée de conservation des enregistrements d’audit qui correspondent à une stratégie et à un niveau de priorité pour que les stratégies spécifiques soient prioritaires sur les autres stratégies. Veuillez noter également que toute stratégie de rétention de journal d’audit personnalisée sera prioritaire sur la stratégie de rétention d’audit par défaut si vous devez conserver des enregistrements d’audit Exchange, SharePoint ou Azure Active Directory pendant au moins un an pour tout ou partie des utilisateurs de votre organisation. Pour plus d’informations, voir [Gérer les stratégies de rétention du journal d’audit](audit-log-retention-policies.md).

## <a name="high-value-audit-events"></a>Événements d’audit à valeur élevée

Les événements d’audit relatifs à la sécurité et à la conformité de valeur élevée sont ceux pouvant vous aider à enquêter sur des violations éventuelles ou d'autres enquêtes légales. L'évènement d'audit *MailItemsAccessed* de la boîte aux lettres est le premier élément à valeur élevée en cours de publication. Cet événement se déclenche lorsque les données de courrier sont consultées par les clients et les protocoles de messagerie. L’événement MailItemsAccessed peut aider les enquêteurs à identifier les violations de données et à mesurer l’étendue des messages susceptibles d’être compromis. Si une personne malveillante a accès aux courriers électroniques, l’événement MailItemsAccessed se déclenche même s’il n’y a pas de signal explicite indiquant qu'un message a été réellement lu (en d’autres termes, le type d’accès via BIND ou synchrone, par exemple, est sauvegardé dans l’enregistrement d’audit).

La nouvelle action MailItemsAccessed de la boîte aux lettres remplace MessageBind dans la journalisation d’audit des boîtes aux lettres dans Exchange Online et offre les améliorations suivantes :

- MessageBind était seulement configurable pour une ouverture de session utilisateur de type AuditAdmin et ne s’appliquait pas aux actions de propriétaires ou de délégués. MailItemsAccessed s’applique à tout type d’ouverture de session.

- MessageBind ne prenait en charge que l'accès à un client de messagerie. Il ne s’appliquait pas aux activités synchrones. Les événements MailItemsAccessed sont déclenchés par les types d’accès BIND et synchrone.

- Les actions MessageBind déclenchaient la création de plusieurs enregistrements d’audit lors de l’accès au même courrier, ce qui entraînait un audit « retentissant ». En revanche, les événements MailItemsAccessed sont regroupés dans un nombre réduit d’enregistrements d’audit.

Pour plus d’informations sur la journalisation de l’audit des boîtes aux lettres, voir [Gérer l’audit des boîtes aux lettres](enable-mailbox-auditing.md).

## <a name="high-bandwidth-access-to-the-office-365-management-activity-api"></a>Accès haut débit à l’API Activité de gestion Office 365

Les organisations ayant accès à des journaux d’audit via l’API Activité de gestion Office 365 étaient restreintes par des seuils de limitation au niveau de l’éditeur. Cela signifie que pour un éditeur faisant une extraction de données pour le compte de plusieurs clients, la limite était partagée par tous les clients.

Grâce à la publication de l'audit avancé, nous allons passer d’une limite au niveau éditeur à une limite au niveau du client. Chaque organisation obtient ainsi son propre quota de bande passante entièrement allouée pour accéder à ses données d’audit. La bande passante n'est pas une limite statique prédéfinie. Elle est modelée sur une combinaison de facteurs, tels que le nombre de sièges au sein de l’organisation, et les organisations E5 obtiennent une bande passante plus importante que les organisations non E5.

Les organisations reçoivent une ligne de base de 2 000 demandes par minute. Cette limite augmentera de façon dynamique en fonction du nombre de sièges d’une organisation et du nombre de licences dans son abonnement. Les organisations E5 disposeront d’environ deux fois plus de bande passante que les autres organisations. La bande passante aura également un plafond maximal pour protéger l’état d’intégrité du service.

Pour plus d’informations, consultez la rubrique « Limitation de l'API » dans la [Référence de l’API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference#api-throttling).
