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
ms.openlocfilehash: 012361e8ebbf1961d5ca21cef97357d5150523d5
ms.sourcegitcommit: 88ab08c0fa1acbc9e066009e131b9f2b0d506c64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2021
ms.locfileid: "50712054"
---
# <a name="advanced-audit-in-microsoft-365"></a>Audit avancé de Microsoft 365

La [fonctionnalité d'audit unifiée](search-the-audit-log-in-security-and-compliance.md) de Microsoft 365 offre aux organisations une visibilité dans de nombreux types d’activités auditées dans différents services de Microsoft 365. L’audit avancé permet aux organisations d’effectuer des investigations de conformité et d’audit en augmentant la rétention du journal d’audit nécessaire pour mener une investigation, en fournissant l’accès à des événements importants qui permettent de déterminer l’étendue de la compromission et un accès plus rapide à l’API de l’Activité de Gestion d’Office 365.

> [!NOTE]
> L’Audit avancé est à la disposition des organisations disposant d’un abonnement Office 365 E5/G5 ou Microsoft 365 Entreprise E5/G5. De plus, une Conformité Microsoft 365 E5 ou E5 eDiscovery et une licence de complément d’audit peuvent être attribuées aux utilisateurs lorsqu'une licence par utilisateur est requise pour des fonctionnalités d’audit avancées, comme dans le cas de la rétention à long terme de journaux d’audit et l’accès à des évènements essentiels pour enquêtes. Pour plus d’informations sur les licences, voir [instructions relatives aux licences Microsoft 365 pour la sécurité et la conformité](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-audit).

Cet article fournit une vue d’ensemble des fonctionnalités Audit avancé et décrit la configuration des utilisateurs pour l’audit avancé.

## <a name="long-term-retention-of-audit-logs"></a>Conservation à long terme des journaux d’audit

L’audit avancé conserve tous les enregistrements d’audit Exchange, SharePoint et Azure Active Directory pendant une durée d'un an. Ceci est réalisé par une stratégie de rétention du journal d’audit par défaut qui conserve tout enregistrement d’audit contenant la valeur **Exchange**, **SharePoint** ou **AzureActiveDirectory** pour la propriété **Charge de travail** (indiquant le service dans lequel l’activité s’est produite) pendant un an. La rétention d’enregistrements d’audit sur des périodes plus longues peut vous aider à effectuer des investigations de conformité ou de vérification en cours. Pour plus d’informations, voir la section « Stratégie de rétention du journal d’audit par défaut » dans [Gérer les stratégies de rétention du journal d’audit](audit-log-retention-policies.md#default-audit-log-retention-policy).

Nous publions également la fonctionnalité pour retenir les journaux d’audit pendant 10 ans. La rétention de 10 ans des journaux d’audit permet de faciliter les investigations de longue durée et de répondre aux obligations réglementaires, légales et internes.

> [!NOTE]
> La rétention des journaux d’audit pendant 10 ans nécessite une licence supplémentaire de complément.  Cette nouvelle licence sera disponible au début de 2021. Pour plus d’informations, voir la section [Questions Courantes sur l’Audit Avancé](#faqs-for-advanced-audit) de cet article.

### <a name="audit-log-retention-policies"></a>Stratégies de rétention du journal d'audit

Tous les enregistrements d’audit générés dans d’autres services qui ne sont pas couverts par la stratégie de rétention par défaut du journal d’audit (décrits dans la section précédente) sont conservés pendant une durée de 90 jours. Toutefois, vous pouvez créer des stratégies de rétention de journal d’audit personnalisées pour retenir d'autres enregistrements d’audit pendant 10 ans. Vous pouvez créer une stratégie pour conserver les enregistrements d’audit basés sur un ou plusieurs critères énumérés ci-après :

- Service Microsoft 365 dans lequel les activités auditées ont lieu.

- Activités auditées spécifiques.

- L’utilisateur effectuant une activité auditée.

Vous pouvez également spécifier la durée de conservation des enregistrements d’audit qui correspondent à une stratégie et à un niveau de priorité pour que les stratégies spécifiques soient prioritaires sur les autres stratégies. Veuillez noter également que toute stratégie de rétention de journal d’audit personnalisée sera prioritaire sur la stratégie de rétention d’audit par défaut si vous devez retenir des enregistrements d’audit Exchange, SharePoint ou Azure Active Directory pendant moins d’un an (ou pendant 10 ans) pour certains ou tous les utilisateurs de votre organisation. Pour plus d’informations, voir [gérer les stratégies de rétention du journal d’audit](audit-log-retention-policies.md).

## <a name="access-to-crucial-events-for-investigations"></a>Accès aux événements essentiels lors d'enquêtes

L’audit avancé permet aux organisations de mener des investigations de conformité et d’audit en fournissant l’accès aux événements importants, tels que l’accès à des éléments de courrier, l’envoi de réponses à des éléments de courrier et leur transfert, ainsi que le moment et la recherche d’un utilisateur dans Exchange Online et SharePoint Online. Ces événements importants peuvent vous aider à identifier les violations possibles et déterminer l’étendue de la compromission.  L’ Audit Avancé fournit les événements importants suivants:

- [MailItemsAccessed](#mailitemsaccessed)

- [Send](#send)

- [SearchQueryInitiatedExchange](#searchqueryinitiatedexchange)

- [SearchQueryInitiatedSharePoint](#searchqueryinitiatedsharepoint)

### <a name="mailitemsaccessed"></a>MailItemsAccessed

L’événement MailItemsAccessed est une action d’audit de boîte aux lettres qui est déclenchée lorsque les données de courrier sont consultées par les protocoles de messagerie et les clients de messagerie. L’action MailItemsAccessed peut aider les enquêteurs à identifier les violations de données et à mesurer l’étendue des messages susceptibles d’être compromis. Si une personne malveillante a accès aux e-mails, l’action MailItemsAccessed se déclenche même s’il n’y a pas de signal explicite indiquant qu'un message a été réellement lu (en d’autres termes, le type d’accès comme BIND ou synchrone, par exemple, est sauvegardé dans l’enregistrement d’audit).

L’action de la boite aux lettres MailItemsAccessed remplace MessageBind dans la journalisation d’audit des boîtes aux lettres dans Exchange Online et offre ces améliorations:

- MessageBind était seulement configurable pour une ouverture de session utilisateur de type AuditAdmin et ne s’appliquait pas aux actions de propriétaires ou de délégués. MailItemsAccessed s’applique à tout type d’ouverture de session.

- MessageBind ne prenait en charge que l'accès à un client de messagerie. Il ne s’appliquait pas aux activités synchrones. Les événements MailItemsAccessed sont déclenchés par les types d’accès BIND et synchrone.

- Les actions MessageBind déclencheraient la création de plusieurs enregistrements d’audit lors de l’accès au même e-mail, ce qui entraînerait un audit « retentissant ». En revanche, les événements MailItemsAccessed sont regroupés dans un nombre réduit d’enregistrements d’audit.

Si vous souhaitez en savoir plus sur les enregistrements d’audit pour les activités MailItemsAccessed, consultez [Utiliser l’audit avancé pour enquêter sur les comptes compromis](mailitemsaccessed-forensics-investigations.md).

Pour rechercher des enregistrements d’audit MailItemsAccessed, vous pouvez rechercher l’activité **Eléments de la boîte aux lettres consultés** dans la liste déroulante des **Activités de la boîte aux lettres Exchange** dans [l’outil de recherche du journal d’audit](search-the-audit-log-in-security-and-compliance.md) dans le centre de conformité de Microsoft 365.

![Recherche d’actions MailItemsAccessed dans l’outil de recherche du journal d’audit](../media/AdvAudit_MailItemsAccessed.png)

Vous pouvez également exécuter la commande [Search-UnifiedAuditLog -Operations MailItemsAccessed](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) ou [Search-MailboxAuditLog -Operations MailItemsAccessed](https://docs.microsoft.com/powershell/module/exchange/search-mailboxauditlog) dans Exchange Online PowerShell.

### <a name="send"></a>Envoyer

L’événement Envoi est également une action d’audit de boîte aux lettres qui est déclenchée lorsqu’un utilisateur effectue l’une des actions suivantes:

- Envoie un message électronique

- Répond à un message électronique

- Transfert un message électronique

Les investigateurs peuvent utiliser l’événement Envoi pour identifier les messages envoyés à partir d’un compte compromis. L’enregistrement d’audit d’un événement Envoi contient des informations sur le message, par exemple, la date d’envoi du message, l’ID InternetMessage, la ligne d’objet et si le message contient des pièces jointes. Ces informations d’audit peuvent aider les investigateurs à identifier les informations relatives aux messages électroniques envoyés à partir d’un compte compromis ou envoyés par un intrus. De plus, les investigateurs peuvent utiliser un outil eDiscovery Microsoft 365 pour rechercher le message (à l’aide de la ligne d’objet ou de l’ID de message) pour identifier les destinataires du message et le contenu réel du message envoyé.

Pour rechercher des enregistrements d’audit d’Envoi, vous pouvez rechercher l’activité **Message envoyé** dans la liste déroulante des **Activités de la boîte aux lettres Exchange** dans [l’outil de recherche du journal d’audit](search-the-audit-log-in-security-and-compliance.md) dans le centre de conformité de Microsoft 365.

![Recherche d’actions de Message envoyé dans l’outil de recherche du journal d’audit](../media/AdvAudit_SentMessage.png)

Vous pouvez également exécuter les commandes [Search-UnifiedAuditLog -Operations Send](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) ou [Search-MailboxAuditLog -Operations Send](https://docs.microsoft.com/powershell/module/exchange/search-mailboxauditlog) dans Exchange Online PowerShell.

### <a name="searchqueryinitiatedexchange"></a>SearchQueryInitiatedExchange

L’événement SearchQueryInitiatedExchange se déclenche lorsqu’une personne utilise Outlook pour rechercher des éléments dans une boîte aux lettres. Des événements se déclenchent lorsque vous effectuez des recherches dans les environnements Outlook suivants :

- Outlook (client de bureau)

- Outlook sur le web (OWA)

- Outlook pour iOS

- Outlook pour Android

- Application Courrier pour Windows 10

Les investigateurs peuvent utiliser l’événement SearchQueryInitiatedExchange pour déterminer si un intrus qui a compromis un compte a recherché ou essayé d’accéder à des informations sensibles dans la boîte aux lettres. L’enregistrement d’audit d’un événement SearchQueryInitiatedExchange contient des informations telles que le texte de la requête de recherche.  L’enregistrement d’audit indique également l’environnement Outlook où vous avez effectué la recherche. En examinant les requêtes de recherche qu’un intrus peut avoir effectué, un investigateur peut mieux comprendre l’objectif des données de messagerie qui ont été recherchées.

Pour rechercher les enregistrements d’audit de SearchQueryInitiatedExchange, vous pouvez rechercher l’activité **Recherche d’émail effectuée** dans la **liste déroulante** des activités de recherche dans [l’outil de recherche du journal d’audit](search-the-audit-log-in-security-and-compliance.md) dans le centre de conformité.

![La recherche d’actions de recherche d’email effectuée  dans l’outil de recherche du journal d’audit](../media/AdvAudit_SearchExchange.png)

Vous pouvez également exécuter le [Search-UnifiedAuditLog-Operations SearchQueryInitiatedExchange](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) dans Exchange Online PowerShell.

> [!NOTE]
> Vous devez exécuter la commande suivante dans Exchange Online PowerShell de sorte que les événements SearchQueryInitiatedExchange (effectués par l’utilisateur E5 spécifié) soient inclus dans les résultats de la recherche dans le journal d’audit: `Set-Mailbox <user identity> -AuditOwner @{Add="SearchQueryInitiated"}`.<br/><br/>
Dans un environnement multigéographique, vous devez exécuter la commande **Set-Mailbox** dans la forêt où se trouve la boîte aux lettres de l’utilisateur. Pour identifier l’emplacement de boîte aux lettres de l’utilisateur, exécutez la commande suivante : `Get-Mailbox <user identity> | FL MailboxLocations`.
Si vous avez déjà exécuté la commande `Set-Mailbox -AuditOwner @{Add="SearchQueryInitiated"}` dans une forêt différente de celle où se trouve la boîte aux lettres de l’utilisateur, vous devez supprimer la valeur SearchQueryInitiated de la boîte aux lettres de l’utilisateur (en exécutant `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}`), puis l’ajouter à la boîte aux lettres de l’utilisateur dans la forêt où elle se trouve.

### <a name="searchqueryinitiatedsharepoint"></a>SearchQueryInitiatedSharePoint

À l’instar de la recherche d’éléments de boîte aux lettres, l’événement SearchQueryInitiatedSharePoint se déclenche lorsqu’une personne recherche des éléments dans SharePoint. Des événements se déclenchent lorsque vous effectuez des recherches dans les types suivants de sites SharePoint :

- Sites d’accueil

- Sites de communication

- Sites concentrateurs

- Sites associés à Microsoft Teams

Les investigateurs peuvent utiliser l’événement SearchQueryInitiatedSharePoint pour déterminer si un intrus a essayé de rechercher des informations sensibles (et éventuellement y a accédé) dans SharePoint. L’enregistrement d’audit d’un événement SearchQueryInitiatedSharePoint contient également le texte de la requête de recherche. L’enregistrement d’audit indique également le type de site SharePoint où vous avez effectué la recherche. En examinant les requêtes de recherche qu’un intrus peut avoir effectué, un investigateur peut mieux comprendre l’objectif et l’étendue des données de fichiers qui ont été recherchées.

Pour rechercher les enregistrements d’audit SearchQueryInitiatedSharePoint, vous pouvez rechercher l’activité **Recherche SharePoint effectuée** dans la **liste déroulante** des activités de recherche dans [l’outil de recherche du journal d’audit](search-the-audit-log-in-security-and-compliance.md) dans le centre de conformité.

![La recherche d’actions de recherche SharePoint effectuée  dans l’outil de recherche du journal d’audit](../media/AdvAudit_SearchSharePoint.png)

Vous pouvez également exécuter le [Search-UnifiedAuditLog-Operations SearchQueryInitiatedSharePoint](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) dans Exchange Online PowerShell.

> [!NOTE]
> Vous devez exécuter la commande suivante dans Exchange Online PowerShell de sorte que les événements SearchQueryInitiatedExchange (effectués par l’utilisateur E5 spécifié) soient inclus dans les résultats de la recherche dans le journal d’audit: `Set-Mailbox <user identity> -AuditOwner @{Add="SearchQueryInitiated"}`.<br/><br/>
Dans un environnement multigéographique, vous devez exécuter la commande **Set-Mailbox** dans la forêt où se trouve la boîte aux lettres de l’utilisateur. Pour identifier l’emplacement de boîte aux lettres de l’utilisateur, exécutez la commande suivante : `Get-Mailbox <user identity> | FL MailboxLocations`.
Si vous avez déjà exécuté la commande `Set-Mailbox -AuditOwner @{Add="SearchQueryInitiated"}` dans une forêt différente de celle où se trouve la boîte aux lettres de l’utilisateur, vous devez supprimer la valeur SearchQueryInitiated de la boîte aux lettres de l’utilisateur (en exécutant `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}`), puis l’ajouter à la boîte aux lettres de l’utilisateur dans la forêt où elle se trouve.

## <a name="high-bandwidth-access-to-the-office-365-management-activity-api"></a>Accès haut débit à l’API Activité de gestion Office 365

Les organisations ayant accès à des journaux d’audit via l’API Activité de gestion Office 365 étaient restreintes par des seuils de limitation au niveau de l’éditeur. Cela signifie que pour un éditeur faisant une extraction de données pour le compte de plusieurs clients, la limite était partagée par tous les clients.

Grâce à la publication de l'audit avancé, nous allons passer d’une limite au niveau éditeur à une limite au niveau du client. Chaque organisation obtient ainsi son propre quota de bande passante entièrement allouée pour accéder à ses données d’audit. La bande passante n'est pas une limite statique prédéfinie. Elle est modelée sur une combinaison de facteurs, tels que le nombre de sièges au sein de l’organisation, et les organisations E5 obtiennent une bande passante plus importante que les organisations non E5.

Les organisations reçoivent une ligne de base de 2 000 demandes par minute. Cette limite augmentera de façon dynamique en fonction du nombre de sièges d’une organisation et du nombre de licences dans son abonnement. Les organisations E5 disposeront d’environ deux fois plus de bande passante que les organisations non-E5. La bande passante aura également un plafond maximal pour protéger l’état d’intégrité du service.

Pour plus d’informations, consultez la rubrique « Limitation de l'API » dans la [Référence de l’API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference#api-throttling).

## <a name="set-up-advanced-audit-for-users"></a>Configurer l’audit avancé pour les utilisateurs

Les fonctionnalités d’audit avancées telles que la possibilité d’enregistrer des événements importants tels que MailItemsAccessed et envoyer nécessitent une licence E5 appropriée attribuée aux utilisateurs. De plus, l’application/plan de service d’audit avancé doit être activé pour ces utilisateurs. Pour vérifier que l’application d’audit avancée est attribuée aux utilisateurs, procédez comme suit pour chaque utilisateur :

1. Dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com/Adminportal), accédez à **Utilisateurs** > **Utilisateurs actifs**, puis sélectionnez un utilisateur.

2. Dans la page déroulante des propriétés de l’utilisateur, cliquez sur **Licences et applications**.

3. Dans la section **Licences** , vérifiez qu’une licence E5 est attribuée à l’utilisateur.

4. Développez la section **Applications** et vérifiez que la case à cocher **Audit avancé Microsoft 365** est activée.

5. Si la case à cocher n’est pas activée, sélectionnez-la, puis cliquez sur **Enregistrer les modifications.**

   La journalisation des enregistrements d’audit pour MailItemsAccessed, Envoyer et d’autres événements importants pour l’utilisateur commence dans les 24 heures.

Pour les organisations qui attribuent des licences à des groupes d’utilisateurs à l’aide d’une gestion de licences basée sur les groupes, vous devez désactiver l’attribution des licences pour Microsoft 365 audit avancé pour le groupe. Une fois que vous avez enregistré vos modifications, vérifiez que l’audit avancé Microsoft 365 est désactivé pour le groupe. Réactivez ensuite l’attribution des licences pour le groupe. Pour obtenir des instructions sur la gestion des licences basée sur les groupes, voir [Attribuer des licences aux utilisateurs par appartenance aux groupes dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-groups-assign).

De plus, si vous avez personnalisé les actions de boîte aux lettres qui sont enregistrées sur les boîtes aux lettres d’utilisateur ou les boîtes aux lettres partagées, les nouvelles actions de boîte aux lettres par défaut, telles que MailItemsAccessed, ne sont pas automatiquement auditées sur ces boîtes aux lettres. Pour plus d’informations sur la modification des actions de boîte aux lettres auditées pour chaque type de connexion, consultez la section « Modifier ou restaurer les actions de boîte aux lettres enregistrées par défaut » dans [Gérer l’audit de boîte aux lettres](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default).

## <a name="faqs-for-advanced-audit"></a>FAQ pour l’audit avancé

**Est-ce que chaque utilisateur a besoin d'une licence E5 pour bénéficier de l'Audit avancé ?**

Pour bénéficier des fonctionnalités d’audit avancées de niveau utilisateur, ce dernier doit se voir attribuer une licence E5. Certaines fonctionnalités vous permettront de vérifier la présence de la licence appropriée pour exposer la fonctionnalité à l’utilisateur. Par exemple, si vous essayez de conserver les enregistrements d’audit pour un utilisateur ne disposant pas d’une licence E5 pendant plus de 90 jours, le système renvoie un message d’erreur.

**Mon organisation dispose d'un abonnement E5. Dois-je faire quelque chose pour accéder aux enregistrements d'audit des événements importants?**

Pour les clients éligibles et les utilisateurs disposants de la licence appropriée, aucune action n’est requise pour accéder aux événements d’audit cruciaux.

**Quand la nouvelle licence de complément de rétention de journal d’audit de 10 ans sera-t-elle disponible?**

Le nouveau complément de rétention de journal d’audit de 10 ans est désormais disponible à l’achat par les clients disposant d’abonnements E5.

**Qu’arrive-t-il aux données du journal d’audit de mon organisation si je crée une stratégie de rétention du journal d’audit de 10 ans lorsque la fonctionnalité est publiée pour la disponibilité générale, mais avant que la licence de complément requise ne soit disponible en février 2021 ?**

Toutes les données du journal d’audit couvertes par une stratégie de rétention de journal d’audit de 10 ans que vous créez après la mise à disposition générale sont conservées pendant 10 ans. Lorsque la licence de complément de rétention de journal d’audit de 10 ans est disponible au début de 2021, vous devez acheter des licences de complément pour les utilisateurs dont les données d’audit sont retenues par une stratégie de rétention d’audit existante de 10 ans.

**Les nouveaux événements dans l’audit avancé sont-ils disponibles dans l’API Activité de gestion Office 365 ?**

Oui. Tant que les enregistrements d’audit sont générés pour les utilisateurs disposant de la licence appropriée, vous pourrez accéder à ces enregistrements via l’API Activité de gestion Office 365.

**Une bande passante élevée est-elle synonyme d’une meilleure latence ou d’un SLA supérieur ?**

Pour le moment, lune bande passante élevée offre un meilleur pipeline, en particulier pour les organisations présentant un grand nombre de signaux d’audit et de modèles de consommation significatifs. Plus de bande passante peut entraîner une meilleure latence. Cependant, il n’y a pas de SLA associé à une bande passante élevée. Les latences standard sont documentées et ne changent pas avec la version d’audit avancée.
