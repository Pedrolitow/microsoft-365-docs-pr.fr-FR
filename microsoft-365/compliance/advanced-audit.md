---
title: Audit avancé de Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-audit
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: L’audit avancé de Microsoft 365 offre de nouvelles fonctionnalités d’audit pour aider votre organisation à effectuer des enquêtes de conformité et de légalité.
ms.openlocfilehash: 51ec75cc8d8ae554ea9cbef3a9ea2aa18171e70a
ms.sourcegitcommit: 9bf6a4f77f9af5fd988f6795bad3b240213a51fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "48950993"
---
# <a name="advanced-audit-in-microsoft-365"></a>Audit avancé dans Microsoft 365

La [fonctionnalité d’audit unifié](search-the-audit-log-in-security-and-compliance.md) de Microsoft 365 fournit aux organisations une visibilité sur de nombreux types d’activités auditées sur différents services de Microsoft 365. L’audit avancé permet aux organisations d’effectuer des enquêtes de légalité et de conformité en augmentant la rétention du journal d’audit nécessaire pour mener une enquête, en fournissant l’accès à des événements importants qui permettent de déterminer l’étendue de la compromission et un accès plus rapide à l’API Activité de gestion Office 365.

> [!NOTE]
> L’audit avancé est disponible pour les organisations disposant d’un abonnement Office 365 E5 or Microsoft 365 Entreprise E5. En outre, les utilisateurs peuvent recevoir une licence de module complémentaire Microsoft 365 E5 Conformité ou E5 eDiscovery et Audit lorsque les fonctionnalités d’audit avancé exigent une licence par utilisateur. C’est le cas, par exemple, de la rétention à long terme des journaux d’audit et de l’accès aux événements cruciaux pour les enquêtes. Si vous souhaitez en savoir plus sur la gestion des licences, veuillez consulter la rubrique [Guide de sécurité et conformité pour les licences Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-audit).

Cet article offre une vue d’ensemble des fonctionnalités d'audit avancé.

## <a name="long-term-retention-of-audit-logs"></a>Conservation à long terme des journaux d’audit

L’audit avancé conserve tous les enregistrements d’audit Exchange, SharePoint, et Azure Active Directory pendant un an. Pour cela, une stratégie par défaut de rétention des journaux d’audit conserve en effet les enregistrements d’audit contenant la valeur **Exchange** , **SharePoint** , ou **AzureActiveDirectory** de la propriété **Workload** (qui indique le service où l’activité s’est produite) pendant un an. La rétention d’enregistrements d’audit sur des périodes plus longues peut vous aider à effectuer des enquêtes de légalité et de conformité en cours. Si vous souhaitez en savoir plus, veuillez consulter la section « Stratégie de rétention de journal d'audit par défaut » dans [Gérer les stratégies de rétention du journal d'audit](audit-log-retention-policies.md#default-audit-log-retention-policy).

Nous publions également la fonctionnalité permettant de conserver les journaux d’audit pendant 10 ans. La rétention des journaux d’audit pendant 10 ans permet de faciliter les enquêtes de longue durée et de répondre aux obligations réglementaires, légales et internes.

> [!NOTE]
> La conservation des journaux d’audit pendant 10 ans nécessite une licence de module complémentaire. Cette nouvelle licence sera disponible début 2021. Si vous souhaitez en savoir plus, veuillez consulter la section [FAQ pour l’audit avancé](#faqs-for-advanced-audit) dans cet article.

### <a name="audit-log-retention-policies"></a>Stratégies de rétention du journal d'audit

Nous conservons tous les enregistrements d’audit générés dans d’autres services et non couverts par la stratégie de rétention par défaut du journal d’audit (décrits dans la section précédente) pendant 90 jours. En revanche, vous pouvez créer des stratégies de rétention de journal d’audit personnalisées pour conserver les autres enregistrements d’audit pendant une période prolongée de 10 ans. Vous pouvez créer une stratégie pour conserver les enregistrements d’audit sur la base d’un ou plusieurs des critères suivants :

- Service Microsoft 365 dans lequel les activités auditées ont lieu.

- Activités auditées spécifiques.

- L’utilisateur effectuant une activité auditée.

Vous pouvez également spécifier la durée de conservation des enregistrements d’audit qui correspondent à la stratégie et un niveau de priorité pour que des stratégies spécifiques soient prioritaires par rapport à d’autres. Notez également que toute stratégie de rétention de journal d’audit personnalisée aura priorité sur la stratégie de rétention d’audit par défaut si vous avez besoin de conserver les enregistrements d’audit Exchange, SharePoint ou Azure Active Directory pendant moins d’une année (ou pendant 10 ans) pour tout ou partie des utilisateurs de votre organisation. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Gérer les stratégies de rétention du journal d'audit](audit-log-retention-policies.md).

## <a name="access-to-crucial-events-for-investigations"></a>Accès aux événements essentiels lors d'enquêtes

L’audit avancé permet aux organisations de mener des enquêtes de légalité et de conformité en donnant accès aux événements cruciaux, tels que la consultation d’éléments de courrier, l’envoi de réponses à des éléments de courrier et leur transfert, ainsi que le moment et l’objet d’une recherche effectuée par un utilisateur dans Exchange Online et SharePoint Online. Ces événements cruciaux peuvent vous aider à identifier les violations possibles et déterminer l’étendue de la compromission. L’audit avancé fournit les événements cruciaux suivants :

- [MailItemsAccessed](#mailitemsaccessed)

- [Send](#send)

- [SearchQueryInitiatedExchange](#searchqueryinitiatedexchange)

- [SearchQueryInitiatedSharePoint](#searchqueryinitiatedsharepoint)

### <a name="mailitemsaccessed"></a>MailItemsAccessed

L’événement MailItemsAccessed est une action d’audit de boîte aux lettres en cas de consultation des données de courrier par les protocoles de messagerie et les clients de messagerie. L’action MailItemsAccessed permet aux enquêteurs d’identifier les violations de données et de déterminer l’étendue des messages éventuellement compromis. Si un attaquant a accédé à des e-mails, l’action MailItemsAccessed se déclenche, même si aucun signal explicite n’indique que l’attaquant a effectivement lu les messages (en d’autres termes, l’enregistrement d’audit comprend le type d’accès tel qu’un lien ou une synchronisation).

L’action de la boite aux lettres MailItemsAccessed remplace MessageBind dans la journalisation d’audit des boîtes aux lettres dans Exchange Online et offre ces améliorations:

- MessageBind était seulement configurable pour une ouverture de session utilisateur de type AuditAdmin et ne s’appliquait pas aux actions de propriétaires ou de délégués. MailItemsAccessed s’applique à tous les types d’ouverture de session.

- MessageBind n’accède qu’à un client de messagerie. Il ne s’applique pas aux activités de synchronisation. Les types d’accès bind (lier) et sync (synchroniser) déclenchent tous deux les événements MailItemsAccessed.

- Les actions MessageBind déclencheraient la création de plusieurs enregistrements d’audit lors de l’accès au même e-mail, ce qui entraînerait un audit « retentissant ». En revanche, les événements MailItemsAccessed sont regroupés dans un nombre réduit d’enregistrements d’audit.

Si vous souhaitez en savoir plus sur les enregistrements d’audit pour les activités MailItemsAccessed, veuillez consulter la rubrique [Utiliser l’audit avancé pour enquêter sur les comptes compromis](mailitemsaccessed-forensics-investigations.md).

Pour rechercher des enregistrements d’audit MailItemsAccessed, vous pouvez rechercher l’activité **Eléments de la boîte aux lettres consultés** dans la liste déroulante des **Activités de la boîte aux lettres Exchange** dans [l’outil de recherche du journal d’audit](search-the-audit-log-in-security-and-compliance.md) dans le centre de conformité de Microsoft 365.

![Recherche d’actions MailItemsAccessed dans l’outil de recherche du journal d’audit](../media/AdvAudit_MailItemsAccessed.png)

Vous pouvez également exécuter la commande [Search-UnifiedAuditLog -Operations MailItemsAccessed](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) ou [Search-MailboxAuditLog -Operations MailItemsAccessed](https://docs.microsoft.com/powershell/module/exchange/search-mailboxauditlog) dans Exchange Online PowerShell.

### <a name="send"></a>Envoyer

L’événement Envoi est également une action d’audit de boîte aux lettres qui est déclenchée lorsqu’un utilisateur effectue l’une des actions suivantes:

- Envoie un message électronique

- Répond à un message électronique

- Transfère un e-mail

Les investigateurs peuvent utiliser l’événement Send (Envoyer) pour identifier les e-mails envoyés depuis un compte compromis. L’enregistrement d’audit d’un événement d’envoi contient des informations sur le message, par exemple, la date d’envoi du message, l’ID InternetMessage, la ligne d’objet et si le message contient des pièces jointes. Ces informations d’audit peuvent aider les enquêteurs à identifier les informations relatives aux e-mails envoyés depuis un compte compromis ou envoyés par un attaquant. De plus, les enquêteurs peuvent utiliser un outil eDiscovery Microsoft 365 pour rechercher le message (à l’aide de la ligne d’objet ou de l’ID de message), puis identifier les destinataires et le contenu réel du message envoyé.

Pour rechercher des enregistrements d’audit d’Envoi, vous pouvez rechercher l’activité **Message envoyé** dans la liste déroulante **Activités de la boîte aux lettres Exchange** de [l’outil de recherche du journal d’audit](search-the-audit-log-in-security-and-compliance.md) dans le Centre de conformité de Microsoft 365.

![Recherche d’actions de Message envoyé dans l’outil de recherche du journal d’audit](../media/AdvAudit_SentMessage.png)

Vous pouvez également exécuter les commandes [Search-UnifiedAuditLog -Operations Send](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) ou [Search-MailboxAuditLog -Operations Send](https://docs.microsoft.com/powershell/module/exchange/search-mailboxauditlog) dans Exchange Online PowerShell.

### <a name="searchqueryinitiatedexchange"></a>SearchQueryInitiatedExchange

L’événement SearchQueryInitiatedExchange se déclenche lorsqu’une personne utilise la barre de recherche d’Outlook sur le web (OWA) pour rechercher des éléments dans une boîte aux lettres. Les enquêteurs peuvent utiliser l’événement SearchQueryInitiatedExchange pour déterminer si un attaquant qui a sans doute compromis un compte a recherché ou essayé de consulter des informations sensibles dans la boîte aux lettres. L’enregistrement d’audit d’un événement SearchQueryInitiatedExchange contient des informations telles que le texte réel de la requête de recherche. En examinant les requêtes de recherche d’un attaquant éventuel, les enquêteurs peuvent mieux comprendre l’objectif des données d’e-mail recherchées.

Pour rechercher les enregistrements d’audit de SearchQueryInitiatedExchange, vous pouvez rechercher l’activité **Recherche d’e-mail effectuée** dans la liste déroulante **Activités de recherche** de [l’outil de recherche du journal d’audit](search-the-audit-log-in-security-and-compliance.md) dans le centre de conformité.

![La recherche d’actions de recherche d’email effectuée  dans l’outil de recherche du journal d’audit](../media/AdvAudit_SearchExchange.png)

Vous pouvez également exécuter le [Search-UnifiedAuditLog-Operations SearchQueryInitiatedExchange](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) dans Exchange Online PowerShell.

> [!NOTE]
> Vous devez exécuter la commande suivante dans Exchange Online PowerShell de sorte que les événements SearchQueryInitiatedExchange (effectués par l’utilisateur E5 spécifié) soient inclus dans les résultats de la recherche dans le journal d’audit: `Set-Mailbox <user identity> -AuditOwner @{Add="SearchQueryInitiated"}`.

### <a name="searchqueryinitiatedsharepoint"></a>SearchQueryInitiatedSharePoint

À l’instar de la recherche d’éléments de boîte aux lettres, l’événement SearchQueryInitiatedSharePoint se déclenche lorsqu’une personne recherche des événements sur le site d’accueil SharePoint de votre organisation. Les enquêteurs peuvent utiliser l’événement SearchQueryInitiatedSharePoint pour déterminer si un attaquant a recherché (et éventuellement trouvé) des informations sensibles dans SharePoint. L’enregistrement d’audit d’un événement SearchQueryInitiatedSharePoint contient également le texte réel de la requête de recherche. En examinant les requêtes de recherche qu’un attaquant a sans doute effectuées, un investigateur peut mieux comprendre l’objectif et l’étendue des données de fichiers qui ont été recherchées.

Pour rechercher les enregistrements d’audit SearchQueryInitiatedSharePoint, vous pouvez rechercher l’activité **Recherche SharePoint effectuée** dans la liste déroulante **Activités de recherche** de [l’outil de recherche du journal d’audit](search-the-audit-log-in-security-and-compliance.md) dans le centre de conformité.

![La recherche d’actions de recherche SharePoint effectuée  dans l’outil de recherche du journal d’audit](../media/AdvAudit_SearchSharePoint.png)

Vous pouvez également exécuter le [Search-UnifiedAuditLog-Operations SearchQueryInitiatedSharePoint](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) dans Exchange Online PowerShell.

> [!NOTE]
> Vous devez exécuter la commande suivante dans Exchange Online PowerShell de sorte que les événements SearchQueryInitiatedSharePoint (effectués par l’utilisateur E5 spécifié) soient inclus dans les résultats de la recherche dans le journal d’audit: `Set-Mailbox <user identity> -AuditOwner @{Add="SearchQueryInitiated"}`.

## <a name="high-bandwidth-access-to-the-office-365-management-activity-api"></a>Accès haut débit à l’API Activité de gestion Office 365

Les organisations qui accèdent à des journaux d’audit via l’API Activité de gestion Office 365 étaient restreintes par des seuils de limitation au niveau de l’éditeur. Cela signifie que pour un éditeur extrayant des données pour le compte de plusieurs clients, tous les clients partageaient la limite.

Grâce à la publication de l'audit avancé, nous allons passer d’une limite au niveau éditeur à une limite au niveau du client. Chaque organisation obtient ainsi son propre quota de bande passante entièrement allouée pour accéder à ses données d’audit. La bande passante n'est pas une limite statique prédéfinie. Elle est modelée sur une combinaison de facteurs, tels que le nombre de sièges au sein de l’organisation, et les organisations E5 obtiennent une bande passante plus importante que les organisations non E5.

Les organisations reçoivent une ligne de base de 2 000 demandes par minute. Cette limite augmentera de façon dynamique en fonction du nombre de sièges d’une organisation et du nombre de licences dans son abonnement. Les organisations E5 disposeront d’environ deux fois plus de bande passante que les organisations non E5. La bande passante aura également un plafond maximal pour protéger l’état d’intégrité du service.

Si vous souhaitez en savoir plus, veuillez consulter la rubrique « Limitation de l'API » dans la [Référence de l’API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference#api-throttling).

## <a name="faqs-for-advanced-audit"></a>FAQ pour l’audit avancé

**Est-ce que chaque utilisateur a besoin d'une licence E5 pour bénéficier de l'Audit avancé ?**

Pour bénéficier des fonctionnalités d’audit avancées de niveau utilisateur, ce dernier doit disposer d’une licence E5. Certaines fonctionnalités vérifient la présence de la licence appropriée pour exposer la fonctionnalité à l’utilisateur. Par exemple, si vous essayez de conserver les enregistrements d’audit pour un utilisateur ne disposant pas d’une licence E5 pendant plus de 90 jours, le système renvoie un message d’erreur.

**Mon organisation dispose d'un abonnement E5. Dois-je faire quelque chose pour accéder aux enregistrements d'audit des événements importants?**

Pour les clients éligibles et les utilisateurs disposants de la licence appropriée, aucune action n’est requise pour accéder aux événements d’audit cruciaux.

**Quand la nouvelle licence de module complémentaire de rétention de journal d’audit de 10 ans sera-t-elle disponible ?**

Le nouveau complément de rétention de journal d’audit de 10 ans sera disponible à l’achat par les clients disposant d’abonnements E5 au début de 2021.

**Qu’arrive-t-il aux données du journal d’audit de mon organisation si je crée une stratégie de rétention du journal d’audit de 10 ans, la fonctionnalité est publiée pour la disponibilité générale, mais avant que la licence de complément requise ne soit disponible au début de 2021 ?**

Toutes les données du journal d’audit couvertes par une stratégie de rétention de journal d’audit de 10 ans que vous créez après la mise à disposition générale sont conservées pendant 10 ans. Lorsque la licence de complément de rétention de journal d’audit de 10 ans est disponible au début de 2021, vous devez acheter des licences de complément pour les utilisateurs dont les données d’audit sont retenues par une stratégie de rétention d’audit existante de 10 ans. De plus, une fois la licence de complément disponible au  début de 2021, les licences appropriées sont appliquées lorsque vous créez des stratégies de rétention de journal d’audit de 10 ans.

**Les nouveaux événements dans l’audit avancé sont-ils disponibles dans l’API Activité de gestion Office 365 ?**

Oui. Tant que les enregistrements d’audit sont générés pour les utilisateurs disposant de la licence appropriée, vous pourrez accéder à ces enregistrements via l’API Activité de gestion Office 365.

**Une bande passante élevée est-elle synonyme d’une meilleure latence ou d’un SLA supérieur ?**

Pour le moment, lune bande passante élevée offre un meilleur pipeline, en particulier pour les organisations présentant un grand nombre de signaux d’audit et de modèles de consommation significatifs. Plus de bande passante peut entraîner une meilleure latence. Cependant, il n’y a pas de SLA associé à une bande passante élevée. Les latences standard sont documentées et ne changent pas avec la version d’audit avancée.
